### Grid:

Categorized by where they are applied (the **Container** vs. the **Items**).
#### 1. Properties for the Parent (Grid Container)
These properties define the grid structure, spacing, and alignment.

|**Property**|**Description**|**Common Values**|
|---|---|---|
|**`display`**|Defines the element as a grid container.|`grid`, `inline-grid`, `subgrid`|
|**`grid-template-columns`**|Defines the number and width of columns.|`100px`, `1fr`, `repeat(3, 1fr)`, `auto`|
|**`grid-template-rows`**|Defines the number and height of rows.|`50px`, `auto`, `minmax(100px, auto)`|
|**`grid-template-areas`**|Defines named grid areas to easily place items.|`"header header" "nav main"`, `none`|
|**`grid-template`**|**Shorthand** for `rows`, `columns`, and `areas` in one line.|_Complex syntax combining above values_|
|**`column-gap`**|Sets the size of the gap between columns.|`20px`, `1rem`|
|**`row-gap`**|Sets the size of the gap between rows.|`20px`, `1rem`|
|**`gap`**|**Shorthand** for `row-gap` and `column-gap`.|`10px` (both), `10px 20px` (row col)|
|**`justify-items`**|Aligns items along the **inline (row) axis** inside their area.|`start`, `end`, `center`, `stretch` (default)|
|**`align-items`**|Aligns items along the **block (column) axis** inside their area.|`start`, `end`, `center`, `stretch` (default)|
|**`place-items`**|**Shorthand** for `align-items` and `justify-items`.|`center` (both), `center start`|
|**`justify-content`**|Aligns the _entire grid_ horizontally if it's smaller than container.|`start`, `end`, `center`, `space-between`, `space-around`|
|**`align-content`**|Aligns the _entire grid_ vertically if it's smaller than container.|`start`, `end`, `center`, `space-between`, `space-around`|
|**`place-content`**|**Shorthand** for `align-content` and `justify-content`.|`center` (both), `center space-between`|
|**`grid-auto-columns`**|Defines width of _implicit_ columns (created automatically).|`100px`, `auto`, `1fr`|
|**`grid-auto-rows`**|Defines height of _implicit_ rows (created automatically).|`100px`, `auto`, `1fr`|
|**`grid-auto-flow`**|Controls how auto-placed items flow into the grid.|`row` (default), `column`, `dense`|
|**`grid`**|**Mega Shorthand** setting all explicit & implicit properties.|_Complex syntax, rarely used by hand_|

#### 2. Properties for the Children (Grid Items)

These properties control where specific items go and how they span across the grid lines.

|**Property**|**Description**|**Common Values**|
|---|---|---|
|**`grid-column-start`**|Specifies on which column line the item starts.|`1`, `2`, `span 2`, `auto`|
|**`grid-column-end`**|Specifies on which column line the item ends.|`3`, `4`, `span 2`, `auto`|
|**`grid-column`**|**Shorthand** for `start` and `end`.|`1 / 3`, `1 / span 2`|
|**`grid-row-start`**|Specifies on which row line the item starts.|`1`, `2`, `span 3`, `auto`|
|**`grid-row-end`**|Specifies on which row line the item ends.|`3`, `4`, `span 3`, `auto`|
|**`grid-row`**|**Shorthand** for `start` and `end`.|`2 / 4`, `1 / span 3`|
|**`grid-area`**|**Shorthand** used to assign an item to a named area OR set start/end lines for both row and column.|`header`, `1 / 2 / 3 / 4` (row-start / col-start / row-end / col-end)|
|**`justify-self`**|Aligns _only this individual item_ horizontally inside its cell.|`start`, `end`, `center`, `stretch`|
|**`align-self`**|Aligns _only this individual item_ vertically inside its cell.|`start`, `end`, `center`, `stretch`|
|**`place-self`**|**Shorthand** for `align-self` and `justify-self`.|`center`, `center stretch`|

#### Key Difference: Alignment Terminology

Alignment syntax is often the hardest part to remember. Here is the logic:
- **Items:** Refers to aligning the items _inside_ their grid cells. (`justify-items`, `align-items`).
- **Content:** Refers to aligning the _grid tracks themselves_ inside the parent container. (`justify-content`, `align-content`).
- **Self:** Refers to overriding alignment for a _single specific item_. (`justify-self`, `align-self`).


---
### Flex Box:

Flexbox is a **one-dimensional** layout system (it deals with rows **OR** columns, not both at the same time).
#### 1. Properties for the Parent (Flex Container)

These properties control the direction and alignment of the items as a group.

|**Property**|**Description**|**Common Values**|
|---|---|---|
|**`display`**|Activates flexbox layout.|`flex`, `inline-flex`|
|**`flex-direction`**|Defines the main axis (direction) items are placed.|`row` (default), `row-reverse`, `column`, `column-reverse`|
|**`flex-wrap`**|Controls whether items force onto one line or can wrap.|`nowrap` (default), `wrap`, `wrap-reverse`|
|**`flex-flow`**|**Shorthand** for `flex-direction` and `flex-wrap`.|`row wrap`, `column nowrap`|
|**`justify-content`**|Aligns items along the **Main Axis** (usually horizontal).|`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`|
|**`align-items`**|Aligns items along the **Cross Axis** (usually vertical).|`stretch` (default), `flex-start`, `flex-end`, `center`, `baseline`|
|**`align-content`**|Aligns _multiple lines_ of content (only works if `flex-wrap: wrap` is on).|`stretch`, `flex-start`, `flex-end`, `center`, `space-between`|
|**`gap`**|Creates space between flex items.|`10px`, `1rem`|
|**`row-gap`**|Creates space only between rows (when wrapping).|`10px`|
|**`column-gap`**|Creates space only between columns.|`10px`|

#### 2. Properties for the Children (Flex Items)

These properties control the sizing and order of individual items.

|**Property**|**Description**|**Common Values**|
|---|---|---|
|**`order`**|Controls the order in which items appear.|`0` (default), `1`, `-1` (integers only)|
|**`flex-grow`**|Defines how much the item will grow relative to others to fill empty space.|`0` (don't grow), `1` (grow evenly), `2` (take twice as much space)|
|**`flex-shrink`**|Defines how much the item will shrink if there isn't enough space.|`1` (default, shrink allowed), `0` (don't shrink)|
|**`flex-basis`**|Defines the initial size of the item before remaining space is distributed.|`auto` (default), `200px`, `50%`, `content`|
|**`flex`**|**Shorthand** for `grow`, `shrink`, and `basis`. **(Highly Recommended)**|`0 1 auto` (default), `1` (grow evenly), `1 0 auto`|
|**`align-self`**|Overrides `align-items` for this specific item.|`auto`, `flex-start`, `flex-end`, `center`, `stretch`|

#### The Cheat Sheet: "The 3 Numbers"
The flex property is the most important child property. It takes three values:
flex: grow, shrink, basis

1. **`flex: 1`** → Grows to fill space, shrinks if needed. (Equivalent to `1 1 0%`).
2. **`flex: 0 1 auto`** → Default behavior. Does not grow, shrinks if crowded, sized by content.
3. **`flex: 0 0 200px`** → Fixed width. Never grows, never shrinks, always 200px.

##### Key Concept: Axes
Unlike Grid (which has fixed X and Y axes), Flexbox axes change based on `flex-direction`.
- **If `flex-direction: row`:** Main Axis is horizontal (Left → Right).
- **If `flex-direction: column`:** Main Axis is vertical (Top → Bottom).

_Tip: `justify-content` always works on the Main Axis, while `align-items` always works on the Cross Axis._

---
r