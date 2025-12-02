There are **5 main values** for the `position` property:
1. Static
2. Relative
3. Absolute
4. Fixed
5. Sticky

Static:
Every element is `static` by default.
Static elements ignore offsets like top/left/right/bottom properties and follow the **normal document flow**.

Relative:
Element remains **in normal flow**, but you can **shift it relative to its original position**.
Offsets(top/left/right/bottom) move it **without affecting other elements' positions**.
Mostly used as a container (parent) for an `absolute` child.

Absolute:
Removed from normal flow.
absolute positioning depends on the nearest non-static ancestor.
If no positioned ancestor exists → positioned relative to the **viewport**.
Mostly used for placing an icon in the corner of a card, or a tooltip.

Positioned **relative to the nearest positioned ancestor** (`relative`, `absolute`, or `fixed`, not static).

Fixed:
Removed from normal flow.
Positioned **relative to the viewport**.
Fixed elements remain fixed during scrolling.
Mostly used for chat widgets, Navigation bars stuck to the top.

Sticky:
A hybrid of `relative` and `fixed`. Sticky combines relative and fixed behavior.
Behaves like `relative` until a specified offset is reached (like `top: 0`).
After crossing the offset, it behaves like `fixed`.
Mostly used for Sticky table headers, section titles, navigation bars.

Extra:
Positioning often interacts with **z-index**. Non-positioned elements (static) cannot use z-index.

Overview:
**CSS provides five main position values:**
1. **static** – default, follows normal flow.
2. **relative** – stays in flow but can be offset from its original position; useful for setting a positioning context.
3. **absolute** – removed from flow and positioned relative to the nearest positioned ancestor.
4. **fixed** – removed from flow and positioned relative to the viewport; does not move on scroll.
5. **sticky** – acts like relative until a threshold is met, then sticks like fixed.  
    **Offsets like top/left only work with non-static positioning.**


**CSS Position Property – Comparison Table**

|Position Value|In Document Flow?|Offset Properties Work?|Positioned Relative To|Scroll Behavior|Common Use Cases|
|---|---|---|---|---|---|
|**static** (default)|✔ Yes|❌ No|Normal document flow|Moves with scroll|Regular elements|
|**relative**|✔ Yes|✔ Yes|Its **original position**|Moves with scroll|Minor adjustments, creating positioning context|
|**absolute**|❌ No|✔ Yes|**Nearest positioned ancestor** (non-static)|Moves with scroll|Tooltips, badges, overlays|
|**fixed**|❌ No|✔ Yes|**Viewport**|❌ Stays fixed during scroll|Sticky headers, chat widgets, menus|
|**sticky**|✔ Yes (until threshold)|✔ Yes|Itself (then viewport after stick point)|Becomes fixed after threshold|Sticky table headers, section labels|

**Extra Notes for Interviewers**
- **z-index works only with positioned (non-static)** elements.
- **absolute searches upward** for the first parent with `position: relative | absolute | fixed | sticky`.
- **sticky requires a scrollable container** and an offset like `top: 0`.
