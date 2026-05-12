# HIVint: Predicting Physical Interactions Between HIV and Human Proteins

Welcome to the official documentation for **HIVint**, a computational method developed to predict direct physical interactions between the Human Immunodeficiency Virus (HIV) and human proteins. HIV relies heavily on the host cell's machinery for survival and replication, interacting with approximately 1,500 human proteins. HIVint specifically focuses on identifying the ~40% of these interactions that are direct (physical) to facilitate the discovery of new therapeutic targets.

**Web Server:** [https://webs.iiitd.edu.in/raghava/hivint/](https://webs.iiitd.edu.in/raghava/hivint/)

---
## citation

## Background

HIV is a retrovirus with a small genome (~9.5 Kb) encoding only 15–20 proteins. Because its own proteome is insufficient for survival, it hijacks host proteins. Halting any essential physical protein-protein interaction (PPI) can effectively interrupt the viral life cycle. HIVint provides a predictive framework to identify these critical human-virus interfaces.

---

## Dataset Information

The models were developed using high-quality data from the **NCBI HIV-Human Protein Interaction Database**.

* **Positive Dataset:** Human proteins known to interact directly (physically) with HIV-1.
* **Negative Dataset:** Randomly selected human proteins from the Mitochondrial, Cytoplasmic, and Nuclear compartments (retrieved from UniProt) to serve as non-interacting controls.

---

## Prediction Approaches

The study implemented four distinct features to represent protein data for the machine learning models:

### 1. Amino Acid Composition (AAC)
Calculates the percentage of each of the 20 natural amino acids. Weights are derived by comparing composition data between interacting and non-interacting sets. An unknown protein is scored by summing the weighted compositions of its residues.

### 2. Dipeptide Composition (DPC)
Analyzes the frequency of 400 (20x20) possible pairs of adjacent amino acids. This captures local sequence order and provides a more detailed cumulative score for interaction potential.

### 3. Split Amino Acid Composition (SAAC)
Sequences are divided into non-overlapping fragments (e.g., N=2 for V3 sequences), and the composition of each fragment is calculated independently. This results in a higher-dimensional input vector (N×20) that captures regional characteristics within the protein.

### 4. Domain-Based Approach
Utilizes the **'hmmpfam'** tool from the **iprscan** software to identify exclusive protein domains. These domains serve as input vectors for classification, identifying structural motifs common in human proteins that physically interact with HIV.

---

## Technical Overview

### Support Vector Machine (SVM)
The core of the prediction engine is based on **SVM_light**, a statistical learning technique.
* **Kernel Functions:** Includes Linear, Polynomial, and Radial Basis Function (RBF) kernels.
* **Optimization:** Unlike neural networks, SVM provides a globally optimized solution for pattern recognition and classification tasks.

### Evaluation Metrics
The performance of the models was rigorously tested using **5-fold cross-validation**. The following metrics were used to determine accuracy:

* **Sensitivity:** Ability to correctly identify true interacting proteins.
* **Specificity:** Ability to correctly identify non-interacting proteins.
* **Accuracy:** Overall percentage of correct predictions.
* **MCC (Matthews Correlation Coefficient):** A measure of the quality of binary classifications, providing a balanced value even if classes are of different sizes.

---

## Applications

* **Drug Target Discovery:** Identifying specific human proteins that, if inhibited, could block HIV replication.
* **Systems Biology:** Mapping the physical interactome between HIV and its human host.
* **Therapeutic Intervention:** Developing new methods to halt the HIV life cycle by disrupting essential protein-protein interfaces.

---

## Contact & Developers

**Prof. Gajendra P. S. Raghava** Department of Computational Biology, Indraprastha Institute of Information Technology (IIIT-Delhi), India.  
**Web Server Details:** [https://webs.iiitd.edu.in/raghava/hivint/algorithm.html](https://webs.iiitd.edu.in/raghava/hivint/algorithm.html)

---

## License

This resource is provided for academic and research purposes. Please refer to the official website for specific usage terms and citation requirements.
