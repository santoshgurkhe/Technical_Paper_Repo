# Python Self Review

**Author:** Santosh Gurkhe

---

# Table of Contents

1. Introduction
2. Python List (Array) Methods
3. Python String Methods
4. Objects and Object-Oriented Programming (OOP)
5. Decorators
6. Virtual Environment (virtualenv)
7. pip Package Manager
8. PEP-8 Standards
9. Conclusion

---

# 1. Introduction

Python is a high-level, interpreted, and object-oriented programming language known for its simple syntax and readability. It is widely used in web development, automation, data science, artificial intelligence, scripting, and software development.

Python provides a rich set of built-in libraries and tools that help developers write clean, efficient, and maintainable code.

---

# 2. Python List (Array) Methods

## What is a List?

A **List** is a built-in Python data structure used to store multiple values in a single variable.

Unlike arrays in languages like C or Java, Python lists can store different data types and can grow or shrink dynamically.

Example:

```python
students = ["Rahul", "Ankit", "Santosh"]
```

---

## Why do we use Lists?

Lists are used to:

- Store multiple values together.
- Easily add, remove, or update items.
- Process collections of data using loops.
- Reduce the need for multiple variables.

Example:

Instead of

```python
student1 = "Rahul"
student2 = "Ankit"
student3 = "Santosh"
```

We can simply write

```python
students = ["Rahul", "Ankit", "Santosh"]
```

---

## When should we use a List?

Use a list when:

- Data needs to be modified.
- Order of items matters.
- Duplicate values are allowed.
- Multiple values need to be stored together.

---

## Common List Methods

| Method | Purpose |
|---------|---------|
| append() | Add one item |
| extend() | Add multiple items |
| insert() | Insert at a specific position |
| remove() | Remove a value |
| pop() | Remove using index |
| clear() | Remove all items |
| index() | Find position |
| count() | Count occurrences |
| sort() | Sort the list |
| reverse() | Reverse the list |
| copy() | Create a copy |

---

## append()

### What is it?

Adds one item at the end of the list.

### Syntax

```python
list.append(item)
```

### Example

```python
fruits = ["Apple", "Banana"]

fruits.append("Mango")

print(fruits)
```

Output

```
['Apple', 'Banana', 'Mango']
```

Explanation:

The new item is added to the end of the list.

---

## extend()

### What is it?

Adds multiple items to the existing list.

```python
numbers = [1,2]

numbers.extend([3,4])

print(numbers)
```

Output

```
[1,2,3,4]
```

---

## insert()

Adds an item at a specified index.

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

## remove()

Removes the first matching value.

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

## pop()

Removes an item using its index.

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

## sort()

Sorts the list in ascending order.

```python
numbers = [4,2,8,1]

numbers.sort()

print(numbers)
```

Output

```
[1,2,4,8]
```

---

## reverse()

Reverses the order of the list.

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

## Important Points

- Lists are mutable.
- Lists allow duplicate values.
- Lists preserve insertion order.
- Lists can store different data types.

---

# 3. Python String Methods

## What is a String?

A **String** is a sequence of characters enclosed in single quotes (' '), double quotes (" "), or triple quotes (''' ''' or """ """).

Example

```python
name = "Santosh"
```

---

## Why do we use Strings?

Strings are used whenever we work with text.

Examples:

- User names
- Passwords
- Messages
- Emails
- File names

---

## When should we use Strings?

Use strings whenever data is textual instead of numeric.

---

## Common String Methods

| Method | Purpose |
|---------|---------|
| upper() | Convert to uppercase |
| lower() | Convert to lowercase |
| title() | Capitalize every word |
| capitalize() | Capitalize first letter |
| strip() | Remove spaces |
| replace() | Replace text |
| split() | Convert string to list |
| join() | Join list into string |
| find() | Find index |
| startswith() | Check prefix |
| endswith() | Check suffix |

---

## upper()

```python
text = "python"

print(text.upper())
```

Output

```
PYTHON
```

---

## lower()

```python
text = "HELLO"

print(text.lower())
```

Output

```
hello
```

---

## replace()

```python
text = "I Love Java"

print(text.replace("Java","Python"))
```

Output

```
I Love Python
```

---

## split()

```python
text = "Python Django Flask"

print(text.split())
```

Output

```
['Python', 'Django', 'Flask']
```

---

## join()

```python
words = ["Python","is","easy"]

print(" ".join(words))
```

Output

```
Python is easy
```

---

## strip()

```python
text = "   hello   "

print(text.strip())
```

Output

```
hello
```

---

## find()

```python
text = "Python Programming"

print(text.find("Program"))
```

Output

```
7
```

---

## startswith()

```python
text = "Python"

print(text.startswith("Py"))
```

Output

```
True
```

---

## endswith()

```python
text = "python.py"

print(text.endswith(".py"))
```

Output

```
True
```

---

## Important Points

- Strings are immutable.
- Every modification returns a new string.
- Strings support indexing and slicing.
- Many built-in methods simplify text processing.

---

## Summary

In this part, we covered:

- What Lists are
- Why and when to use Lists
- Common List methods with examples
- What Strings are
- Why and when to use Strings
- Common String methods with examples

