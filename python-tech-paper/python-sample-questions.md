# Python Self Review – Technical Paper

**Author:** Santosh Gurkhe  
**Language:** Python 3.x  
**Document Type:** Technical Paper / Self Review

---

# Table of Contents

1. Introduction
2. Python Array (List) Methods
3. Python String Methods
4. Objects and Object-Oriented Programming (OOP)
5. Python Decorators
6. Virtual Environment (virtualenv)
7. pip Package Manager
8. PEP-8 Standards Summary
9. Conclusion

---

# 1. Introduction

Python is one of the most popular programming languages because it is simple, readable, and powerful. It is used in web development, automation, artificial intelligence, data science, scripting, and many other domains.

This document summarizes important Python concepts with examples.

---

# 2. Python Array (List) Methods

Python does not have built-in arrays like some programming languages. Most developers use **lists**, which are dynamic arrays.

## Creating a List

```python
numbers = [10, 20, 30]
print(numbers)
```

Output

```
[10, 20, 30]
```

---

## Common List Methods

| Method | Description |
|---------|-------------|
| append() | Adds one element |
| extend() | Adds multiple elements |
| insert() | Inserts at a specific index |
| remove() | Removes a value |
| pop() | Removes by index |
| clear() | Removes all elements |
| index() | Returns position |
| count() | Counts occurrences |
| sort() | Sorts the list |
| reverse() | Reverses the list |
| copy() | Creates a copy |

---

### append()

```python
fruits = ["Apple", "Banana"]
fruits.append("Mango")

print(fruits)
```

Output

```
['Apple', 'Banana', 'Mango']
```

---

### extend()

```python
a = [1,2]
a.extend([3,4])

print(a)
```

Output

```
[1,2,3,4]
```

---

### insert()

```python
numbers = [1,3,4]
numbers.insert(1,2)

print(numbers)
```

Output

```
[1,2,3,4]
```

---

### remove()

```python
numbers = [10,20,30]

numbers.remove(20)

print(numbers)
```

Output

```
[10,30]
```

---

### pop()

```python
numbers = [10,20,30]

numbers.pop()

print(numbers)
```

Output

```
[10,20]
```

---

### sort()

```python
numbers = [5,2,9,1]

numbers.sort()

print(numbers)
```

Output

```
[1,2,5,9]
```

---

### reverse()

```python
numbers = [1,2,3]

numbers.reverse()

print(numbers)
```

Output

```
[3,2,1]
```

---

## List Diagram

```text
Index

0      1      2      3

+------+------+------+------+
| 10   | 20   | 30   | 40   |
+------+------+------+------+
```

---

# 3. Python String Methods

Strings are immutable sequences of characters.

```python
name = "python programming"
```

---

## Common String Methods

| Method | Description |
|---------|-------------|
| upper() | Converts to uppercase |
| lower() | Converts to lowercase |
| title() | Capitalizes each word |
| capitalize() | Capitalizes first letter |
| strip() | Removes spaces |
| replace() | Replaces text |
| split() | Converts string to list |
| join() | Joins list into string |
| find() | Finds index |
| startswith() | Checks prefix |
| endswith() | Checks suffix |

---

### upper()

```python
text = "python"

print(text.upper())
```

Output

```
PYTHON
```

---

### lower()

```python
text = "HELLO"

print(text.lower())
```

Output

```
hello
```

---

### replace()

```python
text = "I love Java"

print(text.replace("Java","Python"))
```

Output

```
I love Python
```

---

### split()

```python
text = "Python Django Flask"

print(text.split())
```

Output

```
['Python','Django','Flask']
```

---

### join()

```python
words = ["Python","is","easy"]

print(" ".join(words))
```

Output

```
Python is easy
```

---

### strip()

```python
text = "   hello   "

print(text.strip())
```

Output

```
hello
```

---

# String Representation

```text
P  y  t  h  o  n
0  1  2  3  4  5
```

---

# 4. Objects and Object-Oriented Programming (OOP)

Object-Oriented Programming organizes code using **classes** and **objects**.

## OOP Concepts

- Class
- Object
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

---

## Class and Object

```python
class Student:

    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)

student = Student("Santosh")

student.display()
```

Output

```
Santosh
```

---

## Object Diagram

```text
             Student Class
           -----------------
           name
           display()

                 |
                 |
          Object Created
                 |
         student = Student()
```

---

## Encapsulation

```python
class Bank:

    def __init__(self):
        self.__balance = 5000

    def show(self):
        print(self.__balance)

bank = Bank()

bank.show()
```

---

## Inheritance

```python
class Animal:

    def sound(self):
        print("Animal Sound")

class Dog(Animal):

    pass

dog = Dog()

dog.sound()
```

---

## Polymorphism

```python
class Dog:

    def sound(self):
        print("Bark")

class Cat:

    def sound(self):
        print("Meow")

animals = [Dog(), Cat()]

for animal in animals:
    animal.sound()
```

---

## Abstraction

```python
from abc import ABC, abstractmethod

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass

class Square(Shape):

    def area(self):
        print("Area of Square")

square = Square()

square.area()
```

---

# OOP Diagram

```text
          Object
             |
      +--------------+
      | Attributes   |
      | Methods      |
      +--------------+

             ↑

          Class
```

---

# 5. Python Decorators

Decorators modify the behavior of functions without changing their original code.

---

## Basic Example

```python
def decorator(func):

    def wrapper():

        print("Before Function")

        func()

        print("After Function")

    return wrapper


@decorator
def hello():

    print("Hello")

hello()
```

Output

```
Before Function
Hello
After Function
```

---

## Decorator Flow

```text
hello()

↓

decorator()

↓

wrapper()

↓

Original Function

↓

Return
```

---

# 6. Virtual Environment (virtualenv)

A virtual environment creates an isolated Python environment for each project.

Benefits

- Separate dependencies
- Avoid version conflicts
- Cleaner projects
- Better deployment

---

## Create Virtual Environment

```bash
python -m venv venv
```

---

## Activate

### Windows

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
source venv/bin/activate
```

---

## Install Packages

```bash
pip install requests
```

---

## Save Dependencies

```bash
pip freeze > requirements.txt
```

---

## Install Requirements

```bash
pip install -r requirements.txt
```

---

## Deactivate

```bash
deactivate
```

---

## Virtual Environment Structure

```text
Project/

│

├── venv/

│   ├── Scripts/

│   ├── Lib/

│   └── Include/

│

├── app.py

└── requirements.txt
```

---

# 7. pip Package Manager

pip is Python's official package manager.

---

## Check Version

```bash
pip --version
```

---

## Install Package

```bash
pip install numpy
```

---

## Upgrade Package

```bash
pip install --upgrade numpy
```

---

## Uninstall Package

```bash
pip uninstall numpy
```

---

## Show Package

```bash
pip show numpy
```

---

## List Packages

```bash
pip list
```

---

## Freeze Installed Packages

```bash
pip freeze
```

---

# pip Workflow

```text
Python Project

↓

pip install

↓

Package Download

↓

Installed into virtual environment
```

---

# 8. PEP-8 Standards Summary

PEP-8 is Python's official style guide.

---

## Naming Conventions

| Type | Example |
|------|---------|
| Variable | total_marks |
| Function | calculate_total() |
| Class | StudentData |
| Constant | MAX_SIZE |

---

## Indentation

Use **4 spaces**

Correct

```python
if True:
    print("Hello")
```

Incorrect

```python
if True:
  print("Hello")
```

---

## Imports

Correct

```python
import os
import sys
```

---

## Line Length

Maximum

```
79 characters
```

---

## Spaces Around Operators

Correct

```python
x = a + b
```

Incorrect

```python
x=a+b
```

---

## Blank Lines

- Two blank lines between classes
- Two blank lines between functions

---

## Comments

```python
# Calculate total marks
```

---

## Docstrings

```python
def add(a, b):
    """
    Returns the sum of two numbers.
    """
    return a + b
```

---

# Good vs Bad Code

Bad

```python
x=10
y=20
print(x+y)
```

Good

```python
first_number = 10
second_number = 20

print(first_number + second_number)
```

---

# Summary Table

| Topic | Key Learning |
|--------|--------------|
| Lists | Store multiple values and provide useful methods |
| Strings | Immutable sequence with many built-in methods |
| OOP | Organizes code using classes and objects |
| Decorators | Extend function behavior without modifying code |
| virtualenv | Isolates project dependencies |
| pip | Installs and manages Python packages |
| PEP-8 | Improves code readability and consistency |

---

# 9. Conclusion

Python provides powerful built-in features that make software development easier and more maintainable. Understanding list methods, string methods, object-oriented programming, decorators, virtual environments, package management, and PEP-8 coding standards helps developers write clean, efficient, and professional Python code.

Following these best practices improves code readability, simplifies collaboration, and makes Python projects easier to maintain and scale.

---

# References

1. https://docs.python.org/3/
2. https://peps.python.org/pep-0008/
3. https://pypi.org/
4. https://realpython.com/
5. https://docs.python.org/3/tutorial/

---
