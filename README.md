# Airbnb NYC 2019: Data Analysis and Price Prediction

## 📌 Project Overview

This project analyzes Airbnb listings across New York City using the **Airbnb NYC 2019 dataset**. The analysis focuses on pricing, room types, neighbourhoods, availability, reviews, and host activity.

The project combines **data cleaning, exploratory data analysis (EDA), data visualization, statistical analysis, and machine learning** to identify patterns in Airbnb listings and predict listing prices.

---

## 🎯 Objectives

The main objectives of this project are to:

* Analyze how Airbnb prices vary across neighbourhoods and room types.
* Identify neighbourhoods with the highest number of Airbnb listings.
* Examine review activity and listing availability.
* Explore relationships between Airbnb prices and other listing characteristics.
* Build regression models to predict Airbnb listing prices.
* Compare different machine learning models based on their performance.
* Identify the features that have the greatest influence on predicted prices.

---

## 📊 Dataset

The project uses the **Airbnb NYC 2019 dataset**.

The dataset contains **48,895 Airbnb listings** and **16 columns** before preprocessing.

### Main Features

| Feature                          | Description                                 |
| -------------------------------- | ------------------------------------------- |
| `id`                             | Unique listing ID                           |
| `name`                           | Listing name                                |
| `host_id`                        | Unique host ID                              |
| `host_name`                      | Host name                                   |
| `neighbourhood_group`            | NYC borough                                 |
| `neighbourhood`                  | Specific neighbourhood                      |
| `latitude`                       | Listing latitude                            |
| `longitude`                      | Listing longitude                           |
| `room_type`                      | Type of accommodation                       |
| `price`                          | Listing price                               |
| `minimum_nights`                 | Minimum required nights                     |
| `number_of_reviews`              | Total number of reviews                     |
| `last_review`                    | Date of most recent review                  |
| `reviews_per_month`              | Average reviews per month                   |
| `calculated_host_listings_count` | Number of listings associated with the host |
| `availability_365`               | Available days during the year              |

---

## 🧹 Data Cleaning

Several data-quality checks and preprocessing steps were performed.

### Data Quality Checks

* Inspected dataset dimensions and data types.
* Checked for duplicate records.
* Identified missing values.
* Examined numerical variables using descriptive statistics.
* Investigated potential outliers.

The dataset contained **no duplicate rows**.

### Missing Values

Missing values were identified in:

* `name`
* `host_name`
* `last_review`
* `reviews_per_month`

Text fields were filled with `"Unknown"`, while missing `reviews_per_month` values were replaced with `0`.

The `last_review` column was subsequently removed because it was not used in the analysis or machine-learning feature set.

### Outlier Treatment

The project used the **Interquartile Range (IQR)** method to identify and reduce the influence of extreme price values. Price, availability, and review-count distributions were also examined using boxplots.

---

## 📈 Exploratory Data Analysis

The project explores several aspects of the Airbnb market.

### Listings by Neighbourhood Group

The number of listings by NYC neighbourhood group was:

* **Manhattan:** 19,506
* **Brooklyn:** 19,415
* **Queens:** 5,567
* **Bronx:** 1,070
* **Staten Island:** 365

### Listings by Room Type

The dataset contains:

* **Entire home/apt:** 22,789
* **Private room:** 21,996
* **Shared room:** 1,138

### Average Price by Neighbourhood Group

| Neighbourhood Group | Average Price |
| ------------------- | ------------: |
| Manhattan           |       $145.95 |
| Brooklyn            |       $105.70 |
| Staten Island       |        $89.24 |
| Queens              |        $88.90 |
| Bronx               |        $77.37 |

### Average Price by Room Type

| Room Type       | Average Price |
| --------------- | ------------: |
| Entire home/apt |       $162.53 |
| Private room    |        $79.02 |
| Shared room     |        $59.29 |

### Review Activity

The project also examined total reviews by neighbourhood group. Brooklyn and Manhattan accounted for the largest amounts of review activity in the dataset.

### Geographic Analysis

Latitude and longitude were used to visualize the geographic distribution of listings across NYC neighbourhood groups and room types.

---

## 🤖 Machine Learning — Price Prediction

After completing the exploratory analysis, machine learning models were developed to predict Airbnb listing prices.

### Models Used

Four regression approaches were evaluated:

1. **Linear Regression**
2. **Decision Tree Regression**
3. **Random Forest Regression**
4. **XGBoost Regression**

The dataset was divided into training and testing sets. Numerical variables were standardized, while categorical variables were transformed using one-hot encoding through a preprocessing pipeline.

### Model Performance

| Model             |    R² |   MSE |
| ----------------- | ----: | ----: |
| Linear Regression |  0.46 |  0.54 |
| Decision Tree     |  0.47 |  0.53 |
| Random Forest     |  0.48 |  0.52 |
| XGBoost           | ~0.51 | ~0.49 |

The XGBoost model achieved the highest reported R² among the models evaluated.

---

## 🔍 Hyperparameter Tuning

Grid Search with 5-fold cross-validation was used to tune the XGBoost model.

The selected parameters were:

```text
n_estimators = 200
max_depth = 6
learning_rate = 0.05
```

The best cross-validation R² reported by Grid Search was approximately **0.514**.

The final model achieved:

```text
R²  = 0.509
MSE  = 0.492
```

on the test set.

---

## ⭐ Feature Importance

Feature importance analysis was performed using the final XGBoost model.

The most influential features included:

* `room_type = Entire home/apt`
* `neighbourhood_group = Manhattan`
* `neighbourhood_group = Brooklyn`
* `room_type = Private room`
* `calculated_host_listings_count`
* `minimum_nights`
* `availability_365`
* `reviews_per_month`
* `number_of_reviews`

The model's feature-importance output showed that **room type and neighbourhood group were particularly influential in predicting listing price**.

SHAP analysis was also used to further examine model feature contributions.

---

## 🛠️ Tools & Technologies

* **Python**
* **Pandas** — Data manipulation
* **NumPy** — Numerical analysis
* **Matplotlib** — Data visualization
* **Seaborn** — Statistical visualization
* **Pipeline** for pipelines
* **Scikit-learn** — Machine learning and preprocessing
* **XGBoost** — Gradient boosting regression
* **SHAP** — Model explainability
* **Jupyter Notebook**

---

## 📌 Key Takeaways

* Manhattan and Brooklyn contain the largest number of listings in the dataset.
* Entire homes/apartments have a substantially higher average price than private and shared rooms.
* Manhattan has the highest average listing price among the NYC neighbourhood groups analyzed.
* Room type and neighbourhood are important factors associated with Airbnb listing prices.
* XGBoost provided the strongest predictive performance among the regression models tested.
* Hyperparameter tuning improved the XGBoost model and produced a test-set R² of approximately 0.51.

---

## 📚 Project Focus

This project demonstrates an end-to-end data analytics workflow:

```text
Data Collection
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis
      ↓
Data Visualization
      ↓
Feature Engineering & Preprocessing
      ↓
Machine Learning
      ↓
Model Evaluation
      ↓
Hyperparameter Tuning
      ↓
Feature Importance & SHAP Analysis
```
