### What do you mean by event loop in Node.js?
Ans:
Node.js is single-threaded, meaning it executes one piece of JavaScript at a time. The Event Loop  is a mechanism that helps Node.js handle a large number of concurrent requests efficiently without creating a new thread for every request.

It continuously checks whether the call stack is empty, and if it is, it pushes callbacks from different queues into the stack for execution.

The Event Loop has multiple phases: Timers, Poll, Check, and Close callbacks.

The Poll phase handles most I/O operations, while the Check phase executes `setImmediate()` callbacks.

Before moving to the next Event Loop phase, Node.js processes the microtask queue completely. which have higher priority than normal callback queues.

Async operations like file handling, timers, and network requests are handled by libuv and the operating system. Once these operations are completed, their callbacks are placed into appropriate queues.

This architecture makes Node.js highly scalable and efficient for I/O-intensive applications like APIs, real-time applications, and streaming services.

##### Extra Info:
The Event Loop has multiple phases:
- Timers
- Pending Callbacks
- Idle/Prepare
- Poll
- Check
- Close Callbacks

Event Loop has phases: 
```
   ┌──────────────────────────┐
   │         timers           │  ← setTimeout, setInterval callbacks (after delay expires)
   └──────────┬───────────────┘
              ↓
   ┌──────────────────────────┐
   │     pending callbacks    │  ← I/O errors from previous cycle
   └──────────┬───────────────┘
              ↓
   ┌──────────────────────────┐
   │       idle, prepare      │  ← internal use only
   └──────────┬───────────────┘
              ↓
   ┌──────────────────────────┐
   │          poll            │  ← fetch new I/O events (fs, network) 
   └──────────┬───────────────┘  <- Retrieves new I/O events; blocks here if queue is empty
              ↓
   ┌──────────────────────────┐
   │          check           │  ← setImmediate callbacks
   └──────────┬───────────────┘  <- `setImmediate()` callbacks
              ↓
   ┌──────────────────────────┐
   │     close callbacks      │  ← socket.on('close', ...) etc.
   └──────────────────────────┘  <- Cleanup callbacks like `socket.on('close')`
```

---
### Explain what CORS is in ExpressJS?
Ans:
**CORS (Cross-Origin Resource Sharing)** is a browser security mechanism that controls whether a frontend application from one origin can access resources from another origin.

An **origin** means the combination of:
- Protocol (`http` / `https`)
- Domain
- Port

Example:
- Frontend → `http://localhost:3000`
- Backend → `http://localhost:5000`

These are considered **different origins** because the ports are different.
