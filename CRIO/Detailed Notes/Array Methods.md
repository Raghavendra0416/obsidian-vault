Array methods:

|**Method**|**Description**|**Mutates Original?**|**What it Returns**|
|---|---|---|---|
|**push()**|Adds one or more elements to the **end**.|Yes|The new **length** of the array.|
|**pop()**|Removes the **last** element.|Yes|The **removed element**.|
|**unshift()**|Adds one or more elements to the **beginning**.|Yes|The new **length** of the array.|
|**shift()**|Removes the **first** element.|Yes|The **removed element**.|
|**splice()**|Adds, removes, or replaces elements at a **specific index**.|Yes|An array containing the **deleted elements**.|
|**slice()**|Copies a portion of the array from a start index to an end index.|**No**|A **new array** with the copied items.|
|**concat()**|Merges two or more arrays together.|**No**|A **new array** with the merged items.|
|**fill()**|Overwrites elements with a static value (e.g., make all `0`).|Yes|The **modified array**.|
|**reverse()**|Reverses the order of elements (first becomes last).|Yes|The **modified array**.|
|**at()**|Accesses an item at an index (allows negative numbers like `-1` for the last item).|**No**|The **item** at that index.|
|**flat()**|Flattens nested arrays (e.g., `[[1], 2]` becomes `[1, 2]`) to a specific depth.|**No**|A **new array** with sub-array elements concatenated.|