# Popular Array Utility Methods

## Basics

```javascript
let numbers = [1, 2, 3];

numbers.push(4);              // [1, 2, 3, 4] - Mutable
numbers.pop();                // [1, 2, 3] - Mutable
numbers.concat([4, 5]);       // [1, 2, 3, 4, 5] - Immutable
numbers.slice(1, 3);          // [2, 3] - Immutable
numbers.splice(1, 1);         // Removes 2 - Mutable
numbers.join("-");            // "1-2-3" - Immutable
numbers.flat();               // Flattens nested arrays - Immutable
```

## Finding

```javascript
numbers.find(n => n > 1);       // First matching value
numbers.indexOf(2);             // Index of value
numbers.includes(2);            // true/false
numbers.findIndex(n => n > 1);  // Index of first match
```

All four are **immutable**.

## Higher Order Functions

A higher-order function takes another function as an argument or returns a function.

### forEach

Runs a function for each element.

```javascript
let numbers = [1, 2, 3];

numbers.forEach(number => {
    console.log(number);
});
```

### filter

Returns elements that match a condition.

```javascript
let numbers = [1, 2, 3, 4];

let evenNumbers = numbers.filter(number => number % 2 === 0);

console.log(evenNumbers); // [2, 4]
```

### map

Creates a new array by changing each element.

```javascript
let numbers = [1, 2, 3];

let doubled = numbers.map(number => number * 2);

console.log(doubled); // [2, 4, 6]
```

### reduce

Combines all elements into a single value.

```javascript
let numbers = [10, 20, 30];

let total = numbers.reduce((sum, number) => sum + number, 0);

console.log(total); // 60
```

### sort

Sorts the elements of an array.

```javascript
let numbers = [30, 10, 20];

numbers.sort((a, b) => a - b);

console.log(numbers); // [10, 20, 30]
```
`forEach`, `filter`, `map`, and `reduce` do not modify the original array.  
`sort` modifies the original array.

## Method Chaining

Multiple array methods can be used together.

```javascript
let result = numbers
    .filter(n => n > 1)
    .map(n => n * 2);

console.log(result);
```
<br>

# Popular String Utility Methods

Strings are **immutable**, so these methods do not change the original string.

## `toUpperCase()`

Converts the string to uppercase.

```javascript
let name = "santosh";

console.log(name.toUpperCase()); // "SANTOSH"
```

## `toLowerCase()`

Converts the string to lowercase.

```javascript
let name = "SANTOSH";

console.log(name.toLowerCase()); // "santosh"
```

## `trim()`

Removes spaces from the beginning and end.

```javascript
let name = "  Santosh  ";

console.log(name.trim()); // "Santosh"
```

## `includes()`

Checks whether a string contains a value.

```javascript
let text = "Hello World";

console.log(text.includes("World")); // true
```

## `indexOf()`

Returns the position of the first occurrence.

```javascript
let text = "Hello World";

console.log(text.indexOf("World")); // 6
```

## `slice()`

Returns a part of a string.

```javascript
let text = "JavaScript";

console.log(text.slice(0, 4)); // "Java"
```

## `replace()`

Replaces the first matching value.

```javascript
let text = "Hello World";

console.log(text.replace("World", "JavaScript"));
// "Hello JavaScript"
```

## `split()`

Converts a string into an array.

```javascript
let text = "JavaScript is easy";

console.log(text.split(" "));
// ["JavaScript", "is", "easy"]
```

## `charAt()`

Returns the character at a given position.

```javascript
let name = "Santosh";

console.log(name.charAt(0)); // "S"
```

## `startsWith()`

Checks whether a string starts with a value.

```javascript
let text = "JavaScript";

console.log(text.startsWith("Java")); // true
```

## `endsWith()`

Checks whether a string ends with a value.

```javascript
let text = "JavaScript";

console.log(text.endsWith("Script")); // true
```

## `concat()`

Joins strings together.

```javascript
let firstName = "Santosh";
let lastName = "Gurkhe";

console.log(firstName.concat(" ", lastName));
// "Santosh Gurkhe"
```

## `substring()`

Returns a part of a string.

```javascript
let text = "JavaScript";

console.log(text.substring(0, 4)); // "Java"
```

## `repeat()`

Repeats a string a given number of times.

```javascript
let text = "Hi ";

console.log(text.repeat(3)); // "Hi Hi Hi "
```

## `replaceAll()`

Replaces all matching values.

```javascript
let text = "cat cat cat";

console.log(text.replaceAll("cat", "dog"));
// "dog dog dog"
```
<br>

# Popular Object Utility Methods

Object methods are used to create, access, copy, and work with object data.

## `Object.keys()`

Returns an array of object keys.

```javascript
let person = { name: "Santosh", age: 22 };

console.log(Object.keys(person));
// ["name", "age"]
```

**Immutable** — does not change the object.

## `Object.values()`

Returns an array of object values.

```javascript
let person = { name: "Santosh", age: 22 };

console.log(Object.values(person));
// ["Santosh", 22]
```

**Immutable**

## `Object.entries()`

Returns key-value pairs as arrays.

```javascript
let person = { name: "Santosh", age: 22 };

console.log(Object.entries(person));
// [["name", "Santosh"], ["age", 22]]
```

**Immutable**

## `Object.assign()`

Copies properties from one object to another.

```javascript
let person = { name: "Santosh" };
let details = { age: 22 };

Object.assign(person, details);

console.log(person);
// { name: "Santosh", age: 22 }
```

**Mutable** — changes the target object.

## `Object.hasOwn()`

Checks whether an object has a specific property.

```javascript
let person = { name: "Santosh" };

console.log(Object.hasOwn(person, "name"));
// true
```

**Immutable**

## `Object.create()`

Creates a new object using another object as its prototype.

```javascript
let person = {
    greet() {
        console.log("Hello");
    }
};

let user = Object.create(person);

user.greet(); // Hello
```

**Immutable** — creates a new object.

## `Object.freeze()`

Prevents changes to an object.

```javascript
let person = { name: "Santosh" };

Object.freeze(person);

person.name = "Rahul";

console.log(person.name); // "Santosh"
```

**Mutates the object's state by making it non-modifiable.**

## `Object.fromEntries()`

Creates an object from key-value pairs.

```javascript
let entries = [["name", "Santosh"], ["age", 22]];

let person = Object.fromEntries(entries);

console.log(person);
// { name: "Santosh", age: 22 }
```

**Immutable** — creates a new object.
