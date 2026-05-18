What is JSON?
**JSON** stands for **JavaScript Object Notation**. It's a way to convert JavaScript objects/arrays into a **text string** so you can store or transfer them.

Why Do We Need JSON?
localStorage, sessionStorage, and cookies can **only store text (strings)**. They cannot directly store objects or arrays.

What is JSON?
**JSON** stands for **JavaScript Object Notation**.
 It is a **lightweight data format** used to **store and transfer data** between systems (browser ↔ server).
- Text-based
- Easy to read and write
- Language-independent (not only for JavaScript)
Even though it looks like a JavaScript object, **JSON is just a string format**, not a JS object.


Why JSON exists (simple idea)
Imagine:
- Your browser asks a server for user details
- Server responds with data

The data must be:  
Easy to understand  
Easy to send over the network

Example of JSON
```json
{
  "name": "Raghavendra",
  "age": 25,
  "isEmployee": true,
  "skills": ["Java", "JavaScript"]
}
```

Important JSON rules
- Keys must be in **double quotes**    
- Values can be:
    - String
    - Number
    - Boolean
    - Array
    - Object
- ❌ No functions
- ❌ No comments

JSON vs JavaScript Object

| JavaScript Object          | JSON                       |
| -------------------------- | -------------------------- |
| Used in code               | Used for data transfer     |
| Keys can be without quotes | Keys **must** be in quotes |
| Can contain functions      | ❌ Functions not allowed    |
| Not a string               | Always a string            |

Example:
```js
// JavaScript Object
const user = { name: "Raghavendra" };

// JSON (string)
const userJSON = '{ "name": "Raghavendra" }';
```

#### Where do we use JSON in JavaScript?
##### Fetching data from APIs
Most APIs send data in JSON format.
```js
fetch("https://api.example.com/users")
  .then(res => res.json())
  .then(data => console.log(data));
```

##### Sending data to a server
When submitting forms or data.
```js
fetch("/saveUser", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Raghavendra", age: 25 })
});
```

##### Storing data in browser (localStorage)
```js
localStorage.setItem(
  "user",
  JSON.stringify({ name: "Raghavendra" })
);

const user = JSON.parse(localStorage.getItem("user"));
```

Configuration files
Many config files use JSON:
- `package.json`
- `.json` settings files

#### JSON methods available in JavaScript:
JavaScript provides a **global `JSON` object** with **2 main methods**.
##### `JSON.stringify()`
Converts **JavaScript object → JSON string**
```js
const obj = { name: "Raghavendra", age: 25 };

const jsonString = JSON.stringify(obj);

console.log(jsonString);
// {"name":"Raghavendra","age":25}
```
Use this when:
- Sending data to server
- Saving data in localStorage

##### `JSON.parse()`
➡️ Converts **JSON string → JavaScript object**
```js
const jsonString = '{"name":"Raghavendra","age":25}';

const obj = JSON.parse(jsonString);

console.log(obj.name); // Raghavendra
```

Use this when:
- Receiving data from server
- Reading from localStorage


JSON.stringify() options (basic idea)
```js
JSON.stringify(obj, null, 2);
```
- Makes JSON **pretty readable**
- Mostly used for debugging


Common beginner mistakes ❌

❌ Parsing a JS object
```js
JSON.parse({ name: "A" }); // ERROR
```

✔ Correct:
```js
JSON.parse('{"name":"A"}');
```

❌ Using single quotes in JSON
```json
{ 'name': 'A' } ❌
```

✔ Correct:
```json
{ "name": "A" }
```

Real-life analogy
- **JavaScript Object** → Used inside your house
- **JSON** → Packed box to send via courier
- **stringify** → Packing items
- **parse** → Unpacking items

Interview-friendly summary

> **JSON** is a lightweight data-interchange format used to exchange data between client and server.  
> In JavaScript, JSON is mainly used while working with APIs, storing data in localStorage, and sending data over HTTP.  
> JavaScript provides `JSON.stringify()` to convert objects to JSON strings and `JSON.parse()` to convert JSON strings back into objects.

----
```javascript
// ❌ This WON'T work properly
const tasks = ['Buy milk', 'Study'];
localStorage.setItem('tasks', tasks); // Stores "[object Array]" - WRONG!

// ✅ This WILL work
localStorage.setItem('tasks', JSON.stringify(tasks)); // Converts to text
```

#### JSON.stringify() - Convert to String
Converts JavaScript data into a JSON string:
```javascript
// Array to string
const tasks = ['Buy milk', 'Study', 'Exercise'];
const tasksString = JSON.stringify(tasks);
console.log(tasksString); // '["Buy milk","Study","Exercise"]'

// Object to string
const user = { name: 'John', age: 25 };
const userString = JSON.stringify(user);
console.log(userString); // '{"name":"John","age":25}'

// Number/Boolean to string
JSON.stringify(42);    // "42"
JSON.stringify(true);  // "true"
```

#### JSON.parse() - Convert Back to JavaScript
Converts a JSON string back into JavaScript data:

```javascript
// String to array
const tasksString = '["Buy milk","Study","Exercise"]';
const tasks = JSON.parse(tasksString);
console.log(tasks[0]); // "Buy milk"

// String to object
const userString = '{"name":"John","age":25}';
const user = JSON.parse(userString);
console.log(user.name); // "John"
console.log(user.age);  // 25
```

#### Real Example: Storing Tasks
**Storing:**
```javascript
const tasks = ['Buy milk', 'Study JS', 'Exercise'];

// Step 1: Convert array to string
const tasksString = JSON.stringify(tasks);
console.log(tasksString); // '["Buy milk","Study JS","Exercise"]'

// Step 2: Store the string
localStorage.setItem('tasks', tasksString);
```

**Retrieving:**
```javascript
// Step 1: Get the string
const tasksString = localStorage.getItem('tasks');
console.log(tasksString); // '["Buy milk","Study JS","Exercise"]'

// Step 2: Convert string back to array
const tasks = JSON.parse(tasksString);
console.log(tasks);    // ['Buy milk', 'Study JS', 'Exercise']
console.log(tasks[0]); // "Buy milk"
```

**Shortcut (all in one line):**
```javascript
// Store
localStorage.setItem('tasks', JSON.stringify(tasks));

// Retrieve
const tasks = JSON.parse(localStorage.getItem('tasks'));
```

More Examples
Storing an Object:
```javascript
const user = {
  name: 'Alice',
  email: 'alice@email.com',
  age: 28
};

// Store
localStorage.setItem('user', JSON.stringify(user));

// Retrieve
const savedUser = JSON.parse(localStorage.getItem('user'));
console.log(savedUser.name);  // "Alice"
console.log(savedUser.email); // "alice@email.com"
```

Storing Array of Objects:
```javascript
const todos = [
  { id: 1, task: 'Buy milk', done: false },
  { id: 2, task: 'Study JS', done: true }
];

// Store
localStorage.setItem('todos', JSON.stringify(todos));

// Retrieve
const savedTodos = JSON.parse(localStorage.getItem('todos'));
console.log(savedTodos[0].task); // "Buy milk"
console.log(savedTodos[1].done); // true
```

Important Notes
**1. Simple strings don't need JSON:**
```javascript
// For simple strings, no JSON needed
localStorage.setItem('username', 'John');
const username = localStorage.getItem('username'); // "John"
```

**2. Handling null (when nothing is stored):**
```javascript
const tasks = JSON.parse(localStorage.getItem('tasks'));
console.log(tasks); // null (if nothing was stored)

// Better way - provide default value:
const tasks = JSON.parse(localStorage.getItem('tasks')) || [];
console.log(tasks); // [] (empty array if nothing stored)
```

**3. Always parse what you stringify:**
```javascript
// Stored with JSON.stringify
localStorage.setItem('data', JSON.stringify(myData));

// Must retrieve with JSON.parse
const data = JSON.parse(localStorage.getItem('data'));
```

Quick Summary

|Method|What it does|When to use|
|---|---|---|
|`JSON.stringify()`|JavaScript → String|Before storing data|
|`JSON.parse()`|String → JavaScript|After retrieving data|

**Think of it like this:**
- `JSON.stringify()` = Pack your data into a box (string) for storage
- `JSON.parse()` = Unpack the box to use your data again

---

