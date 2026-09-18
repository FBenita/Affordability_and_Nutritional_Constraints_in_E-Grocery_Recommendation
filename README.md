# Affordability and Nutritional Constraints in E-Grocery Recommendation

This repository contains the data and computational frameworks used to evaluate constraint-handling mechanisms in food recommender systems. It models the operational failure modes that occur when a user's economic budget strictly conflicts with their nutritional requirements (e.g., sodium, saturated fat, and sugar limits).

The framework contrasts standard heuristic architectures against a proposed two-stage lexicographic goal programming model, demonstrating how percentage-based penalty formulations inherently distribute the burden of constraint compromise across different socioeconomic strata.

## Repository Structure

*   `data/`: Contains the raw USDA Food and Nutrient Database for Dietary Studies (FNDDS) and Purchase to Plate National Average Prices (PP-NAP) datasets, alongside the classified $N=385$ empirical convenience catalog.
*   `notebooks/`: Jupyter notebooks detailing the data ingestion, empirical evaluation, and Monte Carlo sensitivity simulations.
*   `results/`: Output visual analytics, including the two-dimensional phase transition heatmaps.

## Computational Pipeline

The analysis is partitioned into four reproducible notebooks:

1.  **`01_data_ingestion.ipynb`**: Merges FNDDS and PP-NAP records via USDA food codes, applies deterministic keyword classification for preparation-time proxies, and generates the baseline empirical catalog.
2.  **`02_empirical_evaluation.ipynb`**: Evaluates the empirical catalog against three selection architectures: Unconstrained Baseline ($M_0$), Post-Hoc Filtering ($M_1$), Soft-Penalty Scalarization ($M_2$), and Two-Stage Lexicographic Relaxation ($M_3$).
3.  **`03_monte_carlo_simulation.ipynb`**: Executes synthetic market simulations ($N=5000$, $R=500$) varying the negative correlation ($\gamma$) between price and nutrient density to isolate algorithmic failure rates (e.g., candidate pool truncation and penalty calibration limits).
4.  **`04_phase_transition_heatmaps.ipynb`**: Generates 2D sensitivity surfaces mapping the intersection of item price ceilings ($\beta$) and market dependence ($\gamma$) to quantify the socioeconomic distribution of constraint relaxation.

