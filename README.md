# Unsupervised Anomaly Detection in Credit Card Transactions

## Resource Link
Dataset: Credit Card Fraud Detection  
Source: Kaggle  
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

---

## Project Title
**Unsupervised Learning: Anomaly Prediction in Credit Card Transactions**

---

## Problem Statement
Credit card fraud is a growing concern in the financial industry, causing significant financial losses. Detecting fraudulent transactions is challenging because fraud cases are extremely rare and labeled data is often unavailable or limited.  
This project applies **unsupervised learning techniques** to identify potentially fraudulent transactions by detecting unusual patterns and anomalies in transaction data, without using labels during training.

---

## Aim
To detect potential fraudulent credit card transactions using unsupervised learning techniques by identifying anomalies and unusual patterns in transaction data.

---

## Dataset Description
The dataset contains **284,807 transactions** with the following attributes:

- **Time**: Seconds elapsed between each transaction and the first transaction
- **V1 – V28**: Anonymized numerical features obtained using PCA (for privacy)
- **Amount**: Transaction amount
- **Class**: Target variable (1 = fraud, 0 = normal)

> Note: The `Class` label is **not used for training** and is only used for evaluation.

---

## Notebook Contents
- Dataset Information
- Exploratory Data Analysis (EDA)
- Preprocessing
- Dimensionality Reduction (PCA)
- Unsupervised Modeling
- Evaluation
- Insights
- Conclusion

---

## Exploratory Data Analysis
- **Time** shows a multimodal distribution, reflecting user activity patterns over time.
- **Amount** is highly right-skewed, with many small transactions and few very large ones.
- Boxplots reveal extreme outliers in `Amount`, making it a key feature for anomaly detection.
- The dataset is **highly imbalanced**, with fraud representing only ~0.17% of transactions.

---

## Preprocessing
- Removed the target variable to avoid data leakage.
- Applied **MinMaxScaler** for feature scaling.
- Standardized data using **StandardScaler**.
- Checked for null values (none found).
- Analyzed correlations between features.

---

## Dimensionality Reduction
- Applied **Principal Component Analysis (PCA)**.
- Retained **28 principal components**, capturing approximately **95% of the variance**.
- PCA helped reduce noise and improve anomaly detection performance.

---

## Model Used
### Isolation Forest
- Designed for anomaly detection in high-dimensional data.
- Explicit contamination rate set to match fraud ratio (~0.17%).

**Key Parameters:**
- `n_estimators = 200`
- `contamination = 0.0017`
- `random_state = 42`

---

## Results
- Total transactions flagged as anomalies: **485**
- The model successfully detected a large portion of fraudulent transactions.

---

## Evaluation Metrics
Since the dataset is highly imbalanced, evaluation focuses on recall rather than accuracy.

| Metric | Value |
|------|------|
| Precision | 0.0013 |
| Recall | 0.7480 |
| F1-score | 0.0026 |

### Interpretation
- **Recall (74.8%)**: The model detected nearly three-quarters of all fraud cases.
- **Precision is low**, which is expected in unsupervised anomaly detection with extreme class imbalance.
- The model favors catching fraud over minimizing false positives.

---

## Insights
- Most flagged anomalies involve **small transaction amounts**, but high-value transactions are also detected.
- Fraud can occur at **any time**, and anomalies are distributed across the entire timeline.
- Anomalies are detected not only due to extreme values but also due to **unusual feature combinations** in PCA space.
- Many flagged transactions are normal but statistically unusual, which is expected in unsupervised models.

---

## Conclusion
This project demonstrates that **unsupervised learning models**, particularly Isolation Forest, are effective for detecting rare fraudulent transactions in highly imbalanced datasets.  
By learning normal transaction patterns without labels, the model successfully identified anomalous behavior and achieved high recall in detecting fraud. Although precision is low due to the rarity of fraud and the unsupervised approach, the results confirm that unsupervised anomaly detection is a powerful and practical solution for real-world fraud detection where labeled data is limited.

---

## Technologies Used
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn

---

## Author
**Esraa Naji**
