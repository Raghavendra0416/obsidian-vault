https://youtu.be/XF1_MlZ5l6M?si=iJfZTJMEwtvWt9XB
---
Definition:
An **event listener** in JavaScript is a function that waits for a specific event to occur on an element (like a click, keypress, or mouse movement) and then executes code in response.

----

Basic Syntax:
```javascript
element.addEventListener(event, function, options);
```

Simple Example:
```javascript
const button = document.querySelector('button');

button.addEventListener('click', function() {
  alert('Button was clicked!');
});
```
Syntax:
```JavaScript
addEventListener(type, listener)
addEventListener(type, listener, options)
addEventListener(type, listener, useCapture)
```
**Type:**
A case-sensitive string representing the Event Type to listen for.

**Listener:**
The object that receives a notification (an object that implements the Event interface) when an event of the specified type occurs. This must be `null`, an object with a `handleEvent()` method, or a JavaScript function. See The event listener callback for details on the callback itself.

**Options** (Optional):
An object that specifies characteristics about the event listener. The available options are:
- Capture
- Once
- Passive
- Signal

**capture (optional)**  
If `true`, the event listener runs _before_ any other elements inside it are notified — this is called the **capturing phase**.  
If not set, it defaults to `false`, meaning it runs during the normal **bubbling phase** (after inner elements handle the event).

**once (optional)**  
If `true`, the event listener will run **only one time**, then automatically remove itself.  
If not set, it runs every time the event happens.

**passive (optional)**  
If `true`, it means the listener **won’t call** `event.preventDefault()` (it just listens, doesn’t block anything).  
This helps improve performance for scrolling and touch events.  
By default, it’s `false`, except for some events like `wheel` and `touchmove`, where browsers often set it to `true`.

**signal (optional)**  
Lets you use an **AbortSignal** to automatically remove the event listener when `AbortController.abort()` is called.  
Useful for **cleaning up listeners** without manually calling `removeEventListener()`.

**UseCapture (optional)**  
If `true`, the event listener runs **in the capturing phase** — meaning it catches the event **before** it reaches inner elements.  
If `false` (the default), it runs **in the bubbling phase**, meaning it handles the event **after** it reaches inner elements.

Think of it like event travel:
- **Capturing:** top → down (outer to inner).
- **Bubbling:** bottom → up (inner to outer).
---
How It Works:
When you attach an event listener to an element, you're essentially telling JavaScript: "Watch this element, and when this specific thing happens, run this code."

Common Events:
- `click` - when an element is clicked
- `mouseover` - when the mouse moves over an element
- `keydown` - when a key is pressed
- `submit` - when a form is submitted
- `load` - when a page or image finishes loading
- `input` - when an input value changes

More Practical Example:
```javascript
const input = document.querySelector('input');

input.addEventListener('input', function(e) {
  console.log('You typed:', e.target.value);
});
```
The `e` (or `event`) parameter gives you information about the event that occurred, like which key was pressed or which element triggered it.


Removing Event Listeners:
You can also remove event listeners when you don't need them anymore:

```javascript
function handleClick() {
  console.log('Clicked!');
}

button.addEventListener('click', handleClick);
button.removeEventListener('click', handleClick);
```

Event listeners are fundamental to making interactive web pages—they're how you respond to user actions.


**Multiple Listeners** You can add multiple event listeners to the same element for the same event:
```javascript
button.addEventListener('click', function1);
button.addEventListener('click', function2);
// Both will execute when clicked
```

**Event Bubbling & Capturing** Events propagate through the DOM in phases:
```javascript
element.addEventListener('click', handler, true); // Capturing phase
element.addEventListener('click', handler, false); // Bubbling phase (default)
```

**Event Object Methods**:
- `e.preventDefault()` - stops default behavior (like form submission)
- `e.stopPropagation()` - stops event from bubbling up
- `e.target` - the element that triggered the event
- `e.currentTarget` - the element the listener is attached to

**Options Object**:
```javascript
element.addEventListener('click', handler, {
  once: true,      // Removes listener after first trigger
  passive: true,   // Improves scroll performance
  capture: false   // Use capturing phase
});
```

**Arrow Functions vs Regular Functions**:
```javascript
// Arrow function - 'this' refers to surrounding context
button.addEventListener('click', () => console.log(this));

// Regular function - 'this' refers to the element
button.addEventListener('click', function() { console.log(this); });
```

**Old Method (avoid)**:
```javascript
element.onclick = handler; // Only one handler allowed, can be overwritten
```
