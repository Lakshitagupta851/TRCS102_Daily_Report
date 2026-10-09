
# Day 19: Data Preprocessing — Missing Values and Outlier Handling

## 1. Introduction

Data preprocessing is an important step in machine learning. Raw datasets may contain missing values, unusual observations, inconsistent formats, or extreme values that can affect model performance. Preprocessing improves data quality and prepares the dataset for further analysis.

In this task, the King County House Sales dataset was inspected, missing values were checked, and outliers were handled using the Interquartile Range (IQR) method.

## 2. Objectives

- Inspect the dataset and check for missing values.
- Understand missing-value imputation.
- Identify outliers using boxplots.
- Apply IQR-based capping to numerical columns.
- Prepare the data for further machine learning tasks.

## 3. Missing Value Detection and Imputation

Missing values occur when information is unavailable for one or more observations. They can affect statistical analysis and may reduce the performance of machine learning models.

Missing values can be checked using:

```python
df.isnull().sum()
```

Common imputation methods include:

- **Mean Imputation:** Replaces missing values with the mean.
- **Median Imputation:** Replaces missing values with the median.
- **Mode Imputation:** Replaces missing values with the most frequent value.

Median imputation is often useful for numerical data containing extreme values because the median is less affected by outliers than the mean.

## 4. Understanding Outliers

Outliers are observations that differ considerably from most other values in a dataset. For example, a house with an exceptionally large living area or an unusually high price may be considered an outlier.

Outliers may represent genuine observations or data-entry errors. Therefore, they should be examined before deciding how to handle them.

## 5. Interquartile Range (IQR) Method

The Interquartile Range measures the spread of the middle 50% of the data.

**Formula:**

IQR = Q3 - Q1

Where:
- Q1 is the first quartile (25th percentile).
- Q3 is the third quartile (75th percentile).

The lower and upper boundaries are calculated as:

Lower Boundary = Q1 - 1.5 × IQR

Upper Boundary = Q3 + 1.5 × IQR

Values outside these boundaries are considered potential outliers.

In the notebook, a `find_caps()` function calculates the limits. Capping restricts extreme values to the calculated boundaries instead of deleting the corresponding observations.

## 6. IQR Method Illustration

![IQR method illustration](images/preprocessing_illustration.png)

**Observation:** The IQR method identifies potential outliers by examining values that lie outside the lower and upper boundaries.

## 7. Boxplot of Living Area

A boxplot represents the median, quartiles, spread, and potential outliers of numerical data.

<img width="1085" height="592" alt="image" src="https://github.com/user-attachments/assets/c55f0d0f-9801-4648-ac6e-ed5fc2cf6219" />



**Observation:** The boxplot shows points beyond the upper whisker, indicating unusually large living-area values. These observations can influence some machine learning algorithms, so the notebook applies IQR capping to the `sqft_living` column.

## 8. Outlier Capping

The notebook applies IQR-based capping to these numerical columns:

- `price`
- `sqft_living`
- `bedrooms`

The values outside the calculated boundaries are clipped to the lower or upper limit. This approach retains the observations while limiting the influence of extreme values.

<img width="1081" height="590" alt="image" src="https://github.com/user-attachments/assets/9c7cb897-5153-4918-883b-debb9905cb50" />


**Observation:** The graph displays the distribution of house prices after the capping step. The box represents the middle 50% of values, while the whiskers show the range represented by the boxplot.

## 9. Importance of Outlier Handling

Outlier handling is useful because:

1. Extreme values can influence statistical summaries.
2. Some machine learning algorithms are sensitive to large numerical values.
3. Capping can reduce the influence of extreme observations without deleting entire rows.
4. Proper handling can make the dataset more suitable for further analysis.

However, genuine extreme values should not automatically be removed because they may contain important information.

## 10. Conclusion

This task demonstrated missing-value inspection and outlier handling using the IQR method. Potential outliers were identified using boxplots, and capping was applied to selected numerical columns. These steps help prepare the housing dataset for subsequent machine learning tasks.
