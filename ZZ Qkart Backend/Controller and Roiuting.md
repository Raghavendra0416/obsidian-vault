### Database and Server Initialization

- Set up the initial connection to your MongoDB instance using the `mongoose` library.
    
- Configured your Express application to listen for incoming requests on the port specified in your `.env` file.
    

### Express Routing Setup

- Directed all API traffic starting with `/v1/users` to a dedicated User router.
    
- Defined a specific endpoint (`GET /v1/users/:userId`) to capture a dynamic user ID from the URL path.
    

### Controller Implementation

- Created the `getUser` controller function to act as the middleman between the incoming request and your database logic.
    
- Utilized the `catchAsync` wrapper to properly handle any asynchronous errors during the database query.
    
- Programmed the logic to extract the `userId` from the request, fetch the matching document via your service layer, and return either a `200 OK` (with data) or a `404 Not Found` response.
    

### Documentation and Verification

- Learned how to use **JSDoc** tags like `@param` and `@returns` to structure technical comments so that editors like VS Code can parse them for type hinting.
    
- Manually tested the newly created endpoint using the terminal (`curl`) to verify that the router successfully catches requests and triggers the "Not found" logic when given a dummy ID.
    

Are you ready to click the **Mark as Complete** button and dive into the next milestone on API Testing, or do you have any lingering questions about how these files communicate with each other?