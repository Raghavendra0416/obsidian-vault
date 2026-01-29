The `<input>` tag is the most powerful and versatile element in HTML forms. It is used to create interactive controls that allow users to enter data.

It is a **void element** (also known as a self-closing tag), meaning it does not have a closing tag (e.g., you write `<input />`, not `<input></input>`).

### 1. The Power of the `type` Attribute

The behavior of the `<input>` tag changes drastically based on its `type` attribute. Here are the most common types:

- **`type="text"`:** The default. A one-line text field.
- **`type="password"`:** Like text, but characters are masked (shown as dots or asterisks).
- **`type="email"`:** Validates that the text entered is a properly formatted email address.
- **`type="number"`:** Restricts input to numeric values and often provides up/down spinner arrows.
- **`type="checkbox"`:** A square box for selecting zero or more options.
- **`type="radio"`:** A round button for selecting exactly **one** option from a list.
- **`type="date"`:** Opens a native calendar picker date selector.
- **`type="file"`:** Allows the user to upload a file from their device.
- **`type="submit"`:** A button that sends the form data to the server.

There are also more visual input types introduced in HTML5:
- **`type="color"`:** Opens a color picker.
- **`type="range"`:** Displays a slider control for selecting a number within a range.

---
### 2. Common Attributes
To make inputs functional and accessible, you combine them with these key attributes:

|**Attribute**|**Description**|
|---|---|
|**`name`**|**Critical.** This is the identifier used by the server to understand which data point is which when the form is submitted.|
|**`id`**|Used to link the input to a `<label>` (for accessibility) or for CSS/JavaScript targeting.|
|**`placeholder`**|Displays grayed-out "hint" text inside the box that disappears when the user types.|
|**`value`**|The initial value inside the input. For buttons, this is the text on the button.|
|**`required`**|Prevents the user from submitting the form if the field is empty.|
|**`disabled`**|Greys out the input and prevents the user from clicking or typing in it.|

---
### 3. Code Example
Here is how you would construct a basic login form using various input types:

```HTML
<form action="/login" method="POST">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" placeholder="Enter your user ID" required>
  <br><br>

  <label for="pwd">Password:</label>
  <input type="password" id="pwd" name="password" required>
  <br><br>

  <input type="checkbox" id="remember" name="remember_me" value="yes">
  <label for="remember">Remember me</label>
  <br><br>

  <input type="submit" value="Log In">
</form>
```

> **Note on Accessibility:** Always pair your `<input>` with a `<label>` tag. Notice how the `for` attribute in the label matches the `id` of the input. This lets screen readers describe the field correctly and allows users to click the label text to focus the input box.

---
### Summary Table: When are they mandatory?

|**Attribute**|**Mandatory?**|**Role**|
|---|---|---|
|**`type`**|**Virtually Always**|Defines functionality and UI (e.g., text vs. checkbox).|
|**`name`**|**Always** (for forms)|Identifies the data when sending to the server.|
|**`id`**|**Always** (for accessibility)|Connects the input to its label.|
|**`value`**|**Sometimes**|Required for checkboxes, radios, and buttons; optional for text inputs.|
##### Example of a "Perfect" Input
Here is an input with all the practically mandatory fields included:

```HTML
<label for="user-email">Email Address:</label>

<input 
  type="email"        
  id="user-email"     
  name="email_address"
>
```
