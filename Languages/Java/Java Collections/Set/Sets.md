Definition:
A _Set_ in Java is a collection that cannot contain duplicate elements. It is part of the Java Collections Framework and extends the Collection interface.

##### Notes through class:
- Java has used maps to create sets. In map we have keys which does not allow duplicates. So java just used that.
- The major operations performed on sets are similar to list (like add(),addall()...).
- Do not use null elements in Sets. because treeset and enumset does not allow null elements.
- so when we are adding elements java will take the elements, java will take the data we have given as keys and dummy objects for values. Java will create one dummy object and will use the same dummy object for all the data(elements) we are adding. ( This is possible because java uses static inside so it will create one dummy object and use it for all).
- Array list uses arrays to store values || LinkedList uses nodes to store values || hash set -(uses)> HashMap -(uses)> Array of nodes(Key, value).
- Hash set does not follow insertion order.(but when it is adding elements it will follow some order internally, for us it is random order)
- while adding elements we add like Var.add(value).
   -> here if you see it is adding a single value but it follows hashmap which has key and value. so when we use add java will add the values that we have given as keys and will create dummy objects for value.
   
![[Pasted image 20250618125222.png]]

- there no updation in Sets 
- for removal and to check contains we have to use the element in parenthesis (cannot remove the element if index is given(no operation will occur)).
- for each loop can be used to fetch data(elements).
Linked hash set:
- linked hash set will implements linked hash map(so will follow insertion order) -> link of nodes(key, value).
- it will follow insertion order
Tree set:
- Tree set implements tree map -> binary tree
- will store data in sorted order.
- extra methods: 
        ts.first -> returns lowest value element
        ts.last -> returns highest value element
        ts. pollFirst, ts.pollLast will remove lowest and highest value element.
        Descending set-> reverse the set elements.
- can create sub sets by using range inside the ts.subset(range1, range 2);
- the subset is not creating a new set, it is just creating virtual set.


![[Pasted image 20250618130151.png]]

![[Pasted image 20250618125211.png]]

#####  Major Operations Performed on Set

|Operation|Method|Description|
|---|---|---|
|Add element|`add(E e)`|Adds an element if not already present|
|Remove element|`remove(Object o)`|Removes the specified element|
|Check contains|`contains(Object o)`|Returns true if element is in set|
|Get size|`size()`|Returns the number of elements in the set|
|Remove all|`clear()`|Clears all elements|
|Iterate|`iterator()` / for-each|Used to loop over elements|
|Add all|`addAll(Collection c)`|Adds all elements from another collection|
##### Important Points to Remember:
- Set **does not allow duplicates**.
- **Insertion order** is **not preserved** in `HashSet` but is preserved in `LinkedHashSet`.
- `TreeSet` stores elements in **sorted (natural) order**.
- Set implementations are **not thread-safe** by default.
- Use `Collections.synchronizedSet()` to make it thread-safe if needed.
- Null handling varies:
    - `HashSet`, `LinkedHashSet`: allow one `null`.  
    - `TreeSet`: throws `NullPointerException` if comparator is used or if null is added.
- Mutable objects as set elements can lead to unpredictable behavior if their state changes after insertion.
##### Comparison Between Set Types (Table Format)

|Feature|HashSet|LinkedHashSet|TreeSet|
|---|---|---|---|
|Order|Unordered|Insertion Order|Sorted (Natural Order)|
|Nulls Allowed|One null allowed|One null allowed|❌ No nulls allowed|
|Duplicates|❌ Not allowed|❌ Not allowed|❌ Not allowed|
|Performance|Fast (hashing)|Slightly slower|Slower (tree-based)|
|Backed By|HashTable|HashTable + LinkedList|Red-Black Tree|
|Use Case|Fast lookups|Maintain order|Sorted data|

##### Most Asked Interview Questions:
- What is a Set in Java?
- Difference between List and Set?
- What is the difference between Set and Map in Java?
- How does HashSet work internally?
- Can Set contain null elements?
- HashSet vs TreeSet vs LinkedHashSet?
- What happens if you add a mutable object to a Set and then modify it?
- How do you perform set operations like union, intersection, and difference in Java?
- How does TreeSet maintain order?
- What is the time complexity of basic Set operations?
- Is Set thread-safe? How to make it thread-safe?