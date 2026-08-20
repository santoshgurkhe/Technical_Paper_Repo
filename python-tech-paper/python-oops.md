# 4. Objects and Object-Oriented Programming (OOP)

## What is Object-Oriented Programming (OOP)?

Object-Oriented Programming (OOP) is a programming paradigm that organizes code using **objects** and **classes**. It combines data (attributes) and functions (methods) into a single unit called an object.

Instead of writing everything as separate functions, OOP groups related data and behavior together, making code easier to understand, reuse, and maintain.

---

## Why do we use OOP?

OOP is used because it helps us:

- Organize code into logical units.
- Reuse existing code.
- Reduce code duplication.
- Improve code readability.
- Make applications easier to maintain.
- Build scalable software.

---

## When should we use OOP?

Use OOP when:

- Developing medium or large applications.
- Multiple objects share similar properties.
- Code reusability is important.
- Multiple developers work on the same project.
- Building desktop, web, game, or enterprise applications.

For very small scripts or one-time automation tasks, procedural programming is often enough.

---

## Real-World Example

Think about a **Car**.

Every car has:

**Attributes**

- Brand
- Color
- Speed

**Behaviors**

- Start
- Stop
- Accelerate

A car is an object.

The design used to manufacture different cars is called a class.

```
          Class
        +---------+
        |   Car   |
        +---------+
             |
     ------------------
     |        |       |
   Car1     Car2    Car3

 Objects created from one class
```

---

# Class

## What is a Class?

A class is a **blueprint** or **template** used to create objects.

It defines what data and behavior an object will have.

### Why do we use a Class?

Instead of writing the same code repeatedly, we define it once and create multiple objects.

### Syntax

```python
class Student:
    pass
```

### Example

```python
class Student:

    def display(self):
        print("Student Object")

student1 = Student()

student1.display()
```

Output

```
Student Object
```

---

# Object

## What is an Object?

An object is an **instance of a class**.

It contains its own data and can perform actions defined inside the class.

### Example

```python
student = Student()
```

Here,

- Student → Class
- student → Object

---

# Constructor (__init__)

## What is a Constructor?

A constructor is a special method that executes automatically when an object is created.

In Python, the constructor is written using `__init__()`.

### Why do we use it?

It initializes object data.

### Example

```python
class Student:

    def __init__(self, name, age):

        self.name = name
        self.age = age

student = Student("Santosh",22)

print(student.name)
```

Output

```
Santosh
```

---

# self Keyword

## What is self?

`self` refers to the **current object**.

Python automatically passes the current object to every instance method.

### Why do we use self?

It helps access:

- Object variables
- Object methods

Example

```python
class Student:

    def __init__(self,name):

        self.name = name
```

Here,

```
self.name

↓

Current object's name
```

---

# Attributes and Methods

## Attributes

Variables inside a class are called attributes.

Example

```python
class Student:

    def __init__(self):

        self.name = "Santosh"
```

Here,

```
name

↓

Attribute
```

---

## Methods

Functions inside a class are called methods.

```python
class Student:

    def display(self):

        print("Hello")
```

Here,

```
display()

↓

Method
```

---

# Four Pillars of OOP

Python OOP is mainly based on four principles.

```
              OOP

     ┌────────┼─────────┐

 Encapsulation  Inheritance

 Polymorphism   Abstraction
```

---

# 1. Encapsulation

## What is Encapsulation?

Encapsulation means **binding data and methods together** inside a class and restricting direct access to sensitive data.

### Why do we use Encapsulation?

- Protect data.
- Improve security.
- Prevent accidental changes.

### Example

```python
class Bank:

    def __init__(self):

        self.__balance = 10000

    def show_balance(self):

        print(self.__balance)

bank = Bank()

bank.show_balance()
```

Output

```
10000
```

### Important Point

Variables beginning with `__` are private.

---

# 2. Inheritance

## What is Inheritance?

Inheritance allows one class to use the properties and methods of another class.

The new class is called the **Child Class**.

The existing class is called the **Parent Class**.

### Why do we use Inheritance?

- Reuse code.
- Reduce duplication.
- Build relationships.

### Example

```python
class Animal:

    def sound(self):

        print("Animal Sound")

class Dog(Animal):

    pass

dog = Dog()

dog.sound()
```

Output

```
Animal Sound
```

---

## Types of Inheritance

Python supports

- Single
- Multiple
- Multilevel
- Hierarchical
- Hybrid

The most commonly used is **Single Inheritance**.

---

# 3. Polymorphism

## What is Polymorphism?

Polymorphism means

**One Interface, Multiple Behaviors**

The same method behaves differently depending on the object.

### Why do we use Polymorphism?

- Flexible code
- Easy extension
- Better maintainability

### Example

```python
class Dog:

    def sound(self):

        print("Bark")

class Cat:

    def sound(self):

        print("Meow")

animals = [Dog(),Cat()]

for animal in animals:

    animal.sound()
```

Output

```
Bark

Meow
```

---

# 4. Abstraction

## What is Abstraction?

Abstraction means hiding unnecessary implementation details and showing only the essential features.

Example:

While driving a car,

You press the accelerator.

You do not need to know how the engine works internally.

### Why do we use Abstraction?

- Reduce complexity.
- Improve security.
- Hide implementation details.

### Example

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

Output

```
Area of Square
```

---

# Advantages of OOP

- Code Reusability
- Better Organization
- Easy Maintenance
- Easy Testing
- Improved Security
- Scalable Applications

---

# Disadvantages of OOP

- Slightly more complex than procedural programming.
- More memory usage.
- Not suitable for very small scripts.

---

# OOP vs Procedural Programming

| Procedural Programming | Object-Oriented Programming |
|------------------------|-----------------------------|
| Function-based | Class-based |
| Less reusable | Highly reusable |
| Difficult for large projects | Better for large projects |
| Less secure | Better data security |
| Easier for small programs | Better for complex applications |

---

# Applications of OOP

OOP is widely used in:

- Web Development
- Desktop Applications
- Mobile Applications
- Game Development
- Banking Systems
- Hospital Management Systems
- Student Management Systems
- E-commerce Applications

---

# Important Interview Points

- Class → Blueprint for creating objects.
- Object → Instance of a class.
- Constructor → Initializes an object automatically.
- `self` → Refers to the current object.
- Encapsulation → Data hiding.
- Inheritance → Code reuse.
- Polymorphism → One interface, multiple implementations.
- Abstraction → Hide implementation details.
- Python supports multiple inheritance.
- Everything in Python is an object.

---

# Summary

Object-Oriented Programming helps developers build reusable, organized, and maintainable software. By using classes and objects, code becomes easier to understand and extend. The four main principles—Encapsulation, Inheritance, Polymorphism, and Abstraction—are the foundation of OOP and are widely used in real-world Python applications.
