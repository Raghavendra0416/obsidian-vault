### 1. What are hooks?
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
### 2. What are the react-router methods?
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

### 3. How does `useEffect's` behavior change with its dependency array?
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

---
### 4. What does "debouncing" mean, and how can you implement it in React?
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
### 5. Explain the concept of ‘Lifting State Up’ in React.
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

---

### 6. What are props in React?
Ans: 
In React, props (short for properties) are used to pass data from a parent component to a child component. They are read-only, which means a child component cannot modify the props it receives.

Props help make components reusable and dynamic, because we can pass different values to the same component and render different outputs.

For example, a parent component can pass a `name` prop to a child component, and the child can use that value to display personalized content.

In functional components, props are received as a parameter, and we can also use destructuring to access them easily.

Overall, props enable one-way data flow in React, from parent to child, which helps maintain predictable and manageable code.

###### Extra Information:
**Key points to remember**
- Props = data passed from parent → child
- Props are **immutable (read-only)**
- Enable **reusability**
- Support **one-way data flow**

---
### 7. What are the advantages of using functional components over class-based components?
Ans:
Functional components are preferred over class-based components because functional components are simpler to use, easy to read and easier to maintain. They use plain JavaScript functions, so there is no need to deal with complex concepts like `this` binding or lifecycle methods in classes.

With the introduction of React Hooks like `useState` and `useEffect`, functional components can handle state and side effects, which earlier were only possible in class components.

Functional Components allows us to reuse logic through custom hooks, instead of relying on patterns like higher-order components or render props.

Functional components are generally more concise, require less boilerplate code, and are easier to test and debug. Because of these advantages, React now recommends using functional components as the standard approach.`

---
### 8. Differentiate between stateful and stateless components in React?
Ans:
In React, the main difference between stateful and stateless components is how they manage state.

Stateful components have their own state, and they can manage and update that state over time. They are used for dynamic behavior, such as handling user input, API data, or UI changes. Earlier, class components were mainly used for managing state, but now functional components can also handle state using hooks like `useState`.

Stateless components, on the other hand, do not have their own state. They simply receive data through props and render the UI based on that data.

In summary, stateful components handle logic and data, while stateless components focus on presentation.

---
### 9. Explain the difference between `useCallback` and `useMemo` hooks?
Ans: 
`useCallback` and `useMemo` are hooks in react used to improve performance by memoizing values and preventing unnecessary re-renders.

The main difference is that `useMemo` returns a memoized value, whereas `useCallback` returns a memoized function.

`useMemo` is used when we have expensive calculations and want to avoid recalculating them unless dependencies change.

`useCallback` is used to prevent a function from being recreated on every render, especially when passing functions as props to child components, to avoid unnecessary re-renders.

Both hooks depend on a dependency array, and they only recompute when those dependencies change.

---
### 10. What are the differences between the `useRef` hook and the `useState` hook?
Ans:
In React, both `useRef` and `useState` are hooks used to store values across renders, but they serve different purposes.

The main difference is that `useState` is used to store state that affects the UI, and whenever the state changes, it triggers a re-render of the component.

On the other hand, `useRef` is used to store mutable values that do not cause re-renders when updated. It persists the same value across renders without affecting the UI.

`useRef` is commonly used for accessing DOM elements, storing previous values, or keeping mutable variables like timers.

In short, `useState` is used when you want React to re-render the UI on change, while `useRef` is used when you want to persist values without triggering a re-render.

---
### 11. What is the `useContext` hook?
Ans:
`useContext` is a React hook used to access data from a context without having to pass props manually through every level of the component tree.

`useContext` avoids prop drilling, where we pass props through components that don't even need them, just to reach a deeply nested child.

With `useContext`, we can directly access shared data like themes, user information, or language settings from any component that is wrapped inside a Context Provider.

`useContext` takes the context and gives you whatever value is currently stored in its Provider.

Works well with **Context API** and `useContext` Makes code cleaner.

Context API includes:
- `createContext()`
- `Provider`
- `Consumer`

Context API → creates & provides data
`useContext` → consumes that data

---
### 12. What are the React custom hooks? How can custom hooks be created?
Ans:
Custom hooks in React are user-defined functions that allow us to reuse logic across multiple components.

They are created using existing React hooks like `useState`, `useEffect`, or others, and help us extract and share common functionality instead of repeating the same code in different components.

A custom hook is simply a JavaScript function whose name starts with `use`, and it can return values, functions, or state depending on the requirement.

To create a custom hook, we define a function, use built-in hooks inside it, and return the required data or behavior. Then we can reuse that hook in any component.

For example, if multiple components need to fetch data, we can create a custom hook like `useFetch` to handle that logic once and reuse it everywhere.

In short, custom hooks improve code reusability, readability, and maintainability.

---
### 13. How to increase the performance of a ReactJS application?
Ans: 
To improve the performance of a React application, the main goal is to avoid unnecessary re-renders and optimize how components update.

One common technique is using memoization tools like `React.memo`, `useMemo`, and `useCallback` to prevent unnecessary recalculations and re-renders.

We can also optimize component structure by breaking large components into smaller ones and using proper state management so that only the required components re-render.

Another important approach is lazy loading using `React.lazy` and `Suspense`, which helps load components only when needed, reducing initial load time.

Using proper keys in lists improves rendering efficiency, and techniques like code splitting and bundling optimization also help improve performance.

Additionally, we can avoid unnecessary state updates, use `useRef` for non-UI values, and optimize expensive operations.

In short, performance in React is mainly about minimizing unnecessary renders, optimizing computations, and loading resources efficiently.

---
### 14. How to implement UI in frontend using Figma design?
Ans:
To implement UI in the frontend using a Figma design, the first step is to carefully analyze the design, including layout, spacing, colors, typography, and components.

Next, we need to break the design into reusable UI components, such as headers, buttons, cards, and forms, and map them to React components.

Then, we extract design details from Figma using the inspect panel, such as CSS properties, font sizes, colors, margins, and paddings.

After that, we start building the layout using HTML and CSS or frameworks like Tailwind or Bootstrap, 
we need to ensure the design responsive using Flexbox, Grid, and media queries.

Finally, we test the UI across different screen sizes and browsers to ensure consistency and performance.

In short, the process involves analyzing the design, breaking it into components, converting design styles into code, and ensuring responsiveness and accuracy.

---
### 15. 