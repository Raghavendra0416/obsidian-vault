### **Refined thinking example:**

> "Let me scan the list once. For every new word, I’ll count its total occurrences and remember them. I’ll skip words I’ve already processed. That way, I don’t repeat my work, and I don’t need to remove anything from the list."


| Weak Thinking                          | Improved Thinking                            |
| -------------------------------------- | -------------------------------------------- |
| Remove items and repeat work           | Process once, group, then filter or output   |
| Focus on priority too early            | First group similar items, then analyze them |
| Avoid complex structures if restricted | Simulate them using basic lists or logic     |
| Modify original data                   | Use markers or flags instead of deletion     |
| Jump into code without planning        | Pause, define the exact goal, then start     |
| Code blindly                           | Visualize how data flows through your logic  |
| Works = good                           | Think about time/space efficiency too        |

---


Here’s a **printable checklist and flowchart-style guide** to keep your thinking sharp while solving coding problems — especially useful for practice, interviews, or real-world scenarios.

---

## **Coding Problem-Solving Checklist (Mindset Guide)**

### **Step 1: Understand the Problem**

-  What is the **goal**? (e.g., find duplicates, count, filter, transform)
    
-  What **constraints** are given? (e.g., no HashMap, no sorting, memory limit)
    
-  What is the **expected output** format?
    
-  What kind of **data** are you working with? (Strings? Numbers? Lists?)
    

---

### **Step 2: Plan Before You Code**

-  Can I **visualize how data flows**? (Sketch sample input/output)
    
-  What **data structure** suits the problem? (If restricted, can I simulate it?)
    
-  Can I do this in **one pass**, or do I need multiple?
    
-  Do I need to **modify the input**, or can I just **flag/track** items?
    

---

### **Step 3: Choose the Right Strategy**

-  Should I **group** items first, then analyze? (Often better than filtering step-by-step)
    
-  Am I **avoiding repeated work**? (O(n) better than O(n²))
    
-  Can I track needed info using **parallel lists or indexes**?
    
-  Am I checking or modifying elements safely during iteration?
    

---

### **Step 4: Write Code Carefully**

-  Use clear variable names (`checkedItems`, `duplicates`, `counts`)
    
-  Avoid modifying lists in loops — use a new list or mark processed items
    
-  Test your logic with different inputs:
    
    - No duplicates
        
    - All duplicates
        
    - Mixed order
        
    - Case sensitivity
        

---

### **Step 5: Review Your Work**

-  Is the time complexity acceptable? (O(n), O(n log n), etc.)
    
-  Is the space complexity optimized?
    
-  Is the code clean, readable, and easy to debug?
    
-  Is there any unnecessary loop or logic?
    

---

## **Flowchart for Problem-Solving Thinking**

```
START
  |
  v
Read & Understand the Problem
  |
  v
Any Constraints?
  |-- Yes --> Simulate restricted tools (lists, flags, manual compare)
  |
  v
Is Grouping or Counting Needed?
  |-- Yes --> Track using 2 lists: values + counts
  |
  v
Can I Do It In One Pass?
  |-- Yes --> Go for it!
  |-- No  --> Keep passes minimal, avoid rechecking same data
  |
  v
Avoid:
- Removing in loop
- Repeating same comparisons
- Writing without plan
  |
  v
Write & Test with varied inputs
  |
  v
Analyze Complexity (Time + Space)
  |
  v
CLEAN CODE DONE
```

---

Understanding a coding question, breaking it down, and turning it into a solution is a skill you can practice and improve. Here’s a **step-by-step guide** to build that habit.


## **How to Understand a Coding Problem and Break It into Parts**


### **STEP 1: Read the Problem Slowly**

Ask yourself:

- **What is being asked?**
    
    - Output: Is it a value? A list? A count?
        
- **What are the inputs?**
    
    - Single input or multiple? String? Integer? List?
        
- **Are there constraints or restrictions?**
    
    - “Without using HashMap”, “Should be O(n)”, “Sorted output required”?
        

**Example:**  
_"Find the duplicates in a list of strings without using HashMap, HashSet, or contains()."_

---

### **STEP 2: Rephrase the Problem in Your Own Words**

If you can say it simply, you’ve understood it.

**Example:**  
"I need to find which words appear more than once, count how many times, and avoid using built-in tools that would make it easier."

---

### **STEP 3: Identify Core Tasks/Sub-Problems**

Break it down into manageable parts. Think like this:

1. **How will I go through the data?**
    
2. **How do I compare or group items?**
    
3. **How do I track what I’ve already checked?**
    
4. **What do I output, and when?**
    

**For duplicate count:**

- Scan each item
    
- For each item, compare with rest
    
- Track items already checked
    
- If count > 1, store it
    
- Print stored duplicates with their count
    

---

### **STEP 4: Think of Edge Cases Early**

Ask:

- What if the list is empty?
    
- What if all elements are unique?
    
- What if all elements are the same?
    
- Is it case-sensitive?
    

This helps you:

- Write robust logic
    
- Avoid hidden bugs
    

---

### **STEP 5: Choose Tools/Data Structures (based on constraints)**

Now ask:

- Can I use a `Map` or should I simulate it?
    
- Do I need 1 list or 2 lists?
    
- Do I need flags/booleans?
    

Use only what the question allows.

---

### **STEP 6: Sketch the Algorithm (like pseudocode or bullet steps)**

**Example for duplicates:**

- Create empty list `checked`
    
- Create list `duplicates` and `counts`
    
- For every item in list:
    
    - If not in `checked`:
        
        - Count how many times it appears in the list
            
        - If count > 1:
            
            - Add to duplicates and add count
                
        - Add item to `checked`
            

---

### **STEP 7: Write Small and Test Often**

Write in small blocks:

- First: just count one word
    
- Then: try counting all
    
- Finally: add printing logic
    

Use test cases like:

- `["a", "b", "a"]`
    
- `["x"]`
    
- `["apple", "apple", "banana", "banana", "apple"]`
    

---

### **STEP 8: Review Your Solution**

After it works:

- Can I make it cleaner?
    
- Can I reduce the number of loops?
    
- Can I explain this to someone in 30 seconds?
    

---

## **Quick Template You Can Use for Any Problem**

```
1. What is the input?
2. What is the expected output?
3. Any constraints?
4. Can I restate the goal in simple words?
5. What smaller steps make up the solution?
6. What data structures do I need?
7. Any edge cases?
8. Can I do it in one pass?
9. Can I test it with simple inputs?
10. Is my code clean and efficient?
```

---



## **Problem Statement:**

> Given a list of integers, return a list of all numbers that appear more than once, in the order they appear in the original list.
> 
> **Do not use HashMap, HashSet, or contains()**.

---

### Now let’s walk through this using the **10-step template**:

---

### **1. What is the input?**

A list of integers, e.g.  
`[4, 3, 2, 7, 8, 2, 3, 1]`

---

### **2. What is the expected output?**

A list of integers that are duplicates.  
In the above input, `2` and `3` appear twice.  
**Output:** `[2, 3]`

---

### **3. Any constraints?**

- Don’t use HashMap, HashSet, or `contains()`.
    
- Maintain order of first appearance.
    

---

### **4. Can I restate the goal in simple words?**

Yes:

> "Find all numbers that occur more than once and return them, keeping their first appearance order."

---

### **5. What smaller steps make up the solution?**

1. Loop through each number in the list.
    
2. For each number:
    
    - Check if we've already checked it (manually, using a loop).
        
    - Count how many times it appears in the rest of the list.
        
    - If count is more than 1, store it in a result list.
        
3. Return the result list at the end.
    

---

### **6. What data structures do I need?**

- An `ArrayList<Integer>` to store the output (duplicates).
    
- An `ArrayList<Integer>` to keep track of already checked numbers.
    
- Manual looping to replace `contains()`.
    

---

### **7. Any edge cases?**

- Empty list → return empty list.
    
- No duplicates → return empty list.
    
- All numbers are duplicates → return all once.
    

---

### **8. Can I do it in one pass?**

No — since we can't use `HashMap`, we’ll need **nested loops**:

- Outer loop to go through each number
    
- Inner loop to count frequency
    

Still, we can make sure each number is only processed once.

---

### **9. Can I test it with simple inputs?**

Test cases:

- `[1, 2, 2, 3, 4]` → `[2]`
    
- `[1, 1, 1, 1]` → `[1]`
    
- `[]` → `[]`
    
- `[1, 2, 3]` → `[]`
    

---

### **10. Is my code clean and efficient?**

We'll check after writing it.  
Let’s go ahead and write the code together now?

