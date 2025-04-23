# CreditCardFraudDetection
Machine Learning Task2: Credit Card Fraud Detection Assignment

1. Project Objective
The objective of this project is to build a machine learning model capable of detecting fraudulent credit card transactions with high accuracy, especially minimizing false positives while maintaining a strong ROC AUC score (above 0.85).

2. Dataset
Source: KaggleHub Dataset - kartik2112/fraud-detection
Contains transaction-level records, including time, amount, location, user details, and a binary target is_fraud (1 for fraud, 0 otherwise).
The dataset is highly imbalanced, with fraudulent transactions forming a very small portion.

3. Preprocessing & Feature Engineering
Converted transaction timestamps to datetime format and extracted hour, day, and weekday features to capture temporal patterns in fraud.
Categorical columns such as category, merchant, gender, etc., were label encoded for model compatibility.
Irrelevant or personally identifiable information (PII) such as first, last, cc_num were removed.
Transaction amounts were standardized using StandardScaler.

4. Modeling
Two classifiers were trained:
Logistic Regression (with class weights to handle imbalance)
XGBoost Classifier (with scale_pos_weight to address class imbalance)

Evaluation metrics:
Classification report with precision, recall, f1-score
Confusion Matrix
ROC AUC Score
The XGBoost model outperformed Logistic Regression in ROC AUC and was selected as the best model.

5. Error Analysis
False Positives (predicted fraud but actually legit) and False Negatives (predicted legit but actually fraud) were analyzed separately.
Subsets of both were saved for further manual or business rule inspection:
false_positives.csv
false_negatives.csv

6. Model Explainability (SHAP)
To interpret model predictions:
SHAP (SHapley Additive exPlanations) was used to break down feature contributions to individual predictions.
A force plot was generated to explain one false positive, providing insight into why the model considered a legitimate transaction as fraudulent.
This helps in improving trust and debugging the model.

