# Formula 1 Podium Prediction — Milestone 1

Predicting whether a Formula 1 driver finishes on the podium (`positionOrder <= 3`) using only information available **after qualifying and before the race starts**.

CSEN 903 Advanced Computer Lab, Winter 2026 — Milestone 1.

## Contents

| File | Description |
| --- | --- |
| `F1_Podium_Prediction_Milestone1.ipynb` | The single run-all notebook (with outputs from the Kaggle run): audit, cleaning, data-engineering questions, feature engineering, models, experiments, explainability, inference function |
| `Milestone1_Report.pdf` | Analytical report |
| `requirements.txt` | Python libraries used |

- Kaggle notebook: https://www.kaggle.com/code/markkmagedd/notebook1334ac465e
- Dataset: [Formula 1 World Championship (1950–2024)](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020) (Kaggle / Ergast, 14 CSV tables)

## How to run

1. On Kaggle, import the notebook and attach the dataset above (or place the 14 CSVs in a folder named `f1data/` next to the notebook when running locally).
2. Run All. The notebook finds the data folder automatically, needs no manual steps, and peaks at about 0.7 GB of RAM (runs in a 1 GB session).

## Results summary

| Item | Result |
| --- | --- |
| Modeling table | 8,935 driver-race rows (2003–2024), 20 leakage-safe features in 5 groups, 14.4 % podiums |
| Split | Temporal: train 2003–2018, validation 2019–2021, test 2022–2024 |
| Selected model | Random forest (max depth 6) — test PR-AUC 0.709, ROC-AUC 0.939, F1 0.683 |
| Baseline (top 3 on the grid) | Test PR-AUC 0.647 |
| Q1 front-row conversion | Best in 2014–2024: Suzuka 89 %, Monaco 85 %; ranking changes between eras (Spearman 0.45) |
| Q2 home advantage | None after controlling for grid position (odds ratio 0.92, 95 % CI 0.78–1.08) |
| Q3 mechanical retirements | 9.2 % of starts in 2014–2021 vs 6.0 % in 2022–2024 |

Feature importance describes what the model relies on, not causal effects.
