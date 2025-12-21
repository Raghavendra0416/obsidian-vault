
### **What is an Error in JavaScript?**
An **Error** in JavaScript represents something that goes wrong during code execution.
Errors come from:
- Incorrect code syntax
- Invalid operations
- Unexpected input
- Wrong references
- Logical calculation problems

JavaScript has a built-in **Error object**, and all specific errors inherit from it.


##### **Hierarchy of Errors in JavaScript**

```JavaScript
Error
│
├── EvalError
├── RangeError
├── ReferenceError
├── SyntaxError
├── TypeError
├── URIError
└── AggregateError
```

All types are **child classes** of the base **Error** object.

##### **List of All Error Types (with simple explanations)**

##### Error:
- Base (parent) error class.
- Used to create custom errors.

Example:
```js
throw new Error("Something went wrong!");
```

##### SyntaxError:
Happens when JavaScript **syntax is incorrect** → code cannot be parsed.
Example:

```js
console.log("Hello"   // missing closing parenthesis
```

##### ReferenceError:
When you **use a variable that doesn’t exist**.
Example:

```js
console.log(x);   // x is not defined
```

##### TypeError:
When the **type of a value is wrong** or an operation is done on the **wrong type**.
Examples:

```js
null.f();  // trying to call a method on null 
```
```js
let num = 10;
num.toUpperCase(); // number has no toUpperCase
```

##### RangeError:
When a **value is not in the expected range**.
Examples:

```js
new Array(-10);  // invalid array length
```
```js
num.toFixed(200);  // too many digits
```

##### URIError:
When using `encodeURI()` or `decodeURI()` with **malformed URI characters**.
Example:

```js
decodeURIComponent("%");  // invalid encoded character
```

##### EvalError:
- Related to the `eval()` function.
- Rarely seen today — mostly kept for backward compatibility.

Example:
```js
// rarely thrown in modern JS
```

##### AggregateError:

Used when **multiple errors** are collected into one (mainly in Promises like `Promise.any()`).

Example:

```js
const err = new AggregateError([
  new Error("first"),
  new Error("second")
], "Multiple errors");
```

---

Bonus: **Custom Errors (Interview Favorite!)**
You can create your own error by extending the Error class:

```js
class MyCustomError extends Error {
  constructor(message) {
    super(message);
    this.name = "MyCustomError";
  }
}

throw new MyCustomError("Custom issue happened!");
```


Summary Table (Quick Revision)

|Error Type|Meaning (Simple)|Example|
|---|---|---|
|**Error**|Base error class|`throw new Error()`|
|**SyntaxError**|Wrong syntax → code can’t run|Missing brackets|
|**ReferenceError**|Variable not defined|`console.log(x)`|
|**TypeError**|Operation on wrong type|`null.f()`|
|**RangeError**|Value out of allowed range|`new Array(-1)`|
|**URIError**|Malformed URI passed to URI functions|`decodeURIComponent("%")`|
|**EvalError**|Errors with eval() (rare)|legacy|
|**AggregateError**|Many errors grouped|Promises|


**“What are the different types of errors in JavaScript?”**  

> JavaScript has a base Error object, and all built-in errors inherit from it.  
> The main error types are:  
> **SyntaxError, ReferenceError, TypeError, RangeError, URIError, EvalError, and AggregateError.**  
> They all represent different failure scenarios like wrong syntax, missing variables, invalid types, and so on.

---
