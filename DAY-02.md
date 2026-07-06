## DAY 2 OF TRAINING
# Python Foundations — Operators

Welcome to **Day 2 of the Industrial Training for AI & Machine Learning**!

After learning the fundamentals of Python on Day 1, today's session focuses on understanding how Python performs calculations, makes decisions, and executes repetitive tasks efficiently. We will explore different types of **operators**.

These concepts are essential for writing efficient Python programs and form the foundation for solving real-world programming problems. By the end of this session, we will be able to apply operatorsts to simplify repetitive tasks in Python.

---

## Learning Objectives

By the end of this session, you will be able to:
- Understand different types of Python operators and their applications.
- Perform arithmetic, comparison, logical, assignment, membership, identity, and bitwise operations.
- Write simple Python programs by combining operators.

  ## Types Of Operators
  Operators are special symbols used to perform operations on variables and values. Python provides different types of operators for arithmetic calculations, comparisons, logical operations, assignments, bitwise operations, membership testing, and identity checking.

## 1. Arithmetic Operators
Arithmetic operators are used to perform mathematical operations such as addition, subtraction, multiplication, division, modulus, exponentiation, and floor division.
```
a = 15
b = 4

print("Addition:", a + b)
print("Subtraction:", a - b)
print("Multiplication:", a * b)
print("Division:", a / b)
print("Modulus:", a % b)
print("Exponent:", a ** b)
print("Floor Division:", a // b)
```
## Output
```
Addition: 19
Subtraction: 11
Multiplication: 60
Division: 3.75
Modulus: 3
Exponent: 50625
Floor Division: 3
```
## 2. Comparison (Relational) Operators
Comparison operators compare two values and return either True or False. They are mainly used in conditional statements.
```x = 20
y = 10

print("x == y :", x == y)
print("x != y :", x != y)
print("x > y :", x > y)
print("x < y :", x < y)
print("x >= y :", x >= y)
print("x <= y :", x <= y)
```
## Output
```
x == y : False
x != y : True
x > y : True
x < y : False
x >= y : True
x <= y : False
```
## 3. Logical Operators
Logical operators are used to combine multiple conditions. They return a Boolean value (True or False).

and → Returns True if both conditions are true.
or → Returns True if at least one condition is true.
not → Reverses the result.
```
age = 20
has_id = True
print(age >= 18 and has_id)
print(age < 18 or has_id)
print(not has_id)
```
## Output
```
True
True
False
```
## 4. Assignment Operators
Assignment operators are used to assign values to variables. They can also perform operations while assigning the result.
```num = 10

num += 5
print("After += :", num)

num *= 2
print("After *= :", num)

num -= 10
print("After -= :", num)
```
## Output
```
After += : 15
After *= : 30
After -= : 20
```
## 5. Bitwise Operators
Bitwise operators perform operations on the binary representation of integers. They are commonly used in low-level programming and optimization.
```
a = 5
b = 3

print("AND :", a & b)
print("OR :", a | b)
print("XOR :", a ^ b)
print("Left Shift :", a << 1)
print("Right Shift :", a >> 1)
```
## Output
```
AND : 1
OR : 7
XOR : 6
Left Shift : 10
Right Shift : 2
```
## 6. Membership Operators
Membership operators check whether a value exists in a sequence such as a list, tuple, string, or set.

in → Returns True if the element is present.
not in → Returns True if the element is not present.
```
fruits = ["Apple", "Banana", "Mango"]

print("Apple" in fruits)
print("Orange" in fruits)
print("Orange" not in fruits)
```
## Output
```
True
False
True
```
## 7. Identity Operators
Identity operators compare whether two variables refer to the same object in memory.

is → Returns True if both variables refer to the same object.
is not → Returns True if they refer to different objects.
```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print("a is b :", a is b)
print("a is c :", a is c)
print("a == c :", a == c)
print("a is not c :", a is not c)
```
## Output
```
a is b : True
a is c : False
a == c : True
a is not c : True
```



| Operator Type           | Purpose                                               |
| ----------------------- | ----------------------------------------------------- |
| Arithmetic              | Performs mathematical calculations                    |
| Comparison (Relational) | Compares two values                                   |
| Logical                 | Combines multiple conditions                          |
| Assignment              | Assigns and updates variable values                   |
| Bitwise                 | Performs operations on binary values                  |
| Membership              | Checks whether an element exists in a collection      |
| Identity                | Checks whether two variables refer to the same object |



## Exercises: Operators ans Expressions

## Exercise 1: Write a Python script that takes a number (you can hardcode it to start) and checks:

1. If the number is strictly positive (greater than 0) AND even.

2. If it is divisible by 5 or is a multiple of 3.

3. Print both boolean results.

## Solution
```
num = 30

condition1 = (num > 0) and (num % 2 == 0)
condition2 = (num % 5 == 0) or (num % 3 == 0)

print("Positive and Even:", condition1)
print("Divisible by 5 or Multiple of 3:", condition2)
```
## Output
```
Positive and Even: True
Divisible by 5 or Multiple of 3: True
```

## Exercise 2: Find the odd and the even numbers using bitwise operators.

## Solution
```
num = int(input("Enter a number: "))

if num & 1:
    print(num, "is an Odd number")
else:
    print(num, "is an Even number")
```
## Output
```
Enter a number: 15
15 is an Odd number
```

## Exercise 3: Check if a number is positive and even, and check if it is divisible by 5 and multiple of 3.

## Solution
```
number = 30

# 1. Positive AND Even
is_pos_and_even = (number > 0) and (number % 2 == 0)

# 2. Divisible by 5 OR multiple of 3
is_div_5_or_mult_3 = (number % 5 == 0) or (number % 3 == 0)

print(f"For number {number}:")
print(f"Is positive and even? {is_pos_and_even}")
print(f"Is divisible by 5 or multiple of 3? {is_div_5_or_mult_3}")
```
