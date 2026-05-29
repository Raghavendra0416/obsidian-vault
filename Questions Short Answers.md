### What do you mean by event loop in Node.js?
Ans:
Node.js is single-threaded, so it can execute one piece of code at a time. 
To handle large no.of Concurrent requests efficiently, event loop mechanism is used in node.js without creating a new thread for every request.

Event loop checks weather the call stack is empty, and if it is empty, then it pushes callbacks from different queues into stack, for the execution. 

The Event Loop has multiple phases: Timers, Poll, Check, and Close callbacks.

The Poll phase handles most I/O operations, while the Check phase executes `setImmediate()` callbacks.
Async operations like file handling, timers, and network requests are handled by libuv and the operating system. Once these operations are completed, their callbacks are placed into appropriate queues.

Event Loop processes the microtask queue as high priority than normal callback queues.

---
### Explain the differences between SQL and NoSQL databases?
Ans:
SQL databases are relational databases that store data in tables with a fixed schema and use SQL for querying. 
and SQL provides Vertical Scaling and Strong relationships using joins .

and also best for providing strong consistency and are ideal for structured data and transactions.
Example: Banking systems, E-commerce payments.

NoSQL databases are non-relational databases that store data in flexible formats like documents or key-value pairs/Graphs. 
NoSQL provides Horizontal scaling.

They are highly scalable and suitable for large-scale, unstructured, or rapidly changing data applications. 
Example: Chat applications, Social media platforms.

---
### What is ExpressJS?
Ans:
Express.js is a lightweight web framework built on top of Node.js used for developing web servers, REST APIs and Backend Applications.

It simplifies backend development by providing high level features like routing, middleware, request-response handling, and easy integration with databases.

The middleware architecture it supports helps in implementing functionalities like authentication, validation, logging, and security efficiently.

and Express follows a minimal and unopinionated design, giving developers flexibility to structure applications as needed.

These features improve Development speed, Code organization, Scalability, Maintainability.

---
### What is MongoDB?
Ans:
MongoDB is a **NoSQL document-oriented database** used to store and manage large amounts of data in a flexible JSON-like format called **BSON (Binary JSON)**.

Unlike traditional SQL databases that store data in tables and rows, MongoDB stores data in:
- Collections
- Documents

MongoDb provides features like:
- Document-Oriented Database
- Flexible Schema
- Indexing Support
- Aggregation Framework

It is highly scalable and provides high performance while handling unstructured or semi-structured data.

MongoDB integrates easily with JavaScript-based technologies and supports fast and flexible application development.

---
### Explain the differences between Authentication and Authorization?
Ans:
Authentication is the process of verifying a user's identity, through credentials such as username and password, JWT, or OAuth. It tells us, "Who the user is?"
If the credentials are valid, the user is authenticated.

and Authorization always happens after Authentication.
Authorization is the process of determining what an authenticated user is allowed to access or perform across the platform. It tells us, "What are user is allowed to do?"

Authorization checks the user's role or permissions after users login.
Each role has different permissions.

For example, in a banking application, a user must first log in successfully using authentication, and then the system checks the authentication, whether they have permission to perform specific actions(such as viewing accounts or managing users (authorization).)

---
### What does the `mongoose.aggregate()` function do?
Ans:
`mongoose.aggregate()` is used to perform **data processing and analytics operations** on documents in a MongoDB collection using MongoDB's **Aggregation Pipeline Framework**.

It allows us to filter, group, sort, transform, join, and calculate data through stages such as `$match`, `$group`, `$project`, `$sort`, and `$lookup` .

We commonly use:
- `$match` for filtering - Similar to SQL `WHERE`.
- `$group` for generating reports and totals - Similar to SQL `GROUP BY`.
- `$project` for selecting fields,
- `$sort` for ordering/sorting results, 
- `$lookup` for joining collections - Similar to SQL JOIN.
- and `$skip`/`$limit` for pagination.

It is commonly used for reports, dashboards, analytics, and generating summarized data that cannot be easily achieved using normal `find()` queries.

---
### What are validators? 
Ans:
Validators are rules used to verify that data meets specific requirements before it is processed or stored.
They help maintain data integrity by preventing invalid or incomplete data from entering the system.

Without validation, users could send:
- Incorrect data
- Application errors
- Security issues
- Poor data quality
Validators ensure that only valid data is accepted.

Mongoose provides built-in validators that run before a document is saved. If invalid data is provided, Mongoose throws a validation error.

In Mongoose, validators can be defined in schemas using options such as `required`, `min`, `max`, `minlength`, `maxlength`, `enum`, and `match`.

We can also create custom validators for business-specific rules. 
Validators are commonly used at the client, server, and database levels to ensure data quality and application reliability.

---
### What are services, controllers and routes in express.js and how are they linked?
Ans:
 routes, controllers and services are different layers used to separate responsibilities and keep the code organized and maintainable.

Routes define API endpoints and forward requests to controllers.
The main responsibility of routes are:
- Defining URLs, HTTP methods (like GET, POST, PUT, DELETE)
- Calling the correct controller

Controllers handle HTTP requests and responses, extract request data, and call the appropriate service methods.
They are mainly responsible for:
- Read request data
- Call service methods
- Send response
- Handle HTTP status codes

Services contain the business logic and interact with the database.
They perform:
- Calculations
- Validation rules
- Data processing
- Database interactions

The Flow: Route → Controller → Service → Database → Service → Controller → Response.
This separation improves code organization, maintainability, scalability, and testability in real-world applications.

---
### What is MVC architecture?
Ans:
MVC stands for **Model-View-Controller**, a software architecture pattern that separates an application into three components.

Model:
Model manages data and database operations and also represents the application's data and business rules.

the main responsibility of model is:
- Interact with the database
- Create, Read, Update, Delete (CRUD) operations
- Define data structure/schema
- Validate data

View:
View handles the user interface (UI) for displaying data to the user. 
the main responsibilities are:
- Receive user input
- Display UI
Some Examples of view are: HTML pages, React components, Angular components.

Controller:
Controller processes user requests and coordinates between the Model and View. 
The main responsibility of the controller is to:
- Receive requests
- Process input
- Call Model methods
- Return responses

This separation improves code organization, maintainability, scalability, and testability.

---



