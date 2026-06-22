TypeScript is build on top of JS. So, it has everything JS with additional features. 

TypeScript **Advantages** over JS:
- Static Typing
- Code Completion
- Refactoring
- Shorthand Notations

**What is Static and Dynamic Typing?**
**Static Typing:** Static typing checks variable types during compilation before the code runs.
Example: Java, C++, C#. `int a=10;`. We know a in int before the code runs.

**Dynamic Typing:** dynamic typing checks them on the fly during execution.
Example: JavaScript, Python, Ruby. `let a=10`. We know the type during execution.

**Drawbacks** of TypeScript:
- Compilation
- Discipline in Coding
---
### Configuration:
Installation:
```Bash
npm i -g typescript //-g -> means Globally, We are saying to install globally

tsc -v  //Checking version of typescript

tsc //When we run this the tsc code will be converted to js file in dist/index.js file and we need to run index.js file in dist.

node dist/index.js // this will run the js file.
```

Basic Configuration:
```Bash
tsc --init //Creates tsconfig.json file
//Enable rootDir, outDir, sourceMap in tsconfig.json File

Run tsc -> will run tsc files.

A file will be created index.js.map -> this file maps our ts code to js.
```

In `tsconfig.json` file:
- target -> means 'version' of TS.
- `rootDir` -> contains our source files.
- `outDir` -> Contains our JS files.
- `removeComments` -> remove all the comments in Ts while converting code to JS. -> Not there is updated TS versions.
- `noEmitOnError:true` -> If there is Error. TS will throw error before generating JS files. If false then TS will generate JS Files. -> Not there is updated TS versions.
- `sourceMap:true` -> A File that specifies how each line of our Ts code maps to the generated JS code.
- `noUnusedLocal:true` -> will throw error if any variable is created but not used.
- `noUnusedParameters:true` -> will throw error if any parameter is created but not used.
- `noImplicitReturns:true` -> will throw error if no return is present in the function.
---
### Debug:
- Go to Debug and click on  create a `launch.json file` in run. This will create `launch.json file`.
- This file tells Vs code how to debug an application.
- write `"preLaunchTask": "tsc: build - tsconfig.json",` after program in `launch.json file`.
- This file tells Vs code to build our application using this configuration.

---
### How to run TS file Directly?
We need to install `ts-node`.

```Bash
npm install -g ts-node typescript

ts-node -v

ts-node src/index.ts

To find where it got installed we can check by below command in bash:
where ts-node
```

---
### What is the difference between using `tsc` and `ts-node`?
Your computer (Node.js) understands only **JavaScript**, not TypeScript.
	
What `tsc` Does:
`tsc` = TypeScript Compiler
[[What is the difference between using tsc and ts-node]]

---
## How does ts-node work?
Under the hood, `ts-node` uses the TypeScript compiler API.

When you run:
```
ts-node src/index.ts
```

it roughly does:
```
1. Read index.ts2. Use TypeScript compiler to transpile it3. Generate JavaScript in memory4. Pass the JavaScript to Node.js5. Execute it
```

No `.js` file is written to disk.

---
### Types:

| JavaScript | TypeScript |
| ---------- | ---------- |
| number     | any        |
| string     | unknown    |
| boolean    | never      |
| null       | enum       |
| undefined  | tuple      |
| object     |            |

---
Tuples & enum:
[[Tuple]]
[[enum]]

---
