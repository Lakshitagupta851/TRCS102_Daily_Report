# Day 27: Decision Trees — Splitting, Gini Impurity, Visualization and Regularization

## 1. Introduction

A **Decision Tree** is a supervised machine learning algorithm used for classification and regression tasks. It makes predictions by repeatedly splitting data based on feature values.

In this project, a Decision Tree is used to predict whether a Titanic passenger survived or did not survive.

Unlike Logistic Regression, Decision Trees can learn non-linear decision boundaries and automatically capture interactions between features.

## 2. Objectives

* Understand the working of Decision Tree classifiers.
* Learn how Gini Impurity helps select splits.
* Train and visualize a Decision Tree.
* Identify overfitting in an unconstrained tree.
* Apply regularization using `max_depth`.
* Evaluate the model using training and testing accuracy.

## 3. Dataset Description

The project uses the Titanic dataset from `train.csv`.

**Input features:**

* `Pclass`: Passenger class.
* `Age`: Passenger's age.
* `Fare`: Ticket fare.
* `SibSp`: Number of siblings or spouses aboard.
* `Parch`: Number of parents or children aboard.
* `IsFemale`: Binary representation of passenger sex.

**Target variable:** `Survived`

* `0`: Did not survive.
* `1`: Survived.

## 4. Theory

### 4.1 How Decision Trees Work

A Decision Tree consists of:

* **Root node:** The first decision or split.
* **Internal nodes:** Conditions applied to features.
* **Branches:** Outcomes of the conditions.
* **Leaf nodes:** Final predictions.

For example, a tree may ask whether a passenger's age is below a particular value and then examine another feature to predict survival.

### 4.2 Gini Impurity

Gini Impurity measures how mixed the classes are within a node.

$$
Gini = 1-\sum_{i=1}^{n}p_i^2
$$

Here, \(p_i\) represents the proportion of samples belonging to class \(i\).

* **Gini = 0:** The node contains only one class.
* **Gini = 0.5:** Maximum impurity for a binary classification problem when both classes are equally represented.

The tree searches for splits that reduce impurity in the resulting child nodes.

### 4.3 Overfitting

An unrestricted tree can memorize the training data, including noise. It may achieve very high training accuracy but perform less effectively on unseen data.

### 4.4 Regularization

Regularization limits the complexity of a tree.

* `max_depth`: Maximum depth of the tree.
* `min_samples_split`: Minimum samples required to split a node.
* `min_samples_leaf`: Minimum samples required in a leaf.

These parameters help balance model complexity and generalization.

## 5. Implementation in Python

### Step 1: Import Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

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

print("Training samples:", len(X_train))
print("Testing samples:", len(X_test))
```

### Step 3: Train an Unrestricted Decision Tree

```python
model = DecisionTreeClassifier(random_state=42)
model.fit(X_train, y_train)

train_acc = accuracy_score(
    y_train, model.predict(X_train)
)

test_acc = accuracy_score(
    y_test, model.predict(X_test)
)

print("Training Accuracy:", round(train_acc * 100, 2), "%")
print("Testing Accuracy:", round(test_acc * 100, 2), "%")
print("Tree Depth:", model.get_depth())
print("Number of Leaves:", model.get_n_leaves())
```

**Observation:** Compare training and testing accuracy. A large gap can indicate overfitting.

### Step 4: Visualize a Shallow Decision Tree

```python
dt_shallow = DecisionTreeClassifier(
    max_depth=3,
    random_state=42
)

dt_shallow.fit(X_train, y_train)

plt.figure(figsize=(16, 8))

plot_tree(
    dt_shallow,
    feature_names=X.columns,
    class_names=["Died", "Survived"],
    filled=True,
    rounded=True,
    fontsize=9
)

plt.title("Decision Tree with Maximum Depth 3")
plt.show()
```

**Observation:** The visualization shows the splitting conditions, number of samples, class distribution and predicted class at each node.

<img width="1256" height="652" alt="image" src="https://github.com/user-attachments/assets/93eb742c-8f53-4401-8ab1-ffd0d96f5904" />


### Step 5: Tune the Maximum Depth

```python
depths = range(1, 16)

train_scores = []
test_scores = []

for depth in depths:
    dt = DecisionTreeClassifier(
        max_depth=depth,
        random_state=42
    )

    dt.fit(X_train, y_train)

    train_scores.append(
        accuracy_score(y_train, dt.predict(X_train))
    )

    test_scores.append(
        accuracy_score(y_test, dt.predict(X_test))
    )

best_depth = list(depths)[np.argmax(test_scores)]

print("Best Depth:", best_depth)
print(
    "Best Test Accuracy:",
    round(max(test_scores) * 100, 2), "%"
)

plt.figure(figsize=(9, 5))

plt.plot(
    list(depths), train_scores,
    marker="o", label="Training Accuracy"
)

plt.plot(
    list(depths), test_scores,
    marker="s", label="Testing Accuracy"
)

plt.axvline(
    best_depth,
    linestyle="--",
    label=f"Best Depth = {best_depth}"
)

plt.xlabel("Maximum Depth")
plt.ylabel("Accuracy")
plt.title("Decision Tree Accuracy vs Maximum Depth")
plt.xticks(list(depths))
plt.legend()
plt.grid(True)
plt.show()
```

**Observation:** Increasing tree depth usually allows the model to fit training data more closely. However, a deeper tree does not always improve testing performance. The best depth is selected based on the highest observed test accuracy in this experiment.

<img width="1007" height="551" alt="image" src="https://github.com/user-attachments/assets/9248750f-d04e-4ee4-88c2-33294f2a0c1a" />


## 6. Results and Observations

* Decision Trees can learn non-linear relationships between features and the target.
* Gini Impurity helps determine useful data splits.
* An unrestricted tree can overfit the training data.
* Limiting tree depth can reduce model complexity.
* Comparing training and testing accuracy helps identify possible overfitting.
* The best tree depth depends on the dataset and the evaluation results.

*Note: Exact accuracy values depend on executing the notebook with the dataset.*

## 7. Conclusion

In this practical, a Decision Tree classifier was trained to predict Titanic passenger survival. Its splitting mechanism, Gini Impurity and tree visualization were studied. The effect of maximum depth was also examined to understand overfitting and regularization.

The experiment demonstrates that controlling tree complexity is important for building a model that generalizes to unseen data.
