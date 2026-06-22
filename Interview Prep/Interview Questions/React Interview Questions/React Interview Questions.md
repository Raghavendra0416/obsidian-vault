https://www.youtube.com/watch?v=NkWOzTEEcco
---
**What is React and why is it popular?** 
- React is library used for building powerful user interfaces.
- It's key strength lies in the ability to create component based architecture which allows developers to use reusable components.
- Additionally, React virtual DOM is able to create a copy of the original DOM, that minimized direct DOM manipulations, which significantly improves performance. 

**What is Single Page Application (SPA)?**
- It is a type of application that loads a single HTML page.
- and also instead of reloading the whole page, the only effected parts of the page will be reloaded according to the user's actions.
- Like rendering the color change from white to black of a certain component or place in HTML. 
- This helps in:
	- Faster load time.
	- Better responsiveness
	- Smoother user interactions.
- But SPA becomes challenge when it comes to SEO(Search Engine Optimization), because the application uses a single URL so it becomes hard search engines to crawl and index content effectively.

**What is JSX and how does it differ from HTML?**
- A Syntax Extension for JS that allows developers to write HTML-Like Code directly into JS Files.
- Another difference is compulsion to properly close all self-closing tags in react. like an image tag.

**Difference b/w Functional & Class based Components?**
- Class Components are used before hooks, you can think as large and complicated machines.
- Functional Components comes into use after hooks, making them modern easier choice in react.
The Main Difference is:
- Class Components use `React.Componet` and includes `render` method which return JSX. and the state changes inside the component is managed by using `this.state` and updated with `this.setState` .
- In Functional Components we use hooks to handle state and lifecycle limits.
- Before Hooks functional components used to be stateless but after hooks they are ale to manage states.

**Difference b/w Stateless and Stateful Component in React?**
- Stateless components does not manage or store the data, they simply receive the data via prompts and display them. These are best used when we don't want to handle any logic and just want to display content on the user interface.
- Stateful components can manage their own state and update their existing state based on user interaction or other events. They can handle complicated logics and provide the required output as well. 
- By using react hooks we can make functional components either stateful or stateless.

**What are props in React and how are they used?**
- props are used pass the data from parent component to child component in react.
- the child component cannot modify these values because, they are read only. Instead these actions are used to trigger certain actions in child components.

**Difference State and Props in React?**
- State is mutable object that stores dynamic data. means it stores data that changes over time due to other factors, such as user interaction and network requests or other elements.
- Props are immutable object that cannot be modified. 
- State is private and it completely belongs to the component, it belongs to
- Props can be only controlled by the parent element and cannot be changed by child component.

**Controlled & Uncontrolled Components?**->Understand again, the below answer might confuse.
The distinction between controlled and uncontrolled components is **not about where validation happens** (frontend vs backend). It's about **where the form data state is stored and managed**.
- Controlled components are used when control is required when data is being entered into a form. Such as form validation -> we need to fetch the username and password to validate the authenticity.
- Uncontrolled components are used when there is no need to dynamically control inspect the users input. Such as user subscribing to your newsletter or a user uploading a file. In these cases react does not need to react to the input because the data is being sent to server for evaluation.
- Controlled components are accessed through state attribute which makes it easier to change.
- However Uncontrolled components are managed through `ref` it is hard to access the values.

**What is the purpose of Key attribute in react lists?**
- Key Attribute Identifies each item uniquely when the lists re-renders, enabling react to track and update individual items in the list without having to re-render the Entire list items.
- Suppose the is a list and we need to update a single element in the list. without keys the whole list will be re-rendered, react use key attribute to differentiate the keys and re-renders the the key that is updated instead of all the list items which remains the same. 

**What are fragments in react and why are they used?**
- Fragments in react is a way to group the elements together without adding extra nodes to DOM.
- Example for Fragment:
```JS
export default function fun(){
	return <> --------------------------------
		<h1>Hello<h1/>                       | -> `<></>` these are fragments used to grp 
		<p>Welcome to my page<p/>            |      elements instead of using div tag.
	<>----------------------------------------
}
```

- Fragments are used when we want to avoid unnecessary wrapper elements like div tag. 
---
**What is Virtual DOM and how does React use it to improve performance?**
- The Virtual DOM is a lightweight, in-memory representation of actual DOM.
- The Virtual DOM is copy of actual DOM.
But why do we need Virtual DOM?
Ans: 
If there is a situation where we need to update a simple data like increment in the value in the page and without Virtual Dom the whole page re-renders, and it will take significant amount of time to just load a single value. So, here Virtual DOM comes to picture to help.
Virtual DOM checks the original code and check for the changes in the code and reflect them in the original DOM of the specific place where code changes happened and the rest of the components/DOM stays same.

**What are React Lifecycle Methods and When are they used? **-> Notion
- React Lifecycle methods are special functions that provide granular level control to developers to hook into specific points in a component lifecycle.
Why we need lifecycle methods?
we need need lifecycle methods is so that we can attach certain events to a components. like the component is first initialized  or when the components ends. like removing `settimeouts`.
Three main phases in lifecycle methods:
1. Mounting phase
2. Updating phase
3. Unmounting phase
and these phases are further divided.

---
**What is `useState` & `useEffect` ?**
**What is Prop Drilling?**
**What is Context API and how is it used in state management? **
What are Higher Order Component and examples?

---
**Explain the concept of reconciliation in React?**
- A process in React, like what happens in the background when a particular component is updated and how the virtual DOM and real DOM are working together to display the content in the user interface.
There are Different Phases:
- Initial Render
- State or Prop Change
- Diffing
- Update the DOM
- Commit Phase

**Initial Render** -> When  a component is first rendered, React creates a Virtual DOM. Compare the actual DOM and virtual DOM, if there are changes then only change that part of the DOM. Remaining part of the DOM stays same.
**State or Prop Change** -> When state or Prop Change, React creates a new virtual DOM.
**Diffing** -> React compares the old Virtual DOM with new one.
**Update the DOM** -> React only updates the parts of the actual DOM that needs to be changed. Only the change made will be updated and reflected in the original DOM. Remaining DOM stays same.
**Commit Phase** -> Finally, React commits the changes to the actual DOM.

---
**How React Portals work and when they should be used?**
- In React, A Portal is way to render a component's Children into a different part of a DOM outside the parent component hierarchy, While maintaining the react component structure.
- These helps in opening the model(popup/alert/ads in webpage). How? 
	Check video from above at time: 42:44.

**How does React Router handle navigation in a Single Page App?**
**What is React Strict mode and how does it help developers?**

---
**What is React Fiber? How does it differ from old Reconciliation?**
**Reconciliation** is React's process of comparing the old and new Virtual DOM trees and updating only the changed parts of the real DOM. But the disadvantage is The entire reconciliation process(re-rendering of the component) had to finish before React could do anything else. Large component trees could block the browser and make the UI feel laggy.
So, React Fiber is introduced.

**React Fiber** is React's internal rendering architecture introduced in React 16. It implements reconciliation in a more efficient way by breaking rendering work into small units, allowing React to pause, resume, prioritize, and schedule updates for better performance and responsiveness.

The Key Benefits of React Fiber is:
- Priority based updates
- Concurrent rerendering
- Supports suspense & lazy loading
- Pause/Resume/Cancel the work.

