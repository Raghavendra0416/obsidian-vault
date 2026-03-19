### Method Overriding:
**Method overriding** is when a child class redefines a method that already exists in its parent class, replacing the parent's behavior.

```js
class Animal {
  speak() {
    return "Some generic sound";
  }
}

class Dog extends Animal {
  speak() { // overrides Animal's speak()
    return "Woof!";
  }
}

const dog = new Dog();
console.log(dog.speak()); // "Woof!" — Dog's version runs, not Animal's
```

If you still want to call the parent's version alongside the child's, use `super`:

```js
class Dog extends Animal {
  speak() {
    const parentSound = super.speak(); // "Some generic sound"
    return `${parentSound} ...just kidding, Woof!`;
  }
}
```

**Key point:** JS uses the prototype chain — when you call a method, it looks at the child class first, so the overridden version wins.

---
### Constructor Overriding:
Same concept — the child class defines its own `constructor`, overriding the parent's.

**The one strict rule:** In a child constructor, you **must** call `super()` before accessing `this`, otherwise you get a `ReferenceError`. This is unique to constructors — regular method overriding has no such rule.

If you don't define a constructor in the child class at all, JS automatically uses the parent's constructor behind the scenes.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // MUST call super() before using `this`
    this.breed = breed;
  }
}

const dog = new Dog("Rex", "Labrador");
console.log(dog.name);  // "Rex"
console.log(dog.breed); // "Labrador"
```
If `Dog` had no constructor at all, JS does this automatically. But the moment you **write your own constructor** in a child class, you take responsibility for calling `super()` yourself.

Why is `super()` mandatory?
Even though you're calling `Dog`, remember `Dog extends Animal` — meaning `Dog`'s `this` object is built on top of `Animal`. JS needs the parent constructor to run first to **set up the base object** before the child can add anything to it.

Think of it like a foundation:
```JS
Animal constructor → builds the base object (this.name)
Dog constructor   → extends it (this.breed)
```

If you skip `super()`, `this` doesn't exist yet inside `Dog`'s constructor, so JS throws:
```JS
ReferenceError: Must call super constructor before accessing 'this'
```
