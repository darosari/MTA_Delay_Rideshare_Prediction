# MTA Delay & Rideshare Demand Prediction

This data science project applies **machine learning** to model and predict **rideshare demand in New York City** based on **MTA subway delay patterns**. It was developed as a collaborative group assignment for a graduate-level course in data mining and analytics.

---

## Problem Statement
Urban mobility in NYC relies heavily on public transportation. But when the subway system experiences delays, do more people turn to rideshare services like Uber and Lyft?

**Goal:** Use NYC MTA delay data to predict daily rideshare counts and understand how transit disruptions affect alternative transportation demand.

---

## Project Milestones & Key Files

### Checkpoint 1 — [Project Proposal](./files/Project_Proposal.pdf)
- Business use case & motivation
- Overview of problem and ML applicability
- Dataset(s) description
- Proposed modeling approach

### Checkpoint 2 — [EDA & Data Cleaning](./files/checkpoint_2_update.ipynb)
- Exploratory data analysis (EDA)
- Delay category breakdowns
- Data preprocessing & feature engineering
- Missing value strategies

### Checkpoint 3 — [Initial Modeling](./files/MTA_delays_inital_modeling.ipynb)
- Regression models:
  - Linear Regression
  - Random Forest
  - XGBoost
- Evaluation metrics: RMSE, R²
- Feature importance analysis

### Final Analysis — [Refined EDA & Modeling](./files/MTA_delays_EDA.ipynb)
- Streamlined visuals
- Residual analysis
- Prediction-vs-actual plots
- Strongest predictors revealed

---

## Methodology Summary
- **Data Source:** MTA Subway Delays (2020–2025)
- **Target Variable:** Daily rideshare trip counts
- **Features Engineered:**
  - Total delays
  - Delay types (e.g. mechanical, weather)
  - Time of day, borough, holiday flags
- **Models Used:**
  - Linear Regression
  - Random Forest Regressor
  - XGBoost Regressor

---

## Repository Structure
| Folder/File | Description |
|-------------|-------------|
| [`/files`](./files) | All notebooks, datasets, proposal, and final report |
| [`/screenshots`](./screenshots) | Visual output from EDA and modeling stages |
| [`README.md`](./README.md) | You're reading it! |

---

## Project Visuals
| Screenshot | Description |
|----------------|----------------|
| ![](screenshots/sub_delays_v_rideshare_count.png) | Subway delays vs rideshare activity |
| ![](screenshots/xgboost_feature_importants.png) | Top predictors (XGBoost) |
| ![](screenshots/predictionsvactual.png) | Predicted vs Actual comparison |
| ![](screenshots/distribution_of_residuals.png) | Model residuals distribution |
| ![](screenshots/aVp_overtime.png) | Rideshare usage over time |
| ![](screenshots/707_barchart.png) | Delay categories by frequency |

---

## Collaborators
This was a collaborative team effort by:
- **Dawryn Rosario** — [@darosari](https://github.com/darosari) *(Data cleaning, regression modeling, EDA, repository setup)*
- **Rianne Parker** — [@datawitparker](https://github.com/datawitparker) *(Feature engineering, XGBoost, proposal author)*
- **Marko ** — [@data11y](https://github.com/data11y) *(Data collection, visualization, documentation)*

---

## Final Thoughts
- 🔄 Demonstrates how public data can inform real-world transportation planning
- 📉 Tackles challenges in temporal regression and data quality
- ⚙️ Clean and reproducible code for further experimentation or city-specific analysis

---

**Explore Notebooks:** Just click on any linked file to dive into the code!

**Star this repo** if you found it insightful.
