# DAY 15 OF TRAINING

## Titanic Data Analysis — Data Visualization Using Seaborn

Welcome to this session of Industrial Training for AI & Machine Learning!

In this session, we will use Python libraries such as Pandas, Matplotlib, and Seaborn to analyze the Titanic passenger dataset. We will explore passenger age distribution, survival counts, and ticket fare outliers using different types of visualizations.

The aim is to understand how data visualization helps us identify patterns, compare values, and draw meaningful conclusions from a dataset.

---

## Learning Objectives

By the end of this session, you will be able to:

* Load and inspect a dataset using Pandas.
* Understand passenger age distribution using a histogram.
* Compare survival counts using a count plot.
* Identify outliers in ticket fares using a box plot.
* Interpret graphs and extract useful insights from data.

---

## What is Data Visualization?

Data Visualization is the graphical representation of data using charts and graphs. It helps us understand complex datasets by identifying patterns, trends, distributions, and unusual values.

### Installing Required Libraries

```python
pip install pandas numpy matplotlib seaborn
```

### Importing Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 1. Loading and Inspecting the Dataset

The first step in data analysis is loading the dataset and examining its contents. We use the Titanic dataset stored in the `train.csv` file.

```python
df = pd.read_csv("train.csv")

print("Data loaded successfully!")
print(df.head(3))
print(df.isnull().sum())
```

**Output**

The first three rows of the dataset and the number of missing values in each column are displayed.

---

## 2. Passenger Age Distribution — Histogram

A histogram displays the distribution of numerical data by grouping values into intervals called bins. It helps us understand which age ranges occur most frequently.

The KDE curve shows the approximate shape of the age distribution.

### Python Code

```python
plt.figure(figsize=(8, 5))

sns.histplot(
    data=df,
    x="Age",
    kde=True,
    color="purple",
    bins=20
)

plt.title("Titanic Passenger Age Distribution")
plt.xlabel("Age (Years)")
plt.ylabel("Passenger Count")
plt.tight_layout()
plt.savefig("day15_age_distribution.png")
plt.show()
```

### Output

A histogram showing the distribution of passenger ages along with a smooth KDE curve.

![Titanic passenger age distribution](day15_age_distribution.png)

**Observation:** The graph helps identify the most common age ranges among passengers. Missing age values are not included in the histogram.

---

## 3. Passenger Survival Counts — Count Plot

A count plot displays the number of observations in different categories. In the Titanic dataset, the `Survived` column represents passenger survival status.

* `0` represents passengers who did not survive.
* `1` represents passengers who survived.

### Python Code

```python
plt.figure(figsize=(6, 4))

sns.countplot(
    data=df,
    x="Survived",
    hue="Survived",
    palette="Set2",
    legend=False
)

plt.title("Passenger Survival Counts")
plt.xlabel("Survival Status (0 = Died, 1 = Survived)")
plt.ylabel("Number of Passengers")
plt.tight_layout()
plt.savefig("day15_survival_counts.png")
plt.show()
```

### Output

A count plot comparing passengers who survived with those who did not survive.

![Titanic passenger survival counts](day15_survival_counts.png)

**Observation:** The graph shows that more passengers did not survive than survived in the training dataset.

---

## 4. Ticket Fare Distribution — Box Plot

A box plot represents numerical data using quartiles, a median, and whiskers. It helps identify potential outliers.

An outlier is a value that lies unusually far from most other observations.

### Python Code

```python
plt.figure(figsize=(8, 4))

sns.boxplot(
    data=df,
    x="Fare",
    color="pink"
)

plt.title("Ticket Fare Distribution and Outliers")
plt.xlabel("Ticket Fare")
plt.tight_layout()
plt.savefig("day15_fare_boxplot.png")
plt.show()
```

### Output

A box plot showing the distribution of ticket fares and potential outliers.

![Titanic ticket fare box plot](day15_fare_boxplot.png)

**Observation:** The graph helps identify unusually high ticket fares. These values may affect statistical analysis and should be investigated before deciding how to handle them.

---

## Conclusion

In this session, we practiced data visualization using the Titanic dataset. We loaded and inspected the data, studied passenger age distribution, compared survival counts, and identified potential ticket fare outliers.

These visualizations demonstrate how graphs help us understand data clearly and discover meaningful patterns before performing further analysis.

---
