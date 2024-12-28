# Standardization vs. Normalization

## Standardization (Z-Score Normalization)

**Formula:**  
$X_{\text{new}} = \frac{X - \mu}{\sigma}$

- Standardization is helpful when the data follows a Gaussian distribution.  
- It transforms the data such that the mean becomes 0 and the standard deviation becomes 1.  
- Standardization does not get affected by outliers because it does not have a predefined range for transformed features.

---

## Normalization (Min-Max Scaling)

**Formula:**  
$X_{\text{new}} = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}$

- Normalization scales the features to a similar range, typically \([0,1]\) or \([-1,1]\).  
- It is useful when there are no significant outliers, as it cannot handle them effectively.  
- Example: Normalize *age* but not *income*, as income often has a few high-value outliers, while age tends to be more uniformly distributed.

---

## Differences Between Normalization and Standardization

| **Normalization**                          | **Standardization**                           |
|--------------------------------------------|-----------------------------------------------|
| Minimum and maximum values are used for scaling. | Mean and standard deviation are used for scaling. |
| Scales features to a range of \([0,1]\) or \([-1,1]\). | Not bounded to a specific range.              |
| Useful when features are on different scales. | Ensures zero mean and unit standard deviation. |
| Affected by outliers.                       | Not affected by outliers.                     |
