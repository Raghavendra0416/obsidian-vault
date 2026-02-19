
Definition:
Hooks are special functions in React that allow functional components to use features like state, lifecycle methods, and other React capabilities — without needing to write a class component.

Uses:
Hooks make code simpler, more readable and it also allows reusing logic across components. and hooks helps in avoiding issues like "this" keyword confusion.

History:
Before Hooks, if you wanted to manage state or use lifecycle methods, we need to use class components which became complex and hard to reuse. Hooks solved that problem.

Most commonly used Hooks are:
- **`useState`** — Used to manage state in a functional component. For example, tracking a counter value or form input.
- **`useEffect`** — Used to perform side effects like API calls, subscriptions, or DOM manipulation.
- **`useContext`** — Used to share data globally without prop drilling.

Other hooks that we might also use are:
- `useRef`
- `useCallback`
- `useReducer`
- Custom hooks

**Rules of Hooks:**
1. We need call hooks only at the **top level** — not inside loops, conditions, or nested functions.
2. Hooks can only be used in:
	- Functional components
	- Custom hooks