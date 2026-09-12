# When to Use `forEach`, `map`, `filter`, and `reduce`

## `forEach()`

Use when you want to **perform an action** for every element.

```javascript
let names = ["Ram", "Sam"];

names.forEach(name => {
    console.log(name);
});
```

## `map()`

Use when you want to **create a new array** by changing every element.

```javascript
let numbers = [1, 2, 3];

let doubled = numbers.map(number => number * 2);

console.log(doubled); // [2, 4, 6]
```

## `filter()`

Use when you want to **select specific elements**.

```javascript
let numbers = [1, 2, 3, 4];

let even = numbers.filter(number => number % 2 === 0);

console.log(even); // [2, 4]
```

## `reduce()`

Use when you want to **combine elements into one value**.

```javascript
let numbers = [10, 20, 30];

let total = numbers.reduce((sum, number) => sum + number, 0);

console.log(total); // 60

```
<br>

# Mutable and Immutable Methods

**Mutable** methods change the original value.

**Immutable** methods return a new value without changing the original.

## Mutable Example

```javascript
let numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers); // [1, 2, 3, 4]
```

`push()`, `pop()`, `splice()`, and `sort()` are mutable array methods.

## Immutable Example

```javascript
let numbers = [1, 2, 3];

let result = numbers.map(number => number * 2);

console.log(numbers); // [1, 2, 3]
console.log(result);  // [2, 4, 6]
```

`map()`, `filter()`, `slice()`, and `concat()` are immutable array methods.

<br>

# Error Handling with `try...catch`

`try...catch` is used to handle errors without stopping the entire program.

```javascript
try {
    let result = 10 / 0;
    console.log(result);
} catch (error) {
    console.log(error.message);
}
```

If an error occurs inside `try`, the `catch` block handles it.

```javascript
try {
    console.log(name);
} catch (error) {
    console.log("Something went wrong");
}
```

Output:

```text
Something went wrong
```
<br>

# Throwing Errors

`throw` is used to create and send an error manually.

```javascript
function checkAge(age) {
    if (age < 18) {
        throw new Error("Age must be 18 or above");
    }

    return "Allowed";
}

console.log(checkAge(15));
```

Use `try...catch` to handle the thrown error.

```javascript
try {
    checkAge(15);
} catch (error) {
    console.log(error.message);
}
```
<br>

# `throw new Error()` vs `throw "Error message"`

`throw new Error()` creates an Error object with a message and stack trace.

```javascript
throw new Error("Something went wrong");
```

A plain string only throws the string value.

```javascript
throw "Something went wrong";
```

Prefer `throw new Error()` because it provides useful error information for debugging.

# Reading Error Messages and Stack Traces

The error message tells you **what went wrong**, while the stack trace helps find **where it happened**.

```javascript
function divide(a, b) {
    if (b === 0) {
        throw new Error("Cannot divide by zero");
    }

    return a / b;
}

divide(10, 0);
```

Example error:

```text
Error: Cannot divide by zero
    at divide (app.js:3:15)
    at app.js:8:1
```

Check the **error message**, then look at the **file name, line number, and function name** in the stack trace.

# Importance of the `catch` Block

The `catch` block handles errors and prevents unexpected program termination.

```javascript
try {
    JSON.parse("invalid");
} catch (error) {
    console.log("Invalid JSON:", error.message);
}
```

It also helps us display useful error information while debugging.

<br>

# Spread Operator

The spread operator `...` expands elements from an array or properties from an object.

## Array

```javascript
let first = [1, 2];
let second = [3, 4];

let numbers = [...first, ...second];

console.log(numbers); // [1, 2, 3, 4]
```

## Object

```javascript
let person = { name: "Santosh" };

let user = { ...person, age: 22 };

console.log(user);
// { name: "Santosh", age: 22 }
```

# Template Literals

Template literals use backticks `` ` `` and allow variables inside `${}`.

```javascript
let name = "Santosh";
let age = 22;

let message = `My name is ${name} and I am ${age} years old.`;

console.log(message);
```

# Default Parameters

Default parameters provide a default value when no argument is passed.

```javascript
function greet(name = "Guest") {
    console.log(`Hello ${name}`);
}

greet("Santosh"); // Hello Santosh
greet();          // Hello Guest
```

If an argument is passed, it replaces the default value.

<br>

# Destructuring

Destructuring is used to extract values from arrays or objects into variables.

## Array Destructuring

```javascript
let numbers = [10, 20, 30];

let [first, second] = numbers;

console.log(first);  // 10
console.log(second); // 20
```

## Object Destructuring

```javascript
let person = {
    name: "Santosh",
    age: 22
};

let { name, age } = person;

console.log(name); // Santosh
console.log(age);  // 22
```

# Closures

A closure is created when an inner function remembers and can access variables from its outer function even after the outer function has finished.

```javascript
function counter() {
    let count = 0;

    return function () {
        count++;
        return count;
    };
}

let increment = counter();

console.log(increment()); // 1
console.log(increment()); // 2
```

Here, the inner function remembers the `count` variable.

<br>

# Arrow Functions vs Regular Functions

Arrow functions are shorter and handle `this` differently from regular functions.

## Syntax

```javascript
function add(a, b) {
    return a + b;
}

const add = (a, b) => a + b;
```

## `this`

Regular functions have their own `this`.

Arrow functions use `this` from the surrounding scope.

```javascript
const person = {
    name: "Santosh",

    greet() {
        console.log(this.name);
    }
};

person.greet(); // Santosh
```

# `===` vs `==`

`===` checks both **value and type**.

`==` checks the value after type conversion.

```javascript
console.log(5 === "5"); // false
console.log(5 == "5");  // true
```

Prefer `===` because it avoids unexpected type conversion.

# `value === undefined` vs `!value`

`value === undefined` specifically checks whether the value is `undefined`.

```javascript
let value;

console.log(value === undefined); // true
```

`!value` also returns `true` for other falsy values such as `0`, `""`, `null`, and `false`.

```javascript
let value = 0;

console.log(!value); // true
```

So use `value === undefined` when you specifically want to check for `undefined`.

<br>

# Array Utility Methods Chaining

Method chaining means using multiple array methods one after another.

```javascript
let numbers = [1, 2, 3, 4, 5];

let result = numbers
    .filter(number => number > 2)
    .map(number => number * 2);

console.log(result); // [6, 8, 10]
```

# `null` vs `undefined`

`undefined` means a value has not been assigned.

```javascript
let name;

console.log(name); // undefined
```

`null` means we intentionally set the value to nothing.

```javascript
let user = null;

console.log(user); // null
```
<br>

# Importing and Exporting Modules

Modules allow us to split JavaScript code into different files and reuse it.

## Export

`module.exports` is used to export values from a file.

```javascript
// math.js

function add(a, b) {
    return a + b;
}

module.exports = add;
```

## Import

`require()` is used to import the exported value.

```javascript
// app.js

const add = require("./math");

console.log(add(2, 3)); // 5
```
<br>

# Console Methods

Console methods are useful for displaying information and debugging.

```javascript
console.log("Hello");       // General output
console.error("Error");     // Error message
console.info("Information"); // Information
console.warn("Warning");    // Warning message
```

Example:

```javascript
let age = 15;

if (age < 18) {
    console.warn("User is under 18");
}
```

# JavaScript Best Practices

- Use proper indentation.

```javascript
function greet(name) {
    console.log(`Hello ${name}`);
}
```

- Use meaningful variable names.

```javascript
let studentName = "Santosh";
let totalMarks = 85;
```

- Use `const` by default and `let` when the value needs to change.

```javascript
const name = "Santosh";
let count = 0;

count++;
```

- Use clear loop variable names.

```javascript
for (let index = 0; index < numbers.length; index++) {
    console.log(numbers[index]);
}
```

- Avoid unnecessary global variables.

```javascript
function calculateTotal(price, quantity) {
    return price * quantity;
}
```

- Keep functions small and focused on one task.
- Use consistent naming and formatting.
- Avoid unnecessary comments and duplicate code.

# Passing Functions to Other Functions

A function can be passed as an argument to another function and called when needed.

```javascript
function greet(name) {
    console.log(`Hello ${name}`);
}

function executeFunction(callback) {
    callback("Santosh");
}

executeFunction(greet);
```

Here, `greet` is passed to `executeFunction` and called inside it.

# Named Functions and Anonymous Functions

## Named Function

A named function has a function name.

```javascript
function greet() {
    console.log("Hello");
}

greet();
```

## Anonymous Function

An anonymous function does not have its own name.

```javascript
let greet = function() {
    console.log("Hello");
};

greet();
```

Anonymous functions are commonly used as callbacks.

```javascript
let numbers = [1, 2, 3];

numbers.forEach(function(number) {
    console.log(number);
});
```

# Variable Number of Arguments

JavaScript functions can accept any number of arguments using the rest operator `...`.

```javascript
function add(...numbers) {
    return numbers.reduce((sum, number) => sum + number, 0);
}

console.log(add(10, 20));       // 30
console.log(add(10, 20, 30));   // 60
```

# Debugging Strategies

When an error occurs:

1. Read the error message.
2. Check the file and line number.
3. Check the stack trace.
4. Use `console.log()` to check values.
5. Reproduce the error with a small example.

```javascript
function divide(a, b) {
    console.log(a, b);

    return a / b;
}

console.log(divide(10, 0));
```

Use debugging tools such as `console.log()` and browser/VS Code debugger to find the cause of the problem.
