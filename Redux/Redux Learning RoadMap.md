#### STEP 0: Prerequisites (VERY IMPORTANT)
Before Redux, you must be comfortable with:

JavaScript:
- Functions
- Arrow functions
- Objects & arrays
- Spread operator (`...`)
- Array methods (`map`, `filter`, `reduce`)

React:
- `useState`
- `useEffect`
- `useContex`
- `useReducer`
- Props
- Component structure

---

#### STEP 1: Understand the PROBLEM Redux solves
Before learning Redux, understand:

Why do we even need it?

Learn:
- Props drilling problem
- Sharing state between components

Practice:
- Pass data from Parent → Child → Grandchild
- Feel the pain

---
#### STEP 2: Learn Core Redux Concepts (THE HEART)
Focus only on understanding (no need to master code yet)

 Learn these 4 things:
1. **Store**
2. **Action**
3. **Reducer**
4. **Dispatch**

Flow (VERY IMPORTANT)

```text
Component → dispatch(action) → reducer → store updates → UI updates
```

If you understand this, you understand Redux 

---
#### STEP 3: Try Pure Redux (Basic Setup)
Just once, try **without React**

Why?
- Helps you understand internal working

Practice:
- Create a counter using Redux
- Increment / decrement

---
#### STEP 4: React + Redux (Old Way - Just for understanding)

Learn:
- `Provider`
- `useSelector`
- `useDispatch`

Connect Redux with React

---
#### STEP 5: Learn Redux Toolkit (MAIN PART )
Now switch to modern Redux (important for interviews)


Learn these concepts:
1. `configureStore`
	- Creates store easily


2. `createSlice` (MOST IMPORTANT)
	- Combines:
	    - state
	    - reducers
	    - actions

3. `useSelector`
	- Read data from store

4. `useDispatch`
	- Update data

This is what you’ll use in real projects

---
#### STEP 6: Async Logic (INTERVIEW FAVORITE)

Learn:
 `createAsyncThunk`

Used for:
- API calls
- Loading / success / error states

Example use cases:
- Fetch users
- Login API
- Load products

---
#### STEP 7: Project Practice (VERY IMPORTANT)
Build small projects:

Project Ideas:
1. Counter App (basic)
2. Todo App
3. Cart System (important)
4. User Login + API fetch

This is where you actually learn Redux

---
#### STEP 8: Advanced Concepts (After Basics)

Once comfortable:
- Redux DevTools
- Middleware (basic idea)
- State normalization
- Folder structure
---
#### Recommended Learning Order (SHORT VERSION)

Follow this strictly:

```text
1. Why Redux?
2. Store, Action, Reducer, Dispatch
3. Pure Redux (counter app)
4. React + Redux basics
5. Redux Toolkit (createSlice ⭐)
6. Async (createAsyncThunk)
7. Build projects
```

Common Mistake ❌
Don’t:
- Jump directly to advanced topics
- Memorize code without understanding flow

