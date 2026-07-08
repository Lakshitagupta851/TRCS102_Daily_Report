## DAY 13 OF TRAINING
# Python Foundations — Data Exploration with Pandas

Welcome to **Day 13 of the Industrial Training for AI & Machine Learning**!

In today's session, we learned how to read datasets and explore them using Pandas. We also studied different functions used to inspect, summarize, and select data efficiently before performing data analysis or training Machine Learning models.

---

# Learning Objectives

By the end of this session, you will be able to:

- Read CSV files using Pandas.
- Inspect datasets using built-in functions.
- Understand the structure of a DataFrame.
- Select rows and columns from a dataset.
- Perform basic data exploration.

---

# 1. Reading CSV Files

The `read_csv()` function is used to load a CSV (Comma Separated Values) file into a Pandas DataFrame.

## Example

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df)
```

### Output

```
   Name  Age  Marks
0  Aman   20     85
1  Riya   21     90
2  Karan  22     78
```

---

# 2. head()

The `head()` function displays the first five rows of a dataset by default. It helps us quickly preview the data.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.head())
```

### Output

```
   Name  Age  Marks
0  Aman   20     85
1  Riya   21     90
2  Karan 22     78
```

---

# 3. tail()

The `tail()` function displays the last five rows of a dataset.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.tail())
```

### Output

```
   Name  Age  Marks
0  Aman   20     85
1  Riya   21     90
2  Karan 22     78
```

---

# 4. info()

The `info()` function provides information about the DataFrame, including the number of rows, columns, data types, and missing values.

```python
import pandas as pd

df = pd.read_csv("students.csv")

df.info()
```

### Output

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries
Data columns: 3 columns
```

---

# 5. describe()

The `describe()` function generates statistical summaries for numerical columns such as count, mean, minimum, maximum, and standard deviation.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.describe())
```

### Output

```
            Age      Marks
count   3.000000   3.000000
mean   21.000000  84.333333
min    20.000000  78.000000
max    22.000000  90.000000
```

---

# 6. shape

The `shape` attribute returns the number of rows and columns in a DataFrame.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.shape)
```

### Output

```
(3, 3)
```

---

# 7. columns

The `columns` attribute returns the names of all columns in the DataFrame.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.columns)
```

### Output

```
Index(['Name', 'Age', 'Marks'], dtype='object')
```

---

# 8. dtypes

The `dtypes` attribute displays the data type of each column.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.dtypes)
```

### Output

```
Name     object
Age       int64
Marks     int64
dtype: object
```

---

# 9. Selecting Columns

A single column can be selected by using its column name.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df["Marks"])
```

### Output

```
0    85
1    90
2    78
Name: Marks, dtype: int64
```

---

# 10. Selecting Multiple Columns

Multiple columns can be selected by passing a list of column names.

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df[["Name", "Marks"]])
```

### Output

```
    Name  Marks
0   Aman     85
1   Riya     90
2  Karan     78
```

---

# Exercises

## Exercise 1: Display the First Five Rows

### Solution

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.head())
```

### Output

```
Displays the first five rows of the dataset.
```

---

## Exercise 2: Print the Shape of a DataFrame

### Solution

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df.shape)
```

### Output

```
(3, 3)
```

---

## Exercise 3: Display Student Marks

### Solution

```python
import pandas as pd

df = pd.read_csv("students.csv")

print(df["Marks"])
```

### Output

```
0    85
1    90
2    78
```

---

# Key Takeaways

- `read_csv()` is used to load datasets into Pandas.
- Functions like `head()`, `tail()`, `info()`, and `describe()` help inspect data.
- `shape`, `columns`, and `dtypes` provide information about the DataFrame.
- Columns can be selected easily for analysis.
- Pandas is an essential library for data preprocessing and Machine Learning.
