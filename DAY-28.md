# Day 28: Random Forests — Ensemble Learning, Model Evaluation and Feature Importance

## 1. Introduction

**Random Forest** is a supervised machine learning algorithm that combines multiple Decision Trees to make predictions. It is an ensemble learning technique commonly used for classification and regression.

A single Decision Tree may overfit the training data. Random Forest reduces the effect of individual tree errors by combining predictions from multiple trees.

In this project, a Random Forest classifier is used to predict Titanic passenger survival and compared with Decision Tree and Logistic Regression models.

## 2. Objectives

* Understand ensemble learning and Random Forests.
* Learn bootstrap aggregation and feature sampling.
* Train a Random Forest classifier.
* Evaluate model performance using accuracy and a classification report.
* Analyze a confusion matrix.
* Perform five-fold cross-validation.
* Compare feature importance with Logistic Regression coefficients.
* Compare multiple classifiers on the same test set.

## 3. Dataset Description

The Titanic dataset is loaded from `train.csv`.

**Input features:** `Pclass`, `Age`, `Fare`, `SibSp`, `Parch` and `IsFemale`.

**Target variable:** `Survived`

* `0`: Did not survive.
* `1`: Survived.

Missing age values are replaced with the median, missing embarkation values with the mode, and sex is converted into a binary feature.

## 4. Theory

### 4.1 Ensemble Learning

Ensemble learning combines multiple models to produce a prediction. The goal is to obtain more reliable predictions than those from an individual model.

### 4.2 How Random Forest Works

Random Forest builds multiple Decision Trees using two main techniques:

1. **Bootstrap Aggregation (Bagging):** Each tree is trained using a random sample of the training data selected with replacement.
2. **Feature Subspace Sampling:** Each split considers a random subset of available features, helping reduce similarity between trees.

For classification, the forest combines the trees' predictions using majority voting.

### 4.3 Important Hyperparameters

* `n_estimators`: Number of trees in the forest.
* `max_depth`: Maximum depth allowed for each tree.
* `random_state`: Controls reproducibility.
* `n_jobs`: Controls parallel processing; `-1` uses available processors.

### 4.4 Model Evaluation Metrics

* **Accuracy:** Proportion of all predictions that are correct.
* **Precision:** Proportion of predicted positive cases that are actually positive.
* **Recall:** Proportion of actual positive cases correctly identified.
* **F1-score:** Harmonic mean of precision and recall.
* **Confusion Matrix:** Displays correct and incorrect predictions for each class.

### 4.5 Cross-Validation

Five-fold cross-validation divides the training data into five parts. The model is trained and validated five times, using a different part for validation each time.

The mean and standard deviation of the scores help assess performance across different splits.

### 4.6 Feature Importance

Random Forest provides Gini-based feature importance, which measures each feature's contribution to reducing impurity across the trees.

Logistic Regression coefficients have direction:

* Positive coefficients indicate an association with higher predicted log-odds of survival.
* Negative coefficients indicate an association with lower predicted log-odds of survival.

The magnitudes of Logistic Regression coefficients should be interpreted carefully because the features are not standardized.

## 5. Implementation in Python

### Step 1: Import Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.linear_model import LogisticRegression

from sklearn.model_selection import (
    train_test_split,
    cross_val_score
)

from sklearn.metrics import (
    accuracy_score,
    classification_report,
    confusion_matrix,
    ConfusionMatrixDisplay
)

import warnings
warnings.filterwarnings("ignore")
```

### Step 2: Load and Preprocess Data

```python
df = pd.read_csv("train.csv")

df["Age"] = df["Age"].fillna(df["Age"].median())

df["Embarked"] = df["Embarked"].fillna(
    df["Embarked"].mode()[0]
)

df["IsFemale"] = df["Sex"].map({
    "female": 1,
    "male": 0
})

features = [
    "Pclass", "Age", "Fare",
    "SibSp", "Parch", "IsFemale"
]

X = df[features]
y = df["Survived"]

X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.20,
    random_state=42,
    stratify=y
)
```

### Step 3: Train the Random Forest Classifier

```python
rf = RandomForestClassifier(
    n_estimators=100,
    max_depth=5,
    random_state=42,
    n_jobs=-1
)

rf.fit(X_train, y_train)

y_pred_rf = rf.predict(X_test)

train_acc = accuracy_score(
    y_train, rf.predict(X_train)
)

test_acc = accuracy_score(
    y_test, y_pred_rf
)

cv_scores = cross_val_score(
    rf,
    X_train,
    y_train,
    cv=5,
    scoring="accuracy"
)

print("Training Accuracy:", round(train_acc * 100, 2), "%")
print("Testing Accuracy:", round(test_acc * 100, 2), "%")

print(
    "Mean 5-Fold CV Accuracy:",
    round(cv_scores.mean() * 100, 2), "%"
)

print(
    "CV Standard Deviation:",
    round(cv_scores.std() * 100, 2), "%"
)

print("\nClassification Report:")
print(
    classification_report(
        y_test,
        y_pred_rf,
        target_names=["Died", "Survived"]
    )
)
```

**Observation:** Training accuracy, testing accuracy and cross-validation accuracy provide different views of model performance. The classification report gives precision, recall and F1-score for both classes.

### Step 4: Plot the Confusion Matrix

```python
cm = confusion_matrix(y_test, y_pred_rf)

disp = ConfusionMatrixDisplay(
    confusion_matrix=cm,
    display_labels=["Died", "Survived"]
)

disp.plot(colorbar=False)
plt.title("Random Forest Confusion Matrix")
plt.show()
```

**Observation:** The diagonal cells represent correct predictions, while the off-diagonal cells represent incorrect predictions.

### Step 5: Analyze Feature Importance

```python
importance_df = pd.DataFrame({
    "Feature": X.columns,
    "Importance": rf.feature_importances_
})

importance_df = importance_df.sort_values(
    "Importance",
    ascending=False
)

print(importance_df)

plt.figure(figsize=(9, 5))

sns.barplot(
    data=importance_df,
    x="Importance",
    y="Feature"
)

plt.title("Random Forest Feature Importance")
plt.xlabel("Gini Importance")
plt.ylabel("Feature")
plt.tight_layout()
plt.show()
```

**Observation:** Features with higher importance contributed more to impurity reduction in the trained forest. Importance does not establish causation or indicate whether a feature increases or decreases survival probability.

### Step 6: Compare Random Forest with Logistic Regression

```python
lr = LogisticRegression(
    max_iter=1000,
    random_state=42
)

lr.fit(X_train, y_train)

comparison_df = pd.DataFrame({
    "Feature": X.columns,
    "Random Forest Importance": rf.feature_importances_,
    "Logistic Regression Coefficient": lr.coef_[0]
})

print(
    comparison_df.sort_values(
        "Random Forest Importance",
        ascending=False
    )
)
```

**Observation:** Random Forest importance describes the contribution of features to tree splits. Logistic Regression coefficients describe the direction of each feature's contribution to the model's log-odds, holding other features constant.

<img width="1437" height="635" alt="image" src="https://github.com/user-attachments/assets/3d6770a3-7ccd-43e9-97a2-aba14ca9dcd8" />


### Step 7: Compare Three Classifiers

```python
classifiers = {
    "Logistic Regression": LogisticRegression(
        max_iter=1000,
        random_state=42
    ),
    "Decision Tree": DecisionTreeClassifier(
        max_depth=3,
        random_state=42
    ),
    "Random Forest": RandomForestClassifier(
        n_estimators=100,
        max_depth=5,
        random_state=42,
        n_jobs=-1
    )
}

results = []

for name, clf in classifiers.items():
    clf.fit(X_train, y_train)

    predictions = clf.predict(X_test)

    test_accuracy = accuracy_score(
        y_test, predictions
    )

    cv_accuracy = cross_val_score(
        clf,
        X_train,
        y_train,
        cv=5,
        scoring="accuracy"
    ).mean()

    results.append({
        "Model": name,
        "Test Accuracy": test_accuracy,
        "CV Accuracy": cv_accuracy
    })

results_df = pd.DataFrame(results)

print(results_df.to_string(index=False))

plt.figure(figsize=(9, 5))

plt.bar(
    results_df["Model"],
    results_df["Test Accuracy"]
)

plt.title("Classifier Performance Comparison")
plt.ylabel("Test Accuracy")
plt.ylim(0, 1)
plt.xticks(rotation=15)
plt.tight_layout()
plt.show()
```

**Observation:** The comparison shows the test and cross-validation accuracy of each classifier. The model with the highest score should be identified from the actual results rather than assumed in advance.

<img width="881" height="432" alt="image" src="https://github.com/user-attachments/assets/985409d8-e65f-413e-a33d-f115665410b5" />


## 6. Results and Observations

* Random Forest combines multiple Decision Trees to make predictions.
* Bagging and feature sampling help reduce the variance of individual trees.
* Limiting tree depth can help control model complexity.
* The confusion matrix reveals the types of classification errors.
* Cross-validation evaluates performance across multiple training-data splits.
* Feature importance identifies features that contribute to tree-based predictions.
* Comparing several classifiers helps determine which model performs best on the given dataset.

*Note: Exact scores and feature rankings depend on running the notebook with `train.csv`.*

## 7. Conclusion

In this practical, a Random Forest classifier was developed to predict Titanic passenger survival. The model was evaluated using accuracy, a classification report, a confusion matrix and five-fold cross-validation. Feature importance was also compared with Logistic Regression coefficients.

The experiment demonstrates how ensemble learning combines multiple Decision Trees and provides tools for evaluating model performance and understanding feature contributions.
