# Network Intrusion Detection using Logistic Regression

## Index

1. Overview & Dataset
2. Feature Engineering
3. Model Selection & Training
4. Model Evaluation & Cross-Validation
5. Test Prediction & Submission
6. Conclusion

---

## 1. Overview & Dataset

This project performs **binary classification** to detect network intrusions in packet-level data.

* **Training file:** `network_train.csv`
* **Test file:** `network_test.csv`
* **Target:** `Intrusion_Detected`

  * `0` → Normal
  * `1` → Intrusion
* **Dropped column:** `Packet_ID` (used only for submission)

The model is evaluated using **AUC**, as required by Kaggle.

---

## 2. Feature Engineering

The following preprocessing steps were applied:

* Removed non-informative identifier (`Packet_ID`)
* Split data into features (`X`) and target (`y`)
* Missing values handled using **median imputation**
* Feature scaling using **StandardScaler**

---

## 3. Model Selection & Training

**Model used:** Logistic Regression

**Reasons:**

* Suitable for binary classification
* Outputs probabilities for AUC computation
* Handles imbalanced data efficiently

**Configuration:**

* `class_weight = 'balanced'`
* `penalty = 'l2'`
* `max_iter = 1000`

**Training setup:**

* 80–20 stratified train-test split
* Model trained on scaled data

---

## 4. Model Evaluation & Cross-Validation

The model was evaluated using:

* Accuracy
* Confusion Matrix
* Precision, Recall, F1-score
* ROC-AUC score
* ROC Curve
* **5-Fold Stratified Cross-Validation (AUC metric)**

**Results:**

* Test AUC ≈ **0.97**
* Mean CV AUC ≈ **0.98**

AUC was chosen due to class imbalance and Kaggle evaluation criteria.

---

## 5. Test Prediction & Submission

* Applied the same preprocessing steps to test data
* Generated **probability predictions** using `predict_proba`
* Created Kaggle-compatible submission file

---

## 6. Conclusion

The Logistic Regression model achieved a **high AUC**, demonstrating effective intrusion detection.
The pipeline is simple, efficient, and suitable for real-world network security tasks.
