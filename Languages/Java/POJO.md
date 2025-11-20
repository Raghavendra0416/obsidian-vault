### Topics:
- What is POJO class.
- Rules for a class to be called as a POJO class.
- Example of POJO class.
- What is a Java Bean class.
- Rules for a class to be called as Java Bean.
- Example of Java bean class.
- Difference Between POJO & Java Bean.

#### POJO:
- POJO - Plain Old Java Object.
- It is a simple object which does not bound to any restrictions.
- POJO is used to keep data private.
- We can use this POJO class as data type. for Ex: if there are so many employees in the organization but for every employee we cannot create class as it will much trouble, so instead of creating class we create data type(POJO class: Which contains name, id, Salary, etc..  ). We can create n no. of objects using the POJO class. 
- A **POJO** is like a basic form or blueprint.
Rules(Mandatory):
- It must be public.
- It shouldn't implement any interfaces.
- It shouldn't extend any classes.
- It shouldn't have any annotations specified.
- It should not have Main method.
- It is recommended to make the properties (instance variables) as private for improved security.
- It can have getters & setters in order to access the properties.

#### Java Bean:
Rules(Mandatory):
- It should implement serializable interface.
- It should have no-args constructor
- All properties(Instance variable) should be private.
- It should have Getters & Setters(Public) in order to access the file properties.
Note: 
- As Java bean uses serialization (Which helps in transfer of data over a data stream to diff server or data base), it is mostly used when transferring data and if we need the data back we have to do de serialization.
- Java bean is an extended version(or subset) of POJO.
- A **JavaBean** is a **standardized POJO**, ready to work with big tools and frameworks.

|**Aspect**|**POJO (Plain Old Java Object)**|**JavaBean**|**What to Remember**|
|---|---|---|---|
|**Definition**|A simple object with no strict rules|A POJO that follows specific conventions|JavaBean is a specialized POJO with added rules for use in frameworks|
|**Field Access**|Fields can be public or private|Fields **must be private**|Encapsulation is **mandatory** in JavaBeans|
|**Getter/Setter Methods**|Optional|**Required** for all properties|Used for accessing fields via frameworks or tools|
|**Constructor**|Can have any constructor|Must have a **public no-argument constructor**|Needed by frameworks for reflective instantiation|
|**Serialization**|Not required|Should **implement `Serializable`**|Helps in transferring or saving JavaBeans across networks or storage|
|**Naming Convention**|No strict rules|Must follow standard JavaBean naming (`getX()`, `setX()`)|Crucial for tools like JSP, Spring, or JSF to detect properties|
|**Used In**|Used for general programming or domain models|Used in Java EE frameworks, GUI tools, and data binding|JavaBeans are designed for **reusability, configurability**, and **tool support**|
|**Flexibility**|More flexible, fewer restrictions|Less flexible due to structural requirements|POJO is simpler; JavaBean is better for integration with Java platforms|


###  Imagine This Scenario for both POJO and JAVA Bean:

You are building a program to manage employee data in a company. Each employee has:
- **Name**
- **ID**
- **Salary**

Now you want to store details of **hundreds or thousands of employees**. Instead of creating a separate class for every employee (which is impossible and inefficient), you create **one POJO class** that acts as a **data template**.

---
####  **POJO Example – A Simple Data Holder**

```java
public class Employee {
    public String name;
    public int id;
    public double salary;
}
```

#####  How it works:
- This class is called a **POJO** (Plain Old Java Object).
- You can now create **many employee objects** using this one class:

```java
Employee emp1 = new Employee();
emp1.name = "Alice";
emp1.id = 101;
emp1.salary = 50000;

Employee emp2 = new Employee();
emp2.name = "Bob";
emp2.id = 102;
emp2.salary = 60000;
```

>  **You can reuse this class to create as many employees as needed**.  
> Think of it like a **custom data type** — just like `int` or `String`, but defined by you.

---
####  **JavaBean Example – A POJO with Rules**

Let’s improve the `Employee` class to follow **JavaBean standards**:

```java
import java.io.Serializable;

public class EmployeeBean implements Serializable {
    private String name;
    private int id;
    private double salary;

    // No-arg constructor
    public EmployeeBean() {}

    // Getters and setters
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }

    public double getSalary() {
        return salary;
    }
    public void setSalary(double salary) {
        this.salary = salary;
    }
}
```

#####  What’s special here?

- All fields are **private**.
- **Public getter/setter methods** are used to access and modify data.
- A **no-argument constructor** is provided.
- Implements `Serializable` so it can be transferred over a network or saved.

#####  How to use:

```java
EmployeeBean emp = new EmployeeBean();
emp.setName("Charlie");
emp.setId(103);
emp.setSalary(70000);

System.out.println(emp.getName() + " earns " + emp.getSalary());
```

---
####  Summary: When to Use What?

|**Use POJO when...**|**Use JavaBean when...**|
|---|---|
|You need a **simple data container**|You're working with **Java frameworks**, UI tools, or serialization|
|You want **less boilerplate**|You need **encapsulation and tool compatibility**|
|No strict coding rules are needed|Frameworks like Spring, JSP, or Hibernate expect bean conventions|
