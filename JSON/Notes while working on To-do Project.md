- When page is redirected to another page from the current page, then the data in current page will be erased. To overcome this we need to use Local Storage, Browser Storage.

Data Exchange Methods Between Pages:
1. localStorage - Data persists even after closing browser
2. sessionStorage - Data persists only during the browser session (tab open)
3. URL Parameters - Data passed through the URL
4. Cookies - Data stored with expiration dates, accessible by server too How we are gonna use them
###### We need to use different JavaScript files for different HTML pages. 
Reason: Suppose:
We are having 2 HTML files: HTML1, HTML2 and 2 JS files: JS1.js, JS2.js.
When we are redirected from HTML1 to HTML2 then the data we have used and everything will be resettled before going to the HTML2 file. Once we are in HTML2 file then the data from the HTML1 file will be erased. 
So, if we try to use the same file for HTML1 & HTML2 then the values, fields, elements in the HTML1 file won't be there and it will cause the JS script to fail.
If we use different scripts then they HTML files will be having their own data in their own scripts. This individuality will help work more effectively.


Q. What does `window.location.href = ""` mean?
`window.location.href` represents the **current URL of the browser**.
- **Reading it** → gives the current page URL
- **Setting it** → tells the browser to **navigate to a new page**
Even though we are writing this code in js file. We are appending the link and element to the html file, so we need to think we are in html file even if we are in js file while proving the path here.

Append & AppendChild:
`append()` and `appendChild()` can add HTML elements (DOM nodes).
Append -> is used when we need to add multiple elements or data.
AppendChild -> is used when we need to append only a single value. We cannot append text, we can only append DOM elements.