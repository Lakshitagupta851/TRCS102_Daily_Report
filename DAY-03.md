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

## 2. Control Flow Statements

Control flow statements determine the order in which the statements of a program are executed. They allow a program to make decisions, repeat tasks, or change the normal flow of execution based on conditions. Instead of executing every statement sequentially, control flow statements help the program choose different execution paths, making it more efficient, flexible, and capable of solving real-world problems.

## Key Points
Control the sequence of program execution.
Enable decision-making based on conditions.
Execute a block of code repeatedly using loops.
Improve code efficiency by reducing repetition.
Make programs interactive and capable of handling different scenarios.
## Types of Control Flow Statements
## 2.1 Conditional Statements
Used for decision-making.
Examples: if, if-else, if-elif-else, and nested if.
## 2.2 Looping Statements
Used to execute a block of code multiple times.
Examples: for loop and while loop.
## 2.3 Loop Control Statements
Used to modify the normal execution of loops.
break – Terminates the loop immediately.
continue – Skips the current iteration and moves to the next.
pass – Acts as a placeholder when no action is required.

Control flow statements are one of the most important concepts in Python programming because they help create logical, dynamic, and efficient programs by controlling how and when different parts of the code are executed.

## 2.1 Conditional Statements

Conditional statements are used to make decisions in a Python program. They execute different blocks of code based on whether a specified condition is True or False. These statements help a program respond differently to different inputs and situations, making it more dynamic and intelligent.

## if Statement

The if statement is used to execute a block of code only when a specified condition is True.

## Code:
```
age = 20

if age >= 18:
    print("Eligible to vote")
```
## Output:
```
Eligible to vote
```

## if-else Statement

The if-else statement is used to execute one block of code if the condition is True, otherwise another block is executed.

## Code:
```
num = 7

if num % 2 == 0:
    print("Even Number")
else:
    print("Odd Number")
```
## Output:
```
Odd Number
```

## if-elif-else Statement

The if-elif-else statement is used to check multiple conditions. Once a condition becomes True, the corresponding block is executed.

## Code:
```
marks = 75

if marks >= 90:
    print("Grade A")
elif marks >= 60:
    print("Grade B")
else:
    print("Grade C")
```
## Output:
```
Grade B
```

## Nested if Statement

A nested if statement is an if statement placed inside another if statement. It is used when multiple conditions need to be checked one after another.

## Code:
```
age = 20
has_license = True

if age >= 18:
    if has_license:
        print("Eligible to drive")
```
## Output:
```
Eligible to drive
```
## 2.2 Looping Statements

Looping statements are used to execute a block of code repeatedly until a specified condition is met. They help reduce code duplication and make programs more efficient. Python provides two types of loops: for loop and while loop.
### for Loop

The for loop is used to iterate over a sequence such as a list, string, tuple, or a sequence of numbers generated using range(). It is generally used when the number of iterations is known.

## Code:
```
for i in range(1, 6):
    print(i)
```
## Output:
```
1
2
3
4
5
```
## while Loop

The while loop repeatedly executes a block of code as long as the given condition is True. It is useful when the number of iterations is not known beforehand.

## Code:
```
i = 1

while i <= 5:
    print(i)
    i += 1
```
## Output:
```
1
2
3
4
5
```

## 2.3 Loop Control Statements

Loop control statements are used to alter the normal execution of a loop. They help control the flow of iteration by terminating the loop, skipping an iteration, or acting as a placeholder. Python provides three loop control statements: break, continue, and pass.
## break Statement

The break statement immediately terminates the loop when a specified condition is met, and control moves to the next statement after the loop.

## Code:
```
for i in range(1, 6):
    if i == 4:
        break
    print(i)
```
## Output:
```
1
2
3
```

## continue Statement
The continue statement skips the current iteration and continues with the next iteration of the loop.

## Code:
```
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
```
## Output:
```
1
2
4
5
```

## pass Statement

The pass statement is a placeholder that does nothing. It is used when a statement is required syntactically, but no action needs to be performed.

## Code:
```
for i in range(1, 6):
    if i == 3:
        pass
    print(i)
```
## Output:
```
1
2
3
4
5
```
