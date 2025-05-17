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

## Results & Insights

- The attack on MNIST demonstrates how gradients expose input data, setting a baseline for understanding the vulnerability of neural networks.
- Extending the attack to GCNNs trained on ISCAS'85 and EPFL circuit data reveals security concerns in hardware systems.
- Different circuit components show varying levels of susceptibility, with some gate types (e.g., `xor` and `output` gates) proving harder to reconstruct than others.
- The findings emphasize the need for privacy-preserving mechanisms in hardware security.

## How to Use This Repository

1. **Run `ISCAS85+EPFL_Parsing.ipynb`** to preprocess the circuit data and save it as CSV.
2. **Run `Gradient Based Attack to NN.ipynb`** to understand the attack mechanism using MNIST.
3. **Use the GCNN implementation** to train on circuit data and perform the gradient leakage attack.
4. **Analyze reconstruction errors** using the provided statistical and visualization tools.

Contributions to defense strategies and further hardware security research are highly encouraged.

### Result Analysis:
Reconstruction Percentage Error Analysis:

• and (class 0): Errors range from as low as 0.006% to about 5.5%, with many samples showing very low percentages. This indicates that, for "and" gates, the attack generally succeeds well, although a few instances exhibit higher errors.

• input (class 1): Errors are consistently moderate (roughly 3.4% to 5.6%), implying a steady yet slightly higher reconstruction deviation compared to some other gate types.

• nand (class 2): Most reconstruction errors are nearly negligible (on the order of 10^-4 to 10^-3%), demonstrating almost perfect recovery of node features overall—with the exception of one outlier (1.9%).

• nor (class 3): A bimodal behavior is observed: some nodes are reconstructed with virtually zero error while others fall in the 2–4% range, suggesting variability in vulnerability within this class.

• not (class 4): The majority of errors lie between 1.3% and 4.7%; however, one extreme case at ~24.9% indicates occasional reconstruction difficulties.

• or (class 5): Errors are extremely low (mostly around 10^-4 to 10^-3%), showing that "or" gates are highly susceptible to the attack with near-perfect reconstruction.

• output (class 6): Reconstruction errors here are relatively high (generally 4%–8%), reflecting the increased complexity or robustness in these nodes.

• xor (class 7): Consistently high errors (around 22%–25%) suggest that "xor" gates are much less vulnerable, likely due to their inherent structural complexity.

Overall, the findings reveal that vulnerability to gradient-based leakage attacks varies by gate type. While "nand" and "or" gates are exceptionally prone to feature inversion, "xor" and "output" gates are more challenging to reconstruct accurately.
