`async–await` is a JavaScript feature used to handle asynchronous operations in a clean and readable way.

It is built on top of Promises and allows us to write  asynchronous code like fetching data from an API that looks like synchronous, without blocking the main thread.

**Key Points**
- `async` is used before a function and **always returns a Promise**
- `await` is used inside an async function to **wait for a Promise to resolve or reject**
- It improves **readability**, **debugging**, and **error handling**

##### Why do we need async–await?
Before async–await:
- Callbacks → **callback hell**
- Promises with `.then()` → **hard to read for multiple steps**
Async–await solves:
- Better **readability**
- Easier **error handling**
- Code looks **blocking**, but it is **non-blocking**


##### What is `async`?
- `async` is used **before a function**
- It **always returns a Promise**
- If you return a value → JS wraps it in a resolved Promise
- If you throw an error → Promise is rejected
Example:
```JavaScript
async function getData() {
  return "Hello";
}

// Equivalent to:
Promise.resolve("Hello");
```
##### What is `await`?
- `await` is used **inside an async function**
- It **pauses execution** until the Promise resolves or rejects
- It does **NOT block the main thread**

```JavaScript
let result = await somePromise;
```
##### What actually happens step-by-step:
1. When JavaScript encounters `await` and `await` encounters a Promise
2. The async function is **paused**
3. The call stack is **released**
4. Main execution continues
5. Promise resolves/rejects
6. Remaining async code is placed in the **microtask queue**
7. Event loop pushes it back to the call stack
8. The **event loop** manages this process, so JavaScript remains non-blocking
When an async function resumes after `await`, it runs via the microtask queue and does not block or affect the main execution.

**How it works**
- When JavaScript encounters `await`, it:
    1. Pauses the execution of that async function  
    2. Releases the call stack
    3. Resumes execution once the Promise settles
- The **event loop** manages this process, so JavaScript remains non-blocking

##### Why it does NOT affect main execution
- JavaScript has **one main thread**
- `await` **pauses only the current async function**
- The **call stack is freed**
- Other synchronous code keeps executing
- When the Promise settles, the remaining code is queued as a **microtask**

##### Important rules 
1. `await` works **only inside async functions**
2. `async` functions **always return Promises**
3. Multiple `await`s run **sequentially**
4. Use `Promise.all()` for **parallel execution**

**Key Concepts to Mention (Cheat Sheet)**
If you get stuck, just remember to hit these **4 keywords** in your answer:
1. **Syntactic Sugar:** It's just a wrapper around Promises.
2. **Readability:** It replaces `.then()` chains with flat code.
3. **Non-blocking:** It pauses the function, not the whole application.
4. **Try/Catch:** It uses standard error handling.

###### async–await vs Promises

| async–await          | Promises         |
| -------------------- | ---------------- |
| More readable        | Less readable    |
| try–catch for errors | .catch()         |
| Easier debugging     | Harder debugging |

##### Examples:

Basic Example:
```JavaScript
function fetchData() {
  return new Promise(resolve => {
    setTimeout(() => resolve("Data received"), 2000);
  });
}

async function showData() {
  const data = await fetchData();
  console.log(data);
}

showData();
```
Basic Example:
```JavaScript
console.log("Start");

async function test() {
  console.log("Inside async");
  await Promise.resolve();
  console.log("Resumed async");
}

test();
console.log("End");

Output:
Start
Inside async
End
Resumed async
```

Error handling with async–await
Use **try–catch** (very important for interviews)

```JavaScript
async function getUser() {
  try {
    const response = await fetch("/api/user");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error:", error);
  }
}
```

#### **Common Interview Questions & Answers**
##### **1. Why use Async/Await over `.then()` chains?**
- **Readability:** It avoids "callback hell" or long Promise chains, making the code look cleaner and easier to read (top-to-bottom flow).
- **Error Handling:** You can use standard `try/catch` blocks for error handling, which is more intuitive than `.catch()` methods.
- **Debugging:** Debugging is easier because `await` allows you to step over asynchronous calls as if they were synchronous lines of code.

##### **2. Can you use `await` outside of an `async` function?**
- **Historically No:** In standard function definitions, `await` must be inside a function marked with `async`.
- **Top-level Await:** In modern modules (ES Modules), you _can_ use `await` at the top level of a module without a wrapper function, but this depends on the environment (supported in newer Node.js versions and modern browsers).

##### **3. What happens if you forget the `await` keyword?**
If you forget `await`, the function will **not wait** for the Promise to resolve. It will immediately return the Promise object itself rather than the result. This often leads to bugs where code tries to access data that hasn't arrived yet.

##### **4. How do you handle errors in Async/Await?**
Since `.catch()` is not typically used with `await`, you wrap the code in a **`try...catch`** block.
```JavaScript
async function safeFetch() {
  try {
    const data = await someAsyncCall();
  } catch (err) {
    console.log("Error caught:", err);
  }
}
```

##### **5. Does `async/await` block the main thread?**
**No.** It only "pauses" the execution _inside_ that specific `async` function. The rest of the JavaScript runtime (the main thread) continues to handle user events, other scripts, and UI rendering. It is non-blocking.

###### **6. How do you run multiple promises in parallel with Async/Await?**
If you `await` two calls one after another, they run sequentially (slow). To run them in parallel, use **`Promise.all()`**.

**Sequential (Slow):**
```JavaScript
const user = await getUser();       // Waits 2 sec
const orders = await getOrders();   // Waits 2 sec
// Total time: 4 seconds
```
**Parallel (Fast):**
```JavaScript
const [user, orders] = await Promise.all([getUser(), getOrders()]);
// Total time: 2 seconds (both start at the same time)
```

![[Pasted image 20251221193919.png]]

![[Pasted image 20251221193936.png]]