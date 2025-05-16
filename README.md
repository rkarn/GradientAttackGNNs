



## Repository Structure

- **Notebook 1: ISCAS85+EPFL_Parsing.ipynb**  
  Contains the code for parsing circuit netlists (from ISCAS85 and EPFL benchmarks). It extracts node-, edge-, and feature-information and saves the resulting graph dataset as a CSV file.

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
