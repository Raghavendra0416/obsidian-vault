### 1. `reduce()` in JavaScript

`reduce()` is an **array method** used to **convert an array into a single value**.

Syntax:
```jsx
array.reduce((accumulator, currentValue) => {
  return updatedAccumulator;
}, initialValue);
```

 Example:
```jsx
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((acc, curr) => {
  return acc + curr;
}, 0);

console.log(sum); // 10
```

What’s happening:
- `acc` → stores accumulated result
- `curr` → current array element
- `0` → initial value

So basically:

> "Take all values → process them → return ONE final result"

Key idea:
- It **loops through array**
- Keeps an **accumulator**
- Returns **one final result**

![[Pasted image 20260405172907.png]]


---
### 2. `useReducer()` in React

`useReducer` is a **React Hook** used for **state management**, especially when:

- State logic is complex
- Multiple state transitions
- Related state values

Syntax:
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

Example:
```jsx
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </>
  );
}
```

What’s happening:
- `state` → current state
- `dispatch()` → triggers an action
- `reducer()` → decides how state changes

So basically:
> "Current state + action → returns NEW state"

Key idea:
- You **dispatch actions**
- Reducer decides **how state changes**
- Used instead of `useState` for **complex logic**


![[Pasted image 20260405173058.png]]

---
### 3. Reducer in Redux

A **Redux reducer** is a **pure function** used to manage **global application state**.

Syntax:
```jsx
const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}
```

Example (with store):
```jsx
import { createStore } from "redux";

const store = createStore(reducer);

// dispatch actions
store.dispatch({ type: "increment" });

console.log(store.getState()); // { count: 1 }
```


What’s happening:
- `state` → global state
- `action` → describes what happened
- `reducer()` → returns updated state
- `store` → holds entire app state

So basically:

> "Global state + action → returns NEW global state"

Key idea:
- Part of **Redux store**
- Handles **global state**
- Works with **actions + dispatch**

![[Pasted image 20260405173331.png]]

---
### 4. Key Differences (Interview Table)

|Feature|`reduce()` (JavaScript)|`useReducer()` (React)|Redux Reducer|
|---|---|---|---|
|Type|Array method|React Hook|Function (Redux)|
|Purpose|Transform array → single value|Manage component state|Manage global state|
|Used In|JavaScript (anywhere)|React components|Redux store|
|Input|Array elements|Current state + action|Current state + action|
|Output|Single value|Updated state|Updated global state|
|State Management|❌ No|✅ Local state|✅ Global state|
|Dispatch concept|❌ No|✅ Yes|✅ Yes|
|Scope|Local operation|Component-level|Application-wide|
|Complexity|Simple|Medium|High|
|Example Use|Sum, grouping|Forms, UI state|Large apps, shared data|

Simple Analogy:
- **`reduce()`**  
    👉 Like calculating total bill from items in cart

- **`useReducer()`**  
    👉 Like managing a bank account inside one component

- **Redux reducer**  
    👉 Like managing a **central bank system** used by entire country (app)
    

If interviewer asks:

_“Difference between useReducer and Redux reducer?”_

You can say:

> "useReducer is used for local component state, while Redux reducers manage global state shared across the entire application. Both follow the same reducer pattern but differ in scope and architecture."

---
[[Redux Toolkit (Global storage of Data)- Self]]  - Self Written 