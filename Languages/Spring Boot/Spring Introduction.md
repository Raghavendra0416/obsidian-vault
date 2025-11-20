- Provides large number of helper classes.
- In Enterprise applications, applications development becomes more complex.
- Client Side Presentation -> Server Side presentation -> Server side business logic -> Database.

Java Editions: 
- JSE(Java Standard Edition) - Use to develop standalone applications.
- J2EE(Java Enterprise Edition) - use to develop web applications that runs on servers like fb..
- J2ME(Java Micro Edition) - use to build applications that run across all basic & smartphones.

Pro's:
- It's Core java with powerful set of libraries & API's
- Using those set of libraries & API's, Developer can build applications for business computing.
Con's:
- EJB V1 &EJ V2 Complexity:(Disadvantages)
	- Early version of EJB(V1&V2) were extremely complex.
	- Multiple Deployment Descriptors
	- Multiple Interfaces.
	- Poor Performance of entity Beans.
	- Slow execution.
- Implementation & Usage of EJB(Enterprise Java Bean), is highly complex at the initial version of JEE.
- Poor performance of entity beans.
- Without EJB, how we can develop Java Beans? Java beans can be implemented using POJO'S (Plain Old Java Objects).

**To Overcome this, Johnson has created Spring.**

**POJO** (Basic Rules): (Used to hold data, don't follow special rules, simple java class)
- Private fields
- Public getters and setters
- No business logic
- No need to extend any class or implement interfaces

**JavaBean Rules**(Basic Rules): (Special type of POJO, POJO with rules, used in Java - based UI tools & framework)
1. Must have a **public no-arg constructor**
2. Must have **private fields**
3. Must provide **getters and setters**
4. Must be **serializable** (usually implements `Serializable` interface)

Spring Boot:
- It will provide all the configurations by default.
- Also dependency jar file & plugins will be taken care.
- By default embedded tomcat Server is added in your application.


Developer(A dev will develop Spring framework) --> Spring Boot (tool- to develop the framework & run it in server, all configuration taken care by spring boot, provide application ready application) --> Spring framework (Framework that supports Spring & helps dev to make code reusable and easy).

Spring Features:(Design patterns)
- [[Inversion of control (IOC)]]
- [[Dependency Injection(DI)]]
- [[Spring MVC]]
- Spring Data JPA
- Hibernate.
- REST
- AOP
- Spring, Security, etc...

---
#### Summary Categorized
##### Core Concepts
- **Inversion of Control (IoC)**
- **Dependency Injection (DI)**
##### Programming Styles
- **AOP (Aspect-Oriented Programming)**
- **REST (Architectural Style)**

##### Frameworks
- **Spring Framework** (Core, DI, AOP)
- **Spring MVC** (Web layer)
- **Spring Boot** (Simplifies Spring projects)
- **Spring Security** (Authentication/Authorization)
- **Spring Data JPA** (Database Access)

##### External Library
- **Hibernate** (ORM library used by JPA/Spring Data JPA)

---
##### Core Spring Principles:
- **Inversion of Control (IoC)**.
- **Dependency Injection (DI)**.
- **Aspect-Oriented Programming (AOP)**.

- **Inversion of Control (IoC)**: A fundamental design principle where the control of object creation and lifecycle management is transferred from your code to an external container. In Spring, the IoC container is responsible for creating objects (called "beans"), managing their dependencies, and overseeing their entire lifecycle. This promotes loose coupling between components.
- **Dependency Injection (DI)**: This is the primary pattern used to implement IoC. Instead of an object creating its dependencies internally, the dependencies are "injected" into the object by the IoC container. This can be done through constructors, setter methods, or fields.
- **Aspect-Oriented Programming (AOP)**: A programming paradigm that addresses "cross-cutting concerns"—functionalities like logging, security, and transaction management that are required across many parts of an application. Spring AOP allows you to modularize these concerns into "aspects" and apply them declaratively, keeping your business logic clean.
##### Spring Framework Modules:
- **Spring MVC (Model-View-Controller)**.
- **Spring Data JPA**
- **Spring Security**

- **Spring MVC (Model-View-Controller)**: The module for building web applications and RESTful APIs. It provides the `DispatcherServlet`, which acts as a front controller to manage incoming HTTP requests and delegate them to the appropriate handlers (controllers). Spring Boot heavily simplifies the configuration of Spring MVC.
- **Spring Data JPA**: This is not JPA itself, but a project within the larger Spring Data family that makes it easier to implement JPA-based data access layers. Its most powerful feature is the ability to create repository interfaces that automatically generate database queries from method names, significantly reducing boilerplate code. It simplifies pagination, dynamic queries, and overall database interaction.
- **Spring Security**: A powerful and highly customizable framework dedicated to handling **authentication** (verifying who a user is) and **authorization** (deciding what a user is allowed to do) . It provides comprehensive protection against common security threats like CSRF and session fixation and integrates seamlessly with Spring Boot applications.
##### Related Technologies:
- **Hibernate**
- **REST (Representational State Transfer)**

- **Hibernate**: An **Object-Relational Mapping (ORM)** framework. It is the most popular implementation of the **Java Persistence API (JPA)** specification, which is the standard for mapping Java objects to relational database tables. Hibernate handles the conversion of data between your Java objects and the database, and it features a powerful query language (HQL) and advanced caching mechanisms for performance. Spring Boot uses Hibernate as the default JPA provider.
- **REST (Representational State Transfer)**: An architectural style for designing networked applications. REST is not specific to Spring; it's a set of principles for creating scalable, stateless web services that communicate over HTTP. Spring REST refers to the features within Spring MVC, like the `@RestController` annotation, that make it easy to build RESTful APIs that exchange data in formats like JSON.

---
####  Categories and Explanations

|**Concept/Technology**|**Type**|**Explanation**|
|---|---|---|
|**Inversion of Control (IoC)**|**Design Principle**|Instead of creating objects manually, control of object creation and lifecycle is handed over to a container (like Spring).|
|**Dependency Injection (DI)**|**Design Pattern / Technique**|A way to implement IoC. Spring automatically injects required dependencies (objects) instead of us creating them.|
|**Spring Framework**|**Framework**|Core framework providing support for IoC, DI, AOP, etc. It’s the foundation for all other Spring modules.|
|**Spring MVC**|**Web Framework (part of Spring)**|Builds web applications using the Model-View-Controller architecture.|
|**Spring Data JPA**|**Data Access Abstraction (part of Spring)**|Simplifies database interactions using JPA (Java Persistence API), built on top of Hibernate.|
|**Hibernate**|**ORM Framework**|Maps Java objects to database tables (Object-Relational Mapping), used by JPA/Spring Data JPA underneath.|
|**REST** (Representational State Transfer)|**Architectural Style**|Used to create APIs that work over HTTP (GET, POST, PUT, DELETE). Spring MVC and Spring Boot can be used to build REST APIs.|
|**Spring Security**|**Security Framework (part of Spring)**|Adds authentication, authorization, and protection against attacks like CSRF/XSS to Spring apps.|
|**AOP (Aspect-Oriented Programming)**|**Programming Paradigm**|Used in Spring to handle cross-cutting concerns like logging, transactions, and security (without affecting core logic).|
|**Spring Boot**|**Framework Extension**|Makes it easy to build Spring apps quickly with auto-configuration and embedded servers. Often used with MVC, REST, Security, etc.|
