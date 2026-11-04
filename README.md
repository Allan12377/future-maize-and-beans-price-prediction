# BCS 3101 Capstone Project
## Predicting Future Monthly Retail Prices of Maize and Beans in Selected Ugandan Markets

NAME	REG. NO
AYEN GEOFFREY ALEXANDER	2024/A/KCS/5102/G/F  
KYOSHABIRE DIANAH	2024/A/KCS/5188/G/F  
ARINDA ELIZABETH	2024/A/KCS/3099/G/F  
KUKUNDAKWE SAVIOUS	2024/A/KCS/4333/F  
GUMISIRIZA AMBROSE	2024/A/KCS/3143/F  
AINEBYONA ALLAN	2024/A/KCS/1670/F  
NIYONSHUTI MERCY	2025/A/KCS/6117/F  

**Programme:** Bachelor of Computer Science, Year 3 Semester 1  
**University:** Kabale University  
**Course:** BCS 3101 – Basics of Machine Learning / Capstone  

**Date:** November 2026  

---

## Project Goal
Predict the monthly retail price (UGX per kg) of maize and of beans in major Ugandan markets for the next 2–5 years using historical observed prices from the World Food Programme (WFP).

This is a complete re-work from scratch. Every issue raised by the lecturer has been corrected.

## Notebooks (run in this order)

| # | Notebook | What it does |
|---|----------|--------------|
| 01 | Data Loading and Inspection | Load the WFP CSV, check shape, types, date range, record the source |
| 02 | Data Exploration and Cleaning | Keep only Retail Maize & Beans, select 9 major markets, remove duplicates, create clean panel |
| 03 | Feature Engineering and EDA | Create lag features (only past values), yearly trends, correlations |
| 04 | Preprocessing and Train/Test Split | Define feature lists, drop missing lags, **date-based split** (train ≤ 2022, test ≥ 2023) |
| 05 | Model Training and Evaluation | Train 4 models + last-month baseline, compare with MAE in UGX |
| 06 | Model Selection, Saving and Reload | Save full pipelines, reload and prove they work |
| 07 | Future Forecasting 2 to 5 Years | Recursive forecasts up to 2031, save CSV |

Each notebook explains **why** the step is needed, shows the code with comments, and explains the results.

## Key Corrections Made

- Random split → strict date split  
- Leakage features → only lag-1 to lag-12 of past prices  
- No baseline → last-month baseline reported  
- Inflated R² → primary metric is MAE in UGX  
- Missing Pipeline → full scikit-learn Pipeline saved  
- No future forecast → 5-year recursive forecast included  

## How to Run
1. Open Jupyter in the `notebooks/` folder.
2. Run the notebooks in order 01 → 07 (Kernel → Restart & Run All for each).
3. All intermediate CSVs, models and predictions are already generated and saved.

## Main Results (Forward Test 2023–2026)
- Maize last-month baseline MAE ≈ 131 UGX  
- Best maize model (Ridge) MAE ≈ 144 UGX  
- Beans last-month baseline MAE ≈ 288 UGX  
- Best beans model (Ridge) MAE ≈ 324 UGX  

## Files Produced
- `data/cleaned/` and `data/processed/` – all intermediate tables  
- `models/best_maize_pipeline.joblib` and `best_beans_pipeline.joblib`  
- `predictions/future_forecast_2026_2031.csv` – the 5-year forecasts  
