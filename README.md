# 💰 Loan-Default-Risk-Analysis

### A Data-Driven Framework for Credit Risk Mitigation

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Library](https://img.shields.io/badge/Library-Pandas-150458)
![Status](https://img.shields.io/badge/Status-Completed-green)

---

## 📋 Executive Summary
In the lending industry, minimizing Non-Performing Loans (NPLs) is the primary lever for profitability. The objective of this project is to analyze a dataset of 20,000 loan records to identify the key behavioral and financial indicators that distinguish reliable borrowers from high-risk applicants.

Through rigorous **Exploratory Data Analysis (EDA)**, we extracted key insights that significantly enhance borrower profiling, allowing for a more granular understanding of risk beyond simple credit scores. Furthermore, the predictive model (Random Forest) developed on this foundation achieved an **Accuracy of ~90%** and an **ROC-AUC of 0.88**, providing a robust tool for automated loan underwriting.

**Target Variable Distribution:**
![Target Distribution](https://github.com/zava2000/Loan-Default-Risk-Insights/blob/main/Images/Image%205.png)

*The dataset shows a class imbalance (80% Paid vs 20% Default), which was addressed using stratified sampling and class-weighting techniques.*

---

## 💡 Key Risk Insights
Through correlation analysis and segmentation, we isolated the primary drivers of default. The "Heatmap of Correlation" below highlights the strongest predictors:

![Correlation Heatmap](https://github.com/zava2000/Loan-Default-Risk-Insights/blob/main/Images/Feature%20Correlation.png)

**Strategic Takeaways:**
1.  **Employment is the "Knockout" Factor:** Unemployment (`employment_status_Unemployed`) has a massive negative correlation (**-0.53**) with repayment. This is the single strongest predictor of default, suggesting that income verification is the most critical step in the approval funnel.
2.  **The "Debt Trap" (DTI):** Borrowers with a high **Debt-to-Income Ratio** are statistically more likely to default, regardless of their raw income level.
3.  **Credit Score Sensitivity:** There is a clear "risk cliff" below a FICO score of 680. Loans approved below this threshold show a sharp spike in delinquency rates.
4.  **Loan Purpose Risk:** Loans taken for **"Debt Consolidation"** carry a higher inherent risk than loans for "Home Improvement" or "Business," indicating that these borrowers are often already in financial distress.

---

## 📊 Project Methodology

### 1. Exploratory Data Analysis (EDA)
We visualized the borrower profile to understand the portfolio composition.
* **Key Drivers:** Investigated relationships between the main categories against our target variable.
  
![Financials](https://github.com/zava2000/Loan-Default-Risk-Insights/blob/main/Images/Image%206.png)

### 2. Feature Engineering
To prepare the data for modeling, we transformed qualitative risk factors into quantitative features:
* **Ordinal Encoding:** Applied to `education_level` and `grade_subgrade` to preserve the hierarchy of credit quality.
* **One-Hot Encoding:** Applied to nominal variables like `marital_status` and `loan_purpose`.

### 3. Predictive Modeling (Random Forest)
We deployed a **Random Forest Classifier** with `class_weight='balanced'` to penalize errors on the minority class (Defaulters).

---

## 📈 Model Performance & Strategy
The model is tuned to be **High Precision (95%)** for identifying defaults, making it an extremely conservative and safe filter.

| Metric | Score | Interpretation for Business |
| :--- | :--- | :--- |
| **Accuracy** | **90%** | The model correctly classifies 9 out of 10 applicants. |
| **ROC-AUC** | **0.88** | Excellent ability to rank borrowers from "Safe" to "Risky". |
| **Precision (Default)** | **0.95** | When the model predicts a default, it is **95% correct**. This ensures we don't reject good customers unnecessarily. |

### Borrower Profiling & Segmentation
Two distinct profiles emerged from the analysis:
* **The "Prime" Borrower:** Employed, Credit Score > 700, DTI < 20%. *Strategy:* Auto-approval with competitive interest rates to maximize acquisition.
* **The "Subprime" Risk:** Unemployed or Student, Credit Score < 650, Requesting Debt Consolidation. *Strategy:* Auto-rejection or requirement of a co-signer.

---

## 🛠️ Technologies Used
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn (RandomForestClassifier)
* **Environment:** Jupyter Notebook

-----

*This project was developed to demonstrate financial data analysis and credit risk assessment workflows.*
