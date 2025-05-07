# Project Proposal

## Title: Predicting NYC Rideshare Prices Using Subway Delays, Ridership, and Weather Conditions 
 
## Team 
 
- Rianne Parker (@DatawithParker) 
- Marko Masnikosa (@data11y)  - owner of repository 
- Darwyn Rosario (@darosari) 
 
# Introduction 
 
## Objective 
The goal of this project is to develop a predictive model for NYC rideshare (Uber) prices using subway delays, ridership, and weather conditions. This will enable stakeholders to understand price fluctuations and make informed decisions. 
 
## New Approach 
Our approach integrates multiple datasets—including subway activity, weather data, and rideshare price fluctuations—to build predictive models using supervised learning techniques such as regression and classification. 
- **Model Options**: Clustering, Regression, Classification (Supervised Learning) 
- **Significance**: This model will estimate rideshare prices using external factors that are often overlooked, providing price forecasts and alternative transportation options for users. 
 
## Who Cares? 
- **Rideshare Companies**: They can optimize surge pricing strategies based on external transportation conditions. 
- **NYC Residents**: Users can plan rides better, avoiding high surge prices based on predicted conditions. 
- **Transportation Authorities**: Insights into the correlation between subway delays and increased reliance on rideshare services. 
 
# Literature Review 
 
## Related Work 
- Existing studies have integrated weather data with rideshare pricing, but few consider public transit as a key factor. 
- Key References: 
- Study on rideshare surge pricing and alternative transportation 
- Research on congestion pricing and demand elasticity 
- ML models predicting Uber/Lyft demand in urban settings 
- Impact of weather on transportation choices 
 
## Stakeholder Needs 
- **Riders**: Need accurate price predictions for better decision-making. 
- **Rideshare Platforms**: Seek to optimize pricing based on transit alternatives. 
- **City Planners**: Can use insights to improve transit reliability and pricing structures. 
 
## Feeback 
While integrating weather data with rideshare pricing is common, the impact of other transportation modes is often overlooked. We believe MTA subway delays significantly influence rideshare demand. Since surge pricing algorithms are proprietary, our approach aims to incorporate transit alternatives into predictive models, offering NYC residents insights into potential rideshare price fluctuations and alternative commuting options. 
 
# Data 
 
## MTA Delays 
- **Link**: https://data.ny.gov/Transportation/MTA-Subway-Trains-Delayed-Beginning-2020/wx2t-qtaz/about_data 
- **Description**:This dataset reflects the number and percentage of subway trains delayed per weekday based on scheduled service, broken down into specific delay categories.
- **Rows** = 40.5k
- **Columns** = 7 
- **Provenance**: Reliable government source with historical trends. 
- **Metadata Available** = Yes 
 
## MTA Ridership 
- **Link**: https://data.ny.gov/Transportation/MTA-Daily-Ridership-Data-2020-2025/vxuj-8kew/about_data 
- **Description**: Ridership and traffic estimates for subways (including the Staten Island Railway), buses, Long Island Rail Road, Metro-North Railroad, Access-A-Ride, and Bridges and Tunnels, beginning 3/1/2020, and provides a percentage comparison against a comparable pre-pandemic date. 
- **Rows** = 1,776 
- **Columns** = 15 
- **Provenance**: Reliable government source with historical trends 
- **Metadata Available** = Yes 
 
## Rideshare Price Data (Uber-NYC) 
- **Link**: https://www.kaggle.com/datasets/fivethirtyeight/uber-pickups-in-new-york-city 
- **Description**: This dataset is a Monthly report including weekly total dispatched trips and unique dispatched vehicles by base tabulated from FHV Trip Record submissions made by bases. The TLC publishes base trip record data as submitted by the bases.  
- **Rows** = 565,000 
- **Columns** = 4 
- **Provenance**: Sourced from Taxi and Limousine Commission (TLC) for NYC 
- **Metadata Available** = Yes 
 
## Other Sources: 
- **US EPA Weather Data**: https://www.epa.gov/hydrowq/meteorological-data-new-york 
- **NYC Weather Data**: https://www.kaggle.com/datasets/aadimator/nyc-weather-2016-to-2022 	 
- **NYC.gov Taxi and Limousine Commission data**: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page 
 
 
# Methods  
 
## Data collection 
- Combining data from different formats and sources 

## Data Preprocessing 
- Handle missing values via imputation  
- Removing outliers
- Potentially smoothing data with a moving average 
- Trend and seasonality handling 
- Normalize numerical features 
- Encode categorical variables (one-hot encoding) 

## Feature Engineering 
- Extract features like average delay impact on pricing 

## Model Selection 
- Apply supervised learning models (Regression, Classification) 
- Apply time series modeling such as ARIMAX 

## Evaluation 
- Split dataset (80/20 train-test) 
- Use cross-validation 
- Evaluate with RMSE/MAE (for regression) and accuracy (for classification) 

## Interpretability 
- Use visualizations to highlight key price influencers 
 
 
# Project Plan 
 
| Period        | Activity                                        | Milestone |
|--------------|------------------------------------------------|-----------------------------------------------|
| 2/6         | Establish Project Teams, Finalize Proposals    | Submit Project Proposals (Checkpoint 1)      |
| 2/12 - 2/25 | Stakeholder Analysis, Literature Review, Initial Dataset Assessment | Completed Stakeholder Analysis & Dataset Acquisition |
| 2/26 - 3/10 | Exploratory Data Analysis (EDA), Feature Engineering | Identified Key Trends & Derived New Features |
| 3/11 - 3/24 | Preprocessing & Data Cleaning                  | Data Formatted & Missing Values Handled      |
| 3/25 - 4/07 | Model Selection & Training                     | Initial Model Prototypes Tested; (Checkpoint 2) |
| 4/08 - 4/21 | Hyperparameter Tuning & Validation             | Model Performance Optimized                  |
| 4/22 - 5/05 | Model Interpretability & Documentation         | Insights Extracted & Final Report Drafted; Project Presentations (Checkpoint 3) |
| 5/06       | Final Report Submission                         | Completed Project Submission                 |

 
# Risks 
 
| Risk                         | Mitigation Strategy                                           |
|------------------------------|--------------------------------------------------------------|
| **Missing/Inconsistent Data**     | Apply imputation techniques, remove anomalies               |
| **Model Underperformance**       | Experiment with different algorithms & hyperparameter tuning |
| **Data Integration Challenges**  | Standardize formats before merging datasets                 |
| **Unforeseen Stakeholder Needs** | Stay flexible and adjust model based on insights           |
| **Computational Limitations**    | Use cloud resources if needed                               |

 
 


