# 🌲 XGBoost Overview

## 📌 Motivation
Traditional ML algorithms struggled with **scalability** and **overfitting** when data volumes increased. XGBoost (Extreme Gradient Boosting), introduced in **2014**, addressed these issues with improvements in speed, flexibility, and performance.

XGBoost is not a new algorithm — it’s a **highly optimized library based on Gradient Boosting**, enhanced by Tianqi Chen.

---

## 📖 History of XGBoost

### 🌱 Why Gradient Boosting?
Gradient Boosting itself is:
- **Flexible**: Can optimize any differentiable loss function
- **High performance**
- **Robust**: Handles outliers and noise well
- **Supports missing values** internally

### 📈 Evolution of XGBoost
- **2014**: Initial version built for speed and large datasets
- **2016 Kaggle Boom**: In the Higgs Boson competition and others, 16 of 29 winners used XGBoost
- **Open Sourced**: Gained mass adoption and rapid development

---

## 🧩 Core Design Goals of XGBoost
- **Performance**
- **Scalability**
- **Flexibility** (cross-platform + cross-language)

---

## 🛠 Flexibility

### ✅ Cross-Platform
- Works on Linux, Windows, macOS

### ✅ Language Support
- Python, R, Java, Julia, Scala, C++, Rust
- Train in Python, deploy in Java — enabled by model serialization

### ✅ Tool Integration
- Compatible with: `NumPy`, `pandas`, `scikit-learn`, `SHAP`, `MLflow`, `Docker`, etc.

### ✅ Use Cases
- Classification
- Regression
- Time Series Forecasting
- Anomaly Detection
- Ranking Systems (e.g., Learning to Rank)

---

## ⚡ Speed Improvements

### 🧠 Parallel & Distributed Computing
- **Parallelized tree construction** using CPU threads
- **Column block structure** for fast access

### 🚀 Optimizations
1. **Optimized data structures** (e.g., DMatrix)
2. **Cache-aware access patterns**
3. **Out-of-core computation** for large datasets
4. **GPU acceleration**
5. **Distributed computing** using Spark/Ray/Dask

---

## 📊 Performance Features

### 1. Regularized Learning Objective
- Combines loss + regularization (`L1`, `L2`) to avoid overfitting

### 2. Automatic Missing Value Handling
- Learns direction of missing values by computing gain for both left and right and assigning direction that maximizes gain

### 3. Sparsity Aware Split Finding
- Efficient handling of sparse (zero or missing) values — no imputation needed

### 4. Efficient Split Finding
- **Quantile-based binning** (Weighted Quantile Sketch)
- Approximate tree learning on bins

### 5. Tree Pruning
- Uses a `gamma` hyperparameter to prune nodes based on minimum gain
- Both **pre-pruning** and **post-pruning** strategies supported

---

## 🔍 Summary
XGBoost = Gradient Boosting + Engineering Optimizations ✅

It’s a favorite among practitioners for:
- High accuracy
- Speed
- Versatility

---

## How Regression Works in XGBoost

XGBoost handles regression by building a sequence of trees, where each tree is trained to predict the **residual errors** (differences between actual and predicted values) from the previous trees.

Each prediction is a sum of outputs from all previous trees.

### 🔧 Output Calculation for Regression (per leaf node):
```
output = sum(residuals) / (number of residuals + λ)
```
Where:
- `λ` is the regularization term (lambda)
- If `λ = 0`, then:
```
output = average of residuals
```

This helps in **regularizing the model**, controlling overfitting, and ensuring smoother updates.

### 🔍 Default Parameters for Regression:
- `max_depth = 6` by default, which controls the depth of each regression tree
- Other hyperparameters: learning rate, lambda, gamma, etc.

---

## How Classification Works in XGBoost
👉 **Note**: In XGBoost, the decision trees are constructed based on **similarity index**, whereas traditional Gradient Boosting methods (especially for classification) often use metrics like the **Gini Index** to find the best splits. The similarity index in XGBoost provides a more mathematically grounded and performance-optimized approach to splitting, especially for large, sparse, or noisy datasets.

In classification, XGBoost models the **log-odds (logits)** of the target class:

### 🔣 Probability Calculation
```
Probability = e^x / (1 + e^x)
```
Where `x` is the raw score (log-odds) output from the model.

### 🧮 Two-Stage Learning Process

#### Stage 1: Compute Residuals
- Calculate predicted probability for each instance
- Compute residual error = actual - predicted probability

#### Stage 2: Build Tree Using Residuals
- Train a decision tree on these residuals
- For each **leaf node**, compute similarity score:

### 🍃 Leaf Node Score (Similarity Score)
```
similarity = (Σ residual_i)^2 / (Σ p_prev_i * (1 - p_prev_i) + λ)
```
Where:
- `residual_i` is the gradient of the loss (difference between actual and predicted)
- `p_prev_i` is the predicted probability at the previous iteration
- `λ` is the regularization term

This scoring function ensures that each split leads to the most informative and least noisy leaf nodes.

---

## 📐 Indepth Mathematics on which XGBoost is Based

![XGBoost Calculations - by CampusX video](XGBoostMathematics.png)


This image outlines the core gradient-based and regularization-enhanced math that governs both regression and classification in XGBoost. It also highlights how the similarity score and leaf weight are computed from gradients and Hessians.

