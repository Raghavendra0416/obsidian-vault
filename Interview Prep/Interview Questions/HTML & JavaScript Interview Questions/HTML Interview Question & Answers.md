#### 1. Are bold and strong tags same? If not then why?
Ans:

| B tag                                | Strong Tag                        |
| ------------------------------------ | --------------------------------- |
| Physical/ Presentational             | Semantic/ logic                   |
| Make this look bold                  | This information is important     |
| SEO --> Low                          | SEO --> High                      |
| Used for Decoration / Visual Vareity | Used for emphasis & accessibility |

---
#### 2. What is image map?
Ans:

An **image map** is an HTML feature that allows you to create multiple clickable links on a single image. Instead of the entire image pointing to one URL, specific "hotspots" or regions are defined to lead to different destinations.

Core Components

- **The Image (`<img>`):** The base visual element. it must include a `usemap` attribute that links it to the map definition. 
- **The Map Element (`<map>`):** A container that holds the data for the clickable areas. It is linked to the image via a unique `name` attribute.
- **The Area Element (`<area>`):** Defines the specific shape, coordinates, and destination (`href`) for each individual hotspot.

Supported Shapes
- **Rect:** A rectangular area defined by the top-left and bottom-right corner coordinates.
- **Circle:** A circular area defined by the center point and the radius.
- **Poly:** A polygonal shape defined by a series of points (vertices) to create complex outlines.

Why Use Them?
- **Interactive Diagrams:** Perfect for maps of countries, human anatomy, or complex machinery where different parts need individual explanations.    
- **Navigation Menus:** Useful for artistic or non-linear navigation bars where text alone wouldn't fit the design.
- **Visual Organization:** They allow for a clean UI by embedding multiple interactions within a single graphical asset.

Technical Implementation Example

```HTML
<img src="office.jpg" alt="Office Room" usemap="#officemap">

<map name="officemap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.html">
  <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.html">
  <area shape="circle" coords="337,300,44" alt="Coffee Cup" href="coffee.html">
</map>
```

---
#### 3. What is `iframe` tag and uses of `iframe` tag?
Ans:
An **`<iframe>`** (short for **Inline Frame**) is an HTML element used to embed another document or webpage inside your current webpage. It essentially creates a "window" that displays external content without the user having to leave your site.

Core Attributes
- **`src` (Source):** Specifies the URL of the page or file you want to embed.
- **`width` & `height`:** Defines the size of the iframe (can be in pixels or percentages).
- **`title`:** Provides a description for accessibility (vital for screen readers).
- **`sandbox`:** A security feature that restricts what the embedded content can do (e.g., blocking scripts or pop-ups).
- **`loading="lazy"`:** Improves performance by only loading the iframe when the user scrolls near it.

Common Uses of Iframes
- **Embedding Multimedia:** The most frequent use case is adding YouTube or Vimeo videos, Spotify playlists, or SoundCloud tracks directly onto a page.
- **Interactive Maps:** Websites often use iframes to embed Google Maps to show a business location or provide directions.
- **Third-Party Widgets:** Used for integrating social media feeds (Twitter/X, Facebook), weather widgets, or "Like" buttons.
- **Payment Gateways:** Services like PayPal or Stripe often use iframes to keep sensitive credit card fields isolated from the rest of the site for security and compliance.
- **Advertising:** Most web advertisements are delivered via iframes so that the ad network's code doesn't interfere with the main site's layout or scripts.
- **Document Previews:** You can display PDFs, Google Docs, or SlideShares directly in the browser using an iframe.

Security & Best Practices
- **Use HTTPS:** Always ensure the `src` URL uses `https://` to prevent security warnings and data interception.
- **Enable Sandboxing:** Use the `sandbox` attribute to prevent malicious code in an embedded site from accessing your main website’s data.
- **Avoid Overuse:** Loading too many iframes can significantly slow down your page speed since each one is essentially a separate browser session.

Basic Code Example
```HTML
<iframe 
  src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
  width="560" 
  height="315" 
  title="YouTube Video Player" 
  sandbox="allow-scripts allow-same-origin"
  loading="lazy">
</iframe>
```

---
#### 4. What are CSS Counters and example?
Ans:
CSS Counters
- **Definition:** CSS counters are "variables" maintained by CSS that allow you to adjust the numbering of elements based on their appearance in the document.
- **Purpose:** They are used to create automatic numbering for items like headings, chapters, or figures without relying on the browser's default list numbering.

[CSS Counter Example](https://www.w3schools.com/css/css_counters.asp)

Key Properties
- **`counter-reset`**: This "starts" the counter. You usually put this on a parent element (like a `<div>` or `<body>`).
- **`counter-increment`**: This tells the browser to add to the counter value (usually +1) every time it sees a specific element.
- **`content`**: This property is used with `::before` or `::after` to actually display the number on the page.
- **`counter()` function**: This retrieves the current value of the variable to be displayed.

Basic Code Example
In this example, every `<h2>` on the page will automatically be numbered (e.g., "Step 1:", "Step 2:").

**CSS:**

```CSS
/* 1. Create the counter on the container */
body {
  counter-reset: step-counter;
}

/* 2. Increment and display on the target element */
h2::before {
  counter-increment: step-counter;
  content: "Step " counter(step-counter) ": ";
  color: #ff5733; /* Make the number a specific color */
  margin-right: 10px;
}
```

**HTML:**
```HTML
<h2>Add Ingredients</h2>
<h2>Mix Well</h2>
<h2>Bake for 20 Minutes</h2>
```

---
#### 5.

What is A11Y in HTML?
How do you provide security to a webpage using tags ?

---
#### Where do we defiantly need to use Inline styling?
Answer: Loader.

Why do we have to provide In-line styling to loader instead of Internal/External styling?
Answer: 
If we use Internal/External styling the browser has to download the file, render the file and execute the file. But if we use In-Line Styling the browser has to download and execute the file.

#### What Styling has more priority?
Answer: 
In-Line Styling(has more) > Internal Styling (Less compared to in-line & greater than external)> External Styling (less compared to in-line & Internal)

Above all  if !Important is used then that will have high priority.