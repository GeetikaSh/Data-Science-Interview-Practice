# Cross-Validation: A Comprehensive Guide

Cross-validation is a statistical method used to evaluate the performance of machine learning models.
It ensures that a model generalizes well to unseen data by testing it on different subsets of the data.
This process helps prevent overfitting and provides a more robust assessment of the model’s performance.


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
- Temporal data, also known as time-series data, is a collection of data points indexed in order of time.
- Common Time Series Cross-Validation Techniques:

  #### Walk-Forward Validation (Rolling Window)
  - Training set grows with each step, while the test set remains constant.
  - **Example:**  
    - Split 1: Train = [1, 2, 3], Test = [4]  
    - Split 2: Train = [1, 2, 3, 4], Test = [5]  
    - Split 3: Train = [1, 2, 3, 4, 5], Test = [6]  

  #### Sliding Window Validation
  - Both training and test sets "slide" forward, maintaining a fixed size.
  - **Example:**  
    - Split 1: Train = [1, 2, 3], Test = [4]  
    - Split 2: Train = [2, 3, 4], Test = [5]  
    - Split 3: Train = [3, 4, 5], Test = [6]  

  #### Expanding Window Validation
  - Training set expands, while the test set remains fixed. Variation of walk-forward validation.
  - **Example:**  
    - Split 1: Train = [1], Test = [2]  
    - Split 2: Train = [1, 2], Test = [3]  
    - Split 3: Train = [1, 2, 3], Test = [4]  

  #### Blocked Time Series Cross-Validation
  - Data is divided into blocks, with each block acting as a training-test pair.
  - Useful for testing the model on distinct sections of data.
  - **Example:**  
    - Split 1: Train = [1, 2, 3], Test = [4, 5]  
    - Split 2: Train = [4, 5, 6], Test = [7, 8]  

`Temporal data, also known as time-series data, is a collection of data points that are indexed in order of time.`

### Monte Carlo Cross Validation

![Monte Carlo Cross Validation](https://github.com/user-attachments/assets/b18d5a13-f7da-46bc-ad47-1ed20d71f6ad)

 - Repeatedly splits the dataset into random training and testing sets.
 - The model is evaluated on each split, and the results are averaged to estimate performance.
 - Best suited for datasets without temporal dependency but can be adapted for time series data by preserving order.

```python
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.linear_model import LinearRegression

# Example Data
X = np.random.rand(100, 1)  # Features
y = 3 * X.squeeze() + np.random.randn(100) * 0.5  # Target

# Monte Carlo Cross-Validation
n_splits = 10
test_size = 0.2
metrics = []

for _ in range(n_splits):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=test_size, random_state=None)
    model = LinearRegression()
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    mse = mean_squared_error(y_test, y_pred)
    metrics.append(mse)

print("Average MSE:", np.mean(metrics))
print("Variance in MSE:", np.var(metrics))
```

## Pros and Cons of Cross-Validation

### Pros
- Provides a more reliable estimate of model performance.
- Reduces bias from a single train-test split.

### Cons
- Computationally expensive, especially for large datasets or complex models.

---

## Reference
- [Cross Validation Explained by SharpSight](https://www.sharpsightlabs.com/blog/cross-validation-explained/)
- [Medium: Cross Validation by Om Pramod](https://medium.com/@ompramod9921/cross-validation-623620ff84c2)
