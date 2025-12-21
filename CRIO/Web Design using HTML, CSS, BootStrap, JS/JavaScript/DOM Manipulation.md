**DOM** stands for **Document Object Model**.  
It is a **tree-like representation of HTML** that JavaScript can read and change.

👉 **DOM Manipulation** means **using JavaScript to access, modify, add, or remove HTML elements and their styles/content dynamically**.

---
#### 1️⃣ Why DOM Manipulation is needed
- Change content without reloading the page
- Handle user actions (click, input, submit)
- Build interactive web pages (forms, popups, validation)

**Example real life**:  
When you click a button and text changes → DOM manipulation.

---
#### 2️⃣ DOM Structure (Very Important)
```html
<html>
  <body>
    <h1>Hello</h1>
    <p>Welcome</p>
  </body>
</html>
```

- `document` → root object
- Elements → nodes
- Text → nodes
- Attributes → nodes

---
#### 3️⃣ Selecting Elements (Most Asked)

##### By ID
```js
document.getElementById("title");
```
##### By Class
```js
document.getElementsByClassName("box"); // HTMLCollection
```
##### By Tag
```js
document.getElementsByTagName("p");
```
##### Modern & Most Used
```js
document.querySelector(".box");      // first match
document.querySelectorAll(".box");   // NodeList
```

📌 **Interview tip**  
👉 Prefer `querySelector` / `querySelectorAll`

---
#### 4️⃣ Reading & Changing Content

##### Text

```js
element.innerText = "Hello";
element.textContent = "Hello";
```
##### HTML

```js
element.innerHTML = "<b>Hello</b>";
```

📌 **Difference**
- `innerText` → respects CSS (hidden text ignored)
- `textContent` → faster, raw text
- `innerHTML` → can inject HTML (⚠️ security risk)

---
#### 5️⃣ Changing Styles
```js
element.style.color = "red";
element.style.backgroundColor = "yellow";
```

Better Way (Recommended)
```js
element.classList.add("active");
element.classList.remove("active");
element.classList.toggle("active");
```
---
#### 6️⃣ Handling Events (Very Important)

Click Event

```js
button.addEventListener("click", function () {
  alert("Clicked!");
});
```

#### Common Events
- `click`
- `input`
- `change`
- `submit`
- `keydown`
- `mouseover`

📌 **Interview line**

> Events allow JavaScript to respond to user interactions.

---

#### 7️⃣ Creating & Removing Elements

##### Create

```js
const div = document.createElement("div");
div.innerText = "Hello";
document.body.appendChild(div);
```
##### Remove
```js
element.remove();
```

---

#### 8️⃣ DOM Manipulation vs Developer Tools

|DOM Manipulation|Developer Tools|
|---|---|
|Done via JavaScript|Manual editing|
|Changes persist in code|Temporary|
|Used in production|Only for debugging|

---

#### 9️⃣ Common Interview Questions

**Q1. Is DOM manipulation slow?**  
👉 Yes, frequent DOM changes are expensive.  
Solution: batch updates, use fragments.

**Q2. HTMLCollection vs NodeList?**

- HTMLCollection → live
- NodeList → static (mostly)

**Q3. innerHTML vs textContent?**

- `innerHTML` → HTML + risk
- `textContent` → safe

---

#### 10️. One-Line Definition (For Interview)

> DOM manipulation is the process of dynamically accessing and modifying HTML elements using JavaScript to create interactive web pages.

---
---
---
### CRUD using DOM Manipulation Main
The Below are the fundamental CRUD (Create, Read, Update, Delete) operations for manipulating the DOM:
#### **Create** - Adding elements to the DOM
```javascript
// Create a new element
const newDiv = document.createElement('div');
newDiv.textContent = 'Hello World';
newDiv.className = 'my-class';

// Append to body or another element
document.body.appendChild(newDiv);

// Insert before another element
const existingElement = document.getElementById('existing');
document.body.insertBefore(newDiv, existingElement);

// Insert adjacent HTML
document.body.insertAdjacentHTML('beforeend', '<p>New paragraph</p>');
```

#### **Read** - Accessing elements from the DOM
```javascript
// Get element by ID
const element = document.getElementById('myId');

// Get elements by class name (returns HTMLCollection)
const elements = document.getElementsByClassName('myClass');

// Get elements by tag name
const paragraphs = document.getElementsByTagName('p');

// Query selector (returns first match)
const firstDiv = document.querySelector('.my-class');

// Query selector all (returns NodeList)
const allDivs = document.querySelectorAll('div');

// Read element content
const text = element.textContent;
const html = element.innerHTML;

// Read attributes
const id = element.getAttribute('id');
const value = element.value; // for form inputs
```

#### **Update** - Modifying existing elements

```javascript
const element = document.getElementById('myElement');

// Update text content
element.textContent = 'New text';

// Update HTML content
element.innerHTML = '<strong>Bold text</strong>';

// Update attributes
element.setAttribute('class', 'new-class');
element.id = 'newId';

// Update styles
element.style.color = 'blue';
element.style.fontSize = '20px';

// Add/remove classes
element.classList.add('active');
element.classList.remove('inactive');
element.classList.toggle('visible');
```
#### **Delete** - Removing elements from the DOM

```javascript
// Remove element (modern way)
const element = document.getElementById('myElement');
element.remove();

// Remove child element (older way)
const parent = document.getElementById('parent');
const child = document.getElementById('child');
parent.removeChild(child);

// Remove all children
parent.innerHTML = '';

// Remove attribute
element.removeAttribute('class');
```

#### Practical Example

Here's a complete working example combining all CRUD operations:This interactive demo shows all CRUD operations in action. You can create items, read/display all items, update them, and delete them. Try typing some text and clicking "Create Item" to see it work!

Key takeaways:

- **Create**: Use `createElement()`, `appendChild()`, or `insertAdjacentHTML()`
- **Read**: Use `getElementById()`, `querySelector()`, or `querySelectorAll()`
- **Update**: Modify properties like `textContent`, `innerHTML`, `style`, or `className`
- **Delete**: Use `remove()` or `removeChild()`

---
### CRUD using DOM Manipulation (Concept + Minimal Code)
Assume this HTML **already exists**:

```html
<ul id="list">
  <li id="item1">Apple</li>
  <li id="item2">Banana</li>
</ul>
```
We will **only manipulate existing elements**.

----
#### 1️⃣ CREATE (Add new data to DOM)

👉 **Create = insert new content/element into DOM**

```js
const list = document.getElementById("list");

const newItem = document.createElement("li"); // create in memory
newItem.innerText = "Orange";

list.appendChild(newItem); // insert into DOM
```

📌 Even though you say _don’t create anything_,  
**conceptually CREATE = adding new node/content to DOM**.

---

#### 2️⃣ READ (Get data from DOM)

👉 **Read = fetch existing data from DOM**
```js
const item = document.getElementById("item1");
console.log(item.innerText);
```

OR read all items:
```js
const items = document.querySelectorAll("#list li");

items.forEach(li => {
  console.log(li.textContent);
});
```

📌 Used in:
- Showing values
- Validation
- Debugging

---
#### 3️⃣ UPDATE (Modify existing DOM content)

👉 **Update = change text / HTML / attribute / style**

##### Update text
```js
const item = document.getElementById("item2");
item.innerText = "Mango";
```
##### Update style
```js
item.style.color = "red";
```

##### Update class
```js
item.classList.add("highlight");
```

📌 No new element created — only modified.

---

#### 4️⃣ DELETE (Remove element from DOM)

👉 **Delete = remove existing DOM element**

```js
const item = document.getElementById("item1");
item.remove();
```

OR (older way):

```js
item.parentNode.removeChild(item);
```

---
#### CRUD Summary Table (Interview Ready)

|Operation|DOM Meaning|Example|
|---|---|---|
|Create|Add new node/content|`appendChild()`|
|Read|Get existing data|`innerText`, `textContent`|
|Update|Modify element|`innerText = ""`|
|Delete|Remove element|`remove()`|

---

#### One-Line Interview Answer

> CRUD operations using DOM manipulation involve adding, reading, modifying, and removing HTML elements dynamically using JavaScript without reloading the page.

---
#### Real-World Mapping

|App Feature|DOM CRUD|
|---|---|
|Add task|CREATE|
|Show task|READ|
|Edit task|UPDATE|
|Delete task|DELETE|

---
