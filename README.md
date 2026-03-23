# ARIMA Time Series Forecasting: Pakistan Rainfall & Flood Prediction

Applying SARIMA/SARIMAX time series forecasting to 116 years of Pakistan rainfall data to analyze monsoon patterns and evaluate early warning potential for extreme precipitation events.

**COMP 4581 - Algorithms for Data Science | Spring 2026**

---

## Overview

Pakistan experienced catastrophic monsoon floods in 2022 - over 30 million displaced, $30 billion in damages, roughly 10x normal rainfall. This project explores whether time series algorithms can learn from over a century of historical data to detect abnormal monsoon patterns.

Five models were compared across three datasets:
- **ARIMA(2,0,2)** - baseline, no seasonality
- **SARIMA(1,0,2)(1,1,1,12)** - captures 12-month monsoon cycle *(best performer)*
- **SARIMAX** - SARIMA + ENSO ocean temperature data
- **Historical Average** - naive baseline
- **Last Year Repeat** - naive baseline

## Key Results

| Model | RMSE (mm) | MAE (mm) |
|-------|-----------|----------|
| SARIMA(1,0,2)(1,1,1,12) | **14.06** | **10.98** |
| SARIMAX (+ ENSO) | 13.70 | 10.62 |
| Historical Average | 14.09 | 11.01 |
| ARIMA(2,0,2) | 16.64 | 13.48 |
| Last Year Repeat | 27.63 | 18.38 |

- SARIMA outperforms basic ARIMA by 15% (seasonal component is key)
- ENSO ocean temps confirm La Nina-rainfall correlation (r = -0.258) but only 0.1% RMSE improvement
- The model predicts ~57mm for July 2022 - actual was ~10x that. The confidence interval exceedance IS the early warning signal.

## Datasets

1. **Pakistan Rainfall (Kaggle)** - Monthly rainfall 1901-2016, 1,392 observations
2. **World Bank Climate Indicators** - Population, urbanization, forest cover 1960-2024
3. **NOAA Oceanic Nino Index (ONI)** - Sea surface temperature anomalies 1950-2017

## Repository Structure

```
├── Comp4581_FinalProject_NH.ipynb     # Main Jupyter notebook (code + analysis)
├── Comp4581_FinalProject_Writeup_NH.docx  # Project write-up
├── data/
│   ├── Rainfall_1901_2016_PAK.csv     # Primary rainfall dataset
│   ├── climate-change_pak.csv          # World Bank indicators
│   └── Monthly_Oceanic_Nino_Index__ONI__-_Long.csv  # NOAA ENSO data
├── figures/
│   ├── fig1_pakistan_context.png       # World Bank vulnerability indicators
│   ├── fig2_data_exploration.png      # 116-year rainfall overview
│   ├── fig3_acf_pacf.png             # ACF/PACF plots
│   ├── fig4_decomposition.png        # Time series decomposition
│   ├── fig5_evaluation.png           # Model predictions vs actual
│   ├── fig6_forecast.png             # SARIMA forecast with 2022 context
│   ├── fig7_monsoon.png              # Monsoon intensity analysis
│   ├── fig8_complexity.png           # Algorithm complexity
│   └── fig9_enso.png                 # ENSO correlation analysis
└── README.md
```

## How to Run

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/pakistan-rainfall-forecasting.git
cd pakistan-rainfall-forecasting

# Install dependencies
pip install pandas numpy matplotlib statsmodels scikit-learn

# Run the notebook
jupyter notebook Comp4581_FinalProject_NH.ipynb
```

Make sure the three CSV files are in the same directory as the notebook (or in a `data/` folder and update the paths).

## Tools & Libraries

- Python 3.10+
- pandas, numpy, matplotlib
- statsmodels (ARIMA, SARIMA, SARIMAX)
- scikit-learn (evaluation metrics)

## Author

**Namoos Haider** 
