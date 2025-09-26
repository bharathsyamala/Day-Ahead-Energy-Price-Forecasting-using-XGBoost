# Dutch [NL] Day Ahead Energy Price Forecasting using XGBoost (2015-2020)

This project builds a time series forecasting model using XGBoost to predict day-ahead electricity prices in the Netherlands. The model incorporates weather, load, and generation features, alongside engineered time-based and lag variables, and is evaluated using walk-forward cross-validation.


# Data Sources

Power system data: Open Power System Data (https://data.open-power-system-data.org/time_series/) (NL-specific: load, solar, wind — 2015 to 2020)
Price data: ENTSO-E day-ahead electricity prices (CSV files per year)


# Model Overview

Model: XGBRegressor (XGBoost)

Objective: reg:squarederror

Features:
- Forecasted load: NL_load_forecast_entsoe_transparency
- Actual generation: solar, offshore wind, onshore wind
- Price lags: 1, 2, and 3 quarters (~91 days)
- Time features: hour, day of week, month, etc.

Validation:
- 4-fold TimeSeriesSplit
- Each test set = ~3 months (91 days) with a 24-hour gap

Evaluation metrics:
- RMSE (Root Mean Squared Error)
- Clipped MAPE (Mean Absolute % Error)
- SMAPE (Symmetric MAPE)


# Example Output

Each fold outputs an interactive Plotly chart comparing actual vs predicted prices over time with error metrics in the title:
<img width="1101" height="360" alt="newplot (5)" src="https://github.com/user-attachments/assets/b1762ce0-40ff-491d-8485-743fcd0c3d95" />
More plots are shown directly in the notebook and can be saved if needed.


# Project Structure

.

├── NL_XGBoost.ipynb         # Main notebook

├── GUI_ENERGY_PRICES_*.csv  # ENTSO-E price data (year-wise)

├── NL_60min.csv             # Load and generation data (OPSD)

├── README.md                # This file

└── .gitignore               # Exclude temp files, data




