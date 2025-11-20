## **1. Definition**

- **`undefined`**:  
    A variable that has been declared but has not been assigned any value **automatically** gets `undefined`.  
    It’s the JavaScript engine’s default "no value assigned yet" state.
    
- **`null`**:  
    An **intentional** assignment representing "no value".  
    It’s a developer’s way of saying, _"This variable should be empty right now."_
    

---

## **2. Type**

- **`typeof undefined` → `"undefined"`**
    
- **`typeof null` → `"object"`** _(this is actually a historical bug in JavaScript but kept for backward compatibility)_
    

---

## **3. Usage Intent**

- **Use `undefined`**: Usually the result of not setting a value, missing function parameters, or missing object properties.
    
- **Use `null`**: To explicitly clear a variable or reset it to "nothing".
    

---

## **4. Equality Comparisons**

- **Loose equality (`==`)**:  
    `null == undefined` → `true` _(both considered "empty" in loose checks)_
    
- **Strict equality (`===`)**:  
    `null === undefined` → `false` _(different types)_
    

---

## **5. Common Scenarios**

|Scenario|Result|
|---|---|
|Declared but not assigned|`undefined`|
|Missing function parameter|`undefined`|
|Object property doesn’t exist|`undefined`|
|API returns “no data” intentionally|`null`|

---

## **6. Interview Tip / Gotcha**

- **Don’t say they’re the same.** The **key difference** is _who assigns them_:
    
    - `undefined` → JavaScript itself (default)
        
    - `null` → You, the developer (intentional)
        
- The **`typeof null` bug** is a common trick question.
    

---

✅ **One-liner answer for interviews**:

> "`undefined` means a variable has been declared but not yet assigned a value by the JavaScript engine, while `null` is an explicit assignment by the developer to indicate 'no value'. They are loosely equal but have different types."

---

If you want, I can also give you a **quick visual diagram** that you can recall instantly during interviews. Would you like me to create that?




----

Can you explain the difference between dot notation and square bracket notation when accessing object properties? When would you use one over the other?

**Dot notation** is for when you know the property name in advance and it’s a normal JavaScript name (no spaces, no special characters).  
**Square bracket notation** is for when the property name is dynamic (comes from a variable) or has special characters/spaces.
## **1. Basics**

- **Dot notation (`obj.key`)**
    
    - Access a property **using a literal identifier** (the exact name of the property).
        
    - Property name must be a valid JavaScript identifier (no spaces, no special characters except `_` and `$`, cannot start with a number).
        
- **Square bracket notation (`obj["key"]`)**
    
    - Access a property **using a string or variable** that contains the property name.
        
    - More flexible: works with property names that have spaces, special characters, or are dynamic.
        

---

## **2. Examples**

```js
const person = {
  name: "Alice",
  "favorite color": "blue",
  age: 25
};

// Dot notation
console.log(person.name);           // ✅ "Alice"

// Square bracket notation with string
console.log(person["favorite color"]); // ✅ "blue"

// Square bracket notation with variable
const prop = "age";
console.log(person[prop]);          // ✅ 25
```

---

## **3. When to Use**

### ✅ **Use Dot Notation**

- When you know the property name **ahead of time** and it’s a valid JavaScript identifier.
    
- Cleaner and easier to read.
    

```js
user.name;
car.model;
```

### ✅ **Use Square Bracket Notation**

- **Dynamic property access** (property name comes from a variable, function, or user input).
    
- Property names with **spaces, hyphens, or special characters**.
    
- Accessing properties with **reserved keywords** (rare in modern JS).
    

```js
const key = getUserSelectedKey();
console.log(user[key]); // key decided at runtime

console.log(person["favorite color"]); // spaces in name
```

---

## **4. Interview Tip / Common Pitfalls**

- **Dot notation does not evaluate variables**:
    

```js
const key = "name";
console.log(person.key); // ❌ undefined (looks for literal "key")
```

- **Square bracket notation can evaluate expressions**:
    

```js
console.log(person[key]); // ✅ "Alice"
```

- If you need **dynamic access** → use square brackets.
    
- If you want **static, clear access** → use dot notation.
    

---

✅ **One-liner for interviews**:

> Dot notation is for static, valid identifier property names, while square bracket notation works with dynamic keys, strings with spaces, or special characters.

---

If you want, I can also prepare a **cheat-sheet table** showing dot vs square bracket scenarios with _valid_ and _invalid_ cases side-by-side so you can recall them instantly in an interview. Would you like me to make that?