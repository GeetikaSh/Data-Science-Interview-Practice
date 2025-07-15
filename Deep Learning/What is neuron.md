# 🧠 Neuron – Interview Questions & Answers

_A quick reference for interviews on the basic unit of Deep Learning: the Neuron._

---

## 📌 1. What is an artificial neuron?

**Answer**:  
An **artificial neuron** is a computational unit that mimics a biological neuron. It performs a weighted sum of inputs, adds a bias, and applies an activation function.

**Mathematical formula**:  

$$
y = \phi\left(\sum_{i=1}^{n} w_i x_i + b\right)
$$

Where:
- \( x_i \): input features  
- \( w_i \): weights  
- \( b \): bias  
- ($\phi$): activation function  
- \( y \): output

**Visual Diagram**:
```scss
      x₁      x₂      x₃      xₙ
       │       │       │       │
    ┌──▼──┐ ┌──▼──┐ ┌──▼──┐ ┌──▼──┐
    │ ×w₁ │ │ ×w₂ │ │ ×w₃ │ │ ×wₙ  |
    └──┬──┘ └──┬──┘ └──┬──┘ └──┬──┘
       └───────┴───────┴───────┘
                ▼
            + Bias (b)
                ▼
        Activation Function (φ)
                ▼
             Output (y)
```

---

## 📌 2. What are the key components of a neuron?

**Answer**:
- **Inputs \( x \)**: Feature values  
- **Weights \( w \)**: Strength of each input  
- **Bias \( b \)**: Adjusts the output  
- **Summation Function**: $z = \sum w_i x_i + b$
- **Activation Function \( \phi(z) \)**: Introduces non-linearity

---

## 📌 3. What is the role of the activation function?

**Answer**:  
The activation function $\phi(z)$ allows the neuron to capture **non-linear patterns**. Without it, even deep networks behave like a linear model.

**Common Activation Functions**:

- **Sigmoid**:
  $$
  \sigma(z) = \frac{1}{1 + e^{-z}}
  $$

- **Tanh**:
  $$
  \tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}
  $$

- **ReLU (Rectified Linear Unit)**:
  $$
  \text{ReLU}(z) = \max(0, z)
  $$

---

## 📌 4. What happens when weights are initialized to zero?

**Answer**:  
All neurons learn the **same features**, breaking symmetry. Gradients during backpropagation become identical, making the network fail to learn. Solution: **random weight initialization** (e.g., Xavier, He).

---

## 📌 5. What is the difference between weight and bias?

**Answer**:  
- **Weight**: Controls the importance of each input  
- **Bias**: Allows shifting the activation curve left or right  
Bias helps the model learn even when all input features are zero.

---

## 📌 6. What is a perceptron?

**Answer**:  
A **perceptron** is the simplest neural unit introduced by Frank Rosenblatt. It uses a **step function** as the activation and is suitable only for **linearly separable** problems.

---

## 📌 7. Why are multiple neurons and layers used?

**Answer**:  
To increase the **model's capacity** to learn:
- **Complex and non-linear features**
- **Hierarchical representations** (e.g., edges → shapes → objects)

---

## 📌 8. Can you visualize what a neuron does?

**Answer**:

```scss
       Inputs
         │
x₁ ─────┐
x₂ ─────┼─▶ Weighted Sum (Σ w·x + b) ─▶ Activation ─▶ Output
xₙ ─────┘
```

Mathematically:

$$
z = w_1 x_1 + w_2 x_2 + \dots + w_n x_n + b
$$

$$
y = \phi(z)
$$

---

## 📌 9. What is the output of a neuron used for?

**Answer**:
- In **hidden layers**: passed to the next layer  
- In the **final layer**: used to generate predictions (e.g., classification probability, regression value)

---

## 📌 10. What is the derivative of ReLU and why is it important?

**Answer**:  
ReLU is defined as:

$$
\text{ReLU}(z) = \begin{cases}
      z & \text{if } z > 0 \\
      0 & \text{if } z \leq 0
   \end{cases}
$$

Its **derivative** is:

$$
\frac{d}{dz}\text{ReLU}(z) = \begin{cases}
      1 & \text{if } z > 0 \\
      0 & \text{if } z \leq 0
   \end{cases}
$$

This derivative is used during **backpropagation** to compute gradients and update weights.

---

## ✅ Summary Table

| Component         | Purpose                                    |
|------------------|--------------------------------------------|
| Inputs \( x \)    | Feature values                             |
| Weights \( w \)   | Scale importance of inputs                 |
| Bias \( b \)      | Shifts activation threshold                |
| Summation         | Computes \( z = \sum w_ix_i + b \)         |
| Activation \( \phi \) | Non-linear transformation               |
| Output            | Prediction or input for next layer         |

---

> Understanding the artificial neuron is key to mastering neural networks and building intuition for deeper models like CNNs, RNNs, and Transformers.
