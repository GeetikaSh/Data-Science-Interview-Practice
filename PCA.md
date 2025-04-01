# Principal Component Analysis (PCA)

Principal Component Analysis (PCA) is a powerful technique for dimensionality reduction, data visualization, and feature extraction in machine learning and data analysis.

As the number of features or dimensions in a dataset increases, the amount of data required to obtain a statistically significant result increases exponentially.
This can lead to issues such as overfitting, increased computation time, and reduced accuracy of machine learning models this is known as the **curse of dimensionality** problems.

**Freature Engineering** is used to address this _**curse of dimentionality**_. Feature Engineering is used to reduce the Dimentionality. The main Idea in to reduce the number of input features, whlile reataining all the relevant information.

PCA transforms high-dimensional data into a lower-dimensional form while preserving as much variance as possible.
Principal Component Analysis (PCA) is a dimensionality reduction technique that helps mitigate the curse of dimensionality. It transforms the original features into a new set of uncorrelated features called principal components, which capture the maximum variance in the data. The number of principal components is determined by a predefined parameter, `n_components`, which specifies how many dimensions to retain while preserving as much information as possible.

## How PCA Works

![Principal Component Analysis](https://media.geeksforgeeks.org/wp-content/uploads/20230420165431/Principal-Componenent-Analysisi.webp)

1. **Standardization**: Normalize the dataset to have a mean of 0 and standard deviation of 1.
2. **Covariance Matrix Calculation**: Compute the covariance matrix to understand feature relationships.
3. **Eigen Decomposition**: Find eigenvalues and eigenvectors of the covariance matrix.
   - Eigenvalues represent the variance explained by each principal component.
   - Eigenvectors define the direction of the principal components.
4. **Projection**: Project the data onto the selected principal components.

## Advantages of PCA
- **Reduces Dimentionality:** Helps in handaling the curse of dimentionality by transforming data into fewer features while retaining maximum variance.
- **Remove Redundancy:** PCA removes correlated features, making teh dataset more compact and efficient.
- **Improves Model Performance:** By reducing noise and redundant features, PCA can speed up machie learning models and prevent overfiting.
- **Visualiszation:** PCA helps in reducing data to 2D or 3D for better visualization in high-dimentional datasets.
- **Unsupervised Learning:** PCA doesn't need labeled data, making it useful for explonatory data analysis.

## Disadvantages of PCA
- **Loss of Interpretability:** The transformed features(principal components) are linear combinations of original eatures, making them difficult to interpret.
- **Assumption of Linearity:** PCA assumes that the data follows a linear structure, so it might nort work well for the dataset with non-linear relationships.
- **Sensitivity to Scaling:** If data is not standardized, PCA might give misleading results since it priortizes large-varinance features.
- **May Discard Useful Information:** If important infomation is in low-variance components, PCA may remove it.

## How do you decide the number of principal components to retain in PCA?
The numbe of Principle components(`n_componenets`) to retain is typically chosen based on the **explained variance ratio** or **scree plot**  analysus. Here are the common methods:
1. **Explained Variance Ratio:**
- Each principal component contributes to the toatal variance.
- We select the number of components that retains at least 95% of the variance(or another chosen threshold).
- This is computes as:
 $\sum_{i=1}^{k} \frac{\lambda}{\sum \lambda_i}$ 

where ${\lambda_i}$ are the eigen values of the selected components.

2. **Scree Plot:**
- A plot of eigen values(variance explained) vs. number of components.
- We look for an "elbow point" where adding more components gives diminishing returns.

3. **Kaiser Criterion:**
- Keep components with eigen values greater than .

4. **Cross-Validation:**
- Test model performance using different numbers of components and select the optimal value based on classification/regression performance.

## Implementation Steps

1. Import required libraries (e.g., NumPy, Pandas, Scikit-learn).
2. Load and preprocess the dataset.
3. Standardize the data to ensure all features contribute equally to PCA.
4. Compute the PCA transformation using tools like Scikit-learn's `PCA` class.
5. Analyze the explained variance ratio to decide the number of components to retain.
6. Use the reduced components for visualization or as input for machine learning models.

## Code Example

```python
import numpy as np
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
import matplotlib.pyplot as plt

# Load dataset
data = np.random.rand(100, 5)  # Example dataset with 5 features

# Standardize the data
scaler = StandardScaler()
data_scaled = scaler.fit_transform(data)

# Apply PCA
pca = PCA(n_components=2)  # Reduce to 2 components
data_pca = pca.fit_transform(data_scaled)

# Explained variance ratio
print("Explained variance ratio:", pca.explained_variance_ratio_)

# Plot the reduced data
plt.scatter(data_pca[:, 0], data_pca[:, 1], alpha=0.8)
plt.title("PCA Visualization")
plt.xlabel("Principal Component 1")
plt.ylabel("Principal Component 2")
plt.show()
```

## Best Practices

- **Data Normalization**: Always standardize your data before applying PCA.
- **Explained Variance Ratio**: Retain components that explain most of the variance.
- **Domain Knowledge**: Understand the significance of principal components for your specific problem.

## Assumptions of PCA
PCA makes the following Assumpition

1. **Linearity**
- PCA assumes that the relationships between features are linear, meaning that the data can be well-represented by a linear transformation.

2. **Large Variance Contains More Infromation**
- PCA assumes that features with higher variance are more important in explaining the structure of the data.
- However, this may not always be ture( e.g. in noisy datasets).

3. **Orthogonality of Principal Components**
- PCA assumes that the principal components are **uncorrelated (orthogonal)** to each other.

4. **Mean-Centered Data**
- Thes data should be **centered (mean = 0)** before applying PCA to ensure accurate results.

5. **Equal Importance of Features**
- PCA assumes that features are measured on the **same scale**.
- If features have different scales, **standardization (Z-score normalization)** is required before applying PCA.

---

## Resources
- Scikit-learn PCA Documentation
- Wikipedia - Principal Component Analysis
