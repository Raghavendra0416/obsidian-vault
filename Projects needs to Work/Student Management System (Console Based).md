#### Mini Project Question: Student Management System (Console Based)

👉 Build a **JavaScript program** that manages a list of students and their grades.  
Your program must **use all the following concepts**:

##### Requirements
1. **Data Types, Variables**
    - Use `var`, `let`, and `const` in different scenarios.
    - Show the difference in **scope & re-assignment**.
2. **Condition Statements**
    - Based on student marks, assign grades:
        - ≥90 → A
        - 75–89 → B
        - <75 → C  
3. **Loops**
    - Print all student details using different loops (`for`, `for...of`, `while`).
4. **Functions**
    - Create a **function declaration** for adding students.
    - Create a **function expression** for calculating grades.
    - Create an **arrow function** to find the topper student.
5. **Null & Undefined**
    - Handle the case when a student is not found (return `null` or `undefined`).
6. **Callbacks**
    - Write a function `processStudents` that accepts a callback (e.g., filter students by grade).
7. **Strings & String Methods**
    - Store student names as strings and use methods like `toUpperCase()`, `slice()`, `trim()`. 
8. **Template Strings**
    - Print student info using template literals (`` `ID: ${id}, Name: ${name}` ``).
9. **Arrays & Multi-dimensional Arrays**
    - Store students in an **array of objects**.
    - Also, create a **timetable (2D array)** and print subjects.
10. **Array Methods (Basic & Advanced)**
    - Use `push`, `pop`, `map`, `filter`, `reduce`, `find`, `some`, `every`.
11. **Variable Scope & Hoisting**
    - Demonstrate difference between `var`, `let`, `const` inside a block.
    - Show hoisting with `var` and TDZ with `let`.
12. **Objects**
    - Create a `student` object with properties like `id`, `name`, `marks`, `grade`.
13. **Closures**
    - Write a closure function to auto-generate **student IDs**.
14. **Objects vs Arrays**
    - Explain why you are storing students in an **array of objects** instead of just objects.
15. **Destructuring**
    - Use destructuring to extract `name` and `marks` from a student.
16. **Spread & Rest Operators**
    - Use spread (`...`) to copy student arrays.
    - Use rest (`...args`) to calculate average of marks.
17. **Array of Objects**
    - Store at least 5 students as objects inside an array.
18. **Floating Point & Special Numbers**
    - Show the issue with `0.1 + 0.2`.
    - Print examples of `Infinity` and `NaN`.
19. **Math Functions**
    - Generate random roll numbers.
    - Round off GPA values.
20. **Pass by Value & Reference**
    - Show difference when copying numbers vs copying objects.
21. **Shallow & Deep Copy**
    - Create shallow copy of a student using spread.
    - Create deep copy using `JSON.parse(JSON.stringify())`.
22. **ES6 Features**
    - Must use: `let/const`, arrow functions, template literals, destructuring, spread/rest.
23. **Temporal Dead Zone (TDZ)**
    - Write a small example where accessing a `let` variable before declaration throws an error.

---
####  Final Output Example (Console)

```
📋 Student List:
ID: 1 | Name: RAGHAVENDRA | Marks: 88 | Grade: B
ID: 2 | Name: ANU | Marks: 95 | Grade: A
ID: 3 | Name: SAM | Marks: 72 | Grade: C

🏆 Topper: ANU with 95 marks

🎓 Students with Grade B: [ { id: 1, name: 'Raghavendra', marks: 88, grade: 'B' } ]

📊 Average Marks: 85
🎯 Random Roll No: 532
⚠️ TDZ Error: Cannot access 'x' before initialization
```

Your task: **Implement this entire Student Management System** in **one JavaScript file**, making sure every single topic in the list is used at least once.
