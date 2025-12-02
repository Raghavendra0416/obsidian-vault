- We **cannot** access date properties directly (like `date.year` or `date.day`—these will return `undefined`), so you must use **methods**.
- We need "Getters and Setters" if you are trying to read or change **specific parts** of the date.

**When you MUST use Getters/Setters:**
Because JavaScript `Date` objects don't let you access data directly (e.g., `myDate.month` does not work), you must use Getters/Setters to isolate specific components or calculate logic.

**When you DO NOT need Getters/Setters:**
If you are treating the date as a whole unit—for displaying, saving, or comparing—you often skip the getters/setters completely.
1. Displaying the whole date
2. Sending data to a backend (API/Database)
3. Comparing two dates (Math)

**Crucial Note on Months:** JavaScript counts months from **0 to 11**.
- 0 = January
- 11 = December

##### **Creating a Date:**
There are four primary ways to instantiate a new `Date` object.

| **Method**                   | **Description**                                                       | **Example**                             |
| ---------------------------- | --------------------------------------------------------------------- | --------------------------------------- |
| **`new Date()`**             | Creates a date object with the **current** date and time.             | `const now = new Date();`               |
| **`new Date(value)`**        | Creates a date from a **timestamp** (milliseconds since Jan 1, 1970). | `const date = new Date(1679822000000);` |
| **`new Date(dateString)`**   | Creates a date by parsing a **date string**.                          | `const date = new Date("2024-12-25");`  |
| **`new Date(y, m, d, ...)`** | Creates a date using specific components (year, month, day, etc.).    | `const date = new Date(2024, 11, 25);`  |

##### Getting Date Information (Getters):
We can extract specific information using "getter" methods.

```JavaScript
const now = new Date();

const year = now.getFullYear();    // e.g., 2024
const month = now.getMonth();      // 0-11 (Add +1 for human-readable month)
const date = now.getDate();        // 1-31 (Day of the month)
const day = now.getDay();          // 0-6 (0 is Sunday, 1 is Monday, etc.)
const hours = now.getHours();      // 0-23
const minutes = now.getMinutes();  // 0-59
const time = now.getTime();        // Milliseconds since Jan 1, 1970 (Timestamp)
```
##### Modifying Date Information (Setters):
We can change an existing date object using "setter" methods.
```JavaScript
const myDate = new Date();

myDate.setFullYear(2025);
myDate.setMonth(0); // Sets to January
myDate.setDate(15); // Sets to the 15th

console.log(myDate); // Outputs the updated date in 2025
```
##### Formatting Dates:
JavaScript offers a few built-in ways to convert dates to strings, but `Intl.DateTimeFormat` is the most powerful and modern standard.
1. Basic String Methods:
		-> now.toDateString()
		-> now.toISOString()
		-> now.toLocaleDateString()
2. The Professional Way: `Intl.DateTimeFormat`
    This allows you to customize the output format fully based on language and preferences.

##### `Date.now()` vs. `new Date()`
If you only need the **current timestamp** (for performance testing or unique IDs) and not the full object, use `Date.now()`. It is faster.
- **`new Date()`**: Returns a heavy Object with methods.
- **`Date.now()`**: Returns a simple Number (milliseconds).

##### Common Pitfalls
- **Month Indexing:** Forgetting that January is `0` is the #1 error. Always check your inputs: `new Date(2023, 1, 1)` is **February** 1st, not January.
- **Date Mutation:** Methods like `setDate` change the _original_ object. They do not return a new one.
- **Timezones:** `new Date()` uses the browser's local system time. If you are working with servers across the world, rely on `.toISOString()` or libraries like `date-fns` to handle UTC consistency.

| **Goal**                     | **Do you need Getters/Setters?** | **Method Used**         |
| ---------------------------- | -------------------------------- | ----------------------- |
| **Get just the year**        | **Yes**                          | `.getFullYear()`        |
| **Change the month**         | **Yes**                          | `.setMonth()`           |
| **Print "12/02/2025"**       | **No**                           | `.toLocaleDateString()` |
| **Save to Database**         | **No**                           | `.toISOString()`        |
| **Check if Date A > Date B** | **No**                           | `Date A > Date B`       |

Creating Date:
```JavaScript
// 1. new Date() -> Returns the current moment
const now = new Date();
console.log("1. Current Time:   ", now);

// 2. new Date(value) -> Uses milliseconds since Jan 1, 1970
// 1735689600000 is equivalent to Jan 1, 2025
const fromTimestamp = new Date(1735689600000);
console.log("2. From Timestamp: ", fromTimestamp);

// 3. new Date(dateString) -> Parses a standard date string
//defaults to UTC (Midnight in London)
const fromString = new Date("2025-12-25");
console.log("3. From String:    ", fromString);

// 4. new Date(year, month, day, ...) -> Uses specific numbers
// WARNING: Month is 0-indexed! (0 = Jan, ... 11 = Dec)
// Here: 2025, 11 (Dec), 25 (Day), 14 (2 PM), 30 (Minutes)
//uses your _local_ computer time directly.
const fromComponents = new Date(2025, 11, 25, 14, 30, 0); 
console.log("4. From Components:", fromComponents);
```

To calculate the timestamp between two dates with mixed formats, you **cannot** rely on `new Date("string")` because JavaScript gets confused about which number is the month and which is the day.
The most reliable way is to **manually parse** the strings using `.split('/')` and pass the specific numbers into `new Date(year, monthIndex, day)`.

```JavaScript
// Input 1: MM/DD/YYYY (US Format)
const usDateString = "10/05/2025"; // October 5th

// Input 2: DD/MM/YYYY (International Format)
const intlDateString = "25/12/2025"; // December 25th

// --- STEP 1: Parse the US Date (MM first) ---
const [usMonth, usDay, usYear] = usDateString.split('/');
// Remember: Subtract 1 from month because JS counts 0-11
const date1 = new Date(usYear, usMonth - 1, usDay);

// --- STEP 2: Parse the Intl Date (DD first) ---
const [intlDay, intlMonth, intlYear] = intlDateString.split('/');
// Remember: Subtract 1 from month here too
const date2 = new Date(intlYear, intlMonth - 1, intlDay);


// --- STEP 3: Get Timestamps & Calculate Difference ---
const time1 = date1.getTime();
const time2 = date2.getTime();

console.log(`Timestamp 1: ${time1}`);
console.log(`Timestamp 2: ${time2}`);

// Difference in milliseconds
const difference = Math.abs(time2 - time1); 
console.log(`Difference in ms: ${difference}`);

// Convert to days (optional)
const daysDiff = difference / (1000 * 60 * 60 * 24);
console.log(`Days between: ${daysDiff}`);
```