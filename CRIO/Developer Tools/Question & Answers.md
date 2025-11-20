### What is the use of ip address? which ip address does https will get?  and why does port number is different for every website and how we use this port number? 
Answer:
- **IP address — what for?**  
    It’s the numeric address of a device on the Internet. Routers use it to deliver your packets to the right machine. DNS turns names (like `example.com`) into IPs.
    
- **Which IP does HTTPS use?**  
    When you open `https://domain`, your device does a **DNS lookup** for that domain and connects to **the returned IP** (often a load balancer/CDN) on **port 443**. With **SNI** (a TLS feature), many domains can share the same IP.
    
- **Why different port numbers & how are they used?**  
    Ports identify **which service** on a machine you want. They’re not “per website”; they’re **per service**.
    - Common ones: **80 = HTTP**, **443 = HTTPS**.
    - Non-standard services might use others (e.g., `https://example.com:8443`).
    - Servers “listen” on ports; clients connect to `IP:port`; firewalls allow/deny by port.

### If IP address is used to connect or navigate to the correct server then what does port will do? port will tell if it is http/ https to the server?
Answer:
- **IP vs Port**
    - **IP address** gets you to the right **machine**.
    - **Port** picks the right **service/process on that machine** (like apartment number at a street address). The OS delivers traffic on port 443 to whatever program is “listening” there.
        
- **Does the port tell HTTP vs HTTPS?**
    - **Not exactly.** The **URL scheme** decides the protocol the client speaks:
        - `http://` → client sends **plain HTTP** (default port **80**).
        - `https://` → client starts a **TLS handshake** first, then HTTP inside TLS (default port **443**).
    - Ports are just conventions. You can run HTTPS on another port (e.g., `https://example.com:8443`). If you talk the **wrong protocol** to a port (e.g., plain HTTP to 443), the connection fails.

- **What happens on HTTPS?**
    1. DNS → IP
    2. TCP connect to **IP:443** (or custom)
    3. **TLS handshake** (includes SNI/ALPN)
    4. Send **HTTP** over the encrypted tunnel.

_(Bonus: your computer also uses a temporary **source port** on your side to keep the connection distinct from others.)_

### Real Life Example:
- **Analogy:**  
    Think of a big office tower. The **street address** = the **IP address** (gets you to the right building).  
    The **suite number** = the **port** (gets you to the right company inside the building).
- **On the Internet (one machine running many services):**
    
    ```nginx
    Your laptop 10.0.0.8:53122  →  203.0.113.5:443   (HTTPS website)
                            →  203.0.113.5:80    (HTTP website)
                            →  203.0.113.5:25    (Mail server SMTP)
                            →  203.0.113.5:22    (SSH admin access)
    ```
    
    - The **destination IP (203.0.113.5)** gets you to the correct server.
    - The **destination port** chooses the service on that server (443 = HTTPS, 80 = HTTP, etc.).
    - Your laptop also uses a temporary **source port** (here `53122`) so it can keep this connection distinct from others happening at the same time.

- **What if you “pick the wrong suite”?**  
    If you speak plain HTTP to port **443** (expects TLS first), the server won’t understand—like walking into the accounting office and speaking to them in the wrong language. The protocol and port must match the service you want.

---

### What are HTTP Request Methods?

| HTTP Request Method | Description                                                                                                                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GET                 | Can only be used to fetch data. cannot modify any data.<br>    - Eg. Retrieve list of Facebook friends                                                                                                         |
| POST                | Used to create/upload data from the server and results in change of state of server.<br>	- Eg. Create new post in Facebook                                                                                     |
| PUT                 | Used to completely update already existing data.<br>    - Eg. Update your profile.                                                                                                                             |
| DELETE              | Used to delete existing data from the server.<br>	- Eg. Delete one of the Facebook posts.                                                                                                                      |
| PATCH               | Used to partially update an already existing data.<br>	- Eg. Update relationship status only on your profile page.                                                                                             |
| OPTIONS             | Used to check the HTTP methods a server allows.                                                                                                                                                                |
| CONNECT             | Used to open tunnel to a server.<br>    - Eg. When request is sent over a proxy server.                                                                                                                        |
| HEAD                | Works similar to GET but doesn't retrieve the data but only the response status line and response headers.<br>	- Eg. To check size of the file to be downloaded using content-length                    header |
| TRACE               | Returns the request sent and used for troubleshooting purpose.                                                                                                                                                 |

---

### What are HTTP Status Codes?
HTTP Status codes are part of the HTTP Response. It helps the client understand what happened to the request.

- Status codes are 3 digit numbers (201, 304 etc) and are categorised to 5 different families based on their starting digit.
- Along with the status code, a _Reason-Phrase_ is also present (OK, Moved Permanently etc) which gives a short description of the status code.
- The _Status Code_ is intended for machines whereas _Reason-Phrase_ is for humans.


#### Codes:
- Code 200 means request was successful, and the server returned the requested data.
- Code 302 means the requested resource has been permanently moved to a new URL, the browser will do an automatic redirect to that new location.
- Code 400 means the server cannot process the request because it's malformed (often due to invalid syntax or bad parameters).
- Code 401 means the request you are making requires authentication (missing or invalid login token).
- Code 403 means the server understood the request but you don't have the permission to access the resource.
- Code 404 means the server can't find the requested URL (maybe the page or API endpoint doesn't exist).
- Code 500 mean something went wrong on the server side (it maybe a bug or misconfiguration, or an unhandled exception).