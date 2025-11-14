# Gradient-Based Leakage Attacks for Graph Neural Networks (GNNs) in Circuits

This repository demonstrates gradient-based leakage attacks applied first to a standard neural network trained on the MNIST dataset and then to a several Graph Neural Networks (GNNs) trained on real-world circuit datasets (ISCAS'85 and EPFL) for gate classification and hardware Trojan detection.

## Please refer to `Supplementary materials for Gradient_Attack_GNN.pdf` file for the detailed mathematics and results that are not covered in the paper due to page limit. 

## Notebooks Overview

### `Gate Classification Folder`
The notebooks in this folder introduces the core concept of gradient-based leakage attacks on several GNNs including `GCN`, `GraphSAGE`, `GIN`, and `GAT`. The end-to-end code is given in each of the jupyter notebook.

### `Hardware Trojan Folder`
The notebooks in this folder introduces the core concept of gradient-based leakage attacks on several GNNs including `GCN`, `GraphSAGE`, `GIN`, and `GAT`. The end-to-end code is given in each of the jupyter notebook. It also have the Trojan dataset and the way to generate it by inserting the templates from Trust hub in `Trojan_Injection_Parsing.ipynb`. 

### `ISCAS85+EPFL_Parsing.ipynb`
This notebook parses raw circuit netlist data from the ISCAS'85 and EPFL benchmarks, extracting nodes, edges, and circuit features. The processed data is saved as a CSV file, which is later used to build a graph with DGL as input for the GCNN model.

### `Gradient Based Attack to MNIST.ipynb`
This notebook introduces the core concept of gradient-based leakage attacks on a simple neural network trained with MNIST. It serves as a pedagogical baseline by illustrating how gradients can reveal input information and set the stage for more complex attacks.

## Code Flow

### 1. Pedagogical Baseline with MNIST in `Gradient Based Attack to MNIST.ipynb`
- Implement a neural network.
- Execute a gradient-based leakage attack to reconstruct MNIST inputs.
- Visualize and evaluate reconstruction errors as a baseline for further studies.

### 2. Parsing and Preprocessing Circuit Data in `ISCAS85+EPFL_Parsing.ipynb`
- Parse raw circuit netlists (ISCAS'85 and EPFL) using the dedicated notebook.
- Extract nodes, edges, and key features.
- Save the processed data in CSV format for use in GCNN training.

### 3. GNN (GCN, GraphSAGE, GIN, GAT) for Circuit Data for gate classification in folder `Gate Classification`
- Construct and train a GNNs model using the processed circuit dataset.
- Apply gradient-based leakage attacks to reconstruct sensitive node features.
- Analyze reconstruction errors across different gate types.

### 4. GNN (GCN, GraphSAGE, GIN, GAT) for Hardware Trojan Detection Modelin folder `Hardware Trojan Dection`
- Construct and train a GNNs model using the processed dataset in the folder  `GNNDatasets`.
- Apply gradient-based leakage attacks to reconstruct sensitive node features.
- Analyze reconstruction errors across different class types.

### 5. Comparison with different preventive measures
- Applies to `Gate Classification` and `Hardware Trojan` folders for each notebook
- Run gradient-based attack to GNNs after applying different preventive measures.
- The preventive measures include differential privacy, gradient clipping, secure aggregation, model compression with quantization, and adversarial training.
- Analyze reconstruction errors across different preventive measures for each gate types.



## The `Appendix` showing the outcome of gradient leakage under several defense strategies is given in the `Appendix_Gradient_Attack_GCNN.pdf` file.

Contributions to defense strategies and further hardware security research are highly encouraged.


