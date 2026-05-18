### **Common Request Aliases**
- **axios.get()** – Retrieve data from a server.
- **axios.post()** – Send new data to a server.
- **axios.put()** – Update an existing resource entirely.
- **axios.patch()** – Update specific parts of a resource.
- **axios.delete()** – Remove a resource from the server.
- **axios.head()** – Retrieve response headers only (no body).
- **axios.options()** – Check permitted communication options.

### **Instance and Configuration Methods**
- **axios.create()** – Create a new instance with custom configurations.
- **axios.request()** – The base method for making any type of request via a config object.
- **axios.all()** – Handle multiple concurrent requests (used with `axios.spread`).
- **axios.getUri()** – Generate a URI based on the provided configuration.

### **Interceptors and Defaults**
- **axios.interceptors.request** – Run code before a request is sent.
- **axios.interceptors.response** – Run code after a response is received but before `.then()` or `.catch()`.
- **axios.defaults** – Global configuration settings applied to every request.

---
**Short Answer:**
Axios provides specific alias methods for all major HTTP verbs, including **GET, POST, PUT, PATCH, DELETE, HEAD,** and **OPTIONS**. Additionally, it features utility methods like **axios.create()** for custom instances, **axios.request()** for manual configuration, and **interceptors** for handling global request/response logic.

**Summary:**
Axios simplifies HTTP communication by offering shorthand methods for standard requests, tools for managing concurrent calls, and interceptors to streamline global data handling and error management.