# Customer Loan Eligibility Analysis

This project involves exploratory data analysis (EDA) and predictive modeling to identify customers who might benefit from loan offers. The task focuses on analyzing demographic, transactional, and loan application data to build and evaluate machine learning models.

## Problem Statement

Given datasets about customers (`customers.parquet`), their transaction histories (`transactions.parquet`), and loan application outcomes (`loans.parquet`), the goal was to:

1. Assess data quality and explore patterns in the data.
2. Engineer features that summarize customer behavior and characteristics.
3. Train and evaluate machine learning models to predict loan eligibility.

## Approach

1. **Exploratory Data Analysis**:
   - Investigated data quality, handled missing values, and explored the distribution of key variables.
   - Analyzed patterns in customer balance movements and loan outcomes to identify actionable insights.

2. **Feature Engineering**:
   - Aggregated transaction data to create customer-level features:
     - Average balance and balance slope over time.
     - Income and balance intercept metrics.
   - Created additional features like `loan-to-income ratio`.

3. **Modeling & Evaluation**:
   - Trained multiple classification models:
     - Logistic Regression
     - Random Forest
     - XGBoost
   - Evaluated performance using metrics: **Accuracy, Precision, Recall, F1 Score, and ROC AUC**.

   | Model              | Accuracy | Precision | Recall  | F1 Score | ROC AUC |
   |--------------------|----------|-----------|---------|----------|---------|
   | Logistic Regression| 0.829    | 0.862     | 0.748   | 0.801    | 0.823   |
   | Random Forest      | 0.884    | 0.928     | 0.811   | 0.866    | 0.878   |
   | XGBoost            | 0.875    | 0.920     | 0.799   | 0.855    | 0.869   |

   - **Random Forest** demonstrated the best performance across all key metrics, even without hyperparameter tuning.

4. **Feature Importance**:
   - Identified **`Balance`** as the most important predictor of loan eligibility across all models.
   - Other significant features included `Income`, `Balance Slope`, and `Balance Intercept`.

## Results

- Random Forest achieved the best F1 Score of **0.866** and ROC AUC of **0.878**, making it the top-performing model.
- **Current Balance** was the most important feature influencing predictions, followed by balance slope and intercept.

## Conclusions

The models successfully identify key predictors of loan eligibility. This solution can be further improved by:
- Exploring advanced methods for handling null values.
- Experimenting with additional time-based features (e.g., transaction frequency over time windows).
- Hyperparameter tuning for model optimization.
- Incorporating sequence-based models like LSTMs to analyze balance changes over time.
- Addressing any potential biases in the loan approval process.
