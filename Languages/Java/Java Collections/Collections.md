- What is **Collections**?
- Interfaces provided by collections framework?
- Classes provided by collections framework?
- Hierarchy of collections interface
- Hierarchy of Map interface


#### Collections:
- **Definition**: A **Collection** is a group of objects treated as a single unit. Java Collections Framework provides **classes and interfaces** to store and manipulate data efficiently. 
					  (or)
  main- **Collections in Java** is a **framework** that provides **classes and interfaces** to store and manipulate **groups of data** (like arrays, but more powerful).
- **Collections** -(means)-> framework, **Collection** -(means)-> interface.
- Framework provides many interfaces and their implemented classes in order to store group of objects(elements) in a single entity. 
- **Key Features:**
	- Predefined **interfaces** and **classes**.
	- Supports operations like **searching, sorting, insertion, deletion**.
	- Handles **dynamic data** (unlike arrays which are fixed in size).
-  Note: Don't confuse **Collection (interface)** with **Collections (class)**.
	- Collection → **Interface** (root of the collection hierarchy).
	- Collections → **Utility class** (with static methods like sort(), shuffle()).
	- Mostly all are interfaces(and classes inside it, that other classes has to follow) in collections framework.


- **List**: An ordered collection that allows duplicate elements. Elements can be accessed by their integer index. 
- **Set**: An unordered collection that does not allow duplicate elements.
- **Queue**: A collection used to hold multiple elements prior to processing, typically in a FIFO (first-in, first-out) order.
- **Map**: It is a different data structure which is a part of collection framework. An object that maps keys to values, with each key being unique and mapping to at most one value. It is Separate hierarchy.


These are **core interfaces** in the collections framework:

```
Collection (root)
├── List
├── Set
│   └── SortedSet
│       └── NavigableSet
└── Queue
    └── Deque

Map (separate hierarchy)
├── SortedMap
└── NavigableMap
```


Each interface has classes that implement it:

|Interface|Implementing Classes|
|---|---|
|`List`|`ArrayList`, `LinkedList`, `Vector`, `Stack`|
|`Set`|`HashSet`, `LinkedHashSet`, `TreeSet`|
|`Queue`|`PriorityQueue`, `ArrayDeque`|
|`Deque`|`ArrayDeque`, `LinkedList`|
|`Map`|`HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable`, `WeakHashMap`, `ConcurrentHashMap`|

#### Hierarchy of Collections Interface (Tree Format)

```
java.util
└── Collection (Interface)
    ├── List (Interface)
    │   ├── ArrayList
    │   ├── LinkedList
    │   ├── Vector
    │   └── Stack
    │
    ├── Set (Interface)
    │   ├── HashSet
    │   ├── LinkedHashSet
    │   └── SortedSet (Interface)
    │       └── NavigableSet (Interface)
    │           └── TreeSet
    │
    └── Queue (Interface)
        ├── PriorityQueue
        └── Deque (Interface)
            └── ArrayDeque
```


##### Hierarchy of Map Interface (Separate from Collection)

```
java.util
└── Map (Interface)
    ├── HashMap
    ├── LinkedHashMap
    ├── SortedMap (Interface)
    │   └── NavigableMap (Interface)
    │       └── TreeMap
    ├── Hashtable
    └── ConcurrentMap (Interface)
        └── ConcurrentHashMap
```


![[Pasted image 20250514200856.png]]


![[Pasted image 20250514201236.png]]


![[Pasted image 20250514201512.png]]


![[Pasted image 20250514201557.png]]


#### Java Arrays vs Java Lists – Feature Comparison

|**Feature / Operation**|**Java Array** (`String[]`, `int[]`)|**Java List** (`List<String>`, `List<Integer>`)|
|---|---|---|
|**Fixed Size After Creation**|✅ Yes|❌ No (Resizable)|
|**Add/Remove Elements After Creation**|❌ No (Only overwrite values)|✅ Yes (`add()`, `remove()`)|
|**Access/Modify by Index**|✅ Yes (`arr[0] = value`)|✅ Yes (`list.set(0, value)`)|
|**Store Primitive Types Directly (int, char)**|✅ Yes (`int[]`, `char[]`)|❌ No (Use wrapper types like `Integer`, `Character`)|
|**Generic Support (e.g., `<String>`)**|❌ No|✅ Yes|
|**Multidimensional Support**|✅ Yes (`int[][]`)|🔶 Indirect (`List<List<>>`) – more complex|
|**Length or Size**|✅ `.length`|✅ `.size()`|
|**Enhanced For-Loop Support**|✅ Yes|✅ Yes|
|**Sorting (using utilities)**|✅ `Arrays.sort(array)`|✅ `Collections.sort(list)`|
|**Search (contains, indexOf, etc.)**|❌ No (manual logic needed)|✅ Yes (`contains()`, `indexOf()`)|
|**Conversion to Collection Types**|❌ Manual conversion needed|✅ Already a collection|
|**Thread-safe by default**|❌ No|❌ No (can use `Collections.synchronizedList()`)|
|**Immutable Option Available**|❌ No (not by default)|✅ Yes (`List.of()` or `Collections.unmodifiableList()`)|
|**Performance (for fixed size)**|✅ Fast|🔶 Slightly slower due to dynamic nature|

##### Other:
- Learn in this way - for List: Vector-> ArrayList -> Stack -> LinkedList.
- Before learning Set's hashsets & linked hashsets learn map hashmap's & linked hashmaps.
- **Which ones to focus on while learning search's?**  
	- **Must‑know:** Linear, Binary, Hash‑based, Stream‑based  
	- **Great bonus:** Jump (√n), Exponential, Interpolation (conceptual)  
	- **Specialty:** Fibonacci, Ternary, Pattern/Text only if you’ll deal with heavy string‑search or high‑performance code
