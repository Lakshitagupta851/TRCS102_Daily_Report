
# Day 20: Feature Scaling and Categorical Encoding

## 1. Introduction

After handling missing values and outliers, data often needs to be transformed into a suitable format for machine learning. Numerical features may have different ranges, while categorical information may be stored as text.

This task covers feature scaling, one-hot encoding, feature selection, and saving the preprocessed dataset using the King County House Sales data.

## 2. Objectives

- Understand the importance of feature scaling.
- Apply Min-Max scaling and Standard scaling.
- Convert categorical data into numerical columns.
- Select relevant features for the final dataset.
- Save the preprocessed data into a CSV file.

## 3. Feature Scaling

Feature scaling transforms numerical features to a comparable scale. For example, living area may contain values in the thousands, whereas the number of bedrooms may be a small single-digit number.

Without appropriate scaling, some algorithms may be influenced disproportionately by features with larger numerical ranges.

### A. Min-Max Scaling

Min-Max scaling transforms values into a specified range, usually between 0 and 1.

**Formula:**

X_scaled = (X - X_min) / (X_max - X_min)

Where:
- X is the original value.
- X_min is the minimum value.
- X_max is the maximum value.

In the notebook, `MinMaxScaler` is used to scale `sqft_living` into a new column named `Scaled_size`.

### B. Standard Scaling

Standard scaling transforms values so that the resulting feature has a mean close to 0 and a standard deviation close to 1.

**Formula:**

Z = (X - μ) / σ

Where:
- X is the original value.
- μ is the mean.
- σ is the standard deviation.

The notebook uses `StandardScaler` on `yr_built` and stores the result in `Year_Scaled`.

### Difference Between the Two Methods

- **Min-Max Scaling:** Usually transforms values into the range 0 to 1.
- **Standard Scaling:** Centers values around zero and scales them according to their standard deviation. Values are not restricted to a fixed range.

## 4. Distribution of House Prices

A histogram shows how frequently values occur within different numerical intervals. It is useful for understanding the shape and spread of a numerical variable.

![House price distribution histogram](images/cell13_graph.png)

**Observation:** The distribution is generally right-skewed, with many houses concentrated in the lower-to-middle price ranges and fewer houses at higher prices. Examining this distribution helps identify patterns and potential extreme values before model training.

## 5. One-Hot Encoding

Machine learning algorithms generally require numerical input. One-hot encoding converts categorical values into separate columns containing binary indicators.

For example:

| Neighborhood | Loc_Budget | Loc_Mid-Range | Loc_Premium |
|---|---:|---:|---:|
| Budget | 1 | 0 | 0 |
| Mid-Range | 0 | 1 | 0 |
| Premium | 0 | 0 | 1 |

The notebook uses `pd.get_dummies()` to convert the illustrative `Neighborhood` category into indicator columns.

**Note:** These neighborhood categories are randomly generated for demonstration in the notebook; they are not actual neighborhood classifications from the original housing dataset.

## 6. Feature Selection

Feature selection involves choosing the columns that will be retained for further analysis or model training.

The notebook selects the following columns for the final dataset:

- `price`
- `bedrooms`
- `bathrooms`
- `Scaled_size`
- `floors`
- `waterfront`
- `sqft_living`
- `condition`
- `Loc_Budget`
- `Loc_Mid-Range`
- `Loc_Premium`

Selecting relevant columns helps organize the dataset and prepare it for the next stage of the machine learning workflow.

## 7. Saving the Preprocessed Dataset

The selected data is saved as a CSV file named:

`kc_house_preprocessed.csv`

Saving the preprocessed data makes it easier to load the dataset later for model training, testing, and evaluation without repeating every preprocessing step.

## 8. Importance of Data Preprocessing

Data preprocessing is important because:

1. Scaling helps make numerical features comparable.
2. Encoding converts categorical information into a numerical representation.
3. Feature selection keeps the required columns for analysis.
4. Saving the final dataset supports reuse in later stages of the project.

Scaling and encoding should be performed appropriately for the selected machine learning algorithm. For reliable model evaluation, scaling parameters should be learned from the training data and then applied to the test data.

## 9. Conclusion

This task demonstrated Min-Max scaling, Standard scaling, one-hot encoding, feature selection, and saving the final dataset. These techniques transform data into a more suitable format for machine learning and prepare it for subsequent model development.
