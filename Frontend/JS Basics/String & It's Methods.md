W3Schools - [String]([https://www.w3schools.com/jsref/jsref_obj_string.asp](https://www.w3schools.com/jsref/jsref_obj_string.asp))
##### Declaration and Initialization 
You have three syntaxes for creating a string. While single and double quotes are functionally the same, backticks (template literals) offer more features.

1. Single Quotes ('...')
    A common and simple way to create a string.
```JavaScript
const singleQuoteStr = 'Hello, world!';
```

2. Double Quotes ("...")
	Works identically to single quotes. The choice between them is a matter of coding style or convenience when one type of quote needs to be included within the string.
```JavaScript
const doubleQuoteStr = "It's a beautiful day.";
```
    
3. Template Literals (Backticks `...`)
    This is the most modern and powerful syntax. It allows for:
    - **Expression Interpolation**: You can embed variables and expressions directly into the string using `${...}`.
    - **Multi-line Strings**: You can create strings that span multiple lines without special characters.
```JavaScript
const name = "Alex";
const tempLiteralStr = `Hello, ${name}!
Welcome to our site.`;

console.log(tempLiteralStr);
// Output:
// Hello, Alex!
// Welcome to our site.
```

---
##### Very Important Points to Remember While Working with Strings

1. **Strings are immutable**
    - You **cannot change** a string once it is created. Every string method that seems to "modify" a string actually returns a **new string**.

2. **Strings are indexed**
    - Characters can be accessed using `str[index]` or `str.charAt(index)`. Indexing starts at 0.

3. **Use strict comparison for equality**
    - Always use `===` when comparing strings to avoid type coercion.

4. **`+` operator concatenates strings**
    - Adding strings with `+` joins them. If one operand is a string, the other will be coerced to a string.

5. **Template literals are preferred over concatenation**
    - Use backticks (`` ` ``) with `${}` placeholders to improve readability and avoid errors.

6. **Use `.length` to get character count**
    - Returns the number of UTF-16 code units (not actual Unicode characters in all cases).

7. **Escape characters carefully**
    - Use `\\`, `\'`, `\"`, `\n`, `\t`, etc., to include special characters inside string literals.

8. **Case sensitivity**
    - String comparisons are case-sensitive. `"Hello"` ≠ `"hello"`.

9. **Use `trim()` before storing/validating user input**
    - Prevents whitespace issues in user-entered strings.

10. **Avoid using `new String()`**
    - It creates a string object instead of a primitive. Use string literals instead (`let str = "abc"`).

---
##### String Immutability in JavaScript
**What it means:**
- **Immutability** means once a string is created, it **cannot be changed** in memory.
- Any operation that _appears_ to change a string (like `toUpperCase()` or `replace()`) **actually returns a new string**.

Example:
```js
let str = "hello";
str[0] = "H";       // ❌ Invalid! Has no effect
console.log(str);   // "hello"

let newStr = str.toUpperCase();  // ✅ Creates a new string
console.log(newStr);             // "HELLO"
```

Why it matters:
- Efficient memory use
- Safe sharing between scopes or functions (strings won’t be accidentally changed)
- Helps with debugging and functional programming patterns

##### Template Literals in JavaScript

What are Template Literals?
- Introduced in **ES6**
- Use **backticks** (`` ` ``) instead of quotes
- Allow **multi-line strings**, **embedded expressions**, and **improved readability**

Syntax:
```js
const name = "Alice";
const age = 25;
const message = `My name is ${name} and I am ${age} years old.`;
```

Key Features:
- **Multi-line support:**
```js
const poem = `Roses are red,
Violets are blue.`;
```

- **Expression embedding:**
```js
const total = 5 + 3;
console.log(`Total: ${total}`);  // "Total: 8"
```

##### Template Literals vs Traditional Concatenation

|Feature|Template Literals|Traditional Concatenation|
|---|---|---|
|Syntax|`` `Hello, ${name}` ``|`"Hello, " + name`|
|Multi-line support|Native (with backticks)|Requires `\n` or concatenation|
|Readability|High – clean and embedded expressions|Low – messy with multiple `+` operators|
|Expression evaluation|Inside `${}`|Manual concatenation needed|
|Error-prone (quotes/braces)|Low|Higher – mixing quotes and variables|

Example Comparison:
Traditional:
```js
let greeting = "Hello, " + name + ". You are " + age + " years old.";
```

Template Literal:
```js
let greeting = `Hello, ${name}. You are ${age} years old.`;
```

---

##### Methods in String:
###### Searching and Finding Substrings

|Method|Description|Returns|
|---|---|---|
|`indexOf(substring)`|Finds the first occurrence of the substring|Index (number) or `-1`|
|`lastIndexOf(substring)`|Finds the last occurrence of the substring|Index (number) or `-1`|
|`includes(substring)`|Checks if substring exists in string|`true` or `false`|
|`startsWith(prefix)`|Checks if string starts with the given prefix|`true` or `false`|
|`endsWith(suffix)`|Checks if string ends with the given suffix|`true` or `false`|
|`search(regex)`|Searches string using regex and returns the index of match|Index (number) or `-1`|
|`match(regex)`|Retrieves matches for a regex pattern|Array of matches or `null`|

###### Extracting Parts of Strings

|Method|Description|Returns|
|---|---|---|
|`slice(start, end)`|Extracts section of string between start and end|New string|
|`substring(start, end)`|Similar to `slice`, but does not accept negative indexes|New string|
|`substr(start, length)`|Extracts substring with given length (deprecated)|New string|

###### Checking and Testing Strings

|Method|Description|Returns|
|---|---|---|
|`includes(substring)`|Checks for presence of substring|`true` or `false`|
|`startsWith(prefix)`|Checks if string begins with specified prefix|`true` or `false`|
|`endsWith(suffix)`|Checks if string ends with specified suffix|`true` or `false`|
|`match(regex)`|Tests for pattern and returns matches|Array or `null`|
|`search(regex)`|Searches for pattern and returns position|Index or `-1`|

###### Modifying and Replacing Content

|Method|Description|Returns|
|---|---|---|
|`replace(find, value)`|Replaces first occurrence of pattern with given value|New string|
|`replaceAll(find, value)`|Replaces all matches of pattern|New string|
|`toUpperCase()`|Converts all characters to uppercase|New string|
|`toLowerCase()`|Converts all characters to lowercase|New string|
|`trim()`|Removes whitespace from both ends|New string|
|`trimStart()` / `trimEnd()`|Removes whitespace from start or end|New string|
|`padStart(length, char)`|Pads string at start to reach target length|Padded string|
|`padEnd(length, char)`|Pads string at end to reach target length|Padded string|

###### Combining or Repeating Strings

|Method|Description|Returns|
|---|---|---|
|`concat(string)`|Joins two or more strings|New string|
|`repeat(count)`|Repeats string `count` times|New string|

###### Character Retrieval

|Method|Description|Returns|
|---|---|---|
|`charAt(index)`|Returns character at specified index|Character|
|`charCodeAt(index)`|Returns UTF-16 code of character|Number|
|`codePointAt(index)`|Returns Unicode code point at index|Number|

###### Conversion and Splitting

|Method|Description|Returns|
|---|---|---|
|`split(separator)`|Splits string into array using given separator|Array of substrings|
|`toString()`|Returns the string itself|String|
|`valueOf()`|Returns primitive value of string object|String|

---

