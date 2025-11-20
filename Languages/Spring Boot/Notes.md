#### **Tight Coupling & Loose Coupling:**
**Tight coupling means classes are heavily dependent on each other, while loose coupling means classes have minimal dependencies and interact through interfaces.**

##### Tight Coupling
- **What**: Classes know too much about each other's internal details
- **Problem**: Hard to change, test, and maintain
- **Example**: `Car car = new Car(); Engine engine = new Engine();` - Car directly creates Engine
##### Loose Coupling
- **What**: Classes depend on abstractions (interfaces), not concrete implementations
- **Benefit**: Easy to change, test, and maintain
- **Example**: `Car car = new Car(engine);` - Car receives Engine through constructor

Example:

```java
// Tight Coupling - BAD
class Car {
    private Engine engine = new Engine(); // Hardcoded dependency
}

// Loose Coupling - GOOD  
class Car {
    private Engine engine;
    
    public Car(Engine engine) { // Constructor Dependency injection
        this.engine = engine;
    }
}
```

In the above for 
tight coupling the Engine is dependent on engine, we have created a object for class Engine and we are using that object to fetch the data of the Engine. here the Engine is dependent on Engine (we can only assign data related to Engine to engine var and we cannot assign any other class objects. if we need to assign other classes objects we need to create objects for it which causes tight coupling). But we need less dependency, so we have to use dependency injection. this will reduce the dependency.

