#### Functional Interface(FI):
A Functional Interface is a Interface which has maximum of **1 Abstract Method & 'n' no. of Non- Abstract Methods.**

- Used to perform Functions.
- Function and Method/Block are different. 
- Function is also a method but, we can pass the function as a parameter to var of interface.
- FI is also called as SAM(Single Abstract Method Interface).
- It was introduced in Java 1.8v.
- Any method written inside interface is automatically abstract method, we don't need to specify Abstract keyword before method.
- **Default, Private Static methods** can have body in Interface.
- @functionalInterface -> Will enforce rules to the interface.
- Rules: 
		1. 1 Abstract Method
		2. N no. of Non- Abstract Methods.
		3. @FI should be used before Interface declaration.
- @FI will be in java.util.function package in java.
- Through FI we can create **Anonymous Classes**.
- With One Method in FI we can create different **Anonymous Classes** in the class that we want.

#### Lambda Expression(LE):
For Detailed Explanation -[[Lambda Expression]]

Syntax:
```java
Interface varName = (Arguments) -> {Function Body};

varName.methodNameinInterface(Arguments); //-> calling method here.
```

- It is way of **reducing the line of code.**
- Java language is usually written in **Verbose** (Meaning: Detail explanation, where to go what to do). But Through lambda we can write Short Code using **Anonymous Function**.
- Arrow Token (->) is used in java to represent it is LE.
- Without FI Lambda Expressions will not work. and FI is mostly used in Lambda expressions.

**Real Life Example why FI is needed in LE:**
I have asked a boy to turnoff the light in another room. But there are different lights in the room. So he will come back and ask which light needs to turn off?.

But if there is only one light in another room, he will simply go and off the light and will come back. Because there is only one light he will understand that he needs to turn that only light in the room. 

Assume that the **Room is Interface and the lights are Abstract Functions.** Java will know which to call when there is only one method in FI. and LE uses FI to to create functions. We don't need to specify the method here.

- Arrow Token (->) is used in java to represent it is LE.
- In Java/ LE if one line needs to be executed there is no need to use braces.
Example:

```java
if(i>1)
	sysout("1 is big");
else
	 sysout("1 is small");
```

Above we did not need braces as it is a single statement. Same for lambda:
```java
Car c2 = ( ) -> sysout("Driving fast");
```

When there is no method name before () how does java know which method to call?
Ans. Java will know because we are using FI. FI only consists of one Abstract method. So it will call that method.

- When defining a variable in LE java will understand which method it is by checking FI & assign the same type  to the variable.
- There is nood to define type of var in LE as it will understand from FI.
Example:
```java
(int s)-> {Function Body}; 

s -> {Function Body};
```
in the above we are defining the s type in LE.

- If there is only one value for return type there is no need to  specify return key word in LE.

```java
s -> return 100; // No need to use return if i value is need to be returned

s -> 100 // This will return 100 without using return keyword
```

Anonymous class can be created like:

```java
Car c1= new Car(){ // Car is FI and getSpeed is Abstract method inside FI.
	public int getSpeed(){
	return 96; 
	}
};

System.out.println(c1.getSpeed()); // will print 96.

// instead of creating Anonymous class like this we use LE. it will be one line code in LE.
```

using LE:

```java
Car c1 = () -> 96; // this will return 96.

System.out.println(c1.getSpeed()); // will print 96.
```


#### For Each method:

- for each loop and for each method are different.
- for each methods is introduced in 1.8 java version. 
- for each methods can only be used in **collections concept**. (Does not work for **Arrays**).
- "**Consumer**" is mandatory in in for each loop. Introduced in java 1.8v.
- Consumer is interface.
- for each method accepts/ takes consumer as a parameter.
- Consumer won't return anything. It will just consume the data.
- If you want to use lambda expression inside for each loop then you can only print and perform action, you cannot return anything because consumer 

Example:

```java
list.forEach(i -> sysout(i)); // will print each element in list.
```

Writing in one line is called **Internal looping mechanism.**
Writing using for/ for each loop is called **External looping Mechanism.**
The body of foreach loop cannot be null.

- Mapping(map collections (K,V)) in foreach method use **"BiConsumer Interface."**

```java
Students.forEach((Key,Value)-> System.out.println(kay+" "+Value));
```
