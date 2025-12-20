# Urban Migration Prediction: A Markov Chain Model

## 📌 Project Overview
This project applies **Linear Algebra** and **Probability Theory** to real-world urban planning data. Using **Markov Chains**, we model the population flow between three major US economic hubs: **California**, **Texas**, and **New York**.

By analyzing historical migration data from 2022, we built a transition matrix to simulate future population shifts over the next 50 years and calculate the long-term "Steady State" equilibrium.

## 📊 Data Source
* **Dataset:** [Migration Flows Across U.S. States (2010-2022)](https://www.kaggle.com/datasets/ygebre1/migration-flows-across-u-s-states-20102022)
* **Source:** U.S. Census Bureau data.
* **Year Analyzed:** 2022 (Most recent complete dataset).
* **States Tracked:** California (CA), Texas (TX), New York (NY).

## 🧮 Methodology
The project treats the three states as a **Closed System**.
1.  **Transition Matrix ($P$):** We calculated the probability $P_{ij}$ that a resident of State $i$ moves to State $j$ (or stays) based on 2022 flow counts.
2.  **Simulation Loop:** We projected population for $n$ years using the matrix multiplication formula:
    $$\pi_{n+1} = \pi_n \times P$$
3.  **Steady State:** We calculated the eigenvector corresponding to $\lambda = 1$ to find the theoretical long-term equilibrium where migration stabilizes.

## 📉 Key Findings
Our simulation revealed a significant demographic shift:
* **Texas** acts as an "absorbing state" with a retention rate of **>99.8%**, gaining population from both CA and NY.
* **California** is projected to lose population share, dropping from **~29.4%** in the steady state.
* **New York** stabilizes at a lower population share of **~15.4%**.

| State | Initial Share (2022) | Predicted Steady State Share |
| :--- | :--- | :--- |
| **Texas** | ~29% | **55.1%** |
| **California** | ~38% | **29.4%** |
| **New York** | ~19% | **15.4%** |

## 📂 File Structure
* `migration_model.ipynb`: The main Python analysis notebook.
* `migration_counts_raw.csv`: Raw migration data extracted from Census.
* `transition_matrix.csv`: The calculated probability matrix ($P$).
* `50_year_forecast.csv`: Year-by-year population predictions.
* `steady_state.csv`: The final equilibrium values.

## 🛠️ Requirements & Usage
To run this project, you need Python and the following libraries:

```bash
pip install pandas numpy matplotlib networkx
