# How JavaScript Executes Code

JavaScript code is executed by the JavaScript Engine.

* The engine creates a Global Execution Context first.
* JavaScript executes the code step by step.
* When a function is called, a Function Execution Context is created.
* The function is added to the Call Stack.
* After the function finishes, it is removed from the Call Stack.
* When all code finishes, the Call Stack becomes empty.

## Simple Flow

```text
JavaScript Code
      ↓
JavaScript Engine
      ↓
Execution Context
      ↓
Call Stack
      ↓
Execute Code
```

* Execution Context → Environment where JavaScript code runs.
* Call Stack → Keeps track of functions being executed.
* JavaScript Engine → Executes JavaScript code.

<br>

# Synchronous vs Asynchronous JavaScript

## Synchronous

Synchronous code runs one task at a time and waits for each task to finish.

```javascript
console.log("Task 1");
console.log("Task 2");
console.log("Task 3");
```

Output:

```text
Task 1
Task 2
Task 3
```

## Asynchronous

Asynchronous code can start a task and continue with other code without waiting for it to finish.

```javascript
console.log("Task 1");

setTimeout(() => {
    console.log("Task 2");
}, 2000);

console.log("Task 3");
```

Output:

```text
Task 1
Task 3
Task 2
```

## Difference

```text
Synchronous
Task 1 -> wait -> Task 2 -> wait -> Task 3

Asynchronous
Task 1 -> start Task 2 -> Task 3
                  ↓
              Task 2 later
```

* Synchronous → waits for the current task to finish.
* Asynchronous → continues the next code without waiting.

<br>

# Ways to Make Code Asynchronous in JavaScript

JavaScript can handle asynchronous work mainly using these approaches.

## 1. Callbacks

A callback is a function that runs after an asynchronous task is completed.

```js
setTimeout(() => {
    console.log("Task completed");
}, 2000);

console.log("Next task");
```

Output:

```text
Next task
Task completed
```

## 2. Timers

`setTimeout()` and `setInterval()` can schedule code to run later.

```js
setTimeout(() => {
    console.log("Hello");
}, 2000);
```

The browser handles the timer, so JavaScript can continue executing other code.

## 3. Promises

A Promise represents the future result of an asynchronous operation.

```js
const promise = new Promise((resolve) => {
    setTimeout(() => {
        resolve("Task completed");
    }, 2000);
});

promise.then((result) => {
    console.log(result);
});
```

## 4. async/await

`async/await` is a simpler way to work with Promises.

```js
async function getData() {
    const result = await promise;
    console.log(result);
}

getData();
```
# Web Browser APIs

Web Browser APIs are features provided by the browser that JavaScript can use to perform tasks outside the JavaScript engine.

## Examples

* `setTimeout()` → runs code after a delay
* `setInterval()` → runs code repeatedly
* `fetch()` → gets data from a server
* DOM APIs → work with HTML elements
* Events → handle user actions like `click`
* `localStorage` → stores data in the browser

# Event Loop

Event Loop helps JavaScript handle asynchronous tasks.

It checks if the Call Stack is empty and then moves the waiting callback to the Call Stack.

```text
Call Stack
    ↓
Web APIs
    ↓
Queue
    ↓
Event Loop
    ↓
Call Stack
```

# Callback Hell

Callback Hell happens when we have many callbacks inside other callbacks.

```js
task1(() => {
    task2(() => {
        task3(() => {
            console.log("Done");
        });
    });
});
```

It makes the code difficult to read, debug, and maintain.

# Inversion of Control

Inversion of Control means giving our callback to another function and letting that function decide when to execute it.

```js
setTimeout(() => {
    console.log("Hello");
}, 2000);
```

Here, `setTimeout()` controls when our callback will run.


