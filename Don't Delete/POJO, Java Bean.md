POJO:
**POJO** stands for **Plain Old Java Object**.
Simple Java class
Data representation
Used to hold data.
Doesn’t follow any special rules or framework.
Needs Server? - no

**POJO** Basic Rules:
- Private fields
- Public getters and setters
- No business logic
- No need to extend any class or implement interfaces

JavaBean:
POJO with some rules
used in Java-based UI tools and frameworks.
UI tools, JSP/JSF
Needs Server? - no
Follows Rules? Yes (getters/setters etc.)

JavaBean Rules:
1. Must have a **public no-arg constructor**
2. Must have **private fields**
3. Must provide public **getters and setters**
4. Must be **serializable** (usually implements `Serializable` interface)(optional)

