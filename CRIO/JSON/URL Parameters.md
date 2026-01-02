What are URL Parameters?
URL parameters are **key–value pairs** added to the URL after `?`.
Example:
```Text
https://example.com/profile?name=Raghavendra&age=25
```

- `?` → start of parameters
- `&` → separates parameters
- `name`, `age` → keys
- `Raghavendra`, `25` → values

URL parameters are **always strings**


JavaScript tool used: `URLSearchParams`
```js
const params = new URLSearchParams(window.location.search);
```

This object helps us **read, add, update, and delete** URL parameters.


#### CRUD Operations using URL Parameters

##### CREATE – Add parameters to URL

##### Example: Add user data to URL
```js
const params = new URLSearchParams();

params.set("name", "Raghavendra");
params.set("age", 25);

// Update URL (without reload)
window.history.pushState({}, "", "?" + params.toString());
```

📌 URL becomes:
```
?name=Raghavendra&age=25
```

##### READ – Get parameters from URL
```js
const params = new URLSearchParams(window.location.search);

const name = params.get("name");
const age = params.get("age");

console.log(name); // Raghavendra
console.log(age);  // 25
```

##### UPDATE – Modify existing parameters
```js
const params = new URLSearchParams(window.location.search);

// Update value
params.set("age", 26);

// Update URL
window.history.pushState({}, "", "?" + params.toString());
```

✔ Old value replaced with new one


##### DELETE – Remove parameters
Remove a single parameter
```js
const params = new URLSearchParams(window.location.search);

params.delete("age");

window.history.pushState({}, "", "?" + params.toString());
```

Clear all parameters
```js
window.history.pushState({}, "", window.location.pathname);
```

✔ URL becomes clean (no `?`)

#### Full CRUD Flow (compact)
```js
// CREATE
const params = new URLSearchParams();
params.set("user", "Raghavendra");

// READ
const user = params.get("user");

// UPDATE
params.set("user", "Raghu");

// DELETE
params.delete("user");

window.history.pushState({}, "", "?" + params.toString());
```

#### Working with MULTIPLE values (array-like)
URL:
```
?skills=Java&skills=JS
```

##### READ
```js
const params = new URLSearchParams(window.location.search);
const skills = params.getAll("skills");

console.log(skills); // ["Java", "JS"]
```
##### CREATE
```js
params.append("skills", "Java");
params.append("skills", "JS");
```

##### Common beginner mistakes ❌

❌ Expecting numbers
```js
params.get("age"); // "25" (string)
```

✔ Convert manually
```js
Number(params.get("age"));
```

❌ Trying to store large or sensitive data  
➡ URL params are **visible to everyone**



When to use URL Parameters?
Page navigation  
Filters (search, sort, pagination)  
Passing data between pages  
Not for passwords or large objects


##### URL Parameters vs localStorage vs sessionStorage

|Feature|URL Params|sessionStorage|localStorage|
|---|---|---|---|
|Stored in URL|✔|❌|❌|
|Persists refresh|✔|✔|✔|
|Persists browser close|✔|❌|✔|
|Size|Very small|~5MB|~5MB|
|Secure|❌|✔|✔|

##### Interview-ready explanation 

> URL parameters are key–value pairs appended to the URL to pass data between pages.  
> In JavaScript, they are accessed and manipulated using the `URLSearchParams` API.  
> CRUD operations are performed using `get`, `set`, `append`, and `delete`, and the URL is updated using the History API.
