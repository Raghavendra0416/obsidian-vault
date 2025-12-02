**What is HTTP?**  
HTTP (Hypertext Transfer Protocol) is the basic, stateless protocol browsers and servers use to request and deliver web data (pages, images, APIs).

**Why do we use HTTP?**  
It standardizes how clients and servers communicate, enabling the whole web to interoperate; HTTPS (HTTP over TLS) adds privacy and integrity.

**How do we use HTTP?**  
A browser or app sends an HTTP request (e.g., `GET /page`) with headers and optional body; the server replies with a status code, headers, and content.

![[Pasted image 20251202200515.png]]

---
#### How Does HTTP Request is made and what are the components?

Summary:
1. You enter an `https://...` URL → the browser may check cache, does DNS to find the site’s IP, then opens a connection to port 443 and performs a TLS handshake (HTTPS) to encrypt and verify the server. (**HTTPS first:** The browser does DNS, then a **TLS handshake** (HTTPS) before any HTTP request)
2. Over that secure connection, the browser sends an **HTTP request** (e.g., `GET /path`) with **request headers** (Host, User-Agent, Accept, Cookie, etc.).  
    _Note: “status” is **not** in the request._
3. The server sends an **HTTP response** with a **status code** (200, 404, …), **response headers** (Content-Type, Cache-Control, Set-Cookie, Server, …), and a **body** (often HTML, but could be JSON, images, etc.).
4. The browser parses the HTML, builds the page, and discovers more resources (CSS, JS, images, fonts, API calls). It makes **additional HTTP requests** for those—often reusing the same connection (HTTP/2/HTTP/3 can fetch many in parallel).
5. The page renders; resources may be cached for speed on later visits. Redirects or errors, if any, are handled via status codes and headers.
Quick flow recap:
- URL → DNS → TLS (HTTPS).
- Browser sends HTTP **request** (+ headers).
- Server returns **response** (status + headers + body).
- Browser parses HTML, then fetches CSS/JS/images via more requests.
- Renders page; may cache resources.
to know DNS & TLS go to end of the page

A HTTP request is sent to server.
In server the the request for HTTP is found(if the file location) and sent back a the response as GET. here we are sending a request to download the files from server to load the webpage.

At first the HTML file will be taken and based on that HTML file requests will be made. If a request is successful we will get status as 200 ok.

###### **What does a request contains?**

![[Pasted image 20251104222401.png]]

from the above example you can see that - www . flipkart.com has requested and it is the main html file. based on the html file remaining files requests are sent out. 

###### What does headers of HTTP request contains?
HTTP request in the “General” section
- Request URL
- Request Method
- Status Code
- Remote Address

	- Request URL → URL of the resource fetched (what you typed in the Browser’s URL bar)
	- Request Method → Action to be done. “GET” is for downloading (getting) some resource
	- (Response) Status Code → How the server responded to the request
		- “200 OK” means a successful request
		- As this is a successful “GET” request, server will have sent some data back i.e, website’s HTML content
	- Remote Address → Address of the application serving the resource requested. Has two sections
		- IP address → Location of the server hosting the resource (eg: 163.53.78.128)
		- Port → Location of the application within the server, serving the resource (eg: 443)

###### What is IP address?
 - IP address is varying across these websites but the port number turns out to be the same.
 - Different houses will have different addresses, so do different servers on the internet
 - As IP address essentially is the address of a server in the internet, it will be different for different servers
###### About HTTP protocol:
- `https` is a more secure version of the HTTP protocol and is very widely used instead of `http`
- HTTPS servers can be accessed at Port 443 by default.

12.0.1.15:443 - This type of address is sent. 
- In `12.0.1.15:443`
- `12.0.1.15` is IP address
- 443 denotes the port
- 443 is the default port for HTTPS communication
- IP address of different servers will be different
##### Response headers:
![[Pasted image 20251104224312.png]]
Response headers contain more information about the HTTP response sent by the server.
- `Content-Type` → Type of the response content (eg: `text/html` → HTML)
- `Server` → Web server software used by the server (eg: nginx, Apache, AmazonS3)

Similarly, the Request headers contain more information about the HTTP request sent to the server

---
#### Question & Answers:
##### We looked at how requesting for a HTML file inturn creates a new HTTP request to fetch resources like scripts & images within it. Visit a couple of websites & inspect the resources loaded. Is there any order in which the resources are loaded? Does HTTP mandate this?
###### Answer:
You are right that the **HTTP protocol itself doesn't mandate a specific loading order**.1 HTTP is just the protocol for _requesting_ and _receiving_ resources.2 It doesn't tell a browser _what_ to request or _when_.

However, browsers (like Chrome, Firefox, or Safari) absolutely **do have a complex and specific order** for loading resources.3 This order isn't random; it's heavily optimized to make the page appear usable as quickly as possible.
##### How Browsers Prioritize Loading
The browser's main goal is to paint the page for the user (called the "First Contentful Paint") as fast as it can. To do this, it prioritizes resources based on how critical they are for rendering the initial view.

The general order of discovery and prioritization is:
1. **HTML:** The document itself is always first.
    
2. **Critical CSS:** CSS files referenced in the `<head>` are extremely high priority. The browser won't (and can't) render the page until it downloads and parses the CSS, as it needs to know how to style everything.4 This is known as **render-blocking**.
    
3. **Synchronous JavaScript:** Scripts in the `<head>` (or in the `<body>` without an `async` or `defer` attribute) are also high priority and **render-blocking**.5 The browser has to stop parsing the HTML, download the script, run it, and _then_ continue, because the script could potentially change the page structure (e.g., with `document.write()`).6
    
4. **Fonts:** Web fonts are often loaded with high priority because the browser can't render the text correctly without them.
    
5. **Images & Media (Above the Fold):** Images that are visible in the initial viewport are prioritized.
    
6. **Deferred/Async JavaScript:** Scripts marked with `defer` (run after HTML parsing is complete) or `async` (run whenever they finish downloading) are lower priority because they don't block the initial page paint.7
    
7. **Images & Media (Below the Fold):** Images and other media that are "below the fold" (not visible until the user scrolls) are typically given the lowest priority.8

So, while the browser discovers resources as it parses the HTML from top to bottom, it assigns a **priority** to each one and tries to download the most critical assets first.

##### Is it possible to tell the server software which Flipkart use based on any of the HTTP Response headers the server sent back?
**Answer:**
It is Nginx.
The **Server** response header tells us about the server software used by the Flipkart software. See [snapshot](https://drive.google.com/file/d/12ZIaxALuq8uukuMZ0SBfgiD6EfEQe1bu/view?usp%3Dsharing) & more [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Server)

Though the default behavior is to send the server name, this can be customized to hide it from end-users. See [here](https://stackoverflow.com/a/33513698/9734484)

[HTTP caching](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Caching)

---

What is HTTP?
HTTP (Hypertext Transfer Protocol) is the stateless request–response protocol web browsers and servers use to exchange data (pages, images, APIs).  
It defines methods like GET/POST over TCP (typically port 80).  
HTTPS is HTTP secured with TLS encryption.

How HTTP requests?
- The number of HTTP requests made depends on the web page
-  The URL of a page denotes the location of its HTML file. Hence, its the HTML file which always gets fetched first. Also, browser figures out the other resources a web page needs by checking the HTML file
- Browsers send network requests to the server hosting a web page in the form of HTTP requests
- Networks tab of Chrome Developer Tools lists the HTTP requests made to load a page
- HTML always is the first resource fetched while loading a web page

What HTTP Does
Modern protocols like **HTTP/2** and **HTTP/3** help this process immensely.

- **HTTP/1.1** could only download a few files (like ~6) at a time from one domain, which created a "head-of-line blocking" problem.
- **HTTP/2** introduced **multiplexing**, which allows the browser to request dozens of resources over a _single_ connection. Even then, the browser still tells the server which resources are more important (e.g., "send me this CSS file before this image") so the critical files arrive first.

In short: The browser decides the order, and the HTTP protocol provides the mechanism to fetch the files efficiently based on that order.

---
#### How a Webpage loads:
**Step 1: You type a URL and press Enter.**  
The browser decides to use HTTPS if possible.

**Step 2: Find the server’s address (DNS).**  
Browser/OS asks a DNS resolver (often your ISP’s) which asks other DNS servers to get an IP for the domain.

**Step 3: Travel path to the server.**  
Your device → Wi-Fi/router → your ISP → the internet → (often a nearby CDN edge) at that IP.

**Step 4: Open a connection.**  
Browser and server do a quick TCP “handshake” to talk.

**Step 5: Secure the connection (HTTPS).**  
They do a TLS handshake so traffic is encrypted and the site’s certificate is verified.

**Step 6: Send the request.**  
Browser sends an HTTP request like `GET /path` with headers (and cookies, if any).

**Step 7: Server does the work.**  
The website’s server/app may read from databases or caches and prepares a response.

**Step 8: Get the response.**  
Server sends back a status code (e.g., 200 OK), headers (cache rules, content type), and the page content.

**Step 9: Browser renders the page.**  
It reads the HTML, then fetches CSS, JS, images, fonts, etc., and lays out/paints the page.

**Step 10: More requests happen.**  
Each image/script/font is another (often parallel) HTTP(S) request over the same secure connection.

**Step 11: Caching & policies.**  
Browser/CDN may store files for speed next time; security rules (CORS, CSP, mixed content) are enforced.

**Step 12: You see the page.**  
Interactivity comes from JavaScript; links or actions repeat these steps as needed.

---
#### HTTP Journey:
**Step 1: You enter a URL.**  
The browser figures out the website name (e.g., example.com) and whether to use HTTPS.

**Step 2: Find the server (DNS).**  
It asks DNS “What’s the IP address of example.com?” and gets a number like 93.184.216.34.

**Step 3: Connect to that address.**  
Your device opens a network connection to that IP (TCP handshake).

**Step 4 (HTTPS only): Make it secure.**  
Browser and server do a TLS handshake to encrypt traffic and verify the site’s certificate.

**Step 5: Send an HTTP request.**  
Usually `GET /path` plus headers (who’s asking, what it accepts, cookies, etc.).

**Step 6: Server processes it.**  
The server/app may read a database, hit a cache, or run code to prepare the answer.

**Step 7: Receive an HTTP response.**  
Status line (e.g., `200 OK`), headers (content type, caching), and the body (HTML, JSON, image…).

**Step 8: Browser handles the body.**  
If it’s HTML, the browser starts building the page and discovers more files to fetch (CSS, JS, images).

**Step 9: More HTTP requests for assets.**  
Those files are requested (often over the same connection; HTTP/2/3 can multiplex).

**Step 10: Caching & policies.**  
Browser/CDN may cache responses; security rules like CORS/CSP are enforced.

**Step 11: Render & interact.**  
The page is laid out, painted, and JavaScript runs—clicks and API calls are just more HTTP requests.

**Step 12: Reuse the connection.**  
Keep-Alive/HTTP/2/3 lets multiple requests share one connection for speed.

---

What is DNS?
1. **Goal:** Turn a name (e.g., `example.com`) into an **IP address** (like `93.184.216.34`).
2. **How:** Your browser asks a **DNS resolver** (often your ISP or a public one).
3. **Lookup chain:** Resolver → Root servers → `.com` servers → **Authoritative** server for `example.com`.
4. **Result:** Get the IP, **cache** it for a while (TTL), then the browser can connect to that IP.

What is a TLS handshake (HTTPS)?
1. **Goal:** Create a **secure, encrypted** connection and verify you’re talking to the real server.
2. **Hello:** Browser says “hello” with supported encryption options; server replies with its choices and its **certificate**.
3. **Verify:** Browser checks the certificate (issued by a trusted Certificate Authority) to confirm the server’s identity.
4. **Keys:** Browser and server securely agree on **session keys** (for encryption).
5. **Secure channel:** Now all HTTP data (requests/responses) go through this encrypted tunnel.

**Why it matters:**
- **DNS** finds _where_ to connect.
- **TLS** makes the connection **private** and **authentic** before any HTTP request is sent.

|Feature|DOM|Developer Tools|
|---|---|---|
|Definition|Browser’s internal model of the page|Interface/UI to view & debug the DOM|
|Created by|Browser|Browser tools (e.g., Chrome DevTools)|
|Editable|Yes (via JavaScript)|Yes, but temporary|
|Where it exists|In browser memory|In the DevTools panel|
|Used by JS code?|✔ Yes|❌ No|
|Reflects live changes?|✔ Always|✔ Shows the DOM live|
|Permanent?|✔ DOM updates during runtime|❌ Edits disappear after refresh|