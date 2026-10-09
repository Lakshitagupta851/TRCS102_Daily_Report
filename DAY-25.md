
# Day 25: Lasso Regression — Feature Selection with L1 Regularization 

## Introduction

In Day 24, we learned how Ridge Regression controls overfitting by reducing the size of model coefficients.

In Day 25, we will study **Lasso Regression**, another regularization technique. Lasso uses an L1 penalty and can reduce some coefficients to exactly zero. This makes it useful for reducing model complexity and performing feature selection.

We will also compare a model without regularization, Ridge Regression, and Lasso Regression using the same house-price dataset.

## Objectives

* Understand Lasso Regression.
* Learn the meaning of the L1 penalty.
* Train a Lasso Regression model using Python.
* Evaluate model performance using MAE and R² Score.
* Compare Linear Regression, Ridge Regression, and Lasso Regression.
* Visualize their prediction curves.

## 1. What Is Lasso Regression?

Lasso stands for **Least Absolute Shrinkage and Selection Operator**.

It is a regularization technique that adds a penalty based on the absolute values of model coefficients. Unlike Ridge Regression, Lasso can shrink some coefficients exactly to zero.

Its objective function is:

$$
\text{Loss}=\sum_{i=1}^{n}(y_i-\hat{y}_i)^2+\alpha\sum_{j=1}^{p}|w_j|
$$

Where:

* \(y_i\) = actual value
* \(\hat{y}_i\) = predicted value
* \(w_j\) = model coefficient
* \(\alpha\) = regularization strength

When a coefficient becomes zero, its corresponding feature does not contribute to the model prediction.

## 2. Ridge Regression vs Lasso Regression

| Ridge Regression                          | Lasso Regression                                          |
| ----------------------------------------- | --------------------------------------------------------- |
| Uses an L2 penalty.                       | Uses an L1 penalty.                                       |
| Shrinks coefficients toward zero.         | Can shrink coefficients exactly to zero.                  |
| Usually retains all features.             | Can perform feature selection.                            |
| Useful for controlling coefficient sizes. | Useful for controlling complexity and selecting features. |

Both techniques can help reduce overfitting, but neither guarantees better results for every dataset.

## 3. Load and Prepare the Dataset

We use the same preprocessed house-price dataset and the same training and testing split as in Day 24 so that the models can be compared fairly.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score

# Load the dataset
df = pd.read_csv("kc_house_preprocessed.csv")

# Select 80 houses
df_sample = df.sample(n=80, random_state=42)

# Input feature and target
X = df_sample[["Scaled_size"]]
y = df_sample["price"]

# Split into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=42
)

print("Dataset prepared successfully!")
```

## 4. Train the Lasso Regression Model

We train a Degree 6 polynomial model using Lasso Regression with `alpha=100.0`, matching the notebook's configuration.

```python
# Train the Degree 6 polynomial model with Lasso regularization
lasso_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(alpha=100.0, max_iter=10000)
)

lasso_model.fit(X_train, y_train)

# Predict house prices
y_pred_lasso = lasso_model.predict(X_test)

# Calculate evaluation metrics
mae_lasso = mean_absolute_error(y_test, y_pred_lasso)
r2_lasso = r2_score(y_test, y_pred_lasso)

print("--- Lasso Regression Performance ---")
print(f"MAE: ${mae_lasso:,.2f}")
print(f"R² Score: {r2_lasso:.2%}")
```

### Explanation

* `PolynomialFeatures(degree=6)` generates polynomial features.
* `Lasso(alpha=100.0)` applies the L1 penalty.
* `max_iter=10000` allows additional iterations for model convergence.
* `fit()` trains the model.
* `predict()` generates predictions for the test dataset.
* MAE and R² Score measure the model's performance.

The alpha value controls the strength of regularization. A stronger penalty can set more coefficients to zero, but an excessively strong penalty can also cause underfitting.

## 5. Compare All Three Models

We now compare the model without regularization, Ridge Regression, and Lasso Regression using the same testing data.

```python
# Predict using all three trained models
y_pred_wild = wild_model.predict(X_test)
y_pred_ridge = ridge_model.predict(X_test)
y_pred_lasso = lasso_model.predict(X_test)

# Create a comparison table
comparison = pd.DataFrame({
    "Model": [
        "Polynomial Regression",
        "Ridge Regression",
        "Lasso Regression"
    ],
    "MAE": [
        mean_absolute_error(y_test, y_pred_wild),
        mean_absolute_error(y_test, y_pred_ridge),
        mean_absolute_error(y_test, y_pred_lasso)
    ],
    "R2 Score": [
        r2_score(y_test, y_pred_wild),
        r2_score(y_test, y_pred_ridge),
        r2_score(y_test, y_pred_lasso)
    ]
})

print(comparison.to_string(index=False))
```

### Observation

The comparison table shows the MAE and R² Score for each model.

* A lower MAE means smaller average prediction errors.
* A higher R² Score generally indicates a better fit to the test data.
* Ridge and Lasso apply different penalties, so their predictions may differ.
* The best-performing model should be selected based on evaluation results, not simply because it uses regularization.

## 6. Visualize the Prediction Curves

The notebook compares the three models on one graph. This helps us observe how regularization affects the shape of the predicted relationship between house size and price.

```python
# Create a smooth range of scaled house sizes
x_range = np.linspace(
    X["Scaled_size"].min(),
    X["Scaled_size"].max(),
    500
).reshape(-1, 1)

plt.figure(figsize=(12, 7))

# Plot actual training observations
plt.scatter(
    X_train["Scaled_size"],
    y_train,
    alpha=0.6,
    s=50,
    label="Actual Houses"
)

# Plot the model without regularization
plt.plot(
    x_range.ravel(),
    wild_model.predict(x_range),
    linestyle="--",
    linewidth=2,
    label="Polynomial Regression (No Regularization)"
)

# Plot Ridge predictions
plt.plot(
    x_range.ravel(),
    ridge_model.predict(x_range),
    linewidth=3,
    label="Ridge Regression"
)

# Plot Lasso predictions
plt.plot(
    x_range.ravel(),
    lasso_model.predict(x_range),
    linewidth=3,
    label="Lasso Regression"
)

plt.title("Comparison of Polynomial, Ridge, and Lasso Regression")
plt.xlabel("House Size (Scaled)")
plt.ylabel("House Price ($)")
plt.grid(True, linestyle="--", alpha=0.5)
plt.legend()
plt.tight_layout()
plt.show()
```

### Explanation

* The scatter points represent actual house prices in the training dataset.
* The dashed curve represents the model without regularization.
* The Ridge curve shows predictions using an L2 penalty.
* The Lasso curve shows predictions using an L1 penalty.

The curves help illustrate the differences between the models. The exact shapes and performance depend on the dataset and the selected regularization strengths.

## 7. Applications of Lasso Regression

1. **Feature Selection:** Identifies features that contribute to a model.
2. **Real Estate:** Helps build simpler house-price prediction models.
3. **Healthcare Research:** Can select useful variables from large datasets.
4. **Finance:** Helps simplify predictive models containing many features.
5. **Data Analysis:** Reduces model complexity by eliminating some coefficients.

## 8. Advantages and Limitations of Lasso Regression

### Advantages

* Can set some coefficients exactly to zero.
* Helps reduce model complexity.
* Can improve generalization when irrelevant features are present.
* Produces simpler models that may be easier to interpret.

### Limitations

* A high alpha value can cause underfitting.
* Results depend on the choice of alpha.
* With highly correlated features, it may select one feature over another.
* It does not guarantee better predictive performance than Ridge Regression.

## Conclusion

In Day 25, we learned about Lasso Regression and its L1 regularization penalty. We trained a Lasso model, evaluated it using MAE and R² Score, and compared it with Ridge Regression and Polynomial Regression without regularization.

The main difference is that Ridge Regression shrinks coefficients, while Lasso Regression can shrink some coefficients to exactly zero. Comparing their test performance helps us choose a suitable model for house-price prediction.
