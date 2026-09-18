# Promise Chaining

Promise chaining means using multiple then methods one after another.

```js
promise
    .then((result) => {
        return result + " completed";
    })
    .then((result) => {
        console.log(result);
    });
```

The value returned from one then goes to the next then.

# Handling Errors with catch

catch is used to handle errors in a Promise.

```js
promise
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);
    });
```

If the Promise is rejected or an error occurs inside then, catch handles it.

# finally in Promise Chain

finally runs whether the Promise is fulfilled or rejected.

```js
promise
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);
    })
    .finally(() => {
        console.log("Operation finished");
    });
```

# Error in then With catch

If an error happens inside then, it can be handled by catch.

```js
promise
    .then((result) => {
        throw new Error("Something went wrong");
    })
    .catch((error) => {
        console.log(error.message);
    });
```

The error moves to the nearest catch.

# Error in then Without catch

If an error happens and there is no catch, the error is not handled.

```js
promise
    .then((result) => {
        throw new Error("Error");
    });
```

# Why Put catch Towards the End?

We can put one catch at the end to handle errors from the previous then steps.

```js
promise
    .then((result) => {
        return result + 10;
    })
    .then((result) => {
        throw new Error("Error occurred");
    })
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error.message);
    });
```

# Consuming Multiple Promises by Chaining

We can use Promise chaining when one task depends on the result of the previous task.

```js
getUser()
    .then((user) => {
        return getOrders(user.id);
    })
    .then((orders) => {
        return getPayment(orders[0].id);
    })
    .then((payment) => {
        console.log(payment);
    })
    .catch((error) => {
        console.log(error);
    });
```

Each Promise waits for the previous Promise to complete.


# Promise.all

Promise.all is used when we want to run multiple Promises together and wait for all of them to complete.

```js
Promise.all([promise1, promise2, promise3])
    .then((results) => {
        console.log(results);
    })
    .catch((error) => {
        console.log(error);
    });
```

If all Promises succeed, we get the results as an array.

If any one Promise fails, Promise.all rejects.

# Error Handling with Promises

We can use catch to handle errors in a Promise.

```js
getData()
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log(error);
    });
```

catch handles a rejected Promise and errors that happen inside then.

# Why Error Handling is Important

Error handling helps us handle failures without breaking the whole program.

For example, if a server request fails, we can show an error message instead of leaving the user without a response.

```js
getData()
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log("Failed to get data");
    });
```

# Promisify Callback-Based Async Functions

Promisify means converting a callback-based function into a Promise-based function.

For example, a callback function:

```js
setTimeout(() => {
    console.log("Done");
}, 2000);
```

We can create a Promise version:

```js
function wait() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Done");
        }, 2000);
    });
}

wait().then((result) => {
    console.log(result);
});
```

This makes the function easier to use with Promise chaining and async/await.

# Promisify fs.readFile

Node.js fs.readFile uses a callback to get the file data.

We can convert it into a Promise:

```js
const fs = require("fs");

function readFilePromise(file) {
    return new Promise((resolve, reject) => {
        fs.readFile(file, "utf8", (error, data) => {
            if (error) {
                reject(error);
            } else {
                resolve(data);
            }
        });
    });
}

readFilePromise("data.txt")
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log(error);
    });
```

Here, `resolve` is used when the file is read successfully and `reject` is used when an error occurs.


# Promise.resolve

Promise.resolve creates a fulfilled Promise with the given value.

```js
Promise.resolve("Success")
    .then((result) => {
        console.log(result);
    });
```

# Promise.reject

Promise.reject creates a rejected Promise with the given error.

```js
Promise.reject("Failed")
    .catch((error) => {
        console.log(error);
    });
```
# Promise.all

Promise.all waits for all Promises to complete.

If all succeed, it returns all results. If any one fails, the whole Promise.all fails.

```js
Promise.all([promise1, promise2, promise3])
    .then((results) => {
        console.log(results);
    })
    .catch((error) => {
        console.log(error);
    });
```

# Promise.allSettled

Promise.allSettled waits for all Promises, even if some fail.

It gives the status and result of every Promise.

```js
Promise.allSettled([promise1, promise2, promise3])
    .then((results) => {
        console.log(results);
    });
```

# Promise.any

Promise.any returns the first Promise that is fulfilled.

It ignores rejected Promises until one Promise succeeds.

```js
Promise.any([promise1, promise2, promise3])
    .then((result) => console.log(result))
    .catch((error) => console.log(error));
```

# Promise.race

Promise.race returns the result of the first Promise that settles.

It can be either fulfilled or rejected.

```js
Promise.race([promise1, promise2, promise3])
    .then((result) => console.log(result))
    .catch((error) => console.log(error));
```

