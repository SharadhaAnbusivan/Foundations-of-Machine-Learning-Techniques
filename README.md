# Network Intrusion Detection using Logistic Regression

## Index

1. Overview
2. Dataset
3. Target Variable
4. Feature Engineering
5. Model Selection
6. Model Training
7. Model Evaluation
8. Cross-Validation
9. Model Saving
10. Test Dataset Prediction
11. Tools & Libraries
12. Conclusion

---

## 1. Overview

This project performs **binary classification** to detect network intrusions.
Each network packet is classified as either:

* `0` → Normal traffic
* `1` → Intrusion

Logistic Regression is used, and performance is evaluated mainly using the **AUC metric**.

---

## 2. Dataset

The dataset contains two files:

* `network_train.csv` – Training data with features and labels
* `network_test.csv` – Test data without labels

---

## 3. Target Variable

**Intrusion_Detected**

* `0` → Normal packet
* `1` → Intrusion detected

---

## 4. Feature Engineering

The following steps were applied:

1. Dropped `Packet_ID`
2. Split data into features (`X`) and target (`y`)
3. Handled missing values using **median imputation**
4. Standardised numerical features using **StandardScaler**

---

## 5. Model Selection

**Model Used:** Logistic Regression

**Reasons for selection:**

* Suitable for binary classification
* Produces probability outputs (required for AUC)
* Handles large and imbalanced datasets well
* Computationally efficient and interpretable

**Model Parameters:**

* `class_weight = 'balanced'`
* `penalty = 'l2'`
* `max_iter = 1000`

---

## 6. Model Training

* Data split into **80% training** and **20% testing**
* **Stratified split** used to maintain class balance
* Model trained on scaled training data

---

## 7. Model Evaluation

The following evaluation techniques were used:

* Accuracy
* Confusion Matrix
* Precision, Recall, F1-Score
* ROC-AUC Score
* ROC Curve

**Observed Performance:**

* Test AUC ≈ **0.97**

---

## 8. Cross-Validation

* **5-Fold Stratified Cross-Validation**
* Evaluation metric: **ROC-AUC**
* Ensures balanced class distribution across folds

**Mean CV AUC ≈ 0.98**

---

## 9. Model Saving

The trained components were saved using `joblib`:

* `trained_model.pkl` – Trained Logistic Regression model
* `scaler.pkl` – Trained StandardScaler

These ensure consistent preprocessing during inference.

---

## 10. Test Dataset Prediction

* Applied the same preprocessing pipeline
* Generated **probability predictions** using `predict_proba`
* Created Kaggle-compatible submission file with:

```
Packet_ID,Intrusion_Detected
```

---

## 11. Tools & Libraries Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Joblib

---

## 12. Conclusion

The Logistic Regression model achieved a **high AUC score**, indicating strong intrusion detection capability.
The pipeline is simple, reproducible, and suitable for real-world network security applications.
