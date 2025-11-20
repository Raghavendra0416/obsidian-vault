**Objects in JavaScript**
- **Definition** – Collections of key–value pairs where keys are strings (or Symbols) and values can be any data type.

- **Declaration** –
    ```js
    const obj = { name: "Alex", age: 25 };
    const obj2 = new Object();
    ```

- **Access Properties** –
    - Dot notation: `obj.name`
    - Bracket notation: `obj["name"]`

- **Add / Modify / Delete** –
    ```js
    obj.city = "London";
    obj.age = 26;
    delete obj.city;
    ```

- **Nested Objects** – Objects can contain other objects/arrays.
- **Methods** – Functions as object properties:
    ```js
    const person = { greet() { console.log("Hi"); } };
    ```

- **Built-in Methods** – `Object.keys()`, `Object.values()`, `Object.entries()`, `Object.assign()`.
- **Use Cases** – Storing structured data, configurations, entities, etc.
- **Special Note** – Objects are reference types; changes affect all references.

**Important Points to Remember While Using Objects in JavaScript**
- **Key Types** – Property keys are strings or `Symbol`s (numbers are converted to strings).
- **Reference Type** – Objects are stored by reference; modifying one reference affects all.
- **Property Access** – Use **dot notation** for known keys, **bracket notation** for dynamic keys.
- **Order of Properties** – Not guaranteed for numeric keys; string keys generally maintain insertion order.
- **Adding/Deleting** – Properties can be added or removed anytime unless the object is frozen (`Object.freeze()`).
- **Iteration** – Use `for...in` for enumerable properties, `Object.keys()`/`Object.entries()` for arrays of keys/entries.
- **Shallow vs Deep Copy** – `Object.assign()` and spread (`{...obj}`) make shallow copies; nested objects need deep cloning.
- **Const with Objects** – `const` prevents reassignment, but properties can still change.
- **Prototype** – All objects inherit from `Object.prototype` unless created with `Object.create(null)`.
- **JSON Conversion** – Use `JSON.stringify()` and `JSON.parse()` for serialization/deserialization.

---
#### Different ways to add Objects:

1. Dot Notation

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

// Add new student
students.student3 = { name: "Charlie", age: 21 };
```

2. Bracket Notation

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

// Add new student
students["student3"] = { name: "Charlie", age: 21 };

// Useful when the key is dynamic
const key = "student4";
students[key] = { name: "Diana", age: 19 };
```

3. Object.assign()

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

// Add new student(s)
Object.assign(students, {
  student3: { name: "Charlie", age: 21 },
  student4: { name: "Diana", age: 19 }
});
```

4. Spread Operator (creates new object)

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

// Creates a new object with the added student
const updatedStudents = {
  ...students,
  student3: { name: "Charlie", age: 21 }
};
```

5. If using an array structure instead:

- Array.push()

```javascript
const students = [
  { id: 1, name: "Alice", age: 20 },
  { id: 2, name: "Bob", age: 22 }
];

students.push({ id: 3, name: "Charlie", age: 21 });
```

- Array spread

```javascript
const students = [
  { id: 1, name: "Alice", age: 20 },
  { id: 2, name: "Bob", age: 22 }
];

const updatedStudents = [...students, { id: 3, name: "Charlie", age: 21 }];
```

6. Using a Class with Methods

```javascript
class StudentRegistry {
  constructor() {
    this.students = {};
  }
  
  addStudent(id, studentData) {
    this.students[id] = studentData;
  }
}

const registry = new StudentRegistry();
registry.addStudent("student1", { name: "Alice", age: 20 });
registry.addStudent("student2", { name: "Bob", age: 22 });
```

Key Considerations:
- **Dot notation**: Simple and readable, but key must be a valid identifier
- **Bracket notation**: More flexible, allows dynamic keys and keys with special characters
- **Object.assign()**: Good for adding multiple properties at once
- **Spread operator**: Creates a new object (immutable approach), useful in React/functional programming
- **Array methods**: Better if you need ordered data or frequent iterations

1. Simple Function with Parameters

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

function addStudent(studentsObj, id, name, age) {
  studentsObj[id] = { name: name, age: age };
  return studentsObj;
}

// Usage
addStudent(students, "student3", "Charlie", 21);
console.log(students);
```

2. Function with Object Parameter

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

function addStudent(studentsObj, studentData) {
  const { id, name, age } = studentData;
  studentsObj[id] = { name, age };
  return studentsObj;
}

// Usage
addStudent(students, { id: "student3", name: "Charlie", age: 21 });
```

3. Function that Returns New Object (Immutable)

```javascript
const students = {
  student1: { name: "Alice", age: 20 },
  student2: { name: "Bob", age: 22 }
};

function addStudent(studentsObj, id, studentData) {
  return {
    ...studentsObj,
    [id]: studentData
  };
}

// Usage - creates new object
const updatedStudents = addStudent(students, "student3", { name: "Charlie", age: 21 });
```

4. Method Added to Object

```javascript
const studentRegistry = {
  students: {
    student1: { name: "Alice", age: 20 },
    student2: { name: "Bob", age: 22 }
  },
  
  addStudent: function(id, name, age) {
    this.students[id] = { name, age };
    return this;
  },
  
  // ES6 method syntax
  addStudentES6(id, name, age) {
    this.students[id] = { name, age };
    return this;
  }
};

// Usage
studentRegistry.addStudent("student3", "Charlie", 21);
```

5. Constructor Function Approach

```javascript
function StudentRegistry() {
  this.students = {};
}

StudentRegistry.prototype.addStudent = function(id, name, age) {
  this.students[id] = { name, age };
  return this;
};

// Usage
const registry = new StudentRegistry();
registry.addStudent("student1", "Alice", 20);
registry.addStudent("student2", "Bob", 22);
```

6. Class-based Approach

```javascript
class StudentManager {
  constructor() {
    this.students = {};
  }
  
  addStudent(id, name, age) {
    this.students[id] = { name, age };
    return this;
  }
  
  // Method with object parameter
  addStudentObj(studentData) {
    const { id, ...data } = studentData;
    this.students[id] = data;
    return this;
  }
  
  // Method to add multiple students
  addMultipleStudents(studentsArray) {
    studentsArray.forEach(student => {
      const { id, ...data } = student;
      this.students[id] = data;
    });
    return this;
  }
}

// Usage
const manager = new StudentManager();
manager.addStudent("student1", "Alice", 20)
       .addStudent("student2", "Bob", 22);

// Or with object
manager.addStudentObj({ id: "student3", name: "Charlie", age: 21 });
```

7. Higher-Order Function

```javascript
function createStudentAdder(studentsObj) {
  return function(id, name, age) {
    studentsObj[id] = { name, age };
    return studentsObj;
  };
}

const students = {};
const addStudent = createStudentAdder(students);

// Usage
addStudent("student1", "Alice", 20);
addStudent("student2", "Bob", 22);
```

8. Function with Validation

```javascript
const students = {};

function addStudent(studentsObj, id, name, age) {
  // Validation
  if (!id || !name || !age) {
    throw new Error("All fields are required");
  }
  
  if (studentsObj[id]) {
    throw new Error("Student ID already exists");
  }
  
  if (typeof age !== 'number' || age < 0) {
    throw new Error("Age must be a positive number");
  }
  
  studentsObj[id] = { name, age };
  return studentsObj;
}

// Usage with error handling
try {
  addStudent(students, "student1", "Alice", 20);
} catch (error) {
  console.error(error.message);
}
```

9. Arrow Function Variations

```javascript
const students = {};

// Simple arrow function
const addStudent = (studentsObj, id, name, age) => {
  studentsObj[id] = { name, age };
  return studentsObj;
};

// Arrow function returning new object
const addStudentImmutable = (studentsObj, id, studentData) => ({
  ...studentsObj,
  [id]: studentData
});

// Usage
addStudent(students, "student1", "Alice", 20);
const newStudents = addStudentImmutable(students, "student2", { name: "Bob", age: 22 });
```

Each approach has its benefits:

- **Simple functions**: Easy to understand and use
- **Object methods**: Keep related functionality together
- **Classes**: More structured, good for complex applications
- **Immutable functions**: Safer for functional programming patterns
- **Validation functions**: Ensure data integrity


