### 30. What are Event Listeners?
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
### 31. What is an event loop? How does JavaScript event loop work and how does it contribute to the language's asynchronous nature? Can you explain the concept of the call stack and the message queue in this context?
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
### 32. How to console params and query in JavaScript?
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
### 33. What is Event Bubbling in JavaScript?
Answer:
**Event bubbling** is a concept in JavaScript where an event starts from the **target element** and then **propagates upward** through its parent elements in the DOM tree — so it bubbles from **child to parent**.

Event propagation happens in **three phases**: **capturing** (top to bottom), **target**, and **bubbling** (bottom to top). Event handlers uses in the bubbling by default, but we can enable capturing using `addEventListener` with `{ capture: true }`.

Bubbling is useful for **event delegation** — instead of adding listeners to many child elements, we attach one listener to the parent and use `event.target` to know which child was interacted with. This improves performance and keeps the code easier to maintain,
Examples for Event bubbling are **to-do list** or an **e-commerce product list**.

If we don’t want the event to bubble up, we use `event.stopPropagation()`.

---
### 34. Describe Web Storage?
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
### 35. What are cookies and how are they used?
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
### 36. Explain the differences between Local Storage and Session Storage.
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