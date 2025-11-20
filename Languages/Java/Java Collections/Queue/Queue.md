Definition:
A **queue** is a linear data structure that follows the First-In-First-Out (FIFO) principle, meaning the first element added to the queue will be the first one to be removed. Elements are added at the rear (tail) and removed from the front (head), much like people standing in a line.

![[Pasted image 20250616225849.png]]

Creation of Queue:
	Queue<(type)> queue = new Type of Queue<>(); 
			or
	 Type of Queue<(type)> queue = new Type of Queue<>(); 

Types of Queue based on implementation of interface:
1. Priority Queue(Pure Queue)
2. Array DeQueue(implements Queue & Dequeue)
3. LinkedList(implements Queue & Dequeue & List)

##### Basic operations:
- Addition - add, offer(add & offer works same)
- Retravel - peek (Peek always returns only the highest priority element from the list)
- Removal - poll, remove (if the list is null poll will return null and remove will throw exception)

##### Notes for Priority Queue(as priority queue is pure queue):
- Priority Queue creates an array/ list with 11 size.
- Priority Queue adds elements randomly but it adds top priority value at 1st(priority is decided from lowest to highest).
- While loop should be used to get priority elements from Queue. If for loop is used it won't provide elements based on priority.

##### Notes:
- **No Random Access**: You **cannot access elements by index** like in a List. Only head (front) and tail (rear) operations are supported.
- The initial capacity of priority Queue is 11
-  insertion happens from tail of the list in queue
-  remove will happen from the head(one way(only delete elements from head))
- Most queues (like `PriorityQueue`, `ArrayDeque`, `BlockingQueue`) **do not allow null**.
- `LinkedList` **does allow null**, but it's discouraged.
- **Use `offer()` instead of `add()`** in capacity-restricted queues — `offer()` returns false if it fails, while `add()` throws an exception.
- **Types:** Includes `ArrayBlockingQueue`, `LinkedBlockingQueue`, `PriorityBlockingQueue`, `DelayQueue`, `SynchronousQueue`.

---
##### Very Important Points to Remember While Using Queue:

- **FIFO Principle:** Queues operate on a First-In-First-Out basis—elements are added at the rear and removed from the front
- **Core Operations:** Common queue operations include `enqueue` (add), `dequeue` (remove), `peek` (view front), `isEmpty`, and `size`.
- **Null Element Restrictions:** Some queue implementations (e.g., `ArrayDeque`, `PriorityQueue`) do not allow null elements, while others like `LinkedList` do.
- **Exception Handling:** Methods like `remove()` and `element()` throw exceptions if the queue is empty, while `poll()` and `peek()` return `null` instead.
- **Thread Safety:** Standard queue implementations (`LinkedList`, `ArrayDeque`, `PriorityQueue`) are not thread-safe. Use concurrent queues (e.g., `BlockingQueue`, `ConcurrentLinkedQueue`) for multi-threaded scenarios
- **Blocking vs Non-blocking:** Blocking queues (like `ArrayBlockingQueue`, `LinkedBlockingQueue`) support operations that wait for the queue to become non-empty/full, which is crucial for producer-consumer patterns
- **Capacity Constraints:** Some queues are bounded (fixed capacity, e.g., `ArrayBlockingQueue`), while others are unbounded (grow as needed, e.g., `LinkedList`)
- **Performance:** Choose the right implementation based on performance needs—e.g., `ArrayDeque` and `LinkedList` provide O(1) insertion/removal at both ends
- **Custom Implementations:** When implementing your own queue, manage capacity, resizing, and edge cases (like underflow/overflow) carefully 
- **Use Correct Methods:** Prefer `offer()` and `poll()` for queue operations to avoid exceptions and handle edge cases gracefully   
- **Iterator Support:** Most Java queues support iteration, but the order and behavior may vary depending on implementation  
- **Queue Interface:** Always program to the `Queue` interface, not the implementation, to allow flexibility in changing the underlying queue type
- **Resource Management:** Always clear or properly manage queues to avoid memory leaks, especially in long-running applications

---
##### Comparison of Queue Types

| Queue Type    | Implementation          | Ordering / Structure                  | Null Elements | Thread Safety   | Performance             | Typical Use Case                      |
| ------------- | ----------------------- | ------------------------------------- | ------------- | --------------- | ----------------------- | ------------------------------------- |
| PriorityQueue | Heap-based (min-heap)   | Ordered by priority (not FIFO)        | Not allowed   | Not thread-safe | O(log n) insert/remove  | Priority-based processing, scheduling |
| ArrayDeque    | Resizable array (Deque) | FIFO (or LIFO as stack), double-ended | Not allowed   | Not thread-safe | O(1) insert/remove ends | General queue/stack replacement       |
| LinkedList    | Doubly linked list      | FIFO (queue), double-ended            | Allowed       | Not thread-safe | O(1) insert/remove ends | Simple queue, deque, or list          |

## Java Queue Implementations: Feature Comparison Table

| Collection Type    | Default Capacity  | Initial Capacity           | Allow Duplicates | Allow Null Values | Insertion Order                      | Sorted Order                      | Random Access | Synchronization       |
| ------------------ | ----------------- | -------------------------- | ---------------- | ----------------- | ------------------------------------ | --------------------------------- | ------------- | --------------------- |
| PriorityQueue      | 11                | User specified, default 11 | Yes              | No                | No (ordered by priority, not insert) | Yes (natural order or comparator) | No            | No (not thread-safe   |
| Deque (ArrayDeque) | 16                | User specified, default 16 | Yes              | No                | Yes (maintains insertion order)      | No                                | No            | No (not thread-safe)  |
| Deque (LinkedList) | N/A (linked list) | N/A (linked list)          | Yes              | Yes               | Yes (maintains insertion order)      | No                                | No            | No (not thread-safe)[ |

##### Specialized Queues

| Queue Type      | Implementation                                            | Ordering / Structure                   | Null Elements    | Thread Safety             | Performance             | Typical Use Case                 |
| --------------- | --------------------------------------------------------- | -------------------------------------- | ---------------- | ------------------------- | ----------------------- | -------------------------------- |
| Deque           | Interface (ArrayDeque, LinkedList)                        | Double-ended (insert/remove both ends) | Depends on impl. | Not thread-safe (default) | O(1) insert/remove ends | Stack + queue behaviors          |
| Circular Queue  | Custom (array-based)                                      | FIFO, circular buffer                  | Impl. dependent  | Not thread-safe           | O(1) insert/remove      | Fixed-size buffer, resource mgmt |
| Blocking Queues | Interface (e.g., ArrayBlockingQueue, LinkedBlockingQueue) | FIFO/priority, thread-safe             | Not allowed      | Thread-safe               | Blocking operations     | Producer-consumer, concurrency   |

---
#### Important Interview Questions on Queue:

##### Basic-Level Questions
1. **What is a Queue in Java?**
    - Explain the FIFO principle and mention it is an interface in `java.util`.
2. **What are the main implementations of Queue in Java?**
    - Examples: `LinkedList`, `PriorityQueue`, `ArrayDeque`.
3. **What is the difference between `add()` and `offer()`?**
    - `add()` throws exception if queue is full, `offer()` returns `false`.
4. **What is the difference between `remove()` and `poll()`?**
    - `remove()` throws exception if empty, `poll()` returns `null`.
5. **Can a Queue store `null` values?**
    - Depends on implementation. `PriorityQueue`, `ArrayDeque`, and `BlockingQueue` do **not** allow nulls. `LinkedList` does.
6. **Why is `Queue` not used for random access?**
    - Because it’s designed for sequential access (FIFO), not index-based access like `List`.

---
#####  **Intermediate-Level Questions**
7. **How does `PriorityQueue` work internally?**
    - It is implemented using a binary heap. The smallest (or highest priority) element is at the head.
8. **How do you implement a queue using arrays or linked lists?**
    - Common for coding rounds. You may be asked to write enqueue, dequeue, isFull, isEmpty methods.    
9. **What is the difference between `Queue` and `Deque`?**
    - `Deque` supports both FIFO and LIFO operations; `Queue` supports FIFO only.    
10. **How is `ArrayDeque` better than `LinkedList` for queues?**
    - Faster, no memory overhead of nodes, and resizable.    
11. **What are the limitations of a circular queue?**
    - Fixed size, complexity in handling wrap-around conditions.
12. **How would you implement a circular queue in Java?**

---
#####  Advanced/Conceptual Questions
13. **What is a `BlockingQueue`? When would you use it?**
	- Used in multithreading for producer-consumer problems. Blocks on insert/remove if queue is full/empty.
14. **Explain thread-safe queue implementations in Java.**
	- Examples: `BlockingQueue`, `ConcurrentLinkedQueue`.
15. **What are the types of `BlockingQueue`?**
	- `ArrayBlockingQueue`, `LinkedBlockingQueue`, `PriorityBlockingQueue`, etc.
16. **Why is `ConcurrentLinkedQueue` preferred in high-concurrency environments?**
	- Lock-free, non-blocking, scalable queue for concurrent use.
17. **What is the time complexity of different Queue operations?**
	- `add`, `offer`, `poll`, `remove`, and `peek` are generally **O(1)** for standard queues.
	- `PriorityQueue` operations like `add`, `poll` are **O(log n)**.
18. **How would you detect overflow/underflow in a custom queue implementation?**

#####  Coding / Problem-Solving Questions
19. **Implement a queue using two stacks.**
20. **Reverse a queue using recursion.**
21. **Check if a queue is palindrome.**
22. **Design a task scheduler using `PriorityQueue`.**
23. **Implement LRU cache using Queue and HashMap.**

---
####  Why so many types of queues are created in Java?

Different types of queues are created to solve **different types of problems** efficiently. A **single queue type cannot be optimal** for all situations — because different applications need different behavior in terms of **order, performance, concurrency, or memory use**.

Let’s break it down:
###### 🔹 1. Basic Queue (FIFO)
- **Purpose**: Simple "first-come-first-served" logic.   
- **Examples**: `LinkedList`, `ArrayDeque`.
- **Use Case**: Printer queue, task queue.

> **Why not enough?** These don't support special ordering or concurrency.

---
#####  2. PriorityQueue
- **Purpose**: Automatically keeps elements in **priority order** (not just FIFO).
- **Use Case**: Job schedulers, Dijkstra’s algorithm, event handling.

> **Why needed?** FIFO order isn’t always suitable. Sometimes high-priority tasks must be served first.

---
##### 3. Deque (Double-Ended Queue)
- **Purpose**: Insert/remove from **both front and rear**.
- **Examples**: `ArrayDeque`, `LinkedList`.
- **Use Case**: Undo operations, palindromes, sliding window problems.

> **Why needed?** Adds more flexibility — can act as both **queue and stack**.

---
#####  4. Circular Queue
- **Purpose**: Fixed-size queue that wraps around — efficient use of space.
- **Use Case**: Memory buffers, CPU scheduling.

> **Why needed?** Useful for **bounded memory environments**, unlike normal resizable queues.

---
#####  5. BlockingQueue (and its types)

- **Purpose**: Designed for **multithreading** — automatically waits if queue is full or empty.
- **Examples**: `ArrayBlockingQueue`, `LinkedBlockingQueue`, `PriorityBlockingQueue`.
- **Use Case**: Producer-consumer problems.

> **Why needed?** Standard queues are **not thread-safe** — can cause bugs in concurrent programs.

---
#####  6. Concurrent Queues
- **Examples**: `ConcurrentLinkedQueue`
- **Purpose**: **Lock-free**, high-throughput queues for concurrent access.
- **Use Case**: Real-time applications, network requests handling.


#####  Summary Table:

|Queue Type|Special Purpose|
|---|---|
|Basic Queue|FIFO structure|
|PriorityQueue|Priority-based processing|
|Deque|Double-ended access (stack + queue)|
|Circular Queue|Fixed size, memory-efficient|
|BlockingQueue|Thread-safe blocking operations|
|Concurrent Queue|Lock-free, high-performance queues|

---
#### Most Used Operations in Java Queue:

|Operation|Description|Throws Exception|Returns Special Value|
|---|---|---|---|
|add(e)|Insert element|Yes|No|
|offer(e)|Insert element|No|Yes (`false`)|
|remove()|Remove and return head|Yes|No|
|poll()|Remove and return head|No|Yes (`null`)|
|element()|Retrieve (not remove) head|Yes|No|
|peek()|Retrieve (not remove) head|No|Yes (`null`)|

> 🔸 Use `offer`, `poll`, and `peek` for safer exception-free usage.

##### Additional Operations in Deque (Double-Ended Queue)

|Operation|Front|Rear|What it returns|
|---|---|---|---|
|Add|`addFirst()`|`addLast()`|`void` (throws exception if fails)|
|Offer (safe)|`offerFirst()`|`offerLast()`|`boolean` (`true` if added)|
|Remove|`removeFirst()`|`removeLast()`|`E` (throws exception if empty)|
|Poll (safe)|`pollFirst()`|`pollLast()`|`E` (`null` if empty)|
|Peek (safe)|`peekFirst()`|`peekLast()`|`E` (`null` if empty)|

#####  Other Useful Methods (Depending on Implementation)

|Method|Purpose|
|---|---|
|`isEmpty()`|Checks if queue is empty|
|`size()`|Returns current number of elements|
|`contains(Object o)`|Checks if element is present|
|`clear()`|Removes all elements|
|`toArray()`|Converts queue to array|
|`iterator()`|Returns iterator to loop through elements|

---
