Employee Turnover Prediction — Project Overview
================================================

1. Introduction
--------------
This project applies machine learning to predict employee turnover — the likelihood that an individual employee will voluntarily leave an organization within a given period.
Unlike attrition, which typically refers to involuntary or unplanned departures that are not immediately backfilled, turnover reflects voluntary resignation and carries significant organizational cost, such as:
   - increased recruitment and onboarding expenses
   - loss of institutional knowledge, 
   - disruption to team continuity.

By analyzing key HR factors, this project identifies patterns in employee behavior and produces a classification model capable of flagging employees at elevated risk of departure — enabling proactive retention strategies.

2. Dataset and Feature Overview
------------------------------
Source files:
   hr_analytics.csv — Raw HR dataset
   data.csv — Processed and encoded version used for modeling

Key predictive features span four domains:
   - Role and Tenure
   - Position, Years at Company, Years Since Last Promotion
   - Education level, Total Working Years
   - Relationship Satisfaction, Work-Life Balance, Number of Companies Worked
   - Marital Status, Age, Monthly Income, Monthly Rate, Stock Option Level


3. Project Structure
--------------------

The project is organized as follows:

   - data/ — Raw and processed datasets
   - notebooks/ — Six Jupyter notebooks covering EDA, preprocessing, modeling, evaluation, and interpretation
   - functions (.py files)— Modular utility functions, separated for readability and reuse
   - requirements/ — Serialized best model (.joblib format), ready for deployment in Streamlit
   - model_implementation notebook — Dedicated to loading and testing the saved model on unseen data

4. Preprocessing
----------------

The source data required encoding of categorical variables for model compatibility, but no extensive cleaning was necessary as the dataset arrived in good condition. A notable characteristic of the data is significant class imbalance: the majority of employees remained with the company, while a smaller proportion left. Rather than artificially correcting this imbalance through oversampling or undersampling techniques, the natural distribution was preserved — as it accurately reflects real-world conditions — and addressed through appropriate model selection instead.

5. Exploratory Data Analysis
----------------------------

EDA combined summary statistics with visualizations to understand feature distributions and the degree of class imbalance. Findings confirmed that retained employees substantially outnumber those who departed, reinforcing the decision to select a model well-suited to imbalanced classification tasks.

6. Model Selection and Evaluation
---------------------------------

Algorithm: Random Forest Classifier
Random Forest was selected for its robustness to class imbalance and its ability to model non-linear relationships without requiring resampling techniques. Hyperparameter tuning was performed using GridSearchCV to identify the optimal model configuration prior to final fitting.
Performance:

Accuracy: 0.85 — a strong result, particularly when considered alongside precision and recall metrics
Classification Report: Full per-class metrics are available in notebooks/3_model_selection


7. Model Interpretation
------------------------

Detailed performance interpretation, including feature importance analysis and per-class evaluation, is documented in notebooks/3_model_selection.

8. Model Storage
----------------

The best-performing model is serialized using joblib and stored in the requirements/ directory. It can be loaded and applied directly to any compatible dataset for inference.

9. References 
-------------
S. Flowers (1974), Why Employees Stay. Retrieved from: https://hbr.org/1973/07/why-employees-stay
Dataset: Link: https://www.kaggle.com/datasets/thedevastator/employee-attrition-and-factors
