# Hyperparameter Tunning

In machine learning, there are two main types of parameters involved during model development:

**1. Parameters**
- These are learned during the model training process.
- Examples include weights in a neural network or coefficients in linear regression.

**2. Hyperparameters**
- These are set before the training process begins.
- They govern the training process and model architecture.
- Examples: Learning rate, number of trees in a Random Forest, number of layers in a neural network, batch size, etc.

## Why Do We Tune Hyperparameters?
The main objective of hyperparameter tuning is to minimize training/validation loss and improve model performance (e.g., accuracy, F1-score, AUC).
The right combination of hyperparameters can lead to:
- Faster convergence
- Better generalization
- Avoiding overfitting or underfitting

## Common Hyperparameter Tuning Methods
- Manual Search
* The simplest method where the practitioner chooses and tests hyperparameters by trial and error.

- Grid Search
* Tests all possible combinations from a predefined set of hyperparameter values.
* Exhaustive but computationally expensive.

- Random Search
* Randomly selects combinations of hyperparameters.
* Often more efficient than grid search and can explore a larger search space in fewer iterations.

- Bayesian Optimization
* Builds a probabilistic model (e.g., Gaussian Process) of the objective function.
* Selects the next hyperparameter set based on past evaluations to balance exploration and exploitation.
* More efficient and intelligent than random or grid search.

- Evolutionary Algorithms
* Uses techniques inspired by natural evolution such as mutation, crossover, and selection to evolve a population of hyperparameter configurations over time.
* Suitable for large and complex search spaces.

- Gradient-Based Optimization
* Uses gradients of the validation loss with respect to hyperparameters.
* Requires differentiable models and is more common in neural architecture search or advanced settings.
