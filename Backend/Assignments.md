Sure! Here's a fresh assignment that builds directly on what you just completed — this time shifting focus from external API calls to **full CRUD with in-memory storage**, which will also naturally set you up for the MongoDB/Mongoose step coming next in your path.

---

## 📝 Assignment: Student Records Server

### Objective

Build a local **Student Records Management** REST API using **Node.js** and **Express**, following the same MVC folder structure you used in the Exchange Server. Instead of calling an external API, you will manage data using an **in-memory array** (a JavaScript array that acts as your temporary database).

---

### Project Structure

```
session-3-takehome/
├── controllers/
│   └── studentController.js
├── routes/
│   └── students.js
├── data/
│   └── students.js        ← your in-memory "database"
├── package.json
└── server.js
```

---

### The In-Memory Database (`data/students.js`)

Start with this pre-seeded array. All your CRUD operations will read from and write to this:

```js
let students = [
  { id: 1, name: "Arjun Sharma",  age: 21, branch: "CSE" },
  { id: 2, name: "Priya Nair",    age: 22, branch: "ECE" },
  { id: 3, name: "Rohit Mehta",   age: 20, branch: "MECH" },
];

module.exports = students;
```

---

### Endpoints to Build

|Method|Route|Description|
|---|---|---|
|`GET`|`/students`|Return all students|
|`GET`|`/students/:id`|Return a single student by ID|
|`POST`|`/students`|Add a new student|
|`PUT`|`/students/:id`|Update an existing student by ID|
|`DELETE`|`/students/:id`|Delete a student by ID|

---

### Endpoint Specifications

**`GET /students`**

- Returns all students.
- Response `200`: `{ data: [ ...all students ] }`

---

**`GET /students/:id`**

- Finds the student whose `id` matches the route parameter.
- Response `200`: `{ data: { ...student object } }`
- Response `404` if not found: `{ message: "Student not found" }`

---

**`POST /students`**

- Reads `name`, `age`, `branch` from `req.body`.
- Auto-generates a new unique `id` (hint: look at the last element's id and add 1).
- Pushes the new student into the array.
- Response `201`: `{ message: "Student added successfully", data: { ...new student } }`
- Response `400` if any field is missing: `{ message: "Incomplete data provided" }`

---

**`PUT /students/:id`**

- Finds the student by `id`.
- Updates only the fields provided in `req.body` (you don't need to require all three fields — partial update is fine).
- Response `200`: `{ message: "Student updated successfully", data: { ...updated student } }`
- Response `404` if not found: `{ message: "Student not found" }`

---

**`DELETE /students/:id`**

- Finds and removes the student by `id` from the array.
- Response `200`: `{ message: "Student deleted successfully" }`
- Response `404` if not found: `{ message: "Student not found" }`

---

### Validation Rules

- `id` in route params must be parsed as a number (`parseInt`).
- For `POST`: `name` must be a non-empty string, `age` must be a positive number, `branch` must be a non-empty string.
- A missing or unrecognized `id` always returns `404`.

---

### curl Commands to Test Your Work

```bash
# Get all students
curl http://localhost:3000/students

# Get student by ID
curl http://localhost:3000/students/1

# Add a new student
curl -X POST http://localhost:3000/students \
  -H "Content-Type: application/json" \
  -d '{"name":"Sneha Rao","age":23,"branch":"IT"}'

# Update a student
curl -X PUT http://localhost:3000/students/1 \
  -H "Content-Type: application/json" \
  -d '{"age":22}'

# Delete a student
curl -X DELETE http://localhost:3000/students/3
```

---
### Key Concepts This Assignment Practices

|Concept|Where you'll use it|
|---|---|
|Route parameters (`:id`)|GET, PUT, DELETE by ID|
|`req.body` parsing|POST and PUT|
|Array methods (`find`, `findIndex`, `filter`, `push`)|All CRUD operations|
|HTTP status codes (200, 201, 400, 404)|Every endpoint|
|MVC separation|Same as Exchange Server|

> 💡 **Why this matters for MongoDB later:** Right now your "database" is a JS array. When you add Mongoose, you'll simply swap `students.find()` (array method) for `Student.find()` (Mongoose model method). The controller logic and route structure stays almost identical.

---

No external API this time! You create the `data/students.js` file yourself.

It's just a plain JavaScript file that holds an array — think of it as your **fake database** for now. You write the data directly into it:

```js
// data/students.js
let students = [
  { id: 1, name: "Arjun Sharma", age: 21, branch: "CSE" },
  { id: 2, name: "Priya Nair",   age: 22, branch: "ECE" },
  { id: 3, name: "Rohit Mehta",  age: 20, branch: "MECH" },
];

module.exports = students;
```

Then in your controller, you just `require` it:

```js
const students = require('../data/students');
```

And all your CRUD operations directly mutate this array — `push()` to add, `findIndex()` + splice to delete, etc.

---

**The key difference from your Exchange Server assignment:**

|Exchange Server|Student Records Server|
|---|---|
|Data comes from an **external API** (axios call)|Data lives in a **local JS array** (you create it)|
|Read-only — you only fetch|Read + Write — you fetch, add, update, delete|
|`axios.get(url)`|plain array methods (`find`, `push`, etc.)|

> When you move to MongoDB next, this `data/students.js` file gets replaced by a **Mongoose model** — but your controller logic will look almost the same. That's exactly why this step is useful practice.

---
