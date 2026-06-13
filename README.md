# OceanGuard Optimizer: Data Science on the High Seas

## 📌 Project Overview
Offshore fisheries represent a vital sector in the maritime economy, yet they face massive operational risks and high capital costs. For offshore fishing voyages in developing nations like **Sri Lanka**, fuel expenses, vessel maintenance, and crew wages represent significant financial risks, while changing weather conditions present constant safety hazards. 

This repository contains the end-to-end data science and predictive analytics workflow for **OceanGuard Optimizer**. Using a real-world dataset of **20,000+ Sri Lankan offshore fishing trip records**, we perform comprehensive feature engineering, statistical hypothesis testing, and model training to predict voyage operational costs, calculate break-even catch targets, and assess weather safety risks.

---

## 📁 Repository Directory & Deliverables
This repository contains the primary dataset, analysis source code, and key deliverables:

* 📊 **[Dataset (CSV)](fishing_data.csv)**: Complete dataset containing 20,000 records of fishing trip parameters, weather metrics, species catches, and cost structures.
* 📓 **[Machine Learning Modelling Source File (Jupyter Notebook)](Python_ML_Modelling_Source_File(Venuri)%20(4).ipynb)**: Full Python notebook containing data cleaning, MICE imputation, geographic clustering, feature engineering, statistical tests, and machine learning models.
* 📄 **[Full Project Report (PDF)](Full%20project%20report.pdf)**: Detailed research report detailing the methodologies, model diagnostics, feature analysis, and validation results.
* 📄 **[Individual Contribution Report (PDF)](Individual%20contribution%20report.pdf)**: Individual report highlighting specific modeling contributions, database setup, and feature analytics.
* 📊 **[Presentation Slides (PDF)](slides.pdf)**: Slide deck detailing the project background, model architectures, performance leaderboards, and business impact.

---

## 🛠️ Data Science & Feature Engineering Workflow

The core modeling pipeline, implemented in the [Jupyter Notebook](Python_ML_Modelling_Source_File(Venuri)%20(4).ipynb), consists of the following key steps:

### 1. Data Cleaning & Preprocessing
* **Train/Test Split**: Early 80/20 train/test split to prevent target leakage during feature engineering.
* **MICE Imputation**: Imputed missing `boat_length_ft` values using the **MICE (Multivariate Imputation by Chained Equations)** algorithm via scikit-learn's `IterativeImputer`.

### 2. Advanced Feature Engineering
* **Trip Age**: Calculated from the departure year to capture vessel aging effects.
* **Port Name Matching**: Geographic coordinates of departure ports resolved into Sri Lankan coastal cities.
* **Geographic Clustering**: Grouped fishing coordinates into **15 distinct fishing zones** using **K-Means Clustering**, aligning with the 15 administrative fisheries districts in Sri Lanka.
* **Fuel Cost Calculation**: Derived directly as `fuel_liters * fuel_price_per_liter_LKR`.
* **Net Profit**: Derived as `revenue_LKR - total_cost_LKR`.
* **Sea Condition Categorization**: Classified into Calm, Moderate, and Rough based on wind speeds (`wind_kph`) and wave heights (`wave_m`).

### 3. Statistical Analysis & Diagnostics
* **Multicollinearity Checks (VIF)**: Calculated the Variance Inflation Factor (VIF) to detect collinearity between predictors:
  * `boat_length_ft` (VIF: 24.22) and `engine_hp` (VIF: 20.84) showed high collinearity as expected due to physical vessel dimensions.
  * Crew size (VIF: 3.63) and allowed offshore days (VIF: 1.76) were clean.
* **Independent T-Test**: Conducted an independent t-test to evaluate the cost difference between safe and unsafe voyages. The test yielded a **T-statistic of -3.4920** ($p$-value of **0.0005**), concluding a statistically significant cost difference.

---

## 🏆 Machine Learning Leaderboard

Five regression models were trained on log-transformed cost targets (`total_cost_LKR`) and evaluated on the test set. Models were back-transformed to LKR to compute error metrics:

| Model | Accuracy ($R^2$) | Test MAE (LKR) | Error vs. Mean (%) | MAPE (%) | Test RMSE (LKR) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| 🚀 **XGBoost** | **0.9792** | **26,953.71** | **7.87%** | **9.30%** | **63,012.19** |
| 🌲 **Random Forest** | 0.9784 | 28,996.15 | 8.47% | 9.49% | 69,394.01 |
| 📈 **Ridge** | 0.9644 | 49,784.72 | 14.54% | 12.28% | 120,203.31 |
| 📉 **Elastic Net** | 0.9596 | 56,399.43 | 16.47% | 12.89% | 140,296.44 |
| 📊 **Lasso** | 0.9567 | 58,350.20 | 17.04% | 13.27% | 143,799.35 |

*Note: The original dataset mean trip cost is **342,364.63 LKR**.*

---

## 💡 Strategic Cost Insights for Ship Owners

Using linear regressions and median groupings, the project identifies key cost drivers modeled as "taxes":
1. **Labor Tax (Crew Size)**: Each additional crew member increases the average voyage cost by **31.33%** due to wages and provisioning.
2. **Zone Tax (Fishing Zone)**: Changing the targeted fishing zone introduces up to a **20.51%** cost variance.
3. **Weather Tax (Sea Condition)**: Operating in rough weather conditions adds a **10.55%** cost variance compared to calm seas.

---

## 🎯 Business Impact & Decision Support
* **Pre-Trip Financial Planning**: Pre-departure predictions eliminate uncertainty by forecasting the required capital investment (fuel, ice, food, gear, and wages).
* **Break-Even Target Setting**: Translates predicted costs into real-time catch targets (e.g., target weight in kg of Yellowfin Tuna, Skipjack, or Marlin required to cover expenses).
* **Safety Optimization**: Evaluates wave and wind conditions dynamically to flag unsafe departures, protecting crew lives and fleet assets.
