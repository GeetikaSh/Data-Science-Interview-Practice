# Standardization vs. Normalization

## Standardization (Z-Score Normalization)

**Formula:**  
$X_{\text{new}} = \frac{X - \mu}{\sigma}$

- Useful when data follows a **Gaussian (normal) distribution**. 
- It transforms the data such that the mean becomes 0 and the standard deviation becomes 1.  
- **Less affected by outliers** since it does not have a predefined range.
- Best for datasets with varying units (e.g., income, test scores).  
---

## Normalization (Min-Max Scaling)

**Formula:**  
$X_{\text{new}} = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}$

- Normalization scales the features to a similar range, typically \([0,1]\) or \([-1,1]\).
- Used when absolute boundaries are important (e.g., **image pixel values, age**).
- - **Sensitive to outliers**, as extreme values can disproportionately affect scaling.
- Best when data needs to fit within a specific range, especially for **neural networks** and **distance-based models** (e.g., KNN, SVMs).

---

## Differences Between Normalization and Standardization

| **Normalization**                          | **Standardization**                           |
|--------------------------------------------|-----------------------------------------------|
| Minimum and maximum values are used for scaling. | Mean and standard deviation are used for scaling. |
| Scales features to a range of \([0,1]\) or \([-1,1]\). | Not bounded to a specific range.              |
| Useful when features are on different scales. | Ensures zero mean and unit standard deviation. |
| Affected by outliers.                       | Not affected by outliers.                     |
