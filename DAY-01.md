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

# 2. Sharing References

In Python, multiple variables can refer to the same object in memory. This is known as **sharing references**. Any changes made to a mutable object (such as a list or dictionary) through one variable are reflected when accessed through the other variable because both point to the same memory location.
```
a = [1, 2, 3]
b = a
print(a is b)   # True
```
## 3. Dynamic Typing

Python is a **dynamically typed** language, which means you do not need to declare the data type of a variable explicitly. The type is determined automatically based on the value assigned and can change during program execution.
```python
x = 10
print(type(x))

x = "Hello"
print(type(x))
```

**Output:**
```
<class 'int'>
<class 'str'>
```
# 4. Built-in Data Types

Data types define the kind of value a variable can store and determine the operations that can be performed on it. Python provides several built-in data types, such as **Numeric**, **String**, **List**, **Tuple**, **Set**, **Dictionary**, and **Boolean**. Among these, **Numeric** data types are used to represent numerical values in different forms.
## Numeric Types

Python provides three built-in numeric data types: **int**, **float**, and **complex**. These types are used to represent whole numbers, decimal numbers, and complex numbers, respectively.

### Example

```python
a = 10
b = 3.14
c = 2 + 3j

print(type(a))
print(type(b))
print(type(c))
```

**Output:**
```
<class 'int'>
<class 'float'>
<class 'complex'>
```

**Explanation:**  
- `int` represents whole numbers (e.g., `10`).
- `float` represents decimal numbers (e.g., `3.14`).
- `complex` represents numbers with real and imaginary parts (e.g., `2 + 3j`).
<class 'str'>

## Text/String Type

A **string (`str`)** is a sequence of characters used to store and manipulate textual data in Python. Strings can contain letters, numbers, symbols, and spaces, and they can be enclosed in **single (`' '`), double (`" "`), or triple (`''' '''` or `""" """`) quotes**. Since strings are **immutable**, their contents cannot be changed after creation.
```
python
name = "Lakshita"

print(name)
print(type(name))
```

**Output:**
```
Lakshita
<class 'str'>
```
## Boolean and None Types

Python provides the **Boolean (`bool`)** and **None (`NoneType`)** data types. A Boolean value represents one of two logical states: **`True`** or **`False`**, and is commonly used in comparisons and decision-making. The **`None`** value represents the absence of a value or a null object and is often used to initialize variables or indicate that no value is available.
```python
is_student = True
result = None

print(type(is_student))
print(type(result))
```

**Output:**
```
<class 'bool'>
<class 'NoneType'>
```
