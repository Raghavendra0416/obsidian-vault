### 37. What are hooks?
Ans:
Definition:
Hooks are special functions in React that allow functional components to use features like state, lifecycle methods, and other React capabilities — without needing to write a class component.

Uses:
Hooks make code simpler, more readable and it also allows reusing logic across components and hooks helps in avoiding issues like "this" keyword confusion.

History:
Before Hooks, if you wanted to manage state or use lifecycle methods, we need to use class components which is complex and hard to reuse. Hooks solved that problem.

Most commonly used Hooks are:
- **`useState`** — Used to manage state in a functional component. For example, tracking a counter value or form input.
- **`useEffect`** — Used to perform side effects like API calls, subscriptions, or DOM manipulation.
- **`useContext`** — Used to share data globally without prop drilling.

Other hooks that we might also use are:
- `useRef`
- `useCallback`
- `useReducer`
- Custom hooks

**Rules of Hooks:**
1. We need call hooks only at the **top level** — not inside loops, conditions, or nested functions.
2. Hooks can only be used in:
	- Functional components
	- Custom hooks

----
### 38. What are the react-router methods?
Ans:
React Router provides methods and components that help us handle navigation and routing in a React single-page application without reloading the page.

Commonly used Methods:

	useNavigate ||  ||  useSearchParams  ||  useParams ||  useLocation || useMatch 

1. `useNavigate()`:
	-  `useNavigate()` is used for navigation between the components and used during form submission or login.

2.  `useSearchParams()`:
	- Used to **read and update query parameters** in link and used during filtering and sorting.

3. `useParams()`:
	- Used to **read dynamic route parameters** from the URL and used when we need to access values like `userId` or `productId` from the URL.

4. `useLocation()`:
	- Used to get information about current URL and pass the data between routes.

5. `useMatch()`:
	- Used to Check whether the current URL matches a specific path.

Most used Components:

	BrowserRouter  ||  Routes & Route  ||  Link & NavLink  || Outlet

1. `<BrowserRouter>`
	- Wraps the entire application
	- Enables routing using browser history API

2. `<Routes>` and `<Route>`
	- Define the routing configuration

3. `<Link>` and `<NavLink>`
	- Used for navigation **without page reload**

4. `<Outlet>`
	- Used for **nested routes**

### 39. How does `useEffect's` behavior change with its dependency array?
Ans:
**`useEffect` runs at different times depending on what we pass in its dependency array.**  
The dependency array tells React **when the effect should run again**.

Different scenarios in `useEffect`:

1️⃣ No dependency array
```Javascript
useEffect(() => {
   console.log("Effect runs"); 
});
```
**Behavior:**
If you **don't provide a dependency array at all**, the effect runs after **every single render** -- including the initial render and any re-renders caused by state or prop changes. This can lead to performance issues and infinite loops if not careful.

Use case:
- Rarely used
- Logging or debugging


2️⃣ Empty dependency array `[]`
```JavaScript
useEffect(() => {   
	fetchData(); 
}, []);
```
**Behavior:**
If dependency array empty, React runs the effect **only one time** when the component first appears (`i.e` mounts).

**Use case:**
- API calls
- Initial setup
- Subscriptions

3️⃣ Dependency array with values `[value]`

```Javascript
useEffect(() => {
   console.log(count); 
}, [count]);
```
**Behavior:**
- After the **initial render**, AND
- Whenever **any of the dependencies change.**

**Use case:**
- Reacting to specific state or prop changes
- Conditional API calls


4️⃣ Multiple dependencies `[a, b]`
```javaScript
useEffect(() => {
   doSomething(); 
}, [a, b]);
```

**Behavior:**
- Runs when **any one** of the dependencies changes


and Cleanup function is very important:

```Javascript
useEffect(() => {
  const id = setInterval(() => {}, 1000);

  return () => {
    clearInterval(id);
  };
}, []);
```
**Cleanup runs:**
- Before the effect re-runs
- When the component unmounts

**Use case:**
- Clearing timers
- Removing event listeners
- Canceling subscriptions

-------
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
### 42. What does "debouncing" mean, and how can you implement it in React?
Ans:
**Debouncing is a technique used to limit how often a function is executed.**  
It ensures that a function runs **only after a specified delay**, _after the user has stopped triggering the event_.

Why debouncing is needed:
Without debouncing:
- Function runs on **every keystroke** 
- Too many API calls during typing
- Poor performance with window resize and scroll events

With debouncing:
- Function runs **once after user stops typing**
- Reduced API calls
- Better user experience

We can implement debouncing in React by using `useEffect` with `setTimeout` and a cleanup function.

When a value (like search input) changes:
1. We start a timer using `setTimeout`
2. If the value changes again before the delay ends, we clear the previous timer
3. The function runs only after the user stops typing for the given delay

The cleanup function inside `useEffect` ensures the previous timer is cleared, which is what creates the debounce behavior.

Extra Info:
Debouncing vs Throttling

|Debouncing|Throttling|
|---|---|
|Runs after delay|Runs at fixed intervals|
|Waits for pause|Runs continuously|
|Search input|Scroll, resize|

---
### 43. Explain the concept of ‘Lifting State Up’ in React.
Ans:
**Lifting State Up** means moving state from a child component to a **parent component** so that multiple child components can share and synchronize that state.

Why Do We Need It and how do we do it?
React has **one-way data flow** (data flows from parent to child via props).When two sibling components need to share data, they can't directly communicate with each other. The solution is to lift the state to their parent, which can then pass it down to both children.

When to Use Lifting State Up?
Use it when:
- Multiple components need the same state
- Sibling components need to stay in sync
- A child needs to update state that affects other components
- You need a single source of truth for data

Real World example:
- Temperature Converter
- Shopping Cart
- Form with multiple inputs


### 44. How many ways to create an object in JavaScript?
Answer:
There are **6 main ways:**
1. Object Literal
2. Using `new Object()`
3. Constructor Function
4. ES6 Class (We use Class)
5. `Object.create()`
6. Factory Function
7. `Object.assign()` and Spread Operator -> Used for cloning + merging & Not primary creation method, but still valid

In JavaScript, objects can be created in multiple ways, but the most common ones are object literal, using the Object constructor, constructor functions, ES6 classes, `Object.create()`, and factory functions.

The simplest and most widely used method is the object literal, where we directly define key-value pairs inside curly braces. Another way is using the built-in Object constructor with the `new` keyword, although this is rarely used in modern JavaScript.

Before ES6, constructor functions were commonly used to create multiple objects with similar properties, where the `new` keyword helps in creating a new instance and binding `this`. ES6 introduced classes, which are a cleaner and more readable way to achieve the same functionality as constructor functions and are now preferred in modern development.

JavaScript also provides Object.create(), which allows us to create an object by explicitly setting its prototype, giving more control over inheritance. In addition, factory functions can be used to create and return objects without using `new` or `this`, making them simpler and avoiding common mistakes.