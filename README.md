# PM2.5 Air Pollution Forecasting using Time Series Models
### Urban Microclimate Analysis — Bengaluru & Delhi

---

## Overview

This project forecasts PM2.5 air pollution levels across two Indian cities — Bengaluru and Delhi — using historical urban microclimate data. Three time series models (ARIMA, Prophet, and LSTM) were built and compared to identify the best-performing approach for air quality prediction.

---

## Dataset

- **Source:** Kaggle — Urban Microclimate Dataset (Bengaluru & Delhi)
- **File:** `urban micro climate blr_delhi.xlsx`
- **Size:** 29,040 rows × 55 columns
- **Time Period:** August 2022 – November 2025
- **Features include:** Temperature, Humidity, Wind Speed, Precipitation, Solar Radiation, Cloud Cover, PM2.5, PM10, CO, NO2, SO2, O3, AQI (US & EU standards), Season, Time of Day, Festival Period, Crop Burning Season, and more.

> ⚠️ Dataset not included in this repo due to file size. Download from Kaggle and place it in the working directory.

---

## Project Structure

```
pm25-air-pollution-forecasting/
├── pm25_air_pollution_forecasting.ipynb   # Main notebook (end-to-end)
└── README.md
```

---

## What Was Done

### 1. Data Loading & Exploration
- Loaded the Excel dataset with 29,040 hourly records across 55 features
- Explored shape, data types, and descriptive statistics

### 2. Data Cleaning
- Filled missing AQI values (US & EU) using median imputation
- Dropped rows with missing `AQI_Category` (~151 rows)
- Achieved a fully clean dataset with zero null values

### 3. Exploratory Data Analysis (EDA)
- **City comparison:** Delhi's average PM2.5 (~72.4 µg/m³) was ~3.5x higher than Bengaluru (~20.9 µg/m³)
- **Time of day:** Night and late-night hours had the highest PM2.5 levels
- **Seasonal trends:** Winter had the worst air quality (avg ~64.7 µg/m³), Monsoon the best (~30.3 µg/m³)
- **Weekday vs Weekend:** No significant difference in PM2.5 levels
- **Correlation:** PM2.5 had a moderate negative correlation with temperature (-0.26)

### 4. Time Series Preparation
- Converted `Datetime` to datetime index
- Confirmed stationarity using the **ADF Test** (p-value ≈ 7.77e-13 ✅)
- Split data: **80% train / 20% test**

### 5. Model Training

| Model | Description |
|-------|-------------|
| **ARIMA(1,0,1)** | Classical statistical time series model |
| **Prophet** | Facebook's forecasting model with trend & seasonality |
| **LSTM** | Deep learning model with sequence length of 10, 50 units, 5 epochs |

---

## Results

| Model | RMSE |
|-------|------|
| ARIMA | 37.47 |
| Prophet | 37.27 |
| **LSTM** | **31.54** ✅ |

**LSTM achieved the best performance**, with the lowest RMSE of 31.54, demonstrating its ability to capture complex temporal patterns in air quality data.

---

## How to Run

1. Open the notebook in Google Colab or Jupyter Notebook
2. Download the dataset from Kaggle and upload it to your environment
3. Run all cells from top to bottom

### Requirements
```
pandas
numpy
matplotlib
statsmodels
prophet
tensorflow / keras
scikit-learn
```

---

## Key Findings

- Delhi's air pollution is significantly worse than Bengaluru's, especially during Post-Monsoon and Winter seasons
- PM2.5 peaks at night, likely due to reduced atmospheric mixing and traffic patterns
- LSTM outperforms classical models (ARIMA, Prophet) for this dataset, suggesting non-linear temporal dependencies in pollution data
- Crop burning season is a notable contributing factor to elevated PM2.5 in Delhi

---

## Author

**Vinathi R Khadilkar**  
Connect on [GitHub](https://github.com/VinathiRKhadilkar33)
