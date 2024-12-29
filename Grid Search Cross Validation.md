# Grid Search Cross Validation

When deciding on the best model for a problem statement, a Data Scientist experiments with multiple models and selects the best-performing one.
However, the selected model often runs on default hyperparameters, which may not yield the most optimal solution for the specific use case.
To address this, **Hyperparameter Tuning** is performed to tailor the model to the problem.

There are various hyperparameter tuning methods, including:

- **Random Search**
- **GridSearchCV** (provided by `sklearn`)
- **Manual Search**
- **Bayesian Optimization**

In this page, we focus on **Grid Search Cross Validation**.

---

## What is Grid Search Cross Validation?

Grid Search Cross Validation performs an **exhaustive search** over a predefined grid of hyperparameters.
It evaluates each combination of parameters using cross-validation, ensuring robust model performance.


## Steps Involved:

1. **Define Hyperparameter Grid:**
   - Choose the hyperparameters and specify a range of values or a set of possible options.
   - For example:
     ```python
     param_grid = {
       'C': [0.1, 1, 10],
       'kernel': ['linear', 'rbf'],
       'gamma': ['scale', 'auto']
     }
     ```

2. **Apply GridSearchCV:**
   - Use `GridSearchCV` from `sklearn.model_selection` to evaluate the hyperparameters.
   - Specify the model, the parameter grid, and the number of folds for cross-validation.
   - Example:
     ```python
     from sklearn.model_selection import GridSearchCV
     from sklearn.svm import SVC

     # Define model
     model = SVC()

     # Set up grid search
     grid_search = GridSearchCV(estimator=model, param_grid=param_grid, cv=5)

     # Fit the grid search model
     grid_search.fit(X_train, y_train)
     ```

3. **Evaluate Results:**
   - After fitting the grid search, you can access the best parameters and the best score.
   - Example:
     ```python
     print("Best parameters:", grid_search.best_params_)
     print("Best cross-validation score:", grid_search.best_score_)
     ```

4. **Final Model:**
   - Use the best parameters found during grid search to train your final model.
   - Example:
     ```python
     best_model = grid_search.best_estimator_
     best_model.fit(X_train, y_train)
     ```

## Advantages:
- **Exhaustive Search:** Tests all possible combinations of parameters, ensuring the best performance.
- **Cross-Validation:** Uses cross-validation to avoid overfitting and evaluate model performance more reliably.

## Disadvantages:
- **Computationally Expensive:** For large grids, it can be very time-consuming as it needs to evaluate many combinations.
- **Limited Scope:** The grid search is restricted to the hyperparameter values provided; it may miss optimal values outside of this range.

## Conclusion
Grid Search Cross Validation is a powerful tool for optimizing model performance by systematically tuning hyperparameters.
However, it can be computationally expensive, and it’s essential to manage the size of the search space to make it more feasible.
