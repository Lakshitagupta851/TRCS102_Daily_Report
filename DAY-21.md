# Day 21: Linear Regression — Training a Model to Predict House Prices

## 1. Introduction

Linear Regression is one of the most fundamental supervised machine learning algorithms. It is used to understand the relationship between input variables and a numerical output. It predicts a continuous value by learning the relationship between the input features and the target variable.

In this task, the King County House Sales dataset was used to train a Linear Regression model for predicting house prices. The dataset had already undergone preprocessing, including handling missing values, outliers, scaling, and categorical encoding.

The main objective was to train a model using house size as an input feature and understand how machine learning can be applied to real-world price prediction problems.

## 2. Objectives

* Understand the concept of Linear Regression.
* Load the preprocessed housing dataset.
* Separate input features and the target variable.
* Split the dataset into training and testing sets.
* Train a Simple Linear Regression model.
* Understand the coefficient and intercept of the model.
* Visualize the actual house prices and predicted prices.

## 3. What Is Linear Regression?

Linear Regression is a supervised machine learning algorithm that models the relationship between one or more independent variables and a dependent variable.

It attempts to find the best-fitting straight line that represents the relationship between the input and output data.

For example, the price of a house may depend on its size. Generally, larger houses may have higher prices. Linear Regression learns this relationship from historical data and uses it to predict prices for new houses.

### Types of Linear Regression

**1. Simple Linear Regression:** Uses one independent variable to predict the target variable.

Example: Predicting house price using house size.

**2. Multiple Linear Regression:** Uses two or more independent variables to predict the target variable.

Example: Predicting house price using size, bedrooms, bathrooms, floors, and location.

## 4. Importing Libraries and Loading the Dataset

The notebook uses Python libraries for data handling, visualization, model training, and evaluation.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score

df = pd.read_csv('kc_house_preprocessed.csv')

print("Successfully loaded")
df
```

### Explanation

* **Pandas:** Loads and manages tabular data.
* **Matplotlib:** Creates graphs and visualizations.
* **Seaborn:** Provides statistical visualization tools.
* **train_test_split:** Divides the dataset into training and testing sets.
* **LinearRegression:** Creates the regression model.
* **mean_absolute_error:** Measures the average absolute prediction error.
* **r2_score:** Measures how well the model explains variations in the target variable.

The preprocessed dataset is loaded from `kc_house_preprocessed.csv`.

## 5. Separating Features and Target Variable

Before training the model, the input variables and target variable must be separated.

* **Features (X):** The information used by the model to make predictions.
* **Target (y):** The value that the model must predict.

In this task, the target variable is `price`, while the remaining columns are used as input features.

```python
X = df.drop(columns=['price'])
y = df['price']
```

The `drop()` function removes the price column from the input features. The target variable is then stored separately in `y`.

This separation allows the model to learn the relationship between the available house information and the corresponding house price.

## 6. Train-Test Split

The dataset is divided into training and testing sets before model training.

* **Training Set (80%):** Used to train the model and learn patterns.
* **Testing Set (20%):** Used to evaluate the model on data that was not used during training.

The notebook uses the following code:

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=42
)

print(f"Training set has: {X_train.shape[0]:,} rows")
print(f"Test set has: {X_test.shape[0]:,} rows")
```

### Explanation

The `test_size=0.20` parameter assigns 20% of the observations to testing and the remaining 80% to training.

The `random_state=42` parameter makes the split reproducible, so the same division can be obtained when the code is run again on the same data.

Testing on unseen observations helps estimate how well the model may perform on new data.

## 7. Simple Linear Regression

Simple Linear Regression uses only one independent variable to predict the target.

In this notebook, the `Scaled_size` feature is selected to predict house prices.

```python
X_train_simple = X_train[['Scaled_size']]
X_test_simple = X_test[['Scaled_size']]

model = LinearRegression()

model.fit(X_train_simple, y_train)

print("Simple Linear Regression model has been trained successfully!")
```

### Explanation

1. The `Scaled_size` column is selected from the training and testing datasets.
2. The `LinearRegression()` function initializes the model.
3. The `fit()` method trains the model using the training data.
4. The model learns the relationship between scaled house size and house price.

Since only one input feature is used, this is called Simple Linear Regression.

## 8. Understanding the Regression Equation

Linear Regression represents the relationship between an input and a predicted output using the equation:

$$
y = mx + c
$$

Where:

* \(y\) = Predicted house price.
* \(x\) = Scaled house size.
* \(m\) = Slope or coefficient.
* \(c\) = Intercept.

The slope indicates how the predicted price changes when the input feature increases by one unit. The intercept represents the predicted output when the input value is zero.

The notebook extracts these values from the trained model:

```python
m = model.coef_[0]
c = model.intercept_

print(f"Robot Intercept (c): ${c:,.2f}")
print(f"Robot Coefficient / Slope (m): ${m:,.2f}")

print(
    f"\nThe robot's formula is: "
    f"Price = (${m:,.2f} * Scaled_size) + ${c:,.2f}"
)
```

The coefficient and intercept are learned from the training data rather than being selected manually.

## 9. Predicting House Prices

After training, the model can predict prices for observations in the test set.

```python
y_pred_simple = model.predict(X_test_simple)

y_pred_simple
```

The `predict()` method uses the learned regression equation to estimate house prices from the test set's scaled house sizes.

The predicted values can later be compared with the actual prices to measure model performance.

## 10. Visualizing the Best-Fit Line

A scatter plot and regression line help illustrate the relationship between house size and price.

The notebook uses the following visualization:

```python
y_pred_simple = model.predict(X_test_simple)

plt.figure(figsize=(10, 6))

plt.scatter(
    X_test_simple['Scaled_size'],
    y_test,
    color='royalblue',
    alpha=0.3,
    label='Actual Test Houses'
)

plt.plot(
    X_test_simple['Scaled_size'],
    y_pred_simple,
    color='crimson',
    linewidth=3,
    label='Robot Prediction Line'
)

plt.xlabel('House Size (Scaled MinMaxScaler)')
plt.ylabel('Price ($)')
plt.title('House Price Prediction: Actual vs. Best-Fit Line')
plt.legend()
plt.show()
```

### Observation

The scatter plot represents actual house prices, while the line represents the model's predicted prices. The visualization helps examine how well a straight-line relationship represents the observed data.

Differences between the actual points and predicted values indicate prediction errors. A straight line cannot necessarily capture every factor affecting house prices, but it provides a useful starting point for regression analysis.

## 11. Importance of Linear Regression

Linear Regression is useful because:

1. It is relatively simple to understand and implement.
2. It provides a mathematical relationship between input features and the target.
3. It can be used for predicting continuous numerical values.
4. Its coefficients help interpret the influence of input features.
5. It provides a baseline against which more advanced models can be compared.

However, its performance depends on the quality of the data and how well a linear relationship represents the problem.

## 12. Conclusion

This task introduced Linear Regression using the King County House Sales dataset. The preprocessed data was loaded, the input features and target variable were separated, and the dataset was divided into training and testing sets.

A Simple Linear Regression model was trained using `Scaled_size` to predict house prices. The regression coefficient and intercept were examined, and predictions were visualized using a scatter plot and best-fit line.

This task established the foundation for understanding regression models and prepared the way for Multiple Linear Regression and model evaluation in the next task.
