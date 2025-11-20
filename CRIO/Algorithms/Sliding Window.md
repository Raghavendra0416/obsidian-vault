**When to Use Sliding Window?**
Look for these clues in a problem:
- "Consecutive elements" or "subarray"
- "Maximum/minimum of size K"
- "Longest/shortest substring with..."


**Main Process:**
1. **Expand window (move right pointer):**
    - Add character at `right` to the map
    - Increment its count
2. **Check if window is valid:**
    - Count distinct characters: `charMap.size`
    - Is `charMap.size <= k`?
3. **If invalid (too many distinct chars):**
    - **Shrink from left** until valid again
    - Remove character at `left` from map (decrement count)
    - If count becomes 0, delete that character from map
    - Move `left` pointer forward
4. **Track maximum:**
    - Current window length = `right - left + 1`
    - Update `maxLength` if current is larger
5. **Move right pointer forward and repeat**


**Understanding:**
**What Sliding Window means:**  
Used when we need to find something (like sum, average, count) in _subarrays of fixed size k_.

**How it works:**
1. Compute the **first window sum** (sum of first k elements).
2. Then **slide the window** by 1 element at a time.
3. For each slide, instead of recalculating the whole sum:
    ```js
    windowSum = windowSum - arr[i - k] + arr[i];
    ```
    - Remove the element that goes out of the window (`arr[i - k]`).
    - Add the new element coming into the window (`arr[i]`).
4. Track the **maximum sum** seen so far.
5. Return that max sum at the end.
**Example:**

```js
function maxSum(arr, k) {
  let windowSum = 0;
  let maxSum = 0;

  // Step 1: first window sum
  for (let i = 0; i < k; i++) windowSum += arr[i];
  maxSum = windowSum;

  // Step 2: slide the window
  for (let i = k; i < arr.length; i++) {
    windowSum = windowSum - arr[i - k] + arr[i];
    maxSum = Math.max(maxSum, windowSum);
  }

  return maxSum;
}
```

**Time complexity:** O(n) — because each element is added and subtracted once.  
**Space complexity:** O(1)

**Question:**
do we use the same formula for every sliding window technique: 
windowSum = windowSum - arr[i - k] + arr[i];  ?

**Answer:**
Not always — that formula (`windowSum = windowSum - arr[i - k] + arr[i]`) is used **only for fixed-size sliding window problems**.

When it works
- When the window size is **constant (k)**.
- Example: finding the _maximum or average sum_ of `k` consecutive elements.
- You slide the window by one element at a time, removing the leftmost and adding the new rightmost element.

When it doesn’t work
- When the window size is **variable**, meaning it changes depending on a condition.
    - Example: “Find the longest subarray with sum ≤ K” or “Smallest substring containing all characters”.
    - In these, you use **two pointers** (`start`, `end`) and adjust them dynamically based on the condition.

Summary
- **Fixed-size window →** use the formula.
- **Variable-size window →** use two-pointer logic (expand and shrink conditionally).