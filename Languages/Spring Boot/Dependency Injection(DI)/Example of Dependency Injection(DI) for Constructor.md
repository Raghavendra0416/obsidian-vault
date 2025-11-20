#### Don’t Confuse:

| Term         | Meaning                                                                                        |
| ------------ | ---------------------------------------------------------------------------------------------- |
| **JavaBean** | A simple Java class following the bean conventions (POJO with getters/setters)                 |
| **`@Bean`**  | A Spring annotation used to manually declare a **bean (object) managed by Spring's container** |

#### What is `@Bean` in Spring?

In Spring, `@Bean` is used **inside a configuration class** to tell Spring:

> "Hey, when your container starts, create and manage this object (bean) for me."

#### Example: Using `@Bean` for Constructor Dependency Injection

Let’s go step-by-step with a working example:

#### Step 1: Define Your Service (JavaBean Style)

```java
public class EmailService {
    private String provider;

    public EmailService(String provider) {
        this.provider = provider;
    }

    public void send(String message) {
        System.out.println("Sending via " + provider + ": " + message);
    }
}
```

#### Step 2: Define Dependent Class

```java
public class UserService {
    private final EmailService emailService;

    public UserService(EmailService emailService) {
        this.emailService = emailService;
    }

    public void register(String name) {
        emailService.send("Welcome, " + name);
    }
}
```

#### Step 3: Define Configuration Class Using `@Bean`

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public EmailService emailService() {
        return new EmailService("Gmail");
    }

    @Bean
    public UserService userService() {
        return new UserService(emailService()); // constructor injection
    }
}
```

Here:
- `@Configuration` tells Spring this is a configuration class.
- `@Bean` tells Spring to register the return value as a **Spring Bean**.
- `emailService()` is injected into `userService()` via **constructor**.

#### Step 4: Use Beans in `main()`

```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Main {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        UserService userService = context.getBean(UserService.class);
        userService.register("Raghavendra");
    }
}
```

#### Summary of What You Saw in the Video:

|Concept|Purpose|
|---|---|
|`@Bean`|Tells Spring to manage the object as a bean|
|Constructor|Used to inject one bean into another|
|`@Configuration`|Class that defines beans|
|`ApplicationContext`|Spring's container that manages and wires beans|

#### Final Thoughts:

- The **`@Bean` annotation was used on methods**, not on constructors.
- The constructor is just the **place where injection happens**, but the method that returns the object is what’s marked with `@Bean`.
- This is **manual bean configuration**, common in pure Java Spring apps (alternative to `@Component`, `@Service`, etc.).

Program Examples - [[Creation of Spring project]]

#### Step-by-Step Theory (Refined)

#### **Step 1: Create the Dependency Class**

**Class**: `EmailService`  
**Purpose**: This class performs a specific task (e.g., sending an email).

**What we do**:
- Define a constructor with a parameter (like `provider = "Gmail"`).
- Add a method like `send()` that prints a message.

**This is the class we want to inject into another class**.

#### **Step 2: Create the Dependent Class**

**Class**: `UserService`  
**Purpose**: This class depends on `EmailService` to perform its job.

**What we do**:
- Create a constructor that takes `EmailService` as an argument.
- Store that object in a variable (`this.emailService = emailService`).
- Use it inside a method like `register()` to send a welcome message.

This is the class that needs the dependency to do its work.

---

#### **Step 3: Configuration Class using `@Bean` (Your Doubt)**

**Class**: `AppConfig`  
**Annotation**: `@Configuration`  
**Purpose**: Tell Spring **how to create objects (beans)** and **inject dependencies**.

**What happens here**:
1. Spring sees `@Configuration` → "This class will tell me how to create beans."
2. Inside this class, we create methods annotated with `@Bean`.
    - Each method returns an object (like `new EmailService("Gmail")`).
3. Spring calls these methods **automatically** at startup and stores the returned objects.
4. When `UserService` is being created, Spring sees that it needs an `EmailService` → so it calls `emailService()` method, injects the result into `UserService`.

Think of it like this:

- The `@Configuration` class is a **manual wiring center**.
- Each `@Bean` method says: **“This is how to create this object.”**
- Spring uses it to **create and connect** your objects behind the scenes.

#### **Step 4: Main Class to Run the Program**

**Class**: `Main`  
**Purpose**: Start the app, get Spring to create objects and inject them.

**What happens here**:

1. We create a Spring container using:
    ```java
    ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
    ```
    - This means: "Hey Spring, use `AppConfig` to load all beans."
    
2. We ask Spring for a bean:
    ```java
    UserService userService = context.getBean(UserService.class);
    ```
    - Spring sees: UserService needs EmailService → provides both automatically.
    
3. We call the method:
    ```java
    userService.register("raghavendra");
    ```
    - Which internally uses the injected `EmailService`.

Think of this like:
- **Main method** starts the Spring engine.
- It tells Spring to **read bean instructions from AppConfig**.
- Then asks for the bean you want (`UserService`) — which Spring returns with all dependencies ready.
#### Summary:

| Step   | Description                                    | Real-Life Analogy                                     |
| ------ | ---------------------------------------------- | ----------------------------------------------------- |
| Step 1 | Created a service class (`EmailService`)       | A printer you want to use                             |
| Step 2 | Created dependent class (`UserService`)        | A computer that needs the printer                     |
| Step 3 | Configuration class (`AppConfig` with `@Bean`) | A technician who connects the printer to the computer |
| Step 4 | Main method                                    | You turn on the system and start using it             |

---

![[ChatGPT Image Jul 4, 2025, 01_21_06 AM.png]]

---

#### Break Down of Step 3:

#### What is the purpose of `@Configuration` and `@Bean`?
Imagine this:
- You are the **manager** of a team.
- You need two people: one to **send emails** and one to **register users**.
- Instead of creating them everywhere in your code, you say:  
    **"Hey Spring, when my app starts, please create and manage these people (objects) for me."**

#### `@Configuration` is like a **factory setup**.
- It tells Spring: "This class contains **instructions** on how to create and wire objects (beans)."

#### `@Bean` is like a **machine inside the factory**.
- Each `@Bean` method says: "Here’s how to create one object."

#### Code Step-by-Step (Plain English)

```java
@Configuration
public class AppConfig {
    
    @Bean
    public EmailService emailService() {
        return new EmailService("Gmail");
    }
```

- This tells Spring:  
     “Create an `EmailService` object using the constructor, pass 'Gmail', and manage this object.”

```java
    @Bean
    public UserService userService() {
        return new UserService(emailService()); // inject EmailService into UserService
    }
}
```

- This tells Spring:  
    “Create a `UserService` and give it the `EmailService` we already created above.”

**Spring will automatically call `emailService()` first**, and use its result in `userService()`.

#### What happens internally (Behind the scenes)

1. Spring starts.
2. Sees `@Configuration` → says “Okay, this class contains bean methods.”
3. Sees `@Bean` method `emailService()` → calls it, stores the result as a bean.
4. Sees `@Bean` method `userService()` → calls it, **injects the existing `emailService` bean** as an argument.
5. Now both beans are ready, and Spring manages them.

#### Analogy Summary:

|Role|Real-life Analogy|
|---|---|
|`@Configuration`|Blueprint or factory setup|
|`@Bean`|Factory machines that build objects|
|Spring Container|Factory manager that runs everything|
|`emailService()`|Machine that makes an EmailSender|
|`userService()`|Machine that builds UserService using EmailSender|

---

![[ChatGPT Image Jul 4, 2025, 01_29_38 AM.png]]



#### Notes:

- If Mobile class needs Sim class. 
- We create an object for a class and we can access all the data in the class through the object but if we need another class data we need to create another object and this will cause tight coupling.
- Spring Should be Loose Coupling, this can be achieved by Creating Objects during runtime.
- How Do we create objects during run time? -> by using DI.
- Instead of creating object every time. we use interface to create objects during run time.
- Through this we can dynamically create objects and achieve Loose coupling.
- Wiring and connecting Objects by using special method known as DI.

Example:
- FYI - Constructor and Setter works the same.
For Constructor DI:
- Create class Mobile(main class) & another classes - AirtelSim, JioSim, IdeaSim and an interface- Sim.
-  AirtelSim, JioSim, IdeaSim needs to implement Sim interface.
- Create a variable Sim ar=null; (-> here the Sim is interface)  and  constructor with same class name as Mobile in Mobile class. and the constructor should have Sim s as arguments and ar=s; inside it(below has clear code explanation).
- As we cannot create objects for Interface we create object for mobile class and assign type of sim user wants in run time to the function(i.e new mobile(new AirtelSim()));

```java
//main class
Class Mobile;
{
	Sim ar=null;
	public Mobile(Sim s){
		ar=s;
	}
}
public static void main(String []args){
	Mobile m1= new mobile(new AirtelSim()); // through m1 we can access all the data inside AirtelSim and user can change the type of sim they want during run time.
}
```

```java
//Interface and another classes:
Interface Sim{

}
Class AirtelSim implements Sim{
	
}

Class JioSim implements Sim{
	
}

Class IdeaSim implements Sim{
	
}
```

Setter DI:

```java
//main class
Class Mobile;
{
	Sim ar=null;
	public void setSim(Sim s){
		ar=s;
	}
}
public static void main(String []args){
	Mobile m1= new setSim(new AirtelSim()); // through m1 we can access all the data inside AirtelSim and user can change the type of sim they want during run time.
}
```

```java
//Interface and another classes:
Interface Sim{

}
Class AirtelSim implements Sim{
	
}

Class JioSim implements Sim{
	
}

Class IdeaSim implements Sim{
	
}
```