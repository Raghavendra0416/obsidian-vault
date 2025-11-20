- Generics **define the type of data** you want to use in a class, method, or interface.
- Definition: 
		Generics in Java let you write classes and methods that can work with any type of object, so you don’t have to write the same code again for different types. For example, you can make a single list that holds either numbers, words, or any other objects, and the compiler will help catch mistakes if you use the wrong type.
		or
		**Generics** are a **compile-time feature** in Java that allow you to **define classes, interfaces, and methods with placeholders for data types**. You replace those placeholders with **actual types** (like `String`, `Integer`, etc.) when you use them or needed
		or
		**Generics** allow you to write code that works with any data type while maintaining **type safety**. 
- Types of generics:
	 1. Generic Class
	 2. Generic Method
	 3. Generic Interface
	 4. Bounded Types
	 5. Wildcards
- The generics are written inside "<>" -> inside <> we can pass parameters like T,K,V.....
- When Generics are used in methods it is mandatory to use generics before and after the type. Example: public <K,V>map<K,V> Method Name(map<K,V> map){ code... }. here  K,V are generics and are used before map to ensure there won't be any error. (If you know the type you don't have to use generics before the type).
- **Use generics** when you want to write reusable methods where the type is decided by the caller. Don't use generics if you need to add specific values inside the method — use concrete types instead. Generics are best for utility methods like returning an empty map of any type.
The below(table) are not keywords — just **standard conventions** used for readability and consistency.

| Symbol    | Meaning (Convention)                      | Usage Example                 |
| --------- | ----------------------------------------- | ----------------------------- |
| `T`       | Type                                      | `Box<T>`, `List<T>`           |
| `E`       | Element (used mostly in collections)      | `List<E>`, `Set<E>`           |
| `K`       | Key (used in Maps)                        | `Map<K, V>`                   |
| `V`       | Value (used in Maps)                      | `Map<K, V>`                   |
| `N`       | Number (for numeric types)                | `NumberBox<N extends Number>` |
| `S, U, R` | Secondary, utility types (advanced cases) | `Tuple<T, S>`                 |

---

####  In Interview — You Should Know:

-  What are generics in Java?
- What are the benefits of using generics?
- How do you define a generic class or method?
- What are bounded type parameters?
- What is the difference between `extends` and `super` in generics?
- What are wildcards in generics? What are bounded and unbounded wildcards?
- What is type erasure?
- Can you use primitive types with generics?
- What are raw types and what problems can they cause?
- How do you implement a generic interface?
- Can you create an instance of a generic type?
- How do you create a generic array?
- Can methods be overloaded with different generic type parameters?
- Can a generic class or method be static?
- What are the restrictions on generic types in Java?
- Why generics are used?
-  Difference between generic class vs method.
-  Meaning of `<? extends T>` vs `<? super T>`.
-  What is type erasure?
-  Why `List<int>` is not allowed (use `List<Integer>` instead)?
