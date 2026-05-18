**Shallow copy** — copies only the top-level properties. Nested objects are still **shared by reference**.
**Deep copy** — copies everything recursively. Nested objects are **fully independent**
```JS
const original = { name: "Rex", address: { city: "Delhi" } };

// Shallow copy
//In shalow copy - inner objects or arrays will be effected by the change of inner objects
const shallow = { ...original };
shallow.address.city = "Mumbai";

console.log(original.address.city); // "Mumbai" — original affected!

// Deep copy
//In Deep copy - inner objects or arrays will not be effected by the change of inner objects
const deep = structuredClone(original);
deep.address.city = "Mumbai";

console.log(original.address.city); // "Delhi" — original safe!
```

**Visual:**
```JS
Shallow:  copy.address ──┐
                          ──► { city: "Delhi" }  (same object)
original.address ─────────┘

Deep:     copy.address ──► { city: "Delhi" }  (new object)
original.address ────► { city: "Delhi" }  (separate object)
```

**Quick rule:** If your object has no nesting, shallow copy is fine. The moment you have **objects/arrays inside objects**, you need a deep copy to avoid mutation bugs.

`structuredClone()` is the modern native way to deep copy in JS.

Instead of `structuredClone()` we have few ways:

**1. JSON trick** (most common, but has limitations)
```js
const deep = JSON.parse(JSON.stringify(original));
```
❌ Loses `undefined`, functions, `Date` objects, `Map`, `Set`


**2. `Lodash` `_.cloneDeep()`** (reliable, handles edge cases)
```js
const _ = require('lodash');
const deep = _.cloneDeep(original);
```
Handles almost everything, but requires a library


**3. Manual recursive function** (full control) (May ask in interview!!!!)
```js
function deepCopy(obj) {
  if (typeof obj !== "object" || obj === null) return obj;
  const copy = {};
  for (let key in obj) {
    copy[key] = deepCopy(obj[key]); // recursively copy nested
  }
  return copy;
}
```

**Which to use?**

| Method                 | Safe? | Handles all types? |
| ---------------------- | ----- | ------------------ |
| `structuredClone()`    | ✅     | mostly yes         |
| `JSON.parse/stringify` | ⚠️    | no                 |
| `_.cloneDeep()`        | ✅     | yes                |
| Manual recursive       | ✅     | depends on you     |

