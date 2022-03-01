# Applied-Quantum-Machine-Learning

## Final Report
### Quantum Annealing for Non-negative/binary matrix factorization

Author: Jose Pablo Quesada-Molina (Ph.D. Candidate at DICA, Politecnico di Milano )

This repository contains the implementation and data for the elaboration of the report to be considered for evaluation of the course: **Applied Quantum Machine Learning** taught at Politecnico di Milano (POLIMI) by Professor Paolo Cremonesi (DEIB, POLIMI), Maurizio Ferrari Dacrema (Post-doctoral Researcher at DEIB, POLIMI) and Alessandro Luongo (Research Fellow at Centre for Quantum Technologies). 

This work aims to partially reproduce the results of the **Non-negative/Binary Matrix Factorization (NBMF)** method reported in:

1. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206653
2. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0244026

In the NBMF, an input matrix **A** is decomposed into the product of two low-rank matrices **BC**, subjected to non-negative and binary constraints, respectively.

The folders in this repository are organized as follows:

- The folder called **Implementation** contains a jupyter notebook file called **NBMF.ipynb** which has the full implementation of the method with detailed comments explaining the functionality of each cell; the dataset of facial images **faces.h5**; the image of the annealing schedules considered for the quantum annealing experiments **schedules.png** ; the files containing the graphs of generated embeddings (.pkl extension) and corresponding embedding time lists (.csv extension), for three different instance sizes. 

- The folder called **Summary** contains additional jupyter notebook files for the posprocessing of the results. In particular, this folder contains the files required by the code **plots.ipynb** to generate the plots summarizing the **Relative Error Evolution**, **%Change in B** and **%Change in C**. The folder contains two folders inside, one called **SA** containing the posprocessed results for the simulated annealing experiments, and other called **QA** containing the posprocessed results for the quantum annealing experiments.

- The folder called **Data** contains the original files (.csv, .txt, .png) generated during the execution of the baseline model and the experiments using different quantum annealing schedules. There are 5 folders: **SA-Baseline, Default-annealing, Reverse, Extended-annealing, Pause-Quench**.

**Note:** By default, **Implementation** folder also contains the files that allow to visualize the results associated to the **Reverse** experiment. To visualize the results of other experiments, copy and paste there the corresponding files from **Data**.

