#### Step 1:
Theoretically: 
                      |                                  |
Config Meta data(XML)-->|   Obj <--> Obj          |
                      |   Spring Container    |

Understanding:
- Spring container plays important roles in Creating, Linking, deleting of Objects for Class.
- DI  is injecting Objects in runtime, dynamically - loose coupling. This can be achieved by using setter & constructor injection. [[Dependency Injection(DI)]]
- IOC tells us to let the task of creating objects & linking & deleting objects should be given to 3rd party (Spring Framework-> spring container).
- So for Spring container to understand or assign the values(If mobile is Obj then int simnumb; Jio sim Jsim;) inside the object, it should have config meta data as input.
- Config metadata can be in format of:
	- XML file
	- Annotations
	- Java Code.
- So Before creating xml,  Java beans need to be created.
- Java beans(POJO Class) will create a basic classes we specify the information in the xml file.
- So before creating XML, Create JavaBeans(POJO Classes) and in XML we have to specify which values need to be assigned to variables & objects for those classes.

#### Step 2:
**Create Java Beans**
- We are Using Setter DI(Which has Setters and getters method to fetch the data). We can also use Constructor DI( A little bit Different form Setter DI).
- Create a java class & every variable in the class needs to be private.
- To access those variables(private), create getters & setters(these are public) methods for every variable.
- This is used to define the value is assigning to clas variable.
Example: 

```java
package com.pa....packagename;

public class Customer{
Private String name;
Private String contact;
Private string Address;

//getters & setters for private variables

public void setName(String name){
	this.name=name;
}
public void getName(){
	return name;
}
//Create Public getters and setters methos for all variables in class same as above.
}
```

- Create another class according to requirement.

```java
package com...packagename..;
import java.util.Date;

public classOrder{
private String productId;
private String productName;
private Date orderDate;
Private Customer customer;

// create getters and setter methods for all variables.

}
```

#### Step 3:
Create XML file & provide the required details in the file.
- Create a new file.
- When file is created it will have < ? XML Version="1.0" encoding = "UTF-8"? >
- Provide the structure for XML file.
```HTML
<beans xmlns=....>
	<bean>    ---| --> Provide what data needs to be assigned.
	</bean>   ---|
</beans>
```

What type of data do we have when providing:
1. Primitive Data types
2. Collections
3. References(Objects of another classes)

- for the above 3 types of data has different ways of configurating data in the XML File.


##### Primitive Data Types:
- In 3 ways we can provide:
		1. As Element
		2. as Attribute
		3. P Schema.

Example: 
```HTML
<beans xmlns= ... xmls:p="link" Structure>
	<bean name="Cus" class="packagename.class(full package name with class name)">
	// the below is As Element
	<property name="name">
		<value> Raghavendra</value>
	</property> 
	// the below is As Attribute
	<property contact = "contact" value="1234"/>
	</bean>
</beans>
```

- In P schema we can declare everything in bean, for that we need some information and links in beans tag(not bean).
```HTML
<beans .....>
	<bean name="cus" class "package full name.class name" p:name="Ragavendra" p:contact="1234" p:address="rjy"/>
</beans>
```

p: will take & assign the values to variables. But for that some knid of link & something needs to be given inside "beans"(not bean).


#### Step 4:
Create Spring Container in main class
- While using Spring container import required data to the program(like Date & Time).

```java
// Create Spring Container
ApplicationContext.context = new classpathXMLAplicationsContext("XML File path");
// to get customer Object & check if we were able to create Object we have to:
Customer customer =(Customer) context.getBean("cus"); 
					//|-> This type of typecasting is needed for converting Object to Customer Object.
// ->this context.getBean("cus") will return Object. cus- by name it will create Object & we will fetch the data.
System.out.println("Name" + customer.getname());
System.out.println("Contact" + customer.getContact());
System.out.println("Address" + customer.getAddress());
// |-> we are getting above details of customer through getters methods we have created in class.
```

#### Injecting Collection Objects in Spring:

- We inject in form of
	 1. Lists
	 2. Sets
	 3. Maps
	 4. Properties

List Example:

```java
package com.pa....packagename;

public class Customer{
...
...
List<String> address; //-> we are declaring address as List here for example

//setters and getters methods.
....
....
}
```

```XML
<property name="address">
	<list>
		<value>Vskp</value>
		<value>Hyd</value>
		<value>Chennai</value>
	</list>
</property>
```

Set Example:
- Set is similar to list but we have to use ``` <set> Value tags </set>``` instead of ```<list> value tags </list>```.

Map Example:
- Map has key and value pair so we have to use as below

```XML
<property>
	<map>
	<entry key="Home" Value="Vskp" />
	<entry key="Ofc1" Value="Hyd" />
	<entry key="of2" Value="Kkd" />
	</map>
</property>
```

Properties Example:

```Java
package com.pa....packagename;

public class Customer{
...
...
properties address; //-> we are declaring address as properties here for example

//setters and getters methods.
....
....
}
```

```XML
<property name="address">
	<props>
	<prop key="Home"> Vskp<</prop>
	<prop key="ofc"> Hyd<</prop>
	</props>
</property>
```

#### Injecting References(Classes):
- References are injected in the same way as collections and data types. But there is small change needs to be noted.

Example:
```XML
<bean name="ord" class="com.twg...class path... Order">
	<property name="productid">
		<value>p123</value>
	</property>
	<property name="productName">
		<value>Apple MacBook</value>
	</property>
	<property name="customer">
		<ref bean="cus"></ref> --> this is the name of customer class that we have used in XML(same file). Through this name "cus" it will redirect in same xml file and take cus class.
	</property>
```


#### Creating Java Bean and XML using Constructor:
- In Step2 we have used setter DI here we are using Constructor DI
- Constructor does not need getter methods but to check if the values are set to data we can use "toString" methos -> to print all the variables data.
- In the class, if there are 2 constructors then xml will check the number of arguments and based on that it will select which constructor it has to assign the values.
- In a constructor if we have 2 strings and one integer as arguments, then XML will assign values according to the order we have given - even if it is wrong order(if they are same data type or else will throw error) . to over come it we have to give the variables values in order(in XML) or define data type of variable (in XML) or define index of values(in XML).
- **Constructor Injection:** Dependencies are **required** for the object to even exist. The object is created in a fully valid state.
- **Setter Injection:** Dependencies are **optional** for the initial creation. The object is built first and then configured.

Example:

```java
Order.Java -> class

import util.Date;
Public class Oder{
	private String productID;
	private String productName;
	private Customer customer;

	public Order(String productId,String ProductName,Customer customer){
		this.productid=productId;
		this.productname=productName;
		this.customer=customer;
	}

	@Override
	public String toString(){
		return "Order["productId="+productId+",ProductName="]"
	}

public String toString() {
return "Order [productid=" + productid + ", productname=" + productname+", Customer=" +customer+", getClass ()=" + getClass() +", hashCode()="+ HashCode()+",toString()="+Super.toString()+"]";
}
```

```XML
<bean name="ord" class="com.twg......classPath...Order">
	<Constructor-arg value ="p123" type="java.lang.String" index="0"/>
	<Constructor-arg value ="JavaCourse" type="java.lang.String" index="1"/>
	<Constructor-arg ref="cus" index="2"/>
</bean>
```




#### Why Constructor Injection Doesn't Need a "Getter Check"?
Ans:
With **constructor injection**, you are declaring that an object **cannot be created** without its dependencies. The dependencies are required ingredients.

Think of it like baking a cake . The recipe says you _must_ have flour to make the cake batter.
- **The Constructor:** `public Cake(Flour flour, Sugar sugar)`
- **The Dependency Injection (DI) Framework:** This is your baker. It gathers the flour and sugar _before_ trying to make the cake.

If the baker can't find the flour (the dependency), it can't even start making the cake. The process fails right there, and your application will likely crash on startup with an error message like "Could not find a bean for Flour."

You will never end up with a `Cake` object that is missing `Flour`. Therefore, there's no need to ask the cake, "Hey, did you get the flour?" **If the cake exists, it has the flour. Guaranteed**

#### How This Differs from Setter Injection?
Ans:
With **setter injection**, the object is created first, and _then_ its dependencies are provided through setter methods.

This is like baking a plain sponge cake first and _then_ having the baker add frosting and sprinkles later.
- **The Constructor:** `public Cake()` // Creates an empty cake.
- **The Setter:** `public void setFrosting(Frosting frosting)`
- **The DI Framework:**
    1. Creates an empty `Cake` object.
    2. Finds the `Frosting` dependency.
    3. Calls `cake.setFrosting(frosting)`.

Here, there's a tiny moment where the `Cake` object exists without its `Frosting`. This is why the idea of "checking" with a getter feels more natural. However, a good DI framework still ensures this setter method is called, so you rarely need to check it yourself.

##### Example for above questions:

_Note: In a real application, a Dependency Injection (DI) framework like Spring would automatically create and "inject" these objects for you. This example shows what the framework does behind the scenes._

###### **Constructor Injection: The 'Must-Have' Ingredient:**

With constructor injection, the `Cake` **cannot be created** without its required ingredient, `Flour`. The dependency is **mandatory**.

Step 1: Define the dependency (the ingredient).
This is just a simple class representing our ingredient.

```Java
// The dependency
class Flour {
    @Override
    public String toString() {
        return "All-purpose flour";
    }
}
```

Step 2: Define the main class (Cake) that needs the dependency.
Notice the constructor public Cake(Flour flour). This is the only way to create a Cake. There is no empty new Cake() constructor.

```Java
// The class that needs the dependency
class Cake {
    // It's common to make the dependency 'final' because it won't change after creation.
    private final Flour flour;

    // The ONLY way to create a Cake is by providing Flour in the constructor.
    public Cake(Flour flour) {
        this.flour = flour; // The dependency is assigned here.
        System.out.println("Cake created successfully with: " + this.flour);
    }
}
```

Step 3: See it in action (what the DI framework would do).
To create a Cake, we must first have Flour to pass to its constructor.

```Java
public class Baker {
    public static void main(String[] args) {
        // First, get the required ingredient.
        Flour myFlour = new Flour();

        // Now, create the cake by passing the ingredient to the constructor.
        Cake myCake = new Cake(myFlour);

        // This would cause a compile-time error because there's no such recipe (constructor):
        // Cake anotherCake = new Cake(); // ERROR!
    }
}
```

Result:
The program runs and prints:
Cake created successfully with: All-purpose flour
You can't even run the program if you try to make a cake without flour. The existence of the `myCake` object is your 100% guarantee that the `flour` was injected.

###### **Setter Injection: The 'Optional' Topping:**

With setter injection, the `Cake` is created first as a plain object. Then, a "setter" method is called to add the `Frosting` dependency. The dependency is added **after creation**.

**Step 1: Define the dependency (the topping).**

```Java
// The dependency
class Frosting {
    @Override
    public String toString() {
        return "Vanilla frosting";
    }
}
```

Step 2: Define the main class (Cake) that can receive the dependency.
Notice it has an empty constructor public Cake() and a separate method setFrosting().

```Java
// The class that can receive the dependency
class Cake {
    private Frosting frosting; // Not 'final', because it's set after creation.

    // First, a plain cake is created with an empty constructor.
    public Cake() {
        System.out.println("A plain cake was created...");
    }

    // Later, a setter method is called to add the frosting.
    public void setFrosting(Frosting frosting) {
        this.frosting = frosting;
        System.out.println("...and now it's decorated with: " + this.frosting);
    }
}
```

Step 3: See it in action (what the DI framework would do).
This is a two-step process: first create the object, then call the setter to inject the dependency.

```Java
public class Baker {
    public static void main(String[] args) {
        // Step 1: Create the plain cake. It exists, but without frosting.
        Cake myCake = new Cake();

        // Step 2: Create the dependency and "inject" it using the setter method.
        Frosting myFrosting = new Frosting();
        myCake.setFrosting(myFrosting);
    }
}
```

Result:
The program runs and prints in two stages:
A plain cake was created...
...and now it's decorated with: Vanilla frosting
Because the `Cake` can exist without `Frosting` for a moment, it feels like you might need a "getter" to check. But in a real application, the DI framework guarantees to call the setter for you.

----



 


