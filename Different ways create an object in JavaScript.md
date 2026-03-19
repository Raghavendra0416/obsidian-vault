There are **6 main ways** (you can mention 5–7 depending on depth):

#### 1. Object Literal (Most Common)
```js
const person = {
  name: "Raghav",
  age: 25
};
```
##### Key Points:
- Simplest and most used
- Created directly
- Best for static objects


#### 2. Using `new Object()`
```js
const person = new Object();
person.name = "Raghav";
person.age = 25;
```

##### Key Points:
- Built-in constructor
- Same as object literal internally
- Rarely used in modern JS
    

Interview Tip:  
Say **"Object literal is preferred over this"**

#### 3. Constructor Function
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const p1 = new Person("Raghav", 25);
```

##### Key Points:
- Used before ES6 classes
- `this` refers to new object
- Requires `new` keyword

Important Concept:
- Creates objects via **prototype**


#### 4. ES6 Class (Modern Way ⭐)
```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const p1 = new Person("Raghav", 25);
```
##### Key Points:
- Syntactic sugar over constructor functions
- Cleaner and readable
- Preferred in modern applications
    

#### 5. `Object.create()` (Prototype-based 🔥)
```js
const personProto = {
  greet() {
    console.log("Hello");
  }
};

const p1 = Object.create(personProto);
p1.name = "Raghav";
```

##### Key Points:
- Directly sets prototype
- No constructor function needed
- Used in advanced JS concepts
    

Interview Gold Line:

> "Object.create allows us to manually control prototype chain"


#### 6. Factory Function
```js
function createPerson(name, age) {
  return {
    name,
    age
  };
}

const p1 = createPerson("Raghav", 25);
```
##### Key Points:

- Returns object without `new`
- Avoids `this` issues
- Common in functional programming
    

#### 7. Using `Object.assign()`
```js
const person = Object.assign({}, { name: "Raghav" });
```

##### Key Points:
- Used for cloning + merging
- Not primary creation method, but still valid


### Important Interview Concepts

##### 1. Everything is Object-based

- Objects are collections of key-value pairs
- Functions are also objects

##### 2. Prototype Chain (VERY IMPORTANT 🔥)
Every object has:
```js
__proto__  // or [[Prototype]]
```

Example:
```js
console.log(p1.__proto__);
```

Used for:
- Inheritance
- Method sharing

#### 3. `new` Keyword Internals (Interview Favorite)

When you do:
```js
new Person()
```

It does 4 things:
1. Creates empty object `{}`
2. Sets prototype
3. Binds `this`
4. Returns object

#### 4. Difference: Constructor vs Class

|Feature|Constructor Function|Class|
|---|---|---|
|Syntax|Old|Modern|
|Hoisting|Yes|No|
|Readability|Medium|High|

#### 5. Factory vs Constructor

|Feature|Factory|Constructor|
|---|---|---|
|Uses `new`|❌|✅|
|Uses `this`|❌|✅|
|Simpler|✅|❌|
