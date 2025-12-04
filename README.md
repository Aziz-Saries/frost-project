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
    └── F3_frost_report.pdf        # Final PDF report (answers Q1–Q4, optional Q5)

---

##🧰 Environment Setup
conda create -n frost python=3.10
conda activate frost
pip install -r requirements.txt

##🌡️ Problem Overview
For each CIMIS station and each hour, we aim to forecast:
**Whether frost will occur**
**Probability that temperature < 0°C**
**Seasonal frost patterns** (useful for long-term planning)
**Hourly frost variability** at specific stations
The goal is to create **actionable, interpretable** frost forecasts useful for growers statewide.
