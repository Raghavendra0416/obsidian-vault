- Instead of injecting the dependency via the **constructor**, Spring injects it via a **setter method**.
- The **overall steps are the same**, just the injection **happens in a different place (setters, not constructor)**.
- Setter Injection:
	- Object is first created (with default constructor)
	- Dependencies are injected **afterwards** using setter methods

#### Key Differences

|Aspect|Constructor DI|Setter DI|
|---|---|---|
|How DI is done|Through class constructor|Through setter method|
|When it happens|At object creation|After object is created|
|Spring method call|Calls constructor with dependency|Calls no-arg constructor, then setter|
|Required dependency?|Usually mandatory|Optional|

#### Updated Flowchart (Theoretically)
Here’s what Spring does internally (same idea as the earlier diagram)
1. **Spring starts**
2. Sees `@Configuration`
3. Finds `@Bean` methods
4. Calls the method that returns `UserService`
5. Spring:
    - Creates `UserService` using **no-arg constructor**
    - Calls `setEmailService()` with the injected `EmailService` bean

---
Program Example - [[Creation of Spring project]]
#### Example of Setter Injection in Spring

- another example in [[Example of Dependency Injection(DI) for Constructor]] - at last of the page.
#### EmailService (same as before)

```java
public class EmailService {
    private String provider;

    public EmailService(String provider) {
        this.provider = provider;
    }

    public void send(String msg) {
        System.out.println("Sending via " + provider + ": " + msg);
    }
}
```

#### UserService (with setter)

```java
public class UserService {
    private EmailService emailService;

    public UserService() {
        System.out.println("UserService created");
    }

    public void setEmailService(EmailService emailService) {
        this.emailService = emailService;
    }

    public void register(String name) {
        emailService.send("Welcome, " + name);
    }
}
```

#### AppConfig (Bean Config)

```java
@Configuration
public class AppConfig {

    @Bean
    public EmailService emailService() {
        return new EmailService("Gmail");
    }

    @Bean
    public UserService userService() {
        UserService userService = new UserService();
        userService.setEmailService(emailService()); // Setter Injection
        return userService;
    }
}
```



The **`main()` method** is where:
- You start the **Spring container** using `AnnotationConfigApplicationContext`
- You **get beans** (like `UserService`) from the container
- And then **use those beans** to run your logic

#### `main()` for Constructor DI (or Setter DI) — Looks Like This:

```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Main {
    public static void main(String[] args) {
        // Step 1: Create Spring container using config class
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        // Step 2: Ask Spring for a bean (constructor or setter injected)
        UserService userService = context.getBean(UserService.class);

        // Step 3: Use the bean
        userService.register("Raghavendra");
    }
}
```

#### Whether you're using:

- Constructor Injection
- Setter Injection 
- `@Bean` or `@Component`/`@Autowired`

→ You **always** need a `main()` method (or entry point), unless you're using a web framework (like Spring Boot) where Spring handles it all internally.

Setter Injection changes **only the way Spring wires the object** — not how `main()` behaves.

---

![[ChatGPT Image Jul 4, 2025, 10_55_42 AM.png]]

![[ChatGPT Image Jul 4, 2025, 10_56_05 AM.png]]

---
