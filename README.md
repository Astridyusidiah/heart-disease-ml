# Stroke Risk Prediction Using Interpretable Machine Learning
# Overview

Stroke remains one of the leading causes of long-term disability and mortality worldwide. Early identification of individuals at elevated risk is critical for prevention and timely intervention.

This project evaluates whether classical, interpretable machine learning models can predict stroke occurrence using routinely collected demographic and clinical variables. Particular emphasis is placed on handling severe class imbalance and maintaining interpretability suitable for biomedical and public health research contexts.

# Research Objective

To assess whether interpretable machine learning models can reliably identify individuals at increased stroke risk in a highly imbalanced clinical dataset.

# Dataset

Source: Brain Stroke Dataset (Kaggle)

Sample size: 5,110 individuals

Target variable: stroke

0 = No stroke

1 = Stroke

Stroke prevalence: ~5%

The dataset is observational and reflects real-world class imbalance typical of stroke incidence.

# Features

-Age

-Hypertension

-Heart disease

-Average glucose level

-Body mass index (BMI)

-Smoking status

-Demographic and socioeconomic indicators

# Methods
Data Preprocessing

  -Removal of non-informative identifiers

  -Median imputation for missing BMI values

  -One-hot encoding of categorical variables

  -Standardization of continuous features

  -Stratified train–test split (70/30)

  -Handling Class Imbalance

Three strategies were evaluated:

  -Baseline training on the original imbalanced dataset

  -Class-weighted logistic regression

  -Synthetic Minority Oversampling Technique (SMOTE), applied only to training data

Models

-Logistic Regression
Chosen as the primary model due to interpretability and calibrated risk estimation.

-Random Forest
Used as a nonlinear comparator to assess performance trade-offs.

# Evaluation

-Primary metric: ROC-AUC

-Secondary metrics: Precision, recall, F1-score

-Accuracy is reported but not emphasized due to class imbalance.

# Results
Model	Balancing Strategy	ROC-AUC	Stroke Recall
Logistic Regression	Class-weighted	~0.84	~79%
Logistic Regression	SMOTE	~0.83	~77%
Random Forest	SMOTE	~0.79	~17%


# Key findings:

Logistic Regression achieved substantially higher sensitivity to stroke cases.

Random Forest attained higher overall accuracy but failed to identify most minority-class events.

Accuracy alone is misleading in imbalanced clinical datasets.

# Model Interpretability

SHAP (SHapley Additive Explanations) was used to assess global feature importance and feature impact distributions.

The most influential predictors of stroke risk were:

-Age

-Average glucose level

-Hypertension

-Heart disease

-Body mass index (BMI)

These findings are consistent with established clinical risk factors, supporting the clinical plausibility of the model.

![Global SHAP bar plot](figures/shap_global_beeswarm.png)
![Global SHAP bar plot](figures/shap_global_bar.png)

# Limitations

-Single observational dataset

-Moderate sample size

-No temporal or longitudinal information

-Synthetic oversampling may introduce distributional artifacts
