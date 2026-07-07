## DAY 5 OF TRAINING
# Python Foundations — Functions and Modular Programming

Welcome to **Day 5 of the Industrial Training for AI & Machine Learning**!

In the previous session, we learned about Python functions, built-in functions, and how to create custom functions. In today's session, we will explore more advanced concepts of functions such as the **return statement, different types of arguments, variable scope, and recursive functions**.

These concepts help in writing modular, reusable, and efficient programs, making Python code easier to understand and maintain.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the purpose of the `return` statement.
- Differentiate between various types of function arguments.
- Understand Local and Global scope.
- Learn how recursive functions work.
- Write Python programs using recursion and different argument types.

---

# 1. Return Statement

The `return` statement is used to send a value back from a function to the place where it was called. Unlike `print()`, the returned value can be stored in a variable or used in further calculations.

## Example

```python
def add(a, b):
    return a + b

result = add(15, 20)
print("Sum:", result)
```

## Output

```
Sum: 35
```

---

# 2. Types of Arguments

Python allows different ways of passing arguments to functions.

| Argument Type | Description |
|--------------|-------------|
| Positional Arguments | Values are passed in the same order as parameters. |
| Keyword Arguments | Values are passed using parameter names. |
| Default Arguments | Parameters have default values. |
| Variable-Length Arguments | Accept multiple values using `*args`. |

---

## Positional Arguments

Arguments are passed according to their position.

```python
def student(name, course):
    print(name, "is enrolled in", course)

student("Lakshita", "AI & ML")
```

### Output

```
Lakshita is enrolled in AI & ML
```

---

## Keyword Arguments

Arguments are passed using parameter names, so the order does not matter.

```python
def employee(name, department):
    print(name, "works in", department)

employee(department="IT", name="Rahul")
```

### Output

```
Rahul works in IT
```

---

## Default Arguments

A default value is assigned to a parameter. If no value is passed, the default value is used.

```python
def greet(name="Student"):
    print("Welcome", name)

greet()
greet("Lakshita")
```

### Output

```
Welcome Student
Welcome Lakshita
```

---

## Variable-Length Arguments

The `*args` syntax allows a function to accept any number of arguments.

```python
def total(*numbers):
    print("Sum =", sum(numbers))

total(10, 20, 30, 40)
```

### Output

```
Sum = 100
```

---

# 3. Variable Scope

Variable scope determines where a variable can be accessed in a program. Python mainly has two types of scope:

- Local Scope
- Global Scope

---

## Local Variable

A local variable is created inside a function and can only be accessed within that function.

```python
def display():
    message = "Hello Python"
    print(message)

display()
```

### Output

```
Hello Python
```

---

## Global Variable

A global variable is declared outside the function and can be accessed throughout the program.

```python
course = "Python"

def show():
    print(course)

show()
```

### Output

```
Python
```

---

# 4. Recursive Functions

A recursive function is a function that calls itself until a specific condition is met. Recursion is commonly used in mathematical calculations, searching algorithms, and tree traversal.

## Example: Factorial Using Recursion

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))
```

### Output

```
120
```

---

## Example: Fibonacci Series Using Recursion

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

for i in range(6):
    print(fibonacci(i), end=" ")
```

### Output

```
0 1 1 2 3 5
```

---

# Summary

| Topic | Description |
|--------|-------------|
| Return Statement | Returns a value from a function. |
| Positional Arguments | Arguments passed according to position. |
| Keyword Arguments | Arguments passed using parameter names. |
| Default Arguments | Uses predefined default values. |
| Variable-Length Arguments | Accepts multiple values using `*args`. |
| Local Scope | Variable accessible only inside the function. |
| Global Scope | Variable accessible throughout the program. |
| Recursion | A function calling itself repeatedly until a base condition is met. |

---

# Exercises

## Exercise 1: Return the Square of a Number

### Solution

```python
def square(num):
    return num * num

print(square(8))
```

### Output

```
64
```

---

## Exercise 2: Demonstrate Default Arguments

### Solution

```python
def greet(name="Guest"):
    print("Hello", name)

greet()
greet("Lakshita")
```

### Output

```
Hello Guest
Hello Lakshita
```

---

## Exercise 3: Find the Factorial Using Recursion

### Solution

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(6))
```

### Output

```
720
```

---

## Exercise 4: Find the Sum of Multiple Numbers Using *args

### Solution

```python
def addition(*numbers):
    print("Sum =", sum(numbers))

addition(5, 10, 15, 20)
```

### Output

```
Sum = 50
```
