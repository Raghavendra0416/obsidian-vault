### Basics:

#### What is Java?

- Java is **high-level, object-oriented, and general-purpose** programming language.
- Mostly used for mobile apps and enterprise software to big data and server-side technologies.
- principle of Java **"Write Once, Run Anywhere" (WORA)**, which makes it platform-independent. (How given in below point).
- When a Java program is compiled, it's not converted into machine-specific code but into an intermediate format called **bytecode**. This bytecode can run on any device that has a Java Virtual Machine (JVM).
- Java provides **Classes, Objects, Oops concepts**, and some other features.

#### What are the Oops Concepts?

- Oops concept is based on object.
- Instead of writing procedures that operate on data, OOP is about creating objects that contain both the data (in the form of fields or attributes) and the methods (code or behavior) that operate on that data.
- This approach simplifies software development and makes code more maintainable, reusable, and easier to debug.

Core Concepts of Oops:
**Class:**  A class is a blueprint or template for creating objects.
Example: a `Car` class would define the general properties (like color, model) and behaviors (like drive, brake) that all cars have

**Object:**   An object is a real-world entity and an instance of a class.
Example: If `Car` is the class, then a specific "Volvo" or "Toyota" would be an object created from that class, with its own specific states and behaviors

Principles of Oops:
1. **Inheritance**
2. **Abstraction**
3. **Encapsulation**
4. **Polymorphism**


#### Explain the Principles of Oops?

[[Inheritance, Encapsulation, Abstraction, Polymorphism]]
1. Inheritance: 
	- where a a subclass or child class acquires the properties and behaviors of an a superclass or parent class which allows code reusability.
	- Inheritance can be achieved using `extends`, `super`.
	- `extends` is used to inherit from a superclass.
	- `super` is used to call superclass methods or constructors or superclass fields.

2. **Abstraction**:
	- Abstraction means hiding complex implementation details and showing only the essential features to the user.
	- abstraction is achieved using `abstract` (classes and methods) and `interfaces`.
	-  **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
	- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).
	- **Interface:** Only provide methods not method bodies. who ever  implements these interface has to implement all methods. and it uses implements keyword.
3. **Encapsulation**:
	- It is mechanism of **wrapping of variables, methods** together as a single unit, i.e class.
	- key part of encapsulation is _data hiding_, where the internal state of an object is protected from outside access.
	- The hiding of data is done through **Public, Private, Protected and Getter & Setters methods.**
4. **Polymorphism**:
	- One thing in many forms - means the ability of an object to take on many different forms.
	- two main types of Polymorphism: 
		- **Method Overloading (Compile-time Polymorphism)**-  same method name, different parameters.
		- **Method Overriding (Run-time Polymorphism)** - using `@Override`  keyword.


#### Why do we have to use interface when we have abstraction? and why interface is created and where do we use abstraction and interface?

Abstract Class: Blue print, can only extend one abstract class, `extends` keyword , Can have constructors
Interface: Contract, implement multiple interfaces, `implements` keyword , Cannot have constructors


- They serve different purposes and solve different problems.
- **Interfaces** is to **define a contract** that different, often unrelated, classes can agree to follow.
- An abstract class, on the other hand, is primarily used to **share common code** among closely related classes.

When to Use an Abstract Class:
- **Share Code Among Closely Related Classes** : 
	- You can provide common, implemented methods and fields in the abstract class, reducing code duplication.

- **Provide a Default Implementation**: 
	- This allows you to provide default behavior to methods, that subclasses can use or override.

- **Share State with Non-`public` or Non-`final` Fields**: 
	- Abstract classes can have instance variables with any access modifier (`private`, `protected`, etc.) and can be non-final. Interface fields are, by default, `public`, `static`, and `final`

- **Allow for Future Evolution**: 
	- If you anticipate adding new methods to your base contract in the future.

When to Use an Interface:
- **Achieve a form of Multiple Inheritance**: 
	- A Java class can only `extend` one parent class, but it can `implement` multiple interfaces. This allows a class to inherit behaviors from several sources.

- **Define a Contract for Unrelated Classes**: 
	- Interfaces are ideal when you want to specify a capability that can be applied to a wide range of different classes.

- **Achieve Total Abstraction and Loose Coupling**:
	- Interfaces provide 100% abstraction because they (traditionally) only contain method signatures with no implementation.
	- This creates a clean separation between the definition of a behavior and its implementation, which leads to loosely coupled code.

#### Explain JDK, JRE, JVM and Memory Management?
[[Java Platform, Memory Management]]
- **JVM (Java Virtual Machine):** (Loads, verifies, runs, optimizes bytecode)
	- It's the **runtime engine** that executes Java bytecode, acting as the translator between your code and the specific operating system.
- **JRE (Java Runtime Environment):**  (Prepares libraries and environment)
	- It's the **environment to run Java applications**, bundling the JVM and essential class libraries for execution.
- **JDK (Java Development Kit): (**`.java` → `.class` (compilation))
	- It's the **complete toolkit for Java developers**, including the JRE plus tools like the `javac` compiler for writing, compiling, and running Java code.

JRE contains:
- Class Loader & Bytecode verification
- Java Class Libraries.
- JVM
JVM contains:
- Class Loader Subsystem(Loading, Linking, Initializing)
- Runtime Data Area(Stack Area, Heap Area, Meta Space, Method Area, PC Registers)
- Execution Engine(Interpreter, JIT Compiler, Garbage Collection)

Management:
- It was divided into:
		**1. Stack Area** (Size: 1024KB (1MB)--> RAM)
		**2. Heap Area** (Size: 768MB --> ROM)
		**3. Meta Space/ PermGen** (introduced after java 8)

- How data is stored:
		> **Heap Area:** Objects(Objects=Instance variables + methods), Arrays, Strings, Sub Area- String pool(String literals).
		> **Stack Area:** Local variables, Reference variables, methods.
		> **PermGem/ MetaSpace:** Class Structure, Static variables, Static Methods, Static Blocks, Sub Area- Methods Area(Entire Class Structure will be here).

#### Another:
- What is this Keyword, immutable, lambda expression, Generics, interfaces(java 8 features),pass by value, pass by reference?
- Why immutable is considered as advantage in multithreading application?
- How to achieve multithreading in java?
- What is 404, 401 errors? and 500 series errors?

### Advanced:



