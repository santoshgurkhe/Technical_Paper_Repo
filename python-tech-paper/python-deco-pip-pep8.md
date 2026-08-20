# 5. Python Decorators

## What is a Decorator?

A **Decorator** is a function that modifies or extends the behavior of another function without changing its original code.

Decorators are represented using the **@** symbol in Python.

---

## Why do we use Decorators?

Decorators help us:

- Reuse code.
- Avoid writing duplicate code.
- Add extra functionality without modifying the original function.
- Improve code readability.

---

## When should we use Decorators?

Use decorators when you want to:

- Log function calls.
- Authenticate users.
- Measure execution time.
- Validate input.
- Cache function results.

They are widely used in **Flask**, **Django**, and many Python libraries.

---

## Syntax

```python
@decorator_name
def function_name():
    pass
```

---

## Example

```python
def decorator(func):

    def wrapper():

        print("Before Function")

        func()

        print("After Function")

    return wrapper


@decorator
def hello():

    print("Hello World")


hello()
```

### Output

```
Before Function
Hello World
After Function
```

### Explanation

- `hello()` is passed to the decorator.
- The decorator wraps the original function.
- Extra code runs before and after the original function.

---

## Important Points

- Decorators do not modify the original function.
- They improve code reusability.
- Multiple decorators can be applied to a single function.
- Commonly used in web frameworks and APIs.

---

# 6. Virtual Environment (virtualenv)

## What is a Virtual Environment?

A **Virtual Environment** is an isolated Python environment created for a specific project.

Each project can have its own Python packages and versions without affecting other projects.

---

## Why do we use Virtual Environments?

Without a virtual environment, installing a package updates the global Python installation, which may cause version conflicts between projects.

A virtual environment solves this problem by keeping dependencies isolated.

---

## When should we use a Virtual Environment?

Create a virtual environment for **every Python project**, especially when:

- Working on multiple projects.
- Using different package versions.
- Collaborating with a team.
- Deploying applications.

---

## Create a Virtual Environment

```bash
python -m venv venv
```

This creates a folder named `venv` containing the isolated Python environment.

---

## Activate the Virtual Environment

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

The package is installed only inside the current virtual environment.

---

## Save Installed Packages

```bash
pip freeze > requirements.txt
```

This stores all installed packages and their versions in a `requirements.txt` file.

---

## Install Packages from requirements.txt

```bash
pip install -r requirements.txt
```

---

## Deactivate the Virtual Environment

```bash
deactivate
```

---

## Typical Project Structure

```
Project/

│── venv/
│── app.py
│── requirements.txt
│── README.md
```

---

## Important Points

- Create one virtual environment per project.
- Do not upload the `venv` folder to GitHub.
- Add `venv/` to `.gitignore`.
- Share `requirements.txt` instead of the virtual environment.

---

# 7. pip Package Manager

## What is pip?

**pip** is Python's official package manager.

It is used to install, update, remove, and manage third-party Python packages.

---

## Why do we use pip?

Python's standard library is powerful, but many projects require additional libraries.

Examples:

- NumPy
- Pandas
- Django
- Flask
- Requests
- Matplotlib

pip allows us to install these packages easily.

---

## When should we use pip?

Use pip whenever your project requires an external library.

---

## Common pip Commands

### Check pip Version

```bash
pip --version
```

---

### Install a Package

```bash
pip install numpy
```

---

### Install Multiple Packages

```bash
pip install numpy pandas matplotlib
```

---

### Upgrade a Package

```bash
pip install --upgrade numpy
```

---

### Uninstall a Package

```bash
pip uninstall numpy
```

---

### Display Package Information

```bash
pip show numpy
```

---

### List Installed Packages

```bash
pip list
```

---

### Save Installed Packages

```bash
pip freeze > requirements.txt
```

---

### Install Packages from requirements.txt

```bash
pip install -r requirements.txt
```

---

## Important Points

- Use pip inside a virtual environment.
- Keep packages updated when appropriate.
- Use `requirements.txt` to share project dependencies.
- Install only the packages your project needs.

---

# 8. PEP-8 Standards

## What is PEP-8?

**PEP-8** (Python Enhancement Proposal 8) is the official style guide for writing Python code.

It provides guidelines that make Python code consistent, readable, and easier to maintain.

---

## Why do we follow PEP-8?

Following PEP-8:

- Improves readability.
- Makes collaboration easier.
- Produces professional code.
- Helps maintain consistency across projects.

---

## When should we use PEP-8?

PEP-8 should be followed in every Python project, especially in professional development and open-source projects.

---

## Important PEP-8 Guidelines

### 1. Use Meaningful Variable Names

✅ Good

```python
student_name = "Santosh"
```

❌ Bad

```python
s = "Santosh"
```

---

### 2. Class Names

Use **PascalCase**.

```python
class StudentDetails:
    pass
```

---

### 3. Function and Variable Names

Use **snake_case**.

```python
def calculate_total():
    pass
```

---

### 4. Constants

Use **UPPER_CASE**.

```python
MAX_SIZE = 100
```

---

### 5. Indentation

Use **4 spaces** per indentation level.

✅ Correct

```python
if True:
    print("Hello")
```

---

### 6. Line Length

Keep lines within **79 characters** whenever possible.

---

### 7. Spaces Around Operators

✅ Correct

```python
total = a + b
```

❌ Incorrect

```python
total=a+b
```

---

### 8. Imports

Place imports at the beginning of the file.

```python
import os
import sys
```

---

### 9. Comments

Write clear and meaningful comments.

```python
# Calculate total marks
```

---

### 10. Docstrings

Use docstrings to describe modules, classes, and functions.

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b
```

---

## Important Points

- Follow PEP-8 in every project.
- Use meaningful names.
- Keep code simple and readable.
- Write comments only when necessary.
- Use tools like **pylint**, **flake8**, or **black** to help maintain code quality.

---

# 9. Conclusion

Python provides a simple yet powerful ecosystem for software development.

Understanding:

- List methods
- String methods
- Object-Oriented Programming (OOP)
- Decorators
- Virtual Environments
- pip Package Manager
- PEP-8 Coding Standards

helps developers write clean, reusable, and maintainable code.

By following these concepts and best practices, developers can build professional Python applications and collaborate effectively on real-world projects.

---

# References

1. Python Official Documentation – https://docs.python.org/3/
2. PEP 8 – https://peps.python.org/pep-0008/
3. PyPI – https://pypi.org/
4. Real Python – https://realpython.com/
