# Cross-Validation: A Comprehensive Guide

Cross-validation is a statistical method used to evaluate the performance of machine learning models.
It ensures that a model generalizes well to unseen data by testing it on different subsets of the data.
This process helps prevent overfitting and provides a more robust assessment of the model’s performance.


## Key Concepts in Cross-Validation

### 1. **Training Set**
The subset of data used to train the machine learning model.

### 2. **Validation Set**
A separate subset of data used to fine-tune model parameters or assess performance during training.

### 3. **Test Set**
A completely unseen subset used for final evaluation of the model's performance.


## Why Use Cross-Validation?

- **Generalization**: Ensures the model performs well on new, unseen data.
- **Avoids Overfitting**: Helps prevent the model from memorizing the training data instead of learning from it.
- **Model Selection**: Facilitates comparison of different models or hyperparameter settings.


## Types of Cross-Validation

### 1. **K-Fold Cross-Validation**
![5-Fold Cross Validation](https://github.com/user-attachments/assets/f58e4041-86fa-4ac9-9090-5519a3b088cd)
   - The data is split into *k* equally sized folds.
   - The model is trained on *k-1* folds and validated on the remaining fold.
   - This process repeats *k* times, with each fold serving as the validation set once.
   - The final performance is the average of all *k* evaluations.
     
    ```python
    from sklearn import datasets
    from sklearn.tree import DecisionTreeClassifier
    from sklearn.model_selection import KFold, cross_val_score
    
    X, y = datasets.load_iris(return_X_y=True)
    
    clf = DecisionTreeClassifier(random_state=42)
    
    k_folds = KFold(n_splits = 5)
    
    scores = cross_val_score(clf, X, y, cv = k_folds)
    
    print("Cross Validation Scores: ", scores)
    print("Average CV Score: ", scores.mean())
    print("Number of CV Scores used in Average: ", len(scores))
    ```


### 2. **Stratified K-Fold Cross-Validation**
![Stratified 5 Fold Cross Validation](https://github.com/user-attachments/assets/b40b5781-9f6f-4412-a680-6ad63e11612b)
    - A variation of K-Fold where folds are created to ensure class distribution is preserved (for classification tasks).
    - In simple wors cross-validation that ensures that the proportion of samples for each class is roughly the same in each fold.
    - This is useful when the class distribution is imbalanced, meaning that there are different number of samples for each class.
    
    ```python
    from sklearn import datasets
    from sklearn.tree import DecisionTreeClassifier
    from sklearn.model_selection import StratifiedKFold, cross_val_score
    
    X, y = datasets.load_iris(return_X_y=True)
    
    clf = DecisionTreeClassifier(random_state=42)
    
    sk_folds = StratifiedKFold(n_splits = 5)
    
    scores = cross_val_score(clf, X, y, cv = sk_folds)
    
    print("Cross Validation Scores: ", scores)
    print("Average CV Score: ", scores.mean())
    print("Number of CV Scores used in Average: ", len(scores))
    ```

### 3. **Leave-One-Out Cross-Validation (LOOCV)**
![LOOCV](https://miro.medium.com/v2/resize:fit:720/format:webp/1*T-RXyt_53zxvh8pom3UhOA.png)
    - In this method we use *n-1* samples of the dataset as the training set and *1* sample as the test set. This process is repeated *n* times, each time leaving out a different sample as the test set. 
    - Computationally expensive but useful for small datasets.
    - Since there is only on data point in validation data set and rest in trianing dataset, hence it is more prone to overfitting.
    ```python
    from sklearn import datasets
    from sklearn.tree import DecisionTreeClassifier
    from sklearn.model_selection import LeaveOneOut, cross_val_score
    
    X, y = datasets.load_iris(return_X_y=True)
    
    clf = DecisionTreeClassifier(random_state=42)
    
    loo = LeaveOneOut()
    
    scores = cross_val_score(clf, X, y, cv = loo)
    
    print("Cross Validation Scores: ", scores)
    print("Average CV Score: ", scores.mean())
    print("Number of CV Scores used in Average: ", len(scores))
    ```

### 4. **Time Series Cross-Validation**
- Used for time-dependent data.
- Ensures that training always occurs on past data and testing on future data to preserve temporal order.

### 5. **Monte Carlo Cross-Validation (Shuffle-Split)**
- Randomly splits the dataset into training and testing sets multiple times.
- The model is evaluated on each split, and the results are averaged.

---

## Implementation in Python (Using Scikit-Learn)

```python
from sklearn.model_selection import cross_val_score, KFold
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris

# Load dataset
data = load_iris()
X, y = data.data, data.target

# Define model
model = RandomForestClassifier()

# K-Fold Cross-Validation
kf = KFold(n_splits=5)
scores = cross_val_score(model, X, y, cv=kf)

# Results
print("Cross-Validation Scores:", scores)
print("Mean Score:", scores.mean())
```
Pros and Cons of Cross-Validation
Pros
Provides a more reliable estimate of model performance.
Reduces bias from a single train-test split.
Cons
Computationally expensive, especially for large datasets or complex models.

May not fully capture time-dependent relationships (use time series CV instead).
Best Practices
Use Stratified K-Fold for imbalanced datasets.
Ensure the dataset is shuffled before splitting, unless temporal order matters.
Choose the number of folds (k) based on dataset size (e.g., 5 or 10 for most cases).
Pair cross-validation with hyperparameter tuning for optimal results.

---

## Reference
- [Cross Validation Explained by SharpSight](https://www.sharpsightlabs.com/blog/cross-validation-explained/)
- [Medium: Cross Validation by Om Pramod](https://medium.com/@ompramod9921/cross-validation-623620ff84c2)
