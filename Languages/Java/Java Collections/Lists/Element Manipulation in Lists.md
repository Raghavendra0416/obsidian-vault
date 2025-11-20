

- To reverse a list(ArrayList,Vector,LinkedList) we can use Collections.reverse(); but for stack it is better to use push and pop as it uses LIFO.
####  **ArrayList** – Important Functions to Remember

```java
import java.util.ArrayList;
```

1. **Adding Elements**

```java
list.add("A");                    // Adds element at the end
list.add(1, "B");                 // Adds element at specific index
```

2. **Accessing Elements**

```java
String element = list.get(0);    // Returns element at index 0
```

3. **Updating Elements**

```java
list.set(0, "Z");                // Replaces element at index 0 with "Z"
```

4. **Removing Elements**

```java
list.remove(0);                  // Removes element at index 0
list.remove("A");                // Removes the first occurrence of "A"
```

5. **Size and Check**

```java
list.size();                     // Returns number of elements
list.isEmpty();                  // Checks if list is empty
```

6. **Search**

```java
list.contains("B");             // Checks if list contains "B"
list.indexOf("B");              // Returns index of "B", or -1 if not found
```

7. **Clear List**

```java
list.clear();                   // Removes all elements
```

8. **Iteration**

```java
for (String item : list) {
    System.out.println(item);
}
```

---

####  **Vector** – Important Functions to Remember

```java
import java.util.Vector;
```

1. **Creating a Vector**

```java
Vector<String> vector = new Vector<>();
```

2. **Adding Elements**

```java
vector.add("A");                  // Adds element at the end
vector.add(1, "B");               // Adds element at specific index
```

3. **Accessing Elements**

```java
String element = vector.get(0);   // Gets element at index 0
```

4. **Updating Elements**

```java
vector.set(0, "Z");               // Replaces element at index 0 with "Z"
```

5. **Removing Elements**

```java
vector.remove(0);                 // Removes element at index 0
vector.remove("A");               // Removes first occurrence of "A"
```

6. **Size and Check**

```java
vector.size();                    // Returns number of elements
vector.isEmpty();                 // Checks if vector is empty
```

7. **Search**

```java
vector.contains("B");             // Checks if vector contains "B"
vector.indexOf("B");              // Returns index of "B"
```

8. **Clear Vector**

```java
vector.clear();                   // Removes all elements
```

9. **Capacity Related**

```java
vector.capacity();                // Gets the current capacity
vector.ensureCapacity(20);        // Increases capacity to at least 20
```

10. **Iteration**

```java
for (String item : vector) {
    System.out.println(item);
}
```

---

#### **Stack** – Important Functions to Remember

 - **Stack** is a subclass of **Vector** and follows **LIFO (Last In First Out)** behavior.
 - Stack is ideal when you need **reversing**, **backtracking**, or **undo** operations.

```java
import java.util.Stack;
```

1. **Creating a Stack**

```java
Stack<String> stack = new Stack<>();
```

2. **Push (Add to top)**

```java
stack.push("A");       // Pushes "A" onto the top
stack.push("B");       // Pushes "B" onto the top
```

3. **Pop (Remove top element)**

```java
String top = stack.pop();   // Removes and returns the top element
```

4. **Peek (Look at top without removing)**

```java
String top = stack.peek();  // Returns the top element without removing
```

5. **Check if Empty**

```java
stack.isEmpty();            // Returns true if stack is empty
```

6. **Search**

```java
stack.search("A");          // Returns 1-based position from top or -1 if not found
```

7. **Size**

```java
stack.size();               // Returns number of elements in the stack
```

8. **Iteration (Optional, for display)**

```java
for (String item : stack) {
    System.out.println(item);
}
```

---

#### **LinkedList** – Important Functions to Remember

- **LinkedList** – a powerful and flexible list implementation that also allows **queue** and **deque** behavior.
- **Note:** `LinkedList` is doubly linked and efficient for insertions/deletions from both ends, but slower for random access compared to `ArrayList`.

```java
import java.util.LinkedList;
```

1. **Creating a LinkedList**

```java
LinkedList<String> list = new LinkedList<>();
```

2. **Adding Elements**

```java
list.add("A");                 // Adds at end
list.add(1, "B");              // Adds at specific index
list.addFirst("X");           // Adds at the beginning
list.addLast("Y");            // Adds at the end (same as add())
```

3. **Accessing Elements**

```java
list.get(0);                  // Gets element at index 0
list.getFirst();              // Gets the first element
list.getLast();               // Gets the last element
```

4. **Updating Elements**

```java
list.set(0, "Z");             // Sets element at index 0 to "Z"
```

5. **Removing Elements**

```java
list.remove(0);               // Removes element at index 0
list.remove("B");             // Removes first occurrence of "B"
list.removeFirst();           // Removes the first element
list.removeLast();            // Removes the last element
```

6. **Size and Check**

```java
list.size();                  // Returns number of elements
list.isEmpty();               // Checks if list is empty
```

7. **Search**

```java
list.contains("A");           // Checks if list contains "A"
list.indexOf("A");            // Gets index of "A"
```

8. **Queue Operations**

```java
list.offer("C");              // Adds to the end (like enqueue)
list.poll();                  // Removes and returns head (like dequeue)
list.peek();                  // Returns head without removing
```

9. **Iteration**

```java
for (String item : list) {
    System.out.println(item);
}
```


---
####  **Comparison Table**

| Feature / Method          | ArrayList        | Vector                         | Stack                       | LinkedList                       |
| ------------------------- | ---------------- | ------------------------------ | --------------------------- | -------------------------------- |
| **Implements**            | List             | List, RandomAccess             | List (extends Vector)       | List, Deque, Queue               |
| **Thread-safe?**          | ❌ No             | ✅ Yes                          | ✅ Yes (inherits Vector)     | ❌ No                             |
| **Order maintained?**     | ✅ Yes            | ✅ Yes                          | ✅ Yes (LIFO)                | ✅ Yes                            |
| **Random Access (fast?)** | ✅ Yes (fast)     | ✅ Yes                          | ✅ Yes                       | ❌ No (slow)                      |
| **Insert/Delete (mid)**   | ❌ Slow           | ❌ Slow                         | ❌ Not applicable            | ✅ Fast                           |
| **Add First / Last**      | ❌ Only end       | ❌ Only end                     | ✅ Top only (push)           | ✅ Both (addFirst, addLast)       |
| **Used for**              | General list     | Thread-safe list               | Stack (LIFO behavior)       | Queue/Deque, fast insertions     |
| **Useful Methods**        | `add()`, `get()` | `add()`, `get()`, `capacity()` | `push()`, `pop()`, `peek()` | `addFirst()`, `poll()`, `peek()` |

---

####  Summary of Different Methods to Assign Data to ArrayList for created class object:

1. **Directly using constructor when adding to the list**  
    `students.add(new Student(1, "Alice", "Bangalore", "10th"));`
    
2. **Create a `Student` object first and then use `.add()`**
    
    ```java
    Student s = new Student(2, "Bob", "Chennai", "9th");
    students.add(s);
    ```
    
3. **Initialize an empty object and set fields manually**  
    (Less preferred without setters, but still possible)
    
    ```java
    Student s = new Student(0, "", "", "");
    s.id = 3;
    s.name = "Charlie";
    ...
    students.add(s);
    ```
    
4. **Use setter methods (recommended if you follow JavaBean conventions)**  
    You'd need to define `setId()`, `setName()` etc., in the `Student` class.

---
#### Adding n number of elements at a time:

1. **Using `Arrays.asList()` (Java 5+)**

```java
import java.util.ArrayList;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<>(Arrays.asList("Apple", "Banana", "Mango", "Orange"));
        System.out.println(fruits);
    }
}
```

- This creates a list with initial elements.
- The result is mutable if wrapped in `new ArrayList<>()`.

2. **Using `Collections.addAll()`**

```java
import java.util.ArrayList;
import java.util.Collections;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<>();
        Collections.addAll(fruits, "Apple", "Banana", "Mango", "Orange");
        System.out.println(fruits);
    }
}
```

- This is useful if you already have an `ArrayList` and want to add elements in one go.


3. **Using Java 9+ `List.of()` (Immutable list)**
	If you're just creating a fixed list (not necessarily an `ArrayList`), use:

```java
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> fruits = List.of("Apple", "Banana", "Mango", "Orange");
        System.out.println(fruits);
    }
}
```

⚠️ `List.of()` returns an **immutable** list — you **cannot add or remove** elements after creation.


Optional: Convert `List.of()` to Mutable `ArrayList`

```java
ArrayList<String> fruits = new ArrayList<>(List.of("Apple", "Banana", "Mango", "Orange"));
```

Summary Table

|Method|Mutable|Java Version|
|---|---|---|
|`new ArrayList<>(Arrays.asList(...))`|✅|5+|
|`Collections.addAll(...)`|✅|5+|
|`List.of(...)`|❌|9+|

#### **Map**

Java doesn't support `Map` literals directly like some other languages, but here are clean alternatives:

##### Java 8 and earlier (Double brace initialization)
```Java
import java.util.*;

Map<String, Integer> map = new HashMap<String, Integer>() {{
    put("A", 1);
    put("B", 2);
    put("C", 3);
}};
```
⚠️ This creates an anonymous class and may cause memory leaks — **use with caution**.

 #### Java 9+ (Immutable Map)

```Jaava
import java.util.*;

Map<String, Integer> map = Map.of("A", 1, "B", 2, "C", 3);
```

- Creates an **immutable** map.
- Maximum 10 entries with `Map.of()`; use `Map.ofEntries(...)` for more.

##### Java 8+ using `Stream` (mutable map)

```Java
import java.util.*;
import java.util.stream.*;

Map<String, Integer> map = Stream.of(
    new AbstractMap.SimpleEntry<>("A", 1),
    new AbstractMap.SimpleEntry<>("B", 2),
    new AbstractMap.SimpleEntry<>("C", 3)
).collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));
```

#### Summary Table:

| Collection   | Bulk Add with Constructor | `Collections.addAll()` | Java 9+ Literal |
| ------------ | ------------------------- | ---------------------- | --------------- |
| `ArrayList`  | ✅                         | ✅                      | ✅ (`List.of`)   |
| `LinkedList` | ✅                         | ✅                      | ✅ (`List.of`)   |
| `Queue`      | ✅ via `LinkedList`        | ✅                      | ✅ (`List.of`)   |
| `Set`        | ✅                         | ✅                      | ✅ (`Set.of`)    |
| `Map`        | ❌ (special cases)         | ❌                      | ✅ (`Map.of`)    |

---


#### Java Collections & Streams Methods Cheat Sheet

| **Category**                            | **Method**                           | **What it Does**      | **Key Point 🚀**      | **Return Value**          | **Needs Lambda** | **Doesn’t Need Lambda** | **Quick Example**                                |
| --------------------------------------- | ------------------------------------ | --------------------- | --------------------- | ------------------------- | ---------------- | ----------------------- | ------------------------------------------------ |
| **List (java.util.List)**               | `add(E)` / `add(int,E)`              | Append/insert element | May shift indices     | `boolean` / `void`        | ❌                | ✅                       | `list.add("x")`                                  |
|                                         | `addAll(Collection)`                 | Append many           | Bulk add              | `boolean`                 | ❌                | ✅                       | `list.addAll(xs)`                                |
|                                         | `get(int)`                           | Read by index         | O(1) for `ArrayList`  | `E`                       | ❌                | ✅                       | `list.get(0)`                                    |
|                                         | `set(int,E)`                         | Replace at index      | In-place              | `E` (old)                 | ❌                | ✅                       | `list.set(0,"y")`                                |
|                                         | `remove(int/E)`                      | Remove by index/value | Shifts indices        | `E`/`boolean`             | ❌                | ✅                       | `list.remove(0)`                                 |
|                                         | `removeIf(Predicate)`                | Remove by condition   | Mutates list          | `boolean`                 | ✅                | ❌                       | `list.removeIf(s->s.isEmpty())`                  |
|                                         | `replaceAll(UnaryOperator)`          | Transform in-place    | Mutates list          | `void`                    | ✅                | ❌                       | `list.replaceAll(String::toUpperCase)`           |
|                                         | `sort(Comparator)`                   | Sort in-place         | Stable since Java 8   | `void`                    | (Optional) ✅     | ✅                       | `list.sort(Comparator.naturalOrder())`           |
|                                         | `contains(Object)`                   | Membership test       | `equals()`-based      | `boolean`                 | ❌                | ✅                       | `list.contains("a")`                             |
|                                         | `indexOf/lastIndexOf`                | Find index            | `-1` if none          | `int`                     | ❌                | ✅                       | `list.indexOf("a")`                              |
|                                         | `subList(from,to)`                   | View/slice            | Backed by original    | `List<E>` (view)          | ❌                | ✅                       | `list.subList(1,3)`                              |
| **Set (java.util.Set)**                 | `add(E)` / `remove(E)`               | Insert/remove unique  | No order in `HashSet` | `boolean`                 | ❌                | ✅                       | `set.add("x")`                                   |
|                                         | `contains(Object)`                   | Membership test       | O(1) avg in `HashSet` | `boolean`                 | ❌                | ✅                       | `set.contains("x")`                              |
| **Queue/Deque**                         | `offer(E)` / `add(E)`                | Enqueue               | Prefer `offer`        | `boolean`                 | ❌                | ✅                       | `q.offer(x)`                                     |
|                                         | `poll()` / `remove()`                | Dequeue               | `poll` is null-safe   | `E` / `null`              | ❌                | ✅                       | `q.poll()`                                       |
|                                         | `peek()` / `element()`               | Read head             | `peek` is null-safe   | `E` / `null`              | ❌                | ✅                       | `q.peek()`                                       |
|                                         | `push(E)` / `pop()`                  | Stack ops on Deque    | LIFO                  | `void` / `E`              | ❌                | ✅                       | `dq.push(x); dq.pop()`                           |
| **Map (java.util.Map)**                 | `put(K,V)` / `putIfAbsent`           | Add/replace entry     | Returns old value     | `V` (old)                 | ❌                | ✅                       | `map.put(k,v)`                                   |
|                                         | `get(K)` / `getOrDefault`            | Lookup value          | Default fallback      | `V`                       | ❌                | ✅                       | `map.getOrDefault(k,0)`                          |
|                                         | `remove(K)` / `remove(K,V)`          | Remove entry          | Conditional form      | `V`/`boolean`             | ❌                | ✅                       | `map.remove(k)`                                  |
|                                         | `containsKey/Value`                  | Membership test       | Key faster than value | `boolean`                 | ❌                | ✅                       | `map.containsKey(k)`                             |
|                                         | `forEach(BiConsumer)`                | Visit entries         | Order by impl         | `void`                    | ✅                | ❌                       | `map.forEach((k,v)->...)`                        |
|                                         | `compute/computeIfAbsent/Present`    | Atomic update         | Great for caches      | `V`                       | ✅                | ❌                       | `map.computeIfAbsent(k, key->new ArrayList<>())` |
|                                         | `merge(K,V,BiFunction)`              | Combine values        | Concise counters      | `V`                       | ✅                | ❌                       | `map.merge(k,1,Integer::sum)`                    |
|                                         | `replaceAll(BiFunction)`             | Transform values      | In-place              | `void`                    | ✅                | ❌                       | `map.replaceAll((k,v)->v+1)`                     |
| **Streams (java.util.stream)**          | `stream()` / `parallelStream()`      | Create stream         | Lazy pipeline         | `Stream<E>`               | ❌                | ✅                       | `list.stream()`                                  |
|                                         | `map(Function)`                      | Transform each        | 1–1 mapping           | `Stream<R>`               | ✅                | ❌                       | `s.map(String::length)`                          |
|                                         | `flatMap(Function)`                  | Flatten inner streams | For nested data       | `Stream<R>`               | ✅                | ❌                       | `s.flatMap(List::stream)`                        |
|                                         | `filter(Predicate)`                  | Keep matching         | Drop others           | `Stream<E>`               | ✅                | ❌                       | `s.filter(x->x>0)`                               |
|                                         | `distinct()`                         | Remove duplicates     | `equals()`-based      | `Stream<E>`               | ❌                | ✅                       | `s.distinct()`                                   |
|                                         | `sorted()` / `sorted(Comparator)`    | Sort                  | Natural or custom     | `Stream<E>`               | (Optional) ✅     | ✅                       | `s.sorted()`                                     |
|                                         | `peek(Consumer)`                     | Side-effect tap       | Don’t rely for logic  | `Stream<E>`               | ✅                | ❌                       | `s.peek(System.out::println)`                    |
|                                         | `limit/skip(long)`                   | Truncate/offset       | Short-circuit ops     | `Stream<E>`               | ❌                | ✅                       | `s.limit(10)`                                    |
|                                         | `anyMatch/allMatch/noneMatch`        | Match checks          | Short-circuit         | `boolean`                 | ✅                | ❌                       | `s.anyMatch(x->x>0)`                             |
|                                         | `findFirst/findAny`                  | Get an element        | Optional result       | `Optional<E>`             | ❌                | ✅                       | `s.findFirst()`                                  |
|                                         | `min/max(Comparator)`                | Extremes              | Optional result       | `Optional<E>`             | ✅                | ❌                       | `s.min(naturalOrder())`                          |
|                                         | `count()`                            | Number of elements    | Terminal op           | `long`                    | ❌                | ✅                       | `s.count()`                                      |
|                                         | `reduce(...)`                        | Fold to one value     | Identity/accumulator  | `Optional<T>` / `T`       | ✅                | ❌                       | `s.reduce(0,Integer::sum)`                       |
|                                         | `collect(Collector)`                 | Gather results        | Use `Collectors`      | depends (e.g., `List<E>`) | ✅                | ❌                       | `s.collect(toList())`                            |
|                                         | `toArray()` / `toArray(IntFunction)` | Array from stream     | Typed with lambda     | `Object[]` / `T[]`        | (Optional) ✅     | ✅                       | `s.toArray(String[]::new)`                       |
| **Arrays (java.util.Arrays)**           | `Arrays.sort(arr)`                   | Sort array in-place   | For primitives/refs   | `void`                    | (Optional) ✅     | ✅                       | `Arrays.sort(a)`                                 |
|                                         | `Arrays.parallelSort(arr)`           | Parallel sort         | Big arrays            | `void`                    | (Optional) ✅     | ✅                       | `Arrays.parallelSort(a)`                         |
|                                         | `Arrays.binarySearch(arr,key)`       | Search sorted array   | Requires sorted       | `int` (index/`<0`)        | ❌                | ✅                       | `Arrays.binarySearch(a, x)`                      |
|                                         | `Arrays.fill(arr,val)`               | Fill array            | In-place              | `void`                    | ❌                | ✅                       | `Arrays.fill(a, 0)`                              |
|                                         | `Arrays.copyOf/Range`                | Copy array            | Resize/slice          | `T[]`                     | ❌                | ✅                       | `Arrays.copyOf(a, n)`                            |
|                                         | `Arrays.equals/deepEquals`           | Compare arrays        | Deep for nested       | `boolean`                 | ❌                | ✅                       | `Arrays.equals(a,b)`                             |
| **Collections (java.util.Collections)** | `sort(List)`                         | Sort list in-place    | Uses TimSort          | `void`                    | (Optional) ✅     | ✅                       | `Collections.sort(list)`                         |
|                                         | `reverse(List)`                      | Reverse in-place      | Mutates               | `void`                    | ❌                | ✅                       | `Collections.reverse(list)`                      |
|                                         | `shuffle(List)`                      | Random order          | Provide `Random` opt  | `void`                    | ❌                | ✅                       | `Collections.shuffle(list)`                      |
|                                         | `swap(List,i,j)`                     | Swap two items        | In-place              | `void`                    | ❌                | ✅                       | `Collections.swap(list,0,1)`                     |
|                                         | `fill(List,val)`                     | Fill list             | In-place              | `void`                    | ❌                | ✅                       | `Collections.fill(list, 0)`                      |
|                                         | `copy(dst,src)`                      | Copy elements         | dst size ≥ src        | `void`                    | ❌                | ✅                       | `Collections.copy(dst, src)`                     |
|                                         | `frequency(coll,o)`                  | Count occurrences     | `equals()`-based      | `int`                     | ❌                | ✅                       | `Collections.frequency(list,"a")`                |
|                                         | `min/max(coll,cmp?)`                 | Extremes              | Optional comparator   | `E`                       | (Optional) ✅     | ✅                       | `Collections.max(list)`                          |
|                                         | `unmodifiableList(...)`              | Read-only view        | Throws on write       | `List<E>`                 | ❌                | ✅                       | `Collections.unmodifiableList(list)`             |
|                                         | `synchronizedList(...)`              | Thread-safe wrapper   | Coarse sync           | `List<E>`                 | ❌                | ✅                       | `Collections.synchronizedList(list)`             |

Quick Takeaways
- **Needs Lambda:** anything that takes a functional interface (`Predicate`, `Function`, `Consumer`, `Comparator`, `BiFunction`, etc.) — e.g., `stream().map/filter`, `List.removeIf`, `Map.merge`, `Map.compute*`, `replaceAll`, `forEach`, `sorted(Comparator)`.
- **Doesn’t Need Lambda:** structural and utility operations — e.g., `add`, `get`, `contains`, `Arrays.sort(arr)`, `Collections.reverse`, `Map.put/get`.
- **Returns vs Mutates:**
    - **Mutates in-place:** `List.sort`, `Collections.sort/reverse/shuffle/fill/swap`, `Arrays.sort/fill`, `List.replaceAll/removeIf` (mutates), `Map.replaceAll/compute/merge` (mutates map).    
    - **New value/container:** Streams’ `map/filter/distinct/sorted` (return new streams), `collect` (returns a new collection), `subList` (view), `Arrays.copyOf` (new array), `unmodifiableList` (new view).


---

