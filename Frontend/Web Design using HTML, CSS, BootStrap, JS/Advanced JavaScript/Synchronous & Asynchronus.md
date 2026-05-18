**The Core Difference**
- **Synchronous:** "One thing at a time." The code runs in sequence. The program waits for the current line to finish before moving to the next line. It is **blocking**.
- **Asynchronous:** "Multitasking." The code starts a task and moves to the next line immediately without waiting for the first one to finish. It is **non-blocking**.
							| OR |
- **Synchronous functions** execute **line by line**, and each operation **blocks** the next one until it completes.    
- **Asynchronous functions** start an operation and **do not block** the execution; results are handled later via callbacks, Promises, or `async–await`.

##### Core differences

| Feature         | Synchronous           | Asynchronous                    |
| --------------- | --------------------- | ------------------------------- |
| Execution       | Sequential            | Non-blocking                    |
| Waiting         | Blocks next line      | Does not block                  |
| Call stack      | Occupies stack        | Releases stack                  |
| Performance     | Slower for I/O        | Better for I/O                  |
| User experience | UI can freeze         | UI remains responsive           |
| Examples        | Normal function calls | `setTimeout`, `fetch`, Promises |

| **Feature**        | **Synchronous (Sync)**                          | **Asynchronous (Async)**                                            |
| ------------------ | ----------------------------------------------- | ------------------------------------------------------------------- |
| **Execution Flow** | Sequential (Line by line).                      | Concurrent (Skips waits).                                           |
| **Blocking?**      | **Yes.** Stops the whole program while waiting. | **No.** The program continues running other code.                   |
| **Wait Time**      | You wait for the result immediately.            | You get a "promise" (callback) that the result will come later.     |
| **Example**        | A phone call (you must hold the line).          | A text message (you can do other things while waiting for a reply). |
| **Use Case**       | Simple math, logic, variable assignments.       | API calls, file reading, timers (`setTimeout`).3                    |

##### Simple examples:
Synchronous
```js
console.log("Start");
console.log("Middle");
console.log("End");
```
**Output**
```
Start
Middle
End
```

Asynchronous
```js
console.log("Start");

setTimeout(() => {
  console.log("Async task");
}, 0);

console.log("End");
```
**Output**
```
Start
End
Async task
```

How JavaScript handles async internally 
- JavaScript is **single-threaded**
- Asynchronous tasks are handled using:
    - Web APIs
    - Event Loop
    - Callback / Microtask queues
- This allows **non-blocking behavior**

Real-life analogy
- **Synchronous:** Standing in a queue, waiting for your turn
- **Asynchronous:** Ordering food and sitting while it’s prepared

When to use which?
- **Synchronous:** Simple, quick operations
- **Asynchronous:** API calls, file operations, timers, DB access
