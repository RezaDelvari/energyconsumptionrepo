# Predicting Energy Consumption
## Project Proposal 
### The Problem Area
* Develop accurate predictive models for estimating the amount of electricity consumed and produced by prosumers (who both consume and generate energy) with solar panels.
* Explore correlations between energy prices, weather conditions, and the amount of electricity consumed or produced.
* Compare and analyze the energy consumption and production patterns of business and residential prosumers.
### The User
Prosumers, both residential and business entities, experience the challenges of optimizing their energy consumption and production.
### The Big Idea
By leveraging historical data, weather forecasts, and energy pricing information, we can build predictive models that enable prosumers to anticipate their energy needs. In the project's feature engineering phase, we aim to boost model performance by creating relevant features from existing datasets, incorporating time-related variables, and capturing temporal patterns through aggregation and lag features. Moving to model selection and development, our strategy involves choosing appropriate time-series forecasting models like ARIMA, SARIMA, and Prophet, alongside exploring advanced techniques such as machine learning ensemble models and potentially deep learning. This iterative process aims to find the optimal approach for accurately estimating prosumer electricity consumption and production.
### The Impact
* **Enhanced Energy Efficiency**: The project anticipates improving energy efficiency for prosumers through accurate forecasting, aiding in optimal energy consumption and production.
* **Potential Cost Savings**: Prosumers stand to benefit from potential cost savings resulting from optimized energy usage, informed by precise predictive models.
* **Positive Environmental**: By optimizing the use of solar energy, the project aims to contribute to a positive environmental effect, potentially reducing overall carbon emissions.
## The Data
[Predict Energy Behavior of Prosumers](https://www.kaggle.com/competitions/predict-energy-behavior-of-prosumers/data)

***Gathered from Estonia***
### Electricity Consumption and Production Data
Dataset: **train.csv**
Description: Contains information on prosumer electricity consumption and production, including datetime, county, product type, and whether the entry represents consumption or production.
### Gas Prices and Electricity Prices Data
Datasets: **gas_prices.csv, electricity_prices.csv**
Description: Includes data on gas prices and electricity prices, providing insights into market dynamics that influence prosumer behavior.
### Prosumer Characteristics Data
Dataset: **client.csv**
Description: Contains information on prosumer characteristics such as product type, county, installed capacity, and whether the prosumer is a business.
### Weather Data
Datasets: **forecast_weather.csv, historical_weather.csv**
Description: Offers weather-related variables, including temperature, wind speed, and solar radiation, crucial for understanding the impact of weather on energy production.
