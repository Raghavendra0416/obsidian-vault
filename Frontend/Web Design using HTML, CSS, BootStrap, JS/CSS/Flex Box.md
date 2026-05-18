Axis:

|**If flex-direction is...**|**Main Axis is...**|**Cross Axis is...**|
|---|---|---|
|**Row** (Default)|Horizontal ( ⮕ )|Vertical ( ⬇ )|
|**Column**|Vertical ( ⬇ )|Horizontal ( ⮕ )

| **Command**       | **Controls physically...**    | Axis       |
| ----------------- | ----------------------------- | ---------- |
| `justify-content` | **Left ↔ Right** (Horizontal) | Main Axis  |
| `align-items`     | **Top ↕ Bottom** (Vertical)   | Cross Axis |

|**If you want to move items...**|**In row mode use:**|**In column mode use:**|
|---|---|---|
|**Left / Right**|`justify-content`|`align-items`|
|**Up / Down**|`align-items`|`justify-content`|

Basic:

| **Flex Command**                 | **Movement Description**                          | **Where to put?** | **Real-World Example**                                                                             |
| -------------------------------- | ------------------------------------------------- | ----------------- | -------------------------------------------------------------------------------------------------- |
| **1. Setup**                     |                                                   |                   |                                                                                                    |
| `display: flex`                  | Enables flexible layout. Children become "items". | **Parent**        | Turning a standard vertical bullet list `<ul>` into a horizontal menu.                             |
| **2. Direction**                 |                                                   |                   |                                                                                                    |
| `flex-direction: row`            | **Default.** Lines items up Left → Right.         | **Parent**        | Standard website header or navigation bar.                                                         |
| `flex-direction: column`         | Stacks items Top ↓ Bottom.                        | **Parent**        | Mobile layouts or a Sidebar with stacked links.                                                    |
| **3. Main Alignment**            | _(Horizontal spacing)_                            |                   |                                                                                                    |
| `justify-content: center`        | Packs items to the middle.                        | **Parent**        | A "Hero" section with a centered title and button.                                                 |
| `justify-content: space-between` | First item start, Last item end.                  | **Parent**        | **Navbar:** Logo stays on the far left, Links stay on the far right.                               |
| `justify-content: space-around`  | Equal spacing around all items.                   | **Parent**        | A row of pricing cards or social media icons.                                                      |
| **4. Cross Alignment**           | _(Vertical alignment)_                            |                   |                                                                                                    |
| `align-items: center`            | Centers items vertically.                         | **Parent**        | Centering an icon perfectly next to text inside a button.                                          |
| `align-items: stretch`           | **Default.** Stretches to fill height.            | **Parent**        | Equal-height columns in a dashboard (sidebar matches content height).                              |
| **5. Behavior**                  |                                                   |                   |                                                                                                    |
| `flex-wrap: wrap`                | Items drop to next line if no space.              | **Parent**        | A photo gallery that adjusts columns based on screen size.                                         |
| `gap: 20px`                      | Adds space between items.                         | **Parent**        | Adding consistent whitespace between gallery images.                                               |
| **6. Item Specifics**            |                                                   |                   |                                                                                                    |
| `flex: 1`                        | Item grows to take all empty space.               | **Child**         | **Search Input:** The input stretches to fill the bar, while the "Search" button stays fixed size. |
| `align-self: center`             | Overrides parent alignment.                       | **Child**         | One specific item in a list needs to be centered while others are top-aligned.                     |
| `order: -1`                      | Moves item to the visual front.                   | **Child**         | Moving the "Featured" product to the first spot on mobile screens.                                 |

Advanced:

| **Flex Command**               | **Description**                                            | **Where to put?** | **Real-World Example**                                                                                        |
| ------------------------------ | ---------------------------------------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------- |
| **1. Multi-Line Spacing**      | _(Only works if `flex-wrap: wrap` is on)_                  |                   |                                                                                                               |
| `align-content: center`        | Packs **rows** of items together in the middle.            | **Parent**        | You have a gallery of 50 images and want the whole block of rows centered vertically on the page.             |
| `align-content: space-between` | Spacing between **rows** (not items).                      | **Parent**        | Spreading out lines of text or tags to fill a card height.                                                    |
| **2. Precision Sizing**        | _( Breaking down `flex: 1` )_                              |                   |                                                                                                               |
| `flex-basis: 300px`            | Sets the **ideal starting size** before growing/shrinking. | **Child**         | "I want this sidebar to _try_ to be 300px wide, but shrink if it has to."                                     |
| `flex-grow: 2`                 | "Greediness" factor.                                       | **Child**         | Item A has `flex-grow: 1`, Item B has `flex-grow: 2`. Item B will take up **twice** as much empty space as A. |
| `flex-shrink: 0`               | **Prevent shrinking.**                                     | **Child**         | **Crucial:** Prevents an icon or image from getting squished when the screen gets too small.                  |
| **3. Shorthands**              |                                                            |                   |                                                                                                               |
| `flex-flow: row wrap`          | Combines `flex-direction` and `flex-wrap` into one line.   | **Parent**        | Saving typing time. Instead of two lines, you just write one.                                                 |