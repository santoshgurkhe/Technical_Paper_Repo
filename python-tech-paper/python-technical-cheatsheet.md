# Python Cheatsheet

## 1. Array Methods

In Python, we normally use a list when we need something like an array. A list can hold many values, and we can add, remove, or change the values.

### Common Methods

```python
marks = [45, 72, 61, 88]

marks.append(95)       # Add a value at the end
marks.insert(1, 50)    # Add a value at a position
marks.remove(61)       # Remove a value
marks.pop()            # Remove the last value
marks.sort()           # Sort the list
marks.reverse()        # Reverse the list
```

For example, if I have a list of marks, I can use sort() to arrange them from smaller to larger values.

```python
marks = [45, 72, 61, 88]

marks.sort()

print(marks)
```

Output:

```text
[45, 61, 72, 88]
```

Other useful methods include `count()`, `index()`, and `clear()`.

## 2. String Methods

Strings are used to store text. Python has many built-in methods that make it easier to work with text.

### Common Methods

```python
name = "  santosh gurkhe  "

print(name.upper())
print(name.lower())
print(name.strip())
print(name.replace("santosh", "rahul"))
print(name.split())
```

Some commonly used methods are:

* `upper()` converts the text to uppercase.
* `lower()` converts the text to lowercase.
* `strip()` removes extra spaces from the beginning and end.
* `replace()` replaces one part of the string with another.
* `split()` breaks a string into a list.
* `find()` finds the position of some text.
* `startswith()` checks how the string starts.
* `endswith()` checks how the string ends.

For example:

```python
message = "python is easy"

if message.startswith("python"):
    print("This is a Python message")
```

Output:

```text
This is a Python message
```

## 3. Dictionary Methods

A dictionary stores data in key: value pairs. It is useful when we want to connect one value with another.
```python
student = {
    "name": "Santosh",
    "age": 22,
    "marks": 85
}

print(student.keys())
print(student.values())
print(student.items())
print(student.get("name"))

student.update({"city": "Bangalore"})
student.pop("age")

print(student)
```

keys() returns all keys, values() returns all values, and items() returns both keys and values. get() safely gets a value using its key. update() adds or changes data, and pop() removes an item.

## Tuple and Set

A tuple is similar to a list, but its values cannot be changed after creation.
```python
colors = ("red", "blue", "green")

print(colors[0])
print(len(colors))
```
A set stores only unique values. Duplicate values are automatically removed.

numbers = {1, 2, 2, 3, 4, 4}

print(numbers)
```
Output:

{1, 2, 3, 4}
```
## List Comprehension

List comprehension is a short way to create a list using a loop.
```python
numbers = [1, 2, 3, 4, 5]

squares = [num ** 2 for num in numbers]

print(squares)
```
```
Output:

[1, 4, 9, 16, 25]
```

We can also add a condition.

numbers = [1, 2, 3, 4, 5, 6]

even_numbers = [num for num in numbers if num % 2 == 0]

print(even_numbers)

## Exception Handling

Exception handling helps us handle errors without stopping the complete program.
```python
try:
    number = int(input("Enter a number: "))
    print(number)

except ValueError:
    print("Please enter a valid number")

finally:
    print("Program finished")
```
try contains the code that may cause an error. except handles the error. finally always runs whether an error happens or not.

## File Handling

File handling is used to read or write data in files.

Writing to a File - 
```python
with open("notes.txt", "w") as file:
    file.write("I am learning Python")
Reading a File
with open("notes.txt", "r") as file:
    data = file.read()

print(data)
Appending to a File
with open("notes.txt", "a") as file:
    file.write("\nPython is easy")
```
r is used for reading, w for writing, and a for adding content without removing existing data.

##  Lambda Functions

A lambda function is a small function written in one line. It is useful for simple operations.
```python
add = lambda a, b: a + b

print(add(10, 20))
```
```
Output:

30
```
Lambda functions are often used with functions like sorted(), map(), and filter().
```python
numbers = [5, 2, 8, 1]

result = sorted(numbers, key=lambda x: x)

print(result)
```

## 3. Objects and Object-Oriented Programming

Object-Oriented Programming, or OOP, is a way of writing programs using classes and objects. A class is like a plan, and an object is the actual thing created from that class.

For example, we can create a `Student` class and make different student objects from it.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def show_details(self):
        print(self.name, self.marks)


student1 = Student("Santosh", 78)
student1.show_details()
```

### Four Main Pillars of OOP

### 1. Encapsulation

Encapsulation means keeping data and the methods that work with that data together inside a class. It also helps control how the data is accessed.

```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance

    def deposit(self, amount):
        self._balance += amount

    def show_balance(self):
        print(self._balance)


account = BankAccount(1000)
account.deposit(500)
account.show_balance()
```

Here, the balance is kept inside the class and is changed through the `deposit()` method.

### 2. Inheritance

Inheritance allows one class to use the properties and methods of another class. It helps avoid writing the same code again.

```python
class Animal:
    def eat(self):
        print("Animal is eating")


class Dog(Animal):
    def bark(self):
        print("Dog is barking")


dog = Dog()
dog.eat()
dog.bark()
```

Here, `Dog` gets the `eat()` method from `Animal`.

### 3. Polymorphism

Polymorphism means the same method name can behave differently depending on the object using it.

```python
class Dog:
    def sound(self):
        print("Dog barks")


class Cat:
    def sound(self):
        print("Cat meows")


dog = Dog()
cat = Cat()

dog.sound()
cat.sound()
```

Both classes have a `sound()` method, but they give different results.

### 4. Abstraction

Abstraction means hiding the unnecessary details and showing only what is needed. It helps us focus on what an object does instead of how it works internally.

```python
from abc import ABC, abstractmethod


class Payment(ABC):
    @abstractmethod
    def pay(self, amount):
        pass


class UPI(Payment):
    def pay(self, amount):
        print(f"Paid ₹{amount} using UPI")


payment = UPI()
payment.pay(500)
```

Here, the `Payment` class only tells us that a `pay()` method is required. The `UPI` class decides how the payment is handled.

### Why OOP is Useful

OOP helps divide a large program into smaller and manageable parts. It also makes code easier to reuse and maintain.

The four main pillars are:

* Encapsulation: Keep data and methods together.
* Inheritance: Reuse code from another class.
* Polymorphism: Same method, different behavior.
* Abstraction: Hide unnecessary details.


## 4. Decorators

A decorator is a function that adds some extra work to another function. It lets us add functionality without changing the original function.

For example, we can print a message before running a function.

```python
def check_function(func):
    def wrapper():
        print("Function is starting")
        func()

    return wrapper

@check_function
def study():
    print("I am studying Python")


study()
```

Output:

```text
Function is starting
I am studying Python
```

Here, `@check_function` is the decorator. It adds the extra message before study() runs.

Decorators are commonly useful for logging, checking permissions, authentication, and measuring execution time.

## 5. virtualenv

A virtual environment gives a project its own Python environment. It keeps the packages of one project separate from other projects.

For example, two projects may need different versions of the same package. A virtual environment helps avoid conflicts between them.

To create one:

```bash
python -m venv myenv
```

To activate it on Linux:

```bash
source myenv/bin/activate
```

After activation, packages installed with pip will be available in that environment.

To leave the environment:

```bash
deactivate
```

I would normally create a virtual environment before installing packages for a new Python project.

## 6. pip Package Manager

pip is the package manager used in Python. It helps us install, remove, and manage packages.

For example, if a project needs the requests package, we can install it using:

```bash
pip install requests
```

Some useful commands are:

```bash
pip list
pip show requests
pip uninstall requests
pip freeze
```

We can also save the packages used by a project:

```bash
pip freeze > requirements.txt
```

Another person can then install the same packages using:

```bash
pip install -r requirements.txt
```

This is useful when sharing a Python project because everyone can install the required packages.

## 7. PEP 8 Standards Summary

PEP 8 is a set of style guidelines for Python. It helps developers write code that is clean and easy to read.

Some important PEP 8 rules are:

* Use 4 spaces for indentation.
* Use snake_case for variables and functions.
* Use PascalCase for class names.
* Use spaces around operators.
* Keep imports at the top of the file.
* Use meaningful names.
* Avoid very long lines.
* Add blank lines where they improve readability.

Example:

```python
class Student:
    def __init__(self, name):
        self.name = name

    def show_name(self):
        print(self.name)


student = Student("Santosh")
student.show_name()
```

Here, Student follows the class naming style and show_name follows the function naming style.

Following PEP 8 makes code easier for other developers to read and work with. It also keeps the coding style consistent across a project.

## References

- Python Basics : https://chatgpt.com
- Python Decorators: https://docs.python.org/3/glossary.html#term-decorator
- Python Virtual Environments: https://docs.python.org/3/library/venv.html
- Python pip Documentation: https://pip.pypa.io/en/stable/
- PEP 8 Style Guide: https://peps.python.org/pep-0008/
