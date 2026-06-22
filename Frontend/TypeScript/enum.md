#### Enum Characteristics in TypeScript (Revision Notes)
- ✅ Enum is a way to define a **set of named constants**.
- ✅ Improves **readability** by using meaningful names instead of magic values.
- ✅ Enum members can be accessed using **dot notation**.
- ✅ Supports **numeric enums**.
- ✅ Supports **string enums**.
- ✅ Supports **heterogeneous (mixed) enums** (not recommended).
- ✅ Numeric enums auto-increment if subsequent values are not specified.
- ✅ First numeric enum member defaults to `0` if no value is assigned.
- ✅ Enum members can have explicitly assigned values.
- ✅ Enum values can be used in variables, conditions, switches, and function parameters.
- ✅ Provides better type safety than using plain constants.
- ✅ Can be exported and reused across files/modules.
- ✅ Compiles to JavaScript objects (except `const enum`).

#### Numeric Enum Features
- ✅ Supports auto-incrementing values.
- ✅ Supports reverse mapping (value → name).

#### String Enum Features
- ✅ Requires explicit values for each member.
- ✅ Does not support auto-increment.
- ✅ Does not support reverse mapping.
- ✅ More readable in debugging and API responses.

#### Const Enum Features
- ✅ Compiled away during transpilation.
- ✅ No JavaScript object is generated.
- ✅ Better runtime performance.
- ✅ Reduces generated code size.
- ⚠️ Cannot be accessed dynamically at runtime.

#### Best Practices
- ✅ Prefer string enums when values need to be human-readable.
- ✅ Prefer `const enum` for performance-sensitive code.
- ⚠️ Avoid heterogeneous (mixed) enums.
- ⚠️ Use enums only when a fixed set of related constants is required.

---
## Small Example
```TypeScript
enum Size {
    Small = 1,
    Medium,
    Large
}

let mySize: Size = Size.Medium;

console.log(mySize); // 2
```

Auto-incremented values:

```Typescript
Small  = 1
Medium = 2
Large  = 3
```

---
