# Day 22: Multiple Linear Regression — Model Evaluation and House Price Prediction

## 1. Introduction

Multiple Linear Regression is a supervised machine learning technique that predicts a continuous numerical value using multiple independent variables. Unlike Simple Linear Regression, which uses only one input feature, Multiple Linear Regression considers several features to make predictions.

House prices depend on several factors, such as house size, number of bedrooms, bathrooms, floors, condition, and location. Therefore, using multiple features may help a model understand house prices more effectively than using house size alone.

In this task, a Multiple Linear Regression model was trained using the preprocessed King County House Sales dataset. The model was also used to predict the price of a custom house, and its performance was compared with that of the Simple Linear Regression model using Mean Absolute Error (MAE) and the R² score.

## 2. Objectives

* Understand Multiple Linear Regression.
* Train a model using multiple house-related features.
* Compare simple and multiple regression models.
* Predict the price of a custom house.
* Understand Mean Absolute Error (MAE).
* Understand the coefficient of determination (R² score).
* Evaluate and compare model performance.

## 3. What Is Multiple Linear Regression?

Multiple Linear Regression is an extension of Simple Linear Regression that uses two or more independent variables to predict a dependent variable.

For house price prediction, the independent variables may include:

* Number of bedrooms.
* Number of bathrooms.
* Scaled house size.
* Number of floors.
* Waterfront availability.
* Living area.
* House condition.
* Location category.

The general equation of Multiple Linear Regression is:

$$
y = b_0 + b_1x_1 + b_2x_2 + \cdots + b_nx_n
$$

Where:

* \(y\) = Predicted target value.
* \(b_0\) = Intercept.
* \(b_1, b_2, \ldots, b_n\) = Model coefficients.
* \(x_1, x_2, \ldots, x_n\) = Independent variables.
* \(n\) = Number of input features.

The model learns the coefficients from the training data to minimize prediction errors.

## 4. Training the Multiple Linear Regression Model

In this task, all available input features are used to train a new regression model.

```python
multiple_model = LinearRegression()

multiple_model.fit(X_train, y_train)

y_pred_multiple = multiple_model.predict(X_test)

print(y_pred_simple)
print(y_pred_multiple)

print(
    "Multiple Linear Regression model has been trained "
    "and predictions made successfully!"
)
```

### Explanation

1. `LinearRegression()` initializes a new regression model.
2. `fit(X_train, y_train)` trains the model using all the training features.
3. `predict(X_test)` generates predictions for the testing dataset.
4. The predicted values can be compared with the actual house prices.

Using multiple features allows the model to consider more information about each house when estimating its price.

## 5. Simple vs. Multiple Linear Regression

The two models differ mainly in the number of input variables used for prediction.

| Feature                 | Simple Linear Regression | Multiple Linear Regression                       |
| ----------------------- | ------------------------ | ------------------------------------------------ |
| Input variables         | One                      | Two or more                                      |
| Main input in this task | `Scaled_size`            | All available features                           |
| Model complexity        | Lower                    | Higher                                           |
| Interpretation          | Easier                   | Requires interpretation of multiple coefficients |
| Prediction information  | Limited to one feature   | Includes several house characteristics           |

Multiple Linear Regression can capture relationships involving more features, but adding more variables does not automatically guarantee better predictions. The usefulness and quality of the selected features also matter.

## 6. Predicting the Price of a Custom House

The notebook demonstrates how to predict the price of a newly specified house using the trained Multiple Linear Regression model.

The custom house has the following characteristics:

* Bedrooms: 3
* Bathrooms: 2
* Scaled size: 0.35
* Floors: 2
* Waterfront: 0
* Living area: 1800 square feet
* Condition: 4
* Location category: Mid-Range

The notebook creates a DataFrame with these values:

```python
custom_house = pd.DataFrame([{
    'bedrooms': 3.0,
    'bathrooms': 2.0,
    'Scaled_size': 0.35,
    'floors': 2.0,
    'waterfront': 0,
    'sqft_living': 1800.0,
    'condition': 4,
    'Loc_Budget': 0,
    'Loc_Mid-Range': 1,
    'Loc_Premium': 0
}])

custom_house = custom_house[X_train.columns]

predicted_price = multiple_model.predict(custom_house)[0]

print(f"Predicted price for the custom house: ${predicted_price:,.2f}")
```

### Explanation

The input values describe the characteristics of the house whose price is to be predicted.

The location is represented using encoded columns. In this example, the Mid-Range location category is set to 1, while the Budget and Premium categories are set to 0.

The statement:

```python
custom_house = custom_house[X_train.columns]
```

ensures that the custom house's columns appear in the same order as the training features.

Finally, `predict()` estimates the house price using the trained model.

**Observation:** The notebook generates a numerical price prediction from the specified characteristics. The exact predicted price depends on the trained model and the contents of the preprocessed dataset.

## 7. Understanding Model Evaluation

Training a model is not enough to determine whether it makes reliable predictions. Its predictions must be compared with actual values using suitable evaluation metrics.

In this task, the notebook uses two metrics:

1. Mean Absolute Error (MAE).
2. R² Score.

These metrics help evaluate the model's prediction errors and its ability to explain variations in house prices.

## 8. Mean Absolute Error (MAE)

Mean Absolute Error measures the average absolute difference between actual and predicted values.

**Formula:**

$$
MAE = \frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y}_i|
$$

Where:

* \(n\) = Number of observations.
* \(y_i\) = Actual value.
* \(\hat{y}_i\) = Predicted value.

The absolute difference ensures that positive and negative errors do not cancel each other out.

### Interpretation

For house price prediction, MAE indicates the average magnitude of the prediction error in the same units as the target variable. If the target is measured in dollars, MAE is also measured in dollars.

A lower MAE generally indicates more accurate predictions, provided the models are evaluated on the same test data.

## 9. R² Score

The R² score, also called the coefficient of determination, measures how well the model explains the variation in the target variable relative to a baseline that predicts the mean.

Its formula is:

$$
R^2 = 1-\frac{SS_{res}}{SS_{tot}}
$$

Where:

* \(SS_{res}\) = Sum of squared prediction errors.
* \(SS_{tot}\) = Total sum of squares around the actual mean.

### Interpretation

* **R² = 1:** The predictions perfectly match the actual values.
* **R² = 0:** The model performs like the mean-value baseline under the standard R² definition.
* **R² below 0:** The model performs worse than that baseline on the evaluated data.

A higher R² score generally indicates that the model explains more variation in the target variable. However, it does not mean that every prediction is accurate.

## 10. Evaluating and Comparing the Models

The notebook calculates MAE and R² for both the Simple Linear Regression model and the Multiple Linear Regression model.

```python
from sklearn.metrics import mean_absolute_error, r2_score

# Evaluate the simple model
mae_simple = mean_absolute_error(y_test, y_pred_simple)
r2_simple = r2_score(y_test, y_pred_simple)

# Evaluate the multiple model
mae_multiple = mean_absolute_error(y_test, y_pred_multiple)
r2_multiple = r2_score(y_test, y_pred_multiple)

print("=== Model Performance Comparison ===")

print(
    f"Simple Model (Size only): "
    f"MAE = ${mae_simple:,.2f} | R² Score = {r2_simple:.4f}"
)

print(
    f"Multiple Model (All Clues): "
    f"MAE = ${mae_multiple:,.2f} | R² Score = {r2_multiple:.4f}"
)
```

### Explanation

The `mean_absolute_error()` function calculates the average absolute prediction error, while `r2_score()` calculates the coefficient of determination.

Both models are evaluated using the same test targets, making their results comparable.

### Observation

The notebook's key takeaway is that including additional useful features, such as bedrooms, bathrooms, floors, and location, can reduce prediction error and improve the R² score in this experiment.

The actual metric values should be taken from the notebook's execution output rather than assumed or invented.

## 11. Importance of Model Evaluation

Model evaluation is important because:

1. It measures how closely predictions match actual values.
2. It helps compare different machine learning models.
3. It reveals whether a model performs poorly on unseen data.
4. It supports informed decisions about feature selection and model improvement.
5. It helps identify models that may require further training or refinement.

MAE and R² provide complementary information. MAE describes the magnitude of errors, while R² measures the model's explanatory performance relative to a baseline.

## 12. Exercises for Further Practice

### Exercise 1: Change the Train-Test Split

Change the testing proportion from 20% to 30%.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.30, random_state=42
)
```

Retrain the model and observe whether the R² score changes. A different split changes the data available for training and testing, which may affect the evaluation results.

### Exercise 2: Predict Price Using Bedrooms

Train a Simple Linear Regression model using only the `bedrooms` feature instead of `Scaled_size`.

Evaluate the model using MAE and R². Compare its performance with the model based on house size to investigate which feature is more useful for prediction in the selected dataset.

## 13. Conclusion

This task demonstrated Multiple Linear Regression for predicting house prices using several housing characteristics. The model was trained on the preprocessed dataset and used to estimate prices for test observations and a custom house.

The performance of Simple and Multiple Linear Regression was compared using Mean Absolute Error and the R² score. These metrics help assess prediction accuracy and explanatory performance.

The task showed how additional useful features can improve house price prediction. It also highlighted the importance of evaluating machine learning models on unseen data before relying on their predictions.
