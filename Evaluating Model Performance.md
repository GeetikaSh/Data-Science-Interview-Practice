# Evaluating Model Performance

In machine learning, model performance evaluation used model monitoring to assess how well a model is performing at the specific task it was designed for. There avarity of waus to assess the model performance, which are discussed in detail latter in the post.

You might be thinking, thy evaluataing a model is that necessary. Well it is not any important in developemnt and testing stage, but one need to keep in eye on the model performance once it is deployed. Cotinued evaluation can identify trends like data drify and model bias, allowing models to be retained for improved performance.

# Whai is performance in machine learning?
Before diving into the evaluation of model performance, it is important for us to understand that is means by good performance of the model. Well If I have to put it in simple words, then it is nothing but is our designed model is accoplishing the task that it is desigend for. It is very important to understand what "doing well" means with respect to the model. For instance, in a model designed to look for credit card fraud, identifying as many fraudulent transactions as possible will likely be the goal. The number of false positives (where non-fraudulent activity was misidentified as fraud) will be less important than the number of false negatives (where fraudulent activity is not identified). In this case, the recall of the model is likely to be the most important performance indicator. The MLOps team would then define the recall results they consider acceptable in order to determine if this model is performing well or not.

A commonly asked question is about model accuracy vs model performance, but this is a false dichotomy. Model accuracy is one way to measure model performance. Accuracy relates to the percentage of model predictions that are accurate, which is one way to define performance in machine learning. But it will not always be the most important metric of performance, depending on what the model is designed to do. 

# What are the model evaluation methods?
There are two types of Models Classification and Regression, Each type of model have its oven evaluation metric that provides the quantitve measure of the performance of the model.

---
## Classification Metrics

Ckassification metrics are generally used for discrete values of a model might produce when done classifying all the given data. In order to understand how well the model has classified it's target value, we observe the **confision matrix**.
> **Why use these metrics?** In imbalanced datasets, focusing on Precision and Recall provides better insight than overall accuracy.

### **Confusion Matrix**
![](https://github.com/user-attachments/assets/73bdfccd-2a0a-46f1-a3e9-c3c99706d90d)

Please observe the above picture of confusion metrix, it give us teh clear picure of all the correct and incorrect perdictions. Which furtehr helps tus to anayse the performance of the model, especially if w have highly imbalanced data.

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

- **False Positive Rate (FPR)**: Proportion of false positives out of actual negatives.  
$\text{False Positive Rate} = \frac{FP}{FP + TN}$

- **Accuracy**: Propotion of correct predictions out of all predictions.  
$\text{Accuracy} = \frac{TP+TN}{TP+TN+FP+FN}$

- **F1-Score**: Harmonic mean of Precision and Recall. It balances the two metrics.  
$F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$

- **Logarithmic loss**: Measure of how many total errors a model has. The closer to zero, the more correct predictions a model makes in classifications.

- **Area under curve**: Method of visualizing true and false positive rates against each other. Will discuss about area under curve latter in the post.

---
## Regression Metrics
When we are dealing wuth the model that deals with the continious output(whereas clssification models deals with the descrete output), then we use regression metrics for evaluation our model.

**Regression metrics includes**: (Study in detail this time)
- **Cofficient of determination(or R-squared)**: measures variance of a model compared to the actual data.
- **Mean Squared Error**: Measired the amoount of average divergence of the model from the observed data.
- **Mean Absolute Error**: Measured the verticala nd horizontal distance between data points and a linear regression line to illustrae how much a model deviated from the obderved data.
- **Mean Absolute Percentage Error**: Shows mean absolute error as a percentage.
- **Weighted Mean Absolute Percentage Error**: Used actual valus(reather than absolute values) to measure percentage errors.
---

# Refrence
- [Precision Recall Curve| Data Camp](https://www.datacamp.com/tutorial/precision-recall-curve-tutorial)
- [AUC ROC Curve | GeeksforGeeks](https://www.geeksforgeeks.org/auc-roc-curve/)
- [What is Model Performace Evaluation](https://www.fiddler.ai/model-evaluation-in-model-monitoring/what-is-model-performance-evaluation)
