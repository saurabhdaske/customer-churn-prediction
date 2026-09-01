# Customer Churn Prediction

A machine learning project that predicts customer churn and identifies high-risk customer segments to support targeted retention strategies.

## 📌 Project Overview

Customer churn refers to customers discontinuing a company's services.

The objective of this project is to analyze customer characteristics, service usage, contract type, tenure, and payment behavior to identify factors associated with churn and build machine learning models that can predict customers who are likely to churn.

## 🎯 Business Problem

Customer retention is generally more cost-effective than acquiring new customers. Therefore, identifying customers who are at higher risk of leaving can help businesses:

- Prioritize retention efforts
- Target high-risk customer segments
- Improve customer experience
- Reduce potential revenue loss
- Make data-driven retention decisions

## 📊 Dataset

This project uses the **Telco Customer Churn** dataset.

- **Rows:** 7,043
- **Columns:** 21
- **Target variable:** `Churn`
- **Churn = 1:** Customer churned
- **Churn = 0:** Customer did not churn

The dataset contains customer demographics, account information, services, contract details, payment methods, and billing information.

## 🔍 Exploratory Data Analysis

The analysis examined:

- Overall churn distribution
- Contract type and churn
- Customer tenure and churn
- Internet service and churn
- Payment method and churn
- Contract type combined with tenure
- Internet service combined with contract type
- Payment method combined with contract type

### Key Findings

- Month-to-month customers have substantially higher churn than customers on longer-term contracts.
- Customers in their first 12 months show the highest observed churn.
- Month-to-month customers with early tenure represent a particularly high-risk segment.
- Fiber-optic customers on month-to-month contracts show elevated churn.
- Electronic-check users on month-to-month contracts also show elevated churn.

## 🤖 Machine Learning

Two classification models were trained and evaluated:

1. Logistic Regression
2. Random Forest

### Data Preprocessing

The preprocessing workflow included:

- Converting `Churn` from categorical values (`Yes`/`No`) into binary values
- Converting categorical variables into numerical dummy variables
- Excluding `customerID` from model features
- Excluding the exploratory `TenureGroup` variable from model features
- Splitting the dataset into training and testing sets
- Using stratification to maintain the churn distribution

## 📈 Model Performance

The models were evaluated using accuracy, precision, recall, and F1 score.

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.801 | 0.646 | 0.556 | 0.598 |
| Random Forest | 0.785 | 0.618 | 0.497 | 0.551 |

### Selected Model

**Logistic Regression** was selected as the preferred model because it achieved better performance than Random Forest across accuracy, precision, recall, and F1 score on the test dataset.

## 🎚️ Threshold Analysis

The default classification threshold of **0.50** was compared with a lower threshold of **0.30**.

At a threshold of 0.30:

- **Recall increased:** 55.61% → 75.13%
- **Precision decreased:** 64.60% → 52.42%
- **False negatives decreased:** 166 → 93

This demonstrates that classification thresholds can be adjusted according to business priorities.

For a retention-focused business problem, accepting more false positives may be reasonable if the cost of missing a potential churner is high.

## 💡 Business Recommendations

Based on the analysis, retention efforts should prioritize:

1. **Early-tenure customers**  
   Introduce stronger onboarding, early engagement, and targeted retention offers during the first year.

2. **Month-to-month customers**  
   Encourage customers to consider longer-term contracts through appropriate incentives.

3. **Month-to-month + early-tenure customers**  
   Prioritize this combination as one of the highest-risk customer segments.

4. **Fiber-optic + month-to-month customers**  
   Investigate service quality and customer experience while prioritizing retention outreach.

5. **Electronic-check + month-to-month customers**  
   Investigate payment experience and encourage alternative payment methods where appropriate.

6. **Use a lower prediction threshold when appropriate**  
   A threshold of 0.30 can help identify more potential churners when minimizing false negatives is more important than maximizing precision.

## Conclusion

This project developed a customer churn prediction model using the Telco Customer Churn dataset.

Logistic Regression was selected as the preferred model, achieving approximately 80.1% accuracy and 55.6% recall on the test set. The analysis identified month-to-month customers, early-tenure customers, fiber-optic users, and electronic-check users as important high-risk segments.

The results demonstrate how machine learning can support targeted customer retention strategies and help businesses prioritize customers who are more likely to churn.

## Future Improvements

- Perform hyperparameter tuning for Logistic Regression and Random Forest.
- Evaluate additional models such as XGBoost and Gradient Boosting.
- Use cross-validation for more robust model evaluation.
- Address class imbalance using appropriate techniques.
- Optimize the classification threshold based on business costs.
- Deploy the model through an API or dashboard for practical use.

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## 📁 Project Structure

```text
customer-churn-prediction/
│
├── Customer_Churn_Prediction.ipynb
├── README.md
└── .gitignore
