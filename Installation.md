### React + Vite:
How to Install react:
```JavaScript
//To create react app in current folder (Options will be asked while installing).
npm create vite@latest . 

// To create react app in current folder (Options will not be asked, directly react will be installed).
npm create vite@latest . -- --template react
```

---
### Tailwind
How to install Tailwind:
1. **Install the Packages:**
```JavaScript
npm install tailwindcss @tailwindcss/vite
```

2. **Configure Vite:**
```Javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react'; // Assuming you are using React
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
});
```

Open your `vite.config.js` (or `.ts`) file. You need to import the Tailwind plugin and add it to the plugins array.

3. **Import Tailwind into Your CSS:**
```Javascript
@import "tailwindcss";
```

Open your main, global CSS file (this is usually `index.css`, `main.css`, or `App.css`). Delete the default boilerplate code inside it and add this single line at the very top.

---
### BootStrap:
How to install BootStrap:
```Javascript
Step1:
//Install BootStrap
npm install react-bootstrap bootstrap

Step2:
//Add this in main.jsx. This needs to imported only once. 
//The CSS is injected into the root HTML file, it becomes globally available to the entire browser window.
import 'bootstrap/dist/css/bootstrap.min.css';
```

Link to install: https://github.com/reduxjs/redux-devtools/tree/main/extension
- `bootstrap` - It contains all the raw CSS rules that make things look good—the colors, the flexbox grid, the margins, and the fonts. Without this package, your components would have no styling.
- `react-bootstrap` -
	- Standard Bootstrap relies on standard JavaScript (and traditionally jQuery) to make things interactive, like opening modals or dropdowns. This directly manipulates the browser's DOM, which React absolutely hates (React wants exclusive control over the DOM via its Virtual DOM).
	- The `react-bootstrap` package solves this by completely rebuilding Bootstrap's interactive elements as pure React components. It essentially takes the CSS from the `bootstrap` package and applies it the "React way."

---
### Material UI:
Material UI (MUI) is a popular React component library based on Google's Material Design.
```bash
npm install @mui/material @emotion/react @emotion/styled
```

This installs three things:
- **`@mui/material`** — the main MUI component library
- **`@emotion/react`** & **`@emotion/styled`** — MUI's default styling engine (required)

Install MUI Icons
```bash
npm install @mui/icons-material
```
This gives you access to 2,000+ Material Design icons as React components

Install MUI X
```bash
npm install @mui/x-data-grid
```
MUI X includes advanced components like **DataGrid**, **Date Pickers**, **Charts**, etc. Install only what you need.

Add the Roboto Font
MUI is designed with the **Roboto** font in mind. Add it to your `public/index.html`:
```HTML
<link
  rel="stylesheet"
  href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap"
/>
```

---
### Redux:
How to install Redux:
```JavaScript
npm install redux react-redux
```

- **`redux`**: This is the core library. It provides the base functionality to create a store (using `createStore`), combine reducers, and apply middleware like `Redux Thunk`.
- **`react-redux`**: Just like with the Toolkit, you still need this package. It provides the `<Provider>` component to wrap your app and the `useSelector` and `useDispatch` hooks so your React components can talk to the Redux store.


How to install Redux Tool Kit:
```Javascript
npm install @reduxjs/toolkit react-redux
```

- `@reduxjs/toolkit` - This is the official, recommended core library. It contains all the tools necessary to set up your store, create reducers, and manage state efficiently without the boilerplate code of legacy Redux.
- `react-redux` - This is the official binding library. It acts as the bridge, allowing your React components to interact with the Redux store (so components can read state and dispatch actions).

---
### Libraries like BootStrap ( prebuilt UI components ):
1. React BootStrap --> 
2. Material UI  -->
3. Ant Design --> Used in dashboards/admin panels. Rich tables, forms, charts integrations
4. Chakra UI  -->
5. Mantine  --> Good forms, modals, notifications
6. Shadcn/ui  --> Great for portfolio/interview projects
7. Flowbite React --> Tailwind + ready-made components
8. Semantic UI React -->  


For Real Company Feel + Resume Projects:
1. Material UI
2. Ant Design
3. shadcn/ui

For Easy Learning:
1. React Bootstrap
2. Chakra UI

For Modern Portfolio:
1. Tailwind CSS + shadcn/ui
2. Flowbite React


##### Tailwind CSS + shadcn/ui
Best overall for modern Redux Toolkit apps

Why:
- Easy to connect Redux state to components
- Build reusable UI fast
- Full styling control
- Great for dashboards, task apps, admin apps
- Looks modern in interviews

Perfect for:
- Task Management App
- CRM
- E-commerce Admin
- Kanban Board
- SaaS Dashboard


##### Material UI
Best practical company choice

Why:
- Excellent components for Redux state flows
- Dialogs, forms, data tables, snackbars
- Easy loading states with Redux async thunks
- Used in many companies

Perfect for:
- Enterprise dashboards
- Internal tools
- Business products


##### Ant Design
Best for data-heavy Redux apps

Why:
- Powerful forms/tables
- Pagination/filter/sort built-in
- Good for API + Redux projects

Perfect for:
- Admin systems
- HRMS
- Reporting tools

#### Bootstrap now signals:
- Quick prototype
- Legacy project
- Beginner/intermediate learning

----
