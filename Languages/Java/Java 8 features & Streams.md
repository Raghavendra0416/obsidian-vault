If asked about **Java 8 features** in an interview, you can answer concisely like this:

**Java 8 introduced:**
- **Lambda Expressions** for functional programming
- **Stream API** for processing collections
- **Functional Interfaces** to enable lambdas
- **Default & Static Methods** in interfaces
- **New Date and Time API** (`java.time`)
- **Optional Class** to handle null values safely

### **Java 8 features cheat sheet**:

| Feature                             | Description & Example                                                                                                                                              |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Lambda Expressions**              | Concise way to represent functional interfaces.  <br>Syntax:  <br>`(params) -> expression`  <br>Example:  <br>`numbers.forEach(n -> System.out.println(n));`       |
| **Functional Interfaces**           | Interfaces with a single abstract method. Use `@FunctionalInterface` annotation.  <br>Example:  <br>`@FunctionalInterface interface MyFunction { void execute(); } |
| **Method References**               | Shorthand for calling methods.  <br>Syntax:  <br>`Class::staticMethod`  <br>`object::instanceMethod`  <br>Example:  <br>`numbers.forEach(System.out::println);`    |
| **Streams API**                     | Declarative processing of collections.  <br>Example:  <br>`names.stream().filter(n -> n.startsWith("J")).collect(Collectors.toList());`                            |
| **Default & Static Methods**        | Interfaces can have default or static methods.  <br>Example:  <br>`interface MyInterface { default void foo() {}; static void bar() {}; }`                         |
| **Optional Class**                  | Avoids null checks.  <br>Example:  <br>`Optional<String> opt = Optional.of("Hello"); opt.ifPresent(System.out::println);`                                          |
| **Date & Time API (java.time)**     | Modern date/time handling.  <br>Example:  <br>`LocalDate date = LocalDate.now();`  <br>`LocalDateTime dt = LocalDateTime.of(2025, 7, 7, 23, 30);`                  |
| **Collectors**                      | Collect stream results.  <br>Example:  <br>`String joined = names.stream().collect(Collectors.joining(", "));`                                                     |
| **Stream Parallelism**              | Parallel processing.  <br>Example:  <br>`numbers.parallelStream().forEach(System.out::println);`                                                                   |
| **Predicate Interface**             | Used for filtering.  <br>Example:  <br>`Predicate<String> isEmpty = String::isEmpty; isEmpty.test(""); // true`                                                    |
| **Collection API Improvements**     | New methods like `removeIf`, `forEach`, `replaceAll`.  <br>Example:  <br>`list.removeIf(s -> s.isEmpty());`                                                        |
| **CompletableFuture & Concurrency** | Better async programming.  <br>Example:  <br>`CompletableFuture.supplyAsync(() -> "Hello").thenAccept(System.out::println);`                                       |

**Best Practices**
- Prefer **lambdas** and **method references** for concise, readable code.
- Use **Optional** for return types, not for fields or parameters.
- Limit **default methods** to one per interface for clarity.
- Use **streams** for data processing but avoid overusing parallel streams unless performance is measured

#### **Common Syntax Examples**

 -Lambda Expression 
	(x, y) -> x + y

 -Functional Interface 
	@FunctionalInterface interface Converter<F, T> { 
		T convert(F from); 
		}

 -Method Reference 
	String::toUpperCase

 -Stream Example 
	List<-String> filtered = list.stream() 
		.filter(s -> s.length() > 3) 
		.collect(Collectors.toList());

- Optional Example 
Optional<-String> name = Optional.ofNullable(getName()); 
name.ifPresent(System.out::println);

- Date and Time API 
LocalDate today = LocalDate.now(); 
LocalDateTime now = LocalDateTime.now();

---
### Streams:
**Stream** is a sequence of elements supporting sequential and parallel aggregate operations. It’s part of the **java.util.stream** package introduced in Java 8 to bring a functional‑style programming model to processing collections of data.

#### 1. Key Characteristics
1. **No Storage**  
    A stream doesn’t store data; it carries values from a source (e.g., a `Collection`, array, IO channel, or generator).

2. **Functional in Nature**  
    Operations on a stream produce a result but do not mutate its underlying data source. You pass _functions_ (lambdas or method references) to describe what to do.

3. **Lazy Evaluation**  
    Intermediate operations (like `filter`, `map`) are _deferred_ until a terminal operation (like `collect`, `forEach`, `reduce`) is invoked—allowing the runtime to optimize the entire pipeline.

4. **Possibly Unbounded**  
    Streams can be finite (from a list) or infinite (e.g., `Stream.generate(...)` or `Stream.iterate(...)`).

5. **Consumable**  
    Once a terminal operation has been applied, the stream is considered consumed and can no longer be used.

#### 2. Stream Pipeline

A typical stream usage follows three stages:

1. **Source**  
    Create a stream from a data source:
    
    ```java
    List<String> words = Arrays.asList("apple","banana","cherry");
    Stream<String> wordStream = words.stream();
    ```
    
2. **Intermediate Operations** (return another Stream)
    
    - **`filter(Predicate<T>)`**: keep only elements matching a condition
    - **`map(Function<T,R>)`**: transform each element
    - **`sorted()`**: sort elements
    - **`distinct()`**: remove duplicates
    - **`limit(long maxSize)`** / **`skip(long n)`**: truncate or skip elements
    
    _Chaining example:_
    
    ```java
    Stream<String> longWords = wordStream
        .filter(s -> s.length() > 5)
        .map(String::toUpperCase);
    ```
    
3. **Terminal Operations** (produce a result or side‑effect)
    
    - **`collect(Collector<T,A,R>)`**: gather elements into a `List`, `Set`, `Map`, etc.    
    - **`forEach(Consumer<T>)`**: perform an action for each element
    - **`reduce(BinaryOperator<T>)`**: combine elements into one
    - **`count()`**, **`anyMatch()`**, **`allMatch()`**, etc.
    
    _Example:_
    
    ```java
    List<String> result = longWords.collect(Collectors.toList());
    long count = words.stream().filter(s -> s.contains("a")).count();
    ```

#### 3. Parallel Streams

By simply switching to `.parallelStream()` (or calling `.parallel()` on an existing stream), Java will attempt to split the work across multiple threads:

```java
List<Integer> numbers = IntStream.range(1, 1_000_000)
     .boxed()
     .parallel()
     .filter(n -> n % 2 == 0)
     .collect(Collectors.toList());
```

⚠️ Parallel streams can improve performance for large datasets _but_ can also introduce thread‑safety and ordering concerns. Always benchmark and profile.

#### 4. Why Use Streams?

- **Conciseness**: pipelines reduce boilerplate loops.
- **Readability**: declarative style describes _what_ you want, not _how_ to iterate.
- **Composability**: you can mix and match intermediate ops.
- **Lazy & Optimized**: the JVM can fuse operations or short‑circuit when possible.
- **Parallelization**: easily switch to parallel processing.

#### 5. Simple Example

Putting it all together—find the sum of the squares of even numbers in a list:

```java
List<Integer> nums = Arrays.asList(1,2,3,4,5,6);

int sum = nums.stream()                   // source
    .filter(n -> n % 2 == 0)             // keep even
    .map(n -> n * n)                     // square
    .reduce(0, Integer::sum);            // sum up

System.out.println(sum);  // prints 56 (4 + 16 + 36)
```


#### Most important features:

| Feature                                    | Description & Example                                                                                                                                                                   |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Lambda Expressions**                     | Enables concise representation of anonymous functions for functional programming.  <br>Example:  <br>`(x, y) -> x + y`                                                                  |
| **Stream API**                             | Provides a functional approach to process collections with operations like filter, map, and reduce.  <br>Example:  <br>`list.stream().filter(x -> x > 0).collect(Collectors.toList());` |
| **Functional Interfaces**                  | Interfaces with a single abstract method, used as the target for lambda expressions.  <br>Example:  <br>`@FunctionalInterface interface MyFunc { void run(); }`                         |
| **Default & Static Methods in Interfaces** | Allows interfaces to have default and static methods without breaking existing implementations.  <br>Example:  <br>`interface A { default void foo() {}; static void bar() {}; }`       |
| **Date and Time API**                      | Modern, immutable date and time handling via `java.time` package.  <br>Example:  <br>`LocalDate.now()`                                                                                  |
| **Optional Class**                         | Helps avoid null pointer exceptions by representing optional values.  <br>Example:  <br>`Optional.of("value")`                                                                          |

