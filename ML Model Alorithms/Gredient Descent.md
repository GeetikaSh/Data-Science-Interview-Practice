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
- **Batch Gradient Descent:** Uses the entire dataset to compute gradients at every step. This can be slow for large datasets but may lead to a more accurate model. It is effective for convex or relatively smooth error manifolds because it moves directly toward an optimal solution by taking a large step in the direction of the negative gradient of the cost function. However, it can be slow for large datasets because it computes the gradient and updates the parameters using the entire training dataset at each iteration. This can result in longer training times and higher computational costs.
- **Stochastic Gradient Descent (SGD):** Updates parameters for each training sample individually. This can be faster than batch gradient descent but may lead to more noise in the updates.
- **Mini-batch Gradient Descent:** Uses a small random subset of the data to compute updates, balancing between batch and stochastic gradient descents as it can be faster than batch gradient descent and less noisy than Stochastic Gradient Descent.
- **Momentum-based Gradient Descent:** Momentum is a variant of gradient descent that incorporates information from the previous weight updates to help the algorithm converge more quickly to the optimal solution. Momentum adds a term to the weight update that is proportional to the running average of the past gradients, allowing the algorithm to move more quickly in the direction of the optimal solution. The updates to the parameters are based on the current gradient and the previous updates. This can help prevent the optimization process from getting stuck in local minima and reach the global minimum faster.

## What is the role of the learning rate in Gradient Descent?
The learning rate tells us how bis a step we takes towards the minimum. If it’s too small, convergence is slow; if it’s too large, the algorithm might overshoot the minimum or even diverge.

## What is Vanishing and Exploding Gradients
Vanishing and exploding gradients are common problems that can occur during the training of deep neural networks. These problems can significantly slow down the training process or even prevent the network from learning altogether.

- The vanishing gradient problem occurs when gradients become too small during backpropagation. The weights of the network are not considerably changed as a result, and the network is unable to discover the underlying patterns in the data. Many-layered deep neural networks are especially prone to this issue. The gradient values fall exponentially as they move backward through the layers, making it challenging to efficiently update the weights in the earlier layers.
- The exploding gradient problem, on the other hand, occurs when gradients become too large during backpropagation. When this happens, the weights are updated by a large amount, which can cause the network to diverge or oscillate, making it difficult to converge to a good solution.

## What problems can occur if the learning rate is too high or too low?
- **Too High:** Oscillation around the minimum or divergence.
- **Too Low:** Extremely slow convergence, taking a long time to reach the minimum or getting stuck in local minima.

**To address these problems the following technique can be used:**
- **Weights Regularzations:** The initialization of weights can be adjusted to ensure that they are in an appropriate range. Using a different activation function, such as the Rectified Linear Unit (ReLU), can also help to mitigate the vanishing gradient problem.
- **Gradient clipping:** It involves limiting the maximum and minimum values of the gradient during backpropagation. This can prevent the gradients from becoming too large or too small and can help to stabilize the training process.
- **Batch normalization:** It can also help to address these problems by normalizing the input to each layer, which can prevent the activation function from saturating and help to reduce the vanishing and exploding gradient problems.

## How can you improve or speed up Gradient Descent?
- Use adaptive learning rate methods like Adam, RMSProp, or Adagrad.
- Apply momentum to dampen oscillations and accelerate convergence.
- Feature scaling (like normalization or standardization) can also make gradient descent converge faster.

## What is Momentum in Gradient Descent?
: Momentum helps accelerate Gradient Descent by adding a fraction of the previous update vector to the current update. It smoothens updates and helps navigate ravines in the cost surface.
The momentum-based gradient descent update rules are:

$$
v := \beta v + (1 - \beta) \nabla_{\theta} J(\theta)
$$

$$
\theta := \theta - \alpha v
$$

where: $\( \beta \)$ is the momentum term, $\( \alpha \)$ is the learning rate, $\( v \)$ is the velocity (accumulated gradient), $\( \nabla_{\theta} J(\theta) \)$ is the gradient of the loss function with respect to \( \theta \).

## What are some common optimization algorithms derived from Gradient Descent?
- Momentum (discussed above)
- Nesterov Accelerated Gradient (NAG)
- Adagrad
- RMSProp
- Adam (combines momentum + adaptive learning rates)

## Can Gradient Descent get stuck?
Yes. Gradient Descent can get stuck in:
- Local minima (less common in high dimensions)
- Saddle points (points where the gradient is zero but it's neither a minima nor maxima)
- Plateaus (areas where gradient is very small)

Strategies like random restarts, using advanced optimizers (e.g., Adam), or adding noise to gradients can help.

## What is the difference between Gradient Descent and Stochastic Gradient Descent?
- **Gradient Descent** computes gradients using the whole dataset, leading to stable but slow updates.
- **Stochastic Gradient Descent (SGD)** computes gradients using a single sample at a time, making updates noisier but often faster and better at escaping local minima.

## Advantages of Gradient Descent
- **Widely used**: Gradient descent and its variants are widely used in machine learning and optimization problems because they are **effective and easy to implement**.
- **Convergence:** Gradient descent and its variants can converge to a global minimum or a good local minimum of the cost function, depending on the problem and the variant used.
- **Scalability:** Many variants of gradient descent can be parallelized and are scalable to large datasets and high-dimensional models.
- **Flexibility:** Different variants of gradient descent offer a range of trade-offs between accuracy and speed, and can be adjusted to optimize the performance of a specific problem.

## Disadvantages of Gradient Descent
- **Choice of learning rate:** The choice of learning rate is crucial for the convergence of gradient descent and its variants. Choosing a learning rate that is too large can lead to oscillations or overshooting while choosing a learning rate that is too small can lead to slow convergence or getting stuck in local minima.
- **Sensitivity to initialization:** Gradient descent and its variants can be sensitive to the initialization of the model’s parameters, which can affect the convergence and the quality of the solution.
- **Time-consuming:** Gradient descent and its variants can be time-consuming, especially when dealing with large datasets and high-dimensional models. The convergence speed can also vary depending on the variant used and the specific problem.
- **Local optima:** Gradient descent and its variants can converge to a local minimum instead of the global minimum of the cost function, especially in non-convex problems. This can affect the quality of the solution, and techniques like random initialization and multiple restarts may be used to mitigate this issue.

---

# Reference
- [Gradient Descent Algorithm in Machine Learning - GeeksForGeets](https://www.geeksforgeeks.org/gradient-descent-algorithm-and-its-variants/)
