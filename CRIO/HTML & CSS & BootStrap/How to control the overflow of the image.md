to use it:
Background-image: url(),
Backgroung-size:cover,
Background-repeat: no-repeat;

Object-fit: we can use:
- contain,
- cover

The Unit Difference
- **`%` (Percent):** "Be 100% the size of my **Parent** (the div)." 
- **`vw/vh` (Viewport):** "Be 100% the size of the **Browser Screen**."

The Rule of Thumb
- **Use `%`** when you want an element to fit inside a specific card, box, or section.
- **Use `vw/vh`** only when you want something to take up the **entire screen**

1. **Parent (`div`)**: Needs a specific `width` and `height`.
2. **Child (`img`)**: Needs `width: 100%` and `height: 100%` to fill the parent.
3. **Child (`img`)**: Needs `object-fit: cover` to stop the image from looking squashed.

| **Feature**          | **object-fit**                                               | **background-size**                                           |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------- |
| **Applied To**       | Real HTML elements: `<img />` or `<video>`.                  | Empty containers: `<div>`, `<section>`, `<body>`.             |
| **The Image Source** | Comes from HTML: `<img src="...">`                           | Comes from CSS: `background-image: url(...)`                  |
| **Accessibility**    | **High.** You can add `alt="description"`. Google sees this. | **None.** Screen readers ignore it. Google mostly ignores it. |
| **Right Use Case**   | **Content.** (Product photos, User avatars, News images).    | **Decoration.** (Patterns, Textures, Abstract shapes).        |
