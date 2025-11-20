Lambda expressions are a powerful feature introduced in Java 8 that allow you to write more concise, functional-style code. They represent anonymous functions - functions without a name that can be passed around as values.

A **lambda in Java** is essentially a method body, so you **can use `for`, `if-else`, `while`**, etc., inside it — **as long as you use curly braces `{}`** and follow proper syntax.

FYI, If lambda expression is used, a functional interface should be created(outside of class) and a variable with that functional interface should be created before lambda expression for storing the value of lambda and execute it.
If we need to return nothing use consumer by importing it.

#### What is a Lambda Expression?

A lambda expression is essentially an anonymous or unnamed method that doesn't execute on its own but is used to implement a method defined by a functional interface. Think of it as a short block of code that takes parameters and returns a value, similar to methods but without needing a name.

#### Basic Syntax
The fundamental syntax of a lambda expression is:

`(parameter list) -> lambda body`

- The `->` operator is called the arrow operator or lambda operator. Here are the basic forms:
- **No parameters:** `() -> expression`
- **Single parameter:** `parameter -> expression` or `(parameter) -> expression`
- **Multiple parameters:** `(param1, param2) -> expression`

#### Lambda Body Types

Lambda expressions can have two types of bodies:

**1. Expression Body (Single Expression)**

`() -> 3.1415 (x) -> x * 2 (a, b) -> a + b`

**2. Block Body (Multiple Statements)**

`() -> {     double pi = 3.1415;    return pi; }`

For block bodies, you need curly braces and semicolons, and must use explicit `return` statements when returning values.

#### Key Characteristics
Lambda expressions have several important characteristics:

- **Optional type declaration:** The compiler can infer parameter types
- **Optional parentheses:** Single parameters don't need parentheses
- **Optional curly braces:** Single statements don't need braces
- **Optional return keyword:** Single expressions automatically return values
#### Functional Interfaces

Lambda expressions work with functional interfaces - interfaces that have exactly one abstract method. Common functional interfaces include:

- `Consumer<T>`: Takes one parameter, returns nothing
- `Function<T,R>`: Takes one parameter, returns a value
- `Predicate<T>`: Takes one parameter, returns Boolean

Benefits of Lambda Expressions
- **Concise code:** Reduces boilerplate code significantly
- **Functional programming:** Enables functional programming paradigms in Java
- **Readability:** Makes code more readable and expressive
- **Collection operations:** Simplifies operations on collections like filtering, mapping, and iterating

Common Use Cases
Lambda expressions are commonly used with:
- Collection operations (`forEach`, `filter`, `map`)
- Event handling in GUI applications
- Functional interfaces like `Runnable`, `Callable`
- Stream API operations
- Custom functional interfaces

---
#### Syntax:

if condition:

```java
(parameter) -> {
    if (condition) {
        // logic
    } else {
        // logic
    }
}
```

for loop:
- `forEach()` doesn't return anything (`void`).

```java
list.forEach(item -> System.out.println(item));
```

Filter:
- The **filter** operation in Java uses the `Stream.filter()` method with lambda expressions to filter elements based on a condition. Stream should be used for filter to work. `filter()` helps keep the **condition logic separate** from the **action logic**.

```java
stream.filter(predicate) -> filtered_stream
```

Lambda expressions can only be assigned like this:

```java
`fruits out = () -> { logic; return result; };`
```

Remove If:
- `removeIf` goes through the list, applying that rule to every single element.

```Java
ArrayListName.removeIf(n -> n % 2 == 0); // Will only return the elements which are divisible by 2.
```

Replace All(operator):
- This method is specific to List and replaces each element with the result of applying a function (the lambda) to it. It modifies the list in-place.

```Java
List<String> names = new ArrayList<>(Arrays.asList("Alice", "Bob"));
names.replaceAll(name -> name.toUpperCase()); // names is now ["ALICE", "BOB"]
```


ComputeIfAbsent(key, function)
- Used in only Maps
- If the key isn't already in the map, it computes a value using the lambda, adds the key-value pair, and returns the new value. This is great for initializing values.

```Java
Map<String, List<String>> emails = new HashMap<>();
// If "work" key doesn't exist, create a new ArrayList for it
emails.computeIfAbsent("work", k -> new ArrayList<>()).add("ceo@example.com");
```


Quick Comparison:

|Method|What It Does|Modifies Original?|Primary Use Case|
|---|---|---|---|
|**`removeIf`**|Removes elements that match a predicate.|**Yes**|In-place filtering.|
|**`filter`**|Keeps elements that match a predicate.|**No**|Creating a new, filtered stream.|
|**`forEach`**|Performs an action for each element.|**Maybe**¹|Side effects (e.g., printing).|
|**`replaceAll`**|Replaces each element with a new value.|**Yes**|In-place transformation.|

---

#### Why @FunctionalInterface is needed when assigning value from Lambda Expression?

It helps the **compiler validate** that the interface has only **one abstract method**. If someone later tries to add another abstract method, the compiler will throw an error. 

`@FunctionalInterface` annotation in Java has **only one purpose**:
It **tells the compiler** to **enforce the rule** that the interface must have **exactly one abstract method**.

Functional interface allows Default methods, Static methods, Object methods.

If you try to use a lambda expression with an functional interface or without functional interface that has **more than one abstract method**, the **compiler will throw an error**

`@FunctionalInterface` does **not change how lambdas work**. Instead, it acts as a **compile-time safeguard** for the **interface itself**, not its usage.

Why Lambda Needs Assignment to Functional Interface?
  Lambda expressions **cannot exist on their own**. They must be:
1. **Assigned to a variable** with a functional interface type, OR
2. **Passed as a parameter** to a method that expects a functional interface

Here’s the **difference**:

| Scenario                                           | Without `@FunctionalInterface`                                       | With `@FunctionalInterface`                              |
| -------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------- |
| Interface has **1 abstract method**                | ✅ Valid                                                              | ✅ Valid                                                  |
| Interface has **2+ abstract methods**              | ✅ Compiles, but can’t be used in lambda (error at lambda usage site) | ❌ Compile-time error immediately at interface definition |
| Someone **accidentally adds another method** later | ❌ No warning (until lambda is used)                                  | ✅ Immediate compiler error                               |

##### Example:

##### Without `@FunctionalInterface`

```java
interface Operation {
    int compute(int a, int b);
    // Oops! someone adds another method
    int anotherOne(); // No compile error here!
}
```

Compiles fine here, but…

```java
Operation op = (a, b) -> a + b; // ❌ ERROR: Invalid lambda: multiple abstract methods
```

The error comes **only when you try to use the interface in a lambda.**

##### With `@FunctionalInterface`

```java
@FunctionalInterface
interface Operation {
    int compute(int a, int b);
    // ❌ ERROR right here: Multiple non-overridden abstract methods
    int anotherOne();
}
```

Here, the compiler catches the mistake **immediately**, at the **interface level**.

---
#### Functional Interfaces for Lambdas:
- A lambda expression provides the implementation for that single abstract method. Java has many built-in functional interfaces in the `java.util.function` package, but you can also create your own.

Common built-in examples include:
- Runnable
- Consumer<"Type">
- Predicate<"Type">
- Function<T, R>

- `Runnable`: Represents an action that takes no arguments and returns no result.
    - Method: `void run()`
    - Lambda: `() -> System.out.println("Action!")`
- `Consumer<T>`: Represents an operation that accepts a single input argument and returns no result.
    - Method: `void accept(T t)`
    - Lambda: `s -> System.out.println(s)`

- `Predicate<T>`: Represents a predicate (a Boolean-valued function) of one argument. Often used for filtering.
    - Method: `boolean test(T t)`
    - Lambda: `x -> x > 10`

- `Function<T, R>`: Represents a function that accepts one argument and produces a result.
    - Method: `R apply(T t)`
    - Lambda: `str -> str.length()`

Example:

```Java
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;

public class FunctionalInterfacesExample {

    public static void main(String[] args) {

        // 1. Runnable: A task that runs without input or output ⚙️
        Runnable task = () -> System.out.println("I'm a task running in a thread.");
        new Thread(task).start();

        // 2. Predicate: Tests an input and returns true or false ✅
        Predicate<Integer> isPositive = number -> number > 0;

        // 3. Function: Takes an input and returns a different output TRANSFORM
        Function<Integer, String> numberToText = number -> "The number is " + number;

        // 4. Consumer: Takes an input and does something with it (no return) 📥
        Consumer<String> printer = message -> System.out.println(message);

        
        // --- Let's use them on some data ---
        int myNumber = 42;

        if (isPositive.test(myNumber)) {
            String textResult = numberToText.apply(myNumber);
            printer.accept(textResult);
        }
    }
}
```

Output:
```Text
I'm a task running in a thread. 
The number is 42
```


---
#### If we can use interface name to assign the value of lambda then what is the use of Runnable, Consumer<"Type">, Predicate<"Type">, Function<T, R>?
Ans:

What is a Functional Interface?
A **functional interface** is an interface with **only one abstract method**.  
It’s used to represent a **single action** or **operation**, and it works naturally with **lambda expressions**.
Example:

```java
@FunctionalInterface
interface MyPrinter {
    void print(String s);
}
```

You can use a lambda with it:

```java
MyPrinter printer = (s) -> System.out.println(s);
```

**So yes — you _can_ create your own interfaces**.


Then Why Do We Need `Runnable`, `Consumer<T>`, etc.?

Because Java **already provides** many **standard functional interfaces** in the `java.util.function` package.

These are **ready-to-use**, and they **cover most common tasks**.  
This saves you from writing your own interface every time.


Let’s Look at Each One
1. Runnable`
	- Represents: **An action that takes no input and returns nothing.**
	- Commonly used for threads.

```java
Runnable task = () -> System.out.println("Running!");
new Thread(task).start();
```
Instead of writing:
```java
@FunctionalInterface
interface MyTask {
    void run();
}
```
Just use `Runnable`.

2. `Consumer<T>`
	- Represents: A function that **takes one argument** and **returns nothing**.
	- Think of it as “**consumes**” a value.

```java
Consumer<String> printer = s -> System.out.println("Hello, " + s);
printer.accept("World");  // Output: Hello, World
```
Instead of writing:
```java
@FunctionalInterface
interface StringConsumer {
    void accept(String s);
}
```
Just use `Consumer<T>`.

3. `Predicate<T>`
	- Represents: A function that **takes one argument** and **returns a boolean**.
	- Think of it as a **condition checker**.

```java
Predicate<Integer> isEven = i -> i % 2 == 0;
System.out.println(isEven.test(10));  // true
```
Instead of:
```java
@FunctionalInterface
interface MyChecker {
    boolean check(int i);
}
```
Use `Predicate<T>`.

4. `Function<T, R>`
	- Represents: A function that **takes one input (T)** and **returns a result (R)**.

```java
Function<String, Integer> stringLength = s -> s.length();
System.out.println(stringLength.apply("Hello"));  // 5
```
Instead of:
```java
@FunctionalInterface
interface StringToInt {
    int convert(String s);
}
```
Use `Function<T, R>`.

Why Use Built-In Interfaces?

Here’s why Java gives us these:

| Advantage            | Why it matters                                                     |
| -------------------- | ------------------------------------------------------------------ |
| **Reusability**      | Use the same interfaces everywhere — no need to redefine           |
| **Interoperability** | Works well with Java libraries, APIs, streams, collections         |
| **Readability**      | Other developers know what `Predicate<T>` or `Function<T,R>` means |
|  **Testability**     | Easy to mock, test, and compose                                    |

Summary
Yes, you can define your own functional interfaces like `StringProcess`. But:

|If you want to...|Use this built-in interface|
|---|---|
|Run a task|`Runnable`|
|Take a value and return nothing|`Consumer<T>`|
|Check a condition|`Predicate<T>`|
|Convert one type to another|`Function<T, R>`|

 **Think of built-in functional interfaces as "universal tools" for lambda expressions** — just like using standard screwdrivers instead of making your own each time!




##### **Analogy: Java Functional Interfaces as Tools in a Toolbox**
Imagine you're a **mechanic** (programmer), and Java gives you a **toolbox** full of commonly used tools (functional interfaces). You can build your own tools if needed, but most of the time, the ones in the toolbox are **ready to use and perfectly fit**.

```
Java Functional Interface Toolbox
 ┌────────────────────┐
 │      TOOLBOX       │
 └────────────────────┘
        |
        v
┌──────────────────────────┐
│  🔧 Runnable             │  → Task that just "does something"
│  (no input, no output)   │  e.g., Starting a thread
└──────────────────────────┘

┌──────────────────────────┐
│  📦 Consumer<T>          │  → Takes a value, performs action (no return)
│  (input only)            │  e.g., Printing or logging
└──────────────────────────┘

┌──────────────────────────┐
│  ✅ Predicate<T>         │  → Takes a value, returns true/false
│  (input → boolean)       │  e.g., Check if a number is even
└──────────────────────────┘

┌──────────────────────────┐
│  🔁 Function<T, R>       │  → Takes input, returns a result
│  (input → output)        │  e.g., Convert String to Integer
└──────────────────────────┘
```


Visual Cheat Sheet: Signatures

|Interface|Input|Output|Purpose|
|---|---|---|---|
|`Runnable`|none|`void`|Do something (e.g., task)|
|`Consumer<T>`|`T`|`void`|Accept and use a value|
|`Predicate<T>`|`T`|`boolean`|Check a condition|
|`Function<T,R>`|`T`|`R`|Transform one type to another|

Example Mapping

|Real-world action|Functional Interface|Lambda Example|
|---|---|---|
|Start a background job|`Runnable`|`() -> doWork()`|
|Print a value|`Consumer<String>`|`s -> System.out.println(s)`|
|Check if age > 18|`Predicate<Integer>`|`age -> age > 18`|
|Convert Celsius to Fahrenheit|`Function<Double, Double>`|`c -> c * 9/5 + 32`|

 Summary
- Java **gives you a toolbox** of ready-to-use interfaces.
- You can always build custom tools (**your own interfaces**), but using **standard tools is faster and easier**.
- These standard interfaces help your code stay **clean, readable, and compatible** with Java’s powerful features like **Streams**, **Collections**, and **Concurrency APIs**.


----

#### What is Consumer? and can we use this instead of Functional Interface?  

**Consumer** is a **built-in functional interface** in Java, introduced in Java 8 as part of the `java.util.function` package. It represents an operation that accepts a single input argument and returns no result (void). Think of it as a function that "consumes" or processes data without producing a return value.

##### Do they Work the Same way?
**Not exactly the same, but Consumer IS a functional interface.** Think of it this way:
- **Functional Interface** = The general concept (any interface with one method)
- **Consumer** = A specific, ready-made functional interface provided by Java

It's like asking "Do vehicles and cars work the same way?" - a car IS a vehicle, but not all vehicles are cars.

##### Can Consumer Replace Custom Functional Interfaces?
**Sometimes yes, sometimes no.** Consumer works when you need to:
- Take one input
- Return nothing (void)
- Perform some action

But you **cannot** use Consumer when you need to:
- Return a value
- Take multiple parameters
- Have meaningful method names

##### Quick Decision Guide

|Your Need|Use This|
|---|---|
|Process data, no return value|**Consumer**|
|Return a value|**Custom Functional Interface**|
|Multiple parameters|**Custom Functional Interface**|
|Meaningful method names|**Custom Functional Interface**|
|Simple processing/printing|**Consumer**|

##### Comparison

|Aspect|Custom Functional Interface|Consumer Interface|
|---|---|---|
|**Definition**|You create your own|Pre-built by Java|
|**Flexibility**|Custom method names and contracts|Fixed `accept()` method|
|**Reusability**|Specific to your use case|Universal for "consume and return nothing" operations|
|**Import Required**|No (if in same package)|Yes: `import java.util.function.Consumer;`|

##### Bottom Line
- **Consumer is perfect** for simple "do something with data" operations
- **Custom functional interfaces** are needed when Consumer's limitations don't fit your needs
- **In real projects**, you'll use both depending on the situation
- **Consumer works with any data type** through generics: `Consumer<String>`, `Consumer<Integer>`, `Consumer<YourClass>`

**Rule of thumb**: If you just need to process/print/save data without returning anything, Consumer is your friend. If you need more complex operations, create your own functional interface.

---
#### Example:

This is how lambda executes:
1st it will check if there functional interface with the name that we have used in main method and will create a method while using lambda logic and the method  name will be same as in functional interface. Once created it will be ready to execute the logic, whenever the method is called. and the method can be called using variable we have declared earlier.

The local variable and the variables in lambda expression should be different.

```java
@FunctionalInterface
interface StringProcessor {
    void process(String str);  // No implementation - just contract
}

public class Main {
    public static void main(String[] args) {
        String s = "World";
        
        // Step 1: Lambda created and stored
        // The lambda body becomes the implementation of process()
        StringProcessor pro = (str) -> {
            System.out.println("Hello" + s);
        };
        
        // Step 2: Method call triggers lambda execution
        // Java knows to run the lambda body when process() is called
        pro.process(s);  // Output: HelloWorld
    }
}
```


What "Lambda Created and Stored" Actually Means:
**"Created" means:**
- The compiler converts your lambda expression into bytecode
- An object that implements the `StringProcessor` interface is created
- The lambda body is compiled but **not executed**

**"Stored" means:**
- The lambda object is assigned to the variable `pro`
- The variable `pro` now holds a reference to this lambda implementation

What If Lambda Is "Created But Not Stored" Means:
If you write a lambda without storing it in a variable, it becomes **useless**.

```Java
// This creates a lambda but doesn't store it anywhere 
(str) -> {System.out.println("Hello" + str);}; // ❌ Compilation ERROR! 

// You can't use it because there's no way to reference it 
// It's like creating a car but throwing away the keys
```

**What happens:** The compiler will give you an error because the lambda has no target type and cannot be used.

Behind the Scenes: How It Actually Works

**Step 1: Compiler Translation**
When you write:

```java
`StringProcessor pro = (str) -> {System.out.println("Hello" + s);};`
```

The compiler essentially converts it to something like:

```java
`StringProcessor pro = new StringProcessor() {  
@Override    
public void process(String str) {System.out.println("Hello" + s);  // ← Lambda body becomes method body    
} 
};`
```

**Step 2: Method Call Resolution**
When you call:

```java
`pro.process(s);`
```

Java knows to execute the lambda body because:
1. `pro` holds a reference to the lambda implementation
2. The lambda body **becomes** the implementation of the `process()` method
3. Calling `process()` executes the lambda body

![[Pasted image 20250709151749.png]]

#### Decision Guide

|Lambda Function Characteristics|Solution|
|---|---|
|**Same parameters and return type**|Use same functional interface|
|**Different signatures**|Use different functional interfaces|
|**Common patterns** (void, boolean, transformation)|Use built-in interfaces (`Consumer`, `Predicate`, `Function`)|
|**Complex/specific operations**|Create custom functional interfaces|

Best Practices
1. **Reuse built-in interfaces** when possible (`Consumer`, `Function`, `Predicate`, `Supplier`)
2. **Create custom interfaces** only when built-in ones don't fit
3. **Use meaningful names** for custom functional interfaces
4. **Group related lambdas** that share the same interface

Summary
- **Same signature** → Same functional interface 
- **Different signatures** → Different functional interfaces 
- **Consider built-in interfaces** before creating custom ones 
- **One class can have multiple lambdas** using various functional interfaces 

---

#### why functional interface is not used? in what situation do we need use functional interface?

Functional interfaces are widely used in modern Java, but they aren't the solution for every problem. They are specialized tools for a specific job.

When Not to Use a Functional Interface
You should use a regular class or interface instead of a functional interface in these situations:
- When you need more than one action 
	A functional interface can only have one abstract method.2 If you need an object to perform multiple, distinct actions, you need a full interface or class. For example, the List interface has add(), get(), remove(), etc.3 It cannot be a functional interface.

- When an object needs to hold data (state) 
    Functional interfaces are primarily about behavior, not data.4 If you need to create an object that stores information (like a User object with a name and email), you should use a class with fields (instance variables).

- When the logic is very complex
	If the implementation of the single method is very long and complicated, a lambda can become hard to read. In this case, it's often cleaner to use a standard class or a private method to give the complex logic a clear name.
    
When to Use a Functional Interface
You absolutely need to use a functional interface whenever you want to treat a piece of **code as data**—that is, to pass a behavior as an argument to a method, return it from a method, or store it in a variable.
- Passing Behavior into Methods 
	This is the most common and powerful use case. You provide a piece of code (as a lambda) that a method will execute.
- **Stream API**: The entire Stream API is built on this. You pass behavior to methods like `filter` (`Predicate`), `map` (`Function`), and `forEach` (`Consumer`).

```Java
List<String> names = List.of("Arun", "Priya", "Amit");
names.stream()
     .filter(name -> name.startsWith("A")) // Pass a filtering behavior
     .forEach(name -> System.out.println(name)); // Pass a printing behavior
```

- **Concurrency**: To define a task for a thread to run.

```Java
Runnable task = () -> System.out.println("Running task...");
new Thread(task).start(); // Pass the task behavior to the Thread
```


- Defining Simple, In-place Actions 
	They are perfect for short, simple actions where creating a whole new class would be overkill. A great example is providing a custom sorting logic.

```Java
// Before lambdas, you needed an anonymous inner class (very verbose)
// names.sort(new Comparator<String>() { ... });

// With a lambda, it's clean and concise
names.sort((s1, s2) -> s1.compareToIgnoreCase(s2)); // Pass sorting behavior
```


---



Lambda expressions in Java are primarily used to provide a short and clear way to implement a **functional interface** (an interface with only one abstract method). Think of them as a quick, inline way to write a single-purpose function right where you need it.


What is a Lambda Expression? (For a Beginner)
Imagine you have a machine that can only do **one thing**. For example, a machine that only toasts bread.
- **The Old Way (Anonymous Class):** Before lambdas, to tell your program what to do, you had to build a whole blueprint for a "Toaster" class, even if you were only going to use it once. It's like writing a detailed instruction manual just to make one piece of toast.
- **The New Way (Lambda Expression):** A lambda expression is like shouting a quick command: `(bread) -> make it toast!`. It's a short, direct instruction without all the ceremony.


In Java, a lambda expression has three parts:
1. **Parameters:** `(bread)` - The input it takes.
2. **Arrow Token:** `->` - Separates the input from the action.
3. **Body:** `make it toast!` - The action to perform.



###### **Common Uses in a Project (With Examples)**
Here are the most common places you'll use lambda expressions in a real Java project.
###### 1. Iterating Over Collections
	This is one of the most frequent uses. The `forEach` method on lists, sets, and maps accepts a lambda.

**Scenario:** You have a list of names and you want to print each one.
**Before Lambdas (The Old Way):**


```Java
List<String> names = List.of("Alice", "Bob", "Charlie");
for (String name : names) {
    System.out.println(name);
}
```

**With Lambdas (The Modern Way):**

```Java
List<String> names = List.of("Alice", "Bob", "Charlie");
names.forEach(name -> System.out.println(name));
```

Here, `name -> System.out.println(name)` is the lambda expression. It says, "for each `name` in the list, print it."
##### 2. Sorting Collections
When you need to sort objects, you must tell Java _how_ to compare them. A `Comparator` is a functional interface for this.

**Scenario:** You have a list of `Product` objects and want to sort them by price from lowest to highest.

```Java
class Product {
    String name;
    double price;
    // constructor, getters...
}

List<Product> products = ... // list of products

// Sort using a lambda expression
products.sort((p1, p2) -> Double.compare(p1.getPrice(), p2.getPrice()));
```

The lambda `(p1, p2) -> Double.compare(p1.getPrice(), p2.getPrice())` provides the logic to compare two products (`p1`, `p2`) based on their price.

##### 3. Event Handling (like Button Clicks)
In desktop or UI applications, you need to define what happens when a user interacts with something, like clicking a button.

**Scenario:** Define the action for a button click in a JavaFX or Swing application.
```Java
// Assuming 'myButton' is a Button object
myButton.setOnAction(event -> {
    System.out.println("Button was clicked!");
    // You can add more logic here
});
```

The lambda `event -> { ... }` is the action that runs when the button-click event occurs.

##### 4. Using the Stream API
The Stream API is a powerful feature for processing collections of data. It relies heavily on lambda expressions for its operations like `filter`, `map`, and `reduce`.

**Scenario:** From a list of employees, you want to get the names of all employees who work in the "Engineering" department.

```Java
List<Employee> employees = ... // list of employees

List<String> engineerNames = employees.stream()
    .filter(emp -> "Engineering".equals(emp.getDepartment())) // Keep only engineers
    .map(emp -> emp.getName()) // Transform Employee object to just their name
    .collect(Collectors.toList()); // Collect the names into a new list
```

- `filter(emp -> "Engineering".equals(emp.getDepartment()))`: The lambda here acts as a test. It returns `true` for employees in the Engineering department, keeping them in the stream.
- `map(emp -> emp.getName())`: This lambda transforms each `Employee` object into a `String` (their name).

#### A Real-Life Project Example 

Let's put it all together in a simplified e-commerce application scenario.

**Task:** You're working on an online store. You need to find all books that cost less than $15, apply a 10% discount, and get a list of their titles for a "Bargain Books" promotion.

**1. The `Book` Class:**
```Java
class Book {
    private String title;
    private double price;

    // Constructor, getters, setters...
    public String getTitle() { return title; }
    public double getPrice() { return price; }
    public void setPrice(double price) { this.price = price; }
}
```

**2. The Logic Using Lambdas and Streams:**
```Java
// 1. You have a list of all books in your inventory
List<Book> inventory = getBooksFromDatabase();

// 2. Use streams and lambdas to process the list
List<String> bargainBookTitles = inventory.stream()
    // a. Find books cheaper than $15
    .filter(book -> book.getPrice() < 15.00)

    // b. Apply a 10% discount to each of those books
    .peek(book -> book.setPrice(book.getPrice() * 0.90))

    // c. Get the title of each discounted book
    .map(book -> book.getTitle())

    // d. Collect the titles into a final list
    .collect(Collectors.toList());

// 3. Display the results
System.out.println("Bargain Books Promotion:");
bargainBookTitles.forEach(title -> System.out.println("- " + title));
```

