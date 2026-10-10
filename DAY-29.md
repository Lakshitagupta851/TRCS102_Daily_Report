# Day 29: Introduction to Clustering — Unsupervised Learning and K-Means Algorithm

## Project: Customer Segmentation for Retail Marketing

## 1. Introduction

Machine Learning is broadly divided into supervised learning, unsupervised learning, and reinforcement learning. In supervised learning, a model learns from labeled data, whereas unsupervised learning works with data that does not contain predefined target labels.

**Clustering** is an unsupervised machine learning technique used to group similar data points together. Data points within the same cluster are generally more similar to one another than to points in other clusters.

In this project, we use the **K-Means Clustering algorithm** to perform customer segmentation using the Mall Customers dataset. The objective is to identify different groups of customers based on their annual income and spending score.

Customer segmentation is useful in retail marketing because different customer groups may have different purchasing habits, spending patterns, and marketing needs.

## 2. Objectives

* Understand the concept of unsupervised learning.
* Differentiate between supervised and unsupervised learning.
* Learn the working principles of clustering.
* Understand the K-Means clustering algorithm.
* Explore the Mall Customers dataset.
* Perform exploratory data analysis.
* Understand the importance of feature scaling.
* Train a K-Means clustering model.
* Identify customer groups based on income and spending score.

## 3. Theory

### 3.1 What Is Unsupervised Learning?

Unsupervised learning is a machine learning approach in which an algorithm discovers patterns and structures from unlabeled data.

Unlike supervised learning, there is no predefined target variable that the model must predict. Instead, the algorithm attempts to identify relationships, similarities, or hidden structures within the dataset.

**Example:** A shopping mall has information about thousands of customers but does not have predefined customer categories. An unsupervised learning algorithm can group customers according to their income and spending behavior.

### 3.2 Supervised Learning vs. Unsupervised Learning

| Supervised Learning                                                  | Unsupervised Learning                                         |
| -------------------------------------------------------------------- | ------------------------------------------------------------- |
| Uses labeled data.                                                   | Uses unlabeled data.                                          |
| Has a target variable.                                               | Does not require a target variable.                           |
| Learns to predict known outcomes.                                    | Discovers hidden patterns and structures.                     |
| Examples: Linear Regression, Logistic Regression and Decision Trees. | Examples: K-Means, Hierarchical Clustering and DBSCAN.        |
| Common tasks include classification and regression.                  | Common tasks include clustering and dimensionality reduction. |

### 3.3 What Is Clustering?

Clustering is the process of dividing data points into groups called clusters based on their similarities.

The main goal is to create clusters in which the data points are similar to each other while remaining relatively different from points in other clusters.

For example, customers may be grouped into:

* High-income, high-spending customers.
* High-income, low-spending customers.
* Low-income, high-spending customers.
* Low-income, low-spending customers.
* Average-income, average-spending customers.

These groups can help a business understand customer behavior and plan suitable marketing strategies.

### 3.4 What Is the K-Means Algorithm?

K-Means is a centroid-based clustering algorithm that divides a dataset into \(K\) clusters.

Here, \(K\) represents the number of clusters selected before training. Each cluster has a centroid, which represents the center of that cluster.

The algorithm attempts to minimize the sum of squared distances between data points and their assigned cluster centroids.

The objective function is:

$$
J=\sum_{j=1}^{K}\sum_{x_i\in C_j}
\|x_i-\mu_j\|^2
$$

Where:

* \(K\) is the number of clusters.
* \(C_j\) is the set of points in cluster \(j\).
* \(x_i\) is a data point.
* \(\mu_j\) is the centroid of cluster \(j\).

A smaller objective value indicates that the points are closer to their assigned centroids, although it does not automatically guarantee that the chosen number of clusters is appropriate.

### 3.5 Steps of the K-Means Algorithm

**Step 1: Choose K**

Select the number of clusters to create. In this project, we initially use \(K=5\).

**Step 2: Initialize Centroids**

The algorithm selects initial positions for the cluster centroids. The `k-means++` initialization method helps choose starting centroids that are reasonably spread apart.

**Step 3: Assign Data Points**

Each data point is assigned to the nearest centroid according to the selected distance measure.

**Step 4: Update Centroids**

The algorithm calculates the mean position of the points assigned to each cluster and moves the centroid to that position.

**Step 5: Repeat the Process**

The assignment and centroid-update steps repeat until the algorithm converges or reaches its iteration limit.

**Step 6: Obtain the Final Clusters**

The algorithm assigns a cluster label to every data point.

### 3.6 Euclidean Distance

K-Means commonly uses Euclidean distance to measure the distance between data points.

For two points in two-dimensional space:

$$
d(p,q)=\sqrt{(p_1-q_1)^2+(p_2-q_2)^2}
$$

The algorithm assigns a point to the centroid with the smallest distance.

### 3.7 Importance of Feature Scaling

Feature scaling transforms numerical features to comparable scales.

In our dataset, annual income and spending score have different units and distributions. Because K-Means depends on distances, a feature with a larger numerical spread may have a stronger influence on the clustering result.

We use `StandardScaler` to transform each feature so that it has approximately zero mean and unit standard deviation:

$$
z=\frac{x-\mu}{\sigma}
$$

Where:

* \(x\) is the original feature value.
* \(\mu\) is the feature mean.
* \(\sigma\) is the feature standard deviation.
* \(z\) is the standardized value.

Scaling prevents differences in numerical ranges from dominating the distance calculation. However, it does not guarantee that all features have equal practical importance.

### 3.8 Exploratory Data Analysis (EDA)

Exploratory Data Analysis is the process of examining a dataset before building a machine learning model.

It helps us understand:

* The number of rows and columns.
* Data types of the features.
* Missing values.
* Summary statistics.
* Relationships between numerical variables.
* Possible patterns and unusual observations.

EDA helps identify data quality issues and supports better decisions during model development.

## 4. Dataset Description

The project uses the `Mall_Customers.csv` dataset, which contains information about 200 mall customers.

| Feature                  | Description                                         |
| ------------------------ | --------------------------------------------------- |
| `CustomerID`             | Unique identification number of each customer.      |
| `Gender`                 | Gender of the customer.                             |
| `Age`                    | Age of the customer in years.                       |
| `Annual Income (k$)`     | Annual income in thousands of dollars.              |
| `Spending Score (1-100)` | Mall-assigned spending score ranging from 1 to 100. |

For this clustering experiment, we use only two features:

1. `Annual Income (k$)`
2. `Spending Score (1-100)`

The customer ID is excluded because it is an identifier rather than a meaningful measure of customer similarity.

## 5. Implementation in Python

### Step 1: Import the Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

import warnings
warnings.filterwarnings("ignore")

sns.set_theme(style="whitegrid", palette="muted")
plt.rcParams["figure.dpi"] = 110

print("All libraries loaded successfully!")
```

**Explanation:**

* Pandas is used to load and manipulate the dataset.
* NumPy supports numerical calculations.
* Matplotlib and Seaborn create visualizations.
* `KMeans` implements the clustering algorithm.
* `StandardScaler` standardizes numerical features.

### Step 2: Load the Dataset

```python
df = pd.read_csv("Mall_Customers.csv")

print("First five rows:")
print(df.head())
```

The `read_csv()` function loads the dataset into a Pandas DataFrame. The `head()` method displays the first five records.

### Step 3: Explore the Dataset

```python
print("Dataset Shape:", df.shape)

print("\nDataset Information:")
df.info()

print("\nSummary Statistics:")
print(df.describe())

print("\nMissing Values:")
print(df.isnull().sum())

print("\nColumn Names:")
print(df.columns)
```

**Explanation:** These commands help us inspect the dataset structure, numerical distributions, data types, and missing values before applying clustering.

### Step 4: Visualize Customer Distribution

```python
plt.figure(figsize=(8, 5.5))

sns.scatterplot(
    data=df,
    x="Annual Income (k$)",
    y="Spending Score (1-100)",
    s=70,
    alpha=0.8
)

plt.title("Customer Distribution: Income vs Spending Score")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")

plt.tight_layout()
plt.show()
```

A scatter plot allows us to observe how customers are distributed according to income and spending score.

The raw plot may suggest groups with low income and low spending, high income and high spending, and other combinations. These are initial visual observations, not yet the final cluster assignments.

### Step 5: Select Features and Apply Scaling

```python
X = df[
    ["Annual Income (k$)", "Spending Score (1-100)"]
]

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)

X_scaled_df = pd.DataFrame(
    X_scaled,
    columns=X.columns
)

print("First five scaled records:")
print(X_scaled_df.head())
```

**Explanation:** The two selected features are standardized before clustering. The scaled values are used by K-Means to calculate distances and assign customers to clusters.

### Step 6: Train the K-Means Model

```python
kmeans = KMeans(
    n_clusters=5,
    init="k-means++",
    n_init=10,
    random_state=42
)

kmeans.fit(X_scaled)

labels = kmeans.labels_
centroids_scaled = kmeans.cluster_centers_

print("Model training complete!")
print("First 10 cluster labels:", labels[:10])
print("Inertia:", kmeans.inertia_)
```

**Explanation of important parameters:**

* `n_clusters=5`: Creates five clusters.
* `init="k-means++"`: Uses an initialization method that helps choose well-spread starting centroids.
* `n_init=10`: Runs the initialization process multiple times and selects a good solution.
* `random_state=42`: Makes the experiment reproducible.

The resulting cluster labels identify which group each customer belongs to. The numerical labels do not indicate any natural ranking between clusters.

## 6. Advantages of K-Means

1. **Simple to Understand:** The algorithm has a straightforward working process.
2. **Efficient:** It can work well with many numerical datasets.
3. **Easy to Implement:** Libraries such as Scikit-learn provide a ready-to-use implementation.
4. **Useful for Segmentation:** It identifies groups that can be studied separately.
5. **Scalable:** It can handle relatively large datasets when the number of clusters and features is manageable.

## 7. Limitations of K-Means

1. The number of clusters \(K\) must be selected beforehand.
2. Results may depend on the initial centroid positions.
3. Features usually need appropriate scaling.
4. Outliers can influence centroid positions.
5. K-Means may perform poorly on clusters with irregular shapes or substantially different densities.
6. Cluster labels alone do not explain the real-world meaning of each group.
7. The algorithm works primarily with numerical features and requires suitable preprocessing for categorical data.

## 8. Applications of Clustering

* **Retail:** Customer segmentation and targeted marketing.
* **Banking:** Grouping customers by transaction patterns.
* **Healthcare:** Exploring groups of patients with similar characteristics.
* **Education:** Identifying groups of learners with similar learning patterns.
* **E-commerce:** Discovering purchasing behavior.
* **Social Media:** Grouping users by interaction patterns.
* **Manufacturing:** Identifying patterns in production data.

## 9. Results and Observations

* The Mall Customers dataset contains customer information that can be used for segmentation.
* Annual income and spending score are selected as the primary clustering features.
* Standardization prepares these features for distance-based clustering.
* K-Means with \(K=5\) assigns each customer to one of five groups.
* Cluster labels can be used for further analysis and visualization.
* The business meaning of each cluster must be determined by examining its feature values.

## 10. Conclusion

In this practical, the concepts of unsupervised learning, clustering, and the K-Means algorithm were studied. The Mall Customers dataset was loaded and explored, and its income and spending-score features were standardized.

A K-Means model with five clusters was trained to group customers according to their characteristics. This practical demonstrates how unsupervised learning can discover useful patterns in unlabeled data and support data-driven customer segmentation.

The next stage focuses on visualizing the clusters, interpreting customer segments, and using the Elbow Method to examine the choice of \(K\).
