# What is a Promise?

A Promise is an object that represents the result of an asynchronous operation.

A Promise has three states:

* Pending → operation is still running
* Fulfilled → operation completed successfully
* Rejected → operation failed

# How to Create a Promise?

We can create a Promise using the `Promise` constructor.

```js
const promise = new Promise((resolve, reject) => {
    resolve("Success");
});
```

* `resolve()` → success
* `reject()` → failure

# Promise States

```text
Pending
   ↓
Fulfilled

or

Pending
   ↓
Rejected
```

Once a Promise is fulfilled or rejected, its state cannot be changed.

# How to Consume an Existing Promise?

We can consume a Promise using `.then()` and `.catch()`.

```js
promise
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);
    });
```

* `.then()` → handles success
* `.catch()` → handles error
