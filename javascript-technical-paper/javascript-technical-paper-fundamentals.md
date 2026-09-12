# Different Data Types in JavaScript

JavaScript has 8 main data types.

## Primitive Data Types

- String
- Number
- Boolean
- Undefined
- Null
- BigInt
- Symbol

```javascript
let name = "Santosh";       // String
let age = 22;               // Number
let isActive = true;        // Boolean
let value;                  // Undefined
let user = null;            // Null
let big = 123456789n;       // BigInt
let id = Symbol("id");      // Symbol
```
## Non-Primitive Data Type

### Object

Used to store related data as key-value pairs.

~~~javascript
let person = {
    name: "Santosh",
    age: 22
};
~~~

Arrays and functions are also objects in JavaScript.

~~~javascript
let numbers = [10, 20, 30];

function greet() {
    console.log("Hello");
}
~~~

## Checking Data Type

The `typeof` operator is used to check the data type.

~~~javascript
console.log(typeof "Hello");   // string
console.log(typeof 25);        // number
console.log(typeof true);      // boolean
console.log(typeof undefined); // undefined
console.log(typeof 10n);       // bigint
console.log(typeof {});        // object
~~~

`typeof null` returns `"object"` because of a historical behavior in JavaScript.

~~~javascript
console.log(typeof null); // object
~~~

<br>

# Scopes in JavaScript

Scope decides where a variable can be accessed.

## Global Scope

A variable declared outside a function or block has global scope.

```javascript
let name = "Santosh";

function greet() {
    console.log(name);
}

greet();
```

## Function Scope

Variables declared inside a function can only be accessed inside that function.

```javascript
function greet() {
    let message = "Hello";

    console.log(message);
}

greet();
```

## Block Scope

`let` and `const` are available only inside the block `{}` where they are declared.

```javascript
if (true) {
    let age = 22;
    const city = "Bengaluru";

    console.log(age);
}

console.log(age); // Error
```

`var` is function-scoped, not block-scoped.

```javascript
if (true) {
    var age = 22;
}

console.log(age); // 22
```
<br>

# let, var, const

JavaScript provides `let`, `var`, and `const` to declare variables.

## let

`let` allows the value to be changed and is block-scoped.

```javascript
let age = 22;

age = 23;

console.log(age); // 23
```

## const

`const` cannot be reassigned and is block-scoped.

```javascript
const name = "Santosh";

name = "Rahul"; // Error
```

## var

`var` is function-scoped and its value can be changed.

```javascript
var age = 22;

age = 23;

console.log(age); // 23
```

`let` and `const` cannot be accessed outside their block.

```javascript
if (true) {
    let a = 10;
    const b = 20;
    var c = 30;
}

console.log(c); // 30
console.log(a); // Error
console.log(b); // Error
```
<br>

# Why We Must Not Use `var`

`var` is function-scoped and can cause unexpected behavior. Prefer `let` and `const`.

```javascript
if (true) {
    var age = 22;
}

console.log(age); // 22
```

`var` can also be redeclared.

```javascript
var name = "Santosh";
var name = "Rahul";

console.log(name); // Rahul
```

It is better to use:

```javascript
let age = 22;
const name = "Santosh";
```

### var Can Be Hoisted

```javascript
console.log(age); // undefined

var age = 22;
```

This can make the code harder to understand and debug.

<br>

# Why Global Variables Are Bad

Global variables can be accessed and changed from anywhere in the program, which can cause unexpected changes and make debugging difficult.

```javascript
let count = 0;

function increase() {
    count++;
}

increase();

console.log(count); // 1
```

Prefer keeping variables inside the required scope.

<br>

# Truthy and Falsy Values

In JavaScript, values are either **truthy** or **falsy** when used in a condition.

Falsy values include:

```javascript
false
0
""
null
undefined
NaN
```

Example:

```javascript
let name = "";

if (name) {
    console.log("Name exists");
} else {
    console.log("Name is empty");
}

// Name is empty
```

Most other values are truthy:

```javascript
if ("Hello") {
    console.log("Truthy");
}
// Truthy
```
<br>

# Function Hoisting

Function declarations are hoisted, so they can be called before they are declared.

```javascript
greet();

function greet() {
    console.log("Hello");
}
```
Output:
`Hello`

Function expressions are not usable before their assignment.

```javascript
greet(); // Error

const greet = function () {
    console.log("Hello");
};
```
<br>

# What Happens When a Function Has No `return` Statement

If a function does not return a value, it returns `undefined`.

```javascript
function greet() {
    console.log("Hello");
}

let result = greet();

console.log(result); // undefined
```
<br>

# Different Ways of Declaring a Function

## Function Declaration

```javascript
function add(a, b) {
    return a + b;
}
```

## Function Expression

```javascript
const add = function(a, b) {
    return a + b;
};
```

## Arrow Function

```javascript
const add = (a, b) => {
    return a + b;
};
```
<br>

# Pass by Value and Pass by Reference

Primitive values are passed by value.

```javascript
let a = 10;

function change(value) {
    value = 20;
}

change(a);

console.log(a); // 10
```

Objects are passed by reference value, so changes to their properties can affect the original object.

```javascript
let person = {
    name: "Santosh"
};

function changeName(user) {
    user.name = "ABC";
}

changeName(person);

console.log(person.name); // ABC
```
<br>

# Different Types of `for` Loops

## `for` Loop

Used when the number of iterations is known.

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

## `for...in`

Used to iterate over object keys.

```javascript
const person = {
    name: "Santosh",
    age: 22
};

for (let key in person) {
    console.log(key);
}
```

## `for...of`

Used to iterate over values of an iterable such as an array.

```javascript
const numbers = [10, 20, 30];

for (let number of numbers) {
    console.log(number);
}
```

## `forEach`

Used to execute a function for each array element.

```javascript
const numbers = [10, 20, 30];

numbers.forEach(function(number) {
    console.log(number);
});
```

## `while`

Runs while the condition is true.

```javascript
let i = 0;

while (i < 5) {
    console.log(i);
    i++;
}
```
<br>

# Searching MDN

MDN (Mozilla Developer Network) is a useful reference for JavaScript, HTML, CSS, and Web APIs.

Search for the exact method or concept when you need its syntax, parameters, return value, or examples.

Example:

```text
MDN Array.map
MDN Array.filter
MDN JavaScript closures
```
