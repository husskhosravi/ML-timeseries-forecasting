### 📊 Project Title  
Electricity Consumption Forecasting using Multiple Time Series Models:
Linear Regression/Facebook Prophet/ARIMAX/Exponential Smoothing

---

### 🔍 Overview  
This project forecasts hourly electricity consumption for a specific zone using a comprehensive dataset that includes both consumption and weather metrics (e.g., Temperature, Humidity, WindSpeed). The project demonstrates baseline forecasting using Linear Regression and Facebook Prophet, and then explores advanced techniques with ARIMAX and Exponential Smoothing to capture autocorrelation and incorporate exogenous variables. The final outcome shows how different models perform and provides insights into improving forecast accuracy.

---

### 📁 Steps in the Pipeline  

## 1. 📥 Data Loading  
The dataset is imported using pandas from CSV files. The raw data (with columns such as PowerConsumption_Zone1, Temperature, Humidity, and WindSpeed) is parsed by datetime and resampled to hourly averages. A corresponding data dictionary is provided to explain each feature. This step ensures the data is in a uniform format for analysis.

## 2. 🔍 Exploratory Data Analysis  
Initial visualisations are created with Seaborn and Matplotlib to examine trends, seasonality, and outliers in the data. For example, a line chart of hourly consumption reveals a notable drop on January 15, prompting further investigation. Basic statistical summaries help in understanding the range and distribution of consumption and weather variables.

## 3. 🔧 Feature Engineering  
Key features are extracted from the datetime index such as hour-of-day and an overall time trend to support regression analysis. In addition, weather variables (Temperature, Humidity, WindSpeed) are retained as exogenous inputs for advanced models. This dual approach of engineered time features and exogenous variables allows the models to capture both internal patterns and external influences.

## 4. 📊 Baseline Forecasting (Regression & Prophet)  
Two baseline models are implemented:
- **Linear Regression:**  
  An Ordinary Least Squares (OLS) model is fitted using engineered features (e.g., hour dummies and time trend). The model is trained on January 2017 data and tested on the first three days of February 2017. Sample outputs include a **MAE** of **1016.81** and a **MAPE** of **0.0327**.
- **Facebook Prophet:**  
  The dataset is reformatted for Prophet (with columns renamed to `ds` and `y`) and used to forecast the same period. Prophet automatically decomposes the time series into trend and seasonal components. Its performance is improved with a **MAE** of **857.23** and a **MAPE** of **0.0283**.  
Both models are evaluated using visual comparisons of predicted vs actual values and error metrics.

## 5. 📈 Advanced Time Series Modelling  
To further refine the forecasts, advanced models that capture autocorrelation and incorporate exogenous variables are explored:
- **ARIMAX (SARIMAX):**  
  This model integrates weather variables (Temperature, Humidity, WindSpeed) as exogenous inputs while addressing the autoregressive and moving average components with seasonal adjustments (e.g., a seasonal period of 24 hours). It delivers competitive performance with a **MAE** of **910.87** and a **MAPE** of **0.0303**, indicating that including external influences can moderately enhance forecasting accuracy.
- **Exponential Smoothing (Holt-Winters):**  
  An additive Holt-Winters model is applied to capture both trend and seasonality. However, it struggles to capture the underlying dynamics effectively, resulting in a higher error with a **MAE** of **1430.25** and a **MAPE** of **0.0459**.

---

### 📌 Model & Techniques  
- **Linear Regression (OLS):** Utilises engineered features like time trend and hour dummies; serves as a simple baseline.
- **Facebook Prophet:** Automatically detects trend and seasonal patterns, providing interpretable decompositions.
- **ARIMAX (SARIMAX):** Combines autoregressive and moving average components with exogenous variables to capture external influences.
- **Exponential Smoothing (Holt-Winters):** Smooths the data to reveal trend and seasonality, offering an alternative view on the time series structure.  
These models were chosen for their complementary strengths in capturing different aspects of the data, from basic linear trends to complex seasonal effects and external drivers.

---

### 📈 Results & Insights  
The baseline Linear Regression model produced **MAE: 1016.81** and **MAPE: 0.0327**, while Prophet improved on these results with **MAE: 857.23** and **MAPE: 0.0283**. This suggests that Prophet’s capability to automatically decompose and capture trend and seasonal components provides a measurable advantage over a simple linear approach. The ARIMAX model, which integrates exogenous variables such as Temperature, Humidity, and WindSpeed, delivered competitive performance with **MAE: 910.87** and **MAPE: 0.0303**, indicating that including external influences can moderately enhance forecasting accuracy.

In contrast, the Exponential Smoothing model struggled to capture the underlying dynamics, resulting in a higher error with **MAE: 1430.25** and **MAPE: 0.0459**. Overall, while Prophet outperforms the other models in terms of accuracy, ARIMAX presents a viable alternative by explicitly modelling exogenous factors, offering insights into how external conditions drive consumption patterns.

---

### 🛠️ Tech Stack  
- `pandas`  
- `numpy`  
- `seaborn`  
- `matplotlib`  
- `statsmodels`  
- `prophet`  
- `scikit-learn`

---
Thanks for checking out this project!
