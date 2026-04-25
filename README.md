# 📊 Telco Customer Churn Prediction

This project analyzes customer churn behavior in a telecommunications company and builds a machine learning model to identify customers at high risk of leaving.

---

## 🎯 Objective

The goal of this project is to:

- Understand the key factors that drive customer churn
- Build a predictive model to identify customers likely to churn
- Provide actionable insights to support retention strategies

---

## 📂 Dataset

The dataset comes from Kaggle:

**Telco Customer Churn Dataset**

It contains information about:
- Customer demographics
- Services subscribed
- Account information
- Churn status (target variable)

The dataset is loaded directly from GitHub for reproducibility.

The dataset comes from Kaggle:
https://www.kaggle.com/datasets/blastchar/telco-customer-churn


---

## 🔍 Exploratory Data Analysis (EDA)

### Key insights from categorical features:

- **Contract type** is one of the strongest predictors  
  → Month-to-month customers show significantly higher churn

- **Payment method**  
  → Customers using electronic check have higher churn

- **Internet service**  
  → Fiber optic customers exhibit higher churn

- **Additional services (OnlineSecurity, TechSupport, etc.)**  
  → Lack of these services is strongly associated with churn

- Some features (PhoneService, Streaming, MultipleLines)  
  → Show weak or no clear relationship

---

### Key insights from numerical features:

- **Tenure**
  → Strong predictor  
  → New customers are much more likely to churn

- **MonthlyCharges**
  → Higher values are associated with churn  
  → However, significant overlap makes it a weak standalone predictor

- **TotalCharges**
  → Lower values are associated with churn  
  → Reflects shorter customer lifetime

📌 Important relationship:

TotalCharges ≈ tenure × MonthlyCharges


This reinforces that churn mostly happens early in the customer lifecycle.

---

## ⚙️ Modeling

The following models were evaluated:

- Decision Tree
- Random Forest
- XGBoost

Using:
- Cross-validation
- Hyperparameter tuning (GridSearchCV)

### Model selection:

- Random Forest → better F1 score  
- XGBoost → higher recall  

👉 XGBoost was selected because the business goal is to **maximize churn detection**

---

## 🎯 Threshold Optimization

The classification threshold was adjusted:

Default: 0.5 -> Final: 0.3


### Why?

In churn prediction:
- Missing a churn case = high cost
- False positive = acceptable

### Impact:

- Recall increased: **~0.76 → ~0.93**
- Precision decreased (expected trade-off)

---

## 📈 Model Performance

- **Accuracy:** ~0.64  
- **Recall (churn):** ~0.93  

👉 The model prioritizes recall over precision to better capture customers at risk.

---

## 🔍 Model Interpretation (SHAP)

SHAP analysis shows:

- **Contract (Month-to-month)** → strongest driver of churn  
- **Tenure** → low tenure increases churn  
- **Fiber optic service** → associated with higher churn  
- **Lack of OnlineSecurity / TechSupport** → increases churn  
- **MonthlyCharges** → higher values increase churn  
- **TotalCharges** → lower importance due to correlation with tenure and charges  

---

## 💡 Business Insights

- Focus retention strategies on **new customers**
- Encourage **long-term contracts**
- Promote **additional services** (security, support)
- Review **pricing strategy**
- Investigate **fiber optic customer experience**

---

## 🏁 Conclusion

The model effectively identifies customers at risk of churn and provides actionable insights that can support data-driven retention strategies.

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Seaborn, Matplotlib
- Scikit-learn
- XGBoost
- SHAP

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
```

Then run the notebook or script.

📌 Author

Rocío Yut