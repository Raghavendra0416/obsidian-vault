### Backend Files Modified
To connect mongoDB:
- **`src/app.js`**: Added the Mongoose connection logic (`mongoose.connect(...)`) to establish the link between your Node.js server and the MongoDB database.
    
- **`src/routes/v1/todo.route.js`**: Implemented the GET route (`/v1/todos`) to fetch all TODO documents using `Todos.find({})` and added the `console.log` statement for request metadata.
    
- **`src/models/todo.model.js`**: Defined the MongoDB document structure (schema) for your tasks and exported it as a Mongoose model.
    

### Frontend Files Modified

- **Frontend Configuration File**: Updated the backend URL (likely in a file such as `ipConfig.json` or `.env` inside the Frontend folder) to point to your new workspace IP address (`13.235.135.134`) so the frontend could successfully communicate with the backend.