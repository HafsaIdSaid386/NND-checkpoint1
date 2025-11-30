# NND-checkpoint1

# 📘 **Checkpoint 1 – Model & Data Ready**

This repository contains the work completed for **Checkpoint 1** of the AI Retention Radar project.
The goal of this checkpoint is to prepare the dataset, preprocess it, train baseline models,
and ensure that the machine learning pipeline is fully functional.

---

# 📊 **1. Dataset Overview**

* **Rows:** 5,630 customers
* **Columns:** 20 features
* **Target:** `Churn` (0 = Not churned, 1 = Churned)

Features include:

* Customer demographics
* App engagement
* Order history
* Satisfaction score
* Complaint behavior
* Logistics (WarehouseToHome distance)

---

# 🔧 **2. Preprocessing (Full Pipeline)**

A complete preprocessing pipeline was built using scikit-learn:

### **Numeric Features**

* Missing values → filled with **median**
* Scaling → **StandardScaler**

### **Categorical Features**

* Missing values → filled with **most frequent**
* Encoding → **OneHotEncoder**

### **Pipeline Summary**

A `ColumnTransformer` automatically applies all preprocessing
before sending the data to the model.

---

# 🧠 **3. Models Trained**

### ✔ **Baseline Model: Logistic Regression**

* Handles class imbalance with `class_weight='balanced'`
* Evaluated using:

  * AUC
  * Precision
  * Recall
  * Confusion Matrix

### ✔ **Neural Network Model: MLPClassifier**

TensorFlow could not be installed locally, so a shallow neural network
was implemented using **Scikit-Learn MLPClassifier**.

Network architecture:

* 1 hidden layer with 16 neurons
* ReLU activation
* Adam optimizer
* `max_iter=300`

Achieved strong performance with an AUC around **0.88**.

---

# 📈 **4. Model Performance Comparison**

| Model                | AUC Score |
| -------------------- | --------- |
| Logistic Regression  | ~0.82     |
| Neural Network (MLP) | ~0.88     |

The neural network performs the best and will be used in the next checkpoint.

---

# 🛠 **5. Challenges & How They Were Solved**

### **1. Missing Values**

Some features contained NaN values.
**Solution:** Added median/mode imputation inside the preprocessing pipeline.

### **2. Logistic Regression Error (NaN Not Allowed)**

The baseline model crashed due to missing values.
**Solution:** Fixed by adding imputation before scaling/encoding.

### **3. Many Categorical Variables**

Machine learning models cannot train on categories as text.
**Solution:** Applied OneHotEncoder.

### **4. TensorFlow Installation Failure**

TensorFlow was not supported in the local environment.
**Solution:** Switched to Scikit-Learn’s MLPClassifier for the neural network.

### **5. Neural Network Convergence Warning**

This is expected for shallow NNs.
**Solution:** Increased `max_iter`; performance still strong.


