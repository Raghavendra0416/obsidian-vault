## 1️⃣ What is an Event?

An **event** is something that happens in the browser.

Common examples:

- User clicks a button
    
- User types in an input box
    
- Page finishes loading
    
- Mouse moves over an element
    

👉 JavaScript can **listen** for these events and **run code** when they happen.

---

## 2️⃣ Basic Event Handling Flow

**3 simple steps:**

1. Select the HTML element
    
2. Choose the event (click, input, keyup, etc.)
    
3. Attach a function (what should happen)
    

---

## 3️⃣ Most Common Way: `addEventListener()`

This is the **recommended and modern way** ✅

### Example: Button Click

```html
<button id="btn">Click Me</button>
```

```js
// 1. Select element
const button = document.getElementById("btn");

// 2. Attach event listener
button.addEventListener("click", function () {
  alert("Button clicked!");
});
```

📌 **Explanation**

- `"click"` → event type
    
- `function () {}` → event handler (code that runs)
    

---

## 4️⃣ Using Arrow Function (Cleaner)

```js
button.addEventListener("click", () => {
  alert("Clicked using arrow function");
});
```

---

## 5️⃣ Common Event Types (Beginner-Friendly)

|Event|When it happens|
|---|---|
|`click`|Mouse click|
|`dblclick`|Double click|
|`mouseover`|Mouse enters element|
|`mouseout`|Mouse leaves element|
|`input`|User types in input|
|`change`|Input value changes|
|`keydown`|Key pressed|
|`keyup`|Key released|
|`submit`|Form submitted|
|`load`|Page loaded|

---

## 6️⃣ Handling Input Events

```html
<input type="text" id="name" />
```

```js
const input = document.getElementById("name");

input.addEventListener("input", () => {
  console.log(input.value);
});
```

👉 Runs **every time user types**

---

## 7️⃣ Handling Form Submit

```html
<form id="myForm">
  <input type="text" />
  <button>Submit</button>
</form>
```

```js
const form = document.getElementById("myForm");

form.addEventListener("submit", (event) => {
  event.preventDefault(); // stops page refresh
  console.log("Form submitted");
});
```

📌 `event.preventDefault()` is VERY important in forms.

---

## 8️⃣ What is the `event` Object?

JavaScript automatically gives **event details**.

```js
button.addEventListener("click", (event) => {
  console.log(event);
});
```

Common properties:

- `event.target` → element that triggered event
    
- `event.type` → event name (`click`)
    
- `event.key` → pressed key (keyboard events)
    

---

## 9️⃣ Inline Event Handling (NOT Recommended ❌)

```html
<button onclick="sayHi()">Click</button>
```

```js
function sayHi() {
  alert("Hi");
}
```

❌ Avoid this because:

- Mixes HTML & JS
    
- Hard to maintain
    

✅ Use `addEventListener` instead.

---

## 🔟 Multiple Events on Same Element

```js
button.addEventListener("click", () => {
  console.log("First event");
});

button.addEventListener("click", () => {
  console.log("Second event");
});
```

👉 Both will run ✔️

---

## 1️⃣1️⃣ Remove Event Listener

```js
function handleClick() {
  alert("Clicked");
}

button.addEventListener("click", handleClick);

// remove
button.removeEventListener("click", handleClick);
```

⚠️ Function reference must be same.

---

## 1️⃣2️⃣ Real-Life Example

```js
button.addEventListener("mouseover", () => {
  button.style.backgroundColor = "green";
});

button.addEventListener("mouseout", () => {
  button.style.backgroundColor = "";
});
```

---

## 🧠 Easy Way to Remember

👉 **Event Handling Formula**

```
element.addEventListener(eventName, function)
```

---

## 📌 Interview Tip (Important)

> **Q:** How do you handle events in JavaScript?  
> **A:** Using `addEventListener()` to attach event handlers to DOM elements.

---

#### **Three Ways to Attach Event Handlers**

The page explains **three methods** to attach event handlers — here are the main two beginners see most often:

🔹 **a) HTML event attributes**  
You put an `on` event directly in the HTML tag, like:

`<button onclick="alert('Clicked!')">Click me</button>`

Here `onclick` means _when the button is clicked, run this code_. [javascripttutorial.net](https://www.javascripttutorial.net/javascript-dom/handling-events-in-javascript/?utm_source=chatgpt.com)

🔹 **b) JavaScript event listener**  
You _select the element in JavaScript_ and then use `addEventListener()`. This is the modern and preferred way. [javascripttutorial.net](https://www.javascripttutorial.net/javascript-dom/handling-events-in-javascript/?utm_source=chatgpt.com)

Example:

`document.getElementById("btn").addEventListener("click", function () {     alert("Button clicked!"); });`

👉 This separates your HTML and JavaScript, which is cleaner and easier to maintain