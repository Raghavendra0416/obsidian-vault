Major Operations
- Creation of a map
- Addition of elements into the map
- Retrieval of keys from the map
- Retrieval of values from the map
- Deletion of elements from the map
- Verification of keys in the map
- Verification of values in the map
- Updating of elements in the map


![[Pasted image 20250619181345.png]]
  
Map:
- Definition:
	Map is an interface. A class should be created to use map in java. It is a key value pair. (or)
	In Java, a Map is a collection that maps keys to values. Each key can map to at most one value, and keys are unique
- Map won't loop over all records in it's directory instead it will directly go the key and pull the data of the given key.
- All the maps have same operations.
- The `Map` interface in Java does **not implement the `Collection` interface**. It is part of the Java Collections Framework but represents a **separate hierarchy** designed for key-value pairs. Instead of storing individual elements like `List` or `Set`, a `Map` stores **entries**, each consisting of a key and a value. Common implementations of `Map` include `HashMap`, `TreeMap`, and `LinkedHashMap`.
- Map is an interface So, a Class needs to be implemented to use it, so different classes are implemented based on usage. it has several commonly used implementations:(Remember below and their hierarchy) 5 types(total 5 types):
		- HashMap
		- LinkedHashMap
		- TreeMap
		- Hashtable
		- ConcurrentHashMap
- But in the above the **differences are in performance, ordering, and thread safety**, which matter **a lot** depending on the **real-world scenario**.
- `entrySet()` is used to loop through all key-value pairs in a Map, especially when we don't know them in advance. Inside the loop, we can use `.getKey()` and `.getValue()` on each entry.

#####  WHY So Many Map Types?

Each map type is optimized for **different needs**. Here's a breakdown:

| Map Type            | Key Feature                             | Best Use Case                                     |
| ------------------- | --------------------------------------- | ------------------------------------------------- |
| `HashMap`           | Fast access, no order                   | General-purpose when order doesn't matter         |
| `LinkedHashMap`     | Maintains insertion order               | Caching (LRU), preserving user input order        |
| `TreeMap`           | Sorted map (by keys)                    | Sorted data, range queries                        |
| `Hashtable`         | Thread-safe (legacy), synchronized      | Legacy apps (rarely used in modern code)          |
| `ConcurrentHashMap` | Thread-safe, better concurrency support | Multi-threaded environments, web servers, caching |

#### Quick Real-Life Examples

##### 1. **HashMap**

- Most commonly used
- Fast `O(1)` lookup and insert
- Used when order doesn't matter

📍 **Example**:  
Storing product IDs and prices, student names and grades, config settings, etc.

```java
Map<String, Integer> inventory = new HashMap<>();
inventory.put("Apple", 50);
inventory.put("Orange", 40);
```

---
##### 2.  **LinkedHashMap**

- Maintains **insertion order**
- Useful for predictable iteration
- Slightly slower than HashMap


📍 **Example**:  
Implementing **LRU Cache** (Least Recently Used), where you want to evict the oldest entry.

```java
Map<String, String> recentSearches = new LinkedHashMap<>();
recentSearches.put("java", "Java tutorials");
recentSearches.put("python", "Python tutorials");
```

---
##### 3.  **TreeMap**

- Keeps keys **sorted**
- Slower (`O(log n)`) but allows **range operations**

📍 **Example**:  
Banking: sorted transaction timestamps, leaderboard by score, range search in data.

```java
Map<Integer, String> scores = new TreeMap<>();
scores.put(85, "Alice");
scores.put(95, "Bob");
scores.put(90, "Charlie");
```

You can get sub-maps like:

```java
scores.subMap(85, 95); // from 85 to 94
```

---
##### 4.  **Hashtable**

- **Legacy** class (from Java 1.0)
- Thread-safe using coarse-grained locking (slow)
- No null keys or values

📍 **Example**:  
Old Java apps before `ConcurrentHashMap` existed. Rarely used today.

---
##### 5.  **ConcurrentHashMap**

- Designed for **high-performance multi-threaded apps**
- Allows concurrent reads and safe concurrent writes
- Fine-grained locking = better performance than `Hashtable`

📍 **Example**:  
Web servers, multi-threaded caching (e.g., Spring Boot app caching API responses)

```java
ConcurrentMap<String, String> cache = new ConcurrentHashMap<>();
cache.put("user_1", "Raghav");
```

---
#####  Summary Table (Use Case Driven)

|Use Case|Best Map Type|
|---|---|
|Fast, general-purpose lookup|`HashMap`|
|Need predictable iteration order|`LinkedHashMap`|
|Need sorted keys|`TreeMap`|
|Multi-threaded environment|`ConcurrentHashMap`|
|Legacy multi-threaded code|`Hashtable`|
|Implementing LRU cache|`LinkedHashMap`|
|Storing configuration settings|`HashMap`|
|Range query on keys|`TreeMap`|
|Shared cache in multi-threaded app|`ConcurrentHashMap`|

|Operation|Method Used|
|---|---|
|Create Map|`Map<K, V> map = new HashMap<>();`|
|Add Element|`map.put(key, value);`|
|Get All Keys|`map.keySet();`|
|Get All Values|`map.values();`|
|Remove Element|`map.remove(key);`|
|Check Key Exists|`map.containsKey(key);`|
|Check Value Exists|`map.containsValue(value);`|
|Update Element|`map.put(key, newValue);`|

---
#### Java Map Implementations: Feature Comparison

| Collection Type | Default Capacity | Initial Capacity           | Allow Duplicate Keys | Allow Null Keys | Allow Null Values | Insertion Order                 | Sorted Order    | Synchronization      |
| --------------- | ---------------- | -------------------------- | -------------------- | --------------- | ----------------- | ------------------------------- | --------------- | -------------------- |
| Hashtable       | 11               | User specified, default 11 | No                   | No              | No                | No (unordered)                  | No              | Yes (thread-safe)    |
| HashMap         | 16               | User specified, default 16 | No                   | Yes (one)       | Yes (multiple)    | No (unordered)                  | No              | No (not thread-safe) |
| LinkedHashMap   | 16               | User specified, default 16 | No                   | Yes (one)       | Yes (multiple)    | Yes (maintains insertion order) | No              | No (not thread-safe) |
| TreeMap         | 16               | User specified, default 16 | No                   | No              | Yes (multiple)    | No (sorted by key)              | Yes (ascending) | No (not thread-safe) |

---
##### Most Used Operations in Map:
Create Map, Add Element, Get All Keys, Get All Values, Remove Element, Check Key Exists, Check Value Exists, Update Element, replace, empty operations.
**we use the same functions for all types of Maps** in Java, because all Map types implement the Map interface.
- **Create Map**: `Map<String, String> map = new HashMap<>();`
- **Add Element**: `map.put("key1", "value1");`
- **Set/Update Element**: `map.put("key1", "newValue");` _(same method as add — updates if key exists)_
- **Replace Element**: `map.replace("key1", "newValue");` _(only replaces if key exists)_
- **Get Element by Key**: `String value = map.get("key1");`
- **Get All Keys**: `Set<String> keys = map.keySet();`
- **Get All Values**: `Collection<String> values = map.values();`
- **Remove Element**: `map.remove("key1");`
- **Check Key Exists**: `boolean hasKey = map.containsKey("key1");`
- **Check Value Exists**: `boolean hasValue = map.containsValue("value1");`
- **Get Entry Set**: `Set<Map.Entry<K, V>> entries = map.entrySet();`
- **Check if Map is Empty**: `boolean isEmpty = map.isEmpty();`
- **Get Size of Map**: `int size = map.size();`
- **Clear All Entries**: `map.clear();`
- **Put If Absent**: `map.putIfAbsent("key1", "value1");` _(adds only if key is not already present)_

Other commonly used Map operations:

- **Iterate Over Map (Entry Set)**: `for (Map.Entry<String, String> entry : map.entrySet()) {}`
- **Iterate Over Keys**: `for (String key : map.keySet()) {}`
- **Iterate Over Values**: `for (String value : map.values()) {}`
- **Put If Absent**: `map.putIfAbsent("key1", "value1");`
- **Replace with Old Value Check**: `map.replace("key1", "oldValue", "newValue");`
- **Compute Value**: `map.compute("key1", (k, v) -> v + "_updated");`
- **Merge Values**: `map.merge("key1", "value1", (oldVal, newVal) -> oldVal + newVal);`
- **Get Default if Key Not Found**: `map.getOrDefault("key1", "default");`

---

