#### 1. What is Bit Manipulation?
Bit manipulation is the process of using special operators (like `&`, `|`, `^`, `<<`, `>>`) to directly control the individual 1s and 0s that make up a number.

0 - is even & it is positive.
1 - is odd & it is negative.

**Hamming Weight** - The number of "1"s (ones) within that string. It is also known as the population count or bit count.
For example:
- The Hamming weight of "10110" is 3, because there are three "1"s in the string.
- The Hamming weight of "00000" is 0.
- The Hamming weight of "11111" is 5.

while performing Bit Manipulation and we need to do 2's complement we can just use '-' before the number, then the number will be 2's complemented.
	'-' this is the 2's complement representation. The computer did it for us when we used the `-` operator.

& - Used to check the bit.
| - Used to set the bit
^ - Used to where it is different 
Using the 2’s-complement negative `-xor1` is a neat bit-hack that isolates the rightmost set bit of `xor1` in O(1)

---

Bit Masking:
The main technique is called **Bit-masking**, where you use one number (the "mask") to change or check the bits in another number.

We use mask to alternate the other numbers / manipulate other numbers or bits. 
**Example:**
```JavaScript
// To turn on the bit use or operator
  00000000  (current lights)
| 00000100  (our mask)   | -> or operator
----------
= 00000100  (new state: 3rd light is ON)
// To turn off the bits use and operator
00000100 (current lights) 
& 11111011 (our mask) 
---------- 
= 00000000 (new state: 3rd light is OFF)
```

```JavaScript
// To Check if a Bit is ON use and operator
00000100 (current lights) 
& 00000100 (our mask) 
---------- 
= 00000100 (This is not 0, so... YES, it's on)
//To check if the is off
00000000 (current lights) 
& 00000100 (our mask) 
---------- 
= 00000000 (This is 0, so... NO, it's off)
```

```JavaScript
// To flip a Bit we have to use Xor
00000000 (current state: OFF) 
^ 00000100 (our mask) 
---------- 
= 00000100 (new state: ON) 

00000100 (current state: ON) 
^ 00000100 (our mask) 
---------- = 00000000 (new state: OFF)
```

----
#### 2. Signed vs. Unsigned:

"Unsigned" just means the number **cannot be negative**. It's always positive or zero.
"Signed" means the number **can be positive or negative**.

**The Simple Difference:**
- **Signed:** Is the first bit a `1`? Okay, that's a negative number.
- **Unsigned:** I don't care about the first bit, it's just part of a really big positive number.

n << i -> here n is number to be shifted and i is the positions to be shifted
number needs to be shifted(n) << number to be shifted(i)

##### Do we have signed right and signed left and unsigned right and unsigned left? 
Answer:
**No**, we don't really have four distinct types. There is only **one** left shift operation (`<<`). It _always_ does the same thing: it moves bits left and fills the empty spots on the right with zeros.

The "signed" vs. "unsigned" distinction only matters for the **right shift**.

|**Shift Type**|**Operator(s)**|**How Empty Bits are Filled**|**Key Behavior**|
|---|---|---|---|
|**Signed Left**|`<<`|Fills from the **right** with **zeros (0)**.|Multiplies by $2^n$. The sign _can_ change (this is overflow).|
|**Unsigned Left**|`<<`|Fills from the **right** with **zeros (0)**.|Multiplies by $2^n$. **The operation is identical to Signed Left.**|
|**Signed Right** (Arithmetic Shift)|`>>`|Fills from the **left** with the **sign bit**.|Divides by $2^n$. **Preserves the sign** of the number.|
|**Unsigned Right** (Logical Shift)|`>>>` or `>>` (on unsigned types)|Fills from the **left** with **zeros (0)**.|Divides by $2^n$. **Does NOT preserve the sign** (negative numbers become positive).|

---
#### 3. Bitwise Operators:
All other bitwise operators (`&`, `|`, `^`, `~`, `<<`) operate on the 32-bit signed integer representation, but there isn't an "unsigned" version of them.
Example: - **`& (AND): `5 & 1` (0101 & 0001) → `1`
		 `|` (OR):** `5 | 2` (0101 | 0010) → `7`

---
#### 4. How does >> and >>> differ and also do we have << and <<< in js?
Answer:
This is a great question about JavaScript's bitwise operators. The key difference lies in how they handle the **sign bit** (the leftmost bit) of a number.

In JavaScript, all bitwise operations are performed on 32-bit signed integers (using two's complement representation).

<<< - this operator does not exist in JS.

| **Operator** | **Name**                         | **Exists in JS?** | **Shift Direction** | **Padding (What new bits are filled with)**             | **Key Difference**                                                               |
| ------------ | -------------------------------- | ----------------- | ------------------- | ------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `>>`         | **Sign-Propagating Right Shift** | **Yes**           | Right               | Copies of the original **sign bit** (leftmost bit)      | Preserves the sign (negative numbers stay negative).                             |
| `>>>`        | **Zero-Fill Right Shift**        | **Yes**           | Right               | Always **0s**, regardless of the sign.(to leftmost bit) | Ignores the sign (negative numbers become large positive numbers).               |
| `<<`         | **Left Shift**                   | **Yes**           | Left                | Always **0s** (on the right side).                      | This is the only left shift operator.                                            |
| `<<<`        | (Zero-Fill Left Shift)           | **No**            | N/A                 | N/A                                                     | This operator does not exist. It's redundant because `<<` already fills with 0s. |

---
#### 5. Is there any shortcut to calculate bit value of an integer? 
for example: if number 5: bit value is 101. how do i as soon i see the number? is there any shortcut or technique to it.
Answer:
The fastest mental shortcut is the **subtraction method**.
You just need to know the basic powers of 2: **... 64, 32, 16, 8, 4, 2, 1**.

Here’s how to do it for any number:
1. Find the **largest power of 2** that fits into your number. Write a `1`.
2. **Subtract** that power of 2 from your number.
3. Move to the **next smallest** power of 2.
4. Does it fit into your new remainder?
    - **Yes:** Write a `1`. Subtract it from the remainder.
    - **No:** Write a `0`.
5. Repeat this process until you get to 1.

In this conversion method, "does it fit?" means in below: "Is this power of 2 less than or equal to your number?" 
**"Does 32 fit into 25?"**
- Is $32 \le 25$?
- **No.** 32 is _larger_ than 25, so we can't subtract it. We write a `0`

Example Input: `5`
1. Powers of 2: (..., 8, 4, 2, 1)
2. Does **8** fit into 5? No.
3. Does **4** fit into 5? Yes.   
    - Write `1`.
    - Subtract: $5 - 4 = 1$. (Your new remainder is 1).
4. Does **2** fit into 1? No.
    - Write `0`.
5. Does **1** fit into 1? Yes.
    - Write `1`.
    - Subtract: $1 - 1 = 0$. (You're done).

**Result: `101`**

Example Input: `25`
1. Powers of 2: (..., 32, 16, 8, 4, 2, 1)
2. Does **32** fit into 25? No.
3. Does **16** fit into 25? Yes.
    - Write `1`.
    - Remainder: $25 - 16 = 9$.
4. Does **8** fit into 9? Yes.
    - Write `1`.
    - Remainder: $9 - 8 = 1$.
5. Does **4** fit into 1? No.
    - Write `0`.
6. Does **2** fit into 1? No.
    - Write `0`.
7. Does **1** fit into 1? Yes.
    - Write `1`.

**Result: `11001`**

---
#### 6. What is mask in bit manipulation? and where do we use this term usually in bit manipulation? 
Answer:
- A **bitmask** (or "mask") is a number—usually an integer—whose binary pattern is used to select, change, or check specific bits within another number.
- You use it with bitwise operators (`&`, `|`, `^`) to perform three main actions:
	1. **Checking a bit (using `&`)**: To see if a specific bit is "on" (1).
	    - `value & MASK` (If the result is non-zero, the bit was on).
	2. **Setting a bit (using `|`)**: To force a specific bit to be "on" (1).
	    - `value = value | MASK`
	3. **Clearing a bit (using `&` and `~`)**: To force a specific bit to be "off" (0).
	    - `value = value & ~MASK`
It's most commonly used for storing multiple Boolean (true/false) options, called **flags**, within a single number. For example, instead of 8 Boolean variables, you can use one 8-bit number where each bit represents one option. This is common in file permissions, system settings, and computer graphics.

---
#### 7. Is there any shortcut technique calculate bit manipulation? for checking bit and setting bit, clearing bit? 
Answer:
Let `n` be the bit position you want to manipulate (counting from 0 on the right).
**The Mask:** `let mask = 1 << n;`

- **Check Bit $n$:**
    - `if ((value & mask) != 0)`
    - Uses **AND**. If the result is not zero, the bit was set (1).

- **Set Bit $n$ (to 1):**
    - `value = value | mask;`
    - Uses **OR**. This forces the $n^{th}$ bit to `1` and leaves all other bits unchanged.

- **Clear Bit $n$ (to 0):**
    - `value = value & ~mask;`
    - Uses **AND** with an **inverted mask** (`~`). This forces the $n^{th}$ bit to `0` and leaves all others unchanged.

- **Toggle Bit $n$ (flip):**
    - `value = value ^ mask;`
    - Uses **XOR**. This flips the $n^{th}$ bit (0 $\rightarrow$ 1 or 1 $\rightarrow$ 0) and leaves all others unchanged.

