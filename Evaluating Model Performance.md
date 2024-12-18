# Evaluating Model Performance on an Imbalanced Dataset

| **Key Points for Better Evaluation** |  
|---------------------------------------|  
| 1. Avoid relying on accuracy alone.   |  
| 2. Use metrics like **Precision, Recall, F1-Score**, and **AUC-PR**. |  
| 3. Visualize performance using **PR curves** and **ROC curves**. |  
| 4. Apply resampling techniques or cost-sensitive methods to improve evaluation. |  


Imbalanced datasets occur when one class has significantly more samples than others. Traditional metrics like accuracy can be misleading in such cases. Below are techniques to evaluate a model effectively:

---

## 1. **Confusion Matrix**
![](https://github.com/user-attachments/assets/73bdfccd-2a0a-46f1-a3e9-c3c99706d90d)

A confusion matrix breaks down the classification results:
- **True Positives (TP)**: Correctly predicted positive cases.
- **True Negatives (TN)**: Correctly predicted negative cases.
- **False Positives (FP)**: Incorrectly predicted as positive.
- **False Negatives (FN)**: Incorrectly predicted as negative.

It provides insights into **misclassification** types, which are critical in imbalanced settings.

- **Precision**: Proportion of correctly predicted positive cases out of all predicted positives.  
$\text{Precision} = \frac{TP}{TP + FP}$

- **Recall (Sensitivity, True Positive Rate)**: Proportion of actual positives correctly predicted.  
$\text{Recall} = \frac{TP}{TP + FN}$

- **Accuracy**: Propotion of correct predictions out of all predictions.  
$\text{Accuracy} = \frac{TP+TN}{TP+TN+FP+FN}$

- **F1-Score**: Harmonic mean of Precision and Recall. It balances the two metrics.  
$F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$


> **Why use these metrics?** In imbalanced datasets, focusing on Precision and Recall provides better insight than overall accuracy.

---

## 2. **ROC-AUC Curve (Receiver Operating Characteristic - Area Under Curve)**
![ROC-AUC Curve](https://media.geeksforgeeks.org/wp-content/uploads/20230410164437/AUC-ROC-Curve.webp)
- **ROC Curve**: Plots the True Positive Rate (Recall) against the False Positive Rate (FPR).  
- **AUC (Area Under Curve)**: Measures the ability to distinguish between classes.  

The _**ROC curve**_ is a graphical representation used to evaluate the performance of a classification model. It shows the trade-off between the **True Positive Rate (TPR)**  also known as **Recall** and **False Positive Rate (FPR)** at various thresholds.

**Area Under the Curve (AUC)** quantifies the overall performance of a model by measuring the area under the ROC curve. AUC provides a single scalar value to compare models.

| **AUC Value to Interpret the ROC Curve**     | **Interpretation**                                                                                   |  
|--------------------|-----------------------------------------------------------------------------------------------------|  
| **AUC = 1.0**     | Perfect model. It distinguishes between all positive and negative instances perfectly.               |  
| **AUC = 0.5**     | Random guessing. The model has no discriminative power.                                              |  
| **0.5 < AUC < 1.0** | The model performs better than random but is not perfect.                                          |  
| **AUC < 0.5**     | The model performs worse than random guessing, indicating potential issues.                          |  



| **Aspect to Interpret the ROC Curve**              | **Details**                                                                                  |  
|--------------------------|----------------------------------------------------------------------------------------------|  
| **Shape of the Curve**   | - A curve that hugs the **top-left corner** of the plot represents a better model.           |  
|                          | - A diagonal line from (0, 0) to (1, 1) represents a random classifier.                     |  
| **Threshold Behavior**   | - A **low threshold** classifies most instances as positive, increasing TPR but also FPR.    |  
|                          | - A **high threshold** classifies most instances as negative, reducing both TPR and FPR.     |  
| **Comparing Models**     | - The model with the **higher AUC** generally performs better across all thresholds.          |  

> **Note**: ROC-AUC might be less informative when the dataset is extremely imbalanced because it considers both positive and negative classes equally.

---

## 3. **Precision-Recall (PR) Curve**
![PR Curve](https://github.com/user-attachments/assets/654dc1b1-317f-4a80-8d3c-aa85cd2b20d1)
- **ROC Curve**: Plots the True Positive Rate (Recall) against the False Positive Rate (FPR).  
- **AUC (Area Under Curve)**: Measures the ability to distinguish between classes.


> **Why PR over ROC?** For imbalanced datasets, the PR curve often provides more meaningful results as it emphasizes the positive class.

---

## 4. **Balanced Accuracy**

Balanced Accuracy accounts for class imbalance by averaging Recall (TPR) for each class:  
$\text{Balanced Accuracy} = \frac{\text{TPR (positive class)} + \text{TPR (negative class)}}{2}$

---

## 5. **Class-Specific Metrics**

Report metrics for each class (e.g., Precision, Recall, F1-score) to ensure minority classes are not ignored.

---

## 6. **Resampling Techniques for Better Evaluation**

- **Oversampling the minority class** (e.g., SMOTE - Synthetic Minority Over-sampling Technique).  
- **Undersampling the majority class** to balance the dataset.

> Resampling helps balance the data for training and evaluation.

---

## 7. **Cost-Sensitive Learning**

Assign higher misclassification costs to the minority class to penalize false negatives more heavily.

---

## When Is Precission Preffered onad when Is Recall Preffered
### Example Use Case
If you're evaluating a model to detect fraud:
- **High TPR** ensures you catch most fraudulent transactions.
- **Low FPR** prevents flagging too many legitimate transactions as fraud.
---

# PR Curve vs. ROC Curve: A Detailed Comparison

Both **Precision-Recall (PR) curves** and **Receiver Operating Characteristic (ROC) curves** are widely used to evaluate classification models. However, they serve slightly different purposes and excel in different scenarios, especially when dealing with **imbalanced datasets**. Here's how they compare:

---

## **1. Metrics Used**
- **PR Curve**:
  - **Precision (Positive Predictive Value)**: Proportion of true positives out of predicted positives.  
  - **Recall (Sensitivity, True Positive Rate)**: Proportion of true positives out of actual positives.

- **ROC Curve**:
  - **True Positive Rate (Recall/Sensitivity)**: Proportion of true positives out of actual positives.  
  - **False Positive Rate (FPR)**: Proportion of false positives out of actual negatives.  
    `FPR = FP / (FP + TN)`

---

## **2. Focus**
- **PR Curve**:  
  Focuses on the **positive class** (minority class in imbalanced datasets).  
  Highlights the trade-off between precision and recall.  

- **ROC Curve**:  
  Balances performance across **both classes** (positive and negative).  
  Highlights the trade-off between true positive rate and false positive rate.  

---

## **3. Performance Interpretation**
- **PR Curve**:  
  - More sensitive to the performance of the **minority class**.  
  - Useful when the **positive class is rare** (e.g., fraud detection, medical diagnosis).  
  - Gives a better understanding of false positives relative to true positives.  

- **ROC Curve**:  
  - Provides a global view of the model's performance over all thresholds.  
  - Can be misleading on highly imbalanced datasets, as the **true negatives** dominate the FPR, inflating the ROC curve.  

---

## **4. AUC (Area Under the Curve)**
- **AUC-PR**:  
  - Measures the area under the PR curve.  
  - A higher AUC-PR indicates better performance for the **positive class**.  

- **AUC-ROC**:  
  - Measures the area under the ROC curve.  
  - A higher AUC-ROC indicates better overall performance, considering both classes.  

---

## **5. Strengths**
| **Aspect**                  | **PR Curve**                                      | **ROC Curve**                                     |  
|-----------------------------|--------------------------------------------------|-------------------------------------------------|  
| **Imbalanced Datasets**     | Better for evaluating models with imbalanced data. | May overestimate performance due to class imbalance. |  
| **Emphasis**                | Focuses on the **positive class**.                | Balances both positive and negative classes.      |  
| **Threshold Analysis**      | Highlights trade-offs between precision and recall.| Highlights trade-offs between TPR and FPR.        |  

---

## **6. Weaknesses**
- **PR Curve**:  
  - Does not consider true negatives, which might be important in certain scenarios.  

- **ROC Curve**:  
  - FPR can be misleading on imbalanced datasets, as the large number of true negatives dominates its calculation.  

---

## **7. When to Use**
| **Scenario**                               | **Preferred Curve** |  
|--------------------------------------------|----------------------|  
| Highly imbalanced datasets                 | PR Curve             |  
| Balanced datasets                          | ROC Curve            |  
| Emphasizing false positives vs. false negatives | PR Curve             |  
| Overall model performance comparison       | ROC Curve            |  

---

## **Key Example**
- **Fraud Detection (Imbalanced Data)**:  
  Use **PR Curve** to assess how well the model balances precision (minimizing false positives) and recall (catching actual fraud cases).  

- **Binary Classification with Balanced Data**:  
  Use **ROC Curve** to evaluate the overall performance of the model across all thresholds.  

---

## **Visualization Comparison**
1. **PR Curve**:  
   Focuses on how well the model captures true positives without increasing false positives excessively.  

2. **ROC Curve**:  
   Focuses on the ability to distinguish between the positive and negative classes.  

Both curves provide critical insights but are most effective when applied to scenarios they are best suited for.




---
# Refrence
- [Precision Recall Curve| Data Camp](https://www.datacamp.com/tutorial/precision-recall-curve-tutorial)
- [AUC ROC Curve | GeeksforGeeks](https://www.geeksforgeeks.org/auc-roc-curve/)
