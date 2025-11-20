Topics Covered:
- What is Time Complexity?
- How Time complexity is represented?
- Steps to Calculate Time Complexity
- Types of Time Complexity
- All Examples

---
#### **What is Time Complexity?**
Time complexity measures how the runtime of an algorithm grows as the input size increases. It helps us analyze algorithm efficiency and compare different approaches without running actual code. We focus on the worst-case scenario and look at growth rates rather than exact execution times.

---
#### **How Time complexity is represented?**
**Big O Notation**
Big O notation describes the upper bound of time complexity, showing the maximum time an algorithm could take. It ignores constants and lower-order terms, focusing on dominant factors.

---
#### **Steps to Calculate Time Complexity:**
Step 1: Identify the Input Size (n)
Step 2: Count the Operations as a Function of Input Size
Step 3: Focus on the Fastest-Growing Term
Step 4: Drop Constants and Coefficients

##### Step 1: Identify the Input Size (n)
**What it means**: Determine what variable represents the "size" of your input. This is what will grow and affect your algorithm's performance.

**Common inputs**:
- For arrays/lists: `n` is the number of elements
- For strings: `n` is the length of the string
- For numbers: `n` is the value of the number itself
- For matrices: `n` might be rows, `m` might be columns
- For graphs: `n` is vertices, `m` is edges
- For multiple inputs: use different variables (n and m) to represent different input sizes

**Key point**: You're asking "as THIS grows larger, how does my algorithm's runtime change?"

##### Step 2: Count the Operations as a Function of Input Size
**What it means**: Express the total number of operations your algorithm performs in terms of `n`.

**How to count**:
- **Simple statements**: Each assignment, comparison, or arithmetic operation counts as 1
- **Loops**: If a loop runs `n` times and has `k` operations inside, that's `n × k` operations
- **Nested loops**: Multiply the iterations together. If outer loop runs `n` times and inner loop runs `m` times, that's `n × m` operations
- **Consecutive blocks**: Add them together. First loop is `n` operations, second loop is `n²` operations = total is `n + n²`
- **Conditionals**: Take the worst case (the branch that does the most work)
- **Function calls**: Add the time complexity of the called function

**Result**: You get an expression like `3n² + 5n + 10` or `n log n + n` that represents total operations.

##### Step 3: Focus on the Fastest-Growing Term
**What it means**: When `n` gets very large, only the term that grows the fastest actually matters to the runtime.

**Why**: As `n` approaches infinity, the largest term dominates everything else.

**How to identify the dominant term**:
- Look at your expression from Step 2 (e.g., `n² + 100n + 500`)
- Identify which term grows fastest as `n` increases
- Growth rate ranking (slowest to fastest): 1 < log n < n < n log n < n² < n³ < 2ⁿ < n!

**Example comparison**:
- When `n = 10`: `n² = 100`, `n = 10` (n² is 10× larger)
- When `n = 100`: `n² = 10,000`, `n = 100` (n² is 100× larger)
- When `n = 1000`: `n² = 1,000,000`, `n = 1000` (n² is 1000× larger)
The gap keeps growing, so `n²` dominates and we ignore the `n` term.

##### Step 4: Drop Constants and Coefficients
**What it means**: Remove all constant multipliers and standalone constants from your dominant term.

**Why constants don't matter**:
- Big O describes growth rate, not exact runtime
- Constants depend on hardware, language, implementation details
- As `n` grows, the shape of the curve (linear, quadratic, etc.) matters more than the multiplier
- We care about how the algorithm scales, not precise milliseconds

**What to drop**:
- **Coefficients**: `5n²` becomes `n²`, `100n` becomes `n`
- **Standalone constants**: `n + 500` becomes `n`, `n² + 20` becomes `n²`
- **Constant factors in multiplications**: `2n log n` becomes `n log n`

**What to keep**:
- The variable(s): `n`, `m`, etc.
- The relationship: squared, cubed, logarithmic, etc.
- Multiple variables if they're different inputs: `O(n + m)` or `O(n × m)`

**Final form**: Your answer should be expressed as `O(...)` with the simplest form of the dominant term inside.

##### Putting It All Together
**Starting expression**: `3n² + 100n + 50`
1. **Identify input size**: `n` is the array length
2. **Count operations**: Got `3n² + 100n + 50` total operations
3. **Fastest-growing term**: `n²` grows faster than `n` or constant
4. **Drop constants**: Remove `3`, `100`, and `50`

**Final answer**: `O(n²)`

#### Additional Important Concepts
**Best, Average, Worst Case**: Time complexity can differ based on input. Big O typically represents worst-case unless specified otherwise.

**Amortized Complexity**: Sometimes an operation is usually fast but occasionally slow. Amortized analysis averages the cost over many operations.

**Space vs Time**: These same principles apply to analyzing memory usage (space complexity) as well as runtime (time complexity).

---
#### **Types of Time Complexity:**
**Common Time Complexities (from fastest to slowest):**

**O(1) - Constant Time**: The algorithm takes the same time regardless of input size. Examples include accessing an array element by index, inserting at the beginning of a linked list, or hash table lookups.

**O(log n) - Logarithmic Time**: Time grows logarithmically as input increases. Common in algorithms that divide the problem in half each iteration, like binary search or balanced tree operations.

**O(n) - Linear Time**: Time grows proportionally with input size. Examples include iterating through an array, linear search, or finding the maximum element in an unsorted list.

**O(n log n) - Linearithmic Time**: Common in efficient sorting algorithms like merge sort, heap sort, and quick sort (average case). It's the best time complexity achievable for comparison-based sorting.

**O(n²) - Quadratic Time**: Time grows with the square of input size. Typical in nested loops where each element is compared with every other element, like bubble sort, selection sort, or insertion sort.

**O(n³) - Cubic Time**: Common in algorithms with three nested loops, such as certain matrix multiplication algorithms.

**O(2ⁿ) - Exponential Time**: Time doubles with each additional input element. Found in recursive algorithms that solve subproblems multiple times, like naive Fibonacci calculation or generating all subsets.

**O(n!) - Factorial Time**: Extremely slow growth, appearing in algorithms that generate all permutations or solve the traveling salesman problem using brute force.

**Analysis Tips:**
Drop constants (O(3n) becomes O(n)), drop non-dominant terms (O(n² + n) becomes O(n²)), and analyze loops carefully. Nested loops typically multiply complexities, while sequential operations add them. Recursive algorithms often require the Master Theorem or recursion trees for analysis.


---

#### **Examples:**

##### O(1) - Constant Time
**"Always takes the same time, no matter the input size"**

```javascript
// Accessing array element
function getFirst(arr) {
    return arr[0];
}

// Getting object property
function getName(obj) {
    return obj.name;
}

// Simple math
function add(a, b) {
    return a + b;
}

// Checking array length
function getLength(arr) {
    return arr.length;
}
```


##### O(log n) - Logarithmic Time
**"Cuts the problem in half each time"**

```javascript
// Binary search
function binarySearch(arr, target) {
    let left = 0, right = arr.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        if (arr[mid] === target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

// Dividing by 2 repeatedly
function findPowerOfTwo(n) {
    let count = 0;
    while (n > 1) {
        n = n / 2;
        count++;
    }
    return count;
}

// Counting digits
function countDigits(n) {
    let count = 0;
    while (n > 0) {
        n = Math.floor(n / 10);
        count++;
    }
    return count;
}
```


##### O(n) - Linear Time
**"Goes through each element once"**

```javascript
// Simple loop
function printAll(arr) {
    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
}

// Finding max
function findMax(arr) {
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}

// Sum of array
function sum(arr) {
    let total = 0;
    for (let num of arr) {
        total += num;
    }
    return total;
}

// Linear search
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) return i;
    }
    return -1;
}

// Two separate loops (still O(n))
function printTwice(arr) {
    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
}
// O(n) + O(n) = O(2n) = O(n)
```

---

##### O(n log n) - Linearithmic Time
**"Efficient sorting algorithms"**

```javascript
// Merge Sort
function mergeSort(arr) {
    if (arr.length <= 1) return arr;
    
    const mid = Math.floor(arr.length / 2);
    const left = mergeSort(arr.slice(0, mid));
    const right = mergeSort(arr.slice(mid));
    
    return merge(left, right);
}

function merge(left, right) {
    let result = [], i = 0, j = 0;
    
    while (i < left.length && j < right.length) {
        if (left[i] < right[j]) result.push(left[i++]);
        else result.push(right[j++]);
    }
    
    return result.concat(left.slice(i)).concat(right.slice(j));
}

// Quick Sort (average case)
function quickSort(arr) {
    if (arr.length <= 1) return arr;
    
    const pivot = arr[arr.length - 1];
    const left = arr.filter((x, i) => x <= pivot && i < arr.length - 1);
    const right = arr.filter(x => x > pivot);
    
    return [...quickSort(left), pivot, ...quickSort(right)];
}

// Using built-in sort
function sortArray(arr) {
    return arr.sort((a, b) => a - b);
}
```


##### O(n²) - Quadratic Time
**"Nested loop - each element with every other element"**

```javascript
// Two nested loops
function printPairs(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            console.log(arr[i], arr[j]);
        }
    }
}

// Bubble Sort
function bubbleSort(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
            }
        }
    }
    return arr;
}

// Selection Sort
function selectionSort(arr) {
    for (let i = 0; i < arr.length; i++) {
        let minIdx = i;
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        [arr[i], arr[minIdx]] = [arr[minIdx], arr[i]];
    }
    return arr;
}

// Finding duplicates
function hasDuplicate(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] === arr[j]) return true;
        }
    }
    return false;
}
```


##### O(n³) - Cubic Time
**"Three nested loops"**

```javascript
// Three nested loops
function printTriplets(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            for (let k = 0; k < arr.length; k++) {
                console.log(arr[i], arr[j], arr[k]);
            }
        }
    }
}

// Finding triplets that sum to zero
function findTriplets(arr) {
    const triplets = [];
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            for (let k = j + 1; k < arr.length; k++) {
                if (arr[i] + arr[j] + arr[k] === 0) {
                    triplets.push([arr[i], arr[j], arr[k]]);
                }
            }
        }
    }
    return triplets;
}
```


##### O(2ⁿ) - Exponential Time
**"Each element doubles the work"**

```javascript
// Fibonacci (naive recursive)
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Generating all subsets
function subsets(arr) {
    if (arr.length === 0) return [[]];
    
    const first = arr[0];
    const rest = arr.slice(1);
    const subsetsWithoutFirst = subsets(rest);
    const subsetsWithFirst = subsetsWithoutFirst.map(sub => [first, ...sub]);
    
    return [...subsetsWithoutFirst, ...subsetsWithFirst];
}

// Tower of Hanoi
function hanoi(n) {
    if (n === 1) return 1;
    return 2 * hanoi(n - 1) + 1;
}
```

##### O(n!) - Factorial Time
**"Generating all permutations"**

```javascript
// All permutations
function permutations(arr) {
    if (arr.length === 0) return [[]];
    
    const result = [];
    for (let i = 0; i < arr.length; i++) {
        const rest = [...arr.slice(0, i), ...arr.slice(i + 1)];
        const perms = permutations(rest);
        for (let perm of perms) {
            result.push([arr[i], ...perm]);
        }
    }
    return result;
}

// Traveling salesman (brute force)
function tsp(cities) {
    const allRoutes = permutations(cities);
    let minDistance = Infinity;
    
    for (let route of allRoutes) {
        const distance = calculateDistance(route);
        if (distance < minDistance) minDistance = distance;
    }
    return minDistance;
}
```


#### Quick Reference Chart

|Notation|Name|Example|
|---|---|---|
|O(1)|Constant|Array access, hash lookup|
|O(log n)|Logarithmic|Binary search|
|O(n)|Linear|Simple loop, linear search|
|O(n log n)|Linearithmic|Merge sort, quick sort|
|O(n²)|Quadratic|Nested loops, bubble sort|
|O(n³)|Cubic|Triple nested loops|
|O(2ⁿ)|Exponential|Recursive fibonacci|
|O(n!)|Factorial|Permutations|

**Growth comparison** (for n = 10):
- O(1) = 1
- O(log n) ≈ 3
- O(n) = 10
- O(n log n) ≈ 30
- O(n²) = 100
- O(2ⁿ) = 1,024
- O(n!) = 3,628,800




