- We manipulate bits using formulas.
- Bit manipulation has less space and time complexity.
- here bits are 0's and 1's.
- 0 sign- is positive and 1 sign - is negative
- Here we manage bits 0's & 1's to get the required output.

`BigInt` (suffix `n`) supports `& | ^ ~ << >>` **with BigInt operands only** (no mixing with Number; `>>>` not allowed).

(Formula)
Converting a integer to bit value is: sum of (bit value * 2^bit_index).

Converting 6 to bit
( 0 * 2 ^ 0 ) + ( 1 * 2 ^ 1 ) + ( 1 * 2 ^ 2 ) + ( 0 * 2 ^ 3 ) +........ 
0 + 2 + 4 + 0 = 6.

Signs: 
0 - for positive numbers 
1 - for negative numbers

What happens when right shift or left shift operation happens on an integer (Formula)
Left Shift: (multiplies by 2)
a<< x = a * 2 ^ x
Right Shift: (divide by 2)
a>> x = a / 2 ^ x

the **sign bit**.
- If the leftmost bit is **0**, the number is **positive** (or zero).
- If the leftmost bit is **1**, the number is **negative**.

Examples (using 8-bit numbers)
Look only at the leftmost bit to see the sign:
- **`0`**`000 0101`
    - **Sign bit:** 0 (so it's **positive**)
    - **Value:** 5
    - **Result:** +5
- **`1`**`111 1011`
    - **Sign bit:** 1 (so it's **negative**)
    - **Value:** (In two's complement, this represents -5)
    - **Result:** -5

| **Type**     | **Leftmost Bit is...**                       | **Range of Values (for 8 bits)** |
| ------------ | -------------------------------------------- | -------------------------------- |
| **Signed**   | The **sign** (0=pos, 1=neg)                  | -128 to +127                     |
| **Unsigned** | Just **part of the number** (the 128s place) | 0 to 255                         |
Signed vs. Unsigned Right Shift

This is the most important distinction.
- **`>>` (Signed Right Shift):** This is an _arithmetic_ shift. It shifts bits to the right but **preserves the sign bit** (the leftmost bit).
    - If the number is positive (sign bit is 0), it fills the new empty bits on the left with `0`s.
    - If the number is negative (sign bit is 1), it fills the new empty bits on the left with `1`s, maintaining the negative sign.
- **`>>>` (Unsigned Right Shift):** This is a _logical_ shift. It **always fills** the new empty bits on the left with `0`s, regardless of the number's sign. This can cause a negative number to become a large positive number.

Example:
Let's use `-8`. As a 32-bit integer, its binary representation is: `11111111111111111111111111111000` (which is `-8` in two's complement)
1. **Signed Shift (`>>`)** `let x = -8 >> 2;`
    - **Binary:** `11`11111111111111111111111111110`(bits shift right,`1`s are added to the left to keep the sign)
    - **Result:** `x` is `-2`
2. **Unsigned Shift (`>>>`)** `let y = -8 >>> 2;`
    - **Binary:** `00`1111111111111111111111111111110`(bits shift right,`0`s are added to the left)
    - **Result:** `y` is `1073741822` (a large positive number)

what is mask in bit manipulation? and where do we use this term usually in bit manipulation?
Ans:
A **bitmask** (or "mask") is a number—usually an integer—whose binary pattern is used to select, change, or check specific bits within another number.
(i.e. A bit mask is a powerful technique that is widely used in computer science and programming to manipulate bits. You can think of it as a way to turn on or off specific bits in a binary number.
Bit masks are used for performing bitwise operations, such as **AND**, **OR**, **XOR**, and **NOT**, on binary numbers.)
You use it with bitwise operators (`&`, `|`, `^`) to perform three main actions:
1.  **Checking a bit (using `&`)**: To see if a specific bit is "on" (1).
    * `value & MASK` (If the result is non-zero, the bit was on).
2.  **Setting a bit (using `|`)**: To force a specific bit to be "on" (1).
    * `value = value | MASK`
3.  **Clearing a bit (using `&` and `~`)**: To force a specific bit to be "off" (0).
    * `value = value & ~MASK`
It's most commonly used for storing multiple Boolean (true/false) options, called **flags**, within a single number. For example, instead of 8 Boolean variables, you can use one 8-bit number where each bit represents one option. This is common in file permissions, system settings, and computer graphics.


----

#### Why Bit Manipulation?
- **Speed & memory:** Pack multiple small values into one integer, fast flags, compression-ish tricks.
- **Control:** Parse binary protocols, images, network headers, cryptic interview puzzles.
- **Fun:** Elegant one‑liners (e.g., `x & -x` to isolate the lowest set bit).

Bit manipulation involves working directly with individual bits (0s and 1s) in binary representation of numbers. In JavaScript, numbers are stored as 64-bit floating-point values, but bitwise operations convert them to 32-bit signed integers.

#### Binary Number System Basics
Every number can be represented in binary (base-2):
- Decimal 5 = Binary 101
- Decimal 10 = Binary 1010
- Decimal 15 = Binary 1111
Each position represents a power of 2: `2^3, 2^2, 2^1, 2^0`

#### Bitwise Operators in JavaScript

1. AND Operator (&)
	Returns 1 only if both bits are 1.
```javascript
console.log(5 & 3);  // 1
// 5 = 101
// 3 = 011
// ─────────
//     001 = 1
```

2. OR Operator (|)
	Returns 1 if at least one bit is 1.
```javascript
console.log(5 | 3);  // 7
// 5 = 101
// 3 = 011
// ─────────
//     111 = 7
```

3. XOR Operator (^)
	Returns 1 if bits are different.
```javascript
console.log(5 ^ 3);  // 6
// 5 = 101
// 3 = 011
// ─────────
//     110 = 6
```

4. NOT Operator (~)
	Inverts all bits (also inverts sign).
```javascript
console.log(~5);  // -6
// 5 = 00000101
// ~5 = 11111010 (two's complement) = -6
```

5. Left Shift (<<)
	Shifts bits to the left, filling with zeros.
```javascript
console.log(5 << 1);  // 10
// 5 = 101
// 5 << 1 = 1010 = 10
```

6. Right Shift (>>)
	Shifts bits to the right, preserving sign.
```javascript
console.log(5 >> 1);  // 2
// 5 = 101
// 5 >> 1 = 10 = 2
```

7. Zero-fill Right Shift (>>>)
	Shifts bits to the right, filling with zeros.
```javascript
console.log(-5 >>> 1);  // 2147483645
// Treats number as unsigned
```


#### Checking and Setting Bits

Check if i-th Bit is Set
```javascript
function isBitSet(num, i) {
    return (num & (1 << i)) !== 0;
}

console.log(isBitSet(5, 0));  // true (5 = 101, bit 0 is 1)
console.log(isBitSet(5, 1));  // false (bit 1 is 0)
```

Set the i-th Bit
```javascript
function setBit(num, i) {
    return num | (1 << i);
}

console.log(setBit(5, 1));  // 7 (101 → 111)
```

Clear the i-th Bit
```javascript
function clearBit(num, i) {
    return num & ~(1 << i);
}

console.log(clearBit(5, 2));  // 1 (101 → 001)
```

Toggle the i-th Bit
```javascript
function toggleBit(num, i) {
    return num ^ (1 << i);
}

console.log(toggleBit(5, 1));  // 7 (101 → 111)
console.log(toggleBit(7, 1));  // 5 (111 → 101)
```


#### Common Formulas and Patterns
##### Essential Formulas
1. **Set i-th bit**: `num | (1 << i)`
2. **Clear i-th bit**: `num & ~(1 << i)`
3. **Toggle i-th bit**: `num ^ (1 << i)`
4. **Check i-th bit**: `(num & (1 << i)) !== 0`
5. **Turn off rightmost 1**: `num & (num - 1)`
6. **Isolate rightmost 1**: `num & -num`
7. **Create mask of n bits**: `(1 << n) - 1`
8. **Multiply by 2^n**: `num << n`
9. **Divide by 2^n**: `num >> n`
10. **Check power of 2**: `num > 0 && (num & (num - 1)) === 0`
11. **XOR properties**:
    - `a ^ a = 0`
    - `a ^ 0 = a`
    - `a ^ b ^ a = b`
12. **Two's complement**: `~num + 1 = -num`
13. **Count set bits**: Loop with `num & (num - 1)` until num is 0
14. **Number of subsets**: `2^n = 1 << n`
15. **Get lower n bits**: `num & ((1 << n) - 1)`

##### Key Patterns
- **XOR for finding unique**: Cancels out duplicates
- **AND for checking conditions**: Tests specific bits
- **OR for setting flags**: Combines multiple options
- **Bit shifting for powers of 2**: Fast multiplication/division
- **Masks for extracting bits**: Isolate specific bit ranges


#### Counting Bits
Count Set Bits (Hamming Weight)
```javascript
function countSetBits(num) {
    let count = 0;
    while (num > 0) {
        count += num & 1;
        num >>= 1;
    }
    return count;
}

console.log(countSetBits(7));  // 3 (111 has three 1s)
```

Brian Kernighan's Algorithm (Optimized)
```javascript
function countSetBitsOptimized(num) {
    let count = 0;
    while (num > 0) {
        num &= (num - 1);  // Removes rightmost set bit
        count++;
    }
    return count;
}
```

#### Power of Two Operations:
Check if Number is Power of 2
```javascript
function isPowerOfTwo(num) {
    return num > 0 && (num & (num - 1)) === 0;
}

console.log(isPowerOfTwo(8));   // true
console.log(isPowerOfTwo(10));  // false
```

Find Next Power of 2
```javascript
function nextPowerOfTwo(num) {
    num--;
    num |= num >> 1;
    num |= num >> 2;
    num |= num >> 4;
    num |= num >> 8;
    num |= num >> 16;
    return num + 1;
}
```

##### Swapping and Arithmetic:
Swap Two Numbers Without Temp Variable
```javascript
function swap(a, b) {
    a = a ^ b;
    b = a ^ b;  // b = (a ^ b) ^ b = a
    a = a ^ b;  // a = (a ^ b) ^ a = b
    return [a, b];
}

console.log(swap(5, 10));  // [10, 5]
```

Multiply by 2^n
```javascript
function multiplyByPowerOf2(num, n) {
    return num << n;
}

console.log(multiplyByPowerOf2(5, 2));  // 20 (5 * 4)
```

Divide by 2^n
```javascript
function divideByPowerOf2(num, n) {
    return num >> n;
}

console.log(divideByPowerOf2(20, 2));  // 5 (20 / 4)
```

##### Finding Unique Elements:
Find the Unique Number (When All Others Appear Twice)
```javascript
function findUnique(arr) {
    let result = 0;
    for (let num of arr) {
        result ^= num;  // XOR cancels out pairs
    }
    return result;
}

console.log(findUnique([2, 3, 5, 4, 5, 3, 4]));  // 2
```

#### Bit Masking
Extract Lower n Bits
```javascript
function getLowerBits(num, n) {
    return num & ((1 << n) - 1);
}

console.log(getLowerBits(13, 2));  // 1 (1101 → 01)
```

Create Mask with n Bits Set
```javascript
function createMask(n) {
    return (1 << n) - 1;
}

console.log(createMask(4).toString(2));  // "1111"
```

#### Reversing and Rotating Bits

Reverse Bits of a Number
```javascript
function reverseBits(num) {
    let result = 0;
    for (let i = 0; i < 32; i++) {
        result <<= 1;
        result |= (num & 1);
        num >>= 1;
    }
    return result >>> 0;  // Convert to unsigned
}
```

Check if Bits are Palindrome
```javascript
function areBitsPalindrome(num) {
    let reversed = 0;
    let temp = num;
    
    while (temp > 0) {
        reversed = (reversed << 1) | (temp & 1);
        temp >>= 1;
    }
    
    return num === reversed;
}
```

#### Advanced Techniques

Find Position of Rightmost Set Bit
```javascript
function rightmostSetBit(num) {
    return Math.log2(num & -num) + 1;
}

console.log(rightmostSetBit(12));  // 3 (1100, bit at position 3)
```

Isolate Rightmost Set Bit
```javascript
function isolateRightmostBit(num) {
    return num & -num;
}

console.log(isolateRightmostBit(12));  // 4 (1100 → 0100)
```

Turn Off Rightmost Set Bit
```javascript
function turnOffRightmostBit(num) {
    return num & (num - 1);
}

console.log(turnOffRightmostBit(12));  // 8 (1100 → 1000)
```

#### Gray Code
Binary to Gray Code
```javascript
function binaryToGray(num) {
    return num ^ (num >> 1);
}

console.log(binaryToGray(5));  // 7
```

Gray Code to Binary
```javascript
function grayToBinary(gray) {
    let binary = gray;
    while (gray >>= 1) {
        binary ^= gray;
    }
    return binary;
}
```

#### Subset Generation

Generate All Subsets of a Set
```javascript
function generateSubsets(arr) {
    const n = arr.length;
    const totalSubsets = 1 << n;  // 2^n subsets
    const result = [];
    
    for (let i = 0; i < totalSubsets; i++) {
        const subset = [];
        for (let j = 0; j < n; j++) {
            if (i & (1 << j)) {
                subset.push(arr[j]);
            }
        }
        result.push(subset);
    }
    
    return result;
}

console.log(generateSubsets([1, 2, 3]));
// [[], [1], [2], [1,2], [3], [1,3], [2,3], [1,2,3]]
```

#### Optimization Tricks
Check if Number is Odd
```javascript
function isOdd(num) {
    return (num & 1) === 1;
}
```

Absolute Value of Integer
```javascript
function abs(num) {
    const mask = num >> 31;
    return (num + mask) ^ mask;
}
```

Min of Two Numbers
```javascript
function min(a, b) {
    return b ^ ((a ^ b) & -(a < b));
}
```

Max of Two Numbers
```javascript
function max(a, b) {
    return a ^ ((a ^ b) & -(a < b));
}
```
