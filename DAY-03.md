## DAY 3 OF TRAINING
## PYTHON FOUNDATIONS- LOOPS AND CONTROL FLOW STATEMENT
Welcome to **Day 3 of the Industrial Training for AI & Machine Learning**!

After learning the fundamentals of Python, today's session focuses on understanding how Python performs calculations, makes decisions, and executes repetitive tasks efficiently. We will explore different types of **operators**, learn how to use **conditional statements** for decision-making, and understand the working of **loops** to automate repetitive operations.

These concepts are essential for writing efficient Python programs and form the foundation for solving real-world programming problems. By the end of this session, we will be able to apply operators, implement control flow using conditional statements, and use loops to simplify repetitive tasks in Python.

---

## Learning Objectives

By the end of this session, you will be able to:
- Use `if`, `if-else`, and `if-elif-else` statements for decision-making.
- Implement `for` and `while` loops to perform repetitive tasks.
- Control loop execution using `break`, `continue`, and `pass` statements.
- Write simple Python programs by combining operators, conditions, and loops.

---
## 1. Python Loops

Loops are used to execute a block of code repeatedly until a specified condition is met. They help reduce code duplication, improve efficiency, and make programs easier to write and maintain. Python provides two main types of loops: for loop, which is used for iterating over sequences, and while loop, which executes as long as a given condition is True.

## 1.1 For Loop and range() Function

A for loop is used to execute a block of code repeatedly by iterating over a sequence such as a list, tuple, string, or a sequence of numbers. When the number of iterations is known in advance, the for loop is the most suitable choice.

The range() function is commonly used with a for loop to generate a sequence of numbers. It allows us to specify the starting value, ending value (not included), and an optional step size. This combination makes it easy to repeat tasks a fixed number of times.
## Syntax:
```for variable in range(start, stop, step):
    # Code to be executed
```
```
for i in range(1, 6):
    print("Iteration:", i)
```
## Output:
```
Iteration: 1
Iteration: 2
Iteration: 3
Iteration: 4
Iteration: 5
```

## 1.2 While Loop

A while loop is used to execute a block of code repeatedly as long as a specified condition is True. It is useful when the number of iterations is not known in advance. The loop stops automatically when the condition becomes False.

## Syntax:
```
while condition:
    # Code to be executed
```
```
num = 5
i = 1

while i <= 10:
    print(f"{num} x {i} = {num * i}")
    i += 1
```
## Output:
```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```
This is a simple and standard example for demonstrating the while loop in your Day 3 report.
