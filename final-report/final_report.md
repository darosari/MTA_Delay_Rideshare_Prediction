### Title - Forecasting NYC Rideshare Demand Using MTA Delays, Weather, and Ridership Data

### Team
Marko Masnikosa: mmasniko@syr.edu 
- GitHub: https://github.com/data11y - POC <br>

Dawryn Rosario: darosari@syr.edu
- GitHub: https://github.com/darosari

Rianne Parker: riparker@syr.edu
- GitHub: https://github.com/DatawithParker

### Introduction 

The purpose of this project is to develop a machine learning model that predicts hourly rideshare demand in New York City using a combination of subway delay data, daily ridership figures, and weather conditions. By capturing how public transportation disruptions and environmental factors influence commuter behavior, this model aims to support more informed decision-making for key stakeholders in the urban mobility ecosystem.

The approach integrates multiple datasets—including subway activity, weather data, and rideshare price fluctuations—to build predictive models using supervised learning techniques such as regression and classification. 
- **Model Options**: Clustering, Regression, Classification (Supervised Learning) 
- **Significance**: This model will estimate rideshare prices using external factors that are often overlooked, providing price forecasts and alternative transportation options for users. 

## Who Cares? 
- **Rideshare Companies**: They can optimize surge pricing strategies based on external transportation conditions. 
- **NYC Residents**: Users can plan rides better, avoiding high surge prices based on predicted conditions. 
- **Transportation Authorities**: Insights into the correlation between subway delays and increased reliance on rideshare services.

The primary stakeholder for this project is the New York City Department of Transportation (NYC DOT), whose responsibility includes overseeing and optimizing the city's transportation infrastructure. For NYC DOT, being able to anticipate spikes in rideshare usage—especially during subway service interruptions—can aid in traffic management, planning alternate routes, deploying transit resources, and understanding strain on the system during peak disruption periods. A secondary stakeholder includes rideshare companies, who can use demand forecasts to optimize pricing, fleet distribution, and driver availability.

The need being addressed is the lack of an integrated predictive system that accounts for real-time disruptions in public transit and their downstream effects on rideshare systems. While transit authorities typically monitor subway performance and ridership internally, this data is rarely leveraged alongside rideshare and weather data to anticipate shifting travel behaviors. The absence of this capability creates a blind spot in operational planning and service coordination across modes of transportation.

**My part** in the project was to create a supervised machine learning model—specifically, an XGBoost Regressor—that predicts hourly rideshare demand using engineered features derived from subway delays, ridership totals, and hourly weather data. This approach provides a data-driven method for understanding how disruptions in one part of the transportation network ripple outward to influence other services. While the current model does not include real-time prediction or deployment, it serves as an incremental step toward a multimodal, responsive system for urban mobility forecasting.

---

## Literature Review

The stakeholder need identified in this project is the ability to forecast changes in rideshare demand in response to subway service disruptions and adverse weather conditions. For agencies like the NYC Department of Transportation and MTA, having such a forecasting tool would support better congestion management, resource allocation, and commuter communication strategies. Similarly, rideshare companies benefit from understanding when and why demand increases to manage driver availability and dynamic pricing more effectively.

Prior research in transportation analytics has demonstrated that transit reliability, weather events, and time-of-day patterns are all significant drivers of urban travel behavior. Studies have shown that subway delays often lead to increased demand for alternative modes of transportation, including rideshare services. At the same time, inclement weather—such as rain or snow—has been found to suppress walking and biking while pushing commuters toward enclosed or private transport options. While prior work has analyzed MTA ridership data or TLC trip records independently, there is limited research combining these sources in a unified model to forecast rideshare demand. This project addresses that gap by integrating three publicly available datasets—subway delays, weather data, and trip-level rideshare information—into a predictive modeling pipeline. The use of XGBoost was informed by its success in similar transportation prediction tasks, particularly those involving structured, tabular data with a mix of numerical and categorical features. Its ability to handle feature importance analysis also made it well suited for understanding which variables contribute most to demand shifts.

Although the exact problem of predicting hourly rideshare demand using MTA delay data has not been widely studied, this work aligns with and builds on existing methods in smart mobility research, urban resilience planning, and multimodal transport modeling.

---

## Data and Methods

#### Data

The dataset used in this project was created by integrating three primary data sources: hourly rideshare trip data from the New York City Taxi and Limousine Commission (TLC), hourly weather reports from publicly available meteorological datasets, and subway delay and ridership information from the Metropolitan Transportation Authority (MTA). These sources are widely regarded as reliable and are commonly used in urban mobility research and government reporting. All data processing steps were completed using the following notebooks:

- [`TLC_data_gathering.ipynb`](TLC_data_gathering.ipynb): collected and structured hourly rideshare trip data (Marko's Dataset)

- [`MTA Daily Ridership_data_processed.ipynb`](MTA%20Daily%20Ridership_data_processed.ipynb): cleaned and aggregated subway delay reports and station-level ridership figures
- [`MTA_delays_EDA.ipynb`](MTA_delays_EDA.ipynb): conducted exploratory data analysis across all datasets


Missing values were handled using a combination of forward-fill imputation for time series consistency and mean substitution for sparse features. Categorical variables were encoded using one-hot encoding to ensure compatibility with the model. Based on initial visualizations and summary statistics, the dataset appeared relatively balanced in terms of temporal coverage and feature variability.

To help contextualize the data, I created several visualizations, including:

- **Delay Reports Over Time**  
  ![MTA Delay Reports Per Year](MTA_delays_per_year.png)

- **Subway Delays vs. Rideshare Demand**  
  ![Delays vs Rideshare Demand](sub_delays_v_rideshare_count.png)

These plots demonstrate key patterns in the data and reinforce the hypothesis that subway performance impacts rideshare demand.
---

#### Methods

The modeling portion of this project was completed in [`MTA_delays_inital_modeling.ipynb`](MTA_delays_inital_modeling.ipynb). The prediction task was framed as a supervised regression problem, where the target variable was `trip_count`—representing the number of hourly Uber rides. The goal was to predict this variable using weather, transit, and trip-level features.

The modeling pipeline involved the following steps:
1. Splitting the dataset into training and testing sets using an 80/20 ratio
2. Standardizing continuous features using z-score normalization
3. Encoding categorical features through one-hot encoding
4. Initial experimentation with baseline models including Linear Regression and Decision Trees

While these simpler models were useful for benchmarking, they underperformed in both accuracy and generalization. I ultimately selected the **XGBoost Regressor** as the final model due to its ability to capture non-linear relationships and its robustness to overfitting on tabular data. The XGBoost model also enabled post-hoc interpretability via feature importance scoring, which was useful in evaluating which variables had the most impact on demand.

Hyperparameters such as `max_depth`, `learning_rate`, and `n_estimators` were tuned using grid search to optimize model performance. Throughout_


---

## Results

The final model produced the following outcomes:

**Actual vs Predicted Over Time**  
![Actual vs Predicted Trip Count Over Time](aVp_overtime.png)

**Residual Distribution (Error Spread)**  
![Distribution of Residuals](distribution_of_residuals.png)

**Predicted vs Actual Scatterplot**  
![XGBoost Predictions vs. Actuals](predictionsvactual.png)

**Top Feature Importances (XGBoost)**  
![XGBoost Feature Importances](xgboost_feature_importants.png)

### 📉 Model Performance
- RMSE ≈ **1588.20**
- Strong linear correlation between actual and predicted values
- Most influential variable: `service_uber`, followed by `trip_miles_mean` and `trip_time_mean`
- Subway delay counts had moderate predictive value but improved accuracy when included

---

## Discussion

Overall, the model did a solid job predicting hourly rideshare demand using subway delays, ridership, and weather data. I trained an XGBoost Regressor, and it ended up with an RMSE of around 1588. That’s not perfect, but given the range of trip counts and the natural variance in demand, it's a reasonable error. The model picked up on some key patterns — like when subway delays increased during peak hours, there was usually a noticeable spike in Uber demand. That tells me the model is learning something meaningful from the data, not just noise.

From a stakeholder perspective, this hits on an important need: NYC DOT and MTA want to better understand how service disruptions impact commuter behavior. Being able to forecast these demand shifts—even with moderate accuracy—can help them plan ahead for congestion, resource deployment, or public advisories. Rideshare companies could also use this type of model to adjust pricing or driver distribution in real time, especially when things like delays or bad weather are expected.

That said, the model isn’t perfect. It struggled more on weekends and holidays, probably because there's more randomness in travel behavior on those days. Also, some of the weather data was kind of sparse or incomplete in certain windows, so that might’ve affected feature strength. And right now, the model’s using historical data — it’s not plugged into any kind of real-time pipeline, which limits how useful it would be in an actual live setting.

Still, I’d say this project gets us closer to a system that can actually help people make smarter transportation decisions using cross-system data. It’s a good starting point, and it shows that combining datasets like TLC trips, subway delays, and weather does improve predictive power.

---

## Limitations
Some of the limitations in my work include:
- **No real-time delay resolution** — delays are aggregated daily, but real-world users respond to delays in real time.
- **Imbalanced observations** — some service types (e.g., Uber vs Lyft) dominate the dataset.
- **Feature sparsity** — some weather condition variables were sparse or inconsistently reported.

If I had more time, I would also experiment with deep learning architectures and real-time streaming features.

---
### Future Work

If I had more time, there are a few key areas I’d focus on to take this project to the next level. 

1. I’d work on building a real-time pipeline so the model could actually take in live subway delay feeds and weather updates, instead of just using historical data. That would make the predictions way more actionable for stakeholders like NYC DOT or rideshare platforms.

2. I’d spend more time engineering features around event-based activity — like holidays, parades, sports games, etc. Right now, the model doesn’t know when the Knicks are playing or if it’s Thanksgiving weekend, and those kinds of things can really change travel behavior.

3. I’d also want to explore deeper location-based insights. Since the TLC data has pickup and dropoff info, there's a lot of potential to build geospatial models that predict demand by neighborhood or even by block. That could be useful for dynamic dispatching or even informing MTA where delays are hitting riders the hardest.

4. I’d experiment with more complex modeling approaches, like neural networks or time series-specific architectures (LSTM, Temporal Fusion Transformer, etc.). XGBoost worked well, but there’s probably more performance to squeeze out with the right setup and more compute.

Overall, there’s a lot of room to expand this into something that’s not just a school project, but an actual tool that could help manage mobility in NYC.

