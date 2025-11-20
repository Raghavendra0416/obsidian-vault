- Hierarchy of list Interface in java?
- What is a linked List?
- Implementation of linked List?
- What is Node?
- How to use Linked List?
- Important points to remember?



#### Linked List:
- A **Linked List** is a linear data structure where elements (called **nodes**) are stored in **non-contiguous memory locations**
- Linked List implements **"list interface"** and **"dequeue interface"**. So Linked list can use both list interfaces in lists, as well as dequeue interface from queue.
- Default value/initial capacity of Linked list is 0.
- This works different from arrays. This uses Node concept for adding, removing, getting of elements.
- Each node contains:
	1. **Data**
	2. **Pointer (reference) to the next node**
- We cannot initialize size of array(initial capacity) while creating stack. 

#### Implementation:
- Example:
	 LinkedList<"Wrapper_Class"> Obj_Var_Name = new LinkedList<>();
- Linked list can be written in different forms, then the working of linked list will differ based on usage.
	 Collection<"Wrapper_Class"> Obj_Var_Name = new LinkedList<>();
	 Queue<"Wrapper_Class"> Obj_Var_Name = new LinkedList<>();



#### Creation of Linked List:
Linked list is a combination of multiple Nodes. Node is class. While using LinkedList, a object for Node(for every data we add, a new node is created) will be created. Node contains 3 blocks | 1. Previous Node data | 2. Item data | 3. Next Node data | --> this is the structure and object will have all 3 blocks of data. by linking all these objects, linked list will be created. 

##### Points to Remember:
- We cannot initialize size of LinkedList while creating it. 
- LinkedList is not synchronized. 
- Allow Duplicate elements, follows insertion order, does not follow sorting order.
- Linked List is used when there is need to manipulate the data. | Array List is used when there is need to retrieve or store the data. | Vector is used when there is exponential increase of data.(Multi-Threading) | Stack is used when we want to perform LIFO type of actions.

##### Rules While using Linked List and Adding of Elements:
- Default Size = 0.
- First Node = null; Last Node = null;
- When adding new elements, before adding new element the next node value will be null.

Before link is formed the next value will be null.

![[Pasted image 20250518175606.png]]

After Link is formed the next value will be next node address.

![[Pasted image 20250518175925.png]]


##### Getting the values:
When we tried to get the values from linked List. Linked list will divide the value by 2 and 
- if the target value is less than the result value. then it will start searching from 0 to result value. 
- if the target value is greater than the result value. then it will start searching from last index value to result value. 
Example: 
Size =10 (it has 10 elements)
Case 1: Target value = 4;  Case 2: Target value = 7;
result= 10/2 =5
Case 1: it will search from 0 index to 5 for value 4 in list(if it is in 4 it will return index 4).
Case 2: it will search from 10 index to 5 for value 7 in list(if it is in 7 it will return index 7).


##### Removing of elements:
If an element is removed then the next data address( in deleted node )will be given to next( in previous node )and previous data address(in deleted node) will be given to previous data address (in next node's previous).

![[Screenshot 2025-05-18 181041.png]]


##### Types of Linked Lists
1. **Singly Linked List** – Nodes point only to the next node. 
2. **Doubly Linked List** – Nodes point to both previous and next nodes.
3. **Circular Linked List** – Last node points back to the head.

(If have doubts refer below of the page)
##### 1. Singly Linked List
A **singly linked list** is a linear data structure where each node contains:
- Data
- A reference (or pointer) to the **next** node in the list

🔁 **Traversal**: Only in **one direction** (forward)

##### 2. Doubly Linked List
A **doubly linked list** is a linear data structure where each node contains:
- Data
- A reference to the **next** node
- A reference to the **previous** node

🔁 **Traversal**: In **both directions** (forward and backward)

##### 3. Circular Linked List
A **circular linked list** is a variation of a linked list where:
- The **last node** points back to the **first node**

🔁 **Traversal**: Forms a **loop**, so you can go around the list endlessly  
Can be **singly or doubly** linked.

![[Screenshot 2025-05-20 120733 1.png]]

---
##### Important Points to Remember
- **No random access**: Use loops to traverse.
- **Dynamic memory**: More memory-efficient for insertions/deletions. 
- **Watch for null pointers**: Always check `null` before dereferencing.
- **Tail management**: Maintaining a tail pointer can optimize end insertions.

- **Linked Lists** are useful when **frequent insertions/deletions** are needed.
- Avoid when **random access or search** performance is critical.
- Master **traversal**, **reversal**, **loop detection**, and **recursive operations**.
- Understand **memory and pointer concepts** well.

##### Real-Life Use Cases
- Browser History - Navigating back/forward (Doubly Linked List)
- Undo functionality - Text editors or IDEs
- Music/Video Playlist - Navigate forward and backward
- Memory Management- Free and used memory blocks

##### Key Terminology
- **Node**: Basic element containing data and reference(s).
- **Head**: First node in the list.  
- **Tail**: Last node (its `next` is `null`).
- **Traversal**: Iterating through the list.
- **Insertion/Deletion**: Adding or removing nodes.
- **Null**: Used to indicate end or empty links.
- **Recursive Traversal**: Using recursion to process nodes.

#### Interview Questions – Types and Samples

##### 1. Basic Questions
- What is a linked list?
- What is the difference between arrays and linked lists?
- Types of linked lists and use cases?

##### 2. Implementation
- Write code to reverse a linked list.
- How to detect a loop in a linked list? (Use Floyd’s Cycle Detection Algorithm)
- Implement insertion/deletion at: 
    - Beginning    
    - Middle    
    - End
    
##### 3. Tricky/Advanced
- Find the middle element of a linked list.
- Merge two sorted linked lists.
- Find the nth node from the end.
- Remove duplicates from a linked list.
- Check if a linked list is a palindrome.

##### 4. Conceptual
- What is the time complexity of different operations?
- How does garbage collection work with linked lists?
- When would you use a linked list over other data structures?


Great question! Let's break it all down step by step: the difference between using `get(index)` in a **linked list** vs. an **array**, why it's not efficient, and understand the **3 types of linked lists** with real-life analogies.

---


###  Key Difference:

- **Array / ArrayList**:
    - Stored in **contiguous memory**.
    - Access by index is **instant** (O(1) time).
    - Example: `arr[5]` directly goes to the 6th element.    
- **Singly Linked List**:
    - Nodes are scattered in memory.     
    - Each node only has a **reference to the next**.    
    - To reach index 5, you must **start at the head and follow 5 `next` pointers** (O(n) time).     

###  Real-Life Analogy

Imagine a **train**:
- **Array**: You’re at a train station, and all carriages are visible. If you want the 5th carriage, you just **walk directly** to it.
- **Linked List**: You’re in the **first carriage**, and there are **no labels** or bird’s-eye view. To reach the 5th carriage, you must **walk from the first, then to the second, third**, and so on.

That’s why in a singly linked list, you **can’t jump** to the 5th element directly — you must **traverse**.


### ✅ What About `get(index)`?

If you're using **Java's built-in `LinkedList<E>`** (which is a doubly linked list), you **can** write:

```java
linkedList.get(5);
```

But under the hood, it still starts at the **beginning or end** and walks node by node — so it's **O(n)** time.

---

####  Types of Linked Lists and Real-Life Examples

#### 1. Singly Linked List

**Structure**:  
Each node points to the **next** node.

**Example**:

```text
[1] -> [2] -> [3] -> [4] -> null
```

**Real-Life Analogy**:  
A **chain of paper tickets** where each ticket tells you where to find the next one.

**Use Cases**:
- Simple data structures where only forward traversal is needed.  
- Stack implementation (Last In, First Out). 
- Stream processing (e.g., message queues).

#### 2. Doubly Linked List
**Structure**:  
Each node has pointers to **next** and **previous** nodes.
**Example**:

```text
null <- [1] <-> [2] <-> [3] <-> [4] -> null
```

**Real-Life Analogy**:  
A **subway train** where you can walk both forward and backward between carriages.
**Use Cases**:
- Browser history (forward and back).
- LRU Cache (Least Recently Used).
- Implementing deque (double-ended queue).
#### 3. Circular Linked List
**Structure**:  
The last node points back to the **first node**.
**Singly or Doubly Circular** possible.
**Example**:

```text
[1] -> [2] -> [3] -> [4] -> (back to [1])
```

**Real-Life Analogy**:  
A **merry-go-round** or **carousel** — you can keep going around in a loop.
**Use Cases**:
- Round-robin scheduling (e.g., CPU scheduling).
- Multiplayer board games (turn-based systems).
- Music playlists that repeat.
####  Summary Chart

|Type|Direction|Real-Life Analogy|Use Cases|
|---|---|---|---|
|Singly Linked List|Forward only|Chain of papers|Simple stacks, queues|
|Doubly Linked List|Forward/back|Subway train with two doors|LRU Cache, browser history|
|Circular List|Looping|Carousel or game turn tracker|Scheduling, media players, game logic|
