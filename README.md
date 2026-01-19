# Stroke Risk Prediction Using Interpretable Machine Learning

## Overview
Stroke is a major cause of morbidity and mortality worldwide. Early identification of individuals at elevated stroke risk may enable timely clinical intervention and preventive care.  
This project evaluates whether classical, interpretable machine learning models can predict stroke occurrence using routinely collected clinical and demographic variables, while explicitly addressing severe class imbalance.

---

## Research Question
Can interpretable machine learning models reliably identify patients at high risk of stroke from structured clinical data?

---

## Dataset
- **Source:** Brain Stroke Dataset (Kaggle)  
  https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
- **Sample size:** 5,110 patients
- **Target variable:** `stroke`  
  (0 = no stroke, 1 = stroke)
- **Key features:**  
  age, hypertension, heart disease, BMI, average glucose level, smoking status, demographic variables

> The dataset is observational and highly imbalanced (~5% stroke prevalence).

---

## Methods

### Data Preprocessing
- Removal of non-informative identifiers
- Median imputation for missing BMI values
- One-hot encoding of categorical variables
- Feature standardization
- Stratified train–test split (70/30)

### Handling Class Imbalance
- Baseline models trained on original data
- Class-weighted learning
- Synthetic Minority Oversampling Technique (SMOTE) applied to training data only

### Models
- Logistic Regression (baseline, interpretable)
- Random Forest (nonlinear comparator)

### Evaluation Metrics
- ROC-AUC (primary metric)
- Precision, recall, F1-score
- Confusion matrix

### Model Interpretability
- SHAP (SHapley Additive exPlanations)
- Global feature importance
- Patient-level feature contribution analysis

---

## Results

| Model | Balancing Strategy | ROC-AUC | Stroke Recall |
|------|------------------|--------|---------------|
| Logistic Regression | Class-weighted | ~0.84 | ~79% |
| Logistic Regression | SMOTE | ~0.83 | ~77% |
| Random Forest | SMOTE | ~0.76 | ~17% |

Key observations:
- Logistic Regression provides substantially higher sensitivity to stroke cases
- Random Forest achieves higher accuracy but fails to detect minority cases
- Accuracy alone is misleading due to class imbalance

---

## Model Interpretation
SHAP analysis identifies the most influential predictors of stroke risk:
- Age
- Average glucose level
- Hypertension
- Heart disease
- Body mass index (BMI)

These factors are consistent with established clinical risk factors, supporting the interpretability and plausibility of the model.

---

## Limitations
- Single observational dataset
- Limited sample size
- No temporal or longitudinal information
- Synthetic oversampling may introduce distributional artifacts

---

## Future Work
- Validation on multi-center datasets
- Time-to-event or survival analysis
- Temporal modeling of physiological trajectories
- Comparison with clinical risk scoring systems

---


