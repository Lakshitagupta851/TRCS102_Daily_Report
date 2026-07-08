## DAY 12 OF TRAINING
# Python Foundations — Introduction to Pandas

Welcome to **Day 12 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored **Pandas**, one of the most popular Python libraries used for data analysis and manipulation. Pandas provides powerful data structures such as **Series** and **DataFrame**, making it easier to organize, analyze, and process large datasets.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the importance of Pandas.
- Install and import the Pandas library.
- Create and use Pandas Series.
- Create and manipulate DataFrames.
- Differentiate between Series and DataFrame.

---

# 1. What is Pandas?

**Pandas** is an open-source Python library used for data analysis and manipulation. It provides fast, flexible, and efficient data structures for handling structured data. Pandas is widely used in Data Science, Machine Learning, and Artificial Intelligence.

### Installing and Importing Pandas

```python
pip install pandas
```

```python
import pandas as pd
```

---

# 2. Pandas Series

A **Series** is a one-dimensional labeled array capable of storing different types of data such as integers, strings, and floating-point numbers. Each element in a Series has an associated index.

## Creating a Series

```python
import pandas as pd

marks = pd.Series([85, 90, 78, 95])

print(marks)
```

### Output

```
0    85
1    90
2    78
3    95
dtype: int64
```

---

## Accessing Elements of a Series

Series elements can be accessed using their index values.

```python
import pandas as pd

marks = pd.Series([85, 90, 78, 95])

print(marks[1])
```

### Output

```
90
```

---

# 3. Pandas DataFrame

A **DataFrame** is a two-dimensional data structure consisting of rows and columns. It is similar to a table or spreadsheet and is the most commonly used data structure in Pandas.

## Creating a DataFrame

```python
import pandas as pd

data = {
    "Name": ["Aman", "Riya", "Karan"],
    "Age": [21, 20, 22]
}

df = pd.DataFrame(data)

print(df)
```

### Output

```
    Name  Age
0   Aman   21
1   Riya   20
2  Karan   22
```

---

## Accessing a Column

A specific column can be accessed using its column name.

```python
import pandas as pd

data = {
    "Name": ["Aman", "Riya", "Karan"],
    "Age": [21, 20, 22]
}

df = pd.DataFrame(data)

print(df["Name"])
```

### Output

```
0     Aman
1     Riya
2    Karan
Name: Name, dtype: object
```

---

# Difference Between Series and DataFrame

| Series | DataFrame |
|--------|-----------|
| One-dimensional | Two-dimensional |
| Stores a single column of data | Stores multiple columns |
| Has one index | Has rows and columns |
| Created using `pd.Series()` | Created using `pd.DataFrame()` |

---

# AI/ML Example

Pandas DataFrames are commonly used to store datasets before training Machine Learning models.

```python
import pandas as pd

students = {
    "Marks": [80, 90, 75],
    "Result": ["Pass", "Pass", "Pass"]
}

df = pd.DataFrame(students)

print(df)
```

### Output

```
   Marks Result
0     80   Pass
1     90   Pass
2     75   Pass
```

---

# Exercises

## Exercise 1: Create a Pandas Series

### Solution

```python
import pandas as pd

numbers = pd.Series([10, 20, 30, 40])

print(numbers)
```

### Output

```
0    10
1    20
2    30
3    40
dtype: int64
```

---

## Exercise 2: Create a Student DataFrame

### Solution

```python
import pandas as pd

student = {
    "Name": ["Rahul", "Priya"],
    "Marks": [88, 92]
}

df = pd.DataFrame(student)

print(df)
```

### Output

```
    Name  Marks
0  Rahul     88
1  Priya     92
```

---

## Exercise 3: Print a Single Column

### Solution

```python
import pandas as pd

data = {
    "City": ["Delhi", "Mumbai", "Jaipur"],
    "Temperature": [35, 32, 38]
}

df = pd.DataFrame(data)

print(df["City"])
```

### Output

```
0     Delhi
1    Mumbai
2    Jaipur
Name: City, dtype: object
```

---

# Key Takeaways

- Pandas is a powerful library for data manipulation and analysis.
- A Series is a one-dimensional labeled array.
- A DataFrame is a two-dimensional table of data.
- Pandas simplifies handling structured datasets.
- Pandas is widely used in Data Science, AI, and Machine Learning.
