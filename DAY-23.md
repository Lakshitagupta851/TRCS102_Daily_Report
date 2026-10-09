# Day 23: Polynomial Regression — Predicting House Prices Using Curves 🏠📈

## Introduction

In the previous days, we learned how Linear Regression predicts house prices using a straight line. However, real-world data does not always follow a straight-line relationship.

**Polynomial Regression** helps us model curved relationships between input features and the target variable. In this project, we use Polynomial Regression to predict house prices based on house size.

We will use Python, Pandas, Matplotlib, and Scikit-learn to prepare the data, train the model, evaluate its performance, and visualize its predictions.

## Objectives

* Understand the concept of Polynomial Regression.
* Learn the difference between Linear and Polynomial Regression.
* Load and prepare the house-price dataset.
* Train a Degree 2 Polynomial Regression model.
* Evaluate the model using MAE and R² Score.
* Visualize actual house prices and predicted values.

## 1. What Is Polynomial Regression?

Polynomial Regression is a machine learning technique that models relationships between variables using polynomial terms such as \(x^2\), \(x^3\), and higher powers.

Unlike simple Linear Regression, which fits a straight line, Polynomial Regression can fit a curve to the data.

For example, a Degree 2 Polynomial Regression model can be represented as:

$$
y = b_0 + b_1x + b_2x^2
$$

Where:

* \(y\) = predicted house price
* \(x\) = house size
* \(b_0\) = intercept
* \(b_1\) = coefficient of the original feature
* \(b_2\) = coefficient of the squared feature

### Linear Regression vs Polynomial Regression

| Linear Regression                                | Polynomial Regression                         |
| ------------------------------------------------ | --------------------------------------------- |
| Fits a straight line.                            | Can fit a curved line.                        |
| Uses the original feature.                       | Creates additional polynomial features.       |
| Suitable for approximately linear relationships. | Useful for relationships that show curvature. |

## 2. Import Libraries and Load the Dataset

We begin by importing the required libraries and loading the preprocessed dataset named `kc_house_preprocessed.csv`.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score

# Load the preprocessed dataset
df = pd.read_csv("kc_house_preprocessed.csv")

print("Dataset loaded successfully!")

# Select 80 houses for a simpler visualization
df_sample = df.sample(n=80, random_state=42)

# Select house size as the input feature
X = df_sample[["sqft_living"]]

# Select house price as the target
y = df_sample["price"]

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=42
)

print("Training houses:", len(X_train))
print("Testing houses:", len(X_test))
```

### Explanation

* **Pandas:** Loads and processes the dataset.
* **NumPy:** Helps generate numerical values for visualization.
* **Matplotlib:** Creates graphs.
* **PolynomialFeatures:** Generates polynomial features.
* **LinearRegression:** Trains the regression model.
* **train_test_split:** Divides the dataset into training and testing sets.
* **MAE and R² Score:** Measure model performance.

The dataset is sampled to select 80 houses. The data is then divided into 80% training data and 20% testing data.

## 3. Train the Polynomial Regression Model

We create a Degree 2 Polynomial Regression model. It generates a squared feature and uses Linear Regression to learn the relationship between house size and price.

```python
# Create a Degree 2 Polynomial Regression model
poly_model = make_pipeline(
    PolynomialFeatures(degree=2),
    LinearRegression()
)

# Train the model
poly_model.fit(X_train, y_train)

print("Polynomial Regression model trained successfully!")
```

### Explanation

The `PolynomialFeatures(degree=2)` function creates polynomial features up to degree 2.

The `make_pipeline()` function combines polynomial feature generation and Linear Regression into one workflow.

The `fit()` method trains the model using the training data.

## 4. Evaluate Model Performance

After training, we use the test dataset to predict house prices. We evaluate the predictions using Mean Absolute Error (MAE) and the R² Score.

```python
# Predict prices for the test data
y_pred = poly_model.predict(X_test)

# Calculate evaluation metrics
mae = mean_absolute_error(y_test, y_pred)
test_r2 = r2_score(y_test, y_pred)

# Evaluate training performance
y_train_pred = poly_model.predict(X_train)
train_r2 = r2_score(y_train, y_train_pred)

print("--- Model Performance ---")
print(f"Mean Absolute Error (MAE): ${mae:,.2f}")
print(f"Test R² Score: {test_r2:.2%}")
print(f"Training R² Score: {train_r2:.2%}")
```

### Understanding the Evaluation Metrics

**1. Mean Absolute Error (MAE)**

MAE measures the average absolute difference between actual and predicted house prices.

$$
MAE=\frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y}_i|
$$

A smaller MAE indicates that predictions are closer to the actual prices.

**2. R² Score**

The R² Score indicates how well the model explains variations in house prices.

* A score close to 1 indicates a strong fit.
* A score close to 0 indicates that the model explains little of the variation.
* A negative score indicates that the model performs worse than predicting the mean target value on that dataset.

The actual evaluation values depend on the dataset and the trained model; they should be taken from the notebook output rather than assumed in advance.

## 5. Visualize the Polynomial Regression Curve

Visualization helps us compare actual house prices with the curved relationship learned by the model.

```python
# Generate house sizes for a smooth curve
x_range = np.linspace(
    X["sqft_living"].min(),
    X["sqft_living"].max(),
    500
).reshape(-1, 1)

# Predict prices for the generated house sizes
y_range_pred = poly_model.predict(x_range)

# Plot actual house prices
plt.figure(figsize=(10, 6))

plt.scatter(
    X["sqft_living"],
    y,
    alpha=0.7,
    label="Actual House Prices"
)

# Plot the Polynomial Regression curve
plt.plot(
    x_range.ravel(),
    y_range_pred,
    linewidth=3,
    label="Polynomial Regression Curve"
)

plt.title("Polynomial Regression: House Price Prediction")
plt.xlabel("Living Area (Square Feet)")
plt.ylabel("House Price ($)")
plt.grid(True, linestyle="--", alpha=0.5)
plt.legend()
plt.tight_layout()
plt.show()
```

### Observation

The scatter plot represents actual house prices, while the curved line represents prices predicted by the Polynomial Regression model.

The curve helps us observe how the predicted price changes with living area. However, a curved line does not automatically mean that the model is more accurate; its performance must be checked using evaluation metrics.

## 6. Applications of Polynomial Regression

Polynomial Regression can be used in several areas:

1. **Real Estate:** Predicting property prices from house size.
2. **Business:** Studying nonlinear sales trends.
3. **Economics:** Analysing relationships between economic variables.
4. **Engineering:** Modelling curved relationships between measurements.
5. **Environmental Science:** Analysing certain nonlinear changes in environmental data.

## 7. Advantages and Limitations

### Advantages

* Models curved relationships between variables.
* Extends the capabilities of Linear Regression.
* Can capture patterns that a straight line may miss.
* Is available through common Python machine learning libraries.

### Limitations

* Higher-degree polynomials may overfit the training data.
* The model can perform poorly on data outside the observed range.
* Results depend on the quality and suitability of the input features.
* A more complex model is not necessarily a better model.

## Conclusion

In Day 23, we learned how to use **Polynomial Regression** to predict house prices. We loaded and prepared the dataset, selected house size as the input feature, trained a Degree 2 model, evaluated predictions using MAE and R² Score, and visualized the predicted curve.

Polynomial Regression is useful when the relationship between input and output variables is curved rather than approximately linear. Evaluating the model on unseen data helps us understand how well it performs.
