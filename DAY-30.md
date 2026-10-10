# Day 30: Customer Segmentation — Cluster Visualization, Interpretation and the Elbow Method

## Project: Customer Segmentation for Retail Marketing

## 1. Introduction

Customer segmentation is an important application of unsupervised machine learning. It involves dividing customers into groups based on similarities in their characteristics or behavior.

In the previous practical, we introduced clustering, explored the Mall Customers dataset, standardized the selected features, and trained a K-Means model.

In this practical, we continue the project by visualizing the generated clusters, examining their centroids, interpreting the customer segments, and applying the **Elbow Method** to study the appropriate number of clusters.

The final objective is to convert the output of a clustering algorithm into information that can help a business understand its customers and make better marketing decisions.

## 2. Objectives

* Understand the importance of cluster visualization.
* Interpret cluster labels and centroids.
* Convert standardized centroids back to the original feature scale.
* Identify different customer segments.
* Understand inertia and Within-Cluster Sum of Squares (WCSS).
* Implement the Elbow Method.
* Select a reasonable number of clusters.
* Explore the business applications of customer segmentation.
* Understand the limitations of K-Means and the importance of evaluating clustering results.

## 3. Theory

### 3.1 What Is Customer Segmentation?

Customer segmentation is the process of dividing customers into groups based on common characteristics.

These characteristics may include:

* Annual income.
* Spending behavior.
* Purchase frequency.
* Product preferences.
* Age.
* Customer engagement.

In this project, segmentation is based on annual income and spending score.

The resulting groups can help a retail business understand different customer patterns and develop marketing strategies for specific groups.

### 3.2 Importance of Cluster Visualization

After training a clustering model, it is important to visualize the results. Visualization helps us understand how the algorithm has divided the data.

A scatter plot is suitable for this project because we use two numerical features.

* The horizontal axis represents annual income.
* The vertical axis represents spending score.
* Different colors represent different clusters.
* Special markers indicate the centroids.

Visualization helps identify whether the groups appear reasonably separated and whether some clusters overlap.

However, a two-dimensional plot only shows the selected features. It cannot prove that the clusters are meaningful in every possible dimension.

### 3.3 What Are Centroids?

A centroid is the mean position of all data points assigned to a particular cluster.

For a cluster containing \(n\) data points, its centroid is calculated by taking the mean of each feature:

$$
\mu_j=\frac{1}{n_j}
\sum_{x_i\in C_j}x_i
$$

Where:

* \(\mu_j\) is the centroid of cluster \(j\).
* \(C_j\) represents the data points in that cluster.
* \(n_j\) is the number of points in the cluster.

Centroids help describe the typical feature values of each group.

For example, a centroid with relatively high income and high spending score represents a group whose average income and spending score are both high compared with other groups.

### 3.4 Why Do We Inverse-Transform Centroids?

The model is trained using standardized features. Therefore, its centroids are initially expressed in standardized units rather than the original income and spending-score units.

For easier interpretation, we use:

```python
scaler.inverse_transform(centroids_scaled)
```

This converts the centroids back to the original feature scale.

The resulting values are easier to understand because annual income is again expressed in thousands of dollars and spending score is expressed on its original scale.

### 3.5 Interpreting Customer Segments

The numerical labels assigned by K-Means, such as `0`, `1`, `2`, `3`, and `4`, are arbitrary identifiers. Cluster 4 is not necessarily better than Cluster 1.

To interpret the groups, we examine their average income and spending score.

Possible customer segments include:

1. **High Income, High Spending:** Customers who have high income and high spending scores.
2. **High Income, Low Spending:** Customers with high income but comparatively low spending scores.
3. **Average Income, Average Spending:** Customers with moderate values for both features.
4. **Low Income, High Spending:** Customers with relatively low income and high spending scores.
5. **Low Income, Low Spending:** Customers with relatively low values for both features.

These are general interpretations. The actual characteristics of each cluster must be verified from the calculated centroids.

### 3.6 What Is Inertia?

Inertia measures the total squared distance between each data point and the centroid of its assigned cluster.

In K-Means, inertia is also commonly described as Within-Cluster Sum of Squares (WCSS).

$$
WCSS=\sum_{j=1}^{K}
\sum_{x_i\in C_j}
\|x_i-\mu_j\|^2
$$

A smaller inertia value means that data points are, on average in the squared-distance sense, more tightly grouped around their centroids.

However, inertia usually decreases as the number of clusters increases. If every data point is assigned to its own cluster, inertia can become zero. Therefore, the lowest inertia alone is not a sufficient reason to choose a particular value of \(K\).

### 3.7 The Elbow Method

The Elbow Method is a technique used to help choose the number of clusters for K-Means.

It works as follows:

1. Select a range of possible cluster counts.
2. Train a separate K-Means model for each value of \(K\).
3. Record the inertia for each model.
4. Plot the number of clusters against inertia.
5. Identify the approximate point where the curve changes from a steep decline to a more gradual decline.

This point is called the **elbow** because the graph may resemble a bent arm.

Before the elbow, increasing the number of clusters can substantially improve cluster compactness. After the elbow, adding more clusters may provide smaller improvements relative to the extra model complexity.

The elbow is not always clear. It should be treated as a useful heuristic rather than a guarantee of the mathematically optimal number of clusters.

### 3.8 Difference Between Inertia and Silhouette Score

Inertia measures the compactness of clusters by calculating squared distances to centroids.

The silhouette score measures how similar a point is to its own cluster compared with other clusters. It ranges from \(-1\) to \(1\):

* A score near \(1\) suggests that the point fits its own cluster well.
* A score near \(0\) suggests that the point lies near a cluster boundary.
* A negative score may indicate that the point is closer to another cluster.

Silhouette analysis can provide additional information when the elbow plot is unclear.

### 3.9 Business Value of Customer Segmentation

The purpose of customer segmentation is not simply to create groups. The groups should help answer business questions.

For example:

* Which customers might respond to premium product offers?
* Which groups may benefit from discounts?
* Which customers have high spending scores despite lower income?
* Which groups have similar shopping patterns?
* How should marketing resources be allocated?

A business should validate the usefulness of these groups before making important decisions based on them.

## 4. Dataset and Model

This project uses the `Mall_Customers.csv` dataset.

The selected features are:

* `Annual Income (k$)`
* `Spending Score (1-100)`

The data is standardized using `StandardScaler`, and K-Means is initially configured with five clusters.

## 5. Implementation in Python

### Step 1: Import Libraries and Prepare the Dataset

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

df = pd.read_csv("Mall_Customers.csv")

X = df[
    ["Annual Income (k$)", "Spending Score (1-100)"]
]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

print("Dataset loaded successfully!")
print("Number of customers:", len(df))
```

**Explanation:** The dataset is loaded, the two clustering features are selected, and the features are standardized before fitting K-Means.

### Step 2: Train K-Means with Five Clusters

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

df["Cluster"] = labels

print("K-Means clustering completed!")
print("Cluster counts:")
print(df["Cluster"].value_counts().sort_index())
```

The `Cluster` column stores the cluster assignment for each customer. Cluster counts indicate how many customers belong to each group.

### Step 3: Convert Centroids to the Original Scale

```python
centroids_orig = scaler.inverse_transform(
    centroids_scaled
)

centroid_df = pd.DataFrame(
    centroids_orig,
    columns=[
        "Annual Income (k$)",
        "Spending Score (1-100)"
    ]
)

centroid_df.index.name = "Cluster"

print("Cluster Centroids:")
print(centroid_df.round(2))
```

**Observation:** The centroid table helps us understand the typical annual income and spending score of each cluster.

### Step 4: Visualize the Final Clusters

```python
plt.figure(figsize=(10, 6.5))

sns.scatterplot(
    data=df,
    x="Annual Income (k$)",
    y="Spending Score (1-100)",
    hue="Cluster",
    palette="Set1",
    s=70,
    alpha=0.85
)

plt.scatter(
    centroids_orig[:, 0],
    centroids_orig[:, 1],
    color="black",
    marker="*",
    s=300,
    edgecolor="white",
    linewidth=1.5,
    label="Centroids"
)

plt.title("Mall Customer Segmentation (K = 5)")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.legend()
plt.tight_layout()
plt.show()
```

**Explanation:**

* Each point represents a customer.
* Each color represents a cluster.
* The black stars indicate the cluster centroids.
* The positions of the centroids summarize the average feature values of their respective clusters.

### Step 5: Calculate Average Characteristics of Each Cluster

```python
cluster_summary = df.groupby("Cluster").agg(
    Customer_Count=("CustomerID", "count"),
    Average_Income=("Annual Income (k$)", "mean"),
    Average_Spending_Score=("Spending Score (1-100)", "mean")
).round(2)

print("Customer Segment Summary:")
print(cluster_summary)
```

This summary provides a more systematic way to interpret the groups.

The average income and spending score should be examined together rather than using the cluster number alone to decide what the group represents.

### Step 6: Implement the Elbow Method

```python
inertias = []
k_values = range(1, 11)

for k in k_values:
    km = KMeans(
        n_clusters=k,
        init="k-means++",
        n_init=10,
        random_state=42
    )

    km.fit(X_scaled)
    inertias.append(km.inertia_)

plt.figure(figsize=(8.5, 5))

plt.plot(
    list(k_values),
    inertias,
    marker="o",
    linewidth=2
)

plt.axvline(
    5,
    linestyle="--",
    label="Reference: K = 5"
)

plt.title("Elbow Method for Finding the Number of Clusters")
plt.xlabel("Number of Clusters (K)")
plt.ylabel("Inertia (WCSS)")
plt.xticks(list(k_values))
plt.legend()
plt.tight_layout()
plt.show()
```

**Explanation:** The loop trains ten different models, starting with one cluster and increasing the cluster count to ten. Each model's inertia is recorded and displayed in the elbow plot.

### Step 7: Display Inertia Values

```python
inertia_results = pd.DataFrame({
    "Number of Clusters (K)": list(k_values),
    "Inertia (WCSS)": inertias
})

print(inertia_results.round(2).to_string(index=False))
```

The table shows how inertia changes as the number of clusters increases. It can be examined alongside the graph to help identify where the improvement begins to slow down.

### Step 8: Additional Evaluation Using the Silhouette Score

```python
from sklearn.metrics import silhouette_score

silhouette_results = []

for k in range(2, 11):
    km = KMeans(
        n_clusters=k,
        init="k-means++",
        n_init=10,
        random_state=42
    )

    cluster_labels = km.fit_predict(X_scaled)

    score = silhouette_score(
        X_scaled,
        cluster_labels
    )

    silhouette_results.append({
        "Number of Clusters (K)": k,
        "Silhouette Score": score
    })

silhouette_df = pd.DataFrame(silhouette_results)

print(silhouette_df.round(3).to_string(index=False))
```

**Explanation:** The silhouette score provides another perspective on clustering quality. Comparing it with the elbow plot can help assess whether the chosen cluster count is reasonable.

A high silhouette score can indicate well-separated clusters, but no single metric should replace examination of the actual customer segments and their usefulness.

## 6. Results and Observations

* K-Means assigns each customer to one of five clusters in the initial model.
* Centroids summarize the average income and spending score of each group.
* The cluster visualization helps identify patterns and possible separation between customer groups.
* The cluster summary provides numerical evidence for interpreting customer segments.
* Inertia decreases as the number of clusters increases.
* The Elbow Method identifies an approximate point where additional clusters provide smaller reductions in inertia.
* The silhouette score offers complementary information about cluster separation and cohesion.
* The final number of clusters should consider both numerical metrics and practical interpretability.

The original notebook highlights \(K=5\) as the reference elbow point. The actual plotted values should be inspected to assess how clearly the elbow appears.

## 7. Advantages of Customer Segmentation

1. Helps businesses understand customer behavior.
2. Supports more targeted marketing campaigns.
3. Helps identify groups with different spending patterns.
4. Can improve customer relationship management.
5. Helps organize large datasets into more understandable groups.
6. Supports data-driven business planning.

## 8. Limitations and Challenges

1. The selected features may not represent every aspect of customer behavior.
2. K-Means requires the number of clusters to be selected in advance.
3. Different initial centroids can produce different results.
4. Outliers may affect cluster centers.
5. Some customers may lie between two groups rather than fitting clearly into one.
6. Customer behavior can change over time, so segmentation may need to be updated.
7. Cluster membership does not automatically explain why a customer behaves in a particular way.
8. Marketing decisions should not rely on clusters without additional business validation.

## 9. Future Improvements

The project can be improved in several ways:

* Include more relevant customer features when appropriate.
* Compare K-Means with Hierarchical Clustering or DBSCAN.
* Evaluate different cluster counts using silhouette scores.
* Examine outliers before training the model.
* Test whether the segments remain stable across different samples.
* Use the cluster summaries to design and evaluate targeted marketing strategies.

## 10. Conclusion

In this practical, the results of K-Means clustering were visualized and interpreted using customer income and spending score. Centroids were converted back to their original scale to make the clusters easier to understand.

The Elbow Method was implemented by comparing inertia values for different cluster counts. Silhouette analysis was also introduced as an additional method for examining clustering quality.

The project demonstrates that unsupervised learning can uncover patterns in customer data. When combined with careful evaluation and business interpretation, customer segmentation can support more informed retail marketing decisions.
