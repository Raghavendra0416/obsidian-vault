- What is List?
- Hierarchy of list interface in java
- Implementation of ArrayList and Vector.
- How to use ArrayList?
- How to use Vector?
- What is Synchronization?
- What is autoboxing & Generics?
- Important points to remember.


#### Vector
- **Vector** is a **legacy class** that implements the `List` interface and uses a **dynamic array** to store elements. It is **synchronized**, which means it is **thread-safe** (only one thread can modify it at a time). It also allows **duplicate elements** and maintains the **order** of insertion.
- Thread-safe (but slower than ArrayList).
- The Vector store elements in horizontal format.
- Initial capacity of vector is 10. At the beginning, while initializing the capacity is 10.
- Automatically grows in size (doubles when full).
- Vector is mostly used when multi threading, Synchronization and data is increased exponentially.
- Mostly replaced by `ArrayList` or other synchronized lists.
- **Remember main diff btwn arraylist & vector:**- Use **Vector** or **Collections.synchronizedList(new ArrayList<>())** when **working with multiple threads**. 

#### ArrayLists
- **ArrayList** is a **resizable array** implementation of the `List` interface in Java. It allows **duplicate elements**, maintains **insertion order**, and provides **fast access** using indexes. It is **not synchronized**, so it is **not thread-safe** by default.
- An **ordered collection** (you can access elements by position/index).
- It **allows duplicate elements**.
- Initial capacity of ArrayList is 0. If even a single value is added then the capacity will be 10.
- **Grows automatically** when elements are added.
- `List` is a **subinterface** of `Collection`.
- Backed by a **dynamic array**.
- **Not synchronized** → not thread-safe (faster for single-threaded apps).
- **Remember main diff btwn arraylist & vector:**-  Use **ArrayList** for better performance when **thread safety is not required**.



##### Different ways to initialize Vector:
Syntax:
		Vector Obj_Var_Name=new Vector();
		+ If we initialize it like this - We can add any data type to the object variable(through autoboxing). But if different types of data is used it may cause issues.
		 Vector<"Wrapper Class"> Obj_Var_Name = new Vector<>();
		 + If we initialize it like this - If we use Wrapper class, a single data type can be used while initializing values. (Primitive data types cannot be used in the wrapper class).
	### ✅ For Vectors – 3 Ways to Initialize with Data:

#####  1. Using `add()` after creation (common method):

```java
Vector<Integer> v = new Vector<>();
v.add(1);
v.add(2);
v.add(3);
```

#####  2. Using `Arrays.asList()` with constructor:

```java
Vector<Integer> v = new Vector<>(Arrays.asList(1, 2, 3));
```

- This is the cleanest way to initialize a `Vector` with elements in one line.
- `Arrays.asList()` creates a list which the `Vector` constructor copies.

#####  3. Using instance initializer block (less common, but works):

```java
Vector<Integer> v = new Vector<>() {{
    add(1);
    add(2);
    add(3);
}};
```

- This creates an **anonymous subclass** and adds elements in an **initializer block**. 
- Not generally recommended for production use (creates an extra class), but useful for quick testing or examples.

#### Major Operations:
- **Creation** of list
- **Addition** of elements into the list.
- **Retrieval**l of elements from the list.
- **Deletion** of elements from the list.
- **Verification** of elements in the list.
- **Updating** of elements in the list.


#### Implementation of ArrayList and Vector.
##### Example:
Assume there is a hotel and it has 10 beds at the beginning as it newly build. When 5 costumers arrived hotel owner will give the 1st 5 beds to the customers and the 1st 5 beds will get occupied. if 7 customers arrived to the hotel for beds. 
Case 1:  then the hotel owner will create/build a new hotel with extra 50%(by increasing the count of beds by 5), then the hotel beds will be 15 and the beds will be sufficient.   
Case 2: then the hotel owner will create/build a new hotel with extra 100%(by increasing the count of beds by 10), then the hotel beds will be 20 and the beds will be sufficient.   

**ArrayList:** Assume the number of beds as Arraylist and for ArrayList the 50% of array size will be increased. for example if the size of array list is 15 and divided by 50% it is 7.5, then it will round up to 7, and increase the arraylist size 15+7=22. Total number beds are 17.

**VectorList:** Assume the number of beds as Vector and for Vector the 100% of array size will be increased. for example if the size of array list is 10 and divided by 100% it is 10, and increase the VectorList size by 10 i.e 10+10=20. Total number beds are 20.


![[Pasted image 20250514203205.png]]

#### Important points to remember:
- Interview Question: 
	- What is generics in java and why they are introduced?
	- Why we can only use non primitive datatypes inside generics?(Ans: We cannot create objects for primitive data types(as they are predefined), so we have to use non primitive datatypes(Wrapper classes(as we can create objects for classes))).
	- What is Wrapper Class in java?
	- Why we can only use non primitive datatypes inside generics?
- The array list and Vector store elements in horizontal format.
- What is default Capacity of ArrayList & Vector?(When elements not added)
- What is initial capacity?
- Does it allow duplicate elements?
- Does it allow null values?
- Does it maintain insertion order?
- Does it maintain sorted order?
- Does it offer random access of elements?
- is it synchronized?
- What is it good at?