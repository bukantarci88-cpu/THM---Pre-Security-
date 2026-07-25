# Pre-Security - 3. How The Web Works

## 1. DNS in Detail

**DNS:** The **Domain Name System (DNS)** translates human-readable domain names into IP addresses, making it easier to access devices on the internet without remembering complex numerical addresses.

**TLD (Top-Level Domain):** A **Top-Level Domain (TLD)** is the last part of a domain name (e.g., **.com** in *tryhackme.com*). TLDs are categorized as **gTLDs** (Generic TLDs) and **ccTLDs** (Country Code TLDs).

**Second-Level Domain:** The **Second-Level Domain (SLD)** is the main name of the domain (e.g., **tryhackme** in *tryhackme.com*). It can contain up to 63 characters and use letters, numbers, and hyphens.

**Subdomain:** A **subdomain** appears before the SLD (e.g., **admin** in *admin.tryhackme.com*) and helps organize services or sections of a website. It follows the same naming restrictions as an SLD.

**DNS Record Types:** DNS supports various record types that provide different kinds of information, such as website addresses, email servers, and domain aliases.

**A Record:** An **A Record** maps a domain name to an **IPv4 address**.

**AAAA Record:** An **AAAA Record** maps a domain name to an **IPv6 address**.

**CNAME Record:** A **CNAME (Canonical Name) Record** points one domain or subdomain to another domain name, requiring an additional DNS lookup to find the final IP address.

**MX Record:** An **MX (Mail Exchange) Record** specifies the mail servers responsible for handling email for a domain.

**TXT Record:** A **TXT Record** stores text-based information and is commonly used for email authentication, domain verification, and other administrative purposes.

## **2. What happens when you make a DNS request**

![a diagram visualizing the flow described in the text](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1724075620083.png)

- Your computer first checks its local DNS cache for the requested domain. If the address is not found, it sends a query to a recursive DNS server.
- The recursive DNS server checks its own cache. If the record is available, it returns the result; otherwise, it begins searching for the answer.
- The recursive server contacts a root DNS server, which identifies the domain's Top-Level Domain (TLD) and directs the request to the appropriate TLD server.
- The TLD server responds with the address of the domain's authoritative DNS server (nameserver), which stores the domain's DNS records.
- The authoritative DNS server returns the requested DNS record to the recursive server. The result is cached according to its TTL (Time To Live) value and then sent back to the client, enabling communication with the target server.

What field specifies how long a DNS record should be cached for? TTL

What type of DNS Server is usually provided by your ISP? Recursive

What type of server holds all the records for a domain? Autoratitive

## **3. HTTP in Detail**

- **HTTP (HyperText Transfer Protocol)** is the protocol used to communicate with web servers and transfer website content such as HTML pages, images, videos, and other web resources.
- **HTTPS (HyperText Transfer Protocol Secure)** is the encrypted and secure version of HTTP. It protects data in transit and helps verify that you are communicating with the legitimate web server.
- **URL (Uniform Resource Locator)** is the web address used to locate and access resources on the internet. It provides instructions on where a resource is located and how it should be accessed.

![A diagram showing different parts of a URL on an example, where http is the scheme, user:password is the user, tryhackme.com is a domain or the host, 80 is the port, view-room is the path, ?id=1 is the query string, and #task3 is the fragment. The full address is http://user:password@tryhackme.com:80/view-room?id=1#task3.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/34ad66d8b90aaaa35f9536d3b152ea97.png)

**Scheme:** This instructs on what protocol to use for accessing the resource such as HTTP, HTTPS, FTP (File Transfer Protocol).

**User:** Some services require authentication to log in, you can put a username and password into the URL to log in.

**Host:** The domain name or IP address of the server you wish to access.

**Port:** The Port that you are going to connect to, usually 80 for HTTP and 443 for HTTPS, but this can be hosted on any port between 1 - 65535.

**Path:** The file name or location of the resource you are trying to access.

**Query String:** Extra bits of information that can be sent to the requested path. For example, /blog?**id=1** would tell the blog path that you wish to receive the blog article with the id of 1.

**Fragment:** This is a reference to a location on the actual page requested. This is commonly used for pages with long content and can have a certain part of the page directly linked to it, so it is viewable to the user as soon as they access the page.

**HTTP Methods** HTTP methods are a way for the client to show their intended action when making an HTTP request. There are a lot of HTTP methods but we'll cover the most common ones, although mostly you'll deal with the GET and POST method.

**GET Request** This is used for getting information from a web server.

**POST Request** This is used for submitting data to the web server and potentially creating new records

**PUT Request** This is used for submitting data to a web server to update information

**DELETE Request** This is used for deleting information/records from a web server.

What method would be used to create a new user account? POST

What method would be used to update your email address? PUT

What method would be used to remove a picture you've uploaded to your account? Delete

What method would be used to view a news article? GET

**HTTP Status Codes:** These status codes can be broken down into 5 different ranges:

| **100-199 - Information Response** | These are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request. These codes are no longer very common. |
| --- | --- |
| **200-299 - Success** | This range of status codes is used to tell the client their request was successful. |
| **300-399 - Redirection** | These are used to redirect the client's request to another resource. This can be either to a different webpage or a different website altogether. |
| **400-499 - Client Errors** | Used to inform the client that there was an error with their request. |
| **500-599 - Server Errors** | This is reserved for errors happening on the server-side and usually indicate quite a major problem with the server handling the request. |

**Common HTTP Status Codes:** the most common HTTP responses you are likely to come across:

| **200 - OK** | The request was completed successfully. |
| --- | --- |
| **201 - Created** | A resource has been created (for example a new user or new blog post). |
| **301 - Moved Permanently** | This redirects the client's browser to a new webpage or tells search engines that the page has moved somewhere else and to look there instead. |
| **302 - Found** | Similar to the above permanent redirect, but as the name suggests, this is only a temporary change and it may change again in the near future. |
| **400 - Bad Request** | This tells the browser that something was either wrong or missing in their request. This could sometimes be used if the web server resource that is being requested expected a certain parameter that the client didn't send. |
| **401 - Not Authorised** | You are not currently allowed to view this resource until you have authorised with the web application, most commonly with a username and password. |
| **403 - Forbidden** | You do not have permission to view this resource whether you are logged in or not. |
| **405 - Method Not Allowed** | The resource does not allow this method request, for example, you send a GET request to the resource /create-account when it was expecting a POST request instead. |
| **404 - Page Not Found** | The page/resource you requested does not exist. |
| **500 - Internal Service Error** | The server has encountered some kind of error with your request that it doesn't know how to handle properly. |
| **503 - Service Unavailable** | This server cannot handle your request as it's either overloaded or down for maintenance. |

**Headers** are additional bits of data you can send to the web server when making requests. Although no headers are strictly required when making a HTTP request, you’ll find it difficult to view a website properly.

**Common Request Headers** These are headers that are sent from the client (usually your browser) to the server.

**Host:** Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.

**User-Agent:** This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.

**Content-Length:** When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.

**Accept-Encoding:** Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.

**Cookie:** Data sent to the server to help remember your information (see cookies task for more information).

**Common Response Headers** These are the headers that are returned to the client from the server after a request.

**Set-Cookie:** Information to store which gets sent back to the web server on each request (see cookies task for more information).

**Cache-Control:** How long to store the content of the response in the browser's cache before it requests it again.

**Content-Type:** This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.

**Content-Encoding:** What method has been used to compress the data to make it smaller when sending it over the internet.

What header tells the web server what browser is being used? User-Agent

What header tells the browser what type of data is being returned? Content-Type

What header tells the web server which website is being requested? Host

**Cookies** are small pieces of data stored by your browser when a web server sends a **Set-Cookie** header. The browser sends the cookie back with future requests, allowing the server to remember information about the user. Since **HTTP is stateless** and does not remember previous interactions, cookies help maintain sessions, store user preferences, and track whether a user has visited a website before.

## **4. How Websites Work**

- **How Websites Work:** When you visit a website, your browser sends a request to a web server. The server processes the request and sends back data that the browser uses to display the webpage. A web server is a computer that stores and delivers website content.
- **Website Technologies:** Websites are mainly built using:
    - **HTML** – Defines the structure and content of a webpage.
    - **CSS** – Controls the design and appearance of the webpage.
    - **JavaScript** – Adds interactive and dynamic features.
- **HTML Injection:** A vulnerability that occurs when a website displays unfiltered user input. Attackers can inject malicious HTML code if the application does not properly sanitize user-provided data.
- **Input Sanitisation:** A security practice that filters and validates user input to prevent attacks such as HTML Injection and database injection by ensuring unsafe data is not processed.
- **Load Balancers:** Load balancers distribute incoming traffic across multiple servers to improve performance, handle high traffic volumes, and provide availability if one server fails.
- **CDN (Content Delivery Network):** A CDN stores and delivers static website files such as images, videos, CSS, and JavaScript from servers around the world to reduce load times and improve performance.
- **Databases:** Websites use databases to store and retrieve user information and application data. Databases can range from simple files to large server clusters designed for speed and reliability.
- **WAF (Web Application Firewall):** A WAF protects web applications by filtering and analyzing incoming requests to detect and block attacks such as hacking attempts, malicious traffic, and denial-of-service attacks.

**Virtual Hosts**

- **Web Server:** A web server is software that receives client requests and uses the **HTTP protocol** to deliver web content. Common web servers include **Apache, Nginx, IIS, and Node.js**. Web servers store website files in a defined **root directory** and serve them to users when requested.
- **Virtual Hosts:** Virtual hosts allow a single web server to host multiple websites with different domain names. The server checks the hostname in the HTTP request, matches it with the correct virtual host configuration, and delivers the corresponding website. If no match is found, the default website is displayed.
- **Static Content:** Static content is website data that does not change, such as images, CSS files, JavaScript files, and fixed HTML pages. These files are delivered directly from the web server without modification.
- **Dynamic Content:** Dynamic content changes based on user requests or data. Examples include blogs showing the latest posts or search pages displaying different results based on user input. Dynamic pages are generated or updated when requested.