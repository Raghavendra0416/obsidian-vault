
What is a Promise?
A **Promise** in JavaScript is an **object** that represents the eventual **completion or failure of an asynchronous operation** and its resulting value.

It acts as a placeholder for a value that will be available **now, later, or never**.

**Type of Promise**

**Promise is an object**

```js
typeof Promise.resolve(); // "object"
```

More specifically:
- It is an **instance of the built-in `Promise` class**
- Returned by async operations like API calls, timers, file reads, etc.

Example:
Think of it like a **receipt or a buzzer at a restaurant**:
- You place an order (start an async task).
- They give you a buzzer (the Promise).
- The food isn't ready yet (**Pending**).
- Eventually, the buzzer rings, and you get your food (**Resolved/Fulfilled**).
- Or, they tell you they ran out of ingredients (**Rejected**).

**The Three States of a Promise:**
1. **Pending:** The initial state. The operation is still going on (neither finished nor failed).
2. **Fulfilled (Resolved):** The operation completed successfully, and the promise now has a _value_.
3. **Rejected:** The operation failed, and the promise now has a _reason_ (error).

**Promise States**
A Promise can be in **one of three states**:
1. **Pending**
    - Initial state
    - Operation is not completed yet
2. **Fulfilled**
    - Operation completed successfully
    - Promise has a result value
3. **Rejected**
    - Operation failed
    - Promise has an error reason


Once a Promise is **fulfilled or rejected**, it is **settled** and cannot change state again.

---

> "Promises involve two main parts:
> 
> 1. **Producing (Creation):** The code that creates the Promise instance and defines the asynchronous logic (calling `resolve` or `reject`).
> 2. **Consuming (Handling):** The code that waits for the Promise and handles the result using `.then()`, `.catch()`, or `async/await`."

When working with Promises in JavaScript, there are always two distinct sides to the process:
##### The Producing Code ("Creation")
This is the code that **creates** the Promise. It performs the actual asynchronous task (like requesting data from a server, reading a file, or setting a timer).1
- **What it does:** It creates the `new Promise()` and is responsible for calling `resolve()` when it succeeds or `reject()` when it fails.
- **Analogy:** The chef in the kitchen cooking the food.

```JavaScript
// PRODUCING / CREATION
const myPromise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("Operation Successful!"); // Fulfills the promise
    } else {
        reject("Operation Failed!");      // Rejects the promise
    }
});
```
##### The Consuming Code ("Handling")
This is the code that **uses** the Promise. It waits for the Promise to finish and then decides what to do with the result.
- **What it does:** It uses `.then()`, `.catch()`, or `async/await` to react to the outcome.
- **Analogy:** The customer waiting at the table to eat the food (or complain if it's burnt).

```JavaScript
// CONSUMING / HANDLING
myPromise
    .then((message) => {
        console.log(message); // Handles success
    })
    .catch((error) => {
        console.error(error); // Handles error
    });
```

**Basic Example**
```js
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});
```

**How to consume a Promise**
```js
promise
  .then(result => console.log(result))
  .catch(error => console.log(error))
  .finally(() => console.log("Done"));
```

----

Promise: Creation (Producing) vs Handling (Consuming) 

Core interview statement

> **A Promise has two distinct sides:**
> 
> 1. **Creation (Producing the Promise)**
> 2. **Handling (Consuming the Promise)**


##### Creation / Producing a Promise
This is where the **asynchronous operation is defined**.
- Done using the **Promise constructor**
- Takes an **executor function**
- Executor receives two callbacks:
    - `resolve()` → success   
    - `reject()` → failure
- Executor runs **immediately**

```js
const promise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve("Task completed");
  } else {
    reject("Task failed");
  }
});
```


##### Handling / Consuming a Promise
This is where the **result is used**.
- Done using:
    - `.then()` → success
    - `.catch()` → error
    - `.finally()` → always runs
- Can be done **anywhere** the promise is available

```js
promise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  })
  .finally(() => {
    console.log("Done");
  });
```
Visual mapping:

|Side|Responsibility|Example|
|---|---|---|
|Creation|Defines async work|API call|
|Handling|Uses the result|UI update|

Important points:
- Producer and consumer are **independent**
- Promise is created **once**
- Multiple consumers can handle the **same Promise**
- State changes only **once**

---

**Promise vs async–await (relation)**
- `async–await` is **syntactic sugar over Promises**
- `await` waits for a Promise to settle
- Under the hood, it still uses Promises

Real Life Examples:
- Ordering food at a restaurant
- Online payment

Why promises are useful in real applications
- API calls (`fetch`)
- File upload/download
- Database operations
- Payment gateways

