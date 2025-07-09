# Gradient-Based Leakage Attacks for Graph Convolution Neural Networks (GCNNs) in Circuit Analysis

This repository demonstrates gradient-based leakage attacks applied first to a standard neural network trained on the MNIST dataset and then to a Graph Convolutional Neural Network (GCNN) trained on real-world circuit datasets (ISCAS'85 and EPFL).

## Notebooks Overview

### `Gradient Based Attack to NN.ipynb`
This notebook introduces the core concept of gradient-based leakage attacks on a simple neural network trained with MNIST. It serves as a pedagogical baseline by illustrating how gradients can reveal input information and set the stage for more complex attacks.

### `ISCAS85+EPFL_Parsing.ipynb`
This notebook parses raw circuit netlist data from the ISCAS'85 and EPFL benchmarks, extracting nodes, edges, and circuit features. The processed data is saved as a CSV file, which is later used to build a graph with DGL as input for the GCNN model.

## Code Flow

### 1. Pedagogical Baseline with MNIST
- Implement a neural network.
- Execute a gradient-based leakage attack to reconstruct MNIST inputs.
- Visualize and evaluate reconstruction errors as a baseline for further studies.

### 2. Parsing and Preprocessing Circuit Data
- Parse raw circuit netlists (ISCAS'85 and EPFL) using the dedicated notebook.
- Extract nodes, edges, and key features.
- Save the processed data in CSV format for use in GCNN training.

### 3. GCNN Attack on Circuit Data
- Construct and train a GCNN model using the processed circuit dataset.
- Apply gradient-based leakage attacks to reconstruct sensitive node features.
- Analyze reconstruction errors across different gate types.

### 4. Comparison with different preventive measures
- Run gradient-based attack to GCNN after applying different preventive measures.
- The preventive measures include differential privacy, gradient clipping, secure aggregation, model compression with quantization, and adversarial training.
- Analyze reconstruction errors across different preventive measures for each gate types.

## Results & Insights

- The attack on MNIST demonstrates how gradients expose input data, setting a baseline for understanding the vulnerability of neural networks.
- Extending the attack to GCNNs trained on ISCAS'85 and EPFL circuit data reveals security concerns in hardware systems.
- Different circuit components show varying levels of susceptibility, with some gate types (e.g., `xor` and `output` gates) proving harder to reconstruct than others.
- The findings emphasize the need for privacy-preserving mechanisms in hardware security.

## How to Use This Repository

1. **Run `ISCAS85+EPFL_Parsing.ipynb`** to preprocess the circuit data and save it as CSV.
2. **Run `Gradient Based Attack to NN.ipynb`** to understand the attack mechanism using MNIST.
3. **Use the GCNN implementation** to train on circuit data and perform the gradient leakage attack.
4. **Analyze reconstruction errors** using the provided statistical and visualization tools along with several preventive measures.


## The `Appendix` showing the outcome of gradient leakage under several defense strategies is given in the `Appendix_Gradient_Attack_GCNN.pdf` file.

Contributions to defense strategies and further hardware security research are highly encouraged.


