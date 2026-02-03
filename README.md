# Beneficiary Credit Scoring System

An explainable machine learning–based credit scoring system designed to support fair and transparent concessional lending.  
The system evaluates **beneficiary risk and financial need** by combining historical repayment behavior with proxy-based income assessment.

---

## Problem Statement

Traditional credit scoring systems rely heavily on formal income proofs and credit history, which often excludes beneficiaries from underserved or informal sectors. For concessional lending programs, it is important to ensure that loans reach **genuine low-income beneficiaries** while also managing **repayment risk**.

This project aims to build a transparent, data-driven credit evaluation framework that balances **risk control** and **financial inclusion**.

---

## Solution Overview

The system is designed as a **two-stage credit assessment framework**:

### 1. Repayment Risk Modeling
- Predicts the probability of loan default using historical loan and repayment data.
- Evaluated multiple models:
  - Logistic Regression (baseline)
  - Random Forest (non-linear benchmark)
  - HistGradientBoosting (final model)
- Addressed class imbalance using sample-weighted training.
- Tuned decision threshold to balance recall and precision based on business requirements.

### 2. Income Proxy Assessment (Upcoming)
- Estimates income category using proxy indicators (e.g., consumption-based signals).
- Helps identify beneficiaries with high financial need despite limited formal income data.

---

## Final Model Performance (Repayment Risk)

The repayment risk model was evaluated on a held-out test set.  
HistGradientBoosting was selected as the final model due to its superior ranking performance and balanced risk detection.

- **ROC-AUC:** ~0.76  
- **Recall (Defaulters):** ~81%  
- **Precision (Defaulters):** ~22%  
- **Decision Threshold:** 0.45  

The model prioritizes **high recall** to avoid missing risky borrowers, while improving precision through threshold tuning.

---

## Model Comparison Summary

| Model | ROC-AUC | Recall (Defaulters) | Precision (Defaulters) | Remarks |
|------|--------|-------------------|-----------------------|--------|
| Logistic Regression | ~0.71 | High | Low | Explainable baseline |
| Random Forest | ~0.73 | High | Low | Captures non-linear patterns |
| **HistGradientBoosting (Final)** | **~0.76** | **High** | **Improved** | Best trade-off & scalable |

---

## Key Design Highlights

- Leakage-free feature selection (only data available at loan approval time)
- Explicit handling of class imbalance
- Threshold-based decisioning aligned with lending risk tolerance
- Modular and extensible pipeline for re-scoring and future integration
- Emphasis on transparency and explainability

---

## Tech Stack

- **Language:** Python  
- **Libraries:** Pandas, NumPy, Scikit-learn  
- **Environment:** Jupyter Notebook  

---

## Project Status

- Repayment risk model: **Completed**
- Income proxy modeling: **In progress**
- Composite credit score & risk banding: **Planned**
- UI / API integration: **Planned**

---

## Future Work

- Train income proxy model using alternative consumption data
- Combine repayment risk and income proxy into a composite credit score
- Assign beneficiaries to risk–need bands (e.g., Low Risk–High Need)
- Build a simple dashboard or API for score visualization
