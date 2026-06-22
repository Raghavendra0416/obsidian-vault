### Objects:
Normal creation of Object

```TypeScript
//Obj
let Employee: {
    readonly id: number, //connot be changed if initlized once. Readonly
    name: string,
    present?: boolean,  // ? -> mean optional
    retire: (date: Date) => void,
} = {
    id: 1,
    name: 'Raghav',
    retire: (date: Date) => {
        log(date);
    }
}
```

- It has more boiler plate
- Once an object is created, it is difficult to manage that object.
- If we need to create a new object we need to use the same process again. this is uncessary.

- We must follow DRY principal -> Don't Repat Yourself
- We need to use Type Alias.
```TypeScript
//Obj
type Employee= {
    readonly id: number, //connot be changed if initlized once. Readonly
    name: string,
    present?: boolean,  // ? -> mean optional
    retire: (date: Date) => void,
} 
let employee: Employee = {
    id: 1,
    name: 'Raghav',
    retire: (date: Date) => {
        log(date);
    }
}
```

---
### Union Types:
[[Union, Intersection, Literal, Nullable Types]]

---


