Compares adjacent elements and swaps them if in wrong order, repeating until array is sorted.
The largest (or smallest) elements "bubble" up to their correct position with each pass.

1. **Iterate:** Start a loop from the beginning of the array.
2. **Compare:** Compare the current element with the next element.
3. **Swap:** If the current element is greater than the next element, swap them.
4. **Repeat:** Continue this process for the entire array. This completes one "pass." The largest element will now be at the end of the array.
5. **Optimize:** Repeat the entire process, but on each new pass, loop one element fewer than the last pass (since the largest elements are already in place).
6. **Finish:** The algorithm is complete when a full pass is made with no swaps.

Basic Implementation:

``` JavaScript
function bubbleSort(arr) {
  let n = arr.length;
  
  // Outer loop for each pass
  for (let i = 0; i < n - 1; i++) {
    
    // Inner loop for comparison and swapping
    // We use n - i - 1 because the last 'i' elements are already sorted
    for (let j = 0; j < n - i - 1; j++) {
      
      // Compare adjacent elements
      if (arr[j] > arr[j + 1]) {
        // Swap them if they are in the wrong order
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  return arr;
}

// Example usage:
let numbers = [5, 3, 8, 1, 2, 9, 4];
console.log("Original:", numbers);
let sortedNumbers = bubbleSort(numbers.slice()); // .slice() to avoid modifying the original
console.log("Sorted:  ", sortedNumbers);
// Output: Sorted:   [1, 2, 3, 4, 5, 8, 9]
```

---
#### Complete Bubble Sort Dry Run
**Initial array:** `[5, 2, 8, 1]`, n = 4
##### Pass 1 (i=0), j goes from 0 to 2:
```
j=0: arr[0]=5, arr[1]=2 → 5>2? YES → swap → [2, 5, 8, 1]
j=1: arr[1]=5, arr[2]=8 → 5>8? NO → no swap → [2, 5, 8, 1]
j=2: arr[2]=8, arr[3]=1 → 8>1? YES → swap → [2, 5, 1, 8]
```
**After Pass 1:** `[2, 5, 1, 8]` ← largest element (8) reached the end

##### Pass 2 (i=1), j goes from 0 to 1:
```
j=0: arr[0]=2, arr[1]=5 → 2>5? NO → no swap → [2, 5, 1, 8]
j=1: arr[1]=5, arr[2]=1 → 5>1? YES → swap → [2, 1, 5, 8]
```
**After Pass 2:** `[2, 1, 5, 8]` ← second largest (5) in position

##### Pass 3 (i=2), j goes from 0 to 0:
```
j=0: arr[0]=2, arr[1]=1 → 2>1? YES → swap → [1, 2, 5, 8]
```
**After Pass 3:** `[1, 2, 5, 8]` ← **Fully sorted!**

---

#### Question & Answers:
##### 1. **Why `j < n-1-i`?**
- Each pass bubbles the largest unsorted element to its final position at the end.
- The `-i` skips the last `i` elements because they're already sorted, reducing unnecessary comparisons.
What would happen if we used `j < n-1` (without the `-i`)?
Ans: 
- We'd be wasting time checking something we already know is sorted.
- **So the `-i` is savings!** Each pass, we reduce our work by 1 comparison because 1 more element has "bubbled" to its correct position.

##### 2. **Where do we use this?** 
Ans: Educational purposes and understanding sorting fundamentals; rarely used in production due to O(n²) time complexity.

##### 3. **How do we know when to use this?** 
Ans: When the problem explicitly asks for bubble sort, or for teaching/demonstrating basic sorting concepts.

##### 4. **Do we need to use the same code (swapping) if any question is asked using bubble sort?** 
Ans: Yes, the core swapping logic (`if arr[j] > arr[j+1] then swap`) remains the same; only minor variations like sort order or optimization flags may differ.

##### Get familiar with:
- When each algorithm shines
- How to recognize which one fits a problem
- The trade-offs between them.