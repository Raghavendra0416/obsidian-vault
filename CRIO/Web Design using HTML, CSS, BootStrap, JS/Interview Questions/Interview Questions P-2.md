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

JavaScript is single-threaded, meaning it executes one piece of code at a time on the main thread. The **event loop** is the mechanism that lets JavaScript handle **asynchronous operations** like timers, network requests, and user interactions without blocking the main thread.

**Call stack** is where JavaScript keeps track of what function is currently running. When a function is called, it gets pushed onto the stack, and when it finishes, it’s popped off.
As long as there’s something on the call stack, JavaScript is busy, and nothing else can execute on that thread.

Next, asynchronous operations are handled outside the JavaScript engine by the environment — in the browser these are **Web APIs** like `setTimeout`, DOM events, and `fetch`.
When you start an async task, JavaScript hands it off to the environment and continues running the next lines of code.

When that async task finishes, its callback doesn’t run immediately. Instead, it gets placed into a queue. 
`Macrotask` queue** includes things like `setTimeout`, callbacks and UI event handlers.

Now the **event loop** constantly checks: “Is the call stack empty?” If it’s not empty, it waits. Once the stack becomes empty, it first executes everything in the **microtask queue**.

Event loop helps in running different tasks at a time even though it single threaded
