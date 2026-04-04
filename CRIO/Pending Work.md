- Use Json data to populated in a table format.
- What is `URLSearchParms`? why do we use it?
- **`forEach` ignores the returned Promise** from an `async` callback, so it **doesn’t wait**. Your function finishes and returns before the fetches complete.
- **`map` collects the returned Promises** into an array, and then `Promise.all(...)` can **wait for all of them** to finish.

Need to Learn:
https://javascript.plainenglish.io/creating-material-ui-themes-in-react-cc839c9ee683