# Stroke Risk Prediction Using Interpretable Machine Learning

## Overview
Stroke is a leading cause of morbidity and mortality worldwide. Early identification of individuals at elevated stroke risk enables timely clinical intervention and preventive care.

This project investigates whether classical, interpretable machine learning models can reliably predict stroke occurrence using routinely collected clinical and demographic variables. Particular emphasis is placed on handling severe class imbalance and ensuring model interpretability suitable for biomedical research contexts.


## Research Question
Can interpretable machine learning models identify patients at high risk of stroke from structured clinical data, despite substantial class imbalance?



## Dataset
**Source:** Brain Stroke Dataset (Kaggle)  
https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset  

- **Sample size:** 5,110 patients  
- **Target variable:** `stroke`  
  - 0 = no stroke  
  - 1 = stroke  
- **Stroke prevalence:** ~5%

### Key Features
- Age  
- Hypertension  
- Heart disease  
- Average glucose level  
- Body mass index (BMI)  
- Smoking status  
- Demographic variables  

The dataset is observational and highly imbalanced, reflecting real-world stroke incidence.


## Methods

### Data Preprocessing
- Removal of non-informative identifiers  
- Median imputation for missing BMI values  
- One-hot encoding of categorical variables  
- Feature standardization  
- Stratified train–test split (70/30)

### Handling Class Imbalance
- Baseline training on original imbalanced data  
- Class-weighted learning  
- Synthetic Minority Oversampling Technique (SMOTE), applied **only to training data**

### Models
- **Logistic Regression**  
  Baseline model emphasizing interpretability and calibrated risk estimation  
- **Random Forest**  
  Nonlinear comparator to assess performance trade-offs

### Evaluation Metrics
- ROC-AUC (primary metric)  
- Precision, recall, F1-score  
- Confusion matrix  

Accuracy is reported but not treated as a primary metric due to class imbalance.



## Results

| Model | Balancing Strategy | ROC-AUC | Stroke Recall |
|------|-------------------|--------|---------------|
| Logistic Regression | Class-weighted | ~0.84 | ~79% |
| Logistic Regression | SMOTE | ~0.83 | ~77% |
| Random Forest | SMOTE | ~0.76 | ~17% |

### Key Observations
- Logistic Regression achieves substantially higher sensitivity to stroke cases  
- Random Forest attains higher overall accuracy but fails to identify minority-class events  
- Accuracy alone is misleading in highly imbalanced clinical datasets  



## Model Interpretability

SHAP (SHapley Additive exPlanations) was used to analyze both **global feature importance** and **patient-level risk attribution**.

### Global Feature Importance
![Global SHAP Feature Importance (Bar)](figures/shap_global_bar.png)

### Feature Impact Distribution
![Global SHAP Beeswarm](figures/shap_global_beeswarm.png)

### Local Explanation: Highest-Risk Patient
![Local SHAP Explanation](figures/shap_local_highest_risk.png)

### Dominant Predictors of Stroke Risk
- Age  
- Average glucose level  
- Hypertension  
- Heart disease  
- Body mass index (BMI)  

These predictors align with established clinical risk factors, supporting the plausibility and interpretability of the model outputs.

Local SHAP analysis further demonstrates how individual patient characteristics drive high-risk predictions.


## Limitations
- Single observational dataset  
- Moderate sample size  
- Absence of temporal or longitudinal measurements  
- Synthetic oversampling may introduce distributional artifacts  



## Future Work
- Validation on multi-center or population-scale datasets  
- Time-to-event or survival modeling approaches  
- Temporal modeling of physiological trajectories  
- Comparison with established clinical risk scoring systems  



## Repository Structure
```text
.
├── notebooks/
│   └── stroke_prediction_pipeline.ipynb
├── figures/
│   ├── shap_global_bar.png
│   ├── shap_global_beeswarm.png
│   └── shap_local_highest_risk.png
├── README.md
