# TRCS102 - Daily Report

# Day 01 of Training

## Python Basics — Variables and Data Types

Welcome to the Industrial Training for AI & Machine Learning!

Today, we are starting with the absolute core foundation of Python programming. Understanding how Python handles variables and memory is essential, especially as we move into data manipulation, neural networks, and model training later on.

## Learning Objectives

By the end of this session, you will understand:

1. Variables: What they are and how Python handles them in memory (the "reference" model).
2. Data Types: The built-in data types in Python (`int`, `float`, `complex`, `str`, `list`, `tuple`, `dict`, `set`, `bool`, `None`).
3. Mutability vs. Immutability: Why this distinction is critical for data science.
4. Type Casting: How to convert between different data types.
5. Best Practices: Variable naming conventions in Python.

# 1. Variables:Pointers to Memory

In Python, a variable is not a container that stores data directly. Instead, it acts as a **reference (or pointer) to an object in memory**. When a value is assigned to a variable, Python creates the object in memory (if it doesn't already exist) and the variable points to that memory location. Multiple variables can even refer to the same object, making memory management efficient.
### Example

```python
x = 10
y = x

print(x)
print(y)

print(id(x))
print(id(y))
```

**Output (example):**
```
10
10
140719021838552
140719021838552
```

**Explanation:**  
Both `x` and `y` point to the same object in memory, so `id(x)` and `id(y)` are the same.
