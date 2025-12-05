Kadane’s algorithm is for **“Maximum Subarray Sum”** – finding the **largest possible sum of a _contiguous_ subarray**.

##### [Explanation](https://www.youtube.com/watch?v=NUWAXbSlsws)
Time Complexity: O(n)

| Scenario   |                            |                    | Action |
| ---------- | -------------------------- | ------------------ | ------ |
| Scenario 1 | Sub Array sum<br>    (+ve) | Current<br>  (+ve) | Extend |
| Scenario 2 | Sub Array sum<br>    (-ve) | Current<br>  (+ve) | New    |
| Scenario 3 | Sub Array sum<br>    (+ve) | Current<br>  (+ve) | Extend |
| Scenario 4 | Sub Array sum<br>    (-ve) | Current<br>  (+ve) | New    |

I’ll walk you through:
1. What problem Kadane solves
2. Intuition (in plain language)
3. Step-by-step dry run on an array
4. JavaScript implementation (with comments)
5. Edge case: all negative numbers

#### 1. The problem

Given an array of integers (can be positive, negative, zero), find the **maximum sum of any contiguous subarray**.

Example:
```js
[ -2, 1, -3, 4, -1, 2, 1, -5, 4 ]
```

The max sum subarray here is:
```js
[4, -1, 2, 1]   // sum = 6
```
So the answer = **6**.

#### 2. Intuition (Kadane’s idea)

We scan the array from left to right and keep track of:
- `currentSum` → best sum of subarray **ending at the current index**
- `maxSum` → best (maximum) sum we’ve seen so far in the entire array

At each element `num`:
> Either
> - we **extend** the previous subarray: `currentSum + num`
> - or we **start a new subarray** from this element: `num`
> We choose whichever is **bigger**.

So the key formula is:
```js
currentSum = Math.max(num, currentSum + num);
maxSum = Math.max(maxSum, currentSum);
```

##### 3. Step-by-step dry run

Take this array:
```js
const arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
```
Initialize:
- `currentSum = arr[0] = -2`
- `maxSum = arr[0] = -2`

Now go from index 1 to end:
I’ll show as a table:

|i|num|currentSum before|Option 1: num|Option 2: currentSum + num|currentSum after (max of both)|maxSum after|
|---|---|---|---|---|---|---|
|0|-2|—|—|—|`-2` (initial)|`-2`|
|1|1|-2|1|-2 + 1 = -1|**1**|**1**|
|2|-3|1|-3|1 + (-3) = -2|**-2**|1|
|3|4|-2|4|-2 + 4 = 2|**4**|**4**|
|4|-1|4|-1|4 + (-1) = 3|**3**|4|
|5|2|3|2|3 + 2 = 5|**5**|**5**|
|6|1|5|1|5 + 1 = 6|**6**|**6**|
|7|-5|6|-5|6 + (-5) = 1|**1**|6|
|8|4|1|4|1 + 4 = 5|**5**|6|

Final answer: `maxSum = 6`.

Notice:
- Whenever `currentSum + num` becomes worse than just `num`, we **restart** the subarray at `num`.
- `maxSum` always stores the **best value we have ever seen**.

##### 4. JavaScript implementation (step-by-step comments)

##### Version 1: Return max sum (assume array has at least 1 element)

```js
function kadane(arr) {
  if (arr.length === 0) {
    throw new Error("Array must contain at least one element");
  }

  // Step 1: Initialize
  let currentSum = arr[0];  // best sum ending at current index
  let maxSum = arr[0];      // best sum seen so far

  // Step 2: Loop from the 2nd element till the end
  for (let i = 1; i < arr.length; i++) {
    const num = arr[i];

    // Option A: extend previous subarray -> currentSum + num
    // Option B: start new subarray from current element -> num
    currentSum = Math.max(num, currentSum + num);

    // Step 3: update global max if currentSum is better
    maxSum = Math.max(maxSum, currentSum);
  }

  // Step 4: maxSum is our answer
  return maxSum;
}
```

##### Quick test
```js
console.log(kadane([-2, 1, -3, 4, -1, 2, 1, -5, 4])); // 6
console.log(kadane([1, 2, 3]));                       // 6
console.log(kadane([-1, -2, -3]));                    // -1
```

##### 5. Edge case: all negative numbers
Example:
```js
[-5, -2, -7]
```

Here, the maximum subarray is just `[-2]`, answer = `-2`.
Our implementation **already handles this**, because:
- We start `currentSum` and `maxSum` with `arr[0]`.
- We never force them to start from `0`.  
    (If we did `currentSum = Math.max(0, currentSum + num)`, then for all-negative arrays we’d incorrectly get `0`.)

So this version is safe even for all negative numbers.

##### Common practical scenarios:
1. Stock Market – Best Time Window for Profit/Loss Trends
2. Finding High-Traffic Periods on a Website / Server
3. Real-time Sensor Data / Signal Processing
4. Financial Expenditure Analysis
5. Game Development – Streak Detection
6. Image Processing – Brightest Continuous Strip
7. Audio Processing – Loudest Continuous Segment
8. Temperature / Climate – Best Period


---

```JavaScript

function maxSubArray(nums) {
    let maxSoFar = nums[0];      // Best sum we've seen overall
    let maxEndingHere = nums[0]; // Best sum ending at current position
    
    for (let i = 1; i < nums.length; i++) {
        // Key decision: extend current subarray or start new one?
        maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
        
        // Update our global maximum if we found something better
        maxSoFar = Math.max(maxSoFar, maxEndingHere);
    }
    
    return maxSoFar;
}
```

## Visual Example

Let's trace through `[-2, 1, -3, 4, -1, 2, 1, -5, 4]`:
``` JavaScript
Index: 0   1   2   3   4   5   6   7   8
Array: -2  1  -3  4  -1  2   1  -5  4

i=0: maxEndingHere = -2, maxSoFar = -2

i=1: maxEndingHere = max(1, -2+1) = 1
     maxSoFar = 1
     (Starting fresh is better!)

i=2: maxEndingHere = max(-3, 1-3) = -2
     maxSoFar = 1
     (Extending, but result is negative)

i=3: maxEndingHere = max(4, -2+4) = 4
     maxSoFar = 4
     (Starting fresh again!)

i=4: maxEndingHere = max(-1, 4-1) = 3
     maxSoFar = 4
     (Extending: [4, -1])

i=5: maxEndingHere = max(2, 3+2) = 5
     maxSoFar = 5
     (Extending: [4, -1, 2])

i=6: maxEndingHere = max(1, 5+1) = 6
     maxSoFar = 6
     (Extending: [4, -1, 2, 1])

i=7: maxEndingHere = max(-5, 6-5) = 1
     maxSoFar = 6
     (Extending but sum decreases)

i=8: maxEndingHere = max(4, 1+4) = 5
     maxSoFar = 6
     (Extending: still below our max)

Result: 6 (from subarray [4, -1, 2, 1])

```