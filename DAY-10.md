## DAY 10 OF TRAINING
# Python Foundations — NumPy Arrays and Vectorization

Welcome to **Day 10 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored the fundamentals of **NumPy Arrays** and understood why NumPy is preferred over Python lists for numerical computing. We also learned about vectorization and how NumPy performs mathematical operations efficiently.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the advantages of NumPy.
- Create one-dimensional and two-dimensional arrays.
- Compare Python Lists and NumPy Arrays.
- Understand Vectorization.
- Perform mathematical operations on arrays efficiently.

---

# 1. Why NumPy?

NumPy (Numerical Python) is a powerful library used for numerical computations. It provides faster execution, lower memory usage, and supports multi-dimensional arrays, making it ideal for Data Science and Machine Learning.

### Advantages of NumPy

- Faster than Python Lists.
- Uses less memory.
- Supports vectorized operations.
- Easy to perform mathematical computations.
- Widely used in AI and Machine Learning.

---

# 2. Creating a One-Dimensional Array

A one-dimensional array stores elements in a single row.

```python
import numpy as np

arr = np.array([10,20,30,40,50])

print(arr)
```

### Output

```
[10 20 30 40 50]
```

---

# 3. Creating a Two-Dimensional Array

A two-dimensional array consists of rows and columns.

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

# 4. Python List vs NumPy Array

Although both can store collections of data, NumPy arrays are optimized for numerical computations.

| Python List | NumPy Array |
|-------------|-------------|
| Slower | Faster |
| More memory | Less memory |
| Limited mathematical operations | Supports vectorized operations |
| General-purpose | Numerical computing |

---

# 5. Vectorization

Vectorization means performing operations on an entire array without using loops. This makes the code shorter and much faster.

```python
import numpy as np

arr = np.array([1,2,3,4])

print(arr * 5)
```

### Output

```
[ 5 10 15 20]
```

---

# 6. Arithmetic Operations on Arrays

NumPy allows element-wise mathematical operations.

```python
import numpy as np

a = np.array([1,2,3])
b = np.array([4,5,6])

print(a + b)
print(a * b)
```

### Output

```
[5 7 9]
[ 4 10 18]
```

---

# 7. Speed Comparison

NumPy performs calculations much faster than Python lists because operations are implemented in optimized C code.

```python
import numpy as np

a = np.array([10,20,30])

print(a + 10)
```

### Output

```
[20 30 40]
```

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

## Exercise 2: Multiply Every Element by 2

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

## Exercise 3: Add Two Arrays

### Solution

```python
import numpy as np

a = np.array([10,20,30])
b = np.array([1,2,3])

print(a + b)
```

### Output

```
[11 22 33]
```

---

# Key Takeaways

- NumPy provides fast and efficient numerical computations.
- Arrays consume less memory than Python lists.
- Vectorization performs operations without loops.
- NumPy arrays support fast mathematical operations.
- NumPy is a core library in Data Science and Machine Learning.
