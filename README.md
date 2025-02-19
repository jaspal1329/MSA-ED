# MSA-ED
Multiple Sequence Alignment- Error Detector

**Objective**: To build a ML model that can detect errors in whole-genome alignments.

**Approach**: Using simulation-based tools generate a simulated *true* alignment. For the same sequences use an alignment tool to generate *predicted* alignment. Compare both alignments to generate data for the ML model. Use domain knowledge to enhance features. Train a classifier. Use the trained model to detect errors in real alignment file. 

The step-by-step approach is as follows:
1. Decide on a set of species and its corresponding phylogenetic tree
2. Use a simulation tool, which takes as input the genomic sequence of the root of the phylogenetic tree, evolves the sequences along the branches of the phylogenetic tree and outputs sequences of the leaf species and their MSA.This alignment is referred to as the true alignment from now on. The simulation tool must take into consideration the various types and rates of evolutionary events (substitutions, indels, duplications etc.).
3. Generate the MSA of the sequences at the leaves of the tree using an alignment tool. From now on this is referred to as the predicted alignment.
4. Compare the alignment files generated by step 2 and step 3 toidentify portions of the alignment where the predicted alignment agrees with the true alignment, and those where they disagree.
5. Using the data produced in step 4, train a machine learning model to identify the portions of the predicted alignment that are incorrect.

The chosen set of species is shown by the phylogenetic tree. Newick format: (((((Cat:0.145927, Microbat:0.17896) C- M:0.003836, (Cow:0.191657, Pig:0.124472) C-P:0.044324) C-M-C-P:0.012255, Shrew:0.341864) C-M-C-P-S:0.0232,((Human:0.032505, Rhesus:0.037831) H-R:0.018791,(Mouse:0.360046, Rabbit:0.214997) M-R:0.013028)H-R-M-R:0.021174) C-M-C-P-S-H-R-M-R:0.022494, Elephant:0.176934) 

Due to the class imbalance problem, we only build a method to detect errors for the Human-Cow alignment pair.

The code is divided into two folders. 
1. **Training**: The code here takes as input the *true* and *predicted* alignment file and after passing through many steps in the pipeline, saves the machine learning model. Pictorially the pipeline could be represented as (to be added).
2. **Prediction**: The code here takes a real alignment file, processes it and predicts the labels of alignment column using the saved ML model from the training phase. Pictorially the pipeline could be represented as (to be added).


### Authors
Jaspal Singh, McGill University, jaspal.singh2@mail.mcgill.ca

Ramchalam K R, McGill University, ramchalam.kinattinkararamakrishn@mail.mcgill.ca
