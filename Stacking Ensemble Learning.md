# Stacking Ensemble Learning

Stacking is an ensemble learning technique that combines multiple base models (also called level-0 models) to improve predictive performance. Unlike simple voting ensembles, which aggregate predictions using methods like majority vote (classification) or average (regression), stacking introduces a meta-model (also called level-1 model) that learns how to best combine the outputs of the base models.

## How It Works
1. The training dataset is fed to multiple different models (e.g., logistic regression, decision tree, SVM).
2. Each base model makes a prediction. These predictions become the input features for the meta-model.
3. The meta-model is trained to predict the final output using:
- The actual target values
- The predictions from the base models
4. When predicting on new data:
- The input features are first passed to the base models.
- Their outputs are then passed to the meta-model, which produces the final prediction.

## Why Use Stacking?
- Helps reduce underfitting, as multiple learning algorithms are combined.
- Takes advantage of the strengths of different models (e.g., one model may handle linearity well, another may handle non-linearity).
- Often results in better performance than individual models or simple voting.

## Challenges with Stacking
A potential issue is overfitting, especially when:
- All models are trained on the same data
- The dataset is small or biased

To reduce overfitting, we can use data splitting strategies:

### 1. Hold-Out Method (a.k.a. Blending)
- The training dataset is split into three parts:
  - Training Set → for training base models
  - Validation Set → for training the meta-model (using predictions of base models)
  - Test Set → for final evaluation
* The meta-model is trained on predictions from base models applied to the validation set.

**Limitation:** Only a portion of data is used to train each stage.

```
# Split data
X_train, X_val, y_train, y_val = train_test_split(X, y, test_size=0.3, random_state=42)

# Define base models
model1 = LogisticRegression(max_iter=200)
model2 = DecisionTreeClassifier()
model3 = SVC(probability=True)

# Train base models on training set
model1.fit(X_train, y_train)
model2.fit(X_train, y_train)
model3.fit(X_train, y_train)

# Predict on validation set
pred1 = model1.predict_proba(X_val)
pred2 = model2.predict_proba(X_val)
pred3 = model3.predict_proba(X_val)

# Stack predictions horizontally to form meta-features
meta_features = np.hstack((pred1, pred2, pred3))

# Train meta-model on predictions
meta_model = LogisticRegression()
meta_model.fit(meta_features, y_val)

# Final predictions from meta-model
final_pred = meta_model.predict(meta_features)
print("Accuracy (Blending):", accuracy_score(y_val, final_pred))
```

### 2. K-Fold Cross-Validation (a.k.a. Stacking)
- The training set is split into K folds.
- For each fold:
  - Base models are trained on K-1 folds.
  - Predictions are made on the held-out fold.
- This process ensures that all training examples are used both for training and prediction without overlap.
- The meta-model is trained on the stacked predictions from each fold.
- More robust and less prone to overfitting than blending.

```
from sklearn.ensemble import StackingClassifier
from sklearn.model_selection import cross_val_score

# Define base estimators
base_estimators = [
    ('lr', LogisticRegression(max_iter=200)),
    ('dt', DecisionTreeClassifier()),
    ('svm', SVC(probability=True))
]

# Meta-model
meta_model = LogisticRegression()

# Stacking classifier
stack_model = StackingClassifier(
    estimators=base_estimators,
    final_estimator=meta_model,
    cv=5  # K-Fold Cross-validation
)

# Cross-validation scores
scores = cross_val_score(stack_model, X, y, cv=5, scoring='accuracy')
print("Accuracy (Stacking CV):", scores.mean())
```
