# 5 Assumptions of Linear Regression (with Code)

Linear Regression relies on the following key assumptions. Violating them can lead to unreliable or misleading results.

---

## 1. Linearity

**Assumption:**  
The relationship between the independent variables and the dependent variable is **linear**.

**How to Check:**  
Plot predicted values vs. residuals. The residuals should be randomly scattered.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import statsmodels.api as sm
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

# Load example dataset
df = sns.load_dataset('mpg').dropna()
X = df[['horsepower']]
y = df['mpg']

# Add constant for intercept
X_sm = sm.add_constant(X)
model = sm.OLS(y, X_sm).fit()

# Plot residuals vs. predicted values
sns.residplot(x=model.fittedvalues, y=model.resid, lowess=True)
plt.xlabel("Fitted values")
plt.ylabel("Residuals")
plt.title("Linearity Check")
plt.show()
```

## 2. Independence of Errors
**Assumption:**
Residuals should be independent of each other (no autocorrelation).

**How to Check:**
Use the Durbin-Watson statistic.

```python
from statsmodels.stats.stattools import durbin_watson

dw = durbin_watson(model.resid)
print(f"Durbin-Watson: {dw:.2f}")  # Should be around 2 (0–4 scale)
```

## 3. Homoscedasticity
**Assumption:**
The residuals should have constant variance at all levels of the independent variables.

**How to Check:**
Plot residuals vs. fitted values. Look for a funnel shape (heteroscedasticity).

```python
sns.scatterplot(x=model.fittedvalues, y=model.resid)
plt.axhline(0, linestyle='--', color='red')
plt.xlabel("Fitted values")
plt.ylabel("Residuals")
plt.title("Homoscedasticity Check")
plt.show()
```

## 4. Normality of Residuals
**Assumption:**
Residuals should be normally distributed.

**How to Check:**
Use a Q-Q plot and a histogram of residuals.

```python
# Q-Q plot
sm.qqplot(model.resid, line='s')
plt.title("Q-Q Plot for Normality of Residuals")
plt.show()

# Histogram
sns.histplot(model.resid, kde=True)
plt.title("Histogram of Residuals")
plt.show()
```

**## 5. No Multicollinearity
Assumption:**
Independent variables should not be highly correlated.

**How to Check:**
Use the Variance Inflation Factor (VIF).

```python
from statsmodels.stats.outliers_influence import variance_inflation_factor

# If multiple predictors
X_multi = df[['horsepower', 'weight', 'displacement']]
X_multi = sm.add_constant(X_multi)

vif = pd.DataFrame()
vif['Feature'] = X_multi.columns
vif['VIF'] = [variance_inflation_factor(X_multi.values, i)
              for i in range(X_multi.shape[1])]

print(vif)
```

⚠️ A VIF > 5 or 10 indicates high multicollinearity.

