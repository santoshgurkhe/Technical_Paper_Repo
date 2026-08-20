# SOLID Principles in Python

# Table of Contents

1. Introduction
2. What is SOLID?
3. Why Use SOLID Principles?
4. Single Responsibility Principle (SRP)
5. Open/Closed Principle (OCP)
6. Liskov Substitution Principle (LSP)
7. Interface Segregation Principle (ISP)
8. Dependency Inversion Principle (DIP)
9. Summary
10. Advantages of SOLID

---

# Introduction

SOLID is a set of five object-oriented design principles introduced by **Robert C. Martin (Uncle Bob)**.

These principles help developers write code that is:

- Easy to understand
- Easy to maintain
- Easy to extend
- Easy to test
- Less dependent on other classes
- More reusable

SOLID is not a framework or library.

It is a **design guideline** for writing better software.

---

# What is SOLID?

| Letter | Principle |
|---------|-----------|
| S | Single Responsibility Principle |
| O | Open/Closed Principle |
| L | Liskov Substitution Principle |
| I | Interface Segregation Principle |
| D | Dependency Inversion Principle |

---

# Why Use SOLID?

Without SOLID:

- Large classes
- Tight coupling
- Difficult debugging
- Difficult testing
- Difficult to add new features
- High maintenance cost

With SOLID:

- Small classes
- Loose coupling
- Better scalability
- Better readability
- Better testing
- Better code reuse

---

# S — Single Responsibility Principle (SRP)

## Definition

A class should have **only one reason to change**.

It should perform **only one responsibility**.

---

## Purpose

A class should focus on one specific task.

---

## Why use SRP?

If one class performs many tasks:

- It becomes difficult to maintain.
- Bugs increase.
- Code becomes difficult to understand.

---

## Real-world Example

Teacher

Responsibilities:

- Teach students

Teacher should NOT:

- Manage salary
- Clean classroom
- Drive school bus

Each responsibility belongs to a different person.

---

## Bad Example

```python
class Employee:

    def calculate_salary(self):
        print("Calculating salary")

    def save_to_database(self):
        print("Saving employee")

    def send_email(self):
        print("Sending Email")
```

Problems

Employee class has three responsibilities.

- Salary
- Database
- Email

If email logic changes, Employee class changes.

If database changes, Employee class changes.

Too many reasons to modify one class.

---

## Good Example

```python
class Employee:

    def calculate_salary(self):
        print("Calculating salary")


class EmployeeRepository:

    def save(self):
        print("Saving employee")


class EmailService:

    def send(self):
        print("Sending Email")
```

Each class has only one responsibility.

---

## Advantages

- Easy maintenance
- Better readability
- Easy debugging
- Reusable classes

---

## Important Points

- One class
- One responsibility
- One reason to change

---

# O — Open/Closed Principle (OCP)

## Definition

Software entities should be:

- Open for Extension
- Closed for Modification

---

## Purpose

We should be able to add new features without modifying existing code.

---

## Why use OCP?

Modifying existing code may introduce bugs.

Instead, create new classes.

---

## Real-world Example

Mobile Charger

You buy a new phone.

You don't redesign the electricity board.

You simply use a compatible charger.

Existing system remains unchanged.

---

## Bad Example

```python
class Payment:

    def pay(self, method):

        if method == "Credit":
            print("Credit Card")

        elif method == "UPI":
            print("UPI")
```

Every new payment method requires modifying this class.

---

## Good Example

```python
from abc import ABC, abstractmethod

class Payment(ABC):

    @abstractmethod
    def pay(self):
        pass


class CreditCard(Payment):

    def pay(self):
        print("Credit Card Payment")


class UPI(Payment):

    def pay(self):
        print("UPI Payment")
```

Adding PayPal?

Simply create another class.

No existing code changes.

---

## Advantages

- Less bugs
- Easy extension
- Better scalability

---

# L — Liskov Substitution Principle (LSP)

## Definition

A child class should be able to replace its parent class without changing program behavior.

---

## Purpose

Inheritance should not break existing functionality.

---

## Real-world Example

Bird

A Sparrow can fly.

A Penguin is also a Bird but cannot fly.

Therefore Penguin should not inherit a class that forces flying behavior.

---

## Bad Example

```python
class Bird:

    def fly(self):
        print("Flying")


class Penguin(Bird):

    def fly(self):
        raise Exception("Penguins cannot fly")
```

Problem

```python
bird = Penguin()
bird.fly()
```

Program crashes.

LSP is violated.

---

## Good Example

```python
class Bird:
    pass


class FlyingBird(Bird):

    def fly(self):
        print("Flying")


class Sparrow(FlyingBird):
    pass


class Penguin(Bird):
    pass
```

Now everything works correctly.

---

## Advantages

- Better inheritance
- Less runtime errors
- Cleaner design

---

# I — Interface Segregation Principle (ISP)

## Definition

Clients should not be forced to implement methods they don't use.

---

## Purpose

Create small interfaces.

Avoid large interfaces.

---

## Real-world Example

Restaurant

Customer

- Orders food

Chef

- Cooks food

Cashier

- Takes payment

Each role has different responsibilities.

---

## Bad Example

```python
from abc import ABC, abstractmethod

class Worker(ABC):

    @abstractmethod
    def work(self):
        pass

    @abstractmethod
    def eat(self):
        pass


class Robot(Worker):

    def work(self):
        print("Working")

    def eat(self):
        pass
```

Robot doesn't eat.

ISP is violated.

---

## Good Example

```python
class Workable(ABC):

    @abstractmethod
    def work(self):
        pass


class Eatable(ABC):

    @abstractmethod
    def eat(self):
        pass


class Human(Workable, Eatable):

    def work(self):
        print("Working")

    def eat(self):
        print("Eating")


class Robot(Workable):

    def work(self):
        print("Working")
```

Robot only implements what it needs.

---

## Advantages

- Small interfaces
- Cleaner code
- Better flexibility

---

# D — Dependency Inversion Principle (DIP)

## Definition

High-level modules should not depend on low-level modules.

Both should depend on abstractions.

---

## Purpose

Reduce dependency between classes.

---

## Real-world Example

TV Remote

Remote works with different TVs.

Remote depends on a standard interface.

Not on Samsung or Sony directly.

---

## Bad Example

```python
class Keyboard:

    def type(self):
        print("Typing")


class Computer:

    def __init__(self):
        self.keyboard = Keyboard()

    def start(self):
        self.keyboard.type()
```

Computer is tightly coupled to Keyboard.

---

## Good Example

```python
from abc import ABC, abstractmethod

class InputDevice(ABC):

    @abstractmethod
    def input(self):
        pass


class Keyboard(InputDevice):

    def input(self):
        print("Typing")


class VoiceInput(InputDevice):

    def input(self):
        print("Voice Input")


class Computer:

    def __init__(self, device):
        self.device = device

    def start(self):
        self.device.input()


computer = Computer(Keyboard())
computer.start()

computer = Computer(VoiceInput())
computer.start()
```

Computer works with any input device.

---

## Advantages

- Loose coupling
- Easy testing
- Easy extension
- Better flexibility

---

# Summary

| Principle | Meaning |
|-----------|---------|
| SRP | One class, one responsibility |
| OCP | Extend without modifying |
| LSP | Child should replace parent safely |
| ISP | Small, focused interfaces |
| DIP | Depend on abstractions, not concrete classes |

---

# Advantages of SOLID

- Cleaner code
- Reusable code
- Easier maintenance
- Better scalability
- Easier testing
- Reduced coupling
- Improved readability
- Better software architecture

---

# Key Takeaways

- Keep classes small.
- Avoid unnecessary dependencies.
- Use inheritance carefully.
- Depend on interfaces, not implementations.
- Extend code instead of modifying existing code.

Following SOLID principles helps build software that is easier to maintain, extend, and test while reducing bugs and improving code quality.
