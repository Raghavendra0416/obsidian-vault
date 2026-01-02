### CRUD on **Elements**

#### Create (C):
Create a new HTML element
```js
const div = document.createElement("div");
```
```JavaScript
// 1. Create the element
const newBtn = document.createElement('button');

// 2. Add content to it
newBtn.textContent = 'Click Me';

// 3. Attach it to the body (or any other parent)
document.body.appendChild(newBtn);
```

#### Read (R):
Access existing elements
```js
document.getElementById("id");
document.getElementByClass("class");
document.getElementBytagName("tag");
document.querySelector(".class");
document.querySelectorAll("p");
```

Read content:
```js
element.textContent;
element.innerHTML;
```

#### Update (U):
Change element content or style
```js
element.textContent = "Hello";
element.innerHTML = "<b>Hello</b>";
element.style.color = "red";
```

#### Delete (D)
Remove element from DOM
```js
element.remove();
```
or
```js
parent.removeChild(child);
```

---
### CRUD on **Attributes**

#### Create / Add (C)
Add a new attribute.
In JavaScript, creating and updating attributes is often the same method. If the attribute doesn't exist, it is created. If it does, it is updated.
- **`element.setAttribute(name, value)`**: Standard method.
- **Direct Property Access**: `element.id = 'newId'`.

```js
element.setAttribute("id", "box");
element.setAttribute("class", "card");
```
```JavaScript
const link = document.querySelector('a');

// Create/Update the 'href' attribute
link.setAttribute('href', 'https://google.com');

// OR using direct property (common for standard attributes)
link.id = 'nav-link';
link.className = 'active-link'; // Note: use 'className' for class
```

#### Read (R) 
Get attribute value
```js
element.getAttribute("id");
element.hasAttribute("class");
```

#### Update (U)
Change attribute value
```js
element.setAttribute("class", "card active");
```

Direct property update:
```js
element.id = "newId";
element.className = "newClass";
```

#### Delete (D)
Remove attribute
```js
element.removeAttribute("class");
```


#### Summary Table:

| **Operation** | **Elements (Nodes)**                  | **Attributes (Props)**              |
| ------------- | ------------------------------------- | ----------------------------------- |
| **Create**    | `createElement()`, `appendChild()`    | `setAttribute()`, `el.prop = value` |
| **Read**      | `querySelector()`, `getElementById()` | `getAttribute()`, `el.prop`         |
| **Update**    | `textContent`, `innerHTML`            | `setAttribute()`, `el.prop = value` |
| **Delete**    | `remove()`                            | `removeAttribute()`                 |

#### CRUD on **Classes (Special Case of Attributes)**

|Operation|Code|
|---|---|
|Add|`element.classList.add("active")`|
|Read|`element.classList.contains("active")`|
|Update|`element.classList.replace("old","new")`|
|Delete|`element.classList.remove("active")`|
