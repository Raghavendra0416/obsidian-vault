 What is `localStorage`?
- Stores data **permanently** (until manually cleared)
- Data remains even after **browser close / refresh**
- Stores **only strings** → we use **JSON**


Sample data (JavaScript Object)
```js
{
  name: "Raghavendra",
  age: 25,
  role: "Developer"
}
```

##### CREATE – Add data to localStorage
```js
const user = {
  name: "Raghavendra",
  age: 25,
  role: "Developer"
};

// Object → JSON
localStorage.setItem("user", JSON.stringify(user));
```
✔ Data is now saved permanently in the browser


##### READ – Get data from localStorage
```js
const storedUser = localStorage.getItem("user");

// JSON → Object
const userObj = JSON.parse(storedUser);

console.log(userObj.name); // Raghavendra
```


##### UPDATE – Modify existing data
```js
const user = JSON.parse(localStorage.getItem("user"));

// Update
user.age = 26;

// Save again
localStorage.setItem("user", JSON.stringify(user));
```

📌 Update pattern: **Read → Modify → Save**


##### DELETE – Remove data

Delete a specific key
```js
localStorage.removeItem("user");
```

OR clear everything
```js
localStorage.clear();
```


#### Full CRUD flow (compact)
```js
// CREATE
localStorage.setItem("user", JSON.stringify({ name: "Raghavendra", age: 25 }));

// READ
const user = JSON.parse(localStorage.getItem("user"));

// UPDATE
user.age = 26;
localStorage.setItem("user", JSON.stringify(user));

// DELETE
localStorage.removeItem("user");
```

#### CRUD with ARRAY of objects (very common in projects)

##### CREATE (initialize array if not exists)
```js
const users = JSON.parse(localStorage.getItem("users")) || [];

users.push({ id: 1, name: "Raghavendra" });

localStorage.setItem("users", JSON.stringify(users));
```

##### READ
```js
const users = JSON.parse(localStorage.getItem("users"));
console.log(users);
```

##### UPDATE_
```js
const users = JSON.parse(localStorage.getItem("users"));

const updatedUsers = users.map(user =>
  user.id === 1 ? { ...user, name: "Raghu" } : user
);

localStorage.setItem("users", JSON.stringify(updatedUsers));
```

##### DELETE
```js
const users = JSON.parse(localStorage.getItem("users"));

const filteredUsers = users.filter(user => user.id !== 1);

localStorage.setItem("users", JSON.stringify(filteredUsers));
```


Common mistakes ❌
❌ Storing object directly
```js
localStorage.setItem("user", user); // WRONG
```

✔ Correct
```js
localStorage.setItem("user", JSON.stringify(user));
```

❌ Forgetting parse
```js
const user = localStorage.getItem("user");
console.log(user.name); // ERROR
```

##### sessionStorage vs localStorage (quick)

|Feature|sessionStorage|localStorage|
|---|---|---|
|Lifetime|Tab session|Permanent|
|Survives refresh|✔|✔|
|Survives browser close|❌|✔|
|Size|~5MB|~5MB|

Interview-ready explanation ⭐

> localStorage is a Web Storage API that allows storing data in the browser permanently.  
> Since it stores only strings, JavaScript objects are converted to JSON using `JSON.stringify()` and retrieved using `JSON.parse()`.  
> CRUD operations are implemented using `setItem`, `getItem`, `removeItem`, and `clear`.

