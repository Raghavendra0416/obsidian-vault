#### Core structure
- `<!doctype html>`, `<html>`, `<head>`, `<body>` – page skeleton
- In `<head>`: `<title>`, `<meta>`, `<link rel="stylesheet">`, `<script defer>`, `<style>`

#### Page landmarks (semantic layout)
- `<header>` – top banner / branding
- `<nav>` – primary navigation
- `<main>` – unique main content (one per page)
- `<section>` – grouped thematic content
- `<article>` – standalone content item (blog post, card)
- `<aside>` – side content (ads, related links)
- `<footer>` – page or section footer

#### Text & inline semantics
- Headings: `<h1>`…`<h6>`
- Blocks: `<p>`, `<ul>`, `<ol>`, `<li>`, `<blockquote>`
- Inline: `<a>`, `<em>`, `<strong>`, `<code>`, `<pre>`, `<mark>`, `<abbr>`, `<time>`, `<small>`

#### Media
- `<img>` (always use `alt`), `<figure>`, `<figcaption>`
- `<video>`, `<audio>`, `<source>`, `<track>`

#### Containers (when nothing else fits)
- `<div>` (block), `<span>` (inline) – use sparingly; prefer semantic tags first

#### Forms (very common)
- `<form>`, `<label for>`, `<input>`, `<textarea>`, `<select>`, `<option>`
- Helpers: `<button>`, `<fieldset>`, `<legend>`, `<datalist>`, `<output>`
- Useful attributes: `name`, `type`, `value`, `placeholder`, `required`, `min`, `max`

#### Tables (for data, not layout)
- `<table>`, `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<td>`, `scope`

#### Global attributes you’ll use everywhere
- `id` (unique on page), `class` (styling/hooks), `style`, `title`, `hidden`
- Language & direction: `lang`, `dir`
- Accessibility: `role`, `aria-*` (use when semantics alone aren’t enough)
- Custom data: `data-*` (for JS hooks, not for styling logic)

# Minimal starter you can copy

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>My Page</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <header id="site-header">
    <h1 class="brand">Site Name</h1>
    <nav aria-label="Primary">
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/blog">Blog</a></li>
      </ul>
    </nav>
  </header>

  <main id="content">
    <article class="post">
      <header><h2>Post Title</h2></header>
      <p>Hello <strong>world</strong>!</p>
      <figure>
        <img src="photo.jpg" alt="Sunset over hills" />
        <figcaption>A calm evening.</figcaption>
      </figure>
    </article>

    <section aria-labelledby="contact-heading">
      <h2 id="contact-heading">Contact</h2>
      <form action="/submit" method="post">
        <label for="email">Email</label>
        <input id="email" name="email" type="email" required />
        <button type="submit">Send</button>
      </form>
    </section>
  </main>

  <footer>&copy; 2025 Me</footer>
  <script src="app.js" defer></script>
</body>
</html>
```

#### Quick best practices
- Prefer **semantic elements** over generic `<div>`/`<span>`.
- One **visible `<h1>` per page** (per document/`<main>`).
- `id` is unique; use `class` for reusable styles.
- Always add meaningful `alt` text to images.
- Pair `<label>` with inputs (`for` ↔ `id`) for accessibility.
- Use the responsive meta tag (`<meta name="viewport" …>`) for mobile.
---
#### Summary:
#### Most-used elements (practical short list)
- **Structure & head:** `<!doctype html>`, `html`, `head`, `meta`, `title`, `link`, `script`, `body`
- **Layout/landmarks:** `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `div`
- **Text & links:** `h1`–`h3`, `p`, `ul`, `ol`, `li`, `a`, `strong`, `em`, `span`
- **Media:** `img` (with `alt`), `figure`, `figcaption`
- **Forms:** `form`, `label`, `input`, `button`, `select`, `textarea`
- **Tables (when showing data):** `table`, `thead`, `tbody`, `tr`, `th`, `td`

#### Most-used attributes (you’ll touch these constantly)
- **Global:** `id`, `class`, `style`, `title`, `hidden`, `lang`, `dir`, `role`, `aria-*`, `data-*`
- **Links & media:** `href`, `src`, `alt`, `target`, `rel`
- **Forms:** `name`, `type`, `value`, `placeholder`, `required`, `for`, `min`, `max`, `checked`, `selected`
- **Scripting:** `defer`, `async` (on `<script>`)

