# Predicting Energy Consumption
![Firefly Predict Energy Behavior of Prosumers](https://github.com/RezaDelvari/energyconsumptionrepo/assets/150558004/6b947431-8347-4b31-9d6d-5d7a424ccd99)
# Predict Energy Behavior of Prosumers

## Table of Contents

- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [The Data](#the-data)
- [Preprocessing and Data Transformation and Feature Engineering](#preprocessing-and-data-transformation-and-feature-engineering)
- [Training the Models](#training-the-models)
- [Evaluation](#evaluation)
- [Next Steps](#next-steps)
- [License](#license)

## Introduction

The goal is to create an energy prediction model of prosumers to reduce energy imbalance costs.
This competition aims to tackle the issue of energy imbalance, a situation where the energy expected to be used doesn't line up with the actual energy used or produced. Prosumers, who both consume and generate energy, contribute a large part of the energy imbalance. Despite being only a small part of all consumers, their unpredictable energy use causes logistical and financial problems for the energy companies. 

## Project Structure
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
### Business Understanding
The number of prosumers is rapidly increasing, and solving the problems of energy imbalance and their rising costs is vital. If left unaddressed, this could lead to increased operational costs, potential grid instability, and inefficient use of energy resources. If this problem were effectively solved, it would significantly reduce the imbalance costs, improve the reliability of the grid, and make the integration of prosumers into the energy system more efficient and sustainable. Moreover, it could potentially incentivize more consumers to become prosumers, knowing that their energy behavior can be adequately managed, thus promoting renewable energy production and use.
Enefit is one of the biggest energy companies in Baltic region. As experts in the field of energy, we help customers plan their green journey in a personal and flexible manner as well as implement it by using environmentally friendly energy solutions.
At present, Enefit is attempting to solve the imbalance problem by developing internal predictive models and relying on third-party forecasts. However, these methods have proven to be insufficient due to their low accuracy in forecasting the energy behavior of prosumers. The shortcomings of these current methods lie in their inability to accurately account for the wide range of variables that influence prosumer behavior, leading to high imbalance costs. By opening up the challenge to the world's best data scientists through the Kaggle platform, Enefit aims to leverage a broader pool of expertise and novel approaches to improve the accuracy of these predictions and consequently reduce the imbalance and associated costs.
### What do we need to predict?
For each county we need to make predicitons of consumption or production of electricity. For each county we need to make prediction for several subgroups is_business(True/False), is_consumption(True/False), product_type(0, 1, 2, 3).
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
## preprocessing and Data Transformation and Feature Engineering
The provided code encompasses a detailed preprocessing pipeline for a time-series forecasting project. The timestamp_UTC_conversion function primarily focuses on converting a timestamp column in a DataFrame to separate date and time components. It also accommodates potential conflicts by renaming the 'date' column to 'date_' if needed.

The process_date function, designed for DataFrame 'train,' undertakes a multi-step approach. It converts the specified date column to string format to avoid datetime errors and then employs the timestamp_UTC_conversion function for polar UTC conversion. The resulting 'date' and 'time' columns are concatenated into a new 'date_col' column. If the option to extract additional date features is enabled, it goes further to derive features like year, month, day, day of the week, hour, minutes, and seconds. These features can be prefixed if desired, and unnecessary columns related to the original date are dropped.

Furthermore, the reduce_memory_usage function is designed to optimize the memory footprint of the DataFrame by adjusting data types. It iterates through each column, converting numerical types to smaller sizes if possible and converting object types to 'category.'

The subsequent part of the code involves creating lag features for the target variable. It iterates over a range of days, shifting the 'data_block_id' column and merging the DataFrame with itself to create lag features. It then fills NaN values in the lagged target column with the corresponding values from the 'target' column.
## Training the Models
Light GBM is a powerful gradient boosting framework for ensemble learning, specifically designed for efficient and scalable performance on large datasets. In a time series project, Light GBM proves effective due to its ability to handle sequential data and capture temporal dependencies. It employs a unique leaf-wise tree growth strategy, efficiently handles categorical features, and supports parallel and distributed training for enhanced scalability. Light GBM is well-suited for forecasting tasks, leveraging historical information such as lagged variables and rolling statistics. The model's gradient-based learning approach, coupled with its parameter tuning capabilities, makes it a valuable tool for achieving accurate predictions in time series applications while ensuring computational efficiency.
Another model that is deployed for evaluating the results is Long Short-Term Memory (LSTM) networks which are commonly employed in time series forecasting projects due to their ability to capture and model complex temporal dependencies in sequential data. Unlike traditional feedforward neural networks or other time series models, LSTMs excel at handling sequences with long-term dependencies, making them particularly suitable for time series data where patterns and trends may vary over time. LSTMs have internal memory cells that can retain information for extended periods, allowing them to learn and remember patterns over different time scales. This is crucial for capturing seasonality, trends, and irregular patterns in time series data. Additionally, LSTMs can automatically adapt to varying time lags and handle multivariate time series, making them versatile for a wide range of forecasting tasks.
## Evaluation
For the test set, the Mean Absolute Error (MAE) is approximately 73.85, indicating the average absolute difference between predicted and actual values. The Mean Squared Error (MSE) is 78744.73, representing the average squared differences, and the R-squared value is 0.92, denoting the proportion of variance explained by the model. These metrics demonstrate the model's effectiveness in predicting unseen data. Additionally, training set metrics reveal excellent performance, with a low MAE of 29.19, MSE of 10440.63, and a high R-squared of 0.99, highlighting the model's ability to capture patterns in the training data. Similar high-quality metrics on the validation set, such as MAE of 44.21, MSE of 27343.35, and R-squared of 0.98, further underscore the model's robustness and suggest its reliability for forecasting in your time series project.
## Next Steps

As we did not get satisfactory results from an LSTM model, there are several steps that we can take to improve or fix the performance. Here are some suggestions:

1. **Data Preprocessing:**
   - **Scaling:** Ensure that your input features are properly scaled. LSTMs are sensitive to the scale of input data.
   - **Normalization:** Normalize your target variable if it has a wide range of values.

2. **Feature Engineering:**
   - **Additional Features:** Consider adding more relevant features that might improve the model's ability to learn patterns.
   - **Time Features:** Extract and incorporate time-related features such as day of week, month, or season.

3. **Model Architecture:**
   - **Complexity:** Adjust the model complexity. You might try increasing the number of LSTM layers or units, but be cautious about overfitting.
   - **Dropout:** Add dropout layers to prevent overfitting.
   - **Bidirectional LSTM:** Experiment with bidirectional LSTMs, which process the input sequence in both forward and backward directions.

4. **Training Configuration:**
   - **Learning Rate:** Adjust the learning rate. Experiment with different learning rates to find the one that works best.
   - **Epochs:** Train for more epochs or use early stopping to prevent overfitting.

5. **Sequence Length:**
   - **Adjust Sequence Length:** Experiment with different sequence lengths. A longer sequence length might capture more complex patterns.

6. **Ensemble Models:**
   - **Ensemble Methods:** Consider using ensemble methods with multiple LSTM models to improve predictive performance.

7. **Hyperparameter Tuning:**
   - **Grid Search:** Perform a grid search or random search for optimal hyperparameters.

8. **Regularization Techniques:**
   - **L1/L2 Regularization:** Apply L1 or L2 regularization to the LSTM layers to prevent overfitting.

9. **Loss Function:**
   - **Custom Loss Function:** If your problem has specific characteristics, consider designing a custom loss function that aligns better with your objectives.

10. **Evaluate Residuals:**
    - **Residual Analysis:** Analyze residuals to understand where the model is making errors and whether there are specific patterns that need attention.
## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
