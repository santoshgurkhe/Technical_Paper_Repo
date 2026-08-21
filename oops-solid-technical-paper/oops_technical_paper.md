# Introduction to OOP in Python

OOP is a way of writing programs using classes and objects.  
It helps us keep related data and functions together and makes code easier to reuse and manage.

## Class

A class is like a blueprint for creating objects. It defines what data and methods an object can have.

For example, a Student class can contain a student's name and a method to display the name.

```python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)


student = Student("Santosh")
student.display()
```
```
Output:

Santosh
```
Here, Student is the class, and it defines the data and behavior of a student.


## Object

An object is a real instance created from a class.  
Each object can have its own data but uses the methods defined in the class.

```python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)


student1 = Student("Santosh")
student2 = Student("Rahul")

student1.display()
student2.display()
```
```text
Output:

Santosh
Rahul
```

Here, student1 and student2 are objects of the Student class. They use the same class but have different names.

## Constructor

A constructor is the `__init__()` method in a class. It runs automatically when an object is created and is mainly used to set the initial values.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks


student = Student("Santosh", 85)

print(student.name)
print(student.marks)
```
```text
Output:

Santosh
85
```
Here, __init__() sets the name and marks when the student object is created.

## self Keyword

self refers to the current object of a class. It is used to access the variables and methods that belong to that object.

Example
```python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)


student = Student("Santosh")
student.display()
```
```
Output
Santosh
```
Here, self.name stores the name of the current student object.

## Instance Variables

Instance variables are variables that belong to a particular object. Each object can have different values for these variables.

Example
```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks


student1 = Student("Santosh", 85)
student2 = Student("Rahul", 90)

print(student1.name, student1.marks)
print(student2.name, student2.marks)
```
```text
Output :

Santosh 85
Rahul 90
```

Here, name and marks are instance variables. Each student object has its own values.

## Class Variables

Class variables belong to the class and are shared by all objects of that class. They are useful when the same value is needed for every object.

Example
```python
class Student:
    school = "ABC School"

    def __init__(self, name):
        self.name = name


student1 = Student("Santosh")
student2 = Student("Rahul")

print(student1.school)
print(student2.school)
```
```text
Output
ABC School
ABC School
```
Here, school is a class variable because both objects use the same value.


## Methods

Methods are functions written inside a class. They define the actions that an object can perform.

Example
```python
class Calculator:
    def add(self, first, second):
        return first + second

calculator = Calculator()

print(calculator.add(10, 20))
```
```text
Output
30
```

## Four Pillars of OOP in Python
1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

## Encapsulation

Encapsulation means keeping data and related methods together inside a class. It also helps control how data is accessed or changed.

Example
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
```
Output
1500
```

## Abstraction

Abstraction means hiding unnecessary details and showing only the required functionality.

Example :
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

rectangle = Rectangle(10, 5)

print(rectangle.area())
```
```
Output
50
```

## Inheritance

Inheritance allows a child class to use the properties and methods of a parent class.

Example -
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
```
Output
Eating
Barking
```

## Types of Inheritance

Python supports the following main types of inheritance:

- Single Inheritance
- Multiple Inheritance
- Multilevel Inheritance
- Hierarchical Inheritance
- Hybrid Inheritance

# Single Inheritance

One child class inherits from one parent class.

Example -
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

# Multiple Inheritance

One class inherits from more than one parent class.

Example -
```python
class Father:
    def father_skill(self):
        print("Father's skill")


class Mother:
    def mother_skill(self):
        print("Mother's skill")


class Child(Father, Mother):
    pass

child = Child()

child.father_skill()
child.mother_skill()
```
```
Output
Father's skill
Mother's skill
```

# Multilevel Inheritance

A class inherits from another child class.

Example -
```python
class Animal:
    def eat(self):
        print("Eating")


class Dog(Animal):
    def bark(self):
        print("Barking")


class Puppy(Dog):
    def play(self):
        print("Playing")


puppy = Puppy()

puppy.eat()
puppy.bark()
puppy.play()
```

# Hierarchical Inheritance

Multiple child classes inherit from the same parent class.

Example -
```python
class Animal:
    def eat(self):
        print("Eating")


class Dog(Animal):
    pass


class Cat(Animal):
    pass

dog = Dog()
cat = Cat()

dog.eat()
cat.eat()
```

# Hybrid Inheritance

Hybrid inheritance is a combination of two or more types of inheritance.

# Polymorphism

Polymorphism means the same method or operation can behave differently depending on the object.

Example -
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
```
Output
Bark
Meow
```

# Method Overriding

Method overriding happens when a child class provides its own version of a method from the parent class.

Example -
```python
class Animal:
    def sound(self):
        print("Animal makes a sound")


class Dog(Animal):
    def sound(self):
        print("Dog barks")

dog = Dog()

dog.sound()
```
```
Output
Dog barks
```

# Duck Typing

Duck typing means Python focuses on whether an object has the required method instead of checking its class.

Example -
```python
class Dog:
    def speak(self):
        print("Woof")

class Cat:
    def speak(self):
        print("Meow")

def make_sound(animal):
    animal.speak()


make_sound(Dog())
make_sound(Cat())
```
```
Output
Woof
Meow
```

# Operator Overloading

Operator overloading allows us to define how operators such as + and == work with our own objects.

Example -
```python
class Student:
    def __init__(self, marks):
        self.marks = marks

    def __eq__(self, other):
        return self.marks == other.marks


student1 = Student(90)
student2 = Student(90)

print(student1 == student2)
```
```
Output
True
```

# Class Method

A class method works with the class itself and uses cls instead of self.

Example -
```python
class Student:
    school = "ABC School"

    @classmethod
    def change_school(cls, school_name):
        cls.school = school_name

Student.change_school("XYZ School")

print(Student.school)
```
```
Output
XYZ School
```

# Static Method

A static method does not use self or cls. It is used for functionality related to the class but does not need object or class data.

Example -
```python
class Math:
    @staticmethod
    def square(number):
        return number * number

print(Math.square(5))
```
```
Output
25
```

# Abstract Class

An abstract class is used as a base class and can define methods that child classes must implement.

Example -
```python
from abc import ABC, abstractmethod


class Vehicle(ABC):
    @abstractmethod
    def start(self):
        pass

class Car(Vehicle):
    def start(self):
        print("Car started")


car = Car()
car.start()
```
```
Output
Car started
```

# Magic or Dunder Methods

Magic methods are special methods that start and end with double underscores. Python calls them automatically in specific situations.

Some common methods are:

- __init__()
- __str__()
- __repr__()
- __len__()
- __eq__()
- __add__()
- __str__() 
```
# Method

The __str__() method defines what should be shown when an object is printed.

Example -
```python
class Student:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

student = Student("Santosh")

print(student)
```
```
Output
Santosh
```

# References

- Python Documentation - https://docs.python.org/3/tutorial/classes.html?utm_source=chatgpt.com
- GeeksforGeeks - OOP Concepts - https://www.geeksforgeeks.org/python/python-oops-concepts/
- Chatgpt - Used for conceptual explanations and clarification. - http://chatgpt.com

