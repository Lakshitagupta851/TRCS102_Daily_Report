## DAY 7 OF TRAINING
# Python Foundations — Dictionaries and Sets

Welcome to **Day 7 of the Industrial Training for AI & Machine Learning**!

In today's session, we explored two important Python data structures: **Dictionaries** and **Sets**. Dictionaries store data in **key-value pairs**, making data retrieval efficient, whereas Sets store **unique unordered elements** and are useful for removing duplicates and performing mathematical set operations.

These data structures are widely used in Data Science and Machine Learning for storing structured data, handling categorical information, and performing fast lookups.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand Dictionaries and Sets in Python.
- Create and access dictionary elements.
- Perform common dictionary operations.
- Understand Set properties and operations.
- Apply dictionaries and sets in simple AI/ML examples.

---

# 1. Dictionaries

A **Dictionary** is a mutable data structure that stores data in the form of **key-value pairs**. Each key is unique and is used to access its corresponding value.

## Creating a Dictionary

```python
student = {
    "Name": "Lakshita",
    "Age": 20,
    "Branch": "CSE"
}

print(student)
```

### Output

```
{'Name': 'Lakshita', 'Age': 20, 'Branch': 'CSE'}
```

---

## Accessing Dictionary Elements

Dictionary values are accessed using their corresponding keys.

```python
student = {
    "Name": "Lakshita",
    "Age": 20
}

print(student["Name"])
print(student["Age"])
```

### Output

```
Lakshita
20
```

---

## Common Dictionary Methods

### 1. keys()

The `keys()` method returns all the keys present in a dictionary.

```python
student = {"Name":"Lakshita","Age":20}

print(student.keys())
```

### Output

```
dict_keys(['Name', 'Age'])
```

---

### 2. values()

The `values()` method returns all the values stored in the dictionary.

```python
student = {"Name":"Lakshita","Age":20}

print(student.values())
```

### Output

```
dict_values(['Lakshita', 20])
```

---

### 3. items()

The `items()` method returns all key-value pairs.

```python
student = {"Name":"Lakshita","Age":20}

print(student.items())
```

### Output

```
dict_items([('Name', 'Lakshita'), ('Age', 20)])
```

---

### 4. update()

The `update()` method adds new key-value pairs or updates existing ones.

```python
student = {"Name":"Lakshita"}

student.update({"Age":20})

print(student)
```

### Output

```
{'Name': 'Lakshita', 'Age': 20}
```

---

### 5. pop()

The `pop()` method removes the specified key from the dictionary.

```python
student = {"Name":"Lakshita","Age":20}

student.pop("Age")

print(student)
```

### Output

```
{'Name': 'Lakshita'}
```

---

# AI/ML Example using Dictionary

```python
prediction = {
    "Cat":0.15,
    "Dog":0.82,
    "Bird":0.03
}

print(max(prediction, key=prediction.get))
```

### Output

```
Dog
```

---

# 2. Sets

A **Set** is an unordered collection of unique elements. Duplicate values are automatically removed, making sets useful for storing distinct items.

## Creating a Set

```python
numbers = {10,20,30,20,40}

print(numbers)
```

### Output

```
{40, 10, 20, 30}
```

---

## Set Operations

### 1. add()

The `add()` method inserts a new element into a set.

```python
numbers = {10,20,30}

numbers.add(40)

print(numbers)
```

### Output

```
{40, 10, 20, 30}
```

---

### 2. remove()

The `remove()` method deletes a specified element from the set.

```python
numbers = {10,20,30}

numbers.remove(20)

print(numbers)
```

### Output

```
{10, 30}
```

---

### 3. union()

The `union()` method combines two sets.

```python
A = {1,2,3}
B = {3,4,5}

print(A.union(B))
```

### Output

```
{1,2,3,4,5}
```

---

### 4. intersection()

The `intersection()` method returns the common elements between two sets.

```python
A = {1,2,3}
B = {2,3,4}

print(A.intersection(B))
```

### Output

```
{2,3}
```

---

### 5. difference()

The `difference()` method returns the elements present in the first set but not in the second.

```python
A = {1,2,3}
B = {2,3,4}

print(A.difference(B))
```

### Output

```
{1}
```

---

# Difference Between Dictionary and Set

| Dictionary | Set |
|------------|-----|
| Stores key-value pairs | Stores unique values only |
| Uses `{key:value}` | Uses `{value}` |
| Mutable | Mutable |
| Access using keys | No indexing |

---

# Exercises

## Exercise 1: Print Student Details Using Dictionary

### Solution

```python
student = {
    "Name":"Lakshita",
    "Branch":"CSE",
    "Semester":5
}

for key,value in student.items():
    print(key,":",value)
```

### Output

```
Name : Lakshita
Branch : CSE
Semester : 5
```

---

## Exercise 2: Find Common Elements Between Two Sets

### Solution

```python
A = {10,20,30,40}
B = {30,40,50,60}

print(A.intersection(B))
```

### Output

```
{40,30}
```

---

## Exercise 3: Remove Duplicate Values from a List

### Solution

```python
numbers = [10,20,20,30,40,40,50]

unique = set(numbers)

print(unique)
```

### Output

```
{10,20,30,40,50}
```

---

# Key Takeaways

- Dictionaries store data as key-value pairs for efficient access.
- Sets store only unique elements and automatically remove duplicates.
- Dictionary methods simplify updating and retrieving data.
- Set operations such as union and intersection are useful for data analysis.
- Dictionaries and Sets are widely used in AI, Machine Learning, and Data Science.
