A **Promise** is an object in JavaScript that represents the **eventual completion or failure** of an asynchronous operation.

Promises help us avoid "callback hell" and make asynchronous code more readable with `.then()` and `.catch()` or with `async/await`.

A Promise can be in **three states**:
- **Pending** – initial state, operation not finished
- **Fulfilled** – operation completed successfully
- **Rejected** – operation failed with an error

JavaScript provides multiple promise APIs to handle **multiple promises together**:
- `Promise.all()`
- **`Promise.allSettled()`**
- `Promise.race()`
- `Promise.any()`

What is `Promise.allSettled()`?
`Promise.allSettled()` waits for all promises to complete, regardless of whether they succeed or fail.

`Promise.allSettled()` will never rejects for a promise and will return array as results. 

The Return values are array of objects, where each object has:
- **`status`** — Either `"fulfilled"` or `"rejected"`
- **`value`** — The fulfilled value (if status is fulfilled)
- **`reason`** — The rejection reason (if status is rejected)

Real scenarios where we use `Promise.allSettled()` is when calling multiple API's and logging or monitoring async operations and also in batch operations where failure of one task should not cancel others.