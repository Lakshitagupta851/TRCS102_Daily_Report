## DAY 11 OF TRAINING
# Python Foundations — Advanced NumPy Operations

Welcome to **Day 11 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored advanced NumPy operations such as **indexing, slicing, boolean masking, statistical functions, broadcasting, and data normalization**. These operations are essential for data preprocessing and analysis in Artificial Intelligence and Machine Learning.

---

# Learning Objectives

By the end of this session, you will be able to:

- Access array elements using indexing and slicing.
- Filter data using Boolean Masking.
- Apply statistical functions on arrays.
- Understand Broadcasting in NumPy.
- Normalize numerical data using NumPy.

---

# 1. Array Indexing

Indexing is used to access individual elements of a NumPy array. Indexing starts from **0**, similar to Python lists.

## Example

```python
import numpy as np

arr = np.array([10,20,30,40,50])

print(arr[3])
```

### Output

```
40
```

---

# 2. Array Slicing

Slicing allows us to extract a specific portion of an array.

## Example

```python
import numpy as np

arr = np.array([10,20,30,40,50,60])

print(arr[2:5])
```

### Output

```
[30 40 50]
```

---

# 3. Boolean Masking

Boolean Masking is used to filter elements based on a condition. It returns only those elements that satisfy the specified condition.

## Example

```python
import numpy as np

arr = np.array([12,25,18,40,7])

print(arr[arr > 20])
```

### Output

```
[25 40]
```

---

# 4. np.where()

The `np.where()` function checks a condition and returns values based on whether the condition is **True** or **False**.

## Example

```python
import numpy as np

arr = np.array([10,25,35,18])

result = np.where(arr > 20, "High", "Low")

print(result)
```

### Output

```
['Low' 'High' 'High' 'Low']
```

---

# 5. Statistical Functions

NumPy provides built-in statistical functions that simplify data analysis.

## mean()

The `mean()` function returns the average value of an array.

```python
import numpy as np

marks = np.array([70,80,90,100])

print(np.mean(marks))
```

### Output

```
85.0
```

---

## max()

The `max()` function returns the largest element in an array.

```python
import numpy as np

marks = np.array([70,80,90,100])

print(np.max(marks))
```

### Output

```
100
```

---

## min()

The `min()` function returns the smallest element in an array.

```python
import numpy as np

marks = np.array([70,80,90,100])

print(np.min(marks))
```

### Output

```
70
```

---

## sum()

The `sum()` function calculates the total of all elements in an array.

```python
import numpy as np

marks = np.array([70,80,90])

print(np.sum(marks))
```

### Output

```
240
```

---

# 6. Broadcasting

Broadcasting allows NumPy to perform arithmetic operations between arrays of different shapes without writing loops.

## Example

```python
import numpy as np

arr = np.array([2,4,6,8])

print(arr + 5)
```

### Output

```
[ 7  9 11 13]
```

---

# 7. Data Normalization

Normalization scales data to a common range. It is an important preprocessing step in Machine Learning.

## Example

```python
import numpy as np

marks = np.array([70,80,90])

normalized = marks / 100

print(normalized)
```

### Output

```
[0.7 0.8 0.9]
```

---

# Exercises

## Exercise 1: Print Elements Greater Than 50

### Solution

```python
import numpy as np

arr = np.array([25,60,45,80,95])

print(arr[arr > 50])
```

### Output

```
[60 80 95]
```

---

## Exercise 2: Find the Mean of an Array

### Solution

```python
import numpy as np

numbers = np.array([10,20,30,40])

print(np.mean(numbers))
```

### Output

```
25.0
```

---

## Exercise 3: Add 10 to Every Element Using Broadcasting

### Solution

```python
import numpy as np

arr = np.array([5,10,15])

print(arr + 10)
```

### Output

```
[15 20 25]
```

---

## Exercise 4: Find Maximum and Minimum Values

### Solution

```python
import numpy as np

numbers = np.array([25,60,45,80,95])

print("Maximum:", np.max(numbers))
print("Minimum:", np.min(numbers))
```

### Output

```
Maximum: 95
Minimum: 25
```

---

# Key Takeaways

- Indexing and slicing provide efficient access to array elements.
- Boolean masking helps filter data based on conditions.
- NumPy offers powerful statistical functions for data analysis.
- Broadcasting performs arithmetic operations without explicit loops.
- Data normalization prepares numerical data for Machine Learning models.
