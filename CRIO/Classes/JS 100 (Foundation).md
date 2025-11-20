##### **Points to remember:**
- Condition based loop is the one that continues repeating till the condition is true.
- Unary operators are unique operators that can perform operations on a single operand(Increment & Decrement Operators).
- In cases where we need to execute the loop for a known number of times + we need to increment/decrement certain values in each iteration, we can use the For Loop.
- Use **for loop** when we know the count it has to repeat. Use **While loop** when we don't know the number of repetitions.
- When we have to repeat a sequence of instructions, a known number of times.
- For loop - When we have to repeat a sequence of instructions, a known number of times AND we have to increment/decrement values after each iteration.
- While Loop - When we need to plainly execute a loop till a condition turns false and you do not know beforehand how many times to execute the loop.

---
##### Math.random() usage:
How does math.random works? and also to print random numbers between the range why do we need to use Math.random() * (max - min)) + min?
Ans: 
The `Math.random()` function in JavaScript returns a **floating-point**, pseudo-random number in the **range from `0` (inclusive) up to but not including `1` (exclusive)** — i.e., `[0, 1)`.

| Expression                                          | Purpose                        |
| --------------------------------------------------- | ------------------------------ |
| `Math.random()`                                     | Random float in `[0, 1)`       |
| `Math.random() * (max - min) + min`                 | Random float in `[min, max)`   |
| `Math.floor(Math.random() * (max - min + 1)) + min` | Random integer in `[min, max]` |

`Math.random()` gives a decimal between `0` and `1`.  
For example: `0.0`, `0.25`, `0.73`, `0.99`, etc.

Math.random() * (max - min)  → scales it to the correct size.
+min     → shifts it to start from min.


----
##### Session 2:

- Console.log is used to display variables, or messages in the console.
- Errors are part of programming.
- Programming errors are also known as the bugs, and the process of finding & removing these bugs is known as debugging.
- The language of 0s and 1s, which is called Binary Language.
- Keywords are reserved words used by the compiler. It tells the compiler that the keyword has a specific meaning and it cannot be used for another purpose. 
- Number, String, and Boolean are datatypes in JavaScript.


---
#### How To Debug Code
**General Debugging Strategy:**
1. Visualize the Problem First
2. Trace Through Manually
3. Add Strategic Debug Logs
4. Question Every Variable





