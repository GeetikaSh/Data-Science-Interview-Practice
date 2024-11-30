
# Difference Between L1 and L2 Regularization

Regularization techniques are used to prevent overfitting in machine learning models by adding a penalty to the loss function. The penalties are based on the magnitude of the coefficients, and the most common regularization techniques are **L1 Regularization** and **L2 Regularization**.

## L1 Regularization (Lasso Regression)
- **Definition**: L1 regularization adds the absolute value of the coefficients as a penalty term to the loss function.
- **Formula**: Loss = Loss_function + λ * Σ|w|, where w is the weight/coefficients, and λ is the regularization parameter.
- **Key Characteristics**:
  - Encourages sparsity in the model by driving some coefficients to exactly zero.
  - Results in feature selection as irrelevant features are effectively removed.
  - Suitable for datasets with many irrelevant or redundant features.
- **When to Use**: Use L1 regularization when feature selection is important, or when you expect many features to be irrelevant.

## L2 Regularization (Ridge Regression)
- **Definition**: L2 regularization adds the squared value of the coefficients as a penalty term to the loss function.
- **Formula**: Loss = Loss_function + λ * Σw², where w is the weight/coefficients, and λ is the regularization parameter.
- **Key Characteristics**:
  - Shrinks coefficients towards zero but does not make them exactly zero.
  - Helps distribute the impact among all relevant features.
  - Suitable for datasets where all features are expected to contribute to the prediction.
- **When to Use**: Use L2 regularization when you want to reduce overfitting without eliminating features.

## Summary of Differences

| Feature                | L1 Regularization                | L2 Regularization                |
|------------------------|-----------------------------------|-----------------------------------|
| Penalty Term           | Absolute value of coefficients   | Squared value of coefficients    |
| Coefficients Impact    | Drives some coefficients to zero | Shrinks coefficients toward zero |
| Feature Selection      | Performs feature selection       | Does not perform feature selection |
| Sparsity               | Produces sparse models           | Does not produce sparse models   |

## Combined Use
- **Elastic Net** combines L1 and L2 regularization and allows a balance between feature selection and model stability.

---

## Example Usage
- **L1 Regularization Example**: In a model predicting house prices, use L1 regularization if you suspect certain features like "color of the house" might be irrelevant and can be removed.
- **L2 Regularization Example**: In a model predicting stock prices, use L2 regularization to ensure no feature dominates excessively while keeping all features in play.

