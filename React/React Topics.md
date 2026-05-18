## What Public & Assets
Think of it this way:
**`public/` = "Don't touch it, just serve it"** Vite takes whatever is in `public/` and puts it directly into the final build folder **as-is**, without processing it.

**`src/assets/` = "Process it and optimize it"** Vite handles these files during the build — it can compress them, rename them with a hash, and bundle them efficiently.


Real examples of what goes where:

Use `public/` for:
- `favicon.ico` — browsers look for this at exactly `/favicon.ico`, the URL must never change
- `robots.txt` — search engines expect it at exactly `/robots.txt`
- Large videos or PDFs you just want to link to
- Files referenced **outside** your React code (e.g., in plain HTML)

Use `src/assets/` for:
- Images you use **inside components** — hero images, icons, illustrations
- SVGs you import into JSX
- Fonts used in your CSS
- Basically **anything your React components use**

---
