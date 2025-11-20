[Dependency Injection](https://www.youtube.com/watch?v=8qmM31QqlFQ&list=PLh6Yk2rpZu2KwknOHC--vsE5K3XeSCnts&index=3)
Definition:
Dependency Injection is a technique where one object receives the dependencies it needs from an external source, rather than creating them internally.
In Java, it can be implemented manually using constructors or setters, or automatically using frameworks like Spring.
- **Dependency Injection (DI)** is a design patterns.
- Instead of using `new` to create a dependency inside a class, the dependency is passed through a constructor, setter, or method — typically managed by frameworks like **Spring**.
- **Dependency Injection is used to pass (inject) the object of a class into another class (usually through a constructor or setter)** so that we can use the **methods and properties of that class without creating the object ourselves**. It’s commonly used in real-world apps to **reuse third-party or custom services**, like logging, databases, APIs, or payment systems — and is often implemented using **Java Beans** or in frameworks like **Spring**.
- Dependency Injection is a way to implement Inversion of Control by injecting required objects instead of creating them. [[Inversion of control (IOC)]].
[[Example of Dependency Injection(DI) for Constructor]]
[[Example of Dependency Injection(DI) for Setter]]

Dependency Injection(DI):
- Injecting dependency of a object from outside is known as Dependency Injection.
- Wiring & Connecting objects by the following a special method is known as DI.
- Spring Container will inject all the values to var through spring framework.
- Injecting Dependencies through Spring frame work is also known as DI.
- The Objects will be created during Runtime. If an object is created during run time and the object is given as arguments to constructor or setter and the object will be created. this can be achieved by using interfaces.
Why Spring Container inject dependencies? what type of dependencies does spring Inject and how?
How does 3rd party inject Objects?

**Spring Framework:** 
Generally when we develop a project, we create classes and use those classes in another class to fetch the operations of those classes. but this will increase tight coupling and dependency on another classes. (and this is not the best practice).

Spring framework tells us to use - Interfaces and create subclasses through interfaces then an abstraction layer will be formed. this will help in loose coupling and dependency on another classes.

Loose Coupling and Tight Coupling - [[Languages/Spring Boot/Notes|Notes]]

Spring is :
- light weight,
- Aspect - oriented Programing (AOP),
- Inversion Of Control.
- Dependency Injection(DI) framework.

IOC & DI are heart of Spring framework.

Keywords:

|Term|Meaning|
|---|---|
|**Dependency**|Object needed by a class (like `PaymentService`)|
|**Injection**|Supplying the dependency from outside|
|**Java Bean**|Reusable class with default constructor and getters/setters|
|**Constructor Injection**|Dependency injected via constructor|
|**Setter Injection**|Dependency injected via setter method|
|**Interface Injection**|Inject via method defined in an interface (rare in Java)|

Typical Flow:
1. **Create your dependency class** (e.g., `EmailService`)
2. **Inject it into the dependent class** (e.g., `UserService`) via constructor
3. **Use the dependent class in `main()` or controller**
4. In frameworks like **Spring**, the framework handles the injection automatically


