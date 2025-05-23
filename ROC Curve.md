### **ROC-AUC Curve (Receiver Operating Characteristic - Area Under Curve)**
![ROC](https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Roc_curve.svg/330px-Roc_curve.svg.png)

- **ROC Curve**:
    -- Plots the _**True Positive Rate (Recall)**_ against the _**False Positive Rate (FPR)**_.
    -- Balances performance across **both classes** (positive and negative).
    -- Provides a global view of the model's performance over all thresholds.  
    -- Can be misleading on highly imbalanced datasets, as the **true negatives** dominate the FPR, inflating the ROC curve.
    -- Focuses on the ability to distinguish between the positive and negative classes. 
   
- **AUC (Area Under Curve)**: Measures the ability to distinguish between classes. It quantifies the overall
  performance of a model by measuring the area under the ROC curve. AUC provides a single scalar value to compare models.

| **AUC Value**     | **Interpretation**                                                                                   |  
|--------------------|-----------------------------------------------------------------------------------------------------|  
| **AUC = 1.0**     | Perfect model. It distinguishes between all positive and negative instances perfectly.               |  
| **AUC = 0.5**     | Random guessing. The model has no discriminative power.                                              |  
| **0.5 < AUC < 1.0** | The model performs better than random but is not perfect.                                          |  
| **AUC < 0.5**     | The model performs worse than random guessing, indicating potential issues.                          |  


> **Note**: ROC-AUC might be less informative when the dataset is extremely imbalanced because it considers both positive and negative classes equally.

---

## 3. **Precision-Recall (PR) Curve**
![PR Curve](https://github.com/user-attachments/assets/654dc1b1-317f-4a80-8d3c-aa85cd2b20d1)

**PR Curve**:
- Plots _**Precision**_ against _**Recall**_.
-  More sensitive to the performance of the **minority class**.
-  Useful when the **positive class is rare** (e.g., fraud  detection, medical diagnosis).
-  Gives a better understanding of false positives relative to true positives.
-  Focuses on how well the model captures true positives without increasing false positives excessively.    

> **Why PR over ROC?** For imbalanced datasets, the PR curve often provides more meaningful results as it emphasizes the positive class.

| **Aspect**                  | **PR Curve**                                      | **ROC Curve**                                     |  
|-----------------------------|--------------------------------------------------|-------------------------------------------------|  
| **Imbalanced Datasets**     | Better for evaluating models with imbalanced data. | May overestimate performance due to class imbalance. |  
| **Emphasis**                | Focuses on the **positive class**.                | Balances both positive and negative classes.      |  
| **Threshold Analysis**      | Highlights trade-offs between precision and recall.| Highlights trade-offs between TPR and FPR.        |
| **Weakness**                | Does not consider true negatives                   | FPR can be misleading on imbalanced datasets       |

| **When to Use Scenario**                   | **Preferred Curve** |  
|--------------------------------------------|----------------------|  
| Highly imbalanced datasets                 | PR Curve             |  
| Balanced datasets                          | ROC Curve            |  
| Emphasizing false positives vs. false negatives | PR Curve        |  
| Overall model performance comparison       | ROC Curve            |  

---

### **Balanced Accuracy**

Balanced Accuracy accounts for class imbalance by averaging Recall (TPR) for each class:  
$\text{Balanced Accuracy} = \frac{\text{TPR (positive class)} + \text{TPR (negative class)}}{2}$

---

### **Class-Specific Metrics**

Report metrics for each class (e.g., Precision, Recall, F1-score) to ensure minority classes are not ignored.

---

### **Resampling Techniques for Better Evaluation**

- **Oversampling the minority class** (e.g., SMOTE - Synthetic Minority Over-sampling Technique).  
- **Undersampling the majority class** to balance the dataset.

> Resampling helps balance the data for training and evaluation.

---

### **Cost-Sensitive Learning**

Assign higher misclassification costs to the minority class to penalize false negatives more heavily.

---
# Threshold in Classification Models

A **threshold** is a value used to convert a model's predicted probabilities into class labels. It determines how likely an instance is to belong to a particular class.

## How It Works:
- **Predicted Probabilities**: Models output probabilities (between 0 and 1) indicating the likelihood of an instance belonging to the positive class.
- **Threshold Decision**: 
  - If the predicted probability is ≥ threshold, classify as **positive** (1).
  - If the predicted probability is < threshold, classify as **negative** (0).
  
  Typically, the default threshold is **0.5**.

## Example:
- If predicted probability = 0.7, and threshold = 0.5, classify as **positive**.
- If predicted probability = 0.3, and threshold = 0.5, classify as **negative**.

## Adjusting the Threshold:
- **Lower threshold** (e.g., 0.3): Increases **recall** but may reduce **precision** (more false positives).
- **Higher threshold** (e.g., 0.7): Increases **precision** but may reduce **recall** (more false negatives).

## Impact on Metrics:
- The threshold affects metrics like **precision**, **recall**, and **F1 score**.
- **PR Curve** and **ROC Curve** are influenced by threshold adjustments.

## When to Adjust:
- **Imbalanced Datasets**: Adjust to improve performance on the minority class.
- **Business Needs**: Adjust to prioritize **precision** or **recall** based on the application (e.g., fraud detection).
