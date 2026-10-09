# DAY 18 OF TRAINING

## Bivariate Analysis and Correlation — Understanding House-Price Relationships

### Introduction

Bivariate analysis studies the relationship between two variables. In this practical, house prices are compared with living area, waterfront status, and property condition. A correlation heatmap is also used to summarize linear relationships among numeric features in the King County house-price dataset.

### Learning Objectives

* Compare living area with house price using a scatter plot.
* Examine price differences for waterfront and non-waterfront homes.
* Compare average prices across condition categories.
* Understand a correlation heatmap.
* Check missing values and save a filtered dataset.

### 1. Living Area vs. House Price

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(
    data=df, x='sqft_living', y='price', hue='waterfront'
)
plt.title("Living Area vs House Price")
plt.show()
``` 

**Observation:** Each point represents a property. The horizontal axis shows living area in square feet, while the vertical axis shows price. The plot generally indicates that larger living areas tend to be associated with higher prices, although prices vary considerably. The colors distinguish waterfront status.

### 2. Waterfront Status vs. Price

```python
plt.figure(figsize=(8, 5))
sns.boxplot(x='waterfront', y='price', data=df, hue='waterfront')
plt.xticks([0, 1], ['No waterfront', 'Waterfront'])
plt.title("Waterfront Status vs House Price")
plt.show()

```

**Graph:** 


<img width="762" height="485" alt="image" src="https://github.com/user-attachments/assets/795a1288-6a1c-4fd5-939a-4c2983b8dd84" />


**Observation:** A box plot compares the median, spread, and potential outliers in the prices of waterfront and non-waterfront properties. The analysis indicates that waterfront houses tend to be more expensive. However, the plot does not prove that waterfront status alone causes the price difference.

### 3. Condition vs. Average House Price

```python
plt.figure(figsize=(8, 5))
sns.barplot(x='condition', y='price', data=df, hue='condition')
plt.title("Condition vs Average House Price")
plt.show()
```

**Graph:** 
<img width="752" height="492" alt="image" src="https://github.com/user-attachments/assets/c1985155-c4bf-4430-903a-df1dcbaac3d4" />


**Observation:** The bar plot compares average house prices across property-condition categories. It helps explore differences in average selling prices. These differences may also be influenced by living area, location, waterfront status, and other features.

### 4. Correlation Analysis

```python
correlation_map = df.corr(numeric_only=True)

plt.figure(figsize=(10, 8))
sns.heatmap(
    correlation_map, annot=True, cmap='coolwarm',
    vmin=-1, vmax=1
)
plt.title("Correlation Heatmap")
plt.show()
```

**Graph:** 
<img width="820" height="712" alt="image" src="https://github.com/user-attachments/assets/79cedba5-1f72-45ca-ba51-ca2887517457" />


**How to Read the Heatmap**

* Correlation values range from **-1 to +1**.
* A value near **+1** indicates a strong positive linear relationship.
* A value near **-1** indicates a strong negative linear relationship.
* A value near **0** indicates a weak linear relationship.
* The diagonal contains values of 1 because each variable is perfectly correlated with itself.

**Observation:** In the notebook's analysis, living area (`sqft_living`) is one of the features most strongly correlated with price, with a correlation of approximately **+0.70**. Correlation indicates association, not causation.

### 5. Check Missing Values

```python
df.isnull().sum()
```

This displays the number of missing entries in each column and helps determine whether data cleaning is required.

### 6. Save a Filtered Dataset

```python
df_filtered = df[df['bedrooms'] <= 10]
df_filtered.to_csv('kc_house_filtered.csv', index=False)
```

This example removes records with more than 10 bedrooms from the saved working dataset. Such filtering should only be performed after inspecting unusual records and deciding that the rule is suitable for the analysis.

### Conclusion

Bivariate analysis helps reveal relationships that are difficult to understand from a table alone. The scatter plot examines living area and price, the box plot compares waterfront groups, the bar plot compares condition categories, and the heatmap summarizes correlations. These visualizations support data understanding and feature selection, while checking outliers and missing values improves data quality.
