# Predicting Energy Consumption
![Firefly Predict Energy Behavior of Prosumers](https://github.com/RezaDelvari/energyconsumptionrepo/assets/150558004/6b947431-8347-4b31-9d6d-5d7a424ccd99)
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
# Overview
The goal is to create an energy prediction model of prosumers to reduce energy imbalance costs.
This competition aims to tackle the issue of energy imbalance, a situation where the energy expected to be used doesn't line up with the actual energy used or produced. Prosumers, who both consume and generate energy, contribute a large part of the energy imbalance. Despite being only a small part of all consumers, their unpredictable energy use causes logistical and financial problems for the energy companies.
## Business Understanding
The number of prosumers is rapidly increasing, and solving the problems of energy imbalance and their rising costs is vital. If left unaddressed, this could lead to increased operational costs, potential grid instability, and inefficient use of energy resources. If this problem were effectively solved, it would significantly reduce the imbalance costs, improve the reliability of the grid, and make the integration of prosumers into the energy system more efficient and sustainable. Moreover, it could potentially incentivize more consumers to become prosumers, knowing that their energy behavior can be adequately managed, thus promoting renewable energy production and use.
Enefit is one of the biggest energy companies in Baltic region. As experts in the field of energy, we help customers plan their green journey in a personal and flexible manner as well as implement it by using environmentally friendly energy solutions.
At present, Enefit is attempting to solve the imbalance problem by developing internal predictive models and relying on third-party forecasts. However, these methods have proven to be insufficient due to their low accuracy in forecasting the energy behavior of prosumers. The shortcomings of these current methods lie in their inability to accurately account for the wide range of variables that influence prosumer behavior, leading to high imbalance costs. By opening up the challenge to the world's best data scientists through the Kaggle platform, Enefit aims to leverage a broader pool of expertise and novel approaches to improve the accuracy of these predictions and consequently reduce the imbalance and associated costs.
## What do we need to predict?
For each county we need to make predicitons of consumption or production of electricity. For each county we need to make prediction for several subgroups is_business(True/False), is_consumption(True/False), product_type(0, 1, 2, 3).

### 3. Functions
- `preprocess_data`: Function for preparing and pre-processing various datasets for training a machine learning model.
- `create_revealed_targets_train`: Function to create lagged target values for a given dataset.
- `get_agg_target_lag`: Function to aggregate lagged target values in a DataFrame and compute various statistics.

## Instructions

### Running the Code
1. Ensure you have the required Python packages installed. You can install them using `pip install -r requirements.txt`.
2. Open the `energy_prediction.ipynb` notebook and run the code cells sequentially.

### Data
- Place the dataset files in the specified folder structure.
- Modify file paths in the code if your data is stored in a different location.

### Model Training
- Two models are trained: Model 1 for main predictions and Model 2 for production targets.
- Model parameters are specified in the notebook, allowing for customization based on specific requirements.

## Results
- Model performance metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared are provided for both trained models.
- Visualizations of feature importances are included, offering insights into the key factors influencing energy consumption predictions.

## Additional Notes
- This project includes sin and cosine transformations for temporal features, log transformations for specific columns, and the creation of lagged target values to capture temporal dependencies.

## Future Enhancements
- Discuss potential future enhancements or features that could be added to improve the model or extend its capabilities.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
