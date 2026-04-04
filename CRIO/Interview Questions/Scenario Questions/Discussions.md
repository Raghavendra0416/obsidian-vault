#### Scenario:
There are 2 script tags. 
```HTML
Used 1st | module type script tag
<script type="module" src="my-module.js"></script> 
<script src="my-standard-script.js"></script> Used 2nd | standard script tag
```

Q. If the script tags are given in this order which script runs 1st? 
Ans: 
The 2nd script tag runs first. Why?
Because of different "Traffic rules".

Even if the Module script is tiny and downloads instantly, and the Standard script is huge and takes 5 seconds to download, the browser **holds the Module script back intentionally**. It is not a race of speed; it is a rule of law.

**Standard `<script>` is a STOP Sign:** When the browser sees a standard script, it **stops everything**. It stops building the page, stops reading the HTML, and focuses 100% on downloading and running that script. It refuses to move to the next line of code until that script is done. This is called "Parser Blocking."

**Module `<script type="module">` is a "Park and Wait" Sign:** When the browser sees a module, it starts downloading it in the background, but the car keeps driving. It reads the rest of the HTML. It effectively says to the module: _"You wait here. Do not run until I have finished reading the entire HTML file."_

- **Complexity:** Modules can import _other_ modules (e.g., `import { x } from './other.js'`). The browser needs to download the main file, read it, find the imports, download _those_, and build a complete map of dependencies. If it stopped the whole page to do this, your website would freeze for a long time.
- **Performance:** Modern web development prefers that the visual part of your website (HTML/CSS) loads first so the user sees something. By deferring modules automatically, the browser ensures the user sees the page content before the heavy JavaScript logic kicks in.

What do we need to do to run module 1st?
Use defer in the standard script.
If Defer is used then after the HTML loads, window will load module script and will standard script.

---
#### Import and Export in JS.

HTML <-- (Export / Import Data) --> JS 
JS <---- (Export / Import Data) --> JS

How to do it?
- HTML does not export anything.
- `import/export` is about **code modules**, not DOM content.

- **HTML loads JS** using `<script>`
- JS imports/exports only with other JS modules.
- JS “talks to HTML” using the **DOM** (`document.getElementById`, event listeners, etc.), not via import/export.

- **HTML → JS**: load your entry JS file
- **JS → JS**: use `export` and `import`
- **JS → HTML**: update DOM

Exporting Data from JS file:
```JavaScript
// app.js
export const greeting = "Hello from app.js 👋";

export function add(a, b) {
  return a + b;
}
```

```HTML
<!DOCTYPE html>
<html>
  <body>
    <h2 id="msg">---</h2>
    <p id="sum">---</p>

    <script type="module">
      import { greeting, add } from "./app.js";

      document.getElementById("msg").textContent = greeting;
      document.getElementById("sum").textContent = "2 + 3 = " + add(2, 3);
    </script>
  </body>
</html>
```

Exporting and Importing of data between 2 JS files.
```JavaScript
// math2.js
export function add(a, b) { return a + b; }
export function sub(a, b) { return a - b; }
```
```JavaScript
// main.js
import { add, sub } from "./math2.js";
```

Q. If we can access the files or data of html or JS using standard script then what is the use of import and export? (as far as i can understand it is useful for the transfer between the data between js files.)
Answer:

**import/export is mainly for sharing code between JS files**. The big difference is **how that sharing happens** and what it enables.
Why use `import` / `export` if `<script>` already works?
- **Avoid “global pollution”**: If both files have `function init(){}` → one can overwrite the other.
- **Clear dependencies (who uses what):** if `b.js` uses something from `a.js`, you must load `a.js` first.  That’s fragile.
- **Better structure for real projects:** Modules let you organize like:
	- `api.js` → fetch functions
	- `dom.js` → DOM creation
	- `utils.js` → helpers
	- `pages/adventures.js` → page logic
	Each file exports only what’s needed.
- **Reusability**: Same functions can be reused across pages without copying code.
- **Works with modern tooling:** Most modern setups (React, Vite, Webpack, Node, TypeScript) are built around ES modules. Learning import/export is basically required for modern JS development.

Q. When should you use which?(import/ standard script)?
Ans:
Use normal `<script>` when:
- tiny demo / very small page
- you don’t need multiple files or clean separation

Use `type="module"` + import/export when:
- more than one JS file
- you want clean structure (no globals)
- you have shared utilities
- you’re building an actual project


---


