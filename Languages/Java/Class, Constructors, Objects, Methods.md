- Class:
	  + Class is blueprint for creating objects.
	  + It defines the structure and behavior that the objects created from the class will have.
	  + We can call one class data from another class.
	  + Example: let us assume a house and to build it we will create a blue print. Class is similar to that(Class is blue print). we cannot sleep or feel the objects in the house as it is a blue print(yet to construct). to use the objects in the house, we need objects(i.e.. object in class), and every object has a functionality(i.e.. methods in class).
	  + Syntax:
		  class class_Name {
		  //if needed variables
		  //methods
		  //main method
		  }
- Constructors:
		+ Constructors are used to allocate memory to objects.
		+ Constructor is a special method, mainly used to create and initialize objects from a class.
		+ If the User does not create constructor, java will create a constructor itself.
		+ There are 2types of constructor - 1. Implicit or Default Constructor,  2. Explicit Constructor.
		+ **Implicit Constructor:** if a java creates constructor itself then it is implicit constructor.(Java Itself). Will always starts with public. starts with class name. no return type.
		+ **Explicit Constructor:** if constructor created by user  then it is known as Explicit constructor.(Created by User). If we define constructor, java won't add them.
		+ **Overloading**: You can have multiple constructors with different parameters in the same class. This is called **constructor overloading**.
		+ How to provide different explicit constructors in program?
		  Ans: By adding parameters in the parenthesis, java can differentiate the constructors.
		+ Once Constructor is created by user(with. or without parameters), java will not create default constructor.
		+ Syntax:
			public/static class_Name {
			//if any variables needs be initialized or functionality can be written here.
			}
			class_Name obj(Object) = new class_Name(); (Class name after new is constructor)
			
	 **"[This" Keyword:** ](https://www.youtube.com/watch?v=RzxX-HtIlpY&ab_channel=HYRTutorials-Telugu)
			- before understanding this keyword understand what is instance. 
			1. What is this keyword? why do we need it?
			Ans: Instance variable: non static variables in class are called as instance variables. Instance variables describe the object's state. **Instance variables** belong to individual objects of the class. This means that to access or modify an instance variable, you need to have an object of that class.
			this Keyword:
				+ reference variable that refers to the current instance (or object) of a class.
				+ `this` points to the object that is currently calling a method or constructor.
			    + This Keyword points to instance variable.
			    + this keyword will not create additional object
			    + "This" can be used in non-static methods/blocks, constructors, abstract classes, interfaces(private & default methods).
			    + "This" cannot be used in a static context because static methods or blocks are not tied to a specific instance of the class. Thus, there is no "current object" to refer to.
			    + in interfaces "This" keyword is used to get the details of class that has implemented interfaces.
			    + learn memory management for understanding memory allocation of this keyword.
			
			2. Limitations of this keyword?
			3. Understand memory management while using this keyword?

- Objects:
- Methods:
