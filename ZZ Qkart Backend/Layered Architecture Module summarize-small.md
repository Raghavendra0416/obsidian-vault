### Architecture Overview

- The QKart backend utilizes a 5-step layered architecture to separate concerns and manage the request-response cycle.
    
- The standard flow for a request is: Router -> Controller -> Service -> Model -> MongoDB.
    

### Server Startup & Configuration

- **Environment Variables:** Resolved startup crashes by defining `MONGODB_URL` in the `.env` file to securely store database credentials.
    
- **Startup Sequence:** Connected to MongoDB using `mongoose.connect()` _before_ initializing the Express server with `app.listen()` inside the `.then()` block to prevent connection race conditions.
    

### Routing Layer

- **Main Router (`index.js`):** Acted as the primary traffic controller, forwarding all requests starting with `/v1/users` to the dedicated `user.route.js` file using `router.use("/users", userRoute);`.
    
- **Feature Router (`user.route.js`):** Defined the specific endpoint for the activity, mapping the HTTP GET request for `/:userId` directly to the `userController.getUser` method.
    

### Controller Layer

- **Extraction:** Captured the dynamic URL parameter using `req.params.userId`.
    
- **Delegation & Validation:** Passed the extracted ID to the Service layer and handled missing data by throwing a `404 Not Found` `ApiError`.
    
- **Delivery:** Sent the final fetched `userData` back to the client using `res.send()`.
    

### Service Layer

- **Data Fetching:** Implemented `getUserById` and `getUserByEmail` functions utilizing Mongoose methods like `User.findById(id)` and `User.findOne({ email })`.
    
- **Business Logic:** Implemented `createUser(userBody)`, introducing logic to first verify if an email was already registered before saving a new user to the database.
    

### Model Layer

- **Schema Definition:** Built the `userSchema` outlining exact data requirements, including custom validations (e.g., a regex check for passwords requiring both letters and numbers, and format validation for emails).
    
- **Static Methods:** Created the custom `isEmailTaken` static method directly on the schema to efficiently check for duplicate registrations.
    
- **Compilation:** Compiled the schema into a Mongoose `User` model and exported it for the Service layer to interact with the MongoDB database.