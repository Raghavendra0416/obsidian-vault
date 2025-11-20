# Semantic HTML

**Semantic HTML** refers to using HTML elements that clearly describe their meaning and purpose to both browsers and developers. Instead of using generic containers like `<div>` or `<span>` everywhere, semantic elements tell you what kind of content they contain.

## Why Use Semantic HTML?

- **Accessibility**: Screen readers and assistive technologies can better navigate your content
- **SEO**: Search engines understand your page structure better
- **Maintainability**: Code is easier to read and understand
- **Clarity**: The purpose of each section is immediately obvious

## Common Semantic Tags

**Document Structure:**

- `<header>` - Page or section header (logo, navigation, heading)
- `<nav>` - Navigation links
- `<main>` - Main content of the document (only one per page)
- `<section>` - Thematic grouping of content
- `<article>` - Self-contained, independently distributable content
- `<aside>` - Sidebar or tangentially related content
- `<footer>` - Page or section footer

**Content:**

- `<h1>` to `<h6>` - Headings (hierarchical)
- `<p>` - Paragraph
- `<figure>` and `<figcaption>` - Image with caption
- `<mark>` - Highlighted/marked text
- `<time>` - Date or time
- `<address>` - Contact information

**Text Meaning:**

- `<strong>` - Important text (usually bold)
- `<em>` - Emphasized text (usually italic)
- `<code>` - Code snippet
- `<blockquote>` - Long quotation
- `<cite>` - Citation/reference

## Example

```html
<header>
  <h1>My Blog</h1>
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
    </ul>
  </nav>
</header>

<main>
  <article>
    <h2>My First Post</h2>
    <p>This is the content...</p>
  </article>
</main>

<footer>
  <p>&copy; 2025 My Blog</p>
</footer>
```

Using semantic HTML makes your code more meaningful and professional compared to just using `<div>` elements everywhere!


---

---

# CSS Styling Methods

There are three main ways to add CSS styles to HTML:

## 1. Inline Styling

CSS is written directly inside an HTML element using the `style` attribute.

```html
<p style="color: blue; font-size: 18px;">This is inline styled text</p>
<div style="background-color: yellow; padding: 10px;">Yellow box</div>
```

**Pros:**

- Quick for testing or one-off styles
- Highest specificity (overrides other styles)

**Cons:**

- Hard to maintain
- No reusability
- Mixes content with presentation
- Can't use pseudo-classes or media queries

---

## 2. Internal Styling

CSS is written inside a `<style>` tag in the `<head>` section of the HTML document.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: blue;
      font-size: 18px;
    }
    .highlight {
      background-color: yellow;
    }
  </style>
</head>
<body>
  <p>This is styled text</p>
  <div class="highlight">Yellow box</div>
</body>
</html>
```

**Pros:**

- Good for single-page sites
- Styles are contained in one file
- Can use all CSS features

**Cons:**

- Styles only apply to that one HTML file
- Increases page load time
- Not reusable across multiple pages

---

## 3. External Styling

CSS is written in a separate `.css` file and linked to the HTML document.

**styles.css:**

```css
p {
  color: blue;
  font-size: 18px;
}
.highlight {
  background-color: yellow;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p>This is styled text</p>
  <div class="highlight">Yellow box</div>
</body>
</html>
```

**Pros:**

- Best practice for most projects
- Reusable across multiple pages
- Easier to maintain and organize
- Browser caching improves performance
- Separates content from presentation

**Cons:**

- Requires an additional HTTP request
- Slightly more setup

---

## Best Practice

**Use external styling** for most projects. It keeps your code organized, maintainable, and follows the separation of concerns principle. Internal styling can be useful for small single-page projects, and inline styling should be used sparingly, mainly for quick tests or dynamic styles applied via JavaScript.