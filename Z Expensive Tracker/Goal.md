
# ✅ Day 1 — Project Setup + Basic Layout

## Create / Complete:

```text
src/
App.jsx
main.jsx
components/layout/
  Navbar.jsx
  Sidebar.jsx
pages/
  Dashboard.jsx
```

## What to Build

### `main.jsx`
Connect React app + Redux store later.

### `App.jsx`
Basic layout:
- Navbar top
- Sidebar left
- Dashboard right

### `Navbar.jsx`
Simple top bar:
- Logo
- App name

### `Sidebar.jsx`
Menu:
- Dashboard
- Transactions
- Reports
- Settings

### `Dashboard.jsx`
Just text:

```text
Welcome Dashboard
```

## Goal End of Day 1:

✅ App looks like a real dashboard layout

---

# ✅ Day 2 — Routing + Pages

## Create:

```text
pages/
Transactions.jsx
AddTransaction.jsx
Reports.jsx
Settings.jsx
NotFound.jsx
```

## Add React Router

Routes:

```text
/dashboard
/transactions
/add
/reports
/settings
```

## Goal End of Day 2:

✅ Clicking sidebar changes pages

---

# ✅ Day 3 — Redux Toolkit Setup

## Create:

```text
redux/
store.js
redux/slices/
transactionSlice.js
```

## Learn:

- `createSlice()`
    
- `configureStore()`
    
- `useSelector`
    
- `useDispatch`
    

## Add State:

```js
transactions: []
```

## Goal End of Day 3:

✅ Redux connected successfully

---

# ✅ Day 4 — Add Transaction Form

## Build:

`AddTransaction.jsx`

Form fields:

- Title
    
- Amount
    
- Type (Income / Expense)
    
- Category
    
- Date
    
- Submit
    

On submit:

Dispatch action:

```js
dispatch(addTransaction(data))
```

## Goal End of Day 4:

✅ Can add transactions into Redux store

---

# ✅ Day 5 — Transactions Page

## Build:

`Transactions.jsx`

Show all transactions from Redux.

Table/List:

- Title
    
- Amount
    
- Category
    
- Date
    
- Delete Button
    

Add delete action in slice.

## Goal End of Day 5:

✅ Full CRUD basics working

---

# ✅ Day 6 — Dashboard Cards + Totals

## Build Components:

```text
components/dashboard/
SummaryCard.jsx
RecentTransactions.jsx
```

## Show:

- Total Income
    
- Total Expense
    
- Balance
    
- Latest 5 Transactions
    

Use selectors or utility functions.

## Goal End of Day 6:

✅ Real dashboard feeling starts

---

# ✅ Day 7 — Charts + Polish

## Build:

```text
ExpenseChart.jsx
IncomeChart.jsx
```

Use:

- Recharts or Chart.js
    

Show:

- Expense by Category
    
- Monthly trend
    

Also add:

- Loader
    
- Empty states
    
- Nice UI
    

## Goal End of Day 7:

✅ Portfolio-ready project v1

---

# 🔥 What To Ignore Initially

Do later:

```text
hooks/
services/
authSlice.js
themeSlice.js
Login.jsx
```

Not needed first version.

---

# 🎯 Your Daily Focus (Important)

Each day:

## 1 Hour Build

## 30 Min Learn why it works

## 30 Min Refactor

That’s how real devs grow fast.

---

# 🚀 What You’ll Learn By End

- React Components
    
- Props
    
- State
    
- Routing
    
- Redux Toolkit
    
- Forms
    
- CRUD
    
- Dashboard UI
    
- Charts
    
- Folder structure
    

---
