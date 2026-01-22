# NBA All‑Star Prediction (ML + Automated Data Collection)

An end‑to‑end machine learning project that predicts whether an NBA player will be selected as an **All‑Star** in a given season, based on season‑level statistics.
A core part of the project is an **automated crawling/scraping pipeline** that collects player‑season data and builds the modeling dataset.

## Highlights
- **Automated data collection** (crawling notebook) → reproducible dataset creation
- **Feature engineering & cleaning** (handling missing values, scaling/encoding as needed)
- **Classification modeling** (compare multiple ML models)
- **Interpretation & reporting** (final report + clear legend/data dictionary for all abbreviations)

## Repository contents
- **Data collection (crawling):** `notebooks/01_data_collection_crawling.ipynb`  
  Collects player‑season statistics automatically and produces a structured table for analysis/modeling.
- **Modeling & evaluation:** `notebooks/02_modeling_allstar_prediction.ipynb`  
  EDA, feature engineering, training, evaluation, and conclusions.
- **Legend / data dictionary:** `docs/legend.md`  
  Explains dataset columns (e.g., PTS, AST, REB, FG_PCT, etc.).
- **Project documents:**
  - `docs/assignment.pdf` (task description / course document)
  - `report/final_report.pdf` (full write‑up with tables and results)

## Problem statement
Given a player’s season statistics, predict the binary label:
- `All_Star = 1` if the player was selected as an All‑Star that season
- `All_Star = 0` otherwise

## Data
The dataset is built automatically by the crawling pipeline and typically includes:
- player identifiers & metadata (e.g., `PLAYER_ID`, `SEASON_ID`, `TEAM_ABBREVIATION`, `PLAYER_AGE`)
- performance stats (e.g., `PTS`, `AST`, `REB`, `FG_PCT`, `FG3_PCT`, `FT_PCT`, `STL`, `BLK`, `TOV`, etc.)
- the target label: `All_Star`

See `docs/legend.md` for the full column list and definitions.

## Approach
### 1) Data collection (crawling)
- Automatically fetches player‑season data from the chosen public source(s)
- Normalizes/merges tables into a single dataset
- Includes “polite” crawling behavior (rate limiting / retries) where relevant

### 2) Modeling
Typical steps in the modeling notebook:
- EDA and sanity checks (missing values, distributions, correlations)
- Feature engineering (as needed)
- Train/validation split strategy
- Model comparison (e.g., Logistic Regression, tree‑based models, SVM, etc.)
- Evaluation with classification metrics (e.g., precision/recall/F1, ROC‑AUC)

## How to run (optional)
> If you only want to review the work, the notebooks and report are enough. Running locally is optional.

1) Install dependencies:
```bash
pip install -r requirements.txt
```

2) Run notebooks in order:
- `notebooks/01_data_collection_crawling.ipynb`
- `notebooks/02_modeling_allstar_prediction.ipynb`

## Notes
- If the source website/API changes, crawling code may require minor updates (selectors/endpoints).
- If you prefer not to store the generated dataset in GitHub, export it locally and add `data/` to `.gitignore`.

## Project report
A full write‑up with methodology, results, and conclusions is available in:
- `report/final_report.pdf`

## Next improvements
- Package crawling + preprocessing into Python modules/scripts for easier reruns
- Add model interpretability (feature importance / SHAP) and error analysis
- Add unit tests for data parsing and preprocessing steps
