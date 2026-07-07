## DAY 5 OF TRAINING
# Python Foundations — Data Structures (Lists & Tuples)

Welcome to **Day 5 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored Python's **Data Structures**, focusing on **Lists** and **Tuples**. These data structures are widely used for storing, organizing, and manipulating data efficiently. In AI and Machine Learning, they are commonly used for handling datasets, storing model outputs, and performing data preprocessing tasks.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand Python Lists and Tuples.
- Perform common operations on Lists.
- Access elements using indexing and slicing.
- Use built-in List methods.
- Understand the concept of immutable Tuples.
- Differentiate between Lists and Tuples.

---

# 1. Lists

A **List** is an ordered and mutable collection of elements. Lists can store different data types and allow duplicate values. Since they are mutable, elements can be added, removed, or modified after creation.

## Creating a List

```python
fruits = ["Apple", "Banana", "Mango", "Orange"]

print(fruits)
```

### Output

```
['Apple', 'Banana', 'Mango', 'Orange']
```

---

## Accessing List Elements

Elements in a list are accessed using **index numbers** starting from `0`.

```python
fruits = ["Apple", "Banana", "Mango"]

print(fruits[0])
print(fruits[2])
```

### Output

```
Apple
Mango
```

---

## List Slicing

Slicing allows us to retrieve a portion of a list.

```python
numbers = [10,20,30,40,50]

print(numbers[1:4])
```

### Output

```
[20, 30, 40]
```

---

## Common List Methods

Python provides several useful methods for manipulating lists.

```python
numbers = [5, 2, 8]

numbers.append(10)
numbers.sort()

print(numbers)
```

### Output

```
[2, 5, 8, 10]
```

Some commonly used list methods are:

| Method | Purpose |
|---------|---------|
| append() | Adds an element |
| insert() | Inserts an element at a position |
| remove() | Removes an element |
| pop() | Removes element by index |
| sort() | Sorts the list |
| reverse() | Reverses the list |

---

## AI/ML Example using Lists

Lists are commonly used to store model predictions or datasets.

```python
predictions = [0.92, 0.87, 0.95, 0.89]

print("Highest Prediction:", max(predictions))
print("Average Prediction:", sum(predictions)/len(predictions))
```

### Output

```
Highest Prediction: 0.95
Average Prediction: 0.9075
```

---

# 2. Tuples

A **Tuple** is an ordered but **immutable** collection of elements. Once created, its values cannot be modified. Tuples are useful for storing fixed data that should remain unchanged.

## Creating a Tuple

```python
student = ("Lakshita", 20, "CSE")

print(student)
```

### Output

```
('Lakshita', 20, 'CSE')
```

---

## Accessing Tuple Elements

Tuple elements are accessed using indexing, just like lists.

```python
student = ("Lakshita", 20, "CSE")

print(student[0])
print(student[2])
```

### Output

```
Lakshita
CSE
```

---

## Tuple Methods

Tuples provide only two built-in methods because they are immutable.

```python
numbers = (10,20,30,20)

print(numbers.count(20))
print(numbers.index(30))
```

### Output

```
2
2
```

---

## Difference Between List and Tuple

| List | Tuple |
|------|-------|
| Mutable | Immutable |
| Uses `[]` | Uses `()` |
| More methods | Limited methods |
| Slower | Faster |
| Suitable for changing data | Suitable for fixed data |

---

# Exercises

## Exercise 1: Find the Largest Number in a List

### Solution

```python
numbers = [15, 48, 22, 91, 36]

print("Largest Number:", max(numbers))
```

### Output

```
Largest Number: 91
```

---

## Exercise 2: Slice a List

### Solution

```python
numbers = [10,20,30,40,50,60]

print(numbers[2:5])
```

### Output

```
[30, 40, 50]
```

---

## Exercise 3: Count an Element in a Tuple

### Solution

```python
colors = ("Red", "Blue", "Green", "Blue")

print(colors.count("Blue"))
```

### Output

```
2
```

---

## Key Takeaways

- Lists are mutable and suitable for dynamic data.
- Tuples are immutable and ideal for fixed information.
- Indexing and slicing make data access efficient.
- Lists provide many built-in methods for data manipulation.
- Lists and Tuples are widely used in AI and Machine Learning for handling datasets.
