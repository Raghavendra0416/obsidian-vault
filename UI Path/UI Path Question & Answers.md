##### Q.1 What are the different ways a project can build in UI Path?
Ans:
**Sequences:** Small type of projects or linear projects.
**Flow Charts:** Used for large jobs or even used for small projects.
**State Machines:** When a project has certain states and switches during execution.
**ReFramework:** Robotic Enterprise Framework.

---
##### Q2. Different Types of Variables and arguments?
Ans:
Most Used Variables:
String, Int32, Boolean, Generic Value, Array, Data table, list etc...
Three direction argument:
In, Out, In-Out

---
###### Q3. What is the difference between Array and List?
Ans:
**Array:** This a variable type which enables you to store Multiple values of the same type. Has fixed size.
**List:** If you would like to store collections of values and that does not have fixed number of elements.

---

##### Q6. What is UI Path Selector? and Reliable Selector?
Answer:
A **Selector** is a string of XML characters that identifies a specific User Interface (UI) element on the screen.

It works by matching the element's attributes—such as its ID, name, or the window title—to ensure the robot interacts with the exact right component, regardless of its position on the screen.

---

##### Q5. What is the difference between Full Selectors and Partial Selector? 
Ans:
The main difference lies in **where the information is stored** and **how they interact with windows.**

| **Feature**     | **Full Selector**                                                     | **Partial Selector**                                                     |
| --------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **Window Info** | Includes the top-level window information (e.g., `app='chrome.exe'`). | Does **not** include the top-level window information.                   |
| **Storage**     | Stored entirely within the activity itself.                           | Stored partially in the **Attach Window** or **Open Browser** container. |
| **Best Use**    | When switching between multiple windows or applications.              | When performing multiple actions inside the same window.                 |
| **Performance** | Slightly slower (re-checks the window every time).                    | Faster and more reliable for automated sequences.                        |

"A **Full Selector** contains all the information needed to find an element, including the top-level window tag. It’s independent and can work even if the window isn't currently in focus.

A **Partial Selector** lacks the window tag and must be placed inside a container (like 'Attach Window'). Because the container handles the window search once, Partial Selectors are generally faster and more stable for complex workflows."

---

##### Q6. What is Ui Explorer?
Ans:
`UiExplorer` gives you the full picture. It displays the **Visual Tree** (the hierarchy of the app) and every available attribute for an element.
- **Visual Tree:** Shows you the parent and child elements, helping you understand the app's structure.
- **Property Explorer:** Displays all attributes (visible and hidden) associated with a UI element.
- **Fine-Tuning:** Lets you check or uncheck specific attributes to make a selector "stable" (reliable) or "dynamic" (flexible).

---

###### Q7. How many types of recordings available in UI Path?
Ans:
Basic, Desktop, Web, Image, Native Citrix, Computer Vision.

---

##### Q8. How to save Credentials in windows and use in UI Path? and How to save Credentials in UI Path and use while creating a Automation?
Ans:
Credential Manager

---

###### Q9. What is Exception Handling? and their differences?
Ans:
Try Catch, Throw, ReThrow, Terminate workflow etc...

----

##### Q10. What is Data Scraping and Screen Scraping? and their differences?
Ans: 
**Data Scraping:**
Data Scraping extracts structured or tabular data from a browser, application or document and convert it into data table format.
**Screen Scraping:**
It extracts data from a specified UI Element or document using Full Text, Native or OCR Methods.

---

##### Q11. 