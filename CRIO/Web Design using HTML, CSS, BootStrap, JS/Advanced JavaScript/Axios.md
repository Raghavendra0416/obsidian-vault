[`Axios` Examples](https://jasonwatmore.com/post/2021/06/25/axios-http-post-request-examples)

### What is `Axios`?
`Axios` is a popular JavaScript library used to make **HTTP requests** (API calls), like:
- GET (read data)
- POST (send data)
- PUT/PATCH (update data)
- DELETE (remove data)

It works in:
- **Browser** (frontend)
- **Node.js** (backend)

Think of it as an enhanced version of fetch with extra conveniences built in.


### Why use `Axios` if you already know fetch?
Fetch is totally fine. `Axios` is mostly about **convenience + better defaults**.

Key differences you’ll feel immediately:
1. JSON handling is simpler
	- **fetch**: you manually do `await response.json()`
	- `axios`: JSON is auto-parsed, and data is in `response.data`

2. Better error handling by default
	- **fetch** does **not** reject the promise for HTTP errors (like 404/500). You must check `response.ok`.
	- `axios` rejects automatically for non-2xx responses, so `catch` gets triggered.

3. Request/Response interceptors
	You can run code **before every request** and **after every response** (useful for tokens, logging, global error handling).

4. Timeouts + canceling requests are easier
	`Axios` supports request timeouts and cancellation more directly.

5. Automatic request transformation
	`Axios` can send JSON easily, and also handles `FormData` well.


### Getting Started
First, you need to install it:
```bash
npm install axios
```
Then import it:
```javascript
import axios from 'axios';
```


### Basic Usage Comparison
Here's where `Axios` shines compared to fetch. With **fetch**, you'd write:
```javascript
fetch('https://api.example.com/users')
  .then(response => {
    if (!response.ok) throw new Error('Network response was not ok');
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

With **Axios**, the same request is:
```javascript
axios.get('https://api.example.com/users')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```
Notice how you don't need to manually parse JSON or check if the response is okay—Axios handles that automatically.


### `Axios` POST request
```JavaScript
import axios from "axios";

const body = { name: "Sam", role: "Admin" };

const response = await axios.post("https://api.example.com/users", body);

console.log(response.data);
```
`Axios` automatically sends JSON (and sets headers in most cases).

### Understanding `Axios` response structure
`Axios` response looks like this:
- `response.data` → actual data from API (most important)
- `response.status` → HTTP status code (200, 201, etc.)
- `response.headers` → response headers
- `response.config` → request config used

Example:
```JavaScript
const res = await axios.get(url);
console.log(res.status);
console.log(res.data);
```
### Common Methods

`Axios` provides clean methods for different HTTP verbs:
```javascript
axios.get(url, config)
axios.post(url, data, config)
axios.put(url, data, config)
axios.delete(url, config)
```

For a POST request with data:
```javascript
axios.post('https://api.example.com/users', {
  name: 'John',
  email: 'john@example.com'
});
```

### Error handling in `Axios` (important)
`Axios` throws errors automatically for HTTP errors.
```JavaScript
try {
  const res = await axios.get("https://api.example.com/unknown");
  console.log(res.data);
} catch (err) {
  console.log("Message:", err.message);
  console.log("Status:", err.response?.status);
  console.log("Error data:", err.response?.data);
}
```
- `err.response` exists when server responded (like 404, 500)
- If it’s a network issue, `err.response` may be undefined


### The Response Object
When you get a response from `Axios`, it contains:
- `data` - the actual response body (already parsed)
- `status` - HTTP status code (200, 404, etc.)
- `statusText` - HTTP status message
- `headers` - response headers
- `config` - the request configuration
- `request` - the original request object

This is different from fetch where you work directly with the Response object and have to call methods on it.


### Sending headers (like Authorization)
```JavaScript
const token = "abc123";

const res = await axios.get(url, {
  headers: {
    Authorization: `Bearer ${token}`,
  },
});
```

### Query params (cleaner than manual string building)

Instead of:
```JavaScript
axios.get(`/adventures?city=${city}&sort=price`);
```
Do:
```Javascript
axios.get("/adventures", {
  params: { city, sort: "price" }
});
```
`Axios` builds the URL for you.


### Interceptors (super useful in real projects)
Run code automatically for every request/response.
```JavaScript
axios.interceptors.request.use((config) => {
  config.headers.Authorization = `Bearer ${token}`;
  return config;
});

axios.interceptors.response.use(
  (response) => response,
  (error) => {
    // global error handling
    return Promise.reject(error);
  }
);
```

### Creating an `Axios` instance (best practice)
Useful when you always use same base URL.
```JavaScript
const api = axios.create({
  baseURL: "https://api.example.com",
  timeout: 5000,
});

const res = await api.get("/users");
console.log(res.data);
```
This is similar to how you use `config.backendEndpoint` with fetch.


### Quick mental mapping (Fetch → `Axios`)
- `fetch(url)` → `axios.get(url)`
- `await response.json()` → already in `response.data`
- `response.ok` check → `axios` throws automatically
- manual query string → use `params: {}`


### Interceptors (super useful in real projects)

Run code automatically for every request/response.

``axios.interceptors.request.use((config) => {   config.headers.Authorization = `Bearer ${token}`;   return config; });  axios.interceptors.response.use(   (response) => response,   (error) => {     // global error handling     return Promise.reject(error);   } );``


### Creating an `Axios` instance (best practice)
Useful when you always use same base URL.

```JavaScript
const api = axios.create({   baseURL: "https://api.example.com",  
 timeout: 5000, });  
const res = await api.get("/users"); console.log(res.data);
```

This is similar to how you use `config.backendEndpoint` with fetch.

### Quick mental mapping (Fetch → `Axios`)
- `fetch(url)` → `axios.get(url)`
- `await response.json()` → already in `response.data`
- `response.ok` check → axios throws automatically
- manual query string → use `params: {}`