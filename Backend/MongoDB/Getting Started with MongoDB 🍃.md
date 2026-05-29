### 📦 Phase 1 — Core Concepts First
Before touching code, understand what MongoDB _is_:

- **NoSQL vs SQL** — MongoDB stores data as **documents** (JSON-like), not rows/tables
- **Key terms to know:**
    - `Database` → same as SQL database
    - `Collection` → like a SQL table
    - `Document` → like a SQL row (but flexible/schema-less)
    - `Field` → like a SQL column

---
### 🛠️ Phase 2 — Setup
1. Install **MongoDB Community Server** → [mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
2. Install **MongoDB Compass** (GUI to visually explore your data)
3. Or use **MongoDB Atlas** (free cloud database — no local install needed, great for beginners)

---
### 📝 Phase 3 — Learn Basic CRUD Operations

Start with the **Mongo Shell** or Compass to practice raw queries:

```js
// Create
db.users.insertOne({ name: "Alice", age: 25 })

// Read
db.users.find({ age: { $gt: 20 } })

// Update
db.users.updateOne({ name: "Alice" }, { $set: { age: 26 } })

// Delete
db.users.deleteOne({ name: "Alice" })
```

---
### 🔗 Phase 4 — Connect MongoDB to Express.js (Mongoose)
**Mongoose** is the go-to library for using MongoDB with Node/Express:

```bash
npm install mongoose
```

```js
// Basic connection
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/mydb');

// Define a Schema
const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
  email: { type: String, required: true }
});

const User = mongoose.model('User', userSchema);
```

---
### 🗺️ Recommended Learning Order

|Step|Topic|
|---|---|
|1|MongoDB data model (documents, collections)|
|2|CRUD via Compass or Mongo Shell|
|3|Query operators (`$gt`, `$in`, `$and`, etc.)|
|4|Mongoose setup + Schemas + Models|
|5|Build a REST API with Express + Mongoose|
|6|Relationships (embedding vs referencing)|
|7|Indexing & performance basics|


> _Build a simple REST API (e.g. a Todo app or User CRUD) using Express + Mongoose_

---
