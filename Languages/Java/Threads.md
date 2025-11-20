## Threads:

- A thread is a **unit of execution**. Java allows multiple threads to run concurrently (called **multithreading**).
- A thread in Java is a separate path of execution, and multiple threads can run in parallel, sharing the same resources like memory, but executing different parts of the program concurrently.
- When Main method is executed a Thread will be created. Every program in java is executed on threads.
- For every thread there will be stack area created in the stack area. 1 thread -> for 1 stack area, 2 threads -> for 2 stack areas..
- A **thread** in Java is an independent path of execution, enabling programs to perform multitasking. You can create threads by either extending the `Thread` class or implementing the `Runnable` interface. The JVM schedules threads for execution, and each thread goes through various states such as new, runnable, blocked, and terminated.

- **What is a Thread?**  
    A thread is a **unit of execution**. Java allows multiple threads to run concurrently (called **multithreading**).
- **Why Use Threads?**  
    To do **multiple tasks at the same time**. For example, one thread can print numbers while another prints letters.
- **How Do Two Threads Run "at the Same Time"?**  
    The **Java Virtual Machine (JVM)** and the **CPU** switch between threads very quickly (called **context switching**). It **looks like** they’re running at the same time. You can create threads by either extending the `Thread` class or implementing the `Runnable` interface.

When main method is executed, where does thread will be created(is it heap/stack or in both(if both how)) in java.
Ans: When the `main` method is executed in Java, a new thread is created to run the Java program. Here's a breakdown of how the thread and memory are involved:

**Can we achieve multithreading in Java _without_ using `Thread` or `Runnable`?**  
The **short answer is: No**, not directly.

#### 1. **Thread Creation:**

- When you execute a Java program, the **main thread** is created by the Java Virtual Machine (JVM). This main thread starts executing the code in the `main` method.
- The `main` thread is **not created explicitly by you** (as a user), but rather by the JVM when the program starts. This thread is a **part of the system’s execution process**.

#### 2. **Memory Allocation:**

In Java, memory is allocated in different regions when the thread is executed:

- **Heap Memory:**
    - The **heap** is used for dynamic memory allocation in Java, where all objects (including instances of classes) are stored.
    - Objects that are created (e.g., instances of classes) in the `main` method or any other part of the program are stored in the heap memory.
    - If you create an object inside the `main` method, it will reside in the heap.
- **Stack Memory:**
    - Each thread has its own **stack** memory. This is where method calls, local variables, and references to objects are stored.
    - The stack memory contains **method calls**, and for the `main` method, local variables like primitive data types or references to objects will be stored in the stack of the main thread.
    - When the `main` method is called, it will have its own stack frame, where the method call and local variables (such as the arguments `String[] args`) are stored.

#### 3. **Heap vs Stack for the Thread:**

- The **main thread** itself does not reside in the heap or stack. The main thread is managed by the JVM and is part of the execution environment. It doesn't live in the heap or stack directly; however, the **main method's execution context** (including local variables) will use both:
    - Local variables and references to objects are stored in the **stack** of the main thread.
    - The **objects** referenced by the main thread (and any created inside the method) will be stored in the **heap**.

#### Example for clarification:

```java
public class Main {
    public static void main(String[] args) {
        String message = "Hello, World!";  // message is a local variable, stored on the stack.
        StringBuilder builder = new StringBuilder("Welcome");  // builder is a reference stored on the stack, but the StringBuilder object resides in the heap.
    }
}
```

In this example:

- The **local variables** `message` and `builder` are stored on the **stack**.
- The **`StringBuilder` object** referred to by `builder` is stored in the **heap**.

Summary:
- The **main thread** is created by the JVM and runs the `main` method.
- The **stack** is used to store method calls, local variables, and references to objects.
- The **heap** is used to store the actual objects that are created or instantiated in the program.

---

##### The Below example is created by **extending the `Thread` class** and  **implementing the `Runnable` interface**. Both threads are started and run **concurrently**.

Code Example

```java
// Thread 1: Created by extending Thread class
class MyThread1 extends Thread {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println("Thread 1 - Number: " + i);
            try {
                Thread.sleep(500); // Pause for 500ms
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
    }
}

// Thread 2: Created by implementing Runnable interface
class MyRunnable implements Runnable {
    public void run() {
        for (char ch = 'A'; ch <= 'E'; ch++) {
            System.out.println("Thread 2 - Letter: " + ch);
            try {
                Thread.sleep(500); // Pause for 500ms
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
    }
}

// Main class to run both threads
public class MixedThreadExample {
    public static void main(String[] args) {
        MyThread1 thread1 = new MyThread1(); // Thread by extending Thread

        MyRunnable runnable = new MyRunnable(); // Runnable object
        Thread thread2 = new Thread(runnable);  // Thread by implementing Runnable

        thread1.start(); // Start Thread 1
        thread2.start(); // Start Thread 2
    }
}
```

### ✅ Output (Sample)

```
Thread 1 - Number: 1
Thread 2 - Letter: A
Thread 1 - Number: 2
Thread 2 - Letter: B
...
```

_Note:_ The output order may vary each time due to thread scheduling by the JVM.

---
