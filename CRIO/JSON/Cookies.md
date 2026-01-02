What are Cookies?
Cookies are **small key–value data** stored in the browser and **sent to the server with every HTTP request**.

- Stored as **strings**
- Can have **expiry time**
- Limited size (~4 KB)
- Accessible via `document.cookie`

Example cookie:
```
username=Raghavendra
```

Cookie format (important)
```
key=value; expires=DATE; path=/
```

Example:
```
user=Raghavendra; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/
```

#### CRUD Operations using Cookies
##### CREATE – Set a Cookie

Basic cookie (session cookie)
```js
document.cookie = "user=Raghavendra";
```

📌 This cookie is deleted when the browser is closed.

##### Cookie with expiry (persistent)
```js
document.cookie =
  "user=Raghavendra; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/";
```


##### READ – Get Cookies
`document.cookie` returns **all cookies as a string**:
```js
console.log(document.cookie);
// user=Raghavendra; theme=dark
```

##### Read a specific cookie (simple helper)
```js
function getCookie(name) {
  const cookies = document.cookie.split("; ");
  for (let cookie of cookies) {
    const [key, value] = cookie.split("=");
    if (key === name) return value;
  }
  return null;
}

console.log(getCookie("user")); // Raghavendra
```


##### UPDATE – Update a Cookie

**Same as create**, just overwrite the value.
```js
document.cookie =
  "user=Raghu; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/";
```

✔ Old value is replaced


##### DELETE – Remove a Cookie

Set expiry date in the **past**
```js
document.cookie =
  "user=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/";
```

✔ Cookie deleted


#### Full CRUD Flow (compact)
```js
// CREATE
document.cookie = "role=developer; path=/";

// READ
console.log(document.cookie);

// UPDATE
document.cookie = "role=senior-developer; path=/";

// DELETE
document.cookie = "role=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/";
```

#### Storing JSON data in Cookies (Not recommended, but possible)
```js
const user = { name: "Raghavendra", age: 25 };

// CREATE
document.cookie = `user=${JSON.stringify(user)}; path=/`;

// READ
const storedUser = JSON.parse(getCookie("user"));
console.log(storedUser.name);
```

⚠️ **Avoid this in real apps** (size & security limits)


Common beginner mistakes ❌

❌ Expecting object storage  
Cookies store **only strings**

❌ Forgetting `path=/`  
Without it, deletion may fail

❌ Storing sensitive data  
Cookies are visible unless **HttpOnly** (server-side only)


#### Cookies vs localStorage vs sessionStorage

| Feature | Cookies | sessionStorage | localStorage |
|------|------|------|------|
| Sent to server | ✔ | ❌ | ❌ |
| Size limit | ~4 KB | ~5 MB | ~5 MB |
| Expiry | ✔ | Tab-based | Permanent |
| Accessible in JS | ✔ | ✔ | ✔ |
| Secure option | ✔ (HttpOnly) | ❌ | ❌ |


When should you use Cookies?
✅ Authentication (session IDs, tokens – server-side)  
✅ User preferences (theme, language – small data)  
❌ Large data storage  
❌ Client-only state (use localStorage instead)


Interview-ready explanation ⭐

> Cookies are small pieces of data stored in the browser and automatically sent with HTTP requests.  
> In JavaScript, cookies are managed using `document.cookie`.  
> CRUD operations are done by setting, reading, updating, and expiring cookies using string-based syntax.
