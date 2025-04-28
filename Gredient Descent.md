# Greadient Descent

The main idea behing Gradient Descent is thst we are iteratively adjusting the model parameter such that we are able to reduce the difference between the **predicted** and **actual** values, thus improving the model performance. Basically a Gradient Descent is the itrative model to find the local minimum of a diffrentiable function. Gradient Descent is an optimization algorithm used to minimize a function by iteratively moving in the direction of the steepest descent, defined by the negative of the gradient. In machine learning, it's mainly used to minimize the cost function in training models.

It is one of the most important topics in Machine Learning because it is the building block for Linear Regression, Logistic Regression, Support Vector Mechanism and Neural Network.

## How does Gradient Descent work?
Gradient Descent updates model parameters (like weights) by calculating the gradient of the loss function with respect to the parameters. It then moves the parameters slightly in the opposite direction of the gradient to reduce the loss, using the update rule:

$$
\theta = \theta - \alpha \nabla_\theta J(\theta)
$$

where: $\( \theta \)$ are the parameters, $\( \alpha \)$ is the learning rate, $\( J(\theta) \)$ is the cost function.

## What are the different types of Gradient Descent?
- **Batch Gradient Descent:** Uses the entire dataset to compute gradients at every step.
- **Stochastic Gradient Descent (SGD):** Updates parameters for each training sample individually.
- **Mini-batch Gradient Descent:** Uses a small random subset of the data to compute updates, balancing between batch and stochastic gradient descents.

## What is the role of the learning rate in Gradient Descent?
The learning rate tells us how bis a step we takes towards the minimum. If it’s too small, convergence is slow; if it’s too large, the algorithm might overshoot the minimum or even diverge.



---

# Reference
- [Gradient Descent Algorithm in Machine Learning - GeeksForGeets](https://www.geeksforgeeks.org/gradient-descent-algorithm-and-its-variants/)
