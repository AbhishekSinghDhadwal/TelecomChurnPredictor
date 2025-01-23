
# Telecom Churn Prediction

## Overview
This project aims to predict customer churn for a telecom company by analyzing customer behavior over a four-month period. The goal is to identify high-value customers who are at risk of churning and recommend actionable strategies to improve customer retention.

---

## Problem Statement
In the highly competitive telecom industry, customer churn poses significant challenges. Acquiring new customers costs 5-10 times more than retaining existing ones. Predicting churn, especially for prepaid customers, is critical as they can leave without formal notice. This project focuses on the Indian and Southeast Asian markets, where the prepaid model dominates. 

### Definitions of Churn:
- **Revenue-based churn**: Customers generating minimal or no revenue.
- **Usage-based churn**: Customers with no incoming/outgoing calls or internet usage over a defined period.

### Objective:
- Predict churn in the 9th month based on data from months 6, 7, and 8.
- Identify key indicators of churn.

---

## Dataset
The dataset contains customer-level information over four months:
- **Columns**: 226 features, including usage patterns, recharge amounts, and customer demographics.
- **Rows**: ~100,000 customer records.

### Key Details:
- **Monthly Encodings**: June (6), July (7), August (8), and September (9).
- **High-Value Customers**: Defined as those whose average recharge in the first two months is above the 70th percentile.
- **Target Variable**: Churn (1 if the customer stopped using services in month 9, 0 otherwise).

Refer to the included Data Dictionary for details on column abbreviations and meanings.

---

## Methodology
### Data Preparation
1. **Initial Cleanup**:
   - Removed non-predictive columns (e.g., `mobile_number`, `circle_id`).
   - Addressed missing values through imputation or column removal.
2. **Feature Engineering**:
   - Derived metrics such as average revenue, total usage, and recharge patterns.
   - Tagged high-value customers.

### Exploratory Data Analysis (EDA)
- Analyzed data distributions and correlations.
- Segmented customers by usage and revenue metrics.

### Target Definition
- Churn is defined by the absence of calls and internet usage in the churn phase (month 9).

### Dimensionality Reduction
- Applied **Principal Component Analysis (PCA)** to reduce 226 features into a smaller set of components while retaining variance.

### Modeling
1. **Algorithms**:
   - Logistic Regression (baseline).
   - Random Forest, Gradient Boosting (e.g., XGBoost).
2. **Class Imbalance Handling**:
   - Used SMOTE and class weighting techniques.
3. **Evaluation Metrics**:
   - Precision, Recall, F1-Score, and AUC-ROC.

### Model Evaluation and Insights
- Selected the best-performing model based on evaluation metrics.
- Identified significant predictors of churn using feature importance (e.g., decision trees) and regression coefficients.

---

## Results
- **Best Model**: Gradient Boosting with an AUC-ROC of 0.85.
- **Key Indicators of Churn**:
   - Decline in recharge amounts.
   - Reduced call and internet usage in the action phase.
- **Recommendations**:
   - Offer retention incentives to high-risk customers.
   - Monitor declining usage patterns for early intervention.

---

## Project Pipeline
1. **Data Collection**: Load and clean telecom customer data.
2. **EDA and Feature Engineering**: Derive meaningful metrics and segment customers.
3. **Model Building**:
   - Apply dimensionality reduction.
   - Train and tune predictive models.
4. **Evaluation**: Assess models based on business-centric metrics.
5. **Insights and Recommendations**: Use findings to propose retention strategies.

---

## Requirements
- Python Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `imbalanced-learn`

