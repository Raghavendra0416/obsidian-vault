### Hooks:
Hooks are special functions in React that allow user to use **`useState` and other React features inside functional components** without writing class components.

Only Class components could manage the state, but hooks made functional components to manage state. and also make the code more readable and easy to reuse.

some key rules for hooks:

Call hooks cannot be used inside the loops and conditions or nested functions.

hooks can only be used inside the react.

Example for hooks: `useState, useEffect, useMemo, useCallback, useRef, useContext, useReducer`, custom hook.

In React, when a component re-renders, all variables and functions inside it are recreated. To optimize performance, we can use hooks like `useCallback` or `useMemo`, not `useEffect`.

For Understanding: `useLayoutEffect` — not used much.

---

#### `useState` Hook:

`useState` is a Hook in React used to manage state in functional components. It allows us to store values and update them, and whenever the state changes, React re-renders the component so the UI becomes interactive.

We can use multiple `useState` hooks in a single component to manage different pieces of state independently.

Syntax:

```jsx
const [state, setState] = useState(initialValue);
```

- `state` → current value
- `setState` → function to update it
- `initialValue` → default value

---

#### `useEffect` Hook:

In React, when a component re-renders, all variables and functions inside it are recreated. To handle the situation, we can use `useEffect` hook.

`useEffect` is a Hook in React used to handle **side effects** in functional components.

Side Effects are:

- API calls
- DOM manipulation
- Timers (`setTimeout`, `setInterval`)
- Event listeners

`useEffect` can run after every render if needed or we can also control its run by using dependency array.

and also while using `useEffect` returning cleanup function is mandatory as it prevents memory leaks, clean timers and event listeners.

Syntax:

```jsx
useEffect(() => {
  // side effect code

  return () => {
    // cleanup (optional)
  };
}, [dependencies]);
```

Extra Information: A cleanup function in `useEffect` is a function that runs **before the component unmounts** or **before the effect runs again**, used to **clean up side effects**.

If we don’t use a cleanup function in React, side effects like timers, event listeners, will continue running even after the component is removed, which can lead to memory leaks and unexpected behavior.

Without Cleanup function timers, event listeners will continue to run even after the component is removed—How?

Example of what will happen if Clean Up function is not used:

User enters a page and timers(set Timeout/set Interval) will start and the interval time to complete is 3secs, but the user has closed the page in 1sec, the timer will continue to run and will return, but the page is already closed and it is trying to update the component that is no longer exists. this situation will lead to warnings and memory issues.

---

#### `useMemo` Hook:

`useMemo` is a Hook in React used to **memorize (cache) a computed value** so that it is **recalculated only once or when its dependencies changes.**

`useMemo` is used to avoid Unnecessary re-computation, Expensive calculations on every render.

`useMemo` should be used only when there is a real performance issue, not for every calculation.

If `useMemo` is not used, the calculation will run on **every render**, which can lead to performance issues if the calculation is complex or expensive. Overusing `useMemo` can also hurt performance due to extra memory and comparison overhead, so it should be used only when needed.

Syntax:

```jsx
const memoizedValue = useMemo(() => {
  return expensiveFunction();
}, [dependencies]);
```

---

#### `useCallaback` Hook:

`useCallback` is a Hook in React used to **memoize a function**, so that the function is **not recreated on every render** unless its dependencies change.

In React, for Every render → functions are **re-created** and this can cause Unnecessary re-renders of child components and performance issues. But with `useCallback` we can overcome this situation.

It is mainly used to prevent unnecessary re-renders of child components when functions are passed as props.

`useCallback` memoizes a function, while `useMemo` memoizes a computed value.

|Hook|Memoizes|
|---|---|
|`useMemo`|Value|
|`useCallback`|Function|

Syntax:

```jsx
const memoizedFunction = useCallback(() => {
  // function logic
}, [dependencies]);`
```

---

|Hook|What it returns|Purpose|Where we use it|
|---|---|---|---|
|`useEffect`|Nothing (or cleanup function)|Handle side effects|API calls, timers, subscriptions, event listeners, syncing with external systems|
|`useMemo`|Value|Memoize computed value|Expensive calculations (filtering, sorting, large data processing)|
|`useCallback`|Function|Memoize function|When passing functions to child components (to prevent unnecessary re-renders)|

---

#### `useRef` Hook:

`useRef` is a Hook in React used to store mutable values that persist across re-renders of a component. It is commonly used to access DOM elements and to store values without causing a re-render. Since updating a ref does not trigger a re-render, it cannot be used to update the UI. The value inside `useRef` is accessed using the `.current` property.

Without `useRef`, we can’t store values without re-render or directly access DOM elements efficiently.

[[Reduce(JS) & useReducer (React) & Reducer(Redux)]] -- Understand the difference.

`useRef` are used when:

- Focusing an input field automatically
- Controlling video/audio playback (play, pause)
- Storing previous value of a variable
- Tracking number of renders

Syntax:

```jsx
const ref = useRef(initialValue);
//Access value using:
ref.current
```

---

#### `useContext` Hook:

`useContext` allows to share values between multiple levels of components without passing props through each level.

that means `useContext` allows direct access to shared data this makes code more **cleaner and maintainable.**

`useContext` is not ideal for **very complex state logic.**

`useContext` is used to avoid prop drilling.

**"Prop Drilling"** — passing props through components that don't even need them, just to reach a deeply nested child.

`useContext` takes the context and gives you whatever value is currently stored in its Provider.

3 Steps to Use Context

```
1. CREATE  the context  (createContext)
2. PROVIDE the data     (Context.Provider) -- Wrap components with Provider
3. CONSUME the data     (useContext) -- Use useContext to access data
```

Real world examples where we could use `useContext` are:

- User authentication (logged-in user info)
- Theme (dark/light mode)
- Language settings

Extra Information: Instead of passing props through multiple components, we store data in a Context and access it wherever needed using `useContext`.

`useContext` and Context Api different?

Ans: Yes, they are related but not the same. Context API is the overall feature, and `useContext` is a hook used to consume it.

**Context API**

- It is the **full system** for sharing data globally in React
- Includes:
    - `createContext()`
    - `Provider`
    - `Consumer`

Think of it as the **tool/setup**

Context API → creates & provides data

**useContext**

- It is a **hook**
- Used to **read (consume)** data from the Context API

Think of it as the **way to use that tool**

`useContext` → consumes that data

To use `useContext` hook we need to follow the below steps:

Provider Component:

```
1. import { createContext } from ‘react’;
2. export const MyContext = createContext();
3. < MyContext.Provider value={ value }>
    <Child / >
    < / MyContext.Provider >
```

Consumer Component:

```
1. import React, { useContext } from ‘react’;
    
    import { MyContext } from `./ComponentA';
    
2. const value = useContext( MyContext );
```

|Question|Answer|
|---|---|
|What problem does `useContext` solve?|Prop drilling — passing data through many layers|
|What are the 3 steps?|`createContext` → `Provider` → `useContext`|
|Can any component access context?|Only components **inside** the Provider|
|Does context update cause re-render?|✅ Yes — all consumers re-render when value changes|
|Is context a replacement for Redux?|For simple global state yes, for complex apps Redux/Zustand is better|

---

#### `useReducer` Hook:

When state has **multiple values** and **complex logic**, `useState` gets messy. `useReducer` puts **all state logic in one place** — clean, organized, and predictable.

`useReducer` is used when — State is **complex** (multiple values) and if state updates depend on **previous state** and ****Logic becomes hard to manage with `useState`

`useReducer` is used using State, Reducer function, Dispatch function.

and in this:

- **Reducer** → function that decides how state changes
- **Action** → describes what to do
- **Dispatch** → triggers state update

Flow:

dispatch(action) → reducer → new state → UI update

4 Key Terms

```
STATE    →  the current data           { count: 0 }
ACTION   →  what happened             { type: "INCREMENT" }
REDUCER  →  function that updates     (state, action) => newState
DISPATCH →  how you trigger action    dispatch({ type: "INCREMENT" })
```

---

Custom Hook: A custom hook is a JavaScript function in React that allows you to reuse logic across multiple components using built-in hooks like `useState`, `useEffect`, etc.

We use Custom Hook to create reusable logic, avoid code duplication.

The Naming rule we should follow while creating a custom hook is to use “use”.

Some real world examples where we can use custom hooks are while Form handling, Fetching API Data, Window resize listener.

---

#### `useLayoutEffect` Hook:

For Understanding: `useLayoutEffect` — not used much.

`useLayoutEffect` is similar to `useEffect` but runs synchronously after the DOM is updated and before the browser paints. It is used when we need to measure or modify the DOM before the user sees it, such as for layout calculations or avoiding flickering in React.

Overusing `useLayoutEffect`:

- Blocks rendering
- Slows performance

Prefer `useEffect` unless necessary

Syntax:

```jsx
useLayoutEffect(() => {
  // side effect logic

  return () => {
    // cleanup function (optional)
  };
}, [dependencies]);
```

---

### Differences between Hooks:

#### Difference between `useState` & `useEffect`

|Feature|useState|useEffect|
|---|---|---|
|Purpose|Manage **state (data)**|Handle **side effects**|
|What it does|Stores and updates values|Runs logic after render|
|Trigger|Called manually using setter|Runs automatically based on dependencies|
|Re-render|Updating state **causes re-render**|Does NOT directly cause re-render (unless state updated inside it)|
|Usage|UI data (count, input, toggle)|API calls, timers, subscriptions|
|Syntax|`useState(initialValue)`|`useEffect(() => {}, [deps])`|
|Execution time|During render|After render|
|Return value|`[state, setState]`|Optional cleanup function|

---

#### Difference between `useState` & `useReducer`

|Feature|useState|useReducer|
|---|---|---|
|Best for|Simple state|Complex state|
|Logic|Scattered|Centralized|
|Updates|Direct|Through reducer|
|Readability|Easy|Better for complex logic|

---

#### Difference between `useMemo` & `useCallback`

|Feature|useMemo|useCallback|
|---|---|---|
|Purpose|Memoizes a **value**|Memoizes a **function**|
|Return type|Computed value|Function|
|Use case|Avoid expensive calculations|Prevent function re-creation|
|When it runs|When dependencies change|When dependencies change|
|Common usage|Heavy computations (filter, sort, loops)|Passing functions to child components|
|Helps with|Performance optimization|Prevent unnecessary re-renders|
|Syntax|`useMemo(() => value, [deps])`|`useCallback(() => {}, [deps])`|
|Relation|Returns result of function|Returns the function itself|
|With React.memo|Indirectly helps|Directly helps prevent re-renders|
|Overuse impact|Adds overhead|Adds overhead|

---

#### Difference between all Hooks

|Hook|Purpose|What it Handles|Causes Re-render?|When it Runs|Best Use Case|
|---|---|---|---|---|---|
|**useState**|Manage state|Simple data (count, input)|✅ Yes|On state update|UI state management|
|**useEffect**|Side effects|API calls, timers, subscriptions|❌ (directly)|After render|External operations|
|**useMemo**|Memoize value|Expensive calculations|❌|When dependencies change|Performance optimization|
|**useCallback**|Memoize function|Function reference|❌|When dependencies change|Prevent child re-renders|
|**useRef**|Store mutable value / DOM access|Persistent value, DOM elements|❌|Persists across renders|DOM access, no re-render storage|
|**useContext**|Access global data|Shared state (theme, auth)|✅ (on context change)|On context update|Avoid prop drilling|
|**useReducer**|Manage complex state|Complex logic, multiple states|✅|On dispatch|Structured state management|
|**Custom Hook**|Reuse logic|Any reusable logic|Depends on used hooks|Depends on implementation|Code reuse|

---

### Other Questions:

#### How to Control Unnecessary re-rendering?

Tools like React Profiler and render count tracking help identify unnecessary re-renders, while dependency arrays help control when certain logic runs. However, they do not directly prevent re-renders; instead, we use optimization techniques like `React.memo`, `useMemo`, and `useCallback` to reduce unnecessary rendering in React.

To control unnecessary re-rendering we can use:

1. React Profiler.
2. Render Count Tracking.
3. Dependency Checks ( `useEffect` / `useMemo` / `useCallback` ).

**React Profiler:**

What it does:

- Measures rendering performance
- Shows which components re-render.
- Shows time taken for every component.

Purpose:

- **Debugging tool**, not optimization tool

**Render Count Tracking:**

Example idea:

- Logging renders (`console.log`)
- Counting renders using `useRef`

Purpose:

- Helps detect unnecessary re-renders

Dependency Checks ( `useEffect` / `useMemo` / `useCallback` ):

What it does:

- Controls when logic runs
- Prevents unnecessary recalculations

Purpose:

- Helps **optimize behavior**, not stop re-render

How to find Unnecessary re-rendering Issue:

Detect → Analyze → Optimize

1. Use **Profiler / logs** → find re-render issue
2. Analyze cause → props/state changes
3. Fix using memoization

|Tool|Purpose|
|---|---|
|React Profiler|Analyze performance|
|Render count|Detect re-renders|
|Dependency array|Control execution|
|React.memo / useMemo / useCallback|Optimize|

---

#### Real DOM vs Virtual DOM

|Feature|Real DOM|Virtual DOM|
|---|---|---|
|Definition|Actual DOM in browser|Lightweight copy of DOM in memory|
|Update speed|Slow ( But Faster in case of smaller Updates)|Fast|
|Performance|Less efficient|Highly efficient|
|Manipulation|Direct DOM manipulation|Uses diffing algorithm|
|Cost|Expensive operations|Optimized updates|
|Used by|Traditional JS|React|

---

#### If Virtual DOM does not render components. How do Debug?

If components are not rendering in React, we debug by checking state, props, conditional rendering logic, and lifecycle behavior rather than the Virtual DOM itself.

Use Dev tools in the browser and console the errors to find the issue.

---

#### Prevent unnecessary re-rendering

To prevent unnecessary re-rendering of child components in React, we can use `React.memo` to memoize the child component so it only re-renders when its props actually change.

We can use `React.memo` , `useMemo` , `useCallback` and also we need to Avoid unnecessary state changes.

If we are dealing with class components then we can use `shouldComponentUpdate` to control the component re-render. if `true` → skip re-render, `false` → allow re-render.

---

#### Lifting State up

Lifting state up means **moving state from a child component to a common parent component** so that multiple child components can **share and stay in sync with the same data** in React.

We use it when — Two or more components need **same data,** Keeping state in one child causes **data inconsistency.**

Component NOT re-rendering after lifting state up — Why?

If a component does not re-render after lifting state up in React, it is usually due to issues with state updates, props not changing by reference, or memoization preventing re-render.

issues — State not updated properly, same reference passed, `React.memo/ useMemo/ useCallback` is blocking the re-render, props not passed correctly, need to check conditional rendering.

We should check the above to debug the issue.

Why use Lifting State Up when we have `useContext`?

Lifting state up is used for sharing state between a few related components, while `useContext` is used for global or widely shared state in React.

Comparison:

|Feature|Lifting State Up|`useContext`|
|---|---|---|
|Scope|Few components|Many components|
|Complexity|Simple|Slightly complex|
|Setup|No extra setup|Requires Context|
|Performance|More controlled|Can cause wider re-renders|
|Use case|Parent-child relation|Global data|

---

#### Higher Order Components

A Higher-Order Component (HOC) is a function in React that **takes a component as input and returns a new enhanced component with additional functionality**.

It’s like a wrapper that adds extra features to a component without modifying the original component.

HOC is used to Reuse logic across components, Avoid code duplication.

HOC is Less used in modern React and it is Replaced by **custom hooks + hooks-based patterns**

Syntax:

```jsx
const EnhancedComponent = HOC(OriginalComponent);
```

HOC vs Custom Hook:

|Feature|HOC|Custom Hook|
|---|---|---|
|Pattern|Component wrapper|Function|
|Reuse|Component logic|Hook logic|
|Usage|Older pattern|Modern React|
|UI control|Can modify UI|Cannot modify UI directly|

---

#### `useContext` vs State Management Library

**Simple Explanation:**

**`useContext`**

- Just a way to **share data globally**
- Not a full state management solution

State Management Library

- Designed to **handle complex state logic**
- Provides structure, tools, and scalability

|Feature|`useContext`|State Management Library (Redux, Zustand, etc.)|
|---|---|---|
|Purpose|Share data globally|Manage complex global state|
|Complexity|Simple|More structured & scalable|
|Setup|Built-in in React|Requires installation & setup|
|State handling|Basic|Advanced (middleware, reducers, etc.)|
|Performance|Can cause re-renders of all consumers|Optimized updates (fine-grained control)|
|Best for|Small–medium apps|Large-scale apps|
|Debugging|Limited tools|DevTools, time-travel debugging|
|Data flow|Simple|Predictable (especially Redux)|

---

#### How do `useEffect` hook mimics the lifecycle methods of the class based components?

`useEffect` in React mimics lifecycle methods by controlling when the effect runs using the dependency array. With an empty array, it behaves like `componentDidMount`; with dependencies, it behaves like `componentDidUpdate`; and with a cleanup function, it behaves like `componentWillUnmount`. A single `useEffect` can handle **multiple lifecycle behaviors.**

Mapping: Class Lifecycle → `useEffect`

|Class Lifecycle Method|useEffect Equivalent|
|---|---|
|componentDidMount|`useEffect(() => {}, [])`|
|componentDidUpdate|`useEffect(() => {}, [deps])`|
|componentWillUnmount|`useEffect(() => { return cleanup }, [])`|

---

#### Controlled vs Uncontrolled Components

Controlled components are managed by React state, where input values are controlled using state and updated via event handlers. Uncontrolled components rely on the DOM to manage form data and use refs to access values. Controlled components provide more control and are preferred in most cases in React.

|Feature|Controlled Component|Uncontrolled Component|
|---|---|---|
|Definition|Form data is controlled by React state|Form data is handled by DOM itself|
|Source of truth|React (`useState`)|DOM (`ref`)|
|Data handling|Stored in state|Accessed using `useRef`|
|Re-render|Updates cause re-render|No re-render on input change|
|Control|Full control over input|Limited control|
|Validation|Easy to validate|Harder to validate|
|Usage|Preferred in most cases|Used for simple cases|

---

#### Pure Component

A Pure Component in React is a component that **re-renders only when its props or state change**, based on a **shallow comparison (reference check)**.

It helps improve performance by avoiding unnecessary re-renders and is similar to `React.memo` in functional components.

In Class Component we extend `React.PureComponent` and for functional component we use `React.memo` .

---

#### Stateful vs Stateless Components

Stateful components manage their own state and handle dynamic data, while stateless components do not have state and simply render UI based on props. Stateful components are used for logic and interaction, whereas stateless components are mainly used for presentation in React.

Stateful → “I manage data”

Stateless → “I just display data”

|Feature|Stateful Component|Stateless Component|
|---|---|---|
|Definition|Has its own state|Does not manage state|
|Data handling|Uses `useState` / `useReducer`|Receives data via props|
|Re-render|Changes when state updates|Re-renders only when props change|
|Complexity|More complex|Simple and easy|
|Logic|Contains business logic|Mostly UI (presentation)|
|Example use|Forms, counters, dynamic UI|Buttons, display components like Display user name|

---

#### Keys in React

Keys in React are used to uniquely identify elements in a list and understand which items in a list are changed so it can update only those items instead of re-rendering the entire list.

Keys must be unique among siblings and should be used in list rendering and this improves performance.

Don’t use index as keys as it updates the wrong UI and breaks the performance optimization.

Example:

```jsx
items.map(item => (
  <li key={item.id}>{item.name}</li>
));
```

---

#### React Router

React Router is a library in React used to handle **navigation and routing in single-page applications (SPA)** without reloading the page.

Common React Router Methods:

1. `<BrowserRouter> <BrowserRouter/>` — Wraps the app and enables routing.
2. `<Routes> <Routes>` — Container for all routes.
3. `<Route path= "/" element={<Home/>}>` — Defines path → component mapping.
4. `<Link to="/">Home<Link>` — Used for navigation without page reload.
5. `<NavLink to="/" style={'Provide styling here'}> Home <NavLink/>` — Same as `Link` but adds active styling.
6. `useNavigate` — Programmatic navigation.
7. `Navigate` — Redirect to another route. `useNavigate` & `Navigate` are used as combination for navigation.
8. `useParams` —- Access URL parameters.
9. `useLocation` — Get current URL info. and we to print the path we have to use `location.pathname` .
10. `Outlet` — sed for nested routes

React Router enables client-side routing, improving performance and user experience.

---

### Situation Based Questions:

#### **What kind of problems can occur when using `useCallback`, and how would you troubleshoot a situation where the callback is still being recreated on every render despite using it?**

Common Issues occur while using `useCallback` are:

1. Incorrect or unstable dependencies that are Changing Every Render
2. Overusing `useCallback`
3. Not using with `React.memo`
4. New object/array/function passed
5. Parent re-render causing dependency update

**Troubleshoot:**

1. Check dependencies and Stabilize dependencies
2. Avoid inline objects/functions — If not avoided, Creates new referenc e every render
3. Use `React.memo` on child
4. Debug with console.
5. Use React `DevTools Profiler` .

---

#### Downsides of Overusing `useCallback`

1. Unnecessary Overhead — React has to: Store memoized function & Compare dependencies, So more cost than benefit.
2. Increased Complexity — Harder to: Read, Maintain, Debug.
3. Dependency Bugs — Missing or wrong dependencies.
4. No Benefit Without `React.memo` — If child is not memoized: `useCallback` is useless.
5. Memory Usage

**When SHOULD you use `useCallback`?**

1. Passing function to child component.
2. Function used in dependency array.
3. Expensive re-render scenarios.

**When NOT to use:**

1. Simple functions
2. Not passed as props
3. No performance issue — Premature optimization

Extra Information:

Decision Rule

Ask yourself:

1. Is function passed to child?
2. Is child memoized (`React.memo`)?
3. Is there a performance issue?

If **YES → use `useCallback`**

If **NO → don’t use it**

---

#### What common issues can occur when using the Virtual DOM in React, and how would you troubleshoot performance problems related to excessive re-renders?

Common issues with the Virtual DOM in React arise from excessive re-renders, inefficient state updates, and unstable references. These lead to performance problems. We troubleshoot by identifying unnecessary renders using tools like React Profiler and optimize using memoization techniques such as `React.memo`, `useMemo`, and `useCallback`

Common Issues with Virtual DOM:

1. Excessive Re-renders — Frequent state updates, Parent re-render → all children re-render
2. Unstable References —- New object every render → re-render
3. Missing or Wrong Keys
4. Large Component Trees — Deep hierarchy: More diffing work, Slower updates.
5. Expensive Calculations in Render — Expensive Calculations in Render.
6. Overuse of Context ( All consumers to re-render ), Callback (Re-renders if not used correctly)

How to Troubleshoot Performance Issues:

1. Use React Profiler
2. Track Render Count — use `useRef` in every component to check the count.
3. Check Props & State Changes
4. Analyze Dependency Arrays
5. Use React DevTools — Inspect: Props, State, Component tree.

Optimization Methods:

1. `React.memo` — Prevent child re-renders.
2. `useMemo` — Optimize expensive calculations.
3. `useCallback` — Stabilize function references.
4. Split Components — Reduce re-render scope
5. Avoid Unnecessary State Updates — Only update when needed

---

#### When debugging excessive re-render issues using React Developer Tools, what specific indicators or metrics would you look at to identify which components are causing unnecessary renders?

When debugging excessive re-renders in React using React DevTools, I focus on components with high render frequency, changed props/state, and render duration using the Profiler, and I analyze why each component re-rendered.

What to Check in React DevTools (Profiler)

1. Render Count / Frequency.
2. Why did this render? — DevTools shows: Props changed, State changed, Parent re-rendered.
3. Changed Props — Which prop changed, Was it actually needed? New object/function reference every render?
4. State Updates
5. Render Duration (Time Taken)
6. Component Tree Depth
7. Props Drilling / Context Updates

Extra Information:

Step-by-Step Debug Flow

1. Open **Profiler tab**
2. Record interaction
3. Check:
    - Render count
    - Render duration
4. Click component
5. Check:
    - “Why did this render?”
6. Identify unnecessary updates
7. Apply optimization

---

#### In Lifting State up, If two sibling components that share state through their parent start showing inconsistent values after a state update, how would you debug and fix the issue?

If two sibling components show inconsistent values after lifting state up in React, the issue is usually due to incorrect state updates, stale props, or improper data flow. I would debug by verifying state updates in the parent, checking props passed to children, and ensuring there are no reference or memoization issues.

Common Causes:

1. Props not passed properly
2. State not updated correctly
3. Memoization blocking update
4. Stale state (async update issue) — If previous value is not taken in consideration to calculate the current value.
5. Each child computing value differently.

How to Debug:

1. Check Parent State
2. Check Props in Both Children
3. Use React DevTools
4. Remove Memoization Temporarily
5. Ensure: Using immutable updates
6. Check if the State is only in the parent

How to Fix:

1. Use Functional Updates
2. Ensure Immutable Updates
3. Remove Duplicate State — Keep state only in parent
4. Fix Memoization

=================================================================

**Q. If after verifying that props are passed correctly the sibling components still show inconsistent data, what steps would you take to inspect Reacts component re-render behavior and identify where the state synchronization is breaking?**

Ans.

If props are correct but siblings still show inconsistent data in React, I would inspect component re-render behavior using React DevTools Profiler, analyze render triggers, check memoization, and verify if any component is using stale values or blocking updates.

Debugging:

1. Use React DevTools Profiler
2. Check “Why did this render?” — For each component: Props changed?, State changed?, State changed?.
3. Compare Render Behavior of Siblings
4. Check Memoization Issues
5. Check if correct dependencies are being passed?
6. Check if children: Compute values differently?

x

Final Fix Strategy

1. Ensure **both siblings re-render**
2. Ensure **same props reference changes**
3. Remove incorrect memoization
4. Fix stale closures
5. Keep **single source of truth**

---

#### How JavaScript Event loop is different from React Queue?

JavaScript Event Loop — Browser's Queue

```
setTimeout()     → goes to Web API → then callback queue → event loop picks it
fetch()          → goes to Web API → then callback queue → event loop picks it
Click event      → goes to callback queue → event loop picks it
```

> Handles **async operations** — managed by the **browser**

React's Queue — React's Internal Queue

```
setCount()       → goes to React's update queue → React processes it
setState()       → goes to React's update queue → React processes it
```

> Handles **state updates** — managed by **React itself**

The Similarity:

Both are **"collect first, process later"** patterns:

```
Don't execute immediately → add to queue → process when ready
```

The Difference

||JS Event Loop|React Queue|
|---|---|---|
|Managed by|Browser|React internally|
|Handles|Async operations|State updates|
|Purpose|Non-blocking JS|Batching re-renders|

> Think of it like:
> 
> - **Event Loop** = Post office sorting mail _(browser level)_
> - **React Queue** = Your inbox prioritizing emails _(React level)_
> 
> Both queue things up — but at different levels!

Example for React Queue using `useCallback` :

counting the number of times user clicked. How `useCallback` works:

When `setCount` is called, React doesn't re-render **immediately** — it adds it to a **queue** first.

```jsx
setCount() called
      ↓
React adds to queue → [ re-render App ⏳ ]
      ↓
React checks value → same or different?
      ↓
Different → picks from queue → 🔄 re-renders
Same      → removes from queue → ⛔ nothing happens
```

---