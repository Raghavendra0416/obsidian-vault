#### Compiler:
- Java uses **both a compiler and an interpreter**, often referred to as a "hybrid" approach.1 Here's how it works:
	1. **Compilation (to Bytecode):**
	    - First, your Java source code (the`.java` file) is compiled by the Java compiler(`javac`).
	    - This compiler doesn't produce machine code directly. Instead, it translates the source code into an intermediate format called **bytecode** (stored in `.class` files).4
	    - This bytecode is platform-independent, meaning the same `.class` file can run on any system that has a Java Virtual Machine (JVM). This is Java's famous "Write Once, Run Anywhere" capability.
	2. **Interpretation and Just-in-Time (JIT) Compilation (by JVM):**
	    - When you run a Java program, the **Java Virtual Machine (JVM)** comes into play.
	    - The JVM acts as an interpreter for the bytecode. It reads the bytecode instructions and translates them into machine-specific instructions for the underlying hardware.
	    - To improve performance, modern JVMs also include a **Just-in-Time (JIT) compiler**. The JIT compiler monitors the execution of the bytecode. If it identifies frequently executed code segments (called "hotspots"), it compiles these segments directly into native machine code.11 This compiled machine code can then be executed much faster, bypassing the interpretation step for those particular sections.

- In summary:
	- **Compiler (`javac`):** Compiles `.java` files into platform-independent bytecode (`.class` files).
	- **Interpreter (JVM):** Interprets bytecode line by line.
- **JIT Compiler (part of JVM):** Dynamically compiles frequently used bytecode into native machine code at runtime for performance optimization.

This two-step process provides Java with both platform independence and good performance.