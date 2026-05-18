##### Declaration and Initialization

Declaring an Empty Array:
```JavaScript
const emptyArray = [];
```

Declaring and Initializing with Values:
```JavaScript
// An array of strings
const fruits = ["Apple", "Banana", "Cherry"];

// An array of numbers
const scores = [95, 88, 100];
```

- We can create objects inside the arrays in the place of elements.

---

##### 1. Methods for Adding & Removing Elements

|Method & Syntax|Description|Mutates Original?|Returns|
|---|---|---|---|
|`push(item, ...)`|Adds one or more elements to the **end**.|**Yes**|The new length of the array.|
|`pop()`|Removes the **last** element.|**Yes**|The removed element.|
|`unshift(item, ...)`|Adds one or more elements to the **beginning**.|**Yes**|The new length of the array.|
|`shift()`|Removes the **first** element.|**Yes**|The removed element.|
|`concat(arr2, ...)`|Joins two or more arrays together.|No|A new, merged array.|
##### 2. Methods for Iterating & Transforming (Functional Methods)
- These methods take a function (a "callback") to perform an action. They are the cornerstone of modern JavaScript.

|Method & Syntax|Description|Mutates Original?|Returns|
|---|---|---|---|
|`forEach(callback)`|Runs a function for each element.|No|`undefined`.|
|`map(callback)`|Creates a **new array** by calling a function on every element.|No|A new array with the results.|
|`filter(callback)`|Creates a **new array** with all elements that pass a test function.|No|A new array with the filtered elements.|
|`reduce(callback, initial)`|Reduces the array to a single value by calling a function on each element.|No|The final, single value.|
|`flat(depth)`|Creates a **new array** with all sub-array elements concatenated into it.|No|A new, flattened array.|
|`flatMap(callback)`|Same as `map()` followed by `flat()` of depth 1.|No|A new, flattened array.|
##### 3. Methods for Finding Elements

|Method & Syntax|Description|Mutates Original?|Returns|
|---|---|---|---|
|`indexOf(item)`|Finds the **first index** of a specified element.|No|The index number, or `-1` if not found.|
|`includes(item)`|Checks if the array contains a specified element.|No|`true` or `false`.|
|`find(callback)`|Returns the **first element** that passes a test function.|No|The element itself, or `undefined`.|
|`findIndex(callback)`|Returns the **index of the first element** that passes a test function.|No|The index number, or `-1`.|
|`some(callback)`|Checks if **at least one** element passes a test function.|No|`true` or `false`.|
|`every(callback)`|Checks if **all** elements pass a test function.|No|`true` or `false`.|
|`at(index)`|Gets the element at a specific index. Can use negative numbers to count from the end.|No|The element, or `undefined`.|

##### 4. Methods for Slicing & Splicing
This is a critical pair to understand. `slice` is non-destructive, while `splice` is destructive.

|Method & Syntax|Description|Mutates Original?|Returns|
|---|---|---|---|
|`slice(start, end)`|Returns a shallow copy of a portion of the array.|No|A new array with the selected elements.|
|`splice(start, count, ...items)`|**Changes** the array by removing, replacing, or adding elements.|**Yes**|An array of the deleted elements.|

##### 5. Methods for Ordering & Reversing
- The methods ending in `-ed` (e.g., `toSorted`) are the modern, non-mutating versions.

| Method & Syntax         | Description                                                            | Mutates Original? | Returns                              |
| ----------------------- | ---------------------------------------------------------------------- | ----------------- | ------------------------------------ |
| `reverse()`             | Reverses the order of the elements in the array.                       | **Yes**           | The original array, now reversed.    |
| `sort(compareFunc)`     | Sorts the elements of the array.                                       | **Yes**           | The original array, now sorted.      |
| `toReversed()`          | (Modern) Like `reverse()`, but returns a **new** reversed array.       | No                | A new, reversed array.               |
| `toSorted(compareFunc)` | (Modern) Like `sort()`, but returns a **new** sorted array.            | No                | A new, sorted array.                 |
| `toSpliced(...)`        | (Modern) Like `splice()`, but returns a **new** array with the change. | No                | A new array with the splice applied. |

##### 6. Methods for Converting to a String

|Method & Syntax|Description|Mutates Original?|Returns|
|---|---|---|---|
|`join(separator)`|Joins all elements into a single string.|No|A string.|
|`toString()`|Converts the array to a comma-separated string.|No|A string.|

##### 7. Static Methods (Called on `Array` itself)

|Method & Syntax|Description|
|---|---|
|`Array.isArray(obj)`|Checks if the given object is an array. Returns `true` or `false`.|
|`Array.from(iterable)`|Creates a new array from an iterable object (like a string or a Set).|
