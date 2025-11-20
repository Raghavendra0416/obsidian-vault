- For Multi-Dimensional array:
	- type arr_name**[N]**[M]**;
	- N- Number of columns.
	- M- Number of rows.
	
Let's break this down step by step, starting with the basics and then extending to what **o** and **p** mean in the context of multi-dimensional arrays.

### 1. **`int arr[n][m];`**

This is a **2D array**.

- **n**: This is the number of **columns** in the array. It tells you how many elements there are horizontally (across).
- **m**: This is the number of **rows** in the array. It tells you how many elements there are vertically (down).

So, in a 2D array, you have **m rows** and **n columns**.

**Example**: `int arr[3][4];`

- **3 rows** (vertical direction).
- **4 columns** (horizontal direction).

This creates a grid-like structure, where you can imagine it as a table with 3 rows and 4 columns.

---

### 2. **`int arr[n][m][o];`**

This is a **3D array**. Now, you're adding another level of depth.

- **n**: This is the **number of 2D arrays** in the 3D array. It tells you how many "layers" of 2D arrays you have.
- **m**: This is still the number of **rows** in each 2D array.
- **o**: This is the number of **columns** in each 2D array. It tells you how many elements there are horizontally in each of the rows of your 2D arrays.

So, in a 3D array, you have **n 2D arrays**, and each 2D array has **m rows** and **o columns**.

**Example**: `int arr[2][3][4];`

- **2 layers** of 2D arrays (first dimension).
- Each layer has **3 rows** (second dimension).
- Each row has **4 columns** (third dimension).

This creates a structure where you have 2 "2D tables," each with 3 rows and 4 columns.

---

### 3. **`int arr[n][m][o][p];`**

This is a **4D array**. You’re adding another level of depth.

- **n**: This is the number of **3D arrays** (first dimension). It tells you how many "layers" of 3D arrays you have.
- **m**: This is the number of **2D arrays** in each 3D array (second dimension). Each 3D array contains **m 2D arrays**.
- **o**: This is the number of **rows** in each 2D array (third dimension).
- **p**: This is the number of **columns** in each 2D array (fourth dimension).

So, in a 4D array, you have **n 3D arrays**, each 3D array contains **m 2D arrays**, each 2D array has **o rows**, and each row has **p columns**.

**Example**: `int arr[2][3][4][5];`

- **2 sets of 3D arrays** (first dimension).
- Each 3D array has **3 2D arrays** (second dimension).
- Each 2D array has **4 rows** (third dimension).
- Each row has **5 columns** (fourth dimension).

This creates a structure where you have 2 "groups" of 3D arrays, and each of these groups has 3 "tables" (2D arrays), where each table has 4 rows and 5 columns.

---

### Visualizing the Structures:

#### 1. **2D Array (`n x m`)**:

Think of it like a table:

```
Row1: Element, Element, Element, Element (total n elements)
Row2: Element, Element, Element, Element (total n elements)
Row3: Element, Element, Element, Element (total n elements)
...
(total m rows)
```

#### 2. **3D Array (`n x m x o`)**:

Imagine you have `n` 2D arrays stacked together. Each of those 2D arrays has `m` rows and `o` columns.

```
Layer1 (2D Array):  
Row1: Element, Element, Element, Element  
Row2: Element, Element, Element, Element  
Row3: Element, Element, Element, Element  

Layer2 (2D Array):  
Row1: Element, Element, Element, Element  
Row2: Element, Element, Element, Element  
Row3: Element, Element, Element, Element  
...
(total n layers)
```

#### 3. **4D Array (`n x m x o x p`)**:

Now imagine `n` 3D arrays stacked together. Each 3D array contains `m` 2D arrays, and each 2D array has `o` rows and `p` columns:

```
Group1 (3D Array):  
Layer1 (2D Array):  
Row1: Element, Element, Element, Element, Element  
Row2: Element, Element, Element, Element, Element  

Layer2 (2D Array):  
Row1: Element, Element, Element, Element, Element  
Row2: Element, Element, Element, Element, Element  

Layer3 (2D Array):  
Row1: Element, Element, Element, Element, Element  
Row2: Element, Element, Element, Element, Element  

Group2 (3D Array):  
...
```

### Recap:

- **n**: Represents how many "groups" or "layers" you have (first dimension).
- **m**: Represents how many "2D arrays" each group or layer contains (second dimension).
- **o**: Represents how many "rows" each 2D array has (third dimension).
- **p**: Represents how many "columns" each row of a 2D array has (fourth dimension).

These dimensions just give you more and more levels to organize data. As the number of dimensions increases, you move from simpler structures like tables (2D) to more complex, multi-layered data structures (3D, 4D, etc.).