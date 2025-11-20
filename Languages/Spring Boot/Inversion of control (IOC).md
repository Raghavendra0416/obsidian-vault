While learning IOC learn with these topics:
1. What is IOC?  
2. What is Spring Container?
3. What is Java Beans?
4. What is Configuration meta-data?
5. Declaration of Spring Container?
6. What is resources?
7. What is XML files & how hey are written?
8. What does Spring Container consist?
9. What is Bean factory? Application Context?
10. How do we configure XML Files in Spring?
11. Container for Bean Factory Application context?
12. What layers do we have while working on a project?
13. What are jar & war files?
14. What is Maven & Gradle?
15. How do we download jar files?
16. How does Maven know & download the repaired jar files for the project?
17. What details needs to be given while downloading jar files? and where does these details given?
18. Explanation of .xml file? & What are the important dependencies needed while creating java spring boot project?


**Before Learning IOC understand what is Dependency Injection:**
#### **[[Dependency Injection(DI)]]:**
Injecting dependency of a object from outside is known as Dependency Injection. It reduces the dependency on a single object while creating an object for class and focuses on creating the required objects(instead of depending and creating a single object) during runtime. This will cause loose coupling in java while creating Objects.

How DI can be done? How do we remove the dependency on a single object?
Example: 
	Mobile(Interface)-> 1. AirtelSim--|
					2. IdeaSim---|--->Classes which implements interface.
					3. JioSim-----|

2 Methods to use DI:
		1. Constructor DI(CDI)
		2. Setter DI(SDI)
		Both works same but method names are different & use cases are different.
- Provide object as argument to CDI/SDI. Then they will create the Object.
- No Need to return any values in SOI/CDI.
- The method will create the object during runtime. This is how spring will help to create objects dynamically.

#### Inversion of Control (IOC):
**Inversion of Control (IoC)** in Java is a design principle where the control of object creation and dependency management is transferred from the program (developer) to a framework or container like **Spring**.

IOC will inverts the responsibility of managing the lifecycle of object from application to framework.

- Instead of a class creating its own dependencies, they are provided from outside — typically by a framework.(In interview)
- IoC means the framework controls the flow and dependencies, not the programmer.
- Dependency Injection is one of the most common ways to achieve Inversion of Control in frameworks like Spring.

IOC -(from)-(Giving responsibility & management)-> Application -(to)-> Framework (is a external source..i.e 3rd party)(is in spring).

- Creating (C), Linking(L), Destruction(D) - (C,L,D) - of objects are done by Spring framework.
- Inside Spring framework -> spring container will perform all CLD.
- Spring Container needs **Beans**(Not mandatory as config metadata is given) **& Configuration Metadata** to link the data(i.e variables or any other data in class) between objects after creation.


	               |                        |
Beans                     --->    |      Spring Container             |
				    |                                               |
configuration         --->   |         Obj <-(C,L,D)-> Obj       |
Meta Data                        |                                               |
                    |                                               |

- Beans are not mandatory as most of the data related to linking will be given in configuration metadata.

Configuration Metadata          --------->  1. XML File            ------|
can be supplied in form of 						  2. Annotations      ------|----> Based on these Spring will                                                                     3. Java Code          ------|        perform CLD on Objects                                           
- by representing Spring container we have 2 interfaces:
		1. Bean Factory {Org.Springframework.beans.factory}                 -----|-->Both are  
		2. Application Context {Org.Springframework.beans.Context}    -----|      Interfaces.
Bean Factory -> for simple Application
Application Context -> Enterprise Application

- Through Bean Factory or Application Context, we cannot create Obj. so we use XML Bean Factory or Application Context.
-  These XML files are used to Create Obj for both bean factory & Application context.


**Bean Factory:**
Bean Factory(Interface)                      Resources::
   |-> .XML Bean factory (Sub Class     |-> Class path Resource (same package)
(Will only take resource path as I/P)   |-> File Path Resource (outside of package)

**Application Context:** (No need for resources)
-> ClasspathXMLApplicationContext(Same Package)
-> FileSystemXMLApplicationContext(Outside of package)
-> XML WebApplication Context
-> AnnotationConfigApplicationContext
-> AnnnotationConfigWebApplicationContext
the above are sub classes of Application Context.

Example:
**Bean Factory:**
Resource r= classPathResource("Config.xml"); -> "Config.xml" - file path
                |-> inside same package and this will be changed if it is outside of package.

Beanfactory f = new XMLBeanfactory(r);
  |-> Interface              |-> new object is created using resources

**Application Context:**
ApplicationContext c = new FileSystemXMLApplicationContext("path of the file"); 
  |-> Interface                          |-> new obj is created. This will be changed if the file is in different                                                          location of class or changed based per usage. 
  "path of the file" -> will be changed based location of class & usage.

##### How does a program written? What we need to create Project?
Ans:
- Programs are written in classes and all the classes combined into jar files (package) & war files at the end of the project.
- All files are saved as **".jar files"** after development for "Standalone Projects". for some to use the package when required.
- All files are saved as **".War files"** after development for **"Web Projects"**.
- Once these files are created these can be used by the end user to develop another project.

**Which tools help while downloading jar files?**
Ans:
So, if we are creating a project -> we need specific .jar files (with these files, we don't need to write the code that is already written) according to our project.
Tools:
1. Maven
2. Gradle

Maven:
- Download all the files related to pure java.
- Used when there is a need to create pure java project.
Gradle:
- Download all the jar files related to multiple technology
- Used when there is a need to create project with multiple technologies.

**So How does Maven download jar files? How do we add them in our project?**






