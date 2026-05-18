### 🃏 Card 1: The Document Foundation

This is the basic skeleton of every HTML page.

- **`<!DOCTYPE html>`**: Declares the document type.
- **`<html>`**: The root element that wraps all content.
- **`<head>`**: Contains meta-information (data _about_ the page).
    - **`<title>`**: The title shown in the browser tab.
    - **`<meta>`**: For character set (`charset="UTF-8"`), viewport, and descriptions.
    - **`<link>`**: To link external files, like CSS.
- **`<body>`**: Contains all the visible content of the page.


---
### 🃏 Card 2: Essential Content Tags

These are the most common tags you'll use to build your content.

- **Headings**: `<h1>` (most important) through `<h6>` (least important).
- **Paragraph**: `<p>` for blocks of text.
- **Links**: `<a>` (the "anchor" tag).
    - `href` attribute: The URL to link to.
    - `target="_blank"`: To open the link in a new tab.
- **Images**: `<img>`
    - `src` attribute: The path to the image file.
    - `alt` attribute: **Crucial for accessibility**. Describes the image if it can't be seen.


---
### 🃏 Card 3: Text Formatting

How to style text _semantically_ (what it _means_, not just what it _looks_ like).

- **`<strong>`**: For important text (usually bold).
- **`<em>`**: For emphasized text (usually italic).
- **`<b>`**: Bold text (without the extra "importance" of `<strong>`).
- **`<i>`**: Italic text (without the extra "emphasis" of `<em>`).
- **`<br>`**: A line break.
- **`<hr>`**: A horizontal rule (a thematic break or line).

---
### 🃏 Card 4: Lists

How to organize items.

- **Unordered List**: `<ul>`
    - List Item: `<li>` 
- **Ordered List**: `<ol>`
    - List Item: `<li>`
- **Description List**: `<dl>`
    - Description Term: `<dt>`
    - Description Details: `<dd>`

---
### 🃏 Card 5: Semantic Layout (HTML5)

These tags describe the _purpose_ of a section, which is great for SEO and accessibility.

- **`<header>`**: Introductory content (like a logo, site title, nav).
- **`<footer>`**: Closing content (like copyright, contact info).
- **`<nav>`**: Contains main navigation links.
- **`<main>`**: The main, unique content of the page.
- **`<article>`**: A self-contained piece of content (e.g., a blog post).
- **`<section>`**: A generic grouping of related content.
- **`<aside>`**: Sidebar content (related, but separate from the main content).

---
### 🃏 Card 6: Containers

The "boxes" you use to group elements for styling (with CSS) or structure.

- **`<div>`**: A "division" or block-level container. It's a generic box.
- **`<span>`**: An inline container, used to group small parts of text or content _within_ a block.

---
### 🃏 Card 7: Forms

How you collect user input.

- **`<form>`**: The wrapper for all form elements.
    - `action` attribute: Where to send the data.
    - `method` attribute: `GET` or `POST`.

- **`<label>`**: Describes an input field (crucial for accessibility).
    - `for` attribute: Links the label to an input's `id`.

- **`<input>`**: The most common form element.
    - `type` attribute: Can be `text`, `email`, `password`, `number`, `checkbox`, `radio`, `submit`, `file`, `date`, and more.

- **`<textarea>`**: For multi-line text input.
    
- **`<select>`**: A dropdown menu.
    - **`<option>`**: An item in the dropdown.

- **`<button>`**: A clickable button.

---
### 🃏 Card 8: Tables

For displaying data in rows and columns.

- **`<table>`**: The main table wrapper.
- **`<thead>`**: The table header group.
- **`<tbody>`**: The table body group.
- **`<tr>`**: A table row.
- **`<th>`**: A table header cell (for titles).
- **`<td>`**: A table data cell (for regular content).
- **`colspan` / `rowspan`**: Attributes to make a cell span multiple columns or rows.

---
### 🃏 Card 9: Media

How to embed other content.

- **`<audio>`**: Embeds sound.
- **`<video>`**: Embeds a video player.
- **`<iframe>`**: Embeds another HTML page (e.g., a YouTube video or Google Map).

---
### 🃏 Card 10: Other Essentials

A few final key concepts.

- **Comments**: ``
- **HTML Entities**: Special codes for reserved characters (e.g., `&copy;` for ©, `&lt;` for <, `&gt;` for >).
- **Accessibility (a11y)**: The practice of making your site usable by everyone, including those with disabilities (e.g., using `alt` text, `label`s, and semantic HTML).

---
### 🃏 Card 11: Scripting & Styling Tags

These are crucial for making your site interactive and look good.

- **`<script>`**: The most important tag for adding JavaScript. You can write code directly inside it or use the `src` attribute to link to an external `.js` file (which is the recommended way).
- **`<style>`**: Used to add internal CSS rules directly inside your HTML `<head>`. (This is different from `<link>`, which links to an _external_ `.css` file).

---
### 🃏 Card 12: Advanced Form Elements

These give you more control over your forms.

- **`<fieldset>`**: Groups related form controls together.
- **`<legend>`**: Provides a caption for the `<fieldset>`.
- **More `<input>` types**: `date`, `color`, `range`, `file`.
- **Validation Attributes**: `required` (must be filled out), `pattern` (must match a regex), `minlength`, `maxlength`.

---
### 🃏 Card 13: Advanced Media & Imagery

For more responsive and descriptive media.

- **`<figure>`**: A container for self-contained content, like an image, diagram, or code, that is referenced from the main text.
- **`<figcaption>`**: A caption for the `<figure>`.
- **`<picture>`**: Allows you to provide different image sources for different screen sizes or resolutions (for responsive design).
- **`<source>`**: Used inside `<picture>`, `<audio>`, or `<video>` to specify multiple media resources.

---
### 🃏 Card 14: More Semantic Elements

For adding more _meaning_ to your text.

- **`<blockquote>`**: For long, multi-line quotations (often indented).
- **`<q>`**: For short, inline quotations (adds quotes automatically).
- **`<code>`**: For displaying a small piece of computer code.
- **`<pre>`**: For "preformatted" text. It respects white space and line breaks (perfect for larger code blocks).
- **`<details>` / `<summary>`**: Creates a "disclosure" widget that the user can open and close. `<summary>` is the visible part, and `<details>` holds the hidden content.

---
### 🃏 Card 15: Advanced `<head>` & Metadata

This controls how your site interacts with browsers, search engines, and social media.

- **`<base>`**: Specifies the base URL for all relative URLs in the document (e.g., all links starting with `/` will be relative to this base).
- **Advanced `<meta>` tags**:

    - `viewport`: **Crucial for mobile.** Tells the browser how to control the page's dimensions and scaling. (`<meta name="viewport" content="width=device-width, initial-scale=1.0">`)
    - `description`: The description of your site shown in search engine results.
    - **Open Graph (OG)**: Meta tags for social media (`og:title`, `og:description`, `og:image`) that control how your page looks when shared on sites like Facebook or X (Twitter).
    - `robots`: Tells search engine crawlers what they can (`index`, `follow`) or can't (`noindex`, `nofollow`) do.


---
### 🃏 Card 16: On-Page Graphics

How to draw and display graphics directly in HTML.

- **`<svg>` (Scalable Vector Graphics)**: The root element for an XML-based vector graphic. Ideal for logos, icons, and charts that need to scale perfectly at any size.
    - Common child elements: `<path>`, `<circle>`, `<rect>`, `<text>`.

- **`<canvas>`**: A "bitmap" drawing surface. You use JavaScript to draw pixels on it. Ideal for games, complex animations, or image processing.
    

---
### 🃏 Card 17: Advanced Accessibility (A11y)

Writing HTML that works for _everyone_, including users with disabilities who rely on assistive technology (like screen readers).

- **ARIA (Accessible Rich Internet Applications)**: Attributes that add semantics to elements when HTML's built-in tags aren't enough.
    
- **`role` attribute**: Used to explicitly define what an element is, especially for custom widgets (e.g., `role="button"`, `role="dialog"`, `role="tablist"`).
    
- **`aria-*` attributes**: Provides properties to assistive tech.
    - **`aria-label`**: Adds a "name" to an element that _only_ screen readers can access (e.g., for an icon button like `<button aria-label="Close">X</button>`).
    - **`aria-labelledby`**: Links an element to another element that serves as its label.
    - **`aria-hidden="true"`**: Hides an element from screen readers (e.g., for purely decorative icons).
    - **`aria-expanded`**: Tells a screen reader if a collapsible element is open or closed.
        

---
### 🃏 Card 18: Internationalization (i18n)

Tags for making your content adaptable to different languages and regions.

- **`lang` attribute**: You've seen it on `<html>`, but it can also be used on any element to declare a change in language (e.g., `<p>My name is <span lang="fr">Jean</span>.</p>`).
- **`dir` attribute**: Sets the text direction. `ltr` (left-to-right) or `rtl` (right-to-left) for languages like Arabic or Hebrew.
- **`<ruby>`, `<rt>`, `<rp>`**: Used to display "ruby" annotations, which are pronunciation guides for East Asian characters. `<rt>` holds the text, and `<rp>` holds parentheses for browsers that don't support ruby.
    

---
### 🃏 Card 19: Specialized Semantic Tags

These tags provide very specific meaning for niche use cases.

- **`<time>`**: For marking up dates, times, or durations.
    - `datetime` attribute: Provides a machine-readable format (e.g., `<time datetime="2025-12-25">Christmas Day</time>`).
- **`<address>`**: For contact information (email, physical address, phone number) related to an article or the whole document.
- **`<mark>`**: Represents a "run of text in one document marked or highlighted for reference purposes" (like using a digital highlighter).
- **`<progress>`**: A progress bar showing the completion of a task.
- **`<meter>`**: A scalar measurement within a known range (a gauge), like disk usage or a password strength meter.
    

---
### LD; Card 20: Modern & Expert Topics

These are part of the "Web Components" standard, allowing you to create your own reusable HTML elements.

- **`<template>`**: A container for holding HTML that is not rendered by the browser immediately. Its content is "inert" and can be cloned and activated later using JavaScript.
- **`<slot>`**: A placeholder inside a web component that you can fill with your own "child" HTML, allowing for flexible and composable components.
- **Custom Elements**: While this is more a JavaScript API, it's the _result_ of this part of HTML, allowing you to `document.createElement("my-custom-card")`.
    

---
### 🃏 Card 21: ⛔️ Deprecated (Do Not Use!)

This is the "warning" card. These tags are obsolete, and their functionality should be achieved with **CSS**.

- **Do not use**: `<font>`, `<center>`, `<marquee>`, `<blink>`.
- **Why?**: These tags mix _content_ (HTML) with _presentation_ (CSS), which is bad practice. HTML is for _meaning_, CSS is for _looks_.
- **Do not use**: `<frameset>`, `<frame>`, `<noframes>`.
- **Why?**: These have been replaced by the `<iframe>` element and modern CSS layout techniques (like Flexbox and Grid).