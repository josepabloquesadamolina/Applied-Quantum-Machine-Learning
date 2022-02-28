# Applied-Quantum-Machine-Learning

## Report of the course Applied Quantum Machine Learning
### Quantum Annealing for Non-negative/binary matrix factorization (NBMF)

Author: Jose Pablo Quesada-Molina (Ph.D. Candidate at DICA, Politecnico di Milano )

This repository contains the implementation and data for the elaboration of the report to be considered for evaluation of the course: **Applied Quantum Machine Learning** taught at Politecnico di Milano (POLIMI) by Professor Paolo Cremonesi (DEIB, POLIMI), Alessandro Luongo (Research Fellow at Centre for Quantum Technologies) and Maurizio Ferrari Dacrema (Post-doctoral Researcher at DEIB, POLIMI). 

This work aims to partially reproduce the results of the **Non-negative/Binary Matrix Factorization (NBMF)** method reported in:

1. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206653
2. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0244026

The folders in this repository are organized as follows:

- The folder called **Implementation** contains a jupyter notebook file called **NBMF.ipynb** which has the full implementation of the method with detailed comments explaining the functionality of each cell; the dataset of facial images **faces.h5**; the files containing the graphs of generated embeddings (.pkl extension) and corresponding embedding time lists (.csv extension), for three different instance sizes.

- The folder called **Summary** contains additional jupyter notebook files for the posprocessing of the results. In particular, this folder contains the files required by the code **plots.ipynb** to generate the plots summarizing the **Relative Error Evolution**, **%Change in B** and **%Change in C**. The folder contains two folders inside, one called **SA** containing the posprocessed results for the simulated annealing experiments, and other called **QA** containing the posprocessed results for the quantum annealing experiments.

- The folder called **Data** contains the original files (.csv, .txt, .png) generated during the execution of the experiments contained in this report. Again, there are two folders inside: **SA** and **QA**. Within **SA** there are 2 folders: **SA35** and **SA65**, referring to the original files from the simulated annealing experiments for the intermediate and maximum instance size, respectively. Within **QA**, there are 4 folders: **Default-Forward, Reverse, Extended-Forward, Pause-Quench** referring to the original files from the experiments using different quantum annealing schedules.

# Problem description and its QUBO formulation

The matrix factorization method considered in this work, described as Non-negative/Binary Matrix Factorization (NBMF), aims to find a decomposition for an $n\times m$ matrix, $A$, into the product of two matrices, $B$ and $C$, where $B$ is an $n\times k$ matrix, $C$ is a $k\times m$ matrix and $k << $ min$(n,m)$. That is, find $B$ and $C$ such that: 

\begin{equation}
  A \approx BC 
\end{equation}

Specific constraints are enforced on $B$ and $C$: the components of $B$ must be non-negative (i.e., $B_{ij} \geq 0$) and the components of $C$ must be binary (i.e., $C_{ij} \in \{0, 1\}$).


There are two main subroutines employed to perform the NBMF. The first one, is related to the solution of a non-negative least squares problem (bound-constrained minimization) associated to the determination of $B$. For this,  Nelder-Mead method has been chosen. A regularization part, $\alpha \| X\|_{F}$, with $\alpha = 1\times 10^{-2}$, is added to the objective function to avoid over-fitting. By selecting the Frobenius Norm, $\|D\|_{F}:= \sqrt{Tr(DD^{T})}=\sqrt{\sum_{i}\sum_{j}|d_{ij}|^{2}}$, the objective function can be easily transformed to a matrix trace version:

\begin{equation}
  {B= arg min}_{X \in {\mathbb{R}}^{+n\times k}} Tr((A-XC)(A-XC)^{T})+\alpha Tr(XX^{T})
\end{equation}

or to a scalar one:

\begin{equation}
  {B= arg min}_{X \in {\mathbb{R}}^{+n\times k}} \sum_{i=0}^{n}\sum_{j=0}^{m}(A_{i,j}-\sum_{l=0}^{k}X_{i,l}C_{l,j})^{2}+\alpha\sum_{l=0}^{k} (X_{i,l})^{2}
\end{equation}

For the second subroutine, we focus on utilizing a D-Wave 2000Q quantum annealer to compute:

\begin{equation}
    {C= arg min}_{X \in \{0,1\}^{k\times m}} \| A-BX\|_{F}^{2}
\end{equation}

The previous equation can be solved by solving a set of independent optimization problems; one for each column of $C$. That is, if we denote the $j^{th}$ columns of $C$ and $A$ by $C_{j}$ and $A_{j}$, respectively, then the previous equation can be re-written as:

\begin{equation}
    {C_{j}=arg min}_{q\in \{0,1\}^{k}} \|A_{j}-Bq\|_{L_{2}}^{2}   
\end{equation}

where $q$ represents a vector of $k$ binary variables and the solution for $C_{j}$. In this way, it is possible to move from an equation which involves the optimization of $km$ binary variables, to one involving only $k$ binary variables. 

The binary least squares problem associated to $C_{j}$ can be readily represented in the form of a QUBO, by setting:

\begin{align}
    Q_{k,k}=\sum_{i=1}^{n} B_{ik}(B_{ik}-2A_{ij})\\
    Q_{kl}=2\sum_{l=1}^{k-1}\sum_{i=1}^{n} B_{ik}B_{il}
\end{align}

