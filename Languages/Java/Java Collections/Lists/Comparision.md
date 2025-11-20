
#### Java List Interface Implementations: Feature Comparison

| Collection Type | Default Capacity  | Initial Capacity  | Allow Duplicates | Allow Null Values | Insertion Order       | Sorted Order | Random Access | Synchronization      |
| --------------- | ----------------- | ----------------- | ---------------- | ----------------- | --------------------- | ------------ | ------------- | -------------------- |
| Vector          | 10                | User specified    | Yes              | Yes               | Yes (insertion order) | No           | Yes           | Yes (thread-safe)    |
| ArrayList       | 10                | User specified    | Yes              | Yes               | Yes (insertion order) | No           | Yes           | No (not thread-safe) |
| Stack           | 10                | User specified    | Yes              | Yes               | Yes (LIFO order)      | No           | Yes           | Yes (thread-safe)    |
| LinkedList      | N/A (linked list) | N/A (linked list) | Yes              | Yes               | Yes (insertion order) | No           | No            | No (not thread-safe) |



#### Java Arrays vs Java Lists – Feature Comparison

| **Feature / Operation**                        | **Java Array** (`String[]`, `int[]`) | **Java List** (`List<String>`, `List<Integer>`)         |
| ---------------------------------------------- | ------------------------------------ | ------------------------------------------------------- |
| **Fixed Size After Creation**                  | ✅ Yes                                | ❌ No (Resizable)                                        |
| **Add/Remove Elements After Creation**         | ❌ No (Only overwrite values)         | ✅ Yes (`add()`, `remove()`)                             |
| **Access/Modify by Index**                     | ✅ Yes (`arr[0] = value`)             | ✅ Yes (`list.set(0, value)`)                            |
| **Store Primitive Types Directly (int, char)** | ✅ Yes (`int[]`, `char[]`)            | ❌ No (Use wrapper types like `Integer`, `Character`)    |
| **Generic Support (e.g., `<String>`)**         | ❌ No                                 | ✅ Yes                                                   |
| **Multidimensional Support**                   | ✅ Yes (`int[][]`)                    | 🔶 Indirect (`List<List<>>`) – more complex             |
| **Length or Size**                             | ✅ `.length`                          | ✅ `.size()`                                             |
| **Enhanced For-Loop Support**                  | ✅ Yes                                | ✅ Yes                                                   |
| **Sorting (using utilities)**                  | ✅ `Arrays.sort(array)`               | ✅ `Collections.sort(list)`                              |
| **Search (contains, indexOf, etc.)**           | ❌ No (manual logic needed)           | ✅ Yes (`contains()`, `indexOf()`)                       |
| **Conversion to Collection Types**             | ❌ Manual conversion needed           | ✅ Already a collection                                  |
| **Thread-safe by default**                     | ❌ No                                 | ❌ No (can use `Collections.synchronizedList()`)         |
| **Immutable Option Available**                 | ❌ No (not by default)                | ✅ Yes (`List.of()` or `Collections.unmodifiableList()`) |
| **Performance (for fixed size)**               | ✅ Fast                               | 🔶 Slightly slower due to dynamic nature                |

#### Java Arrays vs Vector – Comparison

Here’s a **clear comparison between `List` and `Vector`** in table format:

|Feature|`List` (Interface)|`Vector` (Class)|
|---|---|---|
|**Type**|Interface|Concrete class|
|**Part of**|`java.util` package, part of Collection framework|`java.util` package, part of Collection framework|
|**Can be instantiated?**|❌ No, it's an interface|✅ Yes, can create object directly|
|**Implementations**|`ArrayList`, `LinkedList`, `Vector`, etc.|A specific implementation of `List`|
|**Thread Safety**|Depends on implementation (e.g., ArrayList is not)|✅ Thread-safe (methods are synchronized)|
|**Performance**|Faster (non-synchronized versions like ArrayList)|Slower due to synchronization|
|**Use in New Code**|Recommended to use `List` with required implementation|❌ Not recommended (considered legacy in most cases)|
|**Growable?**|Depends on implementation|✅ Yes, grows by doubling its size when full|
|**Access Type**|Index-based (via implementations like ArrayList)|Index-based|
|**Legacy?**|Modern interface|Considered legacy; introduced in Java 1.0|
