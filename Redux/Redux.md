### Definition
**Redux is a state management library** used to manage and centralize the state of your application. Instead of storing data in multiple components, Redux stores everything in **one global place (store)**.

> Redux is used to manage global state using a predictable flow: actions, reducers, and a centralized store.

Extra Information: Redux Toolkit (RTK) is the **modern, recommended way to use Redux, It simplifies Redux a LOT.**

Old Redux Problem:
- Too much boilerplate
- Actions file
- Reducer file
- Types file
- Store setup
---
### Why Redux instead of Hooks? How Redux Solve it?
Hooks can manage the state but the key difference is **scale and structure.**

#### Problem with Hooks (in large apps)
If you try to replace Redux using only hooks:
❌ Too many contexts
❌ Hard to organize logic
❌ Debugging becomes messy
❌ No clear structure for updates

Example Problem:
Imagine:
- User data
- Cart data
- Notifications
- API states

If you use only hooks:

```
UserContext
CartContext
ThemeContext
NotificationContext
```

👉 This becomes **Context Hell** 😵

#### How Redux Solve it?
Redux gives STRUCTURE

Redux enforces a pattern:

```
Action → Reducer → Store → UI
```

So:
- Everything is predictable
- All updates follow the same flow

#### Difference:
Hooks vs Redux

|Feature|Hooks|Redux|
|---|---|---|
|Scope|Local / small global|Fully global|
|Structure|Flexible (can get messy)|Strict & predictable|
|Debugging|Hard|Easy (DevTools 🔥)|
|Middleware|No|Yes|
|Best for|Small apps|Large apps|

Redux vs Context API

|Feature|Redux|Context API|
|---|---|---|
|Complexity|High|Low|
|Best for|Large apps|Small apps|
|Debugging|Excellent|Limited|
|Middleware|Yes|No|

---

### Core Concepts of Redux

Flow:
```
Component → dispatch(action) → reducer → store updates → UI updates
```

Think of Redux like a system:

1. Store
- The **single source of truth**
- Holds all application state

```jsx
const store = createStore(reducer);
```

1. Action:
- A simple object that describes **what happened**

```jsx
{ type: "INCREMENT" }
```

3. Reducer
- A function that updates state based on action

```jsx
function counterReducer(state = 0, action) {
  switch(action.type) {
    case "INCREMENT":
      return state + 1;
    default:
      return state;
  }
}
```

4. Dispatch
- Sends action to reducer

```jsx
store.dispatch({ type: "INCREMENT" });
```

---

### How to use Redux in Components using Counter Example

Order to always remember:
Reducer → Store → Dispatch → Read 

Think of it like a vending machine — the reducer is the _machine's logic_ (what each button does), the store is the _machine itself_, dispatch is _pressing a button_, and `getState` is _checking what came out_. You always build the logic before you build the machine.

```jsx
// ============================================================
// STEP 1 — CREATE THE STORE FACTORY
// Think of this as a "store builder". You give it a reducer,
// and it gives back an object with two tools: getState & dispatch.
// In real Redux you'd import this from the 'redux' package,
// but here we're building it ourselves to see how it works.
// ============================================================
const createStore = (reducer) => {

  // This is the actual state variable. It lives INSIDE the store,
  // hidden from the outside world. Nobody can touch it directly.
  // We call the reducer once on startup (with undefined + empty action)
  // so it returns its default value (0 in our case).
  let state = reducer(undefined, {});

  return {

    // getState() is the only way to READ the current state.
    // It just returns whatever is stored in the 'state' variable above.
    getState: () => state,

    // dispatch() is the only way to CHANGE the state.
    // You pass it an action object, it runs the reducer,
    // and saves the new state back into the 'state' variable.
    dispatch: (action) => { state = reducer(state, action); }

  };
};

// ============================================================
// STEP 2 — WRITE THE REDUCER
// A reducer is just a function with two rules:
//   1. It receives the current state + an action
//   2. It RETURNS the new state (never modifies the old one)
//
// Write this BEFORE createStore, because createStore needs it.
// ============================================================
function counterReducer(state = 0, action) {
  //                    ↑
  // state = 0 is the DEFAULT VALUE.
  // On the very first call, state is undefined,
  // so it falls back to 0. This is your starting state.

  switch (action.type) {
    // Each "case" matches the action.type string.
    // Return the NEW state — do not modify the old one.

    case "INCREMENT": return state + 1;  // e.g. 0 → 1 → 2
    case "DECREMENT": return state - 1;  // e.g. 2 → 1
    case "RESET":     return 0;          // always go back to 0

    default: return state;
    // IMPORTANT: Always have a default.
    // If an unknown action comes in, return state unchanged.
  }
}

// ============================================================
// STEP 3 — BUILD YOUR STORE
// Now wire everything together. Pass your reducer into createStore.
// You only ever create ONE store for your whole app.
// ============================================================
const store = createStore(counterReducer);
//            ↑
// At this point, state is initialized to 0
// (createStore called counterReducer(undefined, {}) internally)

// ============================================================
// STEP 4 — DISPATCH ACTIONS
// This is how you interact with the store.
// dispatch() takes an action object: { type: "SOME_STRING" }
// It sends it to the reducer, which figures out the new state.
// ============================================================
store.dispatch({ type: "INCREMENT" }); // reducer: 0 + 1 = 1  → state is now 1
store.dispatch({ type: "INCREMENT" }); // reducer: 1 + 1 = 2  → state is now 2
store.dispatch({ type: "DECREMENT" }); // reducer: 2 - 1 = 1  → state is now 1

// ============================================================
// STEP 5 — READ THE STATE
// getState() returns the current value stored in the store.
// ============================================================
console.log(store.getState()); // → 1

// ============================================================
// ORDER TO BUILD THINGS IN (summary)
// ============================================================
//
//  1. Write the reducer first
//     → It's a plain function, easiest to write and test alone
//
//  2. Create the store using that reducer
//     → const store = createStore(counterReducer)
//
//  3. Dispatch actions to change state
//     → store.dispatch({ type: "..." })
//
//  4. Read state whenever you need it
//     → store.getState()
//
// ============================================================
```

**The full Redux loop, in plain terms:**

1. **Action** — just a plain JS object with a `type` field. It's like a message saying _"something happened."_ It never changes state itself.
2. **Reducer** — a pure function that takes `(currentState, action)` and returns the _new_ state. No side effects — same inputs always give same output.
3. **Store** — the single source of truth. It holds state and calls your reducer whenever an action is dispatched.
4. **Dispatch** — the only way to trigger a state change. `store.dispatch({ type: "INCREMENT" })` sends the action to the reducer, which computes the next state.

The key mental model: **data flows one way** — UI dispatches an action → reducer updates state → UI re-renders from new state. Nothing mutates state directly.

---
### Where do we use Redux?
Redux is used in **medium to large applications** where:
1. Many components share the same data (Ex: User login info, Theme).
2. Complex state logic (Ex: Multiple APIs, Dependent state updates ).
3. Avoid prop drilling
4. Need predictable state

---

### What is Redux Toolkit? Why is recommended instead of Redux code?
Redux Toolkit (RTK) is the **modern, recommended way to use Redux.** It simplifies Redux a LOT.

Example with Redux Toolkit

```jsx
import {createSlice }from"@reduxjs/toolkit";

constcounterSlice=createSlice({
  name:"counter",
  initialState: { value:0 },
  reducers: {
    increment: (state) => {
state.value+=1;
    }
  }
});

exportconst { increment }=counterSlice.actions;
exportdefaultcounterSlice.reducer;
```

- That’s it. No switch-case. No boilerplate.

Why Redux Toolkit is better:

1. Less code (No manual action types)
2. Built-in Immer (You can "mutate" state safely)
3. Built-in async support (Using `createAsyncThunk`)
4. Easy store setup

---