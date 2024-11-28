# Why Divide by \( n - 1 \) in Sample Standard Deviation?

- When calculating the **sample standard deviation**, we aim to estimate the **population standard deviation**. Here's why dividing by $( n - 1 )$ instead of $( n )$ is necessary

## Bias in Variance Estimation
- When calculating the variance using a sample, the sample mean $( \bar{x} \)$ is used instead of the true population mean $( \mu \)$.
- Since the sample mean is calculated from the data, it introduces a **bias** because the data points are closer to $( \bar{x} \)$. than they would be to $( \mu \)$.
- This leads to an **underestimation** of the population variance.

## Bessel's Correction
- To correct this bias, we divide by $( n - 1 )$ instead of $( n )$. This adjustment accounts for the loss of one degree of freedom when calculating the sample mean $( \bar{x} \)$.
- Degrees of freedom $( n - 1 )$ reflect the number of values in the sample that can vary independently once the mean is fixed.
- This observation arose because researchers noticed that dividing by $( n )$ underestimated the standard deviation, particularly for skewed data. Experiments were conducted to calculate the standard deviation by dividing by $( n - 1 )$, $( n - 2 )$, and so on. It was observed that dividing by $( n - 1 )$ provided results very close to the true population standard deviation. This is known as correcting for the **underestimated standard deviation**, which is why $( n - 1 )$ is used.

## Mathematical Explanation
- The variance formula is:

  $s^2 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n - 1}$

- Dividing by $( n - 1 )$ ensures that the expected value of $( s^2 )$ matches the true population variance $(sigma^2)$.

## Standard Deviation
- The sample standard deviation is simply the square root of the unbiased variance:
  
  $s = \sqrt{s^2} = \sqrt{\frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n - 1}}$

## Key Point
Using $( n - 1 )$ instead of $( n )$ gives a more accurate estimate of the population variance and standard deviation, especially for small sample sizes. For large samples, the difference becomes negligible.

## Refrence
- Krish Nair You tube Video: [Why Sample Variance is Divided by n-1](https://youtu.be/vGsRwB3TsiE?si=tAnS1-1_1hqyrc1U)
