MUI uses these breakpoints under the hood:

| Key  | Width             |
| ---- | ----------------- |
| `xs` | 0px → (mobile)    |
| `sm` | 600px → (tablet)  |
| `md` | 900px → (laptop+) |
So `display: { xs: 'flex', sm: 'none' }` means:
- On **mobile** (`xs`) → show it (`flex`)
- On **tablet and above** (`sm` and up) → hide it (`none`)

This is MUI's **responsive `sx` syntax** — instead of writing a value directly, you pass an object where each key is a breakpoint. MUI applies them as CSS `min-width` media queries internally.

----

