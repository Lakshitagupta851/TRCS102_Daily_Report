## DAY 8 OF TRAINING
# Python Foundations — Introduction to NumPy

Welcome to **Day 8 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored **NumPy (Numerical Python)**, one of the most important libraries used in Data Science, Artificial Intelligence, and Machine Learning. NumPy provides powerful support for creating and manipulating multi-dimensional arrays and performing mathematical operations efficiently.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the importance of NumPy.
- Install and import the NumPy library.
- Create one-dimensional and multi-dimensional arrays.
- Learn different array creation functions.
- Understand array attributes such as shape, size, dimensions, and data type.

---

# What is NumPy?

**NumPy (Numerical Python)** is an open-source Python library used for numerical computing. It provides a powerful **N-dimensional array** object and several built-in functions that make mathematical computations faster and more efficient than Python lists.

### Installing and Importing NumPy

```python
pip install numpy
```

```python
import numpy as np
```

---

# Creating NumPy Arrays

NumPy arrays are created using the `array()` function. They can store multiple values of the same data type efficiently.

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

print(arr)
```

### Output

```
[10 20 30 40]
```

---

# Creating a Two-Dimensional Array

A two-dimensional array consists of rows and columns and is commonly used for storing tabular data.

```python
import numpy as np

matrix = np.array([[1,2,3],
                   [4,5,6]])

print(matrix)
```

### Output

```
[[1 2 3]
 [4 5 6]]
```

---

# Data Type (dtype)

Every NumPy array has a specific data type. The `dtype` attribute is used to identify the type of elements stored in the array.

```python
import numpy as np

arr = np.array([10,20,30])

print(arr.dtype)
```

### Output

```
int64
```

---

# NumPy Array Creation Functions

NumPy provides several built-in functions to create arrays quickly.

---

## 1. zeros()

The `zeros()` function creates an array in which every element is **0**.

```python
import numpy as np

arr = np.zeros((2,3))

print(arr)
```

### Output

```
[[0. 0. 0.]
 [0. 0. 0.]]
```

---

## 2. ones()

The `ones()` function creates an array where every element is **1**.

```python
import numpy as np

arr = np.ones((2,2))

print(arr)
```

### Output

```
[[1. 1.]
 [1. 1.]]
```

---

## 3. arange()

The `arange()` function creates an array containing values within a specified range.

```python
import numpy as np

arr = np.arange(1,11)

print(arr)
```

### Output

```
[ 1  2  3  4  5  6  7  8  9 10]
```

---

## 4. linspace()

The `linspace()` function generates evenly spaced numbers between a specified start and end value.

```python
import numpy as np

arr = np.linspace(0,10,5)

print(arr)
```

### Output

```
[ 0.   2.5  5.   7.5 10. ]
```

---

# Array Attributes

NumPy arrays provide several useful attributes for understanding their structure.

---

## 1. shape

The `shape` attribute returns the number of rows and columns in an array.

```python
import numpy as np

arr = np.array([[1,2],[3,4]])

print(arr.shape)
```

### Output

```
(2, 2)
```

---

## 2. ndim

The `ndim` attribute returns the number of dimensions of an array.

```python
import numpy as np

arr = np.array([[1,2],[3,4]])

print(arr.ndim)
```

### Output

```
2
```

---

## 3. size

The `size` attribute returns the total number of elements in the array.

```python
import numpy as np

arr = np.array([[1,2],[3,4]])

print(arr.size)
```

### Output

```
4
```

---

## 4. dtype

The `dtype` attribute returns the data type of array elements.

```python
import numpy as np

arr = np.array([10,20,30])

print(arr.dtype)
```

### Output

```
int64
```

---

# Summary of Array Creation Functions

| Function | Purpose |
|----------|---------|
| `array()` | Creates a NumPy array |
| `zeros()` | Creates an array filled with zeros |
| `ones()` | Creates an array filled with ones |
| `arange()` | Creates an array with values in a range |
| `linspace()` | Creates evenly spaced values |

---

# Exercises

## Exercise 1: Create a NumPy Array

### Solution

```python
import numpy as np

arr = np.array([5,10,15,20])

print(arr)
```

### Output

```
[ 5 10 15 20]
```

---

## Exercise 2: Create a 3×3 Array of Ones

### Solution

```python
import numpy as np

arr = np.ones((3,3))

print(arr)
```

### Output

```
[[1. 1. 1.]
 [1. 1. 1.]
 [1. 1. 1.]]
```

---

## Exercise 3: Print Array Shape and Size

### Solution

```python
import numpy as np

arr = np.array([[10,20,30],
                [40,50,60]])

print("Shape:", arr.shape)
print("Size:", arr.size)
```

### Output

```
Shape: (2, 3)
Size: 6
```

---

# Key Takeaways

- NumPy is a powerful library for numerical computing.
- Arrays are faster and more efficient than Python lists.
- NumPy provides built-in functions to create arrays quickly.
- Array attributes help understand the structure of data.
- NumPy forms the foundation of Data Science, AI, and Machine Learning.
