# Applied-Quantum-Machine-Learning

## Report of the course Applied Quantum Machine Learning
### Quantum Annealing for Non-negative/binary Matrix Factorization

Author: Jose Pablo Quesada-Molina (Ph.D. Candidate at DICA, Politecnico di Milano )

This repository contains the implementation and data for the elaboration of the report required evaluation of the course: **Applied Quantum Machine Learning** taught at Politecnico di Milano (POLIMI) by Professor Paolo Cremonesi (DEIB, POLIMI), Alessandro Luongo (Research Fellow at Centre for Quantum Technologies) and Maurizio Ferrari Dacrema (Post-doctoral Researcher at DEIB, POLIMI). 

This work aims to partially reproduce the results of the **Non-negative/binary matrix factorization** method reported in:

1. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0206653
2. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0244026

The folders in this repository are organized as follows:

- The folder called **Implementation** contains a jupyter notebook file called **NBMF.ipynb** which has the full implementation of the method with detailed comments explaining the functionality of each cell; the dataset of facial images **faces.h5**; the files containing the graphs of generated embeddings (.pkl extension) and corresponding embedding time lists (.csv extension), for three different instance sizes.

- The folder called **Summary** contains additional jupyter notebook files for the posprocessing of the results. In particular, this folder contains the files required by the code **plots.ipynb** to generate the plots summarizing the **Relative Error Evolution**, **%Change in B** and **%Change in C**. The folder contains two folders inside, one called **SA** containing the posprocessed results for the simulated annealing experiments, and other called **QA** containing the posprocessed results for the quantum annealing experiments.

- The folder called **Data** contains the original files (.csv, .txt, .png) generated during the execution of the experiments contained in this report. Again, there are two folders inside: **SA** and **QA**. Within **SA** there are 2 folders**SA35** and **SA65**, referring to the original files from simulated annealing for the intermediate instance size and  maximum instance size, respectively. Within **QA**, there are 4 folders **Default-Forward, Reverse, Extended-Forward, Pause-Quench** referring to the original files corresponding to the different quantum annealing schedules explored.
