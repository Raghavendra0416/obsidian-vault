### 32. What are Event Listeners?
Ans:
An **event listener** is a function in JavaScript that waits for a specific event to occur on an HTML element and when the event occurs the event listener executes callback function.

`addEventListener` is preferred because it allows multiple handlers on the same event, separates HTML from JavaScript, and provides more control through the options parameter.

**Common Events**: browser events, click, double click, mouse enter, mouse leave, key down, key up, submit, focus, blur, change, load, scroll, resize.

Syntax:
```JavaScript
element.addEventListener(event, callbackFunction, options);
```

We can pass an event object to the callback function and this event object will contain information regarding the event that occurred. The event object specifies information like target element, mouse coordinates, key pressed, etc..  

`e.target` is used to identify the clicked child

Events propagate through the DOM in two phases. 
1. Capturing: target --> root
2. Bubbling: root --> target (used by Default in event listeners)

You can specify capturing with the third parameter: `addEventListener('click', handler, true)`.

We can use `removeEventListener()` to remove events, with this function we can prevent memory leaks.

---
### 33. What is an event loop? How does JavaScript event loop work and how does it contribute to the language's asynchronous nature? Can you explain the concept of the call stack and the message queue in this context?
Answer:
###### What is an event loop? 
JavaScript is single-threaded, meaning it executes one piece of code at a time on the main thread. The **event loop** is the mechanism that lets JavaScript handle **asynchronous operations** like timers, network requests, and user interactions without blocking the main thread.

###### How does JavaScript event loop work?
The event loop keeps checking the call stack, and whenever it’s empty, it runs queued microtasks first, then queued macro tasks, by moving them onto the stack.”

###### How does it contribute to the language's asynchronous nature?
(Question understanding:
Even though JavaScript runs your code **one line at a time on a single call stack**, how is it still able to do things like **timers, network requests, and click handlers** without freezing the program and while continuing to run other code?)
Answer:
The event loop makes JavaScript asynchronous by letting the runtime finish work in the background, queue the callbacks, and then run those callbacks only when the call stack is free, so the main thread doesn’t block.

###### Can you explain the concept of the call stack and the message queue in this context?
The **call stack** is where JavaScript keeps track of the functions that are currently executing. Every time a function is called, it gets pushed onto the stack, and when it finishes, it gets popped off. JavaScript executes whatever is on top of the stack, and if the stack is busy, no other JavaScript code can run on the main thread.

 Callbacks from asynchronous operations wait until JavaScript is ready to execute them in Macro task queue.
For example, callbacks from `setTimeout`,  other browser events are placed in this queue once they’re ready.
The **event loop** constantly checks whether the call stack is empty, and when it is, it takes the next callback from the Macro task queue and pushes it onto the call stack to run.

So the call stack is what’s running now, and the **queues (microtask queue and macrotask/message queue)** hold callbacks waiting to run when the stack is free.

---
### 34. How to console params and query in JavaScript?
Answer:

In a URL, there are two common kinds of inputs: **query parameters** and **path parameters**.

**Query parameters** are the key–value pairs that come after a question mark `?`. For example, in `...?city=goa&id=12`, `city` and `id` are query parameters.
We can read Query parameters using `window.location.search`, and then parse them using `URLSearchParams`. Through parsing, we can log a specific query parameter value like `id` or `city` and `URLSearchParams` can also loop over all query params and log key–value pairs.

**Path parameters** are values that are part of the URL path itself. For example, `/adventures/12` — here `12` is usually the path parameter.
We can read path parameter using `window.location.pathname` and split it by `/`, and take the part we need and console log it.

We can use Express  functions to log them:
`req.query` gives all **query parameters**
`req.params` gives all **route/path parameters**

Once we extract them, we simply use `console.log()` to print the value or the full object.
Query params are optional filters, while path params usually identify a specific resource in the route.”

---
### 35. What is Event Bubbling in JavaScript?
Answer:
**Event bubbling** is a concept in JavaScript where an event starts from the **target element** and then **propagates upward** through its parent elements in the DOM tree — so it bubbles from **child to parent**.

Event propagation happens in **three phases**: **capturing** (top to bottom), **target**, and **bubbling** (bottom to top). Event handlers uses in the bubbling by default, but we can enable capturing using `addEventListener` with `{ capture: true }`.

Bubbling is useful for **event delegation** — instead of adding listeners to many child elements, we attach one listener to the parent and use `event.target` to know which child was interacted with. This improves performance and keeps the code easier to maintain,
Examples for Event bubbling are **to-do list** or an **e-commerce product list**.

If we don’t want the event to bubble up, we use `event.stopPropagation()`.

---
### 36. Describe Web Storage?
Answer:

**Web Storage** is a browser feature that lets us store data as **key–value pairs** on the user’s device. It’s mainly used to save small pieces of information so it can be reused later without needing a server call.

- Stores **strings only**. (we use `JSON.stringify()` and `JSON.parse()`)
- It’s **synchronous**, so don’t store large data because it can slow the UI.
- Not meant for sensitive data like passwords

There are **two types**:
	1. Local Storage
	2. Session Storage

Local Storage:
- Data is stored **persistently** (it stays even after closing and reopening the browser).
- Useful for things like theme preference (dark/light), language setting
Session Storage:
- Data is stored only for the **current tab/session**.
- It is cleared when the tab or browser is closed.
- Useful for temporary form data, step-by-step flows.

Common operations
- Save: `setItem(key, value)`
- Read: `getItem(key)`
- Remove one: `removeItem(key)`
- Clear all: `clear()`

FYI-
- **Web Storage** is the **overall browser feature / API** (the umbrella term).
- Under Web Storage, there are **two storage types**:
    1. **localStorage**
    2. **sessionStorage**
---
### 37. What are cookies and how are they used?
Answer:
**Cookies** are small pieces of data (key–value text) that a website stores in the user’s browser.
The browser automatically sends cookies back to the same website on every HTTP request, so the server can “remember” the user.

How cookies are used:
- A user visits a website.
- The server sends a response with a `Set-Cookie` header.
- The browser saves that cookie.
- On the next requests to that same site, the browser includes it in the `Cookie` header automatically.

Common use cases:
- Login/session management
- User preferences
- Analytics and tracking

Types:
	1. Session cookie - removed when the browser/tab session ends.
	2. Persistent cookie - has an expiration date (`Expires` / `Max-Age`) and stays longer.
	3. Security flags

Key limitations:
- Cookies are small (roughly **a few KB each**) and limited in count per site.
- They are best for **small identifiers**, not large data.

Quick comparison with Web Storage:
**Cookies** are sent to the server automatically with requests.
**localStorage/sessionStorage** are not automatically sent with requests.

---
### 38. Explain the differences between Local Storage and Session Storage.
Answer:

Local Storage:
- Persists even after closing/reopening the browser.
- Shared across tabs/windows of the same origin
- Key–value pairs stored as **strings**.
- Use Cases: Theme, language, long-term preferences
- If we store objects/arrays, we use `JSON.stringify()` while saving and `JSON.parse()` while reading.
- It is Synchronous
- Not ideal for sensitive data

Session Storage:
- Exists only for the current tab/session; cleared when the tab is closed.
- Has separate storage per tab.
- Use Cases: Multi-step forms, temporary state for that tab.
- Key–value pairs stored as **strings**
- If we store objects/arrays, we use `JSON.stringify()` while saving and `JSON.parse()` while reading.
- It is Synchronous.
- Not ideal for sensitive data

---
### 39. How many ways to create an object in JavaScript?
Answer:
In JavaScript, objects can be created in multiple ways:
There are **6 main ways:**
1. Object Literal
2. Using `new Object()`
3. Constructor Function
4. ES6 Class (We use Class)
5. `Object.create()`
6. Factory Function
7. `Object.assign()` and Spread Operator -> Used for cloning + merging & Not primary creation method, but still valid


The simplest and most widely used method is the object literal, where we directly define key-value pairs inside curly braces. 

Before ES6, constructor functions were commonly used to create multiple objects, where the `new` keyword helps in creating a new instance and binding `this`  although this is rarely used in modern JavaScript. ES6 introduced classes, which are a cleaner and more readable way to achieve the same functionality as constructor functions.

JavaScript also provides `Object.create()`, which allows us to create an object by explicitly setting its prototype, giving more control over inheritance. In addition, factory functions can be used to create and return objects without using `new` or `this`, making them simpler and avoiding common mistakes.

---
### 40. What are Promises? Explain `Promise.allSettled()` promise API with example.
Ans:
**Definition**:
A **Promise** is an object in JavaScript that represents the **eventual completion or failure** of an asynchronous operation.

Promises help us avoid "callback hell" and make asynchronous code more readable with `.then()` and `.catch()` or with `async/await`.

A Promise can be in **three states**:
- **Pending** – initial state, operation not finished
- **Fulfilled** – operation completed successfully
- **Rejected** – operation failed with an error

JavaScript provides multiple promise methods to handle **multiple promises together**:
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

Real scenarios where we use `Promise.allSettled()` is when calling multiple API's  where failure of one task should not cancel others and logging or monitoring async operations.

```JavaScript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success");
  }, 1000);
});
```

---
### 41. How to manage 3 Parallel API calls?
Ans:
We can manage 3 parallel API calls in JavaScript by triggering all requests at the same time and then handling their results together.

The most common and recommended way is using **`Promise.all()`**, and depending on the requirement, we can also use **`Promise.allSettled()`**.

`Promise.all():`
We use `Promise.all()` when all APIs must succeed.
Behavior
- All 3 APIs are called **in parallel**
- If **any one fails**, the entire promise rejects
- Faster than sequential calls.

**`Promise.all()` returns a single Promise.**  
That returned Promise:
- **resolves** with an **array of resolved values**
- **rejects immediately** if **any one** of the input promises rejects


`Promise.allSettled():`
We use `Promise.allSettled()` when APIs are independent. 
`Promise.allSettled()` waits for all promises to complete, regardless of whether they succeed or fail.
`Promise.allSettled()` will never rejects for a promise and will return array as results. 

The Return values are array of objects, where each object has:
- **`status`** — Either `"fulfilled"` or `"rejected"`
- **`value`** — The fulfilled value (if status is fulfilled)
- **`reason`** — The rejection reason (if status is rejected)

---
### 42. What is a Constructor?
Ans:
A **constructor** is a special function that is used to **create and initialize objects**.
It like a blueprint for making multiple similar objects.

The Classic Way:
Before ES6, constructors were just regular functions used with the `new` keyword:

```JS
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const user1 = new Person("Alice", 25);
const user2 = new Person("Bob", 30);

console.log(user1.name); // Alice
```

- `this` refers to the new object being created.
- `new` does 4 things:
	- Creates a new empty object
	- Sets `this` to that object
	- Links it to the function's prototype
	- Returns the object

The Modern Way:
With ES6, constructors are defined inside classes:
and Each class can have only **one constructor**

```JS
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const user = new Person("Alice", 25);
```

- The `constructor()` method runs automatically when you create an object with `new`
- Class groups everything in one place → easier to read & maintain
- Classes provide cleaner syntax, better readability, built-in support for inheritance, and avoid common pitfalls like incorrect `this` binding.
- Classes always run in **strict mode** where it Prevents silent bugs.
---
### 43. What is the 'this' keyword in JavaScript?
Ans:
`this` is a keyword in JavaScript that refers to the object which is currently executing the function, The important thing to understand is that the value of `this` is not fixed — it depends on how the function is called.

For example, in a regular function, `this` refers to the global object, which is `window` in browsers, or `undefined` in strict mode.

When a function is called as a method of an object, `this` refers to that object.
In constructor functions or classes, when we use the `new` keyword, `this` refers to the newly created object.

Arrow functions are a special case — they do not have their own `this`. Instead, they inherit `this` from their surrounding scope.

We can also explicitly control the value of `this` using methods like `call()`, `apply()`, and `bind()`.

###### Extra Information:
In methods → refers to the **object**
In constructors → refers to the **new object**
In arrow functions → **inherits from parent scope**
Can be controlled using:
    - `call()`
    - `apply()`
    - `bind()`

Different Cases of `this`:
1. Global Scope  -- Refers to browser → `window` but in strict mode → `undefined` 
2. Inside a Regular Function -- Refers to browser → `window` but in strict mode → `undefined` 
3. Inside an Object Method -- refers to the **object calling the method**
4. Inside a Constructor -- refers to the **newly created object**
5. **Arrow Functions** -- Arrow functions **do NOT have their own `this`** So, They take `this` from the **surrounding scope**.

---
### 44. 