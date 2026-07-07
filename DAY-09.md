## DAY 9 OF TRAINING
# Python Foundations — NumPy Array Operations

Welcome to **Day 9 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored advanced NumPy concepts such as **array indexing, slicing, views, copies, broadcasting, and vectorization**. These operations make NumPy one of the fastest and most efficient libraries for numerical computing and are widely used in Data Science and Machine Learning.

---

# Learning Objectives

By the end of this session, you will be able to:

- Access array elements using indexing.
- Extract portions of arrays using slicing.
- Understand the difference between Views and Copies.
- Learn the concept of Broadcasting.
- Perform fast mathematical operations using Vectorization.

---

# 1. Array Indexing

Indexing is used to access individual elements of a NumPy array. The index starts from **0**, just like Python lists.

## Example

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

print(arr[2])
```

### Output

```
30
```

---

# 2. Array Slicing

Slicing allows us to extract a portion of an array using the syntax `start:end`.

## Example

```python
import numpy as np

arr = np.array([10,20,30,40,50,60])

print(arr[1:5])
```

### Output

```
[20 30 40 50]
```

---

# 3. Two-Dimensional Indexing

Elements of a 2D array are accessed using **row and column indices**.

## Example

```python
import numpy as np

arr = np.array([[1,2,3],
                [4,5,6]])

print(arr[1,2])
```

### Output

```
6
```

---

# 4. Views

A **View** shares memory with the original array. Changes made in the view are reflected in the original array.

## Example

```python
import numpy as np

arr = np.array([10,20,30])

view = arr.view()

view[0] = 100

print(arr)
```

### Output

```
[100  20  30]
```

---

# 5. Copies

A **Copy** creates a completely separate array. Changes made in the copied array do not affect the original array.

## Example

```python
import numpy as np

arr = np.array([10,20,30])

copy = arr.copy()

copy[0] = 100

print(arr)
print(copy)
```

### Output

```
[10 20 30]
[100 20 30]
```

---

# Difference Between View and Copy

| View | Copy |
|------|------|
| Shares original memory | Creates new memory |
| Changes affect original array | Changes do not affect original array |
| Faster | Slightly slower |

---

# 6. Broadcasting

Broadcasting allows NumPy to perform operations on arrays of different shapes without writing loops.

## Example

```python
import numpy as np

arr = np.array([10,20,30])

print(arr + 5)
```

### Output

```
[15 25 35]
```

---

# 7. Vectorization

Vectorization allows mathematical operations to be performed on entire arrays without using loops. This makes NumPy programs faster and more efficient.

## Example

```python
import numpy as np

a = np.array([1,2,3])

b = np.array([4,5,6])

print(a + b)
```

### Output

```
[5 7 9]
```

---

# AI/ML Example

NumPy can quickly normalize numerical data before training a Machine Learning model.

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

## Exercise 1: Access the Last Element of an Array

### Solution

```python
import numpy as np

arr = np.array([5,10,15,20])

print(arr[-1])
```

### Output

```
20
```

---

## Exercise 2: Slice an Array

### Solution

```python
import numpy as np

arr = np.array([10,20,30,40,50])

print(arr[2:])
```

### Output

```
[30 40 50]
```

---

## Exercise 3: Demonstrate Broadcasting

### Solution

```python
import numpy as np

arr = np.array([2,4,6])

print(arr * 2)
```

### Output

```
[ 4  8 12]
```

---

## Exercise 4: Add Two Arrays Using Vectorization

### Solution

```python
import numpy as np

a = np.array([1,2,3])

b = np.array([4,5,6])

print(a + b)
```

### Output

```
[5 7 9]
```

---

# Key Takeaways

- Indexing and slicing provide quick access to array elements.
- Views share memory with the original array, whereas copies create independent arrays.
- Broadcasting performs operations on arrays of different shapes efficiently.
- Vectorization eliminates loops and improves performance.
- NumPy is an essential library for numerical computing, Data Science, and Machine Learning.
