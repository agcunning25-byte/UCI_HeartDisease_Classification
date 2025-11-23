# 🩺 Heart Disease Detection and Classification
This project focuses on developing a robust machine learning model to predict the presence of heart disease using clinical and demographic patient data from the UCI Heart Disease Dataset available on Kaggle.

# 🎯 Project Objective
Cardiovascular diseases (CVDs) are the leading cause of death globally, accounting for an estimated 17.9 million lives each year. Early detection and management are critical.

Working as a Data Scientist, the objective was to:

Develop a highly accurate machine learning model capable of forecasting heart disease.

Pinpoint the key contributing factors to the prediction, providing interpretable insights for clinical application.

# ⚙️ Methodology
The project followed a standard machine learning workflow, including data preprocessing, extensive Exploratory Data Analysis (EDA), feature engineering, model selection, and hyperparameter tuning.

# Data Preparation and Preprocessing
* **Handling Missing Values:** A significant number of Cholesterol (0) values were treated as missing and imputed with the mean of non-zero values (approx. 245).

* **Outlier Correction:** Negative values in the Oldpeak feature were identified as noise and replaced with 0.

* **Feature Engineering:** A new interaction feature, OPxBS (Oldpeak × FastingBS), was created to capture potential combined effects.

* **Encoding and Scaling:** Categorical features were One-Hot Encoded, and numerical features were scaled using StandardScaler to prepare the data for modeling.

# Modeling and Evaluation
A variety of classification algorithms were implemented and evaluated using Grid Search Cross-Validation to identify the best-performing model based on the test set Recall score, as high recall is essential for minimizing false negatives (missing a heart disease case).

| Model | Libraries Used |
| ----- | -------------- |
| Linear Models | Logistic Regression |
| Tree-Based Models | Decision Tree, Random Forest |
| Ensemble Models | XGBoost Classifier |
| Other Models | Support Vector Machine (SVC) |
# 📈 Results and Key Findings
The Tuned Support Vector Machine demonstrated the strongest performance (in terms of recall alone), achieving the following metrics on the test set:

| Metric | Score |
| ------ | ----- |
| Test Accuracy | 83.15% |
| Test Recall | 97.05% |
| Test Precision | 77.95% |
| Test F1-Score | 86.46% |
# Feature Importance Insights
SHAP summary revealed the most critical predictors of heart disease:

* ST_Slope (Slope of the peak exercise ST segment)
* ChestPainType (ASY - asymptomatic)
* Old Peak (ST (numeric value measured in depression)
* Gender

# Permutation Importances
A permutation inspection revealed the most important features for minimizing recall:

* Sex_F
* Age
* Old Peak x Resting BS x ST_Slope (an engineered feature to help the model classify in areas of high overlap)
* Old Peak > 1.20

# Conclusions
* **ST_Slope is the dominant predictor of heart disease:** Far outweighing all other features, a downsloping or flat segment during stress tests strongly indicates heart disease, while an upsloping segment signifies healthy patients.

* **Patients without typical chest pain (ASY) are at higher risk:** This highlights the danger of "silent" heart disease, where factors like diabetes or severe blockage may prevent patients from feeling typical angina symptoms.

* **Exercise-related cardiac changes are superior predictors:** Functional stress indicators like ST_Slope, MaxHR, and ExerciseAngina are much more powerful in heart disease prediction than static demographic and laboratory values (Age, Cholesterol, RestingBP).

# 💻 Repository Structure
```text
├── Heart_Failure.ipynb  # The main Jupyter Notebook with all the analysis and modeling.
├── README.md            # Project overview and results. (This file)
└── data/
    └── heart.csv        # The original dataset used for the analysis.
```
