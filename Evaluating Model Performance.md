# Evaluating Model Performance on an Imbalanced Dataset

Imbalanced datasets occur when one class has significantly more samples than others. Traditional metrics like accuracy can be misleading in such cases. Below are techniques to evaluate a model effectively:

---

## 1. **Confusion Matrix**
A confusion matrix breaks down the classification results:
- **True Positives (TP)**: Correctly predicted positive cases.
- **True Negatives (TN)**: Correctly predicted negative cases.
- **False Positives (FP)**: Incorrectly predicted as positive.
- **False Negatives (FN)**: Incorrectly predicted as negative.

It provides insights into **misclassification** types, which are critical in imbalanced settings.

---

## 2. **Precision, Recall, and F1-Score**

- **Precision**: Proportion of correctly predicted positive cases out of all predicted positives.  
$$
\text{Precision} = \frac{TP}{TP + FP}
$$

- **Recall (Sensitivity, True Positive Rate)**: Proportion of actual positives correctly predicted.  
$$
\text{Recall} = \frac{TP}{TP + FN}
$$

- **F1-Score**: Harmonic mean of Precision and Recall. It balances the two metrics.  
$$
F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
$$

> **Why use these metrics?** In imbalanced datasets, focusing on Precision and Recall provides better insight than overall accuracy.

---

## 3. **ROC-AUC Curve (Receiver Operating Characteristic - Area Under Curve)**

- **ROC Curve**: Plots the True Positive Rate (Recall) against the False Positive Rate (FPR).  
- **AUC (Area Under Curve)**: Measures the ability to distinguish between classes.  
   - AUC closer to 1 indicates a good model.  
   - AUC near 0.5 suggests a random classifier.

> **Note**: ROC-AUC might be less informative when the dataset is extremely imbalanced because it considers both positive and negative classes equally.

---

## 4. **Precision-Recall (PR) Curve**

- **Precision-Recall Curve**: Precision vs. Recall across thresholds.  
- **AUC-PR**: The area under the PR curve focuses on the minority class performance.

> **Why PR over ROC?** For imbalanced datasets, the PR curve often provides more meaningful results as it emphasizes the positive class.

---

## 5. **Balanced Accuracy**

Balanced Accuracy accounts for class imbalance by averaging Recall (TPR) for each class:  
$$
\text{Balanced Accuracy} = \frac{\text{TPR (positive class)} + \text{TPR (negative class)}}{2}
$$

---

## 6. **Class-Specific Metrics**

Report metrics for each class (e.g., Precision, Recall, F1-score) to ensure minority classes are not ignored.

---

## 7. **Resampling Techniques for Better Evaluation**

- **Oversampling the minority class** (e.g., SMOTE - Synthetic Minority Over-sampling Technique).  
- **Undersampling the majority class** to balance the dataset.

> Resampling helps balance the data for training and evaluation.

---

## 8. **Cost-Sensitive Learning**

Assign higher misclassification costs to the minority class to penalize false negatives more heavily.

---

## Summary

For evaluating models on imbalanced datasets:  
1. Avoid relying on accuracy alone.  
2. Use metrics like **Precision, Recall, F1-Score**, and **AUC-PR**.  
3. Visualize performance using **PR curves** and **ROC curves**.  
4. Apply resampling techniques or cost-sensitive methods to improve evaluation.
