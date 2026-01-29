Await can only be used inside a async function, if it is used normally it will throw an error.

While Using Fetch, `await` should be used before fetch, If await is not used before fetch, fetch will return promise object. The code won't pause until fetched value to be returned. it will return `Promise { <pending> }`.

An `async` function **always returns a Promise**, no matter what you `return` inside it. It returns a Promise that will eventually resolve to `data`.
- The below function will return promise.
```JavaScript
async function fetchData() {
  // ...
  return data;
}
```
Think of it like JavaScript automatically wraps your return value:
```JavaScript
async function fetchData() {
  return data;
}

// behaves like:
function fetchData() {
  return Promise.resolve(data);
}
```

1) await rules
- Normally, `await` can only be used inside an `async` function.
- Exception: In ES Modules (`<script type="module">`), top-level `await` is allowed.

2) Why fetch() returns a Promise
- `fetch(url)` is asynchronous (network call).
- So it returns a Promise that will later resolve to a `Response` object.
  Example:
  const responsePromise = fetch(url); // Promise { <pending> }

3) What `await fetch(url)` does
- `await fetch(url)` pauses ONLY the current async function until the Promise resolves.
- It does NOT freeze the whole page / UI. Other code and events can still run.

4) Usually you need TWO awaits with fetch
- 1st await: wait for the response headers/status
  const response = await fetch(url);
- 2nd await: wait for the body to be read/parsed
  const data = await response.json();

5) async functions always return a Promise
- Any function marked `async` always returns a Promise, even if you `return data`.
  Example:
  async function fetchData() { return data; }

- Think of it like:
  function fetchData() { return Promise.resolve(data); }

6) Error handling facts (important!)
- fetch() Promise rejects mainly for network errors / CORS / offline.
- For HTTP errors like 404 or 500, fetch still resolves successfully.
  So you should check:
  if (!response.ok) throw new Error(`HTTP error! Status: ${response.status}`);

7) Errors + Promises in async functions
- If an error is thrown inside an async function and NOT caught,
  the returned Promise becomes REJECTED.
- If you catch the error inside the async function and do NOT re-throw it,
  the Promise usually RESOLVES (often with `undefined`), so an outside `.catch()` may not run.

8) Getting the result of an async function
- Since `fetchData()` returns a Promise, you must use:
  a) await
     const data = await fetchData();
  OR
  b) then()
     fetchData().then(data => { ... });
- You cannot get the real value synchronously like:
  const data = fetchData(); // this is a Promise, not the JSON

