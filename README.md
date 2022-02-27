# Applied-Quantum-Machine-Learning
Author: Jose Pablo Quesada-Molina (Ph.D. candidate at POLIMI)

This repository contains the implementation and data of the Final Report submitted for the evaluation of the course: Applied Quantum Machine Learning from Politecnico di Milano by Professor Paolo Cremonesi (DEIB @ POLIMI), Alessandro Luongo Research ( Research Fellow @ Centre for Quantum Technologies) and Maurizio Ferrari Dacrema (Post-doc Researcher @ DEIB POLIMI). 

The work in this final report aims to partially reproduce the results of the Non-negative/binary matrix factorization method, reported in:

https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206653
https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0244026

Due to limited available quantum computational resources, the factorization of the full-sized input matrix (reported in the previously mentioned works) is implemented and validated using simulated annealing. A reduced-sized version of this input has been instead considered when exploring the use of standard forward quantum annealing and reverse annealing for the solution of the mentioned matrix. Other annealing schedules are also explored.

The Main Folder contain a Jupyter Notebook file called NBMF.ipynb which contains the implementation, with detailed comments regarding the functionality of each cell. The facial images dataset file faces.h5 is also provided together with   
The folder called Plots contains additional Jupyter Notebook code and files developed for the generation of the plots summarizing the Relative Error Evolution, %Change in B and %Change in C. There are two folders inside, one containing the files for the simulated annealing experiments and other containing those for the quantum annealing.
The folder called Data contains the original files (.csv, .txt) from all the experiments generated during the elabotation of this report. Again, there are two folders inside, one containing the files for the simulated annealing experiments and other containing those for the quantum annealing.
