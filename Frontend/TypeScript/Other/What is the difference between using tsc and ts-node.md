This is a very important concept to understand as a TypeScript developer.

## JavaScript vs TypeScript Runtime
Your computer (Node.js) understands only **JavaScript**, not TypeScript.

For example:
```ts
let a: number = 10;
```

The `: number` syntax is TypeScript-specific. Node.js cannot execute it directly.

---

## What `tsc` Does
`tsc` = TypeScript Compiler

It converts:
```ts
let a: number = 10;
console.log(a);
```

into:
```js
let a = 10;
console.log(a);
```

So when you run:
```bash
tsc
```

you get:
```text
src/index.ts
      ↓
dist/index.js
```

Then Node can execute the generated JavaScript:
```bash
node dist/index.js
```

Flow:
```text
TypeScript
    ↓ tsc
JavaScript
    ↓ node
Output
```

---

## What `ts-node` Does
`ts-node` is a helper tool.

Instead of:
```bash
tsc
node dist/index.js
```

it does both steps automatically:
```bash
ts-node src/index.ts
```

Internally:
```text
index.ts
   ↓
ts-node compiles in memory
   ↓
node executes generated JS
   ↓
Output
```

No `.js` file is created.

---

## Visual Comparison

### Using tsc

```bash
tsc
node dist/index.js
```

Result:
```text
index.ts
   ↓
index.js   ← file created
   ↓
executed
```

---

### Using ts-node

```bash
ts-node src/index.ts
```

Result:
```text
index.ts
   ↓
compiled in memory
   ↓
executed
```

No JS file appears on disk.

---
## Why Did `node src/index.js` Work?
Because after running:
```bash
tsc
```

a JavaScript file existed:
```text
src/
 ├─ index.ts
 └─ index.js
```

or

```text
dist/
 └─ index.js
```
Node executed the **JavaScript file**, not the TypeScript file.

This works:
```bash
node src/index.js
```

This does **not** work:
```bash
node src/index.ts
```
because Node cannot understand TypeScript syntax.

---
## Which One Is Used in Real Projects?

### During Development
Most developers use:
```bash
ts-node
```

or
```bash
tsx
```
because it's faster.

Example:
```bash
npx ts-node src/index.ts
```

or
```bash
npx tsx src/index.ts
```

---

### For Production
Nobody runs TypeScript directly on servers.

The common process is:
```bash
tsc
```

which generates:
```text
dist/
  app.js
```

and then:
```bash
node dist/app.js
```

This is what you'll see in most backend applications.

---
## Interview Answer
**Q: What is the difference between `tsc` and `ts-node`?**
**Answer:**
- `tsc` is the TypeScript compiler. It converts `.ts` files into `.js` files but does not execute them.
- `ts-node` compiles TypeScript and immediately executes it using Node.js without creating a JavaScript file on disk.
- In development, `ts-node` is convenient because it combines compilation and execution.
- In production, projects are usually compiled using `tsc` and the generated JavaScript is executed by Node.js.

### Confidence Score (Interview Importance)

|Topic|Importance|
|---|---|
|What is `tsc`|9/10|
|What is `ts-node`|8/10|
|Why Node can't run TypeScript directly|9/10|
|Development vs Production usage|8/10|

---