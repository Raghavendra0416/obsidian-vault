#### Tuple Characteristics in TypeScript (Revision Notes)
- ✅ Tuple is a **fixed-length, ordered collection** of elements.    
- ✅ Each position can have a **different data type**.
- ✅ Type checking is based on the **position (index)** of elements.
- ✅ Provides more strictness than a normal array.
- ✅ Tuple length is known at design time (unless optional/rest elements are used).
- ✅ Elements can be accessed using array indexing.
- ✅ Supports **optional elements (`?`)**.
- ✅ Supports **rest elements (`...`)** for variable-length tuples.
- ✅ Tuples can be used as function parameters and return types.
- ✅ Tuples can have **named elements** for better readability.
- ✅ Tuples are internally represented as arrays in JavaScript.

#### Important Caveat
- ⚠️ Tuples can still use array methods such as:
    - `push()`
    - `pop()`
    - `shift()`
    - `unshift()`
    - `splice()`
- ⚠️ These methods belong to **Array**, not Tuple.
- ⚠️ Using such methods may alter the tuple's intended fixed structure.
- ⚠️ TypeScript allows some of these operations due to JavaScript array compatibility.

#### Making a Tuple Immutable
- ✅ Use the **`readonly`** keyword to prevent modifications.
- ✅ Readonly tuples cannot:
    - Reassign elements
    - Use mutating array methods (`push`, `pop`, etc.)
- ✅ Useful when tuple values should remain unchanged after creation.

#### Tuple vs Array
- **Tuple** → Fixed structure, position-based types.
- **Array** → Variable length, same/general element type.
