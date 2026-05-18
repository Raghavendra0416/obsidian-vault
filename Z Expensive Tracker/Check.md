### Use only these files first:
```JSX
App.jsx
main.jsx
pages/
redux/store.js
redux/slices/transactionSlice.js
components/layout/
components/dashboard/
utils/
```
Ignore hooks/services/constants initially if overwhelmed.
Build gradually.

----
### API:
API = a place your frontend gets/saves data.
Your React app asks:
```text
Give me transactions  
Add new expense  
Update record
Delete record
```
That request goes to an API.

Two Main Types:

##### Local API:
Runs on **your own computer**.

Example:
```Link
http://localhost:3000/transactions
```

`localhost` means your machine only.

Usually created with:
- JSON Server
- Node.js + Express


###### How it works
You start server:
```npm
npm run server
```

Then React app uses it.

###### Pros of Local API
- Fully free  
- Fast  
- Unlimited APIs  
- Great for learning  
- Easy to edit data

###### Cons
- Only works on your laptop  
- If laptop/server off → API gone  
- Others cannot access it

##### Online Hoisted API:
Runs on internet server.

Example:
```Link
https://myapi.com/transactions
```
Can be used anywhere.

Platforms:
- Supabase
- Firebase
- MockAPI
- Your own Node server deployed online

###### Pros of Hosted API
- Works anywhere  
- Share project with recruiters/friends  
- Good for portfolio  
- Real-world experience  
- Data available online

###### Cons
- Free plans may have limits  
- Slightly harder setup  
- Need internet

----
### API in the Project:
##### API Needs to be Used:
- [Mock API](https://mockapi.io/projects)

##### What API Should You Create?
Create resource:
```Text
transactions
```

Then API endpoint becomes:
```JSON
https://your-project.mockapi.io/transactions
```

##### What Data Should It Contain?
Each transaction:
```JSON
{  
  "id": "1",  
  "title": "Salary",  
  "amount": 45000,  
  "type": "income",  
  "category": "Salary",  
  "date": "2026-04-19"  
}
```

Another:
```JSON
{  
  "id": "2",  
  "title": "Groceries",  
  "amount": 2500,  
  "type": "expense",  
  "category": "Food",  
  "date": "2026-04-18"  
}
```

##### Where Do You Use API In Your Project?
Use this folder:
```Text
src/services/

Create:
transactionService.js  
api.js
```


transactionService.js:
```js
import api from "./api";

export const getTransactions = () =>
  api.get("/transactions");

export const addTransaction = (data) =>
  api.post("/transactions", data);

export const deleteTransaction = (id) =>
  api.delete(`/transactions/${id}`);
```


##### Where Does API Data Go?
Flow (Very Important)
```Text
API -> Redux Slice -> Store -> Component UI
```

Example:
1. Dashboard page loads
2. Call API `getTransactions()`
3. Save response in Redux
4. Components read Redux data

##### Real Company Pattern:
```JSX
Page loads
↓
dispatch(fetchTransactions())
↓
API call
↓
Redux store updated
↓
UI rerenders automatically
```


##### Best Beginner Setup for You

Use These APIs
```JSX
GET all:
/transactions

POST add
/transactions

DELETE one
/transactions/1

PUT edit later
/transactions/1
```

----
#### Good Interview Impression:
Suggested Stack:
```Text
React
Redux Toolkit
Material UI
Recharts
React Router
React Hook Form
LocalStorage / Mock API
```

What interviewer sees in this stack:
```Text
Redux Toolkit  
Material UI  
Charts  
Dashboard  
State Management  
CRUD  
Filtering  
Reusable Components
```

---
