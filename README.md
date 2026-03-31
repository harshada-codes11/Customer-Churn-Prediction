# 📊 Customer Churn Prediction using Machine Learning

> ** AI/ML Domain | March 2026**

---

## 🎯 Project Overview

Customer churn prediction is a critical business problem in the telecom industry. This project uses Machine Learning to predict whether a customer will churn (leave the service) based on their demographic, subscription, and billing information.

**Goal:** Build a robust ML pipeline that helps telecom companies proactively identify at-risk customers and take retention actions before they churn.

---

## 📁 Project Structure

```
Customer-Churn-Prediction/
│
├── Customer_Churn_Prediction.ipynb       # Main Google Colab Notebook
├── WA_Fn-UseC_-Telco-Customer-Churn.csv  # Dataset
├── Customer_Churn_Prediction_Report.docx # Project Report (Word Document)
├── Customer_Churn_Prediction_Presentation.pptx  # Presentation (10+ slides)
├── customer_churn_model.pkl              # Saved Trained Model (generated after running notebook)
└── README.md                             # This file
```

---

## 📊 Dataset

| Attribute | Detail |
|-----------|--------|
| **Source** | IBM Telco Customer Churn (Kaggle) |
| **Records** | 7,043 customers |
| **Features** | 21 columns |
| **Target** | `Churn` (Yes/No → 1/0) |
| **Churn Rate** | ~26.5% (class imbalance) |

**Key Features:**
- `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- `tenure`, `MonthlyCharges`, `TotalCharges`
- `Contract`, `PaymentMethod`, `InternetService`
- `OnlineSecurity`, `TechSupport`, `StreamingTV`, etc.

---

## 🔧 Technologies Used

| Tool/Library | Purpose |
|---|---|
| Python 3 | Programming Language |
| Google Colab | Development Environment |
| Pandas, NumPy | Data Manipulation |
| Matplotlib, Seaborn | Data Visualization |
| Scikit-learn | Machine Learning Models |
| Imbalanced-learn (SMOTE) | Class Imbalance Handling |
| Pickle | Model Serialization |

---

## 🔄 Project Workflow

```
Data Loading → EDA → Preprocessing → SMOTE → Model Training → Hyperparameter Tuning → Evaluation → Predictive System
```

### Step-by-Step:
1. **Data Loading & Understanding** — Load CSV, explore shape, data types, distributions
2. **Exploratory Data Analysis (EDA)** — Histograms, boxplots, countplots, correlation heatmap
3. **Data Preprocessing** — Handle missing values, Label Encoding, Train-Test Split (80/20)
4. **SMOTE** — Oversample minority class to fix imbalance (26.5% → 50%)
5. **Model Training** — 4 models with 5-Fold Stratified Cross-Validation
6. **Hyperparameter Tuning** — GridSearchCV on best model (Random Forest)
7. **Model Evaluation** — Accuracy, Precision, Recall, F1, ROC-AUC, Confusion Matrix
8. **Predictive System** — Save model with pickle, load & predict new customers

---

## 🤖 Models Trained

| Model | CV Accuracy |
|---|---|
| Logistic Regression | ~75% |
| Decision Tree | ~78% |
| **Random Forest ✅** | **~85%** |
| Gradient Boosting | ~83% |

> **Best Model:** Random Forest with GridSearchCV Hyperparameter Tuning

---

## 📈 Results (Best Model — Random Forest Tuned)

| Metric | Score |
|---|---|
| Accuracy | ~82% |
| Precision | ~75% |
| Recall | ~68% |
| F1 Score | ~71% |
| ROC-AUC | ~0.85 |

### Top Churn Predictors:
1. `tenure` — shorter tenure = higher churn risk
2. `TotalCharges` — billing history
3. `MonthlyCharges` — higher bills → higher churn
4. `Contract` — month-to-month contracts churn most
5. `PaymentMethod` — electronic check users churn more

---

## 🚀 How to Run

### Option 1: Google Colab (Recommended)
1. Open [Google Colab](https://colab.research.google.com/)
2. Upload `Customer_Churn_Prediction.ipynb`
3. Upload `WA_Fn-UseC_-Telco-Customer-Churn.csv` to the Colab session
4. Run all cells from top to bottom (`Runtime → Run all`)

### Option 2: Local (Jupyter)
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/Customer-Churn-Prediction.git
cd Customer-Churn-Prediction

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn

# Open notebook
jupyter notebook Customer_Churn_Prediction.ipynb
```

---

## 🔮 Predict for a New Customer

```python
import pickle
import pandas as pd

# Load model
with open('customer_churn_model.pkl', 'rb') as f:
    model_data = pickle.load(f)

# Sample customer data
customer = {
    'gender': 'Female', 'SeniorCitizen': 0, 'Partner': 'Yes',
    'Dependents': 'No', 'tenure': 1, 'PhoneService': 'No',
    'MultipleLines': 'No phone service', 'InternetService': 'DSL',
    'OnlineSecurity': 'No', 'OnlineBackup': 'Yes',
    'DeviceProtection': 'No', 'TechSupport': 'No',
    'StreamingTV': 'No', 'StreamingMovies': 'No',
    'Contract': 'Month-to-month', 'PaperlessBilling': 'Yes',
    'PaymentMethod': 'Electronic check',
    'MonthlyCharges': 29.85, 'TotalCharges': 29.85
}

# The predict_churn() function is defined in the notebook
# prediction, probability = predict_churn(customer)
```

---

## 📌 Key Insights

- Month-to-month contract customers have **>40% churn rate**
- Senior citizens churn **~41%** vs non-seniors **~24%**
- Customers without Online Security churn at **42%**
- Short-tenure customers (<12 months) are at **highest risk**
- SMOTE improved minority class recall by **~15%**

---

## 📚 References

- [IBM Telco Customer Churn Dataset — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Imbalanced-learn (SMOTE)](https://imbalanced-learn.org/)
- Chawla, N.V. et al. (2002). *SMOTE: Synthetic Minority Over-sampling Technique*
- Breiman, L. (2001). *Random Forests*. Machine Learning, 45(1), 5–32

---

## 👤 Author

**Harshada Patil**  
AI/ML | 2026  

---

