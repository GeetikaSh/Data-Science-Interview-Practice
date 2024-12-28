# Naive Bayes Classifier

The **Naive Bayes** algorithm is a probabilistic classifier based on **Bayes' Theorem**. It is called "naive" because it assumes that all features are independent of each other, which is rarely true in real-world datasets.

---

## Bayes' Theorem

The foundation of Naive Bayes is **Bayes' Theorem**, which calculates the probability of a hypothesis $H$ given some evidence $E$:

$$
P(H|E) = \frac{P(E|H) \cdot P(H)}{P(E)}
$$

- $P(H|E)$: Posterior probability (probability of $H$ given $E$).
- $P(E|H)$: Likelihood (probability of $E$ given $H$).
- $P(H)$: Prior probability of $H$.
- $P(E)$: Evidence (probability of $E$).

---

## Key Assumptions

1. **Feature Independence**: Naive Bayes assumes that the features are conditionally independent given the target class.
   - Example: If predicting if an email is spam, the word "win" is assumed to be independent of the word "money."

2. **Class Conditional Independence**: The probability of each feature contributes independently to the final classification.

---

## Types of Naive Bayes

1. **Gaussian Naive Bayes**
   - Used when features are continuous and assumed to follow a normal distribution.
   - Likelihood is calculated using the Gaussian probability density function:
   - 
     $P(x|y) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$
     - $\mu$: Mean
     - $\sigma^2$: Variance

2. **Multinomial Naive Bayes**
   - Suitable for discrete data like word counts in text classification.
   - Likelihood is calculated based on feature counts in each class.

3. **Bernoulli Naive Bayes**
   - Used for binary features (e.g., presence or absence of words in a document).
   - Works well for text classification tasks with binary term frequency. Where
     each word represents one features in the data.

---

## Steps in Naive Bayes Classification

1. **Calculate Priors**:
   - $P(Class)$ is estimated as the fraction of training examples belonging to each class.

2. **Compute Likelihood**:
   - For each feature given a class $P(feature|Class)$, calculate probabilities using the type of Naive Bayes selected (Gaussian, Multinomial, or Bernoulli).

3. **Apply Bayes’ Theorem**:
   - Combine priors and likelihoods to calculate posterior probabilities for each class.

4. **Prediction**:
   - Assign the class with the highest posterior probability.

---

## Advantages

- **Fast and Simple**: Easy to implement and computationally efficient.
- **Scalable**: Works well with large datasets.
- **Works Well with Small Data**: Performs surprisingly well even with small amounts of data.
- **Handles Categorical Data**: Particularly effective for text classification.
- **Handles high dimension data**: Workd well with high dimention data.

---

## Limitations

- **Feature Independence Assumption**: Real-world data rarely satisfies the independence assumption, which can degrade accuracy.
- **Zero Frequency Problem**: If a feature value is not present in the training data for a class, the probability is zero. This is addressed using **smoothing** (e.g., Laplace smoothing).
  ```
  Laplace smoothing adds a small constant (e.g., 1) to all probabilities to handle cases where a
  word/class pair has never been seen in training, preventing probabilities of zero.
  ```
- **Not Ideal for Continuous Data**: Gaussian Naive Bayes assumes a normal distribution, which may not always hold.

---

## Applications

- **Text Classification**: Spam detection, sentiment analysis, and document categorization.
- **Medical Diagnosis**: Classifying diseases based on symptoms.
- **Recommendation Systems**: Predicting user preferences based on past data.

---

## Example (Pseudocode)

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.feature_extraction.text import CountVectorizer

# Sample text data
documents = ["Free money now", "Earn money easily", "Work hard and earn more"]
labels = [1, 1, 0]  # 1: Spam, 0: Not Spam

# Convert text to feature vectors
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(documents)

# Train a Naive Bayes model
model = MultinomialNB()
model.fit(X, labels)

# Make a prediction
test_doc = ["Free money"]
test_X = vectorizer.transform(test_doc)
prediction = model.predict(test_X)

print("Prediction:", prediction)  # Output: [1] (Spam)
```

---

## Interview Qustions
- **How does Naive Bayes handle missing data?**\
 Naive Bayes can ignore missing features during classification because it calculates the probabilities for each feature independently.

- **What happens if the independence assumption is violated in Naive Bayes?**\
 The predictions may become less accurate, but Naive Bayes can still work well in practice, especially for large datasets.

---
## Reference
- [Naive Bayes Classifier | GeeksforGeeks](https://www.geeksforgeeks.org/naive-bayes-classifiers/)

