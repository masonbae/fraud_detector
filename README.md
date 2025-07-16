# 💳 Credit Card Fraud Detection

This project identifies fraudulent financial transactions using machine learning, data preprocessing, and exploratory analysis. It uses a real-world, imbalanced dataset and builds a scikit-learn pipeline to automate feature processing and model training. I used this project to learn the weaknesses of an imbalanced dataset and to use these lessons in my next project.

---

## 📊 Dataset

- **Source:** Synthetic dataset with ~6.3 million transactions
- **Columns:** Transaction type, amount, sender/receiver balances, fraud flag
- **Target:** `isFraud` (1 = fraudulent, 0 = legitimate)
- **Imbalance:** Only 0.13% of transactions are fraudulent

---

## 🔍 Exploratory Data Analysis

- Identified fraud occurs almost exclusively in `TRANSFER` and `CASH_OUT` transactions
- Created histograms, bar charts, and correlation heatmaps
- Engineered new features like:
  - `balanceDiffOrig` = sender's balance drop
  - `balanceDiffDest` = receiver's balance gain
- Discovered that many fraud cases leave the sender’s balance at zero

---

## 🧠 Model Pipeline

Built a scikit-learn pipeline with:

- **Preprocessing:**
  - StandardScaler for numeric features
  - OneHotEncoder for transaction type
- **Model:**
  - Logistic Regression with `class_weight='balanced'` to attempt to address class imbalance

---

## 📈 Model Performance

**Logistic Regression Results (on 30% test set):**

| Metric        | Legitimate (0) | Fraudulent (1) | Overall      |
|---------------|----------------|----------------|--------------|
| Precision     | 100%           | **2%**         |              |
| Recall        | 95%            | **95%**        |              |
| F1-Score      | 97%            | **4%**         |              |
| Accuracy      |                |                | **94.65%**   |




**Key Takeaways:**  
✅ High recall = catches most frauds  
⚠️ Low precision = many false alarms and room for improvement using better models or tuning thresholds

---
### 🧮 Confusion Matrix

|                                | 🔍 **Predicted: Not Fraud** | 🚨 **Predicted: Fraud** |
|--------------------------------|-----------------------------|--------------------------|
| ✅ **Actual: Not Fraud**       | 1,804,310 (94.5%)           | 102,012 (5.3%)           |
| ❌ **Actual: Fraud**           | 133 (0.007%)                | 2,331 (0.12%)            |

**Totals:**
- Test Samples: 1,908,786  
- Fraud Cases: 2,464 (~0.13% of total)  
- Non-Fraud Cases: 1,906,322

-

### 🧪 Future Improvements
- Use XGBoost or another model for better precision
- Tune Classification Threshold: Adjust probability cutoff to optimize for precision or F1-score using precision-recall curves
- derive new features from the time such as transaction hour
    




