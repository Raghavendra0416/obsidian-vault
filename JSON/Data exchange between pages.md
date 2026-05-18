
Data Exchange Methods Between Pages:
1. **localStorage** - Data persists even after closing browser
2. **sessionStorage** - Data persists only during the browser session (tab open)
3. **URL Parameters** - Data passed through the URL
4. **Cookies** - Data stored with expiration dates, accessible by server too

Why These Methods?
When you navigate from one HTML page to another, the browser **loads a completely new page** and all JavaScript variables from the previous page are **lost/destroyed**.

So you need a way to "store" the data somewhere that survives the page reload. These four methods provide that storage.

Quick Comparison:

|Method|Survives Browser Close?|Size Limit|Best For|
|---|---|---|---|
|localStorage|✅ Yes|~5-10MB|Long-term data|
|sessionStorage|❌ No (tab close)|~5-10MB|Temporary data|
|URL Parameters|❌ No|Small (~2000 chars)|Simple values|
|Cookies|✅ Yes (with expiry)|~4KB|Server communication|

---

#### 1. Local Storage

**Storing Data:**
```javascript
// Store simple string
localStorage.setItem('username', 'John');

// Store number
localStorage.setItem('age', '25');

// Store array/object (must convert to JSON first)
const tasks = ['Buy milk', 'Study JS', 'Exercise'];
localStorage.setItem('tasks', JSON.stringify(tasks));
```

**Retrieving Data:**
```javascript
// Get simple string
const username = localStorage.getItem('username'); // "John"

// Get array/object (must parse from JSON)
const tasks = JSON.parse(localStorage.getItem('tasks'));
console.log(tasks[0]); // "Buy milk"
```

**Removing Data:**
```javascript
localStorage.removeItem('username'); // Remove one item
localStorage.clear(); // Remove everything
```

#### 2. Session Storage

**Exact same syntax as local Storage!**
```javascript
// Store
sessionStorage.setItem('tempData', 'value');

// Get
const data = sessionStorage.getItem('tempData');

// Remove
sessionStorage.removeItem('tempData');
sessionStorage.clear();
```

**Only difference:** Data disappears when you close the tab.


#### 3. URL Parameters
**Page 1 - Sending Data:**

```javascript
const taskValue = 'Buy groceries';
const priority = 'high';

// Method 1: Direct redirect
window.location.href = `page2.html?task=${taskValue}&priority=${priority}`;

// Method 2: On button click
button.addEventListener('click', function() {
  const input = document.getElementById('task-inp').value;
  window.location.href = `page2.html?task=${encodeURIComponent(input)}`;
});
```

**Page 2 - Receiving Data:**
```javascript
// Get all URL parameters
const urlParams = new URLSearchParams(window.location.search);

// Get specific parameter
const task = urlParams.get('task');        // "Buy groceries"
const priority = urlParams.get('priority'); // "high"

console.log(task, priority);
```

**Note:** Use `encodeURIComponent()` for special characters:

```javascript
const text = "Hello World!";
window.location.href = `page2.html?msg=${encodeURIComponent(text)}`;
```

#### 4. Cookies

**Setting a Cookie:**
```javascript
// Simple cookie
document.cookie = "username=John";

// Cookie with expiration date
const expiryDate = new Date();
expiryDate.setDate(expiryDate.getDate() + 7); // Expires in 7 days
document.cookie = `username=John; expires=${expiryDate.toUTCString()}`;

// Cookie with path
document.cookie = "username=John; path=/; expires=Fri, 31 Dec 2025 23:59:59 GMT";
```

**Getting a Cookie:**
```javascript
function getCookie(name) {
  const value = `; ${document.cookie}`;
  const parts = value.split(`; ${name}=`);
  if (parts.length === 2) {
    return parts.pop().split(';').shift();
  }
  return null;
}

const username = getCookie('username'); // "John"
```

**Deleting a Cookie:**
```javascript
// Set expiration to past date
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";
```

#### Complete Real Example: Todo App

**index.html + indexscript.js:**
```javascript
const taskInput = document.getElementById('task-inp');
const addButton = document.getElementById('addTask-button');

addButton.addEventListener('click', function() {
  const taskValue = taskInput.value;
  
  // Get existing tasks or create empty array
  let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
  
  // Add new task
  tasks.push(taskValue);
  
  // Save back to localStorage
  localStorage.setItem('tasks', JSON.stringify(tasks));
  
  // Redirect to page1
  window.location.href = 'page1.html';
});
```

**page1.html + page1script.js:**
```javascript
// Get tasks from localStorage
const tasks = JSON.parse(localStorage.getItem('tasks')) || [];

// Display tasks
tasks.forEach(task => {
  console.log(task);
  // Or add to DOM
  const li = document.createElement('li');
  li.textContent = task;
  document.body.appendChild(li);
});
```
----
#### Q. If we store in local, where will it store in local? and what is storing in browser mean? if store it browser, where does it store server/local?
Answer:

Where Does localStorage Actually Store Data?
**localStorage stores data on YOUR COMPUTER (local machine)**, not on any server!

Specifically, it's stored in:

- **Windows**: `C:\Users\[YourName]\AppData\Local\Google\Chrome\User Data\Default\Local Storage`
- **Mac**: `~/Library/Application Support/Google/Chrome/Default/Local Storage`
- **Linux**: `~/.config/google-chrome/Default/Local Storage`

What Does "Storing in Browser" Mean?
When we say **"storing in the browser"**, we mean:

- Data is saved in **files on your computer** that the browser manages
- Each browser (Chrome, Firefox, Edge) has its **own separate storage**
- The data stays on **your local machine**, not uploaded anywhere


Visual Explanation:

```
Your Computer (Local)
├── Chrome Browser
│   └── localStorage data (specific to Chrome)
├── Firefox Browser
│   └── localStorage data (specific to Firefox)
└── Edge Browser
    └── localStorage data (specific to Edge)

Server (Remote - somewhere on the internet)
└── Website files, databases, etc.
```

Local vs Server Storage
### Local Storage (Client-Side):

```
┌─────────────────────────────┐
│   YOUR COMPUTER (Client)    │
│                              │
│  ┌────────────────────┐     │
│  │   Browser          │     │
│  │  ┌──────────────┐  │     │
│  │  │ localStorage │  │     │
│  │  │   {data}     │  │     │
│  │  └──────────────┘  │     │
│  └────────────────────┘     │
└─────────────────────────────┘
        ↑
    Stored HERE
    (on your hard drive)
```

**Characteristics:**
- ✅ Fast access (no internet needed)
- ✅ Private to your computer
- ❌ Not accessible from other devices
- ❌ Lost if you clear browser data
- ❌ Can't share with other users

Server Storage (Server-Side):

```
┌─────────────────┐          ┌──────────────────┐
│ YOUR COMPUTER   │          │     SERVER       │
│                 │          │   (Internet)     │
│   Browser       │ ◄──────► │   ┌──────────┐   │
│                 │ Internet │   │ Database │   │
│                 │          │   │  {data}  │   │
└─────────────────┘          │   └──────────┘   │
                             └──────────────────┘
                                     ↑
                                 Stored HERE
                          (on company's server)
```

**Characteristics:**
- ✅ Accessible from any device
- ✅ Shared across all users
- ✅ Backed up and secure
- ❌ Requires internet connection
- ❌ Slower (network delay)


Practical Example:
Using localStorage (Local/Client):

```javascript
// This saves on YOUR computer only
localStorage.setItem('username', 'John');

// If you open the same website on your phone,
// this data WON'T be there! ❌
```

Using Server Storage (requires backend):
```javascript
// This would send data to a server
fetch('https://example.com/api/save', {
  method: 'POST',
  body: JSON.stringify({ username: 'John' })
});

// Now it's saved on the server
// Accessible from any device! ✅
```


How to See Your localStorage Data:
In Chrome/Edge:

1. Press **F12** (open Developer Tools)
2. Go to **Application** tab
3. Click **Local Storage** on the left
4. Select your website
5. You'll see all stored data!


**Try it:**

```javascript
// Run this in your browser console
localStorage.setItem('test', 'Hello World');

// Now check Application → Local Storage
// You'll see: test = "Hello World"
```
Key Differences Summary:

|Aspect|localStorage (Local)|Server Storage|
|---|---|---|
|**Location**|Your computer|Company's server|
|**Access**|Only your browser|Any device/browser|
|**Internet needed?**|No|Yes|
|**Shared with others?**|No|Yes|
|**Survives browser reinstall?**|No|Yes|
|**Speed**|Very fast|Slower|

Important Points:
1. **localStorage is NOT a server** - it's just files on your computer
2. **Each website gets its own localStorage** - Facebook can't see Google's data
3. **Each browser has separate storage** - Chrome data ≠ Firefox data
4. **Clearing browser data deletes localStorage** - "Clear browsing data" removes it
5. **localStorage is per domain** - `example.com` can't access `google.com`'s data

Real-World Analogy:
**localStorage** = Writing in a notebook on your desk
- Only you can see it
- Fast to access
- Lost if notebook is destroyed

**Server Storage** = Storing files in a bank vault
- Accessible from anywhere (with key)
- Safe and backed up
- Need to travel to bank (internet) to access

Data Exchange Methods Between Pages:
1. localStorage - Data persists even after closing browser
2. sessionStorage - Data persists only during the browser session (tab open)
3. URL Parameters - Data passed through the URL
4. Cookies - Data stored with expiration dates, accessible by server too.