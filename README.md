# ❄️ F3 Innovate Frost Risk Forecasting Challenge  
## Team **Tyler and Aziz**

Welcome to the repository for our submission to the **F3 Innovate Frost Risk Forecasting Challenge**.  
Our goal is to build a **probabilistic frost-risk forecasting pipeline** for California specialty crop regions using CIMIS weather station data.

We forecast **frost occurrence and temperature** at multiple lead times and evaluate how well the model generalizes to **new locations and new frost seasons**.

---

## 📁 Repository Structure

```bash
├── data/                          # Cleaned & engineered datasets (CIMIS + optional reanalysis)
├── figures/                       # All plots and visualizations used in the report
├── notebooks/
│   ├── 01_exploration.ipynb       # EDA and basic time-series analysis
│   ├── 02_feature_engineering.ipynb # Lagged features, diurnal/seasonal features, targets
│   ├── 03_modeling_LOSO.ipynb     # Main modeling + LOSO evaluation pipeline
│   └── 04_calibration_plots.ipynb # Reliability diagrams, ECE, PR/ROC curves
├── src/
│   ├── data_utils.py              # Loading, cleaning, and station-wise splitting
│   ├── features.py                # Feature engineering helpers
│   ├── models.py                  # Model wrappers and training routines
│   └── evaluation.py              # Metrics, LOSO loops, plotting utilities
├── requirements.txt               # Python dependencies
├── README.md                      # This file
└── report/
    └── F3_frost_report.pdf        # Final PDF report (answers Q1–Q4)
```

## 🧰 Environment Setup
```
conda create -n frost python=3.10
conda activate frost
pip install -r requirements.txt
```

## 🌡️ Problem Overview
For each CIMIS station and each hour, we aim to forecast:
**Whether frost will occur**
**Probability that temperature < 0°C**
**Seasonal frost patterns** (useful for long-term planning)
**Hourly frost variability** at specific stations
The goal is to create **actionable, interpretable** frost forecasts useful for growers statewide.

## 🚀 Pipeline Overview
1. **Prepoccesing**
Cleaned the CIMIS dataset, handled missing values, engineered new features, applied cyclical encoding, and standardized all predictors.
3. **Feature Selection**
Selected the most relevant weather and derived variables for frost prediction while checking for multicollinearity.
4. **Train–Test Split**
Used LOSO (Use on station out) four test/train split
5. **Model Training**
Trained the classification model using the processed weather features to predict frost events.
6. **Hyperparameter Tuning**
Optimized model parameters using cross-validation to improve performance and reduce overfitting.
7. **Model Evaluation**
Evaluated performance using accuracy, precision, recall, F1-score, and probabilistic calibration metrics.
8. **Unseen Station Testing**
Tested the trained model on the station that was not included during training to assess real-world generalization.
9. **Probabilistic Forecasting**
Generated frost probability predictions to support real-world decision making.
## 🔧 Preprocessing Steps
1. Loaded the full CIMIS daily weather dataset.
2. Added month, year, and day columns for time tracking.
3. Created frost labels aligned with daily weather observations.
4. Checked for missing values across all variables.
5. Examined correlations between weather variables.
8. Engineered new features for early frost detection:
   - Dewpoint depression (air temperature – dewpoint)
   - Short-term cooling rate (temperature change over time)
   - Calm-wind indicator (wind speed < 1 m/s)
   - Vapor pressure deficit (VPD)
   - Applied sine and cosine encoding to:
         Month (to preserve seasonality)
         Wind direction (to preserve circular direction)
9. Standardized all continuous predictor variables.

## 🧠 Modeling Strategy
- Random Forest
- Tuned XGB Boost Classifer

## 📊 Performance Summary


## 📈 Key Visuals & Insights



## 📄 Project Report


## 
