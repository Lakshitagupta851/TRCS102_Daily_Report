## DAY 4 OF TRAINING
# Python Foundations — Functions and Modular Programming

Welcome to **Day 4 of the Industrial Training for AI & Machine Learning**!

After learning Python basics, operators, and control flow, today's session introduces one of the most important concepts in programming—**Functions**. Functions help us organize code into reusable blocks, making programs easier to read, maintain, and debug.

We also explored Python's built-in functions that simplify common tasks such as finding the length of a list, calculating sums, rounding numbers, and more. These functions are frequently used in AI, Data Science, and Machine Learning applications.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the importance of functions in Python.
- Use Python's built-in functions effectively.
- Create your own custom functions.
- Pass values using parameters and arguments.
- Improve code readability through modular programming.

---

# 1. Built-in (Inbuilt) Functions

Python provides many built-in functions that are already available for use. These functions perform common operations without requiring us to write extra code. They help developers save time and make programs more efficient.

Some commonly used built-in functions are:

---
## 1. len()

The `len()` function returns the total number of elements present in a sequence such as a string, list, tuple, dictionary, or set. It is commonly used to determine the size of a collection.

```python
fruits = ["Apple", "Banana", "Mango", "Orange"]

print("Length of the list:", len(fruits))
```

### Output

```
Length of the list: 4
```

---

## 2. sum()

The `sum()` function calculates the sum of all numeric elements in an iterable like a list or tuple. It is useful for finding totals without using loops.

```python
marks = [85, 90, 78, 92]

print("Total Marks:", sum(marks))
```

### Output

```
Total Marks: 345
```

---

## 3. max()

The `max()` function returns the largest value from a sequence or from multiple values passed as arguments. It is useful for finding the highest number in a collection.

```python
numbers = [25, 48, 12, 90, 36]

print("Maximum Number:", max(numbers))
```

### Output

```
Maximum Number: 90
```

---

## 4. min()

The `min()` function returns the smallest value from a sequence or collection of values. It is commonly used to identify the minimum value in a dataset.

```python
numbers = [25, 48, 12, 90, 36]

print("Minimum Number:", min(numbers))
```

### Output

```
Minimum Number: 12
```

---

## 5. abs()

The `abs()` function returns the absolute (positive) value of a number. If the number is already positive, it returns the same value.

```python
number = -45

print("Absolute Value:", abs(number))
```

### Output

```
Absolute Value: 45
```

---

## 6. round()

The `round()` function rounds a floating-point number to the nearest integer or to a specified number of decimal places.

```python
value = 12.56789

print("Rounded Value:", round(value, 2))
```

### Output

```
Rounded Value: 12.57
```

---

## 7. print()

The `print()` function is used to display output on the screen. It is one of the most frequently used functions in Python for displaying results and debugging programs.

```python
name = "Lakshita"
course = "AI & Machine Learning"

print("Name:", name)
print("Course:", course)
```

### Output

```
Name: Lakshita
Course: AI & Machine Learning
```

---

| Function | Purpose |
|----------|---------|
| `len()` | Returns the number of elements in a sequence. |
| `sum()` | Calculates the total of numeric values. |
| `max()` | Returns the largest value. |
| `min()` | Returns the smallest value. |
| `abs()` | Returns the absolute value of a number. |
| `round()` | Rounds a number to the specified decimal places. |
| `print()` | Displays output on the screen. |
## Example 1: Using Built-in Functions

```python
numbers = [10, 20, 30, 40, 50]

print("Length:", len(numbers))
print("Maximum:", max(numbers))
print("Minimum:", min(numbers))
print("Sum:", sum(numbers))
```

## Output

```
Length: 5
Maximum: 50
Minimum: 10
Sum: 150
```

---

## Example 2: round() Function

The `round()` function rounds a floating-point number to the specified number of decimal places.

```python
num = 34.3625463

print(round(num, 3))
```

## Output

```
34.363
```

---

## Example 3: abs() Function

The `abs()` function returns the absolute (positive) value of a number.

```python
num = -15

print(abs(num))
```

## Output

```
15
```

---

# Practical Example

The following example demonstrates how built-in functions can be used together.

```python
password = "abc@123"
marks = [78, 82, 95, 88]

print("Password Length:", len(password))
print("Total Marks:", sum(marks))
print("Highest Marks:", max(marks))
print("Lowest Marks:", min(marks))
```

## Output

```
Password Length: 7
Total Marks: 343
Highest Marks: 95
Lowest Marks: 78
```

---

# 2. Creating Custom Functions

Although built-in functions are useful, we often need to write our own functions to solve specific problems. A custom function is created using the `def` keyword.

### Syntax

```python
def function_name():
    # code
```

---

## Example

```python
def welcome_student():
    print("Welcome to AI/ML Industrial Training!")
    print("Let's build some functions today!")

welcome_student()
```

## Output

```
Welcome to AI/ML Industrial Training!
Let's build some functions today!
```

---

# 3. Parameters and Arguments

Functions become more flexible when values are passed to them. The variables inside the function definition are called **parameters**, while the actual values passed during the function call are called **arguments**.

## Example

```python
def greet_user(name, course):
    print(f"Hello {name}")
    print(f"Welcome to {course}")

greet_user("Lakshita", "AI & Machine Learning")
```

## Output

```
Hello Lakshita
Welcome to AI & Machine Learning
```

---

# Exercise 1

Create a function that adds two numbers.

## Solution

```python
def add_numbers(a, b):
    print("Sum =", a + b)

add_numbers(10, 30)
```

## Output

```
Sum = 40
```

---

# Key Takeaways

- Functions help reduce code repetition.
- Built-in functions make programming faster and easier.
- Custom functions allow developers to write reusable code.
- Parameters and arguments make functions flexible.
- Modular programming improves readability and maintenance of programs.
