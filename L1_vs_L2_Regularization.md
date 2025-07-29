# Regularization

Regularization techniques help prevent **overfitting** in machine learning models **by adding a penalty to the loss function**. These penalties are based on the magnitude of the model's coefficients. In simple words, it adds a penalty term to the loss function to discourage the model from learning noise or irrelevant patterns in the training data. The most common regularization methods are:

- **L1 Regularization (Lasso Regression)**
- **L2 Regularization (Ridge Regression)**
- **Elastic Net (Combination of L1 & L2)**

## Difference Between L1 and L2 Regularization

The key difference between **L1 and L2 regularization** lies in the **penalty term** they apply to the loss function.

### L1 Regularization (Lasso Regression)

- **Definition**: L1 regularization adds the absolute value of the coefficients as a penalty term to the loss function.
- **Formula**:

$$
  \text{Loss} = \text{Loss Function} + \lambda \sum |w|
$$

  where:

  - \( w \) represents the model coefficients.
  - $\lambda$ is the regularization strength.

- **Key Characteristics**:
  - Encourages **sparsity** by setting some coefficients to exactly **zero**.
  - Acts as an automatic **feature selection** mechanism by removing irrelevant features.
  - Best suited for **high-dimensional datasets** with many irrelevant or redundant features.

- **When to Use**:  
  Use **L1 regularization** when feature selection is important, or when you suspect many features are irrelevant. L1 effectively removes such features, making it useful for sparse datasets.

### L2 Regularization (Ridge Regression)

- **Definition**: L2 regularization adds the squared value of the coefficients as a penalty term to the loss function.
- **Formula**:

$$
  \text{Loss} = \text{Loss Function} + \lambda \sum w^2
$$

  where:

  - \( w \) represents the model coefficients.
  - $\( \lambda \)$ controls the regularization strength.

- **Key Characteristics**:
  - Shrinks coefficients **towards zero** but does **not** eliminate them.
  - Helps **distribute importance** across all features.
  - Ideal for datasets where **all features contribute to the prediction**.
  - L2 is also differentiable everywhere, making it computationally more stable for optimization.

- **When to Use**:  
  Use **L2 regularization** when you want to reduce overfitting without completely removing any features. It works well in **high-dimensional datasets** or when **multicollinearity** is present.

### Summary of Differences

| Feature                | L1 Regularization (Lasso)       | L2 Regularization (Ridge)       |
|------------------------|--------------------------------|--------------------------------|
| **Penalty Term**       | Absolute value of coefficients | Squared value of coefficients |
| **Impact on Weights**  | Some coefficients shrink to **zero** | Coefficients shrink but never reach zero |
| **Feature Selection**  | **Yes**, removes irrelevant features | **No**, retains all features |
| **Sparsity**           | Produces **sparse** models     | Does **not** produce sparse models |

## Elastic Net: Combining L1 and L2

- **Definition**: Elastic Net combines **L1 and L2 regularization**, allowing a balance between feature selection and model stability.
- ElasticNet combines L1 and L2 penalties. It's useful when:
  - You suspect some irrelevant features (→ L1).
  - But also need stability across correlated features (→ L2).
It provides a flexible regularization strategy with both sparsity and smoothness.

- **Formula**:

$$
  \text{Loss} = \text{Loss Function} + \lambda_1 \sum |w| + \lambda_2 \sum w^2
$$

- **When to Use**:
  - L1 alone selects too few features.
  - L2 alone does not remove irrelevant features.
  - The dataset is **high-dimensional** and **collinear**.

**Example:** In **genomics**, Elastic Net helps by both selecting relevant genes (**L1**) and stabilizing the model (**L2**).

---

## Example Use Cases

- **L1 Regularization Example**: Suppose you're building a model to predict house prices. If you suspect certain features (e.g., "color of the house") are irrelevant, use **L1** to remove them.
- **L2 Regularization Example**: If you're predicting stock prices and want to **prevent any single feature from dominating the model**, use **L2** to keep all features while controlling their influence.

## Regularization and the Bias-Variance Tradeoff

Regularization plays a critical role in managing **bias and variance**:

- **Without Regularization** → Model may **overfit**, capturing noise rather than general patterns.
- **With L1 or L2 Regularization** → Model learns **simpler patterns**, reducing variance but slightly increasing bias.

### **Key Trade-offs**
✅ **L1 Regularization**: Higher bias, lower variance, effective feature selection.  
✅ **L2 Regularization**: Moderate bias increase, smoother models, better generalization.

---

## How do you tune the regularization parameter λ (lambda)?
- Use cross-validation (e.g., `GridSearchCV`, `RandomizedSearchCV`, or `Bayesian Optimization`) to select the best λ.

In practice:
- High λ → more regularization → simpler model, higher bias.
- Low λ → less regularization → risk of overfitting, higher variance.

## Is regularization only used in linear models?
**No. Regularization is widely used across ML:**
- Logistic regression: To penalize overconfident predictions.
- Neural networks: L2 weight decay, Dropout, Early stopping, BatchNorm.
- Tree-based models (e.g., XGBoost, LightGBM): Use regularization via max depth, min samples split, learning rate, and L1/L2 penalties on leaf weights.

---

By understanding and applying **L1, L2, and Elastic Net Regularization**, you can significantly **improve model performance** and **reduce overfitting** in machine learning applications.
