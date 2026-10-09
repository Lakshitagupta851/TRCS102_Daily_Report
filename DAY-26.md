# Day 26: Classification and Logistic Regression — Predicting Titanic Passenger Survival 🚢

## Introduction

Machine Learning is used to make predictions from data. In regression, we predict continuous values such as house prices, whereas in **classification**, we predict categories or labels.

In this project, we explore **Logistic Regression** using the Titanic dataset. We build a model to predict whether a passenger survived and another model to classify passengers into first, second, or third class.

We also learn how to evaluate classification models using accuracy, confusion matrices, precision, recall, and F1-score.

## Objectives

* Understand classification in Machine Learning.
* Learn the difference between binary and multiclass classification.
* Understand Logistic Regression and the Sigmoid function.
* Prepare the Titanic dataset for model training.
* Predict passenger survival using Binary Classification.
* Predict passenger class using Multiclass Classification.
* Evaluate models using classification metrics.
* Understand how changing the decision threshold affects predictions.

## 1. What Is Classification?

Classification is a supervised Machine Learning technique used to predict a category or label from input features.

For example:

* Predicting whether an email is spam or not spam.
* Predicting whether a passenger survived or did not survive.
* Predicting whether a customer will leave a service.
* Classifying an image into different categories.

There are two major types of classification.

### Binary Classification

Binary Classification predicts one of two possible classes.

**Example:** Predicting Titanic passenger survival.

* `1` = Survived
* `0` = Did not survive

### Multiclass Classification

Multiclass Classification predicts one of three or more classes.

**Example:** Predicting a passenger's ticket class.

* `1` = First class
* `2` = Second class
* `3` = Third class

## 2. What Is Logistic Regression?

Logistic Regression is a supervised Machine Learning algorithm commonly used for classification. It calculates a weighted combination of input features and converts the result into a probability.

For binary classification, it uses the **Sigmoid function**:

$$
\sigma(z)=\frac{1}{1+e^{-z}}
$$

Where:

* \(z\) is the weighted combination of input features.
* \(e\) is the mathematical constant.
* \(\sigma(z)\) is a value between 0 and 1.

The probability is then compared with a decision threshold. By default, a probability of at least 0.5 is classified as class 1, while a probability below 0.5 is classified as class 0.

### Sigmoid Function Visualization

```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(z):
    return 1 / (1 + np.exp(-z))

z = np.linspace(-7, 7, 200)

plt.figure(figsize=(8, 4))
plt.plot(z, sigmoid(z), linewidth=3, label="Sigmoid Curve")
plt.axvline(0, linestyle="--")
plt.axhline(0.5, linestyle=":", label="Threshold (0.5)")

plt.title("The Sigmoid Function")
plt.xlabel("Weighted Input (z)")
plt.ylabel("Probability")
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

### Observation

The Sigmoid curve converts different input values into probabilities between 0 and 1. This allows Logistic Regression to estimate the probability of a passenger belonging to a particular class.

<img width="815" height="392" alt="image" src="https://github.com/user-attachments/assets/dd7c8e7c-f6c0-4c0f-ac53-79c12572e076" />

## 3. Import Libraries and Load the Dataset

We use the Titanic dataset stored in `train.csv`.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import (
    accuracy_score,
    confusion_matrix,
    classification_report
)

# Set visualization style
sns.set_theme(style="whitegrid")

# Load the Titanic dataset
df = pd.read_csv("train.csv")

# Display dataset information
print("Dataset Shape:", df.shape)
print(df.head())
```

### Explanation

* **Pandas:** Loads and processes tabular data.
* **NumPy:** Performs numerical operations.
* **Matplotlib:** Creates graphs.
* **Seaborn:** Creates statistical visualizations.
* **Scikit-learn:** Provides classification algorithms and evaluation metrics.

The `head()` method displays the first five rows, while `shape` shows the number of rows and columns in the dataset.

## 4. Data Preprocessing

Machine Learning algorithms require suitable input values. The Titanic dataset contains missing values and categorical text data.

We perform the following preprocessing steps:

1. Fill missing `Age` values using the median.
2. Fill missing `Embarked` values using the most frequent category.
3. Convert the `Sex` column into numeric values.

```python
# Fill missing age values with the median
df["Age"] = df["Age"].fillna(df["Age"].median())

# Fill missing Embarked values with the most common category
most_common_embarked = df["Embarked"].mode()[0]
df["Embarked"] = df["Embarked"].fillna(most_common_embarked)

# Convert Sex into a numeric feature
df["IsFemale"] = df["Sex"].map({
    "female": 1,
    "male": 0
})

# Select features for binary classification
features = ["Age", "Fare", "SibSp", "Parch", "IsFemale"]

print("Preprocessing complete!")
print(df[features].head())
```

### Explanation

* `Age`: Passenger's age.
* `Fare`: Ticket fare.
* `SibSp`: Number of siblings or spouses aboard.
* `Parch`: Number of parents or children aboard.
* `IsFemale`: 1 for female and 0 for male.

The preprocessing step fills missing values in the selected columns and converts gender into a numeric feature.

## 5. Binary Classification — Predicting Survival

In this task, the model predicts whether a passenger survived the Titanic disaster.

* **Input features (X):** Age, Fare, SibSp, Parch and IsFemale.
* **Target variable (y):** Survived.

### Step 1: Split the Dataset

We divide the dataset into training and testing sets. The training set is used to train the model, while the testing set evaluates its performance on unseen data.

```python
# Define input features and target
X = df[features]
y = df["Survived"]

# Split into 80% training and 20% testing
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

print("Training set size:", X_train.shape[0])
print("Testing set size:", X_test.shape[0])
```

### Step 2: Train the Logistic Regression Model

```python
# Create the model
binary_model = LogisticRegression(max_iter=1000)

# Train the model
binary_model.fit(X_train, y_train)

# Predict survival on test data
y_pred = binary_model.predict(X_test)

print("Binary Logistic Regression model trained successfully!")
```

The `fit()` method trains the model using the training data. The `predict()` method predicts the survival class of passengers in the testing dataset.

### Step 3: Evaluate the Model

We use accuracy, a confusion matrix, and a classification report to evaluate the predictions.

```python
# Calculate accuracy
accuracy_bin = accuracy_score(y_test, y_pred)

print(f"Binary Classification Accuracy: {accuracy_bin:.4f}")
print(f"Accuracy Percentage: {accuracy_bin * 100:.2f}%")

# Generate confusion matrix
cm_bin = confusion_matrix(y_test, y_pred)

print("Confusion Matrix:")
print(cm_bin)

# Display confusion matrix
plt.figure(figsize=(6, 4))
sns.heatmap(
    cm_bin,
    annot=True,
    fmt="d",
    cmap="Blues",
    xticklabels=["Predicted: Not Survived", "Predicted: Survived"],
    yticklabels=["Actual: Not Survived", "Actual: Survived"]
)

plt.title("Binary Classification Confusion Matrix")
plt.xlabel("Predicted Label")
plt.ylabel("Actual Label")
plt.tight_layout()
plt.show()

# Display classification report
print(classification_report(
    y_test,
    y_pred,
    target_names=["Did Not Survive", "Survived"]
))

<img width="567" height="387" alt="image" src="https://github.com/user-attachments/assets/759a2722-609a-4ffb-a599-3b619f9fc077" />

```

## 6. Understanding Classification Metrics

### Accuracy

Accuracy measures the proportion of predictions that are correct.

$$
Accuracy=\frac{\text{Correct Predictions}}{\text{Total Predictions}}
$$

Higher accuracy generally indicates that more predictions are correct.

### Confusion Matrix

A confusion matrix compares actual classes with predicted classes.

| Term                | Meaning                                                  |
| ------------------- | -------------------------------------------------------- |
| True Positive (TP)  | Predicted survived, and actually survived.               |
| True Negative (TN)  | Predicted did not survive, and actually did not survive. |
| False Positive (FP) | Predicted survived, but actually did not survive.        |
| False Negative (FN) | Predicted did not survive, but actually survived.        |

### Precision

Precision measures how many passengers predicted as survivors actually survived.

$$
Precision=\frac{TP}{TP+FP}
$$

### Recall

Recall measures how many actual survivors were correctly identified.

$$
Recall=\frac{TP}{TP+FN}
$$

### F1-Score

F1-score combines precision and recall into a single measure.

$$
F1=2\cdot\frac{Precision\cdot Recall}{Precision+Recall}
$$

These metrics provide more information than accuracy alone.

## 7. Multiclass Classification — Predicting Passenger Class

In this task, we predict whether a passenger belongs to first, second, or third class.

* **Input features (X):** Survived, Age, Fare, SibSp, Parch and IsFemale.
* **Target variable (y):** Pclass.

The target `Pclass` has three possible values, making this a multiclass classification problem.

### Step 1: Prepare the Data

```python
# Select features for multiclass classification
features_multi = [
    "Survived",
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale"
]

X_multi = df[features_multi]
y_multi = df["Pclass"]

# Split the dataset
X_train_multi, X_test_multi, y_train_multi, y_test_multi = (
    train_test_split(
        X_multi,
        y_multi,
        test_size=0.2,
        random_state=42
    )
)

print("Training set size:", X_train_multi.shape[0])
print("Testing set size:", X_test_multi.shape[0])
```

### Step 2: Train the Multiclass Model

```python
# Create the multiclass Logistic Regression model
multiclass_model = LogisticRegression(max_iter=1000)

# Train the model
multiclass_model.fit(X_train_multi, y_train_multi)

print("Multiclass Logistic Regression model trained successfully!")
```

Logistic Regression can handle multiple classes using approaches such as One-vs-Rest or multinomial classification. In multinomial classification, the Softmax function converts class scores into probabilities across the available classes.

### Step 3: Evaluate the Multiclass Model

```python
# Predict passenger classes
y_pred_multi = multiclass_model.predict(X_test_multi)

# Calculate accuracy
accuracy_multi = accuracy_score(y_test_multi, y_pred_multi)

print(f"Multiclass Accuracy: {accuracy_multi:.4f}")
print(f"Accuracy Percentage: {accuracy_multi * 100:.2f}%")

# Generate confusion matrix
cm_multi = confusion_matrix(
    y_test_multi,
    y_pred_multi,
    labels=[1, 2, 3]
)

plt.figure(figsize=(7, 5))
sns.heatmap(
    cm_multi,
    annot=True,
    fmt="d",
    cmap="Blues",
    xticklabels=["Class 1", "Class 2", "Class 3"],
    yticklabels=["Class 1", "Class 2", "Class 3"]
)

plt.title("Multiclass Classification Confusion Matrix")
plt.xlabel("Predicted Class")
plt.ylabel("Actual Class")
plt.tight_layout()
plt.show()

# Display classification report
print(classification_report(
    y_test_multi,
    y_pred_multi,
    labels=[1, 2, 3],
    target_names=["Class 1", "Class 2", "Class 3"],
    zero_division=0
))
```

### Observation

The multiclass model predicts one of three passenger classes. Its confusion matrix is a 3 × 3 table that shows how many passengers from each actual class were assigned to each predicted class.

The classification report provides precision, recall and F1-score for each class.
![Uploading image.png…]()


## 8. Binary vs. Multiclass Classification

| Aspect             | Binary Classification            | Multiclass Classification         |
| ------------------ | -------------------------------- | --------------------------------- |
| Number of classes  | Exactly two                      | Three or more                     |
| Titanic example    | Predicting survival              | Predicting passenger class        |
| Target             | `Survived`                       | `Pclass`                          |
| Probability method | Sigmoid-based binary probability | Softmax or One-vs-Rest approaches |
| Confusion matrix   | 2 × 2                            | 3 × 3 for three classes           |
| Example output     | Survived or did not survive      | First, second or third class      |

## 9. Experiment: Add Passenger Class as a Feature

The passenger's ticket class may provide useful information for predicting survival. We can test whether including `Pclass` changes the model's accuracy.

```python
# Add Pclass to the binary classification features
features_with_pclass = [
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale",
    "Pclass"
]

X_extra = df[features_with_pclass]
y_extra = df["Survived"]

X_train_extra, X_test_extra, y_train_extra, y_test_extra = (
    train_test_split(
        X_extra,
        y_extra,
        test_size=0.2,
        random_state=42
    )
)

# Train the new model
model_extra = LogisticRegression(max_iter=1000)
model_extra.fit(X_train_extra, y_train_extra)

# Predict and evaluate
y_pred_extra = model_extra.predict(X_test_extra)
accuracy_extra = accuracy_score(y_test_extra, y_pred_extra)

print(f"Accuracy with Pclass: {accuracy_extra * 100:.2f}%")
print(f"Previous accuracy: {accuracy_bin * 100:.2f}%")
```

### Explanation

Adding `Pclass` allows the model to consider passenger class when predicting survival. The accuracy may improve or remain similar, depending on the data and model. The comparison should be based on the actual printed results.

## 10. Experiment: Change the Decision Threshold

By default, binary Logistic Regression commonly uses a threshold of 0.5. We can increase it to 0.7 so that a passenger is predicted to have survived only when the model estimates a survival probability of at least 70%.

```python
# Get predicted probabilities
probabilities = binary_model.predict_proba(X_test)

# Extract probability of survival (class 1)
prob_survival = probabilities[:, 1]

# Apply a threshold of 0.7
y_pred_threshold = (prob_survival >= 0.7).astype(int)

# Calculate accuracy
accuracy_threshold = accuracy_score(
    y_test,
    y_pred_threshold
)

print(f"Accuracy with 0.7 threshold: {accuracy_threshold * 100:.2f}%")

# Plot the confusion matrix
cm_threshold = confusion_matrix(
    y_test,
    y_pred_threshold
)

plt.figure(figsize=(6, 4))
sns.heatmap(
    cm_threshold,
    annot=True,
    fmt="d",
    cmap="Greens",
    xticklabels=["Predicted: Not Survived", "Predicted: Survived"],
    yticklabels=["Actual: Not Survived", "Actual: Survived"]
)

plt.title("Confusion Matrix with 0.7 Threshold")
plt.xlabel("Predicted Label")
plt.ylabel("Actual Label")
plt.tight_layout()
plt.show()
```

### Observation

Increasing the threshold makes the model more conservative about predicting survival. It generally predicts fewer passengers as survivors, which can reduce false positives while increasing false negatives. Accuracy may increase or decrease, so it should be checked using the results.

## 11. Applications of Logistic Regression

1. **Healthcare:** Predicting the likelihood of a disease category.
2. **Email Filtering:** Classifying messages as spam or not spam.
3. **Banking:** Estimating the likelihood of loan default.
4. **Marketing:** Predicting whether a customer may respond to an offer.
5. **Transportation:** Analysing passenger-related outcomes.
6. **Customer Analytics:** Predicting customer churn.

## 12. Advantages and Limitations

### Advantages

* Simple to understand and implement.
* Suitable for binary and multiclass classification.
* Produces probabilities that can support decision-making.
* Efficient for many classification problems.
* Supports evaluation through standard classification metrics.

### Limitations

* May not model complex nonlinear relationships without additional features or transformations.
* Performance depends on the quality of the input data.
* Missing values and categorical variables require appropriate preprocessing.
* Accuracy alone may not adequately describe performance when classes are imbalanced.

## Conclusion

In Day 26, we explored Classification and Logistic Regression using the Titanic dataset. We cleaned missing values, converted categorical data into numerical features, and trained models for binary and multiclass classification.

We evaluated model performance using accuracy, confusion matrices, precision, recall and F1-score. We also explored how adding passenger class as a feature and changing the decision threshold can affect predictions.

This practical demonstrates how Logistic Regression can solve real-world classification problems and how evaluation metrics help us understand the strengths and limitations of a trained model.
