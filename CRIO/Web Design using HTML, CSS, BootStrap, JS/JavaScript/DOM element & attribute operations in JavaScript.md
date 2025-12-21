**Create → Select → Insert → Update → Remove → Attribute → Event**
## 1️⃣ Creating Elements & Nodes

|Method / Property|Description|
|---|---|
|`document.createElement(tagName)`|Creates a new HTML element|
|`document.createTextNode(text)`|Creates a text node|
|`document.createComment(text)`|Creates a comment node|
|`document.createDocumentFragment()`|Creates a lightweight container for multiple nodes|
|`element.cloneNode(true/false)`|Clones an element (`true` = deep clone)|

---

## 2️⃣ Accessing / Selecting Elements

|Method / Property|Description|
|---|---|
|`document.getElementById(id)`|Selects element by ID|
|`document.getElementsByClassName(class)`|Selects elements by class (HTMLCollection)|
|`document.getElementsByTagName(tag)`|Selects elements by tag name|
|`document.querySelector(css)`|Selects first matching element|
|`document.querySelectorAll(css)`|Selects all matching elements (NodeList)|
|`element.children`|Returns only element children|
|`element.childNodes`|Returns all child nodes (text + elements)|
|`element.parentElement`|Returns parent element|
|`element.nextElementSibling`|Next sibling element|
|`element.previousElementSibling`|Previous sibling element|

---

## 3️⃣ Adding / Inserting Elements into DOM

|Method / Property|Description|
|---|---|
|`parent.appendChild(child)`|Adds element at the end|
|`parent.append(node1, node2)`|Adds multiple nodes/text|
|`parent.prepend(node)`|Adds element at the beginning|
|`element.insertBefore(newNode, refNode)`|Inserts before a reference node|
|`element.insertAdjacentElement(pos, el)`|Inserts element at a position|
|`element.insertAdjacentHTML(pos, html)`|Inserts HTML string|
|`element.insertAdjacentText(pos, text)`|Inserts text|

---

## 4️⃣ Updating / Modifying Elements (Content & Style)

|Method / Property|Description|
|---|---|
|`element.innerHTML`|Gets/sets HTML content|
|`element.innerText`|Gets/sets visible text|
|`element.textContent`|Gets/sets all text|
|`element.style.property`|Updates inline CSS|
|`element.className`|Gets/sets class name|
|`element.classList.add()`|Adds class|
|`element.classList.remove()`|Removes class|
|`element.classList.toggle()`|Toggles class|
|`element.classList.replace()`|Replaces class|

---

## 5️⃣ Removing / Clearing Elements

|Method / Property|Description|
|---|---|
|`element.remove()`|Removes element from DOM|
|`parent.removeChild(child)`|Removes child element|
|`element.innerHTML = ""`|Clears all children|
|`element.replaceWith(newNode)`|Replaces element|
|`parent.replaceChild(newNode, oldNode)`|Replaces child|

---

## 6️⃣ Creating & Managing Attributes

|Method / Property|Description|
|---|---|
|`element.setAttribute(name, value)`|Adds/updates attribute|
|`element.getAttribute(name)`|Gets attribute value|
|`element.removeAttribute(name)`|Removes attribute|
|`element.hasAttribute(name)`|Checks if attribute exists|
|`document.createAttribute(name)`|Creates attribute node (rarely used)|

---

## 7️⃣ Direct Attribute Properties (Preferred Way)

|Method / Property|Description|
|---|---|
|`element.id`|Gets/sets id|
|`element.href`|Gets/sets link URL|
|`element.src`|Gets/sets image source|
|`element.value`|Gets/sets input value|
|`element.checked`|Gets/sets checkbox state|
|`element.disabled`|Enables/disables element|
|`element.placeholder`|Sets input placeholder|

---

## 8️⃣ Event Handling on Elements

|Method / Property|Description|
|---|---|
|`element.addEventListener(event, fn)`|Attaches event listener|
|`element.removeEventListener(event, fn)`|Removes event listener|
|`element.onclick = fn`|Inline event handler|

---

## 9️⃣ 🔹 Additional Important Operations (Often Missed)

|Method / Property|Description|
|---|---|
|`element.matches(css)`|Checks if element matches selector|
|`element.closest(css)`|Finds nearest matching ancestor|
|`element.contains(node)`|Checks child relationship|
|`element.dataset`|Access `data-*` attributes|
|`element.focus()`|Focuses element|
|`element.blur()`|Removes focus|
|`element.scrollIntoView()`|Scrolls element into view|

---
