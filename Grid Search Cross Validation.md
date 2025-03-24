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

**Grid Search Cross-Validation** is a hyperparameter tuning technique that **systematically searches** through a predefined set of hyperparameter values. It evaluates every possible combination using cross-validation to identify the best-performing set of parameters. This approach ensures that the model generalizes well to unseen data by selecting the optimal configuration based on validation performance.

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
- **Reliable Performance Estimation:** Uses **cross-validation**, reducing the risk of overfitting by validating model performance on multiple subsets of data.
- **Reproducibility:** Since it follows a structured search, it produces consistent and repeatable results.

## Disadvantages:
- **Computationally Expensive:** For large grids, it can be very time-consuming as it needs to evaluate many combinations.
- **Limited Scope:** The grid search is restricted to the hyperparameter values provided; it may miss optimal values outside of this range.
- **Scalability Issues:** As the number of hyperparameters increases, the search space grows exponentially, making it impractical for deep learning models.

## When to Prefer Randomized Search Over Grid Search
Randomized Search is preferred over Grid Search in the following scenarios:\
✅ **Large Hyperparameter Space** – When there are many hyperparameters with a wide range of possible values, Grid Search becomes computationally expensive, whereas Randomized Search explores the space more efficiently.\
✅ **Limited Computational Resources** – If time or processing power is constrained, Randomized Search can find good hyperparameters faster without evaluating every combination.\
✅ **Diminishing Returns on Grid Search** – In cases where a fine-tuned search is unnecessary, Randomized Search often finds near-optimal parameters without the need for exhaustive evaluation.\
✅ **Uncertain Hyperparameter Ranges** – If you're unsure of the best hyperparameter values, Randomized Search allows exploration over a broader range, potentially discovering better values outside a predefined grid.

## Conclusion
Grid Search Cross Validation is a powerful tool for optimizing model performance by systematically tuning hyperparameters.
However, it can be computationally expensive, and it’s essential to manage the size of the search space to make it more feasible.
