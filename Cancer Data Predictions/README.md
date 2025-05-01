# Cancer Severity Score Prediction

A reproducible R‐based pipeline to predict patient severity scores from demographic and lifestyle risk factors. This repository contains everything needed to reproduce data cleaning, model training, diagnostics for the `Target_Severity_Score`.

---

## 📥 Data Source

- **Kaggle dataset:**   
  [Cancer Severity Dataset](https://www.kaggle.com/datasets/zahidmughal2343/global-cancer-patients-2015-2024?resource=download)  
  Download the CSV and place it as `global_cancer_patients_2015_2024.csv`.

## 🚀 Getting Started

1. **Clone this repo**  
   ```bash
   git clone https://github.com/adityashah841/Analytics-Projects.git
   cd cancer-severity-score
   ```  

2. **Install R dependencies**
  ```r
  install.packages(c(
    "data.table", "ggplot2", "randomForest", "xgboost", "Matrix",
    "glmnet", "car", "boot"
  ))
  ```
3. **Run the R-markdown File**
    - Open the R-markdown file for a documented code and analysis.
    - The markdown file helps in replicating the results.
    - Open the markdown file preferably in R-Studio

---

## 📊 Results & Model

| Model                          | Test-set RMSE | Test-set R² |
|--------------------------------|--------------:|------------:|
| Full OLS (29 variables)        |         0.547 |       0.797 |
| Random Forest                  |         0.566 |       0.785 |
| XGBoost                        |         0.553 |       0.793 |
| **Simple OLS (5 variables)**   |     **0.547** |   **0.797** |

**Final Parsimonious Model**

Severity_Score ≈ 0.941  
               + 0.201 × Smoking  
               + 0.200 × Genetic_Risk  
               + 0.152 × Air_Pollution  
               + 0.150 × Alcohol_Use  
               + 0.100 × Obesity_Level

---

## 🔍 Diagnostics & Stability
1. **Residual Analysis**
    - Residuals vs. Fitted: Flat, homoscedastic band—no unmodeled non-linearity or heteroscedasticity.
    - Q–Q Plot: Points lie almost exactly on the line—residuals ≈ Gaussian.
2. **Multicollinearity**
    - VIFs ≈ 1.00 for all five predictors—virtually no collinearity.
3. Bootstrap (200 replicates)
    - Bias < |0.001|, Std. errors ≈ 0.001 for all coefficients—extremely stable estimates.

---

## 📝 Conclusion
- A simple 5-variable OLS model captures 80% of the variance in severity score (R² ≈ 0.797, RMSE ≈ 0.547).
- Smoking, Genetic_Risk, Air_Pollution, Alcohol_Use, and Obesity_Level are the only meaningful predictors; all other features (cancer type/stage, demographics) add no incremental value.
- Diagnostic plots and numerical checks confirm no remaining structure to model: residuals are well behaved, predictors are orthogonal, and coefficient estimates are robust.
- Recommendation: Adopt the parsimonious OLS formula for reporting and deployment; further improvements require new clinical or molecular features.

---
