Session 4 - developer tools -  need to complete.
### 1. What are the differences between HTML and HTML5?
Answer:
HTML stands for hypertext markup language. and HTML5 is the newer version of HTML. HTML5 provides support to built in multi-media, less syntax, new API's and reduces the need for external plugins.

HTML5 simplifies the syntax for DOCTYPE HTML, and it also adds semantic elements like header, section, footer to provide more meaning to the page structure.

It also provides native support for audio, video and new form input types(like email, date, range, attributes). and older HTML relied more on plugins and presentational tags but HTML5 replaces them.

---
---
### 2. What are the differences between semantic and non-semantic HTML tags?
Answer:
Semantic tags provide meaning to a webpage by using tags like header, section, footer, article, nav -- and these tags provide purpose to both browsers and developers.

coming to non-semantic tags -- non-semantic tags uses div, span which mainly used for layout and styling.

and also semantic tags helps in improving SEO, accessibility and code maintainability.  

Examples:
   Semantic: < header>, < nav>, < main>, < article>, < section>, < aside>, < footer>, 
             < figure>, < time>
   Non-semantic: < div>, < span>

---
---

### 3. What is the purpose of the 'doctype' declaration in HTML documents?
Answer:
##### **Overview:**
The purpose of doctype declaration in HTML is to tell the browser how to interpret and render the page. 

and doctype is a declaration, not an HTML tag —so it doesn’t render anything.

By declaring the correct doctype, development tools (validators and IDEs) know which set of rules to apply and which standard it should follow. That helps in improving error checking and overall code quality.

and also doctype can control modes like standard and quirks mode for the browsers.

The Older HTML versions have long doctypes but HTML5 has simplified it to just `<!DOCTYPE html>`. 

##### **Detailed Explanation:**
“The `<!DOCTYPE html>` declaration is mainly about telling the browser _how_ to interpret and render the page.

By declaring the correct doctype, validators and IDEs know which set of rules to apply. That improves error checking, autocomplete, and overall code quality.

how it interpret and render the page:-
1. It tells the browser which HTML standard to use.
2. It’s a declaration, not an HTML tag: 
		It’s just an instruction to the browser’s rendering engine before parsing the rest of the document.
3. It controls _standards mode_ vs _quirks mode_. 
		What is standard mode?
		Ans: **Standards mode** – they follow the official HTML/CSS specs as closely as possible.
		What id Quirk mode?
		Ans: **Quirks mode** - where they emulate old, legacy behavior to avoid “breaking” old sites and that can lead to inconsistent layout, box model differences, and harder-to-debug CSS.
4. Older HTML versions had longer doctypes but HTML5 simplified all of that to just `<!DOCTYPE html>`. 

---
---

### 4. What are the differences between block elements, inline elements and inline-block elements?
Answer:

- **Block** — starts on a new line, fills available width; you can set **width/height**; vertical margins can **collapse**. (e.g., `div`, `p`)
- **Inline** — sits **within a line** like text; **can’t** set width/height (except replaced elements like `img`); vertical margins don’t affect line flow. (e.g., `span`, `a`)
- **Inline-block** — sits **inline** but behaves like a small block; you **can** set width/height; no margin collapsing; beware whitespace gaps between siblings.

- **Rule of thumb:** block = stacked sections, inline = text-level pieces, inline-block = side-by-side items with controllable size (badges/buttons).

| Block                                                                                  | In-Line                                                                                                   | In-Line Block                                                                                                                                    |
| -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Starts on a new line;**                                                              | **Starts within the same line like text.**                                                                | **Starts on the same line (no forced line break) if space allows.**                                                                              |
| **Takes up the full width available.**                                                 | **Takes up the width of the content**                                                                     | **Content-sized by default, but you _can_ set explicit `width/height`.**                                                                         |
| **Can contain an inline element**                                                      | **Cannot contain a block element (except for < a >).**<br>**- inline elements don’t accept width/height** | **Acts like a block _inside_: <br>- can contain inline and block content; <br>- forms its own formatting context; <br>- no margin collapsing.**  |
| **Examples of block elements -  < ol>,< div>,< ul>, < p>, < h1>, < h2> … < h6>, etc.** | **Examples of inline elements- < a>, < span>, <img>,etc.**                                                | **Common defaults: `<button>`, `<input>`, `<select>`, `<textarea>`; or any element set with `display: inline-block` (e.g., `<span>`, `<div>`).** |

---
---

### 5. Explain CSS selectors and their types?
Answer:
Selectors are how we target elements. 
By using selectors we provide styles to the targeted elements. 
Types of selectors:
- **Universal:** targets **all** elements.  
    `* { box-sizing: border-box; }`
    
- **element:** targets by **tag name**.  
    `p { margin: 0; }`
    
- **Class:** targets elements with a **class**.  
    `.btn { padding: .5rem 1rem; }`
    
- **ID:** targets the **unique** element with that id (use sparingly).  
    `#header { position: sticky; }`
    
- **Attribute:** matches by **attribute/value**.  
    `input[type="email"] { border-color: teal; }`
    
- **Pseudo-class:** matches an element’s **state/structure**.  
    `a:hover { text-decoration: underline; }`  
    `li:nth-child(2) { font-weight: 600; }`
    
- **Pseudo-element:** targets a **part** of an element.  
    `p::first-line { letter-spacing: .5px; }`  
    `.btn::after { content: " →"; }`
    
- **Combinators (relationships):** connect selectors.  

---

**"CSS selectors are patterns used to select and style HTML elements.**

**First, we have basic selectors:**

- **Universal selector (*)** - selects all elements
- **Type(element) selector** - like `div` or `p`, targets specific HTML tags
- **Class selector (.classname)** - targets elements with a specific class
- **ID selector (#idname)** - targets a unique element with that ID
- **Attribute selector** - like `[type="text"]`, selects elements based on attributes

**Then we have combinators that define relationships:**

- **Descendant selector (space)** - like `div p`, selects all `p` inside `div`
- **Child selector (>)** - like `div > p`, selects direct children only
- **Adjacent sibling (+)** - selects the immediate next sibling
- **General sibling (~)** - selects all siblings after an element

**We also have pseudo-classes and pseudo-elements:**

- **Pseudo-classes** like `:hover`, `:focus`, `:first-child`, `:nth-child()` - style elements based on their state or position
- **Pseudo-elements** like `::before`, `::after`, `::first-line` - style specific parts of elements

**And finally, we can group selectors with commas** to apply the same styles to multiple elements, like `h1, h2, h3`.

The specificity order matters too - ID selectors are more specific than classes, which are more specific than type selectors. This helps determine which styles get applied when there are conflicts."

----
CSS selectors are patterns used to target HTML elements for styling. 
and there are 3 types of selectors:

**Basic selectors:** Universal (*), Type/Element (div, p), Class (.classname), ID (#idname), and Attribute selectors [type="text"]. 

**Combinators:** Descendant (space), Child (>), Adjacent sibling (+), and General sibling (~) - these define relationships between elements.

**Pseudo-classes and Pseudo-elements:** Pseudo-classes like :hover, :focus, :nth-child() target elements based on state or position. Pseudo-elements like ::before, ::after style specific parts of elements.

**We can also group selectors with commas** to apply styles to multiple elements at once.

---



