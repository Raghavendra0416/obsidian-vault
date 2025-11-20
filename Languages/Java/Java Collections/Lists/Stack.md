- Hierarchy of List Interface in Java
- What is a Stack
- Implementation of Stack
- How to use Stack?
- Special methods available in Stack?
- Important points to remember?


#### Stack:
- A Stack is a linear data structure that follows the LIFO (Last In, First Out) principle.
- Stack is a class in java which implements the list interface and extends the vector class and also represents the LIFO principle.
- Stack extends Vector.(So Stack will have all the functions of Vector). So Stack can provide all the functions that are performed by Vector.
- 100% capacity increase, initially it will have 10 capacity. (Same as Vector).
- The Stack store elements in Vertical format.
- Stack follows '**LIFO**' - Last In First Out. (Removing of last element first and so on)
- Queue follows **'FIFO'** - First In First Out. (Removing of first element first and so on)

![[Pasted image 20250518122748.png]]

##### Points to remember while using stack:
- The storing of elements will start form 0 and the 0 will be at bottom and upper of 0, 1 will be there, 2,3.... so on.
- We cannot initialize size of array(initial capacity) while creating stack. 
- Stack will not follow LIFO principle if we use basic methods like add(),remove().. like that..
- To follow LIFO principle, stack needs to follow special operations(or methods). 
- Special Operations:
	- **Push()**: Add an item to the top.
	- **Pop():** Remove and return the top item.
	- **Peek():** Return the top item without removing it.
	- **Search():** Search the item in list. start the search of an item form top to bottom. (Searching & indexof will give diff values.)
	- **Empty():** Check if the stack is empty.(empty() & isempty works similar)

Questions:
-  What is default Capacity of ArrayList & Vector?(When elements not added)
- What is initial capacity?
- Does it allow duplicate elements?
- Does it allow null values?
- Does it maintain insertion order?
- Does it maintain sorted order?
- Does it offer random access of elements?
- is it synchronized?
- What is it good at?