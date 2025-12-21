| **Category (Side Heading)** | **Property**            | **Description & Example**                                                                                              |
| --------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Container: Activation**   | `display`               | **Required.** Defines the element as a grid container.<br><br>`display: grid;`                                         |
| **Container: Tracks**       | `grid-template-columns` | Defines width of vertical columns.<br><br>`grid-template-columns: 100px 1fr auto;`                                     |
|                             | `grid-template-rows`    | Defines height of horizontal rows.<br><br>`grid-template-rows: 200px 1fr;`                                             |
|                             | `grid-template-areas`   | Defines a layout using named areas (mapped to children).<br><br>`grid-template-areas: "header header" "main sidebar";` |
| **Container: Spacing**      | `gap` (or `grid-gap`)   | Sets the whitespace between rows and columns.<br>  <br>`gap: 20px;`                                                    |
|                             | `row-gap`               | Sets space only between rows.<br><br>`row-gap: 10px;`                                                                  |
|                             | `column-gap`            | Sets space only between columns.<br><br>`column-gap: 15px;`                                                            |
| **Container: Alignment**    | `justify-items`         | Aligns content **horizontally** (inline axis) inside the track.<br><br>`justify-items: center;` (start, end, stretch)  |
|                             | `align-items`           | Aligns content **vertically** (block axis) inside the track.<br><br>`align-items: center;` (start, end, stretch)       |
|                             | `justify-content`       | Aligns the **whole grid** horizontally if it's smaller than the container.<br><br>`justify-content: center;`           |
|                             | `align-content`         | Aligns the **whole grid** vertically if it's smaller than the container.<br><br>`align-content: center;`               |
| **Item: Positioning**       | `grid-column`           | Shorthand for `grid-column-start` / `end`. Determines where an item sits.<br><br>`grid-column: 1 / 3;` (Span 2 cols)   |
|                             | `grid-row`              | Shorthand for `grid-row-start` / `end`.<br><br>`grid-row: 2 / 4;` (Span 2 rows)                                        |
|                             | `grid-area`             | Assigns an item to a named area defined in the parent.<br><br>`grid-area: header;`                                     |
| **Item: Alignment**         | `justify-self`          | Overrides horizontal alignment for **this single item**.<br><br>`justify-self: end;`                                   |
|                             | `align-self`            | Overrides vertical alignment for **this single item**.<br><br>`align-self: start;`                                     |