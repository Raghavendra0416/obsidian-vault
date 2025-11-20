
- [Collections topic information](https://www.codejava.net/java-core/collections/overview-of-java-collections-framework-api-uml-diagram)

### 🗂️ Summary of Each Interface:

- **List**: Ordered, allows duplicates. Access by index.
    
    - `ArrayList`, `LinkedList`, `Vector`
        
- **Set**: No duplicates, no indexing.
    
    - `HashSet`: Unordered
        
    - `LinkedHashSet`: Maintains insertion order
        
    - `TreeSet`: Sorted order
        
- **Queue**: FIFO ordering (usually). For processing elements.
    
    - `PriorityQueue`: Orders by priority
        
    - `ArrayDeque`: Double-ended queue
        
- **Map**: Key-value pairs (**not a Collection**, but part of the framework)
    
    - `HashMap`: Unordered
        
    - `LinkedHashMap`: Insertion order
        
    - `TreeMap`: Sorted by keys
        

### 🧩 Overview of the Java Collections Framework

The Java Collections Framework provides a set of interfaces and classes that implement commonly reusable collection data structures. It includes:

- **Core Interfaces**: Define the basic operations for collections.
    
    - `Collection`: The root interface.
        
    - `List`: An ordered collection (e.g., `ArrayList`, `LinkedList`).
        
    - `Set`: A collection that does not allow duplicate elements (e.g., `HashSet`, `TreeSet`).
        
    - `Queue`: A collection used to hold multiple elements prior to processing (e.g., `PriorityQueue`, `LinkedList`).
        
    - `Map`: An object that maps keys to values, not a true collection but part of the framework (e.g., `HashMap`, `TreeMap`).
        
- **Implementations**: Concrete classes that implement the collection interfaces.
    
    - `ArrayList`, `LinkedList`, `HashSet`, `TreeSet`, `HashMap`, `TreeMap`, etc.
        
- **Algorithms**: Methods that perform useful computations, such as searching and sorting, on objects that implement collection interfaces.
    
![[collections structure.png]]

