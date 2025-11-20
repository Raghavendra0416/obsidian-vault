#### Inheritance:
- **Inheritance** is a mechanism that allows one class (called a **subclass** or **child class**) to acquire the fields and methods of another class (called the **superclass** or **parent class**). This allows the subclass to reuse, extend, and modify the behavior defined in the parent class. Hierarchical Structure.
- Syntax: 
		class ParentClass {
		    // Parent class code
		 }

		class ChildClass extends ParentClass {
		    // Child class code
		 }
- **"Extends"** keyword is used to inherit the fields and methods of parent class.
- Inheritance can inherit:
		1. Fields (instance variables)
		2. Methods
		3. Constructors (though not directly inherited, they can be called using `super`)
		4. **Nested classes** (if the access modifier allows it)
- Types of inheritance:
		1. **Single Inheritance**: A subclass inherits from one parent class.
		2. **Multilevel Inheritance**: A subclass inherits from another subclass.
		3. **Hierarchical Inheritance**: Multiple subclasses inherit from a single parent class.
- Java does not support **multiple inheritance** (where a class can inherit from multiple parent classes) directly to avoid ambiguity. However, it can be achieved through interfaces.
- Key Words need to remember while using inheritance: 
	- Core Keywords: Extend, Super, This.
	- Access Modifier: Public, Protected, Private.
	- Other: Abstract, Interface, Implements, Final, Instance of.
- Example of inheritance in real life:
		**Vehicle Inheritance**:
			**Parent class:** Vehicle
			**Child classes:** Car, Truck, Bicycle
			A vehicle is a general concept, and different types of vehicles (car, truck, bicycle) inherit common properties like speed, fuel type, and methods like drive() or stop(), but they may add their own specific features, like load capacity or gears.
- **Key concepts of Inheritance:**
		1. **Method Overriding**: 
				Inheritance allows child classes to override methods from the parent class to provide their specific implementation.
		2. **Super Keyword**: 
				The `super` keyword is used to refer to the immediate parent class and can be used to access parent class methods, fields, and constructors.
		3. **Constructor Inheritance**: 
				Constructors are not inherited, but a child class can call the parent class constructor using `super()`.
		4. **Access Modifiers and Inheritance**: 
				You need to understand how inheritance interacts with access modifiers (`private`, `protected`, `public`, and default).
		5. **`final` Keyword**: 
				A class declared as `final` cannot be inherited, and methods declared as `final` cannot be overridden.
		6. **`Object` Class**: 
				Every class in Java implicitly inherits from the `Object` class, so understanding its methods (like `toString()`, `equals()`, `hashCode()`) is crucial.
		7. **Polymorphism**: 
				Inheritance is closely tied to polymorphism, which allows one object to behave in multiple ways. This typically involves method overriding and dynamic method dispatch.
- Commonly asked questions in inheritance:
		1. What is inheritance in Java and how a child class inherits properties and methods from a parent class?
		2. What is the difference between method overriding and method overloading?
		3. Can constructors be inherited in Java?
		4. What is the purpose of the `super` keyword and how `super` is used to access parent class methods, fields, and constructors.?
		5. What is the difference between `super` and `this` keywords? (Super-parent class, this-instance class).
		6. What is the difference between `extends` and `implements` in Java?
		7. What is method overriding in Java?
		8. Can a Java class extend more than one class?
		9. What is a `final` class?
		10. What is an example of polymorphism in the context of inheritance?


#### Learn [[Access Modifiers, Interfaces]] concept before learning Encapsulation.

#### Encapsulation:
- **Encapsulation** refers to the bundling of data (variables) and methods (functions) that operate on that data within a single unit, or class.
						(or)
- it is mechanism of wrapping the data(variables) and code acting on the data(methods) together as a single unit.
						(or)
- Describes the ability of object to hide to hide its data and methods from the rest of the world.
- Focuses on _how_ the data is stored and protected.
- In Encapsulation we are hiding data(not implementation) and we are using methods(like getters & setters) to fetch the data, so they cannot alter or change the data || In Abstraction we will hide implementation and  only shows the functionality.(User will not know the implementation of the functionality they are using)
- Encapsulation: Bundling of data (fields) and the methods (getters/setters) that operate on the data into a single unit (class).
- Keywords while using Encapsulation:
	- Core keywords: Public, Private, Protected
	- Concepts: Data Hiding, Getter & Setters method, JavaBeans Convention, Constructor Overloading (optional)
- Syntax:
			public class ClassName {

		    // Step 1: Private variables (data encapsulation)
		    private DataType variableName;

		    // Step 2: Public getter method (accessor)
		    public DataType getVariableName() {
		        return variableName;
			 }

		    // Step 3: Public setter method (mutator)
		    public void setVariableName(DataType value) {
		        // Optional: Add validation or additional logic
			    this.variableName = value;
			    }
			}
- **Key Points:**
		1. **Data Hiding**: Encapsulation hides the internal state of an object and only exposes necessary functionalities to the outside world.
		2. **Access Control**: The access to the fields (variables) of a class is controlled using **access modifiers** (`private`, `protected`, `public`, and default).
		3. **Public Methods (Getter/Setter)**: To allow controlled access to private fields, **getter** and **setter** methods are used.
		4. **Internal Implementation Details Hidden**
		5. **Controlled Access to Data**
		6. **Immutability**
		7. **Single Responsibility Principle**
		8. **Encapsulation in Object-Oriented Design***
- **Real-life Analogy:**
		Consider a **bank account**:
			- The bank account balance is encapsulated (hidden) from the outside world to prevent unauthorized or unintended access.
			- To deposit or withdraw money, the customer interacts with the bank through **methods** (deposit, withdraw), which internally manipulate the account balance. The customer can't directly change the balance without going through these methods.
- Commonly asked questions in Encapsulation:
		1. What is encapsulation in Java and explain its importance in object-oriented programming?
		2. What are getter and setter methods? Explain the role of getter and setter methods in encapsulation, and why fields are typically made private?
		3. Can we directly access the fields of a class in Java?how direct access to fields is restricted using access modifiers, and why this is beneficial?
		4. What is the difference between encapsulation and inheritance?
- Encapsulation can be **applied** or **implemented** based on how the data and methods are structured:
		1. **Encapsulation with Access Modifiers**
		2. Encapsulation with **Immutable Objects**
		3. **Encapsulation with Validation**
		4. **Encapsulation Using Constructor Initialization**


#### Abstraction:
- **Abstraction** in Java is a concept that allows you to hide the implementation details and only show the functionality to the user.
- It helps in reducing complexity.
- There are two main ways to achieve abstraction in Java:
		1. **Abstract Classes**
		2. **Interfaces**
- The class that is using interface has to follow all the the method that are in the interface(or else the class will throw an error). If there is a scenario where we want to use only few methods from interface we have to use **abstract class**.
- FYI, A class cannot implements another class it can only extend. interface can only be implemented. 
- 100% abstraction is dependent on user as per their implementation of methods in class. to calculate the percentage of abstraction-> check how many methods are implemented or not. 
- Key words need to remember while using Abstraction:
	- Core Keywords: Abstract, Interface, Implements, Extends
##### Abstract Class:
-> Key Characteristics of an Abstract Class:
		1. **Cannot Be Instantiated:** 
				You cannot create an object of an abstract class directly. You must create a subclass that provides implementations for the abstract methods.
		2. **Abstract Methods:** 
			An abstract class can have abstract methods, which are declared without a body. Any subclass of the abstract class must provide an implementation for these methods.
		3. **Concrete Methods**: 
			An abstract class can also have concrete methods (methods with a body), which can be inherited by its subclasses.
		4. **Can Have Constructors**: 
			Even though you can't instantiate an abstract class, it can have constructors that are called when a subclass is instantiated.
- Abstract class cannot be instantiated on its own and is designed to be subclassed by other classes.
- It may contain both **abstract methods** (methods without a body) and **concrete methods** (methods with a body).
- An abstract class serves as a blueprint for other classes, providing some common functionality while leaving certain methods for subclasses to implement.
- Class cannot extends multiple abstract classes.(Why? because it will cause "Dimond Problem")
- In Abstract Class we must have to implement abstract methods to the extended class.(if in abstract class if the method is not abstract , then there is no need to implement it)
- To avoid implementing abstract class methods, we have to extend the abstract class to another abstract class(then there is no need to implement any methods that are abstract)
- Dimond Problem:
	- Two parent classes define the same method or variable.
    - It's unclear which one should be inherited or used — known as the **"diamond problem"**.
##### Interfaces:
-> Key Characteristics of an Interface in Abstraction:
		1. **Abstract Methods**:
		    - By default, all methods in an interface are **abstract** (i.e., they do not have a body). A class that implements the interface must provide implementations for these abstract methods, unless the class itself is abstract.
		    - **Before Java 8**: Methods in an interface are implicitly abstract, and the interface cannot have method bodies.
		    - **After Java 8**: Interfaces can have `default` methods with method bodies and `static` methods, but instance methods are still abstract by default unless specified otherwise.
		2. **No Instance Variables**:
			 - Interfaces cannot have instance variables (fields). They can only declare **constants**, which are implicitly `public`, `static`, and `final`. This means all fields in an interface are constants by default.
		3. **Multiple Inheritance**:
		    - A class can implement multiple interfaces, thus allowing **multiple inheritance** of behavior. This is a key advantage of interfaces over classes, as a class can only inherit from one class (single inheritance).
		4. **Cannot Have Constructors**:
		    - Interfaces cannot have constructors because they cannot be instantiated directly. Only the classes that implement the interface can have constructors.
		5. **Abstract by Default**:
		    - All methods in an interface are abstract by default (unless they are `default` or `static`). This means they don’t have a body and must be implemented by any class that implements the interface.
		6. **Implementation by Class**:
		    - A class that implements an interface is required to provide implementations for all abstract methods defined in the interface. If a class does not implement all the methods, the class must be declared as **abstract**.
		7. **Default Methods (Java 8 and Later)**:
		    - Interfaces can have `default` methods with a method body. This allows you to provide a default implementation of a method within the interface itself, and classes implementing the interface do not have to override the method unless they want to provide a specific implementation.
		8. **Static Methods (Java 8 and Later)**:
		    - Interfaces can have `static` methods. These methods are called on the interface itself and not on instances of the interface.
	    9. **No Access Modifiers for Methods**:
		    - All methods in an interface are implicitly **public**. You cannot specify any other access modifiers for methods in an interface.
- An interface in Java is a collection of abstract methods. Any class that implements an interface must provide the implementation for all the methods declared in the interface.
- In Interface we must have to implement all the methods that was declared in the interface to implemented class.
- Class can implement multiple interfaces(why? because it will avoid "diamond problem" of multiple inheritance)
- Java forces you to **resolve ambiguity** when two interfaces have the same default method.

##### Comparison between Abstract Class and Interface:
- Java introduced **interfaces** to overcome the limitations of **abstract classes**, especially related to **multiple inheritance**.
- Use **abstract class** when you want to share **code** among several closely related classes.
- Use **interface** when you want to specify a **contract** for classes that may not be related.

| Feature                      | **Abstract Class**                                                                                                                                                              | **Interface**                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Instantiation**            | Cannot be instantiated                                                                                                                                                          | Cannot be instantiated                                                                                          |
| **Keyword used**             | `abstract class`                                                                                                                                                                | `interface`                                                                                                     |
| **Inheritance type**         | Supports **single inheritance** only                                                                                                                                            | Supports **multiple inheritance** (via multiple interfaces)                                                     |
| **Main Difference**          | In Abstract Class we must have to implement abstract methods to the extended class.(if in abstract class if the method is not abstract , then there is no need to implement it) | In Interface we must have to implement all the methods that was declared in the interface to implemented class. |
| **Implementation**           | **Abstract classes** can have both abstract and concrete methods.                                                                                                               | **Interfaces** require the implementing class to implement **all methods** (unless the class is abstract).      |
| **Constructors**             | Can have constructors                                                                                                                                                           | Cannot have constructors                                                                                        |
| **Access modifiers**         | Can use any (public, protected, private, etc.)                                                                                                                                  | Methods are `public` by default                                                                                 |
| **Method types**             | Can have abstract and concrete methods                                                                                                                                          | Can have abstract, default, static, and private methods                                                         |
| **Variables**                | Can have instance variables (fields)                                                                                                                                            | Only constants (`public static final`)                                                                          |
| **Extending / Implementing** | Use `extends` keyword                                                                                                                                                           | Use `implements` keyword                                                                                        |
| **Use case**                 | Used when classes are **closely related**                                                                                                                                       | Used to define a **contract for behavior**                                                                      |
| **Multiple Inheritance**     | Not supported directly                                                                                                                                                          | Supported through multiple interfaces                                                                           |
| **Performance**              | Slightly faster as fewer indirections                                                                                                                                           | Slightly slower due to indirections                                                                             |
| **Java Version Flexibility** | Available since Java 1.0                                                                                                                                                        | Default and static methods added from Java 8 onward                                                             |


---
#####  **Basic-Level Questions**

1. What is the difference between an interface and an abstract class in Java?
2. Can we create an object of an abstract class? Why or why not?
3. Can an abstract class have constructors?
4. What happens if you don’t implement all the abstract methods in a subclass?
5. Can we declare a method as abstract and static at the same time?
6. Can an interface have fields or variables?

---
#####  **Intermediate-Level Questions**

7. Can a class implement multiple interfaces? Can it extend multiple abstract classes? Why or why not?
8. What are default methods in interfaces? When would you use them? (Java 8+)
9. When should you use an abstract class instead of an interface?
10. Can an abstract class implement an interface without providing implementations for its methods?
11. How does Java resolve method conflicts when a class implements two interfaces with the same default method?

---
#####  **Advanced-Level / Scenario-Based Questions**

12. You're designing a plugin system: would you use interfaces or abstract classes? Justify your design choice.
13. Can you simulate multiple inheritance in Java? How?
14. Explain how the diamond problem is avoided in Java with interfaces.
15. What’s the difference between a functional interface and a normal interface? (Java 8+)
16. Can an interface extend another interface or abstract class? What about the reverse?

---
#####  Quick Tip: How to Prepare

- Understand the **syntax and rules** around `abstract`, `interface`, `default`, and `static`.
- Know **when to use what** — interface vs abstract class, and the design rationale.
- Practice **writing small examples** that use both abstract classes and interfaces.
- Be ready to **justify your design choices** in a real-world scenario.


#### Polymorphism:
- Poly -means-> Many, Morphism- means-> forms.
- **Polymorphism** is the ability of an object to take on multiple forms.
- Every method is unique.
- Keywords need to remember while using polymorphism:
	- Core Keywords: Override, Super, Instance of.
- There are two main types of polymorphism in Java:
		1. Compile-time Polymorphism (Method Overloading).
		2. Runtime Polymorphism (Method Overriding).
##### Compile-time Polymorphism (Method Overloading):
- Achieved by defining multiple methods with the same name but different parameters within a class.
- The method to be executed is determined at compile time.
- This can be achieved by method overloading.
- **Method Overloading**: Repeating or taking a single method multiple times by adding/assigning extra parameters in the methods. (Same method name, type/order/no . of parameters are different).
##### Runtime Polymorphism (Method Overriding):
- Achieved when a subclass provides a specific implementation of a method that is already defined in its parent class.
- The method to be executed is determined at runtime, based on the actual object type.
- This can be achieved by Method Overriding.
- **Method Overriding**: In Java that allows a subclass to provide a specific implementation of a method that is already defined in its superclass.
- Override annotation is not mandatory.
- Override annotation is used to check if the method is correct or not.
- By writing override we can see if any parameters are passed and if we have given any extra parameters like that.
- Overriding happens **only in a subclass**, where a method in the child class provides a different implementation of a method from the parent class.