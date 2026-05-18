# LearnHub HTML Concepts — Study Checklist

**How to use:** Tick a box when you’ve learned, practiced, or refactored that concept in your own code. Most items link back to elements that exist in _your_ `Index.html`.

---

## Card 01 — Document setup & SEO

-  Core file structure
    
    -  `<!DOCTYPE html>`
        
    -  `<html lang="en">`
        
    -  `<head>`
        
    -  `<body>`
        
-  Metadata
    
    -  `<title>`
        
    -  `<meta charset="UTF-8">`
        
    -  `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
        
    -  `<meta name="description">`
        
    -  `<meta name="keywords">`
        
-  Stylesheets
    
    -  `<link rel="stylesheet" href="./css/styles.css">`
        
    -  `<link rel="stylesheet" href="./css/visualizer.css">`
        
    -  `<link rel="stylesheet" href="./css/responsive.css">`
        

## Card 02 — External assets & libraries

-  Font Awesome (CDN)
    
-  Google Fonts (Poppins)
    
-  Local assets (e.g., `./assets/hero-image.svg`)
    

## Card 03 — Global layout & semantics

-  `<nav>`
    
-  `<main>`
    
-  `<section>` (paged sections)
    
-  `<aside>` (filters sidebar)
    
-  `<footer>`
    
-  Structural `<div>` wrappers
    

## Card 04 — Navigation & links

-  Logo link
    
-  Hash links `href="#..."` to switch sections
    
-  Navigation menu (`<ul><li><a>...`)
    
-  CTA link (e.g., “View All”)
    
-  Social links in footer
    

## Card 05 — Typography & text

-  Headings `h1–h4`
    
-  Paragraphs `<p>`
    
-  Inline text `<span>`
    
-  Emphasis `<strong>`
    

## Card 06 — Lists

-  Unordered lists `<ul>` with `<li>`
    
    -  Navbar list
        
    -  Footer lists
        

## Card 07 — Media & icons

-  Images `<img src ... alt>`
    
-  Font Awesome icons via `<i class="fa* ...">`
    

## Card 08 — Forms & controls (no `<form>` wrapper)

-  Inputs
    
    -  `type="text"`
        
    -  `type="email"`
        
    -  `type="number"`
        
    -  `type="range"`
        
    -  `type="checkbox"`
        
    -  `type="radio"`
        
-  `<label>`
    
-  `<select>`
    
-  `<textarea>`
    
-  `<button>`
    
-  `placeholder` / `value` / `checked` attributes
    

## Card 09 — Accessibility basics

-  Landmark elements (`<nav>`, `<main>`, `<footer>`)
    
-  `alt` text on images
    
-  `aria-label` on theme toggle
    

## Card 10 — Data & attributes

-  `id` attributes (e.g., `#homePage`, `#navMenu`)
    
-  `class` attributes (utility & state classes)
    
-  `data-*` attributes (`data-page`, `data-category`)
    
-  State class `hidden` for visibility control
    

## Card 11 — SPA-style page routing

-  Multiple `.page` sections (home/courses/quiz/playground/visualizer/dashboard/profile)
    
-  Toggle visibility with `hidden` class
    
-  Dynamic injection targets (e.g., `#coursesGrid`, `#quizCards`)
    

## Card 12 — Search & UI widgets

-  Global search input + dropdown
    
-  Hero search (input + button)
    
-  Sort `<select>`
    
-  Price range slider
    
-  Rating radio buttons
    

## Card 13 — Components & patterns

-  Hero section (title, subtitle, stats)
    
-  Cards & grids (courses, testimonials)
    
-  Step-by-step section (How It Works)
    
-  Tabs (Profile page)
    
-  Hamburger menu
    
-  Toasts container
    
-  Loading spinner
    

## Card 14 — Courses & filters sidebar

-  Category checkboxes
    
-  Difficulty radio group
    
-  Price range control + labels
    
-  Rating radio group
    
-  Clear filters button
    

## Card 15 — Quiz UI scaffold

-  Timer display
    
-  Div-based progress bar
    
-  Question text area
    
-  Options container
    
-  Prev/Next buttons
    
-  Submit button
    
-  Results container
    

## Card 16 — Code playground scaffold

-  Problem `<select>`
    
-  `<textarea>` code editor
    
-  Run/Submit buttons
    
-  Output panel
    

## Card 17 — Algorithm visualizer controls

-  Algorithm `<select>`
    
-  Array size slider
    
-  Speed slider
    
-  Conditional number input (binary search)
    
-  Algorithm description text
    
-  Complexity labels (Time, Space)
    
-  Visualization area (array bars container + stats)
    

## Card 18 — Dashboard & charts placeholders

-  Four stat cards
    
-  Category chart container
    
-  Activity chart container
    
-  Streak calendar container
    

## Card 19 — Profile page

-  Avatar + edit button
    
-  Name, bio, and profile stats
    
-  Tabs (About/Achievements/Settings)
    
-  Skills tags
    
-  Toggles (email notifications, dark mode)
    
-  Language `<select>`
    

## Card 20 — Footer

-  Branding & tagline
    
-  Quick Links list
    
-  Support list
    
-  Newsletter email input + button
    
-  Social icons row
    
-  Copyright text
    

## Card 21 — Scripts (placement & organization)

-  Data files (`courses.js`, `users.js`, `quizzes.js`, `problems.js`)
    
-  Utils (`helpers.js`, `dataGenerator.js`, `localStorage.js`)
    
-  Main app script (`main.js`)
    
-  Scripts placed at end of `<body>`
    

---

## Optional extras to learn (not present in this file)

-  Tables (`<table>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<td>`, `colspan`, `rowspan`)
    
-  Ordered lists `<ol>`
    
-  Definition lists `<dl>/<dt>/<dd>`
    
-  `<form>` wrapper + `method`/`action` + client validation (`required`, `pattern`)
    
-  Native `<progress>` / `<meter>`
    
-  Media embeds (`<video>`, `<audio>`, `<iframe>`)
    
-  Favicon + Open Graph / Twitter meta
    
-  Performance: `loading="lazy"`, `preload`, `prefetch`
    
-  PWA basics: web manifest, service worker