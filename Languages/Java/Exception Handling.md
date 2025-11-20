To understand exception handling in Java, start with these foundational concepts:

- What is an Exception?
- Difference between Error and Exception
- Why Exception Handling is Needed
- Basic Syntax: try, catch, finally, throw, throws
- Types of Exceptions (Checked and Unchecked)

- Exception Handling in Java is a mechanism to handle runtime errors so the normal flow of the application can be maintained.
- Java provides a robust and object-oriented way to handle both system-generated and user-defined exceptions.
- Syntax:
	 try{
		//block of code
		}catch(Type of Exception variable){
		// what to do when exception is thrown
		}
- Example:
		try {
	     int result = 10 / 0;
		} catch (ArithmeticException e) {
	    System.out.println("Cannot divide by zero");
		} finally {
	    System.out.println("This will always execute");
		}
- Key Concepts:

| Concept               | Description                                                                        |
| --------------------- | ---------------------------------------------------------------------------------- |
| **Exception**         | An object representing an error or unusual condition during program execution.     |
| **Try-Catch Block**   | Used to catch and handle exceptions.                                               |
| **Throw**             | Used to explicitly throw an exception.                                             |
| **Throws**            | Declares the exceptions that a method might throw.                                 |
| **Finally**           | Block that always executes (used to clean up resources).                           |
| **Custom Exceptions** | You can create your own exceptions by extending `Exception` or `RuntimeException`. |
- **Stack Trace** helps you **debug** by telling you **where** the error happened and **what methods were involved** in reaching that point.
- When an exception happens, Java prints something like this:
	```java
	Exception in thread "main" java.lang.ArithmeticException: / by zero
	    at Main.divide(Main.java:5)
	    at Main.main(Main.java:10)
	```
	-  Let's break this down:
		- `java.lang.ArithmeticException`: This is the **type of exception**.
		- `: / by zero`: This is the **message** that explains the issue.
		- `at Main.divide(Main.java:5)`: It shows that the exception occurred in the `divide()` method of the `Main` class, **on line 5**.    
		- `at Main.main(Main.java:10)`: The call to `divide()` came from the `main()` method on **line 10**.
		So the **stack trace goes from the method where the error occurred** all the way back through the **chain of method calls** that led there.
#### Different types of exceptions in java:
- **Checked Exceptions** (Compile-time)
- **Unchecked Exceptions** (Runtime)
- Custom Exceptions
##### Checked Exceptions (Compile-time)
- Handled explicitly. The compiler checks these.
- Examples:
	- IOException   
	- SQLException
	- ClassNotFoundException
##### Unchecked Exceptions (Runtime)
- Not checked at compile-time.
- Examples:
	- NullPointerException
	- ArithmeticException
	- ArrayIndexOutOfBoundsException
#####  Custom Exceptions
- You can define your own exception by extending `Exception` or `RuntimeException`.
- Example:
		class MyException extends Exception {
		    public MyException(String message) {
		        super(message);
			 }
		 }
##### Exception Hierarchy in Java
```
Object
 └── Throwable
      ├── Error (Serious system errors, not meant to be caught)
      └── Exception
           ├── Checked Exceptions (e.g., IOException)
           └── RuntimeException (Unchecked Exceptions, e.g., NullPointerException)
```
#####  Visual Hierarchy

```
Throwable
├── Error
│   ├── OutOfMemoryError
│   └── StackOverflowError
└── Exception
    ├── IOException
    ├── SQLException
    └── RuntimeException
        ├── NullPointerException
        ├── ArithmeticException
        └── IndexOutOfBoundsException
```

##### Comparison Between Checked & Unchecked Exceptions

|Feature|Checked Exception|Unchecked Exception|
|---|---|---|
|Checked by Compiler|Yes|No|
|Handling Required|Must be handled/declared|Optional|
|Examples|IOException, SQLException|NullPointerException|
|Inherits From|`Exception`|`RuntimeException`|
|When Occurs|Compile-time|Runtime|

##### Error vs Exception in Java

|Feature|**Error**|**Exception**|
|---|---|---|
|**Definition**|Serious issues beyond the control of the program|Issues that can be caught and handled by the program|
|**When Occurs**|Typically at runtime|At compile-time or runtime|
|**Recoverable?**|❌ No – usually can't recover from an Error|✅ Yes – you can handle exceptions using try-catch|
|**Examples**|`OutOfMemoryError`, `StackOverflowError`|`IOException`, `NullPointerException`|
|**Part of Hierarchy**|Subclass of `Throwable`|Subclass of `Throwable`|
|**Handling**|Not meant to be caught or handled in code|Meant to be caught and handled|
-  **Error** = Critical, system-level problems (e.g., JVM issues, memory errors). You **should not** try to handle them.
- **Exception** = Problems in code logic (e.g., divide by zero, file not found). You **should** handle these using try-catch blocks.