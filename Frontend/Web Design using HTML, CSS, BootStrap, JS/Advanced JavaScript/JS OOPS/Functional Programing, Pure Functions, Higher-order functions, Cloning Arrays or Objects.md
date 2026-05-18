Functional Programming:

- Functional programming follows: **INPUT → PROCESS → OUTPUT**
- Focus is on **pure functions** (same input → same output, no side effects)
- Avoid using or modifying **global variables**
- Emphasizes **immutability** (don’t change existing data, create new data instead)
- Pass all required data as **function parameters** (no hidden dependencies)

Key Rules
1. **Do not mutate data**  
    → Create new variables/objects instead of modifying existing ones
2. **Use only function arguments**  
    → No reliance on external/global variables

Example Task
```javascript
function subarray(arr, start, end) {
  return arr.slice(start, end + 1);
}
```
### Functional Programming

**Functional Programming (FP)** is a programming style where we build programs using **pure functions** and **avoid changing data or state**.

Main Rules of Functional Programming
1. **Pure Functions**  
    A function should:
    - Always return the same output for the same input
    - Not change anything outside the function

    ```javascript
    function add(a, b) {
      return a + b;
    }
    ```

2. **No Side Effects**  
    Functions should **not modify external variables, DOM, or global state**.


3. **Immutability**  
    Do **not modify existing data**. Instead create new data.

    ❌ Bad
    ```javascript
    arr.push(4);
    ```

    ✅ Good
    ```javascript
    const newArr = [...arr, 4];
    ```


4. **First-Class Functions**  
    Functions can be:
    - stored in variables
    - passed as arguments
    - returned from other functions

5. **Use Higher-Order Functions**  
    Functions that take other functions as arguments.
    
    Example:
    ```javascript
    arr.map(x => x * 2);
    ```

---
### Pure Function
A **pure function** always returns the **same output for the same input** and **does not change anything outside the function (no side effects).**

Example:
```javascript
function add(a, b) {
  return a + b;
}
```

### Higher-Order Function
A **higher-order function** is a function that **takes another function as an argument or returns a function.**

Example:
```javascript
arr.map(x => x * 2);
```
Here `map()` takes a function as an argument.


**Short definition**
- **Pure Function:** Same input → same output, no external changes.
- **Higher-Order Function:** Function that accepts or returns another function.

---
### Cloning using Spread Operator (JS)

**Array cloning**
```javascript
const arr = [1, 2, 3];
const newArr = [...arr];
```

**Object cloning**
```javascript
const obj = { name: "Ram", age: 25 };
const newObj = { ...obj };
```

This creates a **copy of the array/object**.

- Spread operator → **shallow copy**
- Nested objects still share memory
- Use **`structuredClone()` or JSON methods** for **deep copy**.

#### Issue with Spread Cloning

Spread operator does **shallow copy**, not deep copy.
If the object has **nested objects**, they still share the same reference.

```javascript
const user = {
  name: "Ram",
  address: { city: "Hyderabad" }
};

const newUser = { ...user };
newUser.address.city = "Delhi";

console.log(user.address.city); // Delhi (original also changed)
```

#### How to Overcome It

Use **deep cloning**.

1. **`structuredClone` (modern JS)**

```javascript
const newUser = structuredClone(user);
```

2. **JSON method**

```javascript
const newUser = JSON.parse(JSON.stringify(user));
```


3. Basic Recursive Method for Deep Cloning (JS)
	A **recursive function** can copy nested objects/arrays so that no references are shared.

```JS
function deepClone(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj;
  }

  const clone = Array.isArray(obj) ? [] : {};

  for (let key in obj) {
    clone[key] = deepClone(obj[key]);
  }

  return clone;
}

const user = {
  name: "Ram",
  address: { city: "Hyderabad" }
};

const newUser = deepClone(user);
newUser.address.city = "Delhi";

console.log(user.address.city); // Hyderabad (original not changed)
```

