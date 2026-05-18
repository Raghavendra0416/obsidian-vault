`async` and `defer` are **attributes of the `<script>` tag** used to **control how JavaScript files are loaded and executed** in relation to HTML parsing.

They help **improve page performance** and **avoid blocking the HTML rendering**.


Default behavior (without async/defer)
```html
<script src="app.js"></script>
```

What happens:
1. Browser starts parsing HTML
2. Encounters `<script>`
3. **Stops HTML parsing**
4. Downloads JS
5. Executes JS
6. Resumes HTML parsing

❌ This blocks page rendering and slows down page load.

#### `async`

```html
<script src="app.js" async></script>
```

How `async` works:
- Script is **downloaded in parallel** with HTML parsing
- Script is **executed immediately after download**
- **HTML parsing pauses during execution**
- **Execution order is NOT guaranteed**
##### Key points:
- Non-blocking download
- Execution happens as soon as the file is ready
- Scripts may execute **out of order**
- Best for **independent scripts**
##### Use cases:
- Analytics
- Ads
- Tracking scripts
- Third-party scripts
##### Example:
```html
<script async src="analytics.js"></script>
<script async src="ads.js"></script>
```

➡ `ads.js` may execute before `analytics.js` (order not guaranteed)

#### `defer`
```html
<script src="app.js" defer></script>
```

##### How `defer` works:
- Script is **downloaded in parallel** with HTML parsing
- Script is **executed after HTML parsing is complete**
- **Execution order IS guaranteed**

##### Key points:
- Non-blocking download
- Executes after DOM is ready
- Maintains script order
- DOM is fully available (`document.getElementById` works)

##### Use cases:
- Scripts that depend on DOM
- Main application logic
- Multiple dependent JS files

##### Example:
```html
<script defer src="utils.js"></script>
<script defer src="main.js"></script>
```

➡ `utils.js` always executes before `main.js`

#### `async` vs `defer` (Comparison Table)

|Feature|async|defer|
|---|---|---|
|HTML parsing blocked|❌ No (only during execution)|❌ No|
|Script download|Parallel|Parallel|
|Script execution|As soon as downloaded|After HTML parsing|
|Execution order|❌ Not guaranteed|✅ Guaranteed|
|DOM availability|❌ Not guaranteed|✅ Guaranteed|
|Best for|Independent scripts|DOM-dependent scripts|

#### What if both are used?
```html
<script src="app.js" async defer></script>
```
➡ **`async` takes priority**, `defer` is ignored.


#### Important interview points 
- `async` and `defer` **only work for external scripts**
- They **do not work for inline scripts**
- `defer` scripts behave like `DOMContentLoaded`
- Without `async/defer`, scripts are **render-blocking**

#### When to use what? (Interview-friendly)

- Use **`async`** for:
    - Analytics
    - Ads
    - Third-party scripts
    - Scripts that don’t depend on DOM or other scripts

- Use **`defer`** for:
    - Application logic
    - Scripts that access DOM
    - Scripts with dependencies

#### One-line interview summary

> **`async` loads scripts asynchronously and executes them immediately without order guarantee, while `defer` loads scripts asynchronously but executes them in order after HTML parsing is complete.**

#### Visual timeline: Normal vs async vs defer

![[Pasted image 20251219202154.png]]

![[Pasted image 20251219202215.png]]


#### 1️. Normal `<script>`
```
HTML parsing ──❌ STOP ── Download JS ── Execute JS ── Resume HTML
```
- HTML parsing is **blocked**
- Page load becomes slow

#### 2️. `<script async>`
```
HTML parsing ────────────────▶
           JS download ─────▶ Execute (pauses HTML briefly)
```
- Download happens **in parallel**
- Executes **immediately after download**
- ❌ **Order not guaranteed**


#### 3️. `<script defer>`
```
HTML parsing ────────────────▶ (complete)
           JS download ─────▶ Execute (in order)
```
- Download happens **in parallel**
- Execution happens **after HTML parsing**
- ✅ **Order guaranteed** 

---
