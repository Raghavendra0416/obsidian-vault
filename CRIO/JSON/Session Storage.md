We will store **user data** in `sessionStorage` as **JSON** and perform:
- **C**reate → Add data
- **R**ead → Get data
- **U**pdate → Modify data
- **D**elete → Remove data

📌 `sessionStorage` stores data **only for the current browser tab**.


Sample data structure (JavaScript Object)

```js
{
  name: "Raghavendra",
  age: 25,
  role: "Developer"
}
```
This object **must be converted to JSON** before storing.


#### CREATE – Add data to sessionStorage
```js
const user = {
  name: "Raghavendra",
  age: 25,
  role: "Developer"
};

// Convert object → JSON string
sessionStorage.setItem("user", JSON.stringify(user));
```
✔ Data is now stored in sessionStorage as JSON

#### READ – Get data from sessionStorage
```js
const storedUser = sessionStorage.getItem("user");

// Convert JSON string → object
const userObj = JSON.parse(storedUser);

console.log(userObj.name); // Raghavendra
```
📌 Always use `JSON.parse()` when reading JSON data.

#### UPDATE – Modify existing data
```js
const storedUser = JSON.parse(sessionStorage.getItem("user"));

// Update value
storedUser.age = 26;

// Save updated object back
sessionStorage.setItem("user", JSON.stringify(storedUser));
```

✔ Update = **Read → Modify → Save again**


#### DELETE – Remove data
Delete specific key
```js
sessionStorage.removeItem("user");
```

OR clear all sessionStorage data
```js
sessionStorage.clear();
```

#### Full CRUD flow (compact view)
```js
// CREATE
sessionStorage.setItem("user", JSON.stringify({ name: "Raghavendra", age: 25 }));

// READ
const user = JSON.parse(sessionStorage.getItem("user"));

// UPDATE
user.age = 26;
sessionStorage.setItem("user", JSON.stringify(user));

// DELETE
sessionStorage.removeItem("user");
```


Common beginner mistakes ❌
❌ Forgetting `JSON.stringify`
```js
sessionStorage.setItem("user", user); // WRONG
```

❌ Forgetting `JSON.parse`
```js
const user = sessionStorage.getItem("user");
console.log(user.name); // ERROR
```

✔ Correct:
```js
const user = JSON.parse(sessionStorage.getItem("user"));
```

Interview-friendly explanation

> sessionStorage stores data as **strings**.  
> When storing objects, we convert them to JSON using `JSON.stringify()`.  
> When reading, we convert JSON strings back to objects using `JSON.parse()`.  
> CRUD operations are done using `setItem`, `getItem`, `removeItem`, and `clear`.


