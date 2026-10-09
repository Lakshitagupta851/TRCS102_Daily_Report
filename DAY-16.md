# DAY 16 OF TRAINING

## Titanic Data Analysis — Scatter Plot and Correlation Heatmap

Welcome to this session of Industrial Training for AI & Machine Learning!

In this session, we will continue analyzing the Titanic passenger dataset using Pandas, Matplotlib, and Seaborn. We will examine the relationship between passenger age and ticket fare using a scatter plot and study correlations between numerical features using a heatmap.

These techniques help us understand relationships between variables and identify patterns in a dataset.

---

## Learning Objectives

By the end of this session, you will be able to:

* Handle missing numerical values using median imputation.
* Understand scatter plots and their applications.
* Analyze the relationship between passenger age and ticket fare.
* Understand correlation between numerical variables.
* Create and interpret a correlation heatmap.

---

## What is Relationship Analysis?

Relationship analysis examines how two or more variables are associated with one another. Scatter plots and correlation heatmaps are useful techniques for exploring these relationships.

---

## 1. Handling Missing Age Values

Missing values can affect data analysis. Median imputation replaces missing numerical values with the median of the available observations.

The median is often useful because it is less affected by extreme values than the mean.

### Python Code

```python
df = pd.read_csv("train.csv")

median_age = df["Age"].median()
df["Age"] = df["Age"].fillna(median_age)

print("Missing age values:")
print(df["Age"].isnull().sum())
```

### Output

The number of missing values in the `Age` column is displayed. After median imputation, the number should be zero.

---

## 2. Age vs Ticket Fare — Scatter Plot

A scatter plot represents individual observations as points on a graph. It helps us examine the relationship between two numerical variables.

In this example:

* The X-axis represents passenger age.
* The Y-axis represents ticket fare.
* Different colors represent survival status.

### Python Code

```python
plt.figure(figsize=(8, 5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Fare",
    hue="Survived",
    palette="coolwarm",
    alpha=0.7
)

plt.title("Passenger Age vs Ticket Fare")
plt.xlabel("Age (Years)")
plt.ylabel("Ticket Fare")
plt.grid(True)
plt.show()
```

### Output

The scatter plot displays passenger ages against ticket fares, with colors indicating survival status.


<img width="592" height="441" alt="image" src="https://github.com/user-attachments/assets/fc0a52a9-dd98-48bf-923f-9a1071d4bb69" />

**Observation:** The graph helps compare ticket fares paid by passengers of different ages and examine their survival status. Some passengers paid substantially higher fares than others.

---

## 3. Understanding Correlation

Correlation is a statistical measure that describes the strength and direction of the relationship between two variables.

The correlation coefficient generally ranges from -1 to +1.

* **Positive correlation:** Both variables tend to increase together.
* **Negative correlation:** One variable tends to decrease as the other increases.
* **Zero or near-zero correlation:** There is little or no linear relationship between the variables.

Correlation does not necessarily mean that one variable causes changes in another.

---

## 4. Correlation Heatmap

A heatmap represents numerical values using colors. A correlation heatmap displays correlation coefficients between selected numerical features in a matrix.

The Pandas `corr()` function calculates the correlation matrix, while Seaborn's `heatmap()` function visualizes it.

### Python Code

```python
columns = ["Survived", "Pclass", "Age", "Fare"]

corr = df[columns].corr()

plt.figure(figsize=(7, 5))

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1,
    linewidths=1,
    fmt=".2f"
)

plt.title("Titanic Features Correlation Heatmap")
plt.show()
```

### Output

The correlation heatmap displays relationships among survival status, passenger class, age, and ticket fare. Each cell contains a correlation coefficient, with colors indicating its direction and strength.


<img width="557" height="427" alt="image" src="https://github.com/user-attachments/assets/46cba528-6df2-48f8-becc-57a1d97324fb" />

**Observations:**

* Passenger class and survival generally show a negative correlation because higher numerical class values represent lower passenger classes.
* Ticket fare and survival generally show a positive correlation in the Titanic training dataset.
* The relationship between age and survival may be weaker than some other feature relationships.

The exact values depend on the dataset and are displayed inside the heatmap.

---

## Conclusion

In this session, we explored relationships in the Titanic dataset using scatter plots and correlation heatmaps. We also learned to handle missing age values through median imputation.

Scatter plots help visualize relationships between two numerical variables, while correlation heatmaps summarize relationships among multiple features.

These techniques are useful for exploratory data analysis and help identify patterns before building machine learning models.

---
