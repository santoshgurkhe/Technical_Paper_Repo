# Object-Oriented Programming (OOP) in Python

## What is OOP?

Object-Oriented Programming (OOP) is a programming paradigm that organizes code into **objects**. An object contains **data (attributes)** and **functions (methods)** that operate on that data.

### Why use OOP?

- Makes code reusable.
- Improves code organization.
- Makes projects easier to maintain.
- Models real-world objects.
- Reduces code duplication.

---

# OOP Terminology

| Term | Description |
|------|-------------|
| Class | Blueprint for creating objects. |
| Object | Instance of a class. |
| Attribute | Variable inside a class. |
| Method | Function inside a class. |
| Constructor | Special method (`__init__`) executed when an object is created. |

---

# Class and Object

## Definition

A **class** is a blueprint.

An **object** is an instance of that blueprint.

### Real-world Example

**Blueprint → House**

- Blueprint = Class
- Built House = Object

### Syntax

```python
class Student:
    pass

s1 = Student()
```

---

# Constructor (__init__)

## Definition

The constructor initializes an object's data.

It automatically runs whenever an object is created.

### Syntax

```python
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age

s1 = Student("Santosh", 22)

print(s1.name)
print(s1.age)
```

### Output

```
Santosh
22
```

---

# self Keyword

## Definition

`self` refers to the current object.

### Example

```python
class Student:

    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)

s1 = Student("Rahul")
s1.display()
```

### Output

```
Rahul
```

---

# Instance Variables

## Definition

Variables that belong to each object.

### Example

```python
class Car:

    def __init__(self, brand):
        self.brand = brand

c1 = Car("BMW")
c2 = Car("Audi")

print(c1.brand)
print(c2.brand)
```

### Output

```
BMW
Audi
```

---

# Methods

## Definition

Functions inside a class.

### Example

```python
class Calculator:

    def add(self, a, b):
        return a + b

obj = Calculator()

print(obj.add(10, 20))
```

### Output

```
30
```

---

# Four Pillars of OOP

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

---

# 1. Encapsulation

## Definition

Encapsulation means **binding data and methods together inside one class** and controlling access to data.

### Real-world Example

ATM Machine

- User interacts with buttons.
- Internal processing is hidden.

### Example

```python
class BankAccount:

    def __init__(self, balance):
        self.__balance = balance

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount(1000)

account.deposit(500)

print(account.get_balance())
```

### Output

```
1500
```

---

# 2. Abstraction

## Definition

Abstraction hides implementation details and only shows necessary functionality.

### Real-world Example

Driving a car.

You use

- Steering
- Brake
- Accelerator

You don't need to know how the engine works.

### Example

```python
from abc import ABC, abstractmethod

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):

    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

r = Rectangle(10, 5)

print(r.area())
```

### Output

```
50
```

---

# 3. Inheritance

## Definition

Inheritance allows one class to reuse properties and methods of another class.

### Real-world Example

Vehicle

↓

Car

↓

Electric Car

### Example

```python
class Animal:

    def eat(self):
        print("Eating")

class Dog(Animal):

    def bark(self):
        print("Barking")

dog = Dog()

dog.eat()
dog.bark()
```

### Output

```
Eating
Barking
```

---

# Types of Inheritance

## Single Inheritance

```python
class A:
    pass

class B(A):
    pass
```

---

## Multiple Inheritance

```python
class A:
    pass

class B:
    pass

class C(A, B):
    pass
```

---

## Multilevel Inheritance

```python
class A:
    pass

class B(A):
    pass

class C(B):
    pass
```

---

## Hierarchical Inheritance

```python
class A:
    pass

class B(A):
    pass

class C(A):
    pass
```

---

## Hybrid Inheritance

Combination of multiple inheritance types.

---

# 4. Polymorphism

## Definition

Polymorphism means **one interface, multiple implementations**.

---

## Method Overriding

### Example

```python
class Animal:

    def sound(self):
        print("Animal sound")

class Dog(Animal):

    def sound(self):
        print("Dog barks")

class Cat(Animal):

    def sound(self):
        print("Cat meows")

Dog().sound()
Cat().sound()
```

### Output

```
Dog barks
Cat meows
```

---

## Duck Typing

### Example

```python
class Dog:

    def speak(self):
        print("Woof")

class Cat:

    def speak(self):
        print("Meow")

def sound(animal):
    animal.speak()

sound(Dog())
sound(Cat())
```

### Output

```
Woof
Meow
```

---

## Operator Overloading

### Example

```python
class Student:

    def __init__(self, marks):
        self.marks = marks

    def __eq__(self, other):
        return self.marks == other.marks

s1 = Student(90)
s2 = Student(90)

print(s1 == s2)
```

### Output

```
True
```

---

# Method Overloading (Python Style)

Python does not support traditional method overloading.

Use default parameters or `*args`.

### Example

```python
class Calculator:

    def add(self, *numbers):
        return sum(numbers)

obj = Calculator()

print(obj.add(10))
print(obj.add(10, 20))
print(obj.add(10, 20, 30))
```

### Output

```
10
30
60
```

---

# Class Variables

Shared among all objects.

```python
class Student:

    school = "ABC School"

    def __init__(self, name):
        self.name = name

s1 = Student("A")
s2 = Student("B")

print(s1.school)
print(s2.school)
```

---

# Static Method

```python
class Math:

    @staticmethod
    def square(x):
        return x * x

print(Math.square(5))
```

### Output

```
25
```

---

# Class Method

```python
class Student:

    school = "ABC School"

    @classmethod
    def change_school(cls, name):
        cls.school = name

Student.change_school("XYZ School")

print(Student.school)
```

### Output

```
XYZ School
```

---

# Magic (Dunder) Methods

| Method | Purpose |
|---------|----------|
| `__init__` | Constructor |
| `__str__` | String representation |
| `__repr__` | Official representation |
| `__len__` | Length |
| `__eq__` | Equality (`==`) |
| `__lt__` | Less than (`<`) |
| `__gt__` | Greater than (`>`) |
| `__add__` | `+` operator |
| `__sub__` | `-` operator |

---

# Example of __str__

```python
class Student:

    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

s = Student("Santosh")

print(s)
```

### Output

```
Santosh
```

---

# Advantages of OOP

- Code Reusability
- Better Organization
- Easy Maintenance
- Modular Design
- Improved Security
- Scalability
- Easier Testing
