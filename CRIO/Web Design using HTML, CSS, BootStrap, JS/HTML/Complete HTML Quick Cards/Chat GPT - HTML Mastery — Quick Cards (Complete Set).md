### 🃏 Card 1: Mental Model & Anatomy

**What & why**: HTML gives structure/meaning; CSS styles; JS adds behavior.  
**Key pieces**: tags, elements, attributes, nesting, block vs inline, DOM tree.  
**Pitfalls**: mixing presentational HTML; invalid nesting.  
**Try this**: sketch the DOM tree for a simple page.

---
### 🃏 Card 2: Page Skeleton

**What & why**: The minimal scaffold every page needs.  
**Key elements**: `<!DOCTYPE html>`, `<html lang>`, `<head>`, `<body>`.  
**Must‑haves**: `<meta charset="utf-8">`, `<title>`, viewport meta for mobile.  
**Try this**: create a minimal HTML file that passes the W3C validator.

---

### 🃏 Card 3: Head & Metadata

**What**: Info about the document for browsers, crawlers, and share cards.  
**Key elements**: `<meta name="description">`, `<meta name="viewport">`, `<link rel="icon">`, `<link rel="canonical">`, Open Graph/Twitter meta, `<base>`.  
**Pitfalls**: duplicate titles; forgetting canonical on duplicate content.  
**Try this**: add favicon + description to a demo page.

---

### 🃏 Card 4: Global Attributes

**What**: Attributes available on (almost) all elements.  
**Examples**: `id`, `class`, `title`, `hidden`, `tabindex`, `draggable`, `spellcheck`, `translate`, `contenteditable`, `inert`.  
**Try this**: toggle `hidden` and `inert` to see interactivity/focus changes.

---

### 🃏 Card 5: Text & Inline Semantics

**What**: Meaningful text markup (not just visual).  
**Elements**: headings `h1–h6`, `p`, `em`, `strong`, `small`, `mark`, `sup`, `sub`, `code`, `kbd`, `samp`, `abbr`, `cite`, `q`, `time`, `wbr`, `br`, `hr`.  
**Pitfalls**: using `<b>/<i>` for meaning—prefer `<strong>/<em>`.  
**Try this**: mark up a blog excerpt with appropriate inline semantics.

---

### 🃏 Card 6: Lists

**What**: Group related items.  
**Elements**: `ul/ol/li`, `dl/dt/dd`.  
**Tips**: choose `ol` when order matters; add `value` to continue numbering.  
**Try this**: convert a FAQ into a definition list.

---

### 🃏 Card 7: Links & Navigation

**What**: Connect documents and sections.  
**Elements**: `<a href>`, `<nav>`, skip links.  
**Important attrs**: `rel="noopener noreferrer"`, `download`, `referrerpolicy`.  
**SEO rels**: `canonical`, `alternate`/`hreflang`, `ugc`, `sponsored`, `me`.  
**Try this**: build a top nav with a “skip to main content” link.

---

### 🃏 Card 8: Sections & Landmarks

**What**: Document structure for humans and assistive tech.  
**Elements**: `header`, `main`, `section`, `article`, `aside`, `footer`, `address`.  
**Tip**: one `main` per page; use headings inside sections.  
**Try this**: outline a news homepage with proper landmarks.

---

### 🃏 Card 9: Containers

**What**: Generic grouping.  
**Elements**: `div` (block), `span` (inline).  
**Pitfalls**: “divitis”—overusing containers instead of semantic tags.  
**Try this**: refactor a `div` soup into semantic elements.

---

### 🃏 Card 10: Images & Figures

**What**: Embed graphics with meaning.  
**Elements**: `img`, `figure`, `figcaption`.  
**Attrs**: `alt` (purposeful text), `width/height` (prevent CLS), `loading`, `decoding`, `fetchpriority`, `referrerpolicy`, `crossorigin`.  
**Try this**: add `figcaption` to a chart image describing the insight.

---

### 🃏 Card 11: Responsive Images

**What**: Serve the right image for device/context.  
**Tools**: `srcset`, `sizes`, `<picture>` + `<source>` (art direction).  
**Try this**: provide 1x/2x variants and constrain via `sizes`.

---

### 🃏 Card 12: SVG vs Canvas

**What**: Two graphics approaches.  
**SVG**: semantic/vector, accessible, stylable.  
**Canvas**: pixel API for dynamic drawing.  
**Try this**: inline an SVG icon and style with CSS.

---

### 🃏 Card 13: Audio & Video

**What**: Native media playback.  
**Elements**: `audio`, `video`, `source`, `track`.  
**Attrs**: `controls`, `autoplay`, `muted`, `loop`, `playsinline`, `preload`, `poster`.  
**A11y**: captions via `<track kind="captions">`.  
**Try this**: embed a video with captions and poster.

---

### 🃏 Card 14: Tables for Data

**What**: Tabular data (never for layout).  
**Elements**: `table`, `caption`, `thead/tbody/tfoot`, `tr`, `th`, `td`, `colgroup/col`.  
**A11y**: `scope`, `headers`/`id` for complex tables.  
**Try this**: make a table with a caption and proper header scopes.

---

### 🃏 Card 15: Forms – Core

**What**: Collect and submit user data.  
**Elements**: `form`, `label`, `input`, `textarea`, `select`, `option`, `button`.  
**Attrs**: `action`, `method`, `name`, `value`.  
**Try this**: build a contact form with properly associated labels.

---

### 🃏 Card 16: Inputs & Widgets

**What**: The variety of controls.  
**Types**: `text`, `email`, `url`, `password`, `number`, `tel`, `date`, `time`, `datetime-local`, `month`, `week`, `color`, `range`, `checkbox`, `radio`, `file`, `hidden`, `search`.  
**Try this**: create a settings form using at least 8 input types.

---

### 🃏 Card 17: Form Grouping & Extras

**What**: Structure and hints.  
**Elements**: `fieldset`, `legend`, `datalist`, `optgroup`, `output`, `progress`, `meter`.  
**Try this**: add a `datalist` of suggestions to a search box.

---

### 🃏 Card 18: Validation & UX

**What**: Built‑in constraints and ergonomics.  
**Attrs**: `required`, `min`, `max`, `step`, `pattern`, `maxlength`, `minlength`, `novalidate`.  
**UX**: `autocomplete` tokens (e.g., `email`, `cc-number`), `inputmode`, `enterkeyhint`, `autofocus`, `readonly`, `disabled`, helpful error text via `aria-describedby`.  
**Try this**: validate a credit‑card form with autocomplete tokens.

---

### 🃏 Card 19: Form Submission Control

**What**: Connect controls to target forms and endpoints.  
**Attrs**: `form` (associate outside the `<form>`), `formaction`, `formenctype`, `formmethod`, `formnovalidate`, `formtarget`.  
**Try this**: create two submit buttons that post to different URLs.

---

### 🃏 Card 20: Accessibility (A11y) Essentials

**What**: Make content usable for everyone.  
**Focus**: logical heading order; landmarks; keyboard focus; visible focus; alt text matching purpose.  
**ARIA**: use native semantics first; add ARIA only when needed.  
**Try this**: keyboard‑test a page and fix any focus traps.

---

### 🃏 Card 21: Embeds & Sandboxing

**What**: Third‑party or nested pages.  
**Elements**: `iframe`, `embed`, `object` (legacy).  
**Security**: `sandbox`, `allow` (Permissions Policy), `referrerpolicy`, `srcdoc`.  
**Try this**: embed a page with a restrictive sandbox, then open as needed.

---

### 🃏 Card 22: Interactive Without JS

**What**: Built‑in disclosure/UI.  
**Elements**: `details`/`summary`, `dialog` (with `.showModal()`), Popover API (`popover`, `popovertarget`, `popovertargetaction`).  
**Try this**: make a FAQ using `details` and an “About” modal with `<dialog>`.

---

### 🃏 Card 23: Templates & Web Components (HTML Side)

**What**: Reusable DOM chunks and slots.  
**Elements**: `<template>` (inert markup), `<slot>` (content projection).  
**Concepts**: custom elements, shadow DOM (JS-driven but HTML participates).  
**Try this**: define a template and clone it with minimal JS.

---

### 🃏 Card 24: Scripting Hooks

**What**: Add/optimize scripts.  
**Elements/attrs**: `<script src>`, `type="module"`, `defer`, `async`, `nomodule`, `crossorigin`, `integrity` (SRI).  
**Try this**: switch to modules + `defer` and measure paint timings.

---

### 🃏 Card 25: Styling Hooks

**What**: Attach CSS.  
**Elements**: `<link rel="stylesheet">`, `<style>`.  
**Media**: `media` attribute for conditional styles.  
**Try this**: preload a critical CSS file and compare FCP.

---

### 🃏 Card 26: Resource Hints & Performance

**What**: Guide the browser’s fetches.  
**Hints**: `<link rel="preload" as>`, `rel="modulepreload"`, `preconnect`, `dns-prefetch`, `prefetch`.  
**Images**: `fetchpriority`, `loading`, `decoding`.  
**Try this**: add `preconnect` to a font CDN and inspect timing.

---

### 🃏 Card 27: Security‑Minded HTML

**What**: Reduce common risks.  
**Practices**: `rel="noopener noreferrer"` on external `_blank` links, SRI on third‑party scripts, conservative `iframe sandbox`, `referrerpolicy`.  
**Note**: prefer HTTP headers for CSP; HTML meta fallback exists but is limited.  
**Try this**: audit all external links and add safe `rel` values.

---

### 🃏 Card 28: SEO & Shareability

**What**: Help users and bots find/understand pages.  
**Tools**: headings outline, unique `<title>`, meta description, `rel="canonical"`, `hreflang`, structured data (JSON‑LD inside `<script type="application/ld+json">`).  
**Try this**: add Article schema to a blog post.

---

### 🃏 Card 29: Internationalization (i18n)

**What**: Proper language and direction.  
**Elements/attrs**: `lang` (root and subtrees), `dir="ltr|rtl|auto"`, `<bdi>`, `<bdo>`, ruby annotations (`<ruby><rt><rp>`).  
**Try this**: mark up a bilingual sentence with `bdi` and `dir="auto"`.

---

### 🃏 Card 30: PWA Surface (HTML Bits)

**What**: App‑like integration touchpoints.  
**Hooks**: `<link rel="manifest">`, `meta name="theme-color"`, app icons (`apple-touch-icon`, SVG favicon), `meta name="apple-mobile-web-app-capable"` (where applicable).  
**Try this**: wire up a manifest and verify installability.

---

### 🃏 Card 31: Data Attributes & Microdata

**What**: Attach lightweight data or semantics.  
**`data-*`**: arbitrary values for scripts.  
**Microdata**: `itemscope`, `itemtype`, `itemprop` (less common than JSON‑LD).  
**Try this**: add `data-*` to power a tooltip.

---

### 🃏 Card 32: Referrer/CORS on Elements

**What**: Privacy and cross‑origin fetch rules.  
**Where**: `img`, `script`, `link`, `video`, `iframe` can use `referrerpolicy`/`crossorigin`.  
**Try this**: load an image with `crossorigin` and observe network behavior.

---

### 🃏 Card 33: DevTools & Validation

**What**: Inspect, debug, and verify.  
**Tools**: browser DevTools (Elements, Accessibility tree), Lighthouse, W3C validator.  
**Try this**: run an accessibility snapshot and fix the top issue.

---

### 🃏 Card 34: Compatibility & Progressive Enhancement

**What**: Make features degrade gracefully.  
**Tools**: feature detection, `noscript`, safe fallbacks, semantic HTML first.  
**Try this**: ensure core content works with JS disabled.

---

### 🃏 Card 35: Deprecated/Obsolete & What Not to Use

**What**: Avoid legacy/presentational markup.  
**Examples**: `center`, `font`, `big`, `marquee`, `blink`, framesets, table‑layout for non‑data.  
**Try this**: replace a presentational tag with semantic HTML + CSS.

---

### 🃏 Card 36: Events & Inline Handlers

**What**: Event attributes exist but are best avoided inline.  
**Examples**: `onclick`, `oninput` etc. Prefer JS listeners; keep HTML declarative.  
**Try this**: remove inline handlers and bind via `addEventListener`.

---

### 🃏 Card 37: Printing & Media Targets (HTML Side)

**What**: Prepare for print (mostly CSS), but wire via HTML.  
**Hooks**: alternate styles via `<link media="print">`, proper headings, avoid hidden critical content.  
**Try this**: add a print stylesheet and preview output.

---

### 🃏 Card 38: Metadata Odds & Ends

**What**: Niche but useful.  
**Items**: `<meta name="robots">`, `http-equiv` (charset/refresh—use sparingly), `<base href>`/`target`.  
**Try this**: add `<base href>` and confirm relative URL resolution.

---

### 🃏 Card 39: Performance Budget Checklist (HTML Signals)

**What**: Help the browser start fast.  
**Signals**: order CSS before JS, `defer`/modules, resource hints, explicit `width/height` on media, minimal blocking tags in `<head>`.  
**Try this**: measure CLS before/after adding intrinsic sizes to images.

---

### 🃏 Card 40: Copy & Content Semantics

**What**: Choose elements that reflect intent.  
**Elements**: `address` (contact for nearest ancestor/article), `blockquote cite`, `cite` (works title), `time datetime`, `dfn` (term being defined).  
**Try this**: mark up an author bio with `address` and `time`.

---

## Study Routes

- **Essentials first**: Cards 1–15
    
- **Everyday pro**: Cards 16–28
    
- **Edge/advanced**: Cards 29–40
    

---

## Practice Projects

1. Article page: headings, figure, table, footers (Cards 5, 8, 10, 14, 40).
    
2. Product page: responsive images, forms, SEO meta (Cards 10–11, 15–19, 28).
    
3. Video blog: `<video>` + captions, share cards (Cards 13, 28).
    
4. Docs site: nav + landmarks + a11y (Cards 7–8, 20, 33).
    

---
