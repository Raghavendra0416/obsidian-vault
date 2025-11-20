Arrays:
		+ Similar type of data.
		+ Different types of data:
			Single Dimension Array
			Multi-Dimension Array-
				- 2D Array
				- Jagged Array

| **Method**                  | **Java Syntax**                                                           | **C Syntax**                                                                             |
| --------------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Using `new` keyword**     | `int[] arr = new int[5];`                                                 | `int arr[5];`                                                                            |
| **Direct Initialization**   | `int[] arr = {1, 2, 3, 4, 5};`                                            | `int arr[] = {1, 2, 3, 4, 5};`                                                           |
| **Using `new` with Values** | `int[] arr = new int[]{1, 2, 3, 4, 5};`                                   | `int arr[] = {1, 2, 3, 4, 5};` (same as above)                                           |
| **Using `for` loop**        | `int[] arr = new int[5]; for (int i = 0; i < 5; i++) { arr[i] = i * 2; }` | `int arr[5]; for (int i = 0; i < 5; i++) { arr[i] = i * 2; }`                            |
| **Using `Arrays.fill()`**   | `Arrays.fill(arr, 10);`                                                   | Not directly available in C, need a loop: `for (int i = 0; i < 5; i++) { arr[i] = 10; }` |

#### What difference will it make by declaring object and without declaring object for an array?

Ans: When you declare an array with an object (using `new`), it creates the actual array in memory, and you can then store values in it. Without declaring an object (just declaring the array), it only defines the reference to the array but does not allocate memory for the actual array elements, leading to a `NullPointerException` if you try to access it before initializing it.

Example with object declaration:

```java
int[] arr = new int[5]; // memory allocated
```

Example without object declaration:

```java
int[] arr; // only declares the reference, no memory allocated
```


Different ways to declare arrays in Java:

| **Syntax**                                             | **Description**                                                                      | **Example**                                  |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------ | -------------------------------------------- |
| `type[] arrayName;`                                    | Declaring an array where the type of elements is specified before the variable name. | `int[] numbers;`                             |
| `type arrayName[];`                                    | Declaring an array where the type of elements is specified after the variable name.  | `int numbers[];`                             |
| `type[] arrayName = new type[size];`                   | Declaring and initializing an array with a specified size.                           | `int[] numbers = new int[5];`                |
| `type[] arrayName = {value1, value2, ...};`            | Declaring and initializing an array with specific values.                            | `int[] numbers = {1, 2, 3, 4, 5};`           |
| `type arrayName[] = {value1, value2, ...};`            | Declaring and initializing an array with specific values (alternative syntax).       | `int numbers[] = {1, 2, 3, 4, 5};`           |
| `type[] arrayName = new type[] {value1, value2, ...};` | Declaring and initializing an array without explicitly specifying the size.          | `int[] numbers = new int[] {1, 2, 3, 4, 5};` |

