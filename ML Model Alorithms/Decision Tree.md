# Decision Tree

## Introduction
A **Decision Tree** is a supervised machine learning algorithm used for classification and regression tasks. It is a tree-like model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility.

## Structure of a Decision Tree
A decision tree consists of:
- **Root Node**: The starting point of the tree that represents the entire dataset.
- **Internal Nodes**: Represent tests on an attribute.
- **Branches**: Represent the outcome of a test.
- **Leaf Nodes**: Represent class labels (for classification) or continuous values (for regression).

## How a Decision Tree Works
1. The dataset is split into subsets based on the feature that provides the best information gain.
2. This process is recursively applied to each subset.
3. The tree grows until a stopping criterion is met (e.g., maximum depth, minimum samples per leaf, or pure nodes).

## Splitting Criteria
Decision trees use different criteria to decide the best split at each node:
- **Gini Impurity**: Measures the probability of incorrectly classifying a randomly chosen element.
- **Entropy (Information Gain)**: Measures the level of disorder in a set. Entropy is the measure of randomness.
- **Mean Squared Error (for Regression)**: Measures variance reduction.

## Advantages of Decision Trees
- Easy to understand and interpret.
- Handles both **numerical and categorical data**.
- Requires **minimal data preprocessing**.
- **Captures Non-Linear Relationships:** Can model complex patterns without requiring transformations.

## Disadvantages of Decision Trees
- Prone to overfitting, especially with deep trees.
- Can be sensitive to noisy data.
- **Greedy Algorithm:** It selects splits locally, which may not always be globally optimal.

## Pruning Techniques
Pruning helps reduce overfitting by trimming unnecessary branches:
- **Pre-pruning**: Stops tree growth early based on predefined conditions.
- **Post-pruning**: Removes branches after the tree is built using validation data.

## Implementing a Decision Tree in Python
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_iris

# Load dataset
iris = load_iris()
X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target, test_size=0.2, random_state=42)

# Create and train the model
dt = DecisionTreeClassifier(criterion='gini', max_depth=3, random_state=42)
dt.fit(X_train, y_train)

# Predict
y_pred = dt.predict(X_test)
```

## What is the difference between Gini Impurity and Entropy in a Decision Tree?

| **Criterion**            | **Gini Impurity**                                       | **Entropy**                                          |
|--------------------------|--------------------------------------------------------|------------------------------------------------------|
| **Definition**           | Measures the probability of incorrect classification if we randomly choose a label. | Measures the level of uncertainty or randomness in the dataset. |
| **Formula**             | \( Gini = 1 - \sum p_i^2 \)                            | \( Entropy = - \sum p_i \log_2 p_i \)               |
| **Range**               | 0 (pure) to 0.5 (maximum impurity for a binary class)  | 0 (pure) to 1 (maximum randomness for a binary class) |
| **Computational Efficiency** | Faster to compute (no logarithm)                 | Slightly slower due to log calculations            |
| **Behavior**            | Tends to create purer nodes earlier                    | More sensitive to class distribution               |

### Key Takeaway:
- **Gini Impurity** prefers simpler splits, making it computationally faster.  
- **Entropy** may result in deeper trees but accounts for uncertainty more explicitly.

## Conclusion
Decision trees are a powerful tool for classification and regression tasks. However, they need to be tuned properly to avoid overfitting. They form the basis for more advanced ensemble methods like Random Forests and Gradient Boosting.
