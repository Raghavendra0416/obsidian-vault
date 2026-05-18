| Collection  | Stores                                   | Allows duplicate values? | Order maintained?                                     |
| ----------- | ---------------------------------------- | ------------------------ | ----------------------------------------------------- |
| **Array**   | Indexed list of values                   | ✔ Yes                    | ✔ Yes                                                 |
| **Object**  | Key–value pairs (keys = strings/symbols) | Keys must be unique      | ❌ No guaranteed order (mostly insertion order in ES6) |
| **Map**     | Key–value pairs (keys of any type)       | Keys unique              | ✔ Yes (insertion order)                               |
| **Set**     | Unique values only                       | ❌ No                     | ✔ Yes                                                 |
| **WeakMap** | Key–value pairs (keys must be objects)   | Keys unique              | ✔ Yes                                                 |
| **WeakSet** | Unique objects only                      | ❌ No                     | ✔ Yes                                                 |

**Maps:**

| **Operation**        | **Map Methods**                                    | **Set Methods**                                   |
| -------------------- | -------------------------------------------------- | ------------------------------------------------- |
| **Add data**         | `map.set(key, value)`                              | `set.add(value)`                                  |
| **Get data**         | `map.get(key)`                                     | ❌ (No get → only check using `has()`)             |
| **Check existence**  | `map.has(key)`                                     | `set.has(value)`                                  |
| **Delete one item**  | `map.delete(key)`                                  | `set.delete(value)`                               |
| **Delete all items** | `map.clear()`                                      | `set.clear()`                                     |
| **Total count**      | `map.size`                                         | `set.size`                                        |
| **Iterate entries**  | `map.entries()`                                    | `set.entries()` _(returns `[value, value]`)_      |
| **Iterate keys**     | `map.keys()`                                       | `set.keys()` _(same as values)_                   |
| **Iterate values**   | `map.values()`                                     | `set.values()`                                    |
| **Looping**          | `map.forEach((value, key) => {})`                  | `set.forEach((value) => {})`                      |
| **Default iterator** | `map[Symbol.iterator]()` → same as `map.entries()` | `set[Symbol.iterator]()` → same as `set.values()` |

Sets:

| Method                        | Description                        |
| ----------------------------- | ---------------------------------- |
| `set(key, value)`             | Adds/updates key–value pair        |
| `get(key)`                    | Returns the value for given key    |
| `has(key)`                    | Checks if key exists               |
| `delete(key)`                 | Removes a key–value pair           |
| `clear()`                     | Removes all entries                |
| `size`                        | Number of key–value pairs          |
| `keys()`                      | Returns iterable of keys           |
| `values()`                    | Returns iterable of values         |
| `entries()`                   | Returns iterable of `[key, value]` |
| `forEach((value, key) => {})` | Loop through all entries           |
| `[Symbol.iterator]`           | Default iterator → entries         |

Comparison Table:

| **Action**          | **Map Method (Key-Value)**   | **Set Method (Unique Values)** | **Notes**                                                                       |
| ------------------- | ---------------------------- | ------------------------------ | ------------------------------------------------------------------------------- |
| **Add Item**        | `map.set(key, value)`        | `set.add(value)`               | Map returns the Map itself (chainable). Set returns the Set itself (chainable). |
| **Get Item**        | `map.get(key)`               | _N/A_                          | Sets do not support accessing values by index or key.                           |
| **Check Existence** | `map.has(key)`               | `set.has(value)`               | Returns `true` if found, `false` otherwise.                                     |
| **Delete Item**     | `map.delete(key)`            | `set.delete(value)`            | Returns `true` if the element existed and was removed.                          |
| **Delete All**      | `map.clear()`                | `set.clear()`                  | Removes all elements from the collection.                                       |
| **Count Items**     | `map.size`                   | `set.size`                     | **Note:** This is a property, not a method (no `()`).                           |
| **Iterate (Loop)**  | `map.forEach((v, k) => ...)` | `set.forEach((v, v2) => ...)`  | In Set, the callback arguments are the same (value, value).                     |

Iterator Methods:

| **Iterator**            | **Map Return Value**               | **Set Return Value**                                         |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------ |
| **`.keys()`**           | Returns an iterable of **Keys**.   | Returns an iterable of **Values** (Alias for `.values()`).   |
| **`.values()`**         | Returns an iterable of **Values**. | Returns an iterable of **Values**.                           |
| **`.entries()`**        | Returns `[key, value]` pairs.      | Returns `[value, value]` pairs (for compatibility with Map). |
| **`[Symbol.iterator]`** | Same as `.entries()`               | Same as `.values()`                                          |

|**Feature**|**Regular Object / Array**|**Map / Set**|
|---|---|---|
|**Key Types**|Strings & Symbols only|**Any type** (Objects, Functions, primitives)|
|**Key Order**|Complex rules (mostly insertion)|**Strictly insertion order**|
|**Size**|Manual calculation|**`.size` property**|
|**JSON**|Native support|**Requires manual conversion**|

Important Points: Map
- Keys can be ANY type
- Maintains insertion order
- Fast lookups & insertions
- Iteration is simple
- Avoids key collisions
- Useful when keys are dynamic

Important Points: Set
- Stores only UNIQUE values
- Fast membership checking
- Order is maintained
- Used frequently for removing duplicates
- No indexing
- Best when you only care about VALUES and uniqueness

|Concept|Map|Set|
|---|---|---|
|Stores|Key–value pairs|Only values|
|Key type|Any type|Value only|
|Duplicates|Keys unique|Values unique|
|Order|Maintains order|Maintains order|
|Size|`size` property|`size` property|
|Use case|Fast key lookup|Fast value lookup|