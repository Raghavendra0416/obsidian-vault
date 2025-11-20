### Java Platform:
- There 3 main components in JAVA:
		1. **JDK(Java Development Kit)**
		2. **JRE(Java Run Time Environment)**
		3. **JVM(Java Virtual Machine)**

- **JVM (Java Virtual Machine):** It's the **runtime engine** that executes Java bytecode, acting as the translator between your code and the specific operating system.
- **JRE (Java Runtime Environment):** It's the **environment to run Java applications**, bundling the JVM and essential class libraries for execution.
- **JDK (Java Development Kit):** It's the **complete toolkit for Java developers**, including the JRE plus tools like the `javac` compiler for writing, compiling, and running Java code.

![[Pasted image 20250619114328.png]]
![[Pasted image 20250619113819.png]]
![[Pasted image 20250619114359.png]]


- JVM will be created when java is installed.
- The development tools are in JDK/Bin folder.
- Java file will be in JDK & JRE (as it needed for the execution of program).
- Program files/jre/rt.jar(rt.jar--> will contain all the data like keywords we use in java).
- Javac program file will be only in JDK as developer need to compile the code
- In JAVA--> .java file(in JDK) -will convert to--> .class(in JRE).
- Main Components in JVM architecture [link](https://medium.com/@amitvsolutions/jvm-part-2-architecture-1bf3044a9378):
			1. Class loader Subsystem.
			2. Runtime Data Area
			3. Execution Engine
#### Class Loader Sub System:
##### > Loading: 
- To load files during execution. Mostly class files.
- Divided into 3 Components:
		1. **Boot Strap class loader:** to load rt.jar files
		2. **Extension Class Loader:** to load programs/files in jre/lib/.ext files in this folder.
		3. **Application Class Loader:** loading external classes(external classes will be help java to interact with external applications, for example: excel)
##### > Linking:
- **Verify:** Checks if the java is executing correct byte code or altered code(incorrect code)
- **Prepare:** It will assign default values to static variables.(the default values link for int ->0 as initial value. Mostly empty or 0 values)
- **Resolve:** Reads Symbolic References(Constant Pool)--change it to-->Method References--> Save them in Run Time Constant Pool.
##### > Initialization: 
- It will assign the values to static variables that are assigned in the program.(if int i=5; 5 will be assigned to i, in this stage).

#### Run Time Data Area:
- Variables, methods, objects, classes will be allocated here(Memory allocation).

#### Execution Engine:
- **Interpreter:** it will convert:
	- Interpreter--> Bytecode--to--> System understand language
	- Line by Line
- **JIT Complier:** 
	- Interpreter will tell JIT compiler which code is repeated.
	- Then JIT Compiler will interpret the repeated code and convert them to system understandable code and will save it.
	- When Interpreter tries to interpret the repeated code JIT Complier will send the code it has with it(this will save time in java).
- **Garbage Collection:** Clears unwanted or unused data
	- **Native Method Interface(JNI), Native Method Library:** these will help execution Engine.



![[Screenshot 2025-03-13 003129 1.png]]





### Memory Management:
- RAM(Random Access Memory)- stores data temporarily, ROM(Read Only Memory)- Stores data permanently.
- When java is installed, some memory will be allocated to java in system. JVM will be created when java is installed.
- The allocated memory is called **"Memory Area/ Run Time Data Area"**. or also called Native Area.
- Java will use this area to store the data by dividing the storage to different parts.
- It was divided into:
		**1. Stack Area** (Size: 1024KB (1MB)--> RAM)
		**2. Heap Area** (Size: 768MB --> ROM)
		**3. Meta Space/ PermGen** (introduced after java 8)
- How data is stored:
		> **Heap Area:** Objects(Objects=Instance variables + methods), Arrays, Strings, Sub Area- String pool(String literals).
		> **Stack Area:** Local variables, Reference variables, methods.
		> **PermGem/ MetaSpace:** Class Structure, Static variables, Static Methods, Static Blocks, Sub Area- Methods Area(Entire Class Structure will be here).
- If different String objects are created then different String Pools will be created in Heap.
#### How Memory is allocated in Java while executing program:
- When Main method is executed a Thread ([[Threads]]) will be created. Every program in java is executed on threads.
- Stack has frames in it.(LIFO-Last In First Out). Every frame contains method data.
- The entire class structure will be in Method Area(inside Meta Space).
- Every class has buckets(Memory Area) arranges top it and these buckets will contain class structure in it.
- The data will be assigned as per the storage area(i.e you can see how the data is classified and stored in the above.)
#### Additional points:
- Stack will store the data temporarily and it has high performance.
- If memory is full the Exceptions thrown by java:
	- Stack -> Stack Overflow Exception
	- Heap -> Out of Memory: Java heap Space Exception.
- To Configure the size of heap/stack:
	- Heap: "-Xmx500m" (-Xmx --> is command, 500m --> means 500MB).
	- Stack: "-Xss2m" (-Xss --> is command, 2m --> means 2MB).
- Before Java 8 MetaSapce is part of Heap Area. When the MetaSpace is in heap, it is used to called as "PermGen". After Java 8 they have given different Storage and name.

![[Screenshot 2025-03-12 013232.png]]

#### Journey of Java File:
#####  1. Journey Through JDK (Java Development Kit)

This is the **starting point** for a Java file:
1. **You create a `.java` file** (e.g., `HeroQuest.java`) using an IDE or text editor.
2. **`javac` (Java Compiler) is used**:
    - The Java file is compiled using the command:
        ```
        javac HeroQuest.java
        ```   
    - The compiler checks the code for syntax errors and translates it to **bytecode**.
3. **`.class` file is generated**:
    - This file (e.g., `HeroQuest.class`) contains platform-independent bytecode.
        
    - This `.class` file is the input for the JVM in the next stage.    
    - 
 **End of JDK’s role** → Now the bytecode moves to JRE.
 
---
#####  2. Journey Through JRE (Java Runtime Environment)

The `.class` file enters the **runtime environment**:
1. **You run the class using the `java` command**:
    ```
    java HeroQuest
    ```
2. **JRE sets up the runtime environment**:
    - It includes core Java libraries (`rt.jar`, etc.).
    - It loads necessary files and dependencies to support execution.
3. **JRE passes the bytecode to the JVM**:
    - JVM is part of the JRE.
    - Now the actual execution of the program starts inside the JVM.

 **End of JRE’s role** → JVM takes over to execute the bytecode.

---
#####  3. Journey Through JVM (Java Virtual Machine)

This is where **execution happens**:
1. **Class Loading**:
    - The JVM uses a **ClassLoader** to locate and load `HeroQuest.class`.
2. **Bytecode Verification**:
    - Ensures the bytecode is safe (no illegal operations, type issues, etc.).
3. **Linking & Preparation**:
    - Static memory is allocated.
    - References to other classes (like `System.out`) are resolved.
4. **Execution Engine Starts**:
    - **Interpreter** executes bytecode one instruction at a time.
    - **JIT (Just-In-Time) Compiler** detects frequently-used code and compiles it to **native machine code** to improve speed.
5. **Garbage Collection**:
    - JVM automatically clears memory used by unreachable objects during execution.
6. **Program Output**:
    - The output (like print statements) is displayed on the console.
7. **Program Ends**:
    - JVM terminates and control returns to the OS.
 **End of JVM’s role** → Execution complete.

---

## 🧩 Final Summary: File’s Journey Flow

| Phase           | Component | What Happens                              |
| --------------- | --------- | ----------------------------------------- |
| **Development** | **JDK**   | `.java` → `.class` (compilation)          |
| **Setup**       | **JRE**   | Prepares libraries and environment        |
| **Execution**   | **JVM**   | Loads, verifies, runs, optimizes bytecode |

Let me know if you want this turned into a revision chart, flashcard, or visual diagram!
#### Questions on Memory Management:
1. **What part of memory is used to store instance variables and object data in Java?**  
    ➤ Instance variables and objects are stored in the **heap memory**.
    
2. **What is the role of the JVM's Garbage Collector, and when does it run?**  
    ➤ It **automatically reclaims memory** from unreachable objects, running periodically or when memory is low.
    
3. **What is the difference between stack memory and heap memory in Java?**  
    ➤ **Stack** stores method calls and local variables; **heap** stores objects and class instances.
    
4. **What happens when an object has no more references pointing to it?**  
    ➤ It becomes **eligible for garbage collection**.
    
5. **How does Java handle memory leaks despite having automatic garbage collection?**  
    ➤ Memory leaks occur when **objects are still referenced but no longer used**, preventing GC from reclaiming them.
    
6. **What is the purpose of the `finalize()` method in Java, and why is it discouraged in modern development?**  
    ➤ `finalize()` runs before GC to clean up, but it’s **unreliable and deprecated** due to poor performance and unpredictability.
    
7. **Can you manually force garbage collection in Java? If so, how?**  
    ➤ You can suggest GC with `System.gc()`, but **it’s not guaranteed to run immediately**.
    
8. **What is a memory leak in Java, and how might it occur even with garbage collection?**  
    ➤ A memory leak happens when **unused objects are still referenced**, keeping them from being garbage collected.
    
9. **What do the terms _young generation_, _old generation_, and _permgen/metaspace_ refer to in the context of Java memory management?**  
    ➤ They are **heap sections**: young (new objects), old (long-lived), and permgen/metaspace (class metadata).
    
10. **How does the concept of object reachability affect garbage collection in Java?**  
    ➤ Only **unreachable objects** (not accessible by any live thread) are eligible for garbage collection.
    Here are **one-line answers** for your second set of Java memory management questions:

11. **What is the difference between strong, weak, soft, and phantom references in Java?**  
    ➤ They define **levels of reachability**, where strong prevents GC, weak/soft allow conditional GC, and phantom is used for post-finalization cleanup.
    
12. **Why is it important to avoid creating unnecessary objects inside loops or frequently called methods?**  
    ➤ It leads to **increased garbage creation and GC overhead**, affecting performance.
    
13. **What kind of objects are stored in the method area (Metaspace in Java 8+)?**  
    ➤ **Class metadata**, static methods, and constant pool data are stored there.
    
14. **How does Java prevent memory fragmentation in the heap space?**  
    ➤ It uses **compacting garbage collectors** that rearrange objects to free contiguous space.
    
15. **What is the impact of having large static collections that are never cleared?**  
    ➤ They can cause **memory leaks** by holding onto unused objects indefinitely.
    
16. **What tools or commands can be used to monitor memory usage and detect memory leaks in Java applications?**  
    ➤ Tools like **VisualVM, JConsole, jmap, jstat, and Eclipse MAT** are commonly used.
    
17. **Explain what happens during a "Stop-the-world" event in garbage collection.**  
    ➤ All application threads **pause temporarily** to allow garbage collection to run safely.
    
18. **What is the difference between minor and major garbage collection (GC)?**  
    ➤ **Minor GC** cleans the young generation; **major (or full) GC** cleans the entire heap including the old generation.
    
19. **How can you profile or tune garbage collection behavior for a high-memory Java application?**  
    ➤ Use **JVM GC flags, logs, profiling tools**, and experiment with **different GC algorithms**.
    
20. **What strategies can be used to reduce the frequency of full (major) garbage collections?**  
    ➤ Optimize object lifetimes, **tune heap sizes**, and choose a **low-pause GC algorithm** like G1 or ZGC.
    