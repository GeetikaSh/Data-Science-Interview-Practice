# Why Divide by \( n - 1 \) in Sample Standard Deviation?

**Sample standard deviation** is a measure of how much the values in a sample dataset deviate from the sample mean. It is used instead of **population standard deviation** because collecting data from an entire population is often impractical or impossible due to its large size.

To make the estimate unbiased, we use **Bessel’s correction**, which means we divide by $\( n - 1 \)$ instead of $𝑛$. This adjustment compensates for the fact that a sample tends to underestimate variability in the population. It happens so because when estimating the **population standard deviation** from the **sample standard deviation**,
$\( x_i \)$ is closer to $\( \bar{x} \)$ than to $\( \mu \)$. This results in an **underestimation** of the population variance. To compensate for this, the **Sample Standard Deviation** is divided by $\( n - 1 \)$ instead of $\( n \)$.

> Using \( n - 1 \) instead of \( n \) gives a more accurate estimate of the population variance and standard deviation, especially for small sample sizes. For large samples, the difference becomes negligible.

---

## Bessel's Correction

- To correct this bias, we divide by \( n - 1 \) instead of \( n \). This adjustment accounts for the loss of **one degree of freedom** when calculating the sample mean $\( \bar{x} \)$.  
- Degrees of freedom $\( n - 1 \)$ represent the number of values in the sample that can vary independently once the mean is fixed.  
- This observation arose because researchers noticed that dividing by $\( n \)$ underestimated the standard deviation, particularly for skewed data.  
  Experiments were conducted to calculate the standard deviation by dividing by $\( n - 1 \)$, $\( n - 2 \)$, and so on. It was observed that dividing by $\( n - 1 \)$ provided results very close to the true population standard deviation.  
  This adjustment is known as correcting for the **underestimated standard deviation**, which is why $\( n - 1 \)$ is used.

---

## Mathematical Explanation

- The variance formula is:  
  
  $s^2 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n - 1}$

- The sample standard deviation is simply the square root of the unbiased variance:  

  $s = \sqrt{s^2} = \sqrt{\frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n - 1}}$

---

## Reference

- Krish Nair YouTube Video: [Why Sample Variance is Divided by \( n - 1 \)](https://youtu.be/vGsRwB3TsiE?si=tAnS1-1_1hqyrc1U)
