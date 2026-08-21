# SOLID Principles

SOLID is a group of five principles used to write clean and maintainable code. It helps us organize code properly and makes it easier to update, test, and add new features.

The five SOLID principles are:

1. Single Responsibility Principle
2. Open/Closed Principle
3. Liskov Substitution Principle
4. Interface Segregation Principle
5. Dependency Inversion Principle

# 1. Single Responsibility Principle

A class should handle one main job.

Bad Example - 
```python
class Order:
    def calculate_total(self, price, quantity):
        return price * quantity

    def send_email(self):
        print("Order email sent")
```
```
This class is doing two jobs: calculating the order and sending an email.
```
Good Example-
```python
class Order:
    def calculate_total(self, price, quantity):
        return price * quantity

class EmailService:
    def send_email(self):
        print("Order email sent")
```

Now each class has its own responsibility.


# 2. Open/Closed Principle

We should add new features without changing existing working code.

Bad Example -
```python
class Payment:
    def pay(self, method):
        if method == "UPI":
            print("Payment using UPI")
        elif method == "Card":
            print("Payment using Card")
```

Every time we add a payment method, we need to change this class.

Good Example -
```python
class Payment:
    def pay(self):
        pass

class UPI(Payment):
    def pay(self):
        print("Payment using UPI")

class Card(Payment):
    def pay(self):
        print("Payment using Card")
```
We can add a new payment method by creating a new class.

# 3. Liskov Substitution Principle

A child class should work properly when used instead of its parent class.

Bad Example -
```python
class Bird:
    def fly(self):
        print("Bird is flying")

class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins cannot fly")
```
Penguin cannot properly replace Bird because not every bird can fly.

Good Example -
```python
class Bird:
    def move(self):
        print("Bird is moving")

class Sparrow(Bird):
    def move(self):
        print("Sparrow is flying")

class Penguin(Bird):
    def move(self):
        print("Penguin is walking")
```
Now both classes can replace Bird and work correctly.

# 4. Interface Segregation Principle

A class should only use methods that it actually needs.

Bad Example -
```python
class Machine:
    def print_document(self):
        pass

    def scan_document(self):
        pass

class SimplePrinter(Machine):
    def print_document(self):
        print("Printing")

    def scan_document(self):
        raise Exception("Cannot scan")
```
The printer is forced to implement scanning even though it cannot scan.

Good Example -
```python
class Printer:
    def print_document(self):
        print("Printing")

class Scanner:
    def scan_document(self):
        print("Scanning")
```
The printer and scanner have separate responsibilities.

# 5. Dependency Inversion Principle

A high-level class should not depend directly on one specific class.

Bad Example -
```python
class Email:
    def send(self, message):
        print(message)

class UserService:
    def __init__(self):
        self.email = Email()

    def notify(self):
        self.email.send("Welcome")
```
UserService is directly connected to Email. Changing to SMS requires changing this class.

Good Example -
```python
class Notification:
    def send(self, message):
        pass

class Email(Notification):
    def send(self, message):
        print(f"Email: {message}")

class UserService:
    def __init__(self, notification):
        self.notification = notification

    def notify(self):
        self.notification.send("Welcome")
```
Now we can use Email, SMS, or another notification type without changing UserService.


# References

- Bob Martin SOLID Principles of Object Oriented and Agile Design - https://www.youtube.com/watch?v=TMuno5RZNeE
- SOLID - https://www.youtube.com/playlist?list=PL6n9fhu94yhXjG1w2blMXUzyDrZ_eyOme
