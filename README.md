# Applied-Quantum-Machine-Learning
Author: Jose Pablo Quesada-Molina (Ph.D. candidate at DICA, POLIMI)

This repository contains the implementation and data for the elaboration of the report required evaluation of the course: **Applied Quantum Machine Learning** from Politecnico di Milano by Professor Paolo Cremonesi (DEIB, POLIMI), Alessandro Luongo (Research Fellow @ Centre for Quantum Technologies) and Maurizio Ferrari Dacrema (Post-doctoral Researcher @ DEIB, POLIMI). 

This work aims to partially reproduce the results of the **Non-negative/binary matrix factorization** method, reported in:

1. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206653
2. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0244026

The folders in this repository are organized as follows:

- The Main Folder contains a Jupyter Notebook file called *NBMF.ipynb* which has the full implementation with detailed comments explaining the functionality of each cell. The facial images dataset file *faces.h5* is also provided together with the files containing the information of the statistics for the generated embeddings(.pkl) 
- The folder called Plots contains additional Jupyter Notebook code and files developed for the generation of the plots summarizing the Relative Error Evolution, %Change in B and %Change in C. There are two folders inside, one containing the files for the simulated annealing experiments and other containing those for the quantum annealing.
- The folder called Data contains the original files (.csv, .txt) from all the experiments generated during the elabotation of this report. Again, there are two folders inside, one containing the files for the simulated annealing experiments and other containing those for the quantum annealing.
