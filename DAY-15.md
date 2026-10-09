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
* Interpret graphical data and extract useful insights.

---

## What is Data Visualization?

Data Visualization is the graphical representation of data using charts and graphs. It helps us understand complex datasets by identifying patterns, trends, distributions, and unusual values.

### Installing Required Libraries

```bash
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

### Python Code

```python
df = pd.read_csv("train.csv")

print("Data loaded successfully!")
print(df.head(3))
print(df.isnull().sum())
```

### Output

The first three rows of the Titanic dataset are displayed, followed by the number of missing values in each column.

---

## 2. Passenger Age Distribution — Histogram

A histogram represents the distribution of numerical data by grouping values into intervals called bins. It helps us understand which age ranges occur most frequently.

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
plt.show()
```

### Output

The histogram displays the distribution of passenger ages, along with a smooth KDE curve.

<img width="722" height="485" alt="image" src="https://github.com/user-attachments/assets/cf12126b-1b17-42fc-88b7-35b204158859" />


**Observation:** The graph helps identify the age ranges that occur most frequently among passengers. Missing age values are not included in the histogram.

---

## 3. Passenger Survival Counts — Count Plot

A count plot displays the number of observations belonging to different categories. In the Titanic dataset, the `Survived` column indicates whether a passenger survived.

* `0` represents passengers who did not survive.
* `1` represents passengers who survived.

### Python Code

```python
plt.figure(figsize=(6, 4))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Passenger Survival Counts")
plt.xlabel("Survival Status (0 = Died, 1 = Survived)")
plt.ylabel("Number of Passengers")
plt.show()
```

### Output

The count plot compares the number of passengers who survived with the number who did not survive.

<img width="725" height="487" alt="image" src="https://github.com/user-attachments/assets/bb3bd3f6-5b81-4d17-a7eb-78cace3494d9" />


**Observation:** The graph shows that more passengers did not survive than survived in the Titanic training dataset.

---

## 4. Ticket Fare Distribution — Box Plot

A box plot represents the distribution of numerical data using quartiles, a median, and whiskers. It helps identify potential outliers.

An outlier is a value that lies unusually far from the majority of observations.

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
plt.show()
```

### Output

The box plot displays the distribution of ticket fares and potential outliers.

<img width="672" height="482" alt="image" src="https://github.com/user-attachments/assets/4fdeb9bf-f9de-4466-8ce7-d26755179f2e" />


**Observation:** The graph helps identify unusually high ticket fares. These values may require further investigation before statistical analysis.

---

## Conclusion

In this session, we practiced data visualization using the Titanic dataset. We loaded and inspected the data, studied passenger age distribution, compared survival counts, and identified potential outliers in ticket fares.

These visualizations help us understand data more clearly and discover useful patterns before performing further analysis.

---
