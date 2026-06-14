# rocket-league-pca

Dimensionality reduction (PCA) of Rocket League 3v3 ranked match data (Season 18), sourced from [ballchasing.com](https://ballchasing.com).

Companion code and data for: *Dimensionality reduction of Rocket League match data isolates independent rank and win predictors* (Mesmer & Meyers, 2026).

## Contents

| File | Description |
|---|---|
| `RL_Data_Preparation.Rmd` | Cleans raw ballchasing.com export: handles missingness, winsorises outliers, selects 58 continuous features for PCA. Outputs `pca_data.csv` and `working.csv`. |
| `RL_PCA_Analysis.Rmd` | Runs PCA on `pca_data.csv`, generates scree plot and biplots, correlates component scores with rank and match outcome. |
| `pca_data.csv` | 76,035 player-level observations × 58 standardised numeric performance features (PCA input). |
| `working.csv` | Full working dataset (76,035 × ~90): same observations with match ID, rank, car, and match result retained for downstream correlation analysis. |

## Data provenance

Raw match replay data were retrieved via the ballchasing.com public API. All direct identifiers (player names, platform IDs) and timestamps were removed during data preparation. `match_id` is a randomly generated UUID and carries no identifying information. The files in this repository are the de-identified, processed analytic datasets — not the raw API export.

## Reproducing the analysis

1. Open `RL_PCA_Analysis.Rmd` in R/RStudio.
2. Required packages: `tidyverse`, `DescTools`, `factoextra`, `skimr`, `DataExplorer`, `Hmisc`.
3. Knit — it reads `pca_data.csv` and `working.csv` directly from this directory.

`RL_Data_Preparation.Rmd` documents the cleaning pipeline from the raw API export but requires that raw file (not included here, see Data provenance) to re-run end to end; its outputs (`pca_data.csv`, `working.csv`) are provided directly.

## License

- Code (`.Rmd` files): [MIT](LICENSE)
- Data (`.csv` files): [CC0 1.0](LICENSE-DATA) (public domain)
