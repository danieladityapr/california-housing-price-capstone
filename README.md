
# 🏡 California Housing Price Prediction (Capstone Project)

[California Real Estate]

This project is part of the final capstone from the **Data Science, Machine Learning & AI Bootcamp** at **Purwadhika Digital School**. The goal is to build a predictive model that estimates **California housing prices** based on the 1990 U.S. Census data.

> While the data is historical, the insights and methodology can be used by property companies today to support decision-making in pricing strategies, regional planning, and real estate investments.

---

## 📌 Project Objectives

- Analyze historical housing data to uncover geographic and socioeconomic patterns in property values.
- Develop regression models to predict housing prices using engineered features.
- Provide strategic insights and recommendations based on model results.
- Demonstrate end-to-end data science workflow, including preprocessing, feature engineering, model tuning, and evaluation.

---

## 🧠 Business Relevance

The insights from this project can assist:

- **Business Intelligence Teams** in identifying high-potential regions.
- **Pricing Strategy Departments** in understanding market fluctuations.
- **Tech/Product Teams** in integrating price prediction into dashboards or internal tools.

---

## 📦 Dataset Overview

- **Source:** California Housing Prices (1990 Census)
- **Total Rows:** 14,448
- **Target Variable:** `median_house_value` (in USD)
- **Key Features:**
  - `median_income`, `housing_median_age`
  - `total_rooms`, `total_bedrooms`, `population`, `households`
  - `latitude`, `longitude`, `ocean_proximity` (categorical)

---

## 🛠️ Preprocessing & Feature Engineering

### Key Steps:

- Removed rare category `ISLAND` from `ocean_proximity`
- Filtered out extreme outliers: `people_per_room > 16`
- Handled missing values using **Iterative Imputer**
- Created new features:
  - `rooms_per_household`, `bedrooms_per_room`
  - `population_per_household`, `people_per_room`
  - `income_per_household`

### Geospatial Clustering:
- Used **K-Means** to generate `geo_clusters` based on latitude and longitude (n = 4)

### Scaling & Encoding:
- `StandardScaler` for `housing_median_age`
- `RobustScaler` for other numerical features
- `OneHotEncoder` for `ocean_proximity` and `geo_clusters`

---

## 📊 Exploratory Data Analysis

- **Boxplot** to detect skewed distributions
- **Heatmap** for correlation analysis
- **Distribution plots** for key engineered features

---

## 🤖 Model Selection & Evaluation

We evaluated **11 regression models** using cross-validation and selected the top 3 for fine-tuning:

| Model                  | RMSE    | MAE     | MAPE    |
|------------------------|---------|---------|---------|
| **ExtraTreesRegressor** | **55,389** | **38,022** | **21.85%** |
| RandomForestRegressor | 57,663  | 39,584  | 22.1%   |
| GradientBoostingRegressor | 58,212  | 40,008  | 21.8%   |

Final model: **ExtraTreesRegressor**

---

## 🧮 Model Interpretation (SHAP)

Top influential features:
- `median_income` → positive effect
- `ocean_proximity_INLAND` → lowers price
- `population_per_household` → negative impact
- `people_per_room`, `bedrooms_per_room` → represent density
- `geo_clusters` → reflect regional differences

---

## ✅ Performance Summary

| Metric | Before Tuning | After Tuning | Δ Improvement |
|--------|---------------|--------------|----------------|
| RMSE   | 56,196        | 55,389       | ↓ 807          |
| MAE    | 38,590        | 38,022       | ↓ 568          |
| MAPE   | 22.17%        | 21.85%       | ↓ 0.32%        |

This equates to:
- **±$38,000 MAE**: typical price deviation
- **±$55,000 RMSE**: worst-case deviation  
Still acceptable for a high-variance market like real estate.

---

## 📌 Strategic Recommendations

1. **Use Price Ranges** for external communication (e.g., "$210K–$250K")
2. **Flag Low Confidence Predictions** with RMSE > $55K
3. **Retrain Model Regularly** every 3–6 months
4. **Embed Prediction Confidence Levels**:
   - High Confidence: ≤ $30K
   - Medium: $30K–$50K
   - Low: > $50K
5. **Automate Validation Logic** in internal systems

---

## 📁 Repository Structure

```
📁 california-housing-price-capstone
├── Capstone_California_Housing_Price.ipynb
├── data_california_house.csv
├── File_presentasi_capstone_3.pdf
└── README.md
```

---

## 📇 About Me

**Gregorius Daniel**  
Purwadhika Data Science, ML & AI Bootcamp Graduate  
📧 danieladitya178@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/danieladityapr/)
