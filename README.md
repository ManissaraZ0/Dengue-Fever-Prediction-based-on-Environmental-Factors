# 🦟 Dengue Fever Prediction based on Environmental Factors

This project was developed in 2025 as part of the CP462 Introduction to Data Science course. The primary goal is to predict the number of dengue fever cases in Thailand's Health District 4 (2023) by analyzing environmental and weather datasets.

## 📊 Project Objectives

The core of this project is to practice the end-to-end Data Science pipeline:

* **Data Wrangling:** Cleaning and merging medical records with meteorological data.
* **Exploratory Data Analysis (EDA):** Visualizing distributions and correlations.
* **Insight & Pattern Detection:** Identifying seasonal trends and how weather variables (temperature, humidity, rainfall) impact dengue outbreaks.
* **Machine Learning:** Implementing and comparing multiple regression models to find the most accurate predictor.

## 🛠 Project Workflow

**1. Data Processing & EDA**

* **Cleaning:** Handling missing values and ensuring consistent time-series formats.
* **Visualization:** Using Heatmaps to find correlations between weather factors and infection rates.
* **Trend Analysis:** Detecting monthly patterns to understand when peak infection seasons occur.

**2. Machine Learning Models**

We implemented and compared four linear-based models to predict the case counts:

* **Linear Regression:** The baseline model for identifying linear relationships.
* **Ridge Regression (L2):** Used to prevent overfitting by penalizing large coefficients.
* **Lasso Regression (L1):** Used for feature selection by shrinking less important coefficients to zero.
* **Elastic Net Regression:** A hybrid approach combining both L1 and L2 penalties.
  
## 🔬 Technologies & Libraries
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn

## 📁 Dataset Information

The analysis is based on two primary data sources from 2023:
1. **Dengue Situation Report:** Statistics from Health District 4, Thailand. [Data source](https://opendata.ddc.moph.go.th/en/dataset/odpc4-01/resource/d2b707d9-2bf0-4938-8c19-51864cab2c25?inner_span=True)
2. **Weather Dataset:** Local environmental data including average temperature, precipitation, and humidity. [Data source](https://dpmalert.disaster.go.th/WeatherData/WeatherDataByArea)

## 📈 Performance Comparison

The table below summarizes the performance of each regression model. We compared baseline models against versions with Polynomial Features to capture non-linear relationships between environmental factors and dengue cases.
| Model                   | Train R² | Test R² | MSE  | RMSE | MAE  |
| ----------------------- | -------- | ------- | ---- | ---- | ---- |
| Linear Regression       | 0.35     | 0.33    | 6.70 | 2.59 | 1.74 |
| Ridge (No Poly)         | 0.35     | 0.31    | 6.91 | 2.63 | 1.76 |
| Ridge (With Poly)       | 0.59     | 0.44    | 5.65 | 2.38 | 1.63 |
| Lasso (No Poly)         | 0.34     | 0.32    | 6.82 | 2.61 | 1.75 |
| Lasso (With Poly)       | 0.62     | 0.47    | 5.28 | 2.30 | 1.56 |
| Elastic Net (No Poly)   | 0.34     | 0.32    | 6.82 | 2.61 | 1.75 |
| Elastic Net (With Poly) | **0.68**     | **0.51**    | **4.92** | **2.22** | **1.48** |

## 🔍 Key Insights from Results
1. **Polynomial Impact:** Adding Polynomial Features significantly improved the model performance across all types of regularization. This suggests that the relationship between weather variables (like temperature and rainfall) and dengue outbreaks is non-linear.
2. **Best Performing Model:** Elastic Net with Polynomial Features emerged as the best model, achieving the highest Test $R^2$ of 0.51 and the lowest error rates (MSE: 4.92, MAE: 1.48).
3. **Regularization Effectiveness:** Regularization (Lasso, Ridge, and Elastic Net) helped stabilize the models when using high-dimensional polynomial features, with Elastic Net providing the best balance between bias and variance.
4. **Error Analysis:** An MAE of 1.48 indicates that, on average, the model's prediction deviates by approximately 1.5 cases from the actual reported data, which is a promising result given the complexity of epidemiological data.

## ⚙️ How to Run
1. **Clone the Repository:**
```Bash
git clone <REPOSITORY_URL>
```

2. **Install Requirements:**
```Bash
pip install pandas numpy matplotlib seaborn scikit-learn
```
3. **Run the Notebook:** Open `dengue_analysis.ipynb` in Jupyter Notebook or Google Colab to see the full analysis.
