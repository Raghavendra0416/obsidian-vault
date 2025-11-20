###### key points to remember while definition:
**Collections:** Framework, Class, interfaces, groups of data 
Key features for collections: Dynamic data, Searching, Sorting, deleting, inserting.

List -> order collections, allow duplicate elements.
Set-> Unordered Collections, does not allow duplicate elements.
Queue -> FIFO, Order, Elements -> inserted -> end (tail)
					Elements -> Removed -> Start (head)
Map -> Key: Value, Key being unique.

Pure Classes which implements only Lists, Sets, Queue, Map interface:
List- Vector, Array List
Set - Hash Set
Queue- Priority Queue
Map- Hash Table, Hash Map.

---
#### Similarities between Java Collections:
Comprehensive list of Java Collection classes that share similar naming conventions across the four main collection types: Lists, Sets, Queues, and Maps. This table highlights the classes that have "Array", "Linked", "Hash", or "Tree" in their names, showing their relationship and typical usage.

|Collection Type|Array-based|Linked-based|Hash-based|Tree-based|Other Common Classes|
|---|---|---|---|---|---|
|**List**|ArrayList|LinkedList|—|—|Vector, Stack|
|**Set**|—|LinkedHashSet|HashSet|TreeSet|CopyOnWriteArraySet|
|**Queue/Deque**|ArrayDeque|LinkedList|—|—|PriorityQueue, DelayQueue|
|**Map**|—|LinkedHashMap|HashMap, HashTable|TreeMap|ConcurrentHashMap, WeakHashMap|

##### Explanation
- **Array-based**:
    - `ArrayList` (List), `ArrayDeque` (Queue/Deque) use arrays internally for storage and fast random access.

- **Linked-based**:
    - `LinkedList` (List, Queue/Deque), `LinkedHashSet` (Set), `LinkedHashMap` (Map) use linked nodes to maintain order and allow efficient insertions/removals.

- **Hash-based**:
    - `HashSet` (Set), `HashMap` (Map), `HashTable` (Map, legacy) use hash tables for fast lookup and uniqueness.

- **Tree-based**:
    - `TreeSet` (Set), `TreeMap` (Map) use red-black trees for sorted order.

- **Other Common Classes**:
    - `Vector` and `Stack` are legacy List implementations.
    - `PriorityQueue` and `DelayQueue` are special-purpose queues.
    - `CopyOnWriteArraySet` is a thread-safe Set.
    - `ConcurrentHashMap`, `WeakHashMap` are specialized Map implementations.

##### Key Points
- Classes with similar names (like "LinkedList", "LinkedHashSet", "LinkedHashMap") indicate linked structure and often maintain insertion order.
- "Hash" classes are optimized for quick access and uniqueness.
- "Tree" classes provide sorted order.
- "Array" classes are optimized for indexed access and efficiency.

---
#### Similarities Between List, Set, Queue, and Map
##### Chat GPT response:

| Feature / Collection Type               | **List**                               | **Set**                               | **Queue**                                    | **Map**                               |
| --------------------------------------- | -------------------------------------- | ------------------------------------- | -------------------------------------------- | ------------------------------------- |
| **Part of Collection Framework**        | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes                                 |
| **Import from `java.util`**             | ✅ Yes (`java.util.List`)               | ✅ Yes (`java.util.Set`)               | ✅ Yes (`java.util.Queue`)                    | ✅ Yes (`java.util.Map`)               |
| **Supports Generics**                   | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes                                 |
| **Supports `null` elements**            | ✅ Yes (depending on implementation)    | ✅ Yes (HashSet allows 1 `null`)       | ✅ Yes (e.g., LinkedList)                     | ✅ Yes (1 null key in HashMap)         |
| **Can be Traversed with Iterator**      | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes (via `entrySet()`, etc.)        |
| **Supports `for-each` loop**            | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes (on `entrySet()`, etc.)         |
| **Can be Synchronized (manually)**      | ✅ Yes (`Collections.synchronizedList`) | ✅ Yes (`Collections.synchronizedSet`) | ✅ Yes (`Collections.synchronizedCollection`) | ✅ Yes (`Collections.synchronizedMap`) |
| **Supports Java 8 Streams API**         | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes (`entrySet().stream()`)         |
| **Can be used to store custom objects** | ✅ Yes                                  | ✅ Yes                                 | ✅ Yes                                        | ✅ Yes                                 |

##### perplexity response:

| Feature                       | List                                                                                                                                                                                                                                                         | Set                                                                                                                                                                                                                                                          | Queue                                                                                                                                                                                                                                                        | Map                                                                                                                                                                                                                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Part of Collections Framework | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                              |
| Store Objects (Generic)       | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes (as values)[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                  |
| Allow Null Values             | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                   | Yes (varies by impl.)[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                 | Yes (varies by impl.)[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                 | Yes (keys/values, varies by impl.)[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                 |
| Iterable (can use for-each)   | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes (over keys, values, entries)[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) |
| Support for Bulk Operations   | Yes (addAll, removeAll, etc.)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                   | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                             | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                             | Yes (putAll, clear, etc.)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                                    |
| Not Thread-Safe by Default    | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                              |
| Allow Custom Implementations  | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                             | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                             | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                             | Yes[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                                                                                                                          |
| Resizable (Dynamic Size)      | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table) | Yes[1](https://www.codejava.net/java-core/collections/java-collections-framework-summary-table)[2](https://www.digitalocean.com/community/tutorials/collections-in-java-tutorial)[3](https://www.scribd.com/document/767114786/Collections-Comparison-Table)                              |

##### Flashcard: Common Similarities – Java Collections:
- Part of the **Java Collection Framework**  
- Use **Generics** (`<T>`, `<K, V>`)  
- Can be **iterated** using `Iterator` or `for-each` loop  
- Support **Java 8 Streams API**  
 - Allow **null elements** (depends on implementation)  
 - Can store **custom objects**  
 - Can be **synchronized** using `Collections.synchronizedXXX()`  
- Require import from **`java.util` package**
- **None are thread-safe by default**; thread-safe versions are available or can be created using utility methods.
- **All support bulk operations** such as adding or removing multiple elements at once.
- **List, Set, and Queue** all extend the `Collection` interface, but **Map** does not; it is a separate interface in the framework

---
#### Differences Between Lists, Sets, Queue, Map:

##### Chat Gpt:

| Feature / Collection Type  | **List**                                                                | **Set**                                                               | **Queue**                                                                      | **Map**                                                                          |
| -------------------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| **Duplication**            | Allows duplicate elements                                               | **No** duplicates                                                     | Allows duplicates (depending on impl.)                                         | Keys unique; values may duplicate                                                |
| **Ordering**               | Maintains insertion order                                               | **No** guaranteed order (HashSet)                                     | Typically insertion order (e.g. LinkedList) or priority order (PriorityQueue)  | **No** inherent order (HashMap); ordered variants exist (LinkedHashMap, TreeMap) |
| **Access by index/key**    | Yes: `get(int index)`                                                   | **No** index-based access                                             | **No** index; head/tail operations                                             | Yes: `get(key)`, `put(key,value)`                                                |
| **Null elements / keys**   | Allows `null` elements                                                  | Allows one `null` (HashSet)                                           | Allows `null` (e.g. LinkedList)                                                | Allows one `null` key & multiple `null` values (HashMap)                         |
| **Interface hierarchy**    | Extends `Collection<E>`                                                 | Extends `Collection<E>`                                               | Extends `Collection<E>`                                                        | Separate top‐level interface `Map<K,V>`                                          |
| **Common implementations** | `ArrayList`, `LinkedList`, `Vector`                                     | `HashSet`, `LinkedHashSet`, `TreeSet`                                 | `LinkedList`, `PriorityQueue`, `ArrayDeque`                                    | `HashMap`, `LinkedHashMap`, `TreeMap`, `ConcurrentHashMap`                       |
| **Typical use-case**       | Ordered sequence, random access                                         | Membership testing, de-duplication                                    | Task scheduling, breadth-first traversal                                       | Key-value lookups, associative arrays                                            |
| **Iteration cost**         | O(n)                                                                    | O(n)                                                                  | O(n)                                                                           | O(n) via `entrySet()`                                                            |
| **Add / remove cost**      | O(1) amortized (`ArrayList`), O(1) (`LinkedList`)                       | O(1) amortized (`HashSet`), O(log n) (`TreeSet`)                      | O(1) (`LinkedList`), O(log n) (`PriorityQueue`)                                | O(1) amortized (`HashMap`), O(log n) (`TreeMap`)                                 |
| **Supports indexing**      | Yes                                                                     | No                                                                    | No                                                                             | Key-based only                                                                   |
| **Thread-safe variant**    | `CopyOnWriteArrayList`, synchronized via `Collections.synchronizedList` | `CopyOnWriteArraySet`, synchronized via `Collections.synchronizedSet` | `ConcurrentLinkedQueue`, synchronized via `Collections.synchronizedCollection` | `ConcurrentHashMap`, synchronized via `Collections.synchronizedMap`              |

**Notes:**
- **Ordering**: “insertion order” means elements come out in the sequence they were added.
- **Duplication**: Sets strictly forbid duplicate entries; Lists and Queues allow duplicates by default.
- **Performance**: Listed for typical implementations; can vary with concrete choice.

##### Perplexity:

|Feature/Property|List|Set|Queue|Map|
|---|---|---|---|---|
|**Duplicates Allowed**|Yes|No|Depends (usually no)|Keys: No, Values: Yes|
|**Order Maintained**|Yes (insertion order)|No (except some, e.g. LinkedHashSet)|Yes (FIFO/LIFO/Priority)|No (except LinkedHashMap, TreeMap)|
|**Null Handling**|Multiple nulls allowed|At most one null (varies)|Varies by implementation|One null key, multiple null values|
|**Data Structure**|Elements|Unique elements|Elements (FIFO/LIFO/Priority)|Key-value pairs|
|**Index Access**|Yes (get by index)|No|No|No (access by key only)|
|**Main Use Case**|Ordered collection, duplicates|Unique collection|Processing in order|Mapping keys to values|
|**Implements Collection?**|Yes|Yes|Yes|No|
|**Typical Implementations**|ArrayList, LinkedList|HashSet, TreeSet, LinkedHashSet|LinkedList, PriorityQueue|HashMap, TreeMap, LinkedHashMap|

- **List**: Ordered, allows duplicates, index-based access
- **Set**: Unordered (unless specified), unique elements, no index
- **Queue**: Order based on insertion or priority, typically no duplicates, FIFO/LIFO/Priority
- **Map**: Stores key-value pairs, unique keys, values can duplicate, not a Collection

---
