## Requirement: — Need to store the data/State globally so any component can access the data that is stored Globally and make the state changes based on requirement.

### How do we do that?
To store data users need to pass the data (through input or forms etc..).
The data passed by user, is picked up through component. 

Now we have data. We need to make it Global. But How?
We need to follow the below steps.

**FYI:-** we are going to work with 3 files. `store.js ,slice.js, component.jsx`. 
and It is mandatory to import and export modules. The importing and exporting the modules are also mandatory.
What are the mandatory files we need to create for using redux-toolkit and also what are mandatory to import? ==At the end of the page.==

##### Flow:
```Text
User Input → Dispatch Action → Slice updates State → Components read State
```

```Text
User fills form
   ↓
handleClick()
   ↓
dispatch(addItem(taskData))
   ↓
Redux creates action
   ↓
Reducer (taskSlice) runs
   ↓
state.tasks updated
   ↓
Store holds updated state
```

#### Step 1:
We got the Data from the users, But we need to pass the data to store it globally. 

##### So how do we pass the data?
We need to use `Dispatch` , to pass or dispatch the data.

To Dispatch the data we need the following:
We need to import:
```JSX
// useDispatch hook
import { useDispatch } from "react-redux";

// Actions from another file i.e slice.js
import { addItem } from "./taskSlice";
```

After importing we need to dispatch the data. How do we do that?
we need to:
```JSX
// provide useDispatch method to a variable
const dispatch = useDispatch();

// while dispatching the data provide the action, you want to perform. like addItem or delItem or  updateItem.
dispatch(addItem(taskData)); // We have dispatched the data using the variable.
```

Now the data is being passed.
How do we perform state change and action on the data we have passed?
i.e is Step-2.

#### Step-2:
##### How do we perform state change and action on the data we have passed?
To do that, we need to create a slice JS file. 

Why we need to create JS file? and What does this JS file do?
Ans:
We are creating another slice JS file because the actions and state can be handled by other components which imports this file.
The JS file will perform actions and changes the state based on requirement.

##### So how does the file perform actions and can change the state?
What needs to be imported to perform actions?

we need to import:
```JSX
import { createSlice } from "@reduxjs/toolkit";
```

We need to use the imported `createSlice`.

```JSX
const taskSlice = createSlice({
name:'user',
initialState:[], // Contains the initial state.
reducers:{
	addItem: (state,action) =>{ //addItem is an action. state resembles the initial state.
		//update the state and perform action here
		}
	}
});
```

How do we use `createSlice`?
To create slice we need to use `createSlice` and inside it we need to pass the following:

1. Name 
2. Initial State
3. Reducers
	1. Actions: like `addItem` , `delitem` 
	2. 2 parameters can be passed: state, action.
	   We make changes to the state here through actions.


Why do we need to use name in the above?
Ans: Name provides unique action types across our application like `user/addItem` or `user/delItem`.

Now we have changed the State or data, but we need to pass the state or data to store globally, for it we need to export the actions and reducer.

like below:
```JSX
// Export the action creators
export const { addItem } = taskSlice.actions;

// Export the reducer
export default taskSlice.reducer;
```

The Below is the example of whole taskSlice.js file. 

Example:
```JSX
import { createSlice } from "@reduxjs/toolkit";

const taskSlice = createSlice({
    name: "taskData",
    initialState: {
        tasks: [],
        nextId: 1,
		//Each object in tasks conatin
		//nextId: 1
        // taskTitle: '',
        // description: '',
        // status: '',
        // priority: '',
        // date: '',
    },

    reducers: {
        addItem: (state, action) => {
            const newTask = {
                id: state.nextId,
                ...action.payload
            };
            state.tasks.push(newTask);
            state.nextId += 1;
            console.log(newTask);  // Same data is being added if clicked addItem
        }
    }
});


// Export the action creators
export const { addItem } = taskSlice.actions;

// Export the reducer
export default taskSlice.reducer;
```


#### Step 3:
Until now:
- We have passed the data users have provided through dispatch.
- We have performed the actions and changed the state through `createSlice`.

Now:
- The State is updated and we need to store the state, so any component can globally access the state.

##### How do we store the State or data?
We need to use the exported data from the taskSlice.js.
Also we need to create another file i.e store.js

##### What is store.js and how do we create it?
To create store.js we need to import:
```JSX
import { configureStore } from "@reduxjs/toolkit";

//Reducer(this contains actions and state)
import taskReducer from "./taskSlice"; //taskSlice is exporting the reducer by default
```

Next, To store the data, we need to configure store.
like below:
```JSX
export const store = configureStore({
    reducer: {
        taskData: taskReducer //The reducer that we took from taskSlice.js
    }
});
```

Now we have stored the data in store (inside reducer).

###### Does Store.js is same for every project?
This file is most common while using redux toolkit.
The only change is multiple slices will be added.

```JSX
export const store = configureStore({  
	reducer: {  
	taskData: taskReducer,  // 1st slice
	userData: userReducer,  //2md Slice
	auth: authReducer  //3rd Slice
	}  
});
```

Now we stored the state/data, but the data is not global (other components cannot use) and also how does component fetch and use the data?
i.e Step 4.


### Step 4:
##### The Data/State is not Global, Why? how to make it Global?
The data/state is not global because:
 we are just storing the data, we are not passing it to the provider to make it available for every components.

So how do we make the data Global?
We need to use provider in `Main.jsx` and pass the stored information inside the provider and wrap all the components(inside provider) that need the stored data.

##### So How do we use Provider?
To use Provider we need to import the below:

```JSX
import { Provider } from "react-redux";

//the store.js file that we used to store the data (for explantaion check Step 3)
import { store } from "./Components/store.js";
```

We need to wrap the provider for the components that needs the data and also we need to pass the data inside the provider, so all components inside the provider can use the data that is passed. like below:

```JSX
// Here i am using the provider in Main.jsx.
createRoot(document.getElementById('root')).render(
  <StrictMode>
    <Provider store={store}> We are wrapping and passing the data to all the components that are wrapped.
      <App />
    </Provider>
  </StrictMode>,
)
```


#### Step 5:
Until Now:
- We have passed the data users have provided through dispatch.
- We have performed the actions and changed the state through `createSlice`.
- We have stored the data.
- To make the data Global we are passing the data by using provider.

Now:
But we need to use the data as well.

##### How do we fetch and use the data which is passed, from different different components?







----
### What are the mandatory files we need to create for using redux-toolkit and also what are mandatory to import?
Ans:
##### Mandatory Files need to be created?
The files themselves are **not mandatory** — but the **responsibilities** each file handles are mandatory. You can name and organize them however you want.

`Newtask.jsx` --> for fetching data from the user and dispatching action. 
`taskSlic.js` --> to perform actions and update the state. 
`store.js` --> used to store the data. 
`main.jsx` --> to provide the stored data to components, for the components to use. 
`some other components` --> that needs the data to display or perform calculations.


##### Mandatory to import:
**In `taskSlice.js`** — define your state and reducers:

```js
import { createSlice } from "@reduxjs/toolkit"  // ✅
```

**In `store.js`** — create the store:

```js
import { configureStore } from "@reduxjs/toolkit"  // ✅
```

**In `main.jsx`** — wrap your app so all components can access the store:

```js
import { Provider } from "react-redux"  // ✅
import { store } from "./Components/store"  // ✅
```

**In any component that wants to SEND data to the store:**

```js
import { useDispatch } from "react-redux"  // ✅
import { addItem } from "./taskSlice"       // ✅ the action creator
```

**In any component that wants to READ data from the store:**

```js
import { useSelector } from "react-redux"  // ← you missed this one
```

The two hooks have distinct roles:

|Hook|Purpose|
|---|---|
|`useDispatch`|**Send** actions to the store (write)|
|`useSelector`|**Read** data from the store (read)|

`Provider` + `store` is the setup that makes both hooks work in any component.

---

###### Can you merge files? Yes, for example:
```Text
// You COULD put taskSlice and store in the same file
// It works but gets messy as the app grows
```

###### Can you rename files? Yes:
```
taskSlice.js  →  tasks.js      ✅ works fine
store.js      →  redux.js      ✅ works fine
NewTask.jsx   →  AddTask.jsx   ✅ works fine
```

###### What IS truly mandatory is the order of operations:
```
1. createSlice          → defines state + reducers + actions
2. configureStore       → registers slices
3. <Provider store>     → makes store available to all components
4. useDispatch          → to write to store
5. useSelector          → to read from store
```

As long as these 5 things exist somewhere in your project, the structure and file names don't matter.

---
