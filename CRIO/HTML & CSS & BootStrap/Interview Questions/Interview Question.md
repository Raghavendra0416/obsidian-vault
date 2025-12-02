Session 4 - developer tools -  need to complete.
### 1. What are the differences between HTML and HTML5?
Answer:
##### Overview:
HTML stands for hypertext markup language. and HTML5 is the newer version of HTML. HTML5 provides support to built in multi-media, less syntax, new API's and reduces the need for external plugins.

HTML5 simplifies the syntax for DOCTYPE HTML, and it also adds semantic elements like header, section, footer to provide more meaning to the page structure.

It also provides native support for audio, video and new form input types(like email, date, range, attributes). and older HTML relied more on plugins and presentational tags but HTML5 replaces them.

---
---
### 2. What are the differences between semantic and non-semantic HTML tags?
Answer:
##### Overview:
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
##### Detailed Explation
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
##### Detailed Explation:
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

##### Overview:
CSS selectors are patterns used to target HTML elements for styling. 
and there are 3 types of selectors:

**Basic selectors:** Universal (*), Type/Element (div, p), Class (.classname), ID (#idname), and Attribute selectors [type="text"]. 

**Combinators:** Descendant (space), Child (>), Adjacent sibling (+), and General sibling (~) - these define relationships between elements.

**Pseudo-classes and Pseudo-elements:** Pseudo-classes like :hover, :focus, :nth-child() target elements based on state or position. Pseudo-elements like ::before, ::after style specific parts of elements.

**We can also group selectors with commas** to apply styles to multiple elements at once.

---
---
### 6. What is CSS Box Model?
Answer:
The CSS Box Model is a fundamental concept in web development that describes how elements are rendered and displayed on a webpage. It consists of four main components: content, padding, border, and margin.
1. Content: It represents the actual content of an element, such as text, images, or other HTML elements. The content area is defined by the width and height properties.
2. Padding: It is the space between the content and the element’s border. Padding can be set using the padding property and can have different values for each side (top, right, bottom, left).
3. Border: It is a line that surrounds the content and padding of an element. Borders can be styled using properties like border-width, border-color, and border-style.
4. Margin: It is the space outside the element’s border, creating a gap between adjacent elements. Margins can be set using the margin property and can also have different values for each side.
	
The CSS box model is responsible for calculating:
- How much space a block element takes up.
- how we calculate the total size using the **`box-sizing`** property.

We have 2 box sizing properties i.e: Content Box, Border Box.

By default, the browser uses `content-box`, where padding and borders are added _outside_ the defined width, often breaking layouts.

Optional But need to learn:
- **`Content-box` (Default Behavior):** The `width` we set is applied to the Content area. Padding and Border are added _on top_ of that width.
- **`Border-box` (Modern Standard):** The `width` you set includes the Content, Padding, and Border.  

Optional:
**Margin Collapse:** Top and bottom margins of adjacent elements sometimes combine into a single margin (equal to the larger of the two) rather than adding up.
Margin collapse means:
**The Concept:** When two vertical margins touch (the bottom of Element A and the top of Element B), they don't add together (e.g., 20px + 30px = 50px). Instead, they **collapse** into a single margin equal to the largest one (30px).

---
### What is CSS selector specificity and how does it work?
Answer:
**CSS Specificity** determines which CSS rule gets applied when multiple rules target the same element. It's a scoring system that browsers use to resolve conflicts between competing styles.

This is important because it helps to resolve conflicts and ensure that the correct styles are applied.

CSS specificity is calculated based on the combination of selectors used to target an element. 
Each selector has a specific weight assigned to it, and the styles with higher specificity will override those with lower specificity.

The specificity hierarchy is as follows:
1. Inline styles: Styles applied directly to an element using the `style` attribute have the highest specificity. They are defined within the HTML tag itself and take precedence over all other styles.
2. ID selectors: Styles applied using the `id` attribute have a higher specificity than class selectors. An ID selector is denoted by a hash symbol (#) followed by the ID name.
3. Class selectors: Styles applied using class selectors have a lower specificity than ID selectors. A class selector is denoted by a period (.) followed by the class name.
4. Element selectors: Styles applied using element selectors have the lowest specificity. An element selector targets all elements of a specific type, such as `<div>` or `<p>`.

Cases:
If two styles have the same specificity, the one that appears later in the CSS file will take precedence.
When multiple styles with different specificity levels conflict, the style with the highest specificity will be applied.

---
### What does `* { box-sizing: border-box; }` do?
Answer:
`* { box-sizing: border-box; }` applies `border-box` sizing to all elements on the page.

**Universal Selector**. It targets **every single element** on the page (divs, paragraphs, buttons, inputs, etc.) and applies the rule to them and
`box-sizing: border-box` changes the box model calculation so that `width` and `height` include the padding and border with the content.

By default, when you set a width like 200px, that's just the content width - padding and border are added on top, making the element larger than expected.
With `border-box`, the width includes the padding and border, so if you set width to 200px, the element is exactly 200px total. This makes layouts much more predictable and easier to work with.

---
### What are grids in CSS?
Answer:
**CSS Grid** is a two-dimensional layout system that lets you create complex layouts using rows and columns.

Grid divides a container into rows and columns, creating a grid-like structure and you can place items anywhere within that grid structure.

This grid system helps in organizing and aligning elements on a web page, making it easier to create flexible designs.

To create a grid layout in CSS, we can use the CSS Grid Layout module. This module introduces a set of properties that define the grid container and its items.

 The main properties used for creating grids are:
 1. `Display: grid`: This property is applied to the container element and defines it as a grid container.
2. `grid-template-columns` and `grid-template-rows`: These properties define the size and number of columns and rows in the grid. We can specify the size using fixed values like pixels or percentages, or using flexible units like `fr` (fractional unit) to distribute the available space.
3. `grid-gap`: This property sets the gap between grid cells, allowing for spacing between columns and rows.
4. `grid-column` and `grid-row`: These properties are used to position and span grid items across columns and rows. We can specify the starting and ending positions of the item within the grid.

**Common use case:** Page layouts, dashboards, image galleries.

---

### What is Flex Box?
Answer:
CSS Flexbox is a one-dimensional layout model designed to arrange items in a single direction—either as a row or a column.

Its primary purpose is to efficiently distribute space and align items within a container, even when the size of those items is unknown or dynamic.

It operates on a specific axis system.
	Main Axis,
	Cross Axis

Main Axis: It is the primary direction that items flow. If direction is `row`, the main axis is horizontal.
Cross Axis: If direction is `row`, the cross axis is vertical.

The items in the main axis can be controlled by using justify-content. 
The items in the cross axis can be controlled by using align-items.

To use Flex Box we need to use Flex module in CSS.
The properties of flex box are:
**`display: flex;`**: Activates the flex context.
**`flex-direction`**: Defines the Main Axis to be row or column.
**`justify-content`**: Controls the items over main axis.
**`align-items`**: Controls the items over cross axis.
**`flex-wrap`**: Determines if items should force themselves onto one line or wrap onto multiple lines.

Flexbox is commonly used for navigation bars, buttons, or perfectly centering elements on a page.

---
### What is the difference between absolute and relative length units in CSS? Provide examples.
Answer:
**Absolute Units:**
Absolute units are static values that does not change based on other settings or screen sizes. for example: if you define a width in absolute unit then the element will appear in same size in all phone, tablet and desktop.

**Relative Units:**
These are dynamic. These sizes are calculated based on the value of other elements like root element, parent element, viewport size.
for example: if you define a width in relative unit then the element will appear in different sizes in  phone, tablet and desktop.

Common usage of Absolute units are:
`px` (pixels), 
`cm` (centimeters), 
`mm` (millimeters), 
`in` (inches).
Once these units are used, then the size of element cannot be changed based on other elements.

Common usage of Relative Units are divided based on:
**Font-Relative Units:** em, rem.
**Viewport-Relative Units:** vw,vh.
**Parent-Relative:** %.

here
"em"  - font size relative to the parent size and
"rem" - font size is relative to the root element font size.
"%" - is also relative to the parent size and mostly used for Width and Height

| **Feature**       | **Absolute (px, cm)**                | **Relative (%, rem, em, vw)**         |
| ----------------- | ------------------------------------ | ------------------------------------- |
| **Scalability**   | Fixed; does not scale well.          | Highly scalable and responsive.       |
| **Accessibility** | Poor; ignores user font preferences. | Excellent; respects user preferences. |
| **Dependency**    | None.                                | Depends on parent, root, or viewport. |
| **Primary Use**   | Borders, shadows, print layouts.     | Layout grids, typography, spacing.    |

If asked **"Which should I use for font sizes?"**
the strongest answer is usually **`rem`**.rem units are mostly used in webpage, as this will help visually impaired users to visualize the font by increasing the font size.

---
### What are the differences between CSS Grids and Flexbox?
Answer:
The Core Difference of flex box and grids are:
**Flexbox** is **One-Dimensional (1D)**. It arranges elements in a single axis - either a main axis or cross axis.
**Grid** is **Two-Dimensional (2D)**. It arranges elements in two axis i.e rows & columns simultaneously.

Flex box primary purpose is to efficiently distribute space and align items within a container
Grid divides a container into rows and columns, creating a grid-like structure and you can place items anywhere within that grid structure.

Flex box operates on a specific axis system.
	Main Axis,
	Cross Axis
Grids operates on 
	Rows
	Columns

To use Flex Box we need to use Flex module in CSS.
The properties of flex box are:
**`display: flex;`**: Activates the flex context.
**`flex-direction`**: Defines the Main Axis to be row or column.
**`justify-content`**: Controls the items over main axis.
**`align-items`**: Controls the items over cross axis.
**`flex-wrap`**: Determines if items should force themselves onto one line or wrap onto multiple lines.

To use Grids we need to use Grid module in CSS.
The properties of Grid are:
 1. `Display: grid`: This property is used to define it is a Grid.
2. `grid-template-columns` and `grid-template-rows`: These properties define the size and number of columns and rows in the grid. We can specify the size using fixed values like pixels or percentages, or using flexible units like `fr` (fractional unit) to distribute the available space.
3. `grid-gap`: This property sets the gap between grid cells, allowing for spacing between columns and rows.
4. `grid-column` and `grid-row`: These properties are used to position the grid items across columns and rows. 

Flexbox is commonly used for navigation bars, buttons, or perfectly centering elements on a page.
Grids are commonly used for Page layouts, dashboards, image galleries.

---
### What are the different CSS position property values?
Answer:
There are **5 main values** for the `position` property:
1. Static
2. Relative
3. Absolute
4. Fixed
5. Sticky

Static:
Every element is `static` by default.
Static elements ignore offsets like top/left/right/bottom properties and follow the **normal document flow**.
Mostly used when we don’t need special positioning.

Relative:
Element remains **in normal flow**.
Offsets(top/left/right/bottom) move it **without affecting/disturbing other elements' positions**.
Mostly used as a container (parent) for an `absolute` child.

Absolute:
Removed from normal flow.
absolute positioning depends on the nearest non-static ancestor.
If no positioned ancestor exists → positioned relative to the **viewport**.
Mostly used for placing an icon in the corner of a card, or a tooltip.

Positioned **relative to the nearest positioned ancestor** (`relative`, `absolute`, or `fixed`, not static).

Fixed:
Removed from normal flow.
Positioned **relative to the viewport**.
Fixed elements remain fixed during scrolling.
Mostly used for chat widgets, Navigation bars stuck to the top.

Sticky:
A hybrid of `relative` and `fixed`. Sticky combines relative and fixed behavior.
Behaves like `relative` until a specified offset is reached (like `top: 0`).
After crossing the offset, it behaves like `fixed`.
Mostly used for Sticky table headers, section titles, navigation bars.

Extra:
Positioning often interacts with **z-index**. Non-positioned elements (static) cannot use z-index.

Overview:
**CSS provides five main position values:**
1. **static** – default, follows normal flow.
2. **relative** – stays in flow but can be offset from its original position; useful for setting a positioning context.
3. **absolute** – removed from flow and positioned relative to the nearest positioned ancestor.
4. **fixed** – removed from flow and positioned relative to the viewport; does not move on scroll.
5. **sticky** – acts like relative until a threshold is met, then sticks like fixed.  
    **Offsets like top/left only work with non-static positioning.**

Document Flow: Static, Relative, Sticky.
Offset properties work on: Relative, Absolute, Fixed, Sticky.

---
### What is Responsive Web Design(RWD)?
Answer:
**Responsive Web Design (RWD)** is an approach to web development where the layout and content **adapt** to different screen sizes, orientations, and resolutions.
Instead of building separate websites for mobile and desktop, we build **one** codebase that looks good on everything from small screens to large screens.

Responsive design mainly uses:
- **Fluid layouts** (percentage-based widths)
- **Flexible images**
- **CSS media queries**

Fluid layouts:
Instead of using fixed absolute units (like `px`) for layout, you use **relative units** (like `%`, `vw`, `fr`).

Flexible Images:
Images (and videos) must be prevented from breaking out of their containers. So we need to provide -" max-width: 100%; height: auto; ".

Media Queries (`@media`):
This is the logic layer. It allows you to apply different CSS styles based on specific conditions like width of the screen.

Responsive CSS **will not work** on a mobile device unless you include this specific HTML tag in the `<head>`:
```HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Responsive CSS **will not work** on a mobile device unless we include meta tag and name with viewport and content width to be device width in the `<head>` tag.

---
### What is Bootstrap?
Answer:
**Definition:**
**Bootstrap** is a popular **open-source CSS framework** developed by Twitter. It is used to build **responsive, mobile-first websites** quickly.

**Core Concept:**
Boot strap follows -> Class-Based Styling.
Instead of writing CSS from scratch, you apply **pre-defined classes** to your HTML elements.

**The Grid System:**
Bootstrap's layout engine is built on a **12-column grid**.
The page width is divided into 12 vertical strips, and we group them to create layouts.
These grid classes use **breakpoints** (sm, md, lg, xl) to automatically adapt the layout for different screen sizes.

**Components:**
**Components** Bootstrap provides a library of **pre-built components**.
- **Interactive Components:** Things like **Modals** (pop-ups), **Accordions**, and **Navbars** that come with built-in JavaScript functionality.
- **UI Elements:** Buttons, cards, forms, and alerts.

**Benefits:**
Overall, it helps developers build websites **faster**, ensures **design consistency**, and handles **cross-device responsiveness** automatically.

---
### What are the differences between semantic and non-semantic HTML tags?
Answer:
Semantic tags: Semantic tags clearly describe **what** kind of content they contain to both the browser and the developer.
Examples:  
`<header>`, `<footer>`, `<nav>`, `<section>`, `<article>`, `<aside>`, `<main>`, `<figure>`

Non-semantic tags: These tags are generic containers. They tell you nothing about their contents. They are purely used for styling (CSS) or grouping elements for layout.
Examples:  
`<div>`, `<span>`, `<b>`, `<i>`

Using semantic tags improves:
- **Accessibility** (screen readers understand content roles)
- **SEO** (search engines understand structure better)
- **Readability & maintainability** (developers understand the layout easily)

Non-semantic tags:
- Are often used for generic containers
- Require classes or IDs to give meaning

---
### What are the differences between block elements, inline elements and inline-block elements?
Answer:
**1. Block Elements**
- Always start on a **new line**.
- Stack **vertically** one after another.
- Occupy the **full available width** (100% of parent width).
- You can set **width, height, margin, padding**.

**Examples:**  
`<div>`, `<p>`, `<h1>–<h6>`, `<section>`, `<article>`, `<footer>`

**When to use:**  
For major layout sections (headers, paragraphs, containers).

**2. Inline Elements**
- **Do NOT start on a new line** (stay within the same line).
- Occupy **only the space needed** by their content.
- **Cannot** set width and height (ignored).
- Margin & padding work **only left/right**, not top/bottom.

**Examples:**  
`<span>`, `<a>`, `<strong>`, `<em>`, `<img>` (_img behaves slightly differently but still inline_)

**When to use:**  
Formatting text inside a line.

**3. Inline-Block Elements**
- Stay **in the same line** like inline elements.
- But you **can set width, height, margin, padding** like block elements.
- Useful when you want elements to sit side-by-side **with controlled size**.

**Examples:**  
Often applied through CSS:  
`display: inline-block;`

**When to use:**  
Buttons, navigation links, cards, or items arranged in a row with fixed size.

**Comparison Table (Interview-Friendly)**

| Property                   | Block                       | Inline                      | Inline-Block                                             |
| -------------------------- | --------------------------- | --------------------------- | -------------------------------------------------------- |
| Starts on new line?        | ✔ Yes                       | ❌ No                        | ❌ No                                                     |
| Takes full width?          | ✔ Yes                       | ❌ No                        | ❌ No                                                     |
| Width & height applicable? | ✔ Yes                       | ❌ No                        | ✔ Yes                                                    |
| Margin/padding works?      | ✔ Fully                     | ❌ Limited (left/right only) | ✔ Fully                                                  |
| Layout behavior            | Stacks vertically           | Fits inside a line          | Inline with control                                      |
| Typical use                | Layout containers           | Text formatting             | Buttons, menus, badges                                   |
| Examples                   | `<div>`, `<p>`, `<h1>–<h6>` | `<span>`, `<a>`, `<strong>` | Often applied through CSS:  <br>`display: inline-block;` |

---
	