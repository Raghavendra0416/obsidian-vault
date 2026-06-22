### Tasks:
**Create a drop down box with search option:**

**Step 1** — The arrow/toggle is on the **right** side, not the left. And the box doesn't "change" — it stays, but the list _appears below it_.

**Step 2** ----  `isOpen` flips between `true`/`false` on click, and the list renders conditionally.

**Step 3** --- Next we need to create a list and in that list we need to create a inputbox and if the inputbox is empty show all elements or show only the items in the input box -> to do that we need to use filter.
One thing to add — `filtered` is **not a state**, it's just a variable computed from `searchTerm` state:
```js
// NOT useState — just a variable
const filtered = ALL_CARS.filter(car =>
    car.toLowerCase().includes(searchTerm.toLowerCase())
);
```
When `searchTerm` is empty → `filter` returns everything. When you type → it returns only matches. React re-renders automatically because `searchTerm` state changed.

**Step 4** --- Once an item is selected then we need to show them as button in the box we have created at the begining, with 'X' to remove if not needed.
 One thing to add — you need `e.stopPropagation()` on the `×` button, otherwise clicking `×` also triggers the parent `<div>`'s `onClick` and reopens the dropdown.
```jsx
<button onMouseDown={e => removeItem(car, e)}>×</button>
//                         ↑ pass the event so you can stopPropagation inside removeItem
```
---
**Your approach re-written cleanly:**
- Create a `<div>` that acts as the select box — arrow on the right, selected tags inside it, clicking it toggles `isOpen`
- Below it, conditionally render the dropdown panel (`isOpen && ...`)
- Inside the panel — a search `<input>` that updates `searchTerm`, and a `<ul>` that shows `filtered` items with checkboxes
- Checking an item adds it to `selected` array and shows it as a tag with `×` in the trigger box. `×` removes it from the array, with `stopPropagation` to prevent reopening
---
