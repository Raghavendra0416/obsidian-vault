Topics Covered:
- What is Space Complexity? 
- How Space complexity is represented? 
- Steps to Calculate Space Complexity?
- Types of Space Complexity?
- All Examples

---
---
#### What is Space Complexity?
**Space complexity** measures the total amount of memory an algorithm uses as a function of the input size. It includes:

- **Input space**: Memory used to store the input data
- **Auxiliary space**: Extra memory used by the algorithm (variables, data structures, recursion stack)

**Note**: When we talk about space complexity, we usually mean **auxiliary space** (the extra space besides the input).

---
---
#### How Space Complexity is Represented?
Space complexity uses the **same Big O notation** as time complexity:

- **O(1)** - Constant space
- **O(log n)** - Logarithmic space
- **O(n)** - Linear space
- **O(n²)** - Quadratic space
- And so on...

**Format**: "This algorithm has O(n) space complexity" or "Space: O(n)"

---
---
#### Steps to Calculate Space Complexity

Step 1: Identify Variables and Data Structures
Step 2: Express Memory Usage as a Function of Input Size
Step 3: Focus on Auxiliary Space
Step 4: Identify the Dominant Term

#### Step 1: Identify Variables and Data Structures
Count all the extra memory being used:
- Primitive variables (numbers, booleans)
- Arrays, objects, maps, sets
- Recursion call stack depth
- Temporary data structures

#### Step 2: Express Memory Usage as a Function of Input Size
Calculate how much space is used in terms of `n`:
- Fixed variables = O(1)
- Array of size n = O(n)
- 2D array of size n×n = O(n²)
- Recursion depth of n = O(n)

#### Step 3: Focus on Auxiliary Space
Don't count the input itself (unless you're creating a copy). Only count the **extra** space your algorithm uses.

#### Step 4: Identify the Dominant Term
Just like time complexity, keep only the fastest-growing term:
- O(n² + n) → O(n²)
- O(5n) → O(n)
- O(n + 100) → O(n)

---
---
#### Types of Space Complexity

##### 1. **Fixed Space (O(1))**
Memory usage doesn't grow with input size - only uses a constant amount of extra space.

##### 2. **Linear Space (O(n))**
Memory grows proportionally with input size - creates one array, uses recursion depth n, etc.

##### 3. **Quadratic Space (O(n²))**
Memory grows with the square of input size - typically 2D arrays or matrices.

##### 4. **Logarithmic Space (O(log n))**
Memory grows logarithmically - typically recursion stack for divide-and-conquer algorithms.

---
---
#### Examples
##### O(1) - Constant Space
**"Uses fixed amount of extra memory"**

```javascript
// Only uses a few variables
function sum(arr) {
    let total = 0;           // O(1) space
    for (let i = 0; i < arr.length; i++) {  // i is O(1) space
        total += arr[i];
    }
    return total;
}
// Space: O(1) - only 2 variables (total, i)
```

```javascript
// Swapping in place
function swap(arr, i, j) {
    let temp = arr[i];       // O(1) space
    arr[i] = arr[j];
    arr[j] = temp;
}
// Space: O(1) - only one temp variable
```

```javascript
// Finding max
function findMax(arr) {
    let max = arr[0];        // O(1) space
    let index = 0;           // O(1) space
    
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
            index = i;
        }
    }
    return max;
}
// Space: O(1) - only max and index variables
```

```javascript
// In-place array reversal
function reverseInPlace(arr) {
    let left = 0;            // O(1)
    let right = arr.length - 1;  // O(1)
    
    while (left < right) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }
    return arr;
}
// Space: O(1) - only two pointers
```

---
##### O(log n) - Logarithmic Space
**"Recursion depth grows logarithmically"**

```javascript
// Binary search (recursive)
function binarySearch(arr, target, left = 0, right = arr.length - 1) {
    if (left > right) return -1;
    
    let mid = Math.floor((left + right) / 2);
    
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) return binarySearch(arr, target, mid + 1, right);
    return binarySearch(arr, target, left, mid - 1);
}
// Space: O(log n) - recursion stack depth is log n
```

```javascript
// Finding power (recursive)
function power(base, exp) {
    if (exp === 0) return 1;
    
    let half = power(base, Math.floor(exp / 2));
    
    if (exp % 2 === 0) return half * half;
    return half * half * base;
}
// Space: O(log n) - recursion depth is log n
```

---
##### O(n) - Linear Space
**"Creates array or recursion depth equal to input size"**

```javascript
// Creating a new array
function doubleArray(arr) {
    let result = [];         // O(n) space
    for (let i = 0; i < arr.length; i++) {
        result.push(arr[i] * 2);
    }
    return result;
}
// Space: O(n) - result array has n elements
```

```javascript
// Recursive factorial
function factorial(n) {
    if (n === 0) return 1;
    return n * factorial(n - 1);
}
// Space: O(n) - recursion stack has n calls
```

```javascript
// Copying array
function copyArray(arr) {
    let newArr = [...arr];   // O(n) space
    return newArr;
}
// Space: O(n) - new array of size n
```

```javascript
// Using hash map
function findDuplicates(arr) {
    let seen = {};           // O(n) space in worst case
    let duplicates = [];     // O(n) space in worst case
    
    for (let num of arr) {
        if (seen[num]) {
            duplicates.push(num);
        }
        seen[num] = true;
    }
    return duplicates;
}
// Space: O(n) - hash map + duplicates array
```

```javascript
// Fibonacci with memoization
function fibonacci(n, memo = {}) {
    if (n <= 1) return n;
    if (memo[n]) return memo[n];
    
    memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
    return memo[n];
}
// Space: O(n) - memo object stores n values
```

```javascript
// Filter array
function filterEven(arr) {
    let result = [];         // O(n) space
    for (let num of arr) {
        if (num % 2 === 0) {
            result.push(num);
        }
    }
    return result;
}
// Space: O(n) - result can be size n
```

---
##### O(n²) - Quadratic Space
**"Creates 2D array or matrix"**

```javascript
// Creating 2D array
function create2DArray(n) {
    let matrix = [];         // O(n²) space
    for (let i = 0; i < n; i++) {
        matrix[i] = [];
        for (let j = 0; j < n; j++) {
            matrix[i][j] = i * j;
        }
    }
    return matrix;
}
// Space: O(n²) - n×n matrix
```

```javascript
// Storing all pairs
function allPairs(arr) {
    let pairs = [];          // O(n²) space
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            pairs.push([arr[i], arr[j]]);
        }
    }
    return pairs;
}
// Space: O(n²) - storing n² pairs
```

```javascript
// Distance matrix
function distanceMatrix(points) {
    let n = points.length;
    let distances = Array(n).fill(0).map(() => Array(n).fill(0));
    
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            distances[i][j] = calculateDistance(points[i], points[j]);
        }
    }
    return distances;
}
// Space: O(n²) - n×n distance matrix
```

```javascript
// Pascal's Triangle
function pascalTriangle(n) {
    let triangle = [];       // O(n²) space
    
    for (let i = 0; i < n; i++) {
        triangle[i] = Array(i + 1).fill(1);
        for (let j = 1; j < i; j++) {
            triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j];
        }
    }
    return triangle;
}
// Space: O(n²) - storing entire triangle
```

---
##### O(2ⁿ) - Exponential Space
**"Generates all subsets or combinations"**

```javascript
// Generate all subsets
function allSubsets(arr) {
    if (arr.length === 0) return [[]];
    
    let first = arr[0];
    let rest = allSubsets(arr.slice(1));
    let withFirst = rest.map(subset => [first, ...subset]);
    
    return [...rest, ...withFirst];
}
// Space: O(2ⁿ) - stores 2^n subsets
```

```javascript
// Fibonacci without memoization
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}
// Space: O(n) for recursion depth, but the tree has 2^n nodes
// However, at any point, only O(n) stack frames exist
```

---
##### O(n!) - Factorial Space
**"Generates all permutations"**

```javascript
// All permutations
function permutations(arr) {
    if (arr.length === 0) return [[]];
    
    let result = [];
    for (let i = 0; i < arr.length; i++) {
        let rest = [...arr.slice(0, i), ...arr.slice(i + 1)];
        let perms = permutations(rest);
        for (let perm of perms) {
            result.push([arr[i], ...perm]);
        }
    }
    return result;
}
// Space: O(n!) - stores n! permutations
```

---
---
#### Space vs Time Trade-offs

```javascript
// TIME OPTIMIZED: O(n) time, O(n) space
function hasDuplicateWithSet(arr) {
    let seen = new Set();    // O(n) space
    for (let num of arr) {   // O(n) time
        if (seen.has(num)) return true;
        seen.add(num);
    }
    return false;
}

// SPACE OPTIMIZED: O(n²) time, O(1) space
function hasDuplicateNested(arr) {
    for (let i = 0; i < arr.length; i++) {      // O(n²) time
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] === arr[j]) return true;
        }
    }
    return false;
}
```

---
---
#### Quick Comparison Table

| Algorithm                 | Time       | Space    |
| ------------------------- | ---------- | -------- |
| Sum array                 | O(n)       | O(1)     |
| Copy array                | O(n)       | O(n)     |
| Binary search (iterative) | O(log n)   | O(1)     |
| Binary search (recursive) | O(log n)   | O(log n) |
| Merge sort                | O(n log n) | O(n)     |
| Quick sort                | O(n log n) | O(log n) |
| Bubble sort               | O(n²)      | O(1)     |
| Factorial (recursive)     | O(n)       | O(n)     |
| Fibonacci (recursive)     | O(2ⁿ)      | O(n)     |
| Fibonacci (memoized)      | O(n)       | O(n)     |
| All subsets               | O(2ⁿ)      | O(2ⁿ)    |
| All permutations          | O(n!)      | O(n!)    |

---
---
#### Key Takeaways
1. **In-place algorithms**: O(1) space - modify input without extra arrays
2. **Recursive algorithms**: Space = recursion depth
3. **Dynamic programming**: Often trades space for time (memoization)
4. **Arrays/Objects**: Creating new ones = O(n) or more space
5. **Always consider**: Can I solve this in-place to save space?
