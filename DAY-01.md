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

## 5. Mutability vs. Immutability

One of the most important concepts in Python is understanding mutable and immutable objects.
| Mutable Objects | Immutable Objects |
| --------------- | ----------------- |
| List            | Integer           |
| Dictionary      | Float             |
| Set             | String            |
|                 | Tuple             |
 ## Immutable Example (Integer)

When an integer changes, Python creates a new object.
```
a = 5
print(f"Value : {a}")
print(f"Address : {id(a)}")
a = a + 1
print(f"Value : {a}")
print(f"Address : {id(a)}")
```
## Output
```
Value : 5
Address : 140735280934984

Value : 6
Address : 140735280935016
```
## Mutable Example (List)

Lists are mutable, so they are modified without creating a new object.
```
numbers = [1,2,3]
print(numbers)
print(id(numbers))
numbers.append(4)
print(numbers)
print(id(numbers))
```
## Output
```
[1,2,3]
140735281652736

[1,2,3,4]
140735281652736
```

## 6. Sequence and Collection Types

Sequence and collection types are used to store multiple values in a single variable. Sequence types store elements in an ordered manner and support indexing and slicing, while collection types help organize and manage groups of related data efficiently. Common examples include String (str), List (list), Tuple (tuple), Set (set), and Dictionary (dict). These data types make data storage, access, and manipulation simple and efficient in Python.
```my_list = ["apple", "banana", "cherry", "apple"]
my_tuple = ("apple", "banana", "cherry", "apple")

new=list(my_tuple)
new.append("grapes")
my_tuple=tuple(new)
print(my_tuple)
```
## Output
```
('apple', 'banana', 'cherry', 'apple', 'grapes')
```
## 7. Type Casting and Conversion

Type casting (or type conversion) is the process of converting a value from one data type to another. Python provides built-in functions such as int(), float(), str(), and bool() for type conversion. It helps ensure data is in the required format for performing operations.
```
num = "25"

x = int(num)

print(x)
print(type(x))
```
## Output
```
25
<class 'int'>
```
## 8. Variable Naming Rules

Variable names in Python must follow certain rules to make the code valid and readable. A variable name must start with a letter or underscore (_), cannot begin with a number, cannot contain spaces or special characters (except _), and cannot use Python keywords. Variable names are also case-sensitive, meaning age and Age are treated as different variables.

## Examples

Valid:
```
student_name = "Lakshita"
_age = 20
marks1 = 95
```
Invalid:
```
1name = "Lakshita"    # Starts with a number
student-name = "ABC"  # Contains '-'
class = 10            # 'class' is a keyword
```
## 9. Knowledge Check & Coding Exercises
## Exercise 1: Identify the Identity
Predict the output of the following code, then write the code below it and execute it to verify.
```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)
print(a == c)
print(a is c)
```
## Solution
```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print("a is b:", a is b)
print("a == c:", a == c)
print("a is c:", a is c)
```
## Exercise 2: The Immutability Trap
What will happen when you try to run the following code? Run it and modify the code appropriately so that it returns a modified tuple.
```
fruits = ("apple", "pear", "cherry")

# Modify the second item to "banana"
```
## Solution
```
fruits = ("apple", "pear", "cherry")
# Convert to list, modify, and convert back
fruits_list = list(fruits)
fruits_list[1] = "banana"
fruits = tuple(fruits_list)
print("Modified tuple:", fruits)
```
## Exercise 3: Explicit Cast and Set Magic
Given a list of user roles, write a Python program to:
1.Print the total number of user accounts.
2.Print the list of unique roles in the system.
3.Count the total number of unique roles.
## Solution
```
roles = ["admin", "user", "user", "editor", "admin", "user", "viewer"]
# 1. Print total counts
print("Total user accounts:", len(roles))
# 2. Unique roles list/set
unique_roles = set(roles)
print("Unique roles in the system:", unique_roles)
# 3. Count unique roles
print("Count of unique roles:", len(unique_roles))
```
## Exercise 4: AI Hyperparameters Dictionary
Create a dictionary containing the following hyperparameters:
Learning Rate (LR): 0.001
Batch Size: 32
Optimizer: "Adam"
Epochs: 10
Early Stopping: True
Print each value using its corresponding key. Then update the learning rate to 0.005 and print the dictionary to verify the changes.
## Solution
```
hyperparameters = {
    "learning_rate": 0.001,
    "batch_size": 32,
    "optimizer": "Adam",
    "epochs": 10,
    "early_stopping": True
}

# Print specific keys
print("LR:", hyperparameters["learning_rate"])
print("Batch Size:", hyperparameters["batch_size"])
print("Optimizer:", hyperparameters["optimizer"])
print("Epochs:", hyperparameters["epochs"])
print("Early stopping:", hyperparameters["early_stopping"])

# Update learning rate in-place
hyperparameters["learning_rate"] = 0.005

print("\nUpdated dictionary:", hyperparameters)
```
