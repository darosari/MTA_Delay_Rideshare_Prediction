# Forecasting NYC Rideshare Demand Using MTA Delays, Weather, and Ridership Data

## Team
**Dawryn Rosario**  
darosari@syr.edu | [GitHub](https://github.com/darosari)

**Rianne Parker**  
riparker@syr.edu | [GitHub](https://github.com/datawitparker)

**Marko Masnikosa**  
mmasniko@syr.edu | [GitHub](https://github.com/data11y)

---

## Overview
This project builds a machine learning model to forecast hourly rideshare demand in NYC using a fusion of MTA subway delay records, daily ridership, and hourly weather data. The primary goal is to analyze how disruptions in public transportation affect shifts in commuter behavior toward rideshare services.

**Key Use Cases**:
- **Rideshare platforms**: Anticipate demand for better pricing/logistics.
- **City planners**: Predict congestion and improve service coverage.
- **NYC residents**: Gain insights into factors that drive rideshare spikes.

---

## Literature Context
Prior studies show that both transit reliability and weather influence urban mobility. While some models look at these factors individually, our approach combines them into one predictive system. Using XGBoost, we optimized both performance and interpretability, identifying the features most responsible for spikes in rideshare use.

---

## Data Sources
We utilized three primary datasets:
- **TLC Rideshare Data** (hourly Uber rides)
- **MTA Subway Delays** (daily delay summaries)
- **NOAA Weather Reports** (hourly local weather metrics)

**Preprocessing Techniques**:
- Time-based joins by date/hour
- One-hot encoding of categorical weather conditions
- Forward-fill and mean imputation for missing entries

### Notebooks
- `TLC_data_gathering.ipynb`  
- `MTA Daily Ridership_data_processed.ipynb`  
- `MTA_delays_EDA.ipynb`

---

## Modeling Approach

**Target**: `trip_count` (hourly Uber rides)  
**Model**: XGBoost Regressor (after testing Linear Regression and Decision Tree)

### Pipeline:
1. Data split (80/20 train-test)
2. Feature scaling
3. Hyperparameter tuning (`learning_rate`, `n_estimators`, `max_depth`)
4. Model evaluation using RMSE and residual analysis

---

## Visual Results

**Subway Delays vs. Rideshare Count**  
Shows a strong positive relationship between increased subway disruptions and higher Uber trip counts.  
![Subway Delays vs Rideshare Count](./pictures/sub_delays_v_rideshare_count.png)

**XGBoost Feature Importances**  
Highlights the dominant role of trip-specific features and subway delays.  
![XGBoost Feature Importances](./pictures/xgboost_feature_importants.png)

**Predicted vs. Actual Rideshare Volumes**  
Demonstrates strong predictive alignment with some expected variance.  
![Predicted vs Actual](./pictures/predictionsvactual.png)

**Residuals Distribution**  
Residuals are roughly normal, centered around zero—indicating low model bias.  
![Residuals](./pictures/distribution_of_residuals.png)

**Rideshare Volume Over Time**  
Capture of total hourly rides across the entire dataset.  
![Volume Over Time](./pictures/aVp_overtime.png)

**Annual MTA Delay Counts**  
Illustrates a consistent rise in annual subway delays from 2020 to 2024.  
![Delay Counts Per Year](./pictures/MTA_delays_per_year.png)

---

## Model Performance
- **RMSE**: 1588.2
- **Top Features**:
  - `service_uber`
  - `trip_miles_mean`
  - `trip_time_mean`
  - `total_delays`

---

## Project Structure
| Folder | Description |
|--------|-------------|
| `checkpoint1/` | Proposal & rubric |
| `checkpoint2/` | Local examples, rubric, and early models |
| `checkpoint3/` | Final checkpoint feedback |
| `Data Processing/mta_delays/` | All core data cleaning, EDA, and modeling notebooks |
| `final-report/` | Final writeup, rubric |
| `pictures/` | All visual outputs used in documentation |

---

## Key Insights
- Subway delays were a strong predictor of increased rideshare use.
- Weather, though less dominant, helped refine hourly predictions.
- The model remained interpretable and responsive across scenarios.

### Limitations
- Gaps in hourly weather reporting
- Lack of geospatial resolution
- Holiday/event impacts not fully captured

---

## Future Improvements
- Incorporate live APIs for real-time modeling
- Add geolocation analysis of delays and rides
- Integrate special events or holidays as dummy features
- Experiment with temporal models (e.g., LSTM)

---

## Contributor Roles
- **Dawryn Rosario** – EDA, modeling, data cleaning, GitHub setup
- **Rianne Parker** – Feature engineering, literature review, parameter tuning
- **Marko Masnikosa** – Data collection, charts, and documentation

---

This repository demonstrates how transportation, weather, and urban activity data can be merged to forecast rideshare demand. The approach balances reproducibility and insight, offering a launchpad for real-world implementation in smart city planning.
