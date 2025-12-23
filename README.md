# Heart Disease Prediction Using Machine Learning

## Background
Heart disease is a leading cause of mortality worldwide. Predicting disease outcomes using clinical features can help early intervention.

## Research Question
Can machine learning models accurately predict the presence of heart disease based on patient clinical data?

## Dataset
- Source: Heart Disease UCI Dataset (Kaggle)  
  https://www.kaggle.com/datasets/redwankarimsony/heart-disease-data
- Features: age, sex, cholesterol, blood pressure, etc.
- Target: presence of heart disease

## Methods
1. Data preprocessing: handle missing values, encode categorical features, scale numeric features
2. Models: Logistic Regression (baseline), Random Forest (advanced)
3. Evaluation metrics: Accuracy, ROC-AUC, Confusion Matrix, Classification Report
4. Interpretability: SHAP values for feature contribution

## Results
- Accuracy & ROC-AUC comparison between models
- Feature importance visualizations
- Interpretation of top contributing clinical factors

## Discussion
- Top features align with known risk factors (age, cholesterol, blood pressure)
- Limitations: small dataset, observational bias
- Future Work: larger datasets, multi-hospital validation, survival analysis
