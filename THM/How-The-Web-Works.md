# DNS in detail

## What is DNS ?

DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers.

## Domain Hierarchy

### TLD (Top-Level Domain)

A TLD is the most righthand part of a domain name. 

So, for example, the tryhackme.com TLD is .com. 

There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain). 

Historically a gTLD was meant to tell the user the domain name's purpose; for example, a .com would be for commercial purposes, .org for an organisation, .edu for education and .gov for government.

And a ccTLD was used for geographical purposes, for example, .ca for sites based in Canada, .co.uk for sites based in the United Kingdom and so on.

### Second-Level Domain

Taking tryhackme.com as an example, the .com part is the TLD, and tryhackme is the Second Level Domain.

### Subdomain

A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it; for example, in the name admin.tryhackme.com the admin part is the subdomain.

You can use multiple subdomains split with periods to create longer names, such as jupiter.servers.tryhackme.com. 

But the length must be kept to 253 characters or less. There is no limit to the number of subdomains you can create for your domain name.

## DNS Record Types

DNS isn't just for websites though, and multiple types of DNS record exist. We'll go over some of the most common ones.

### A Record

These records resolve to IPv4 addresses, for example 104.26.10.229

### AAAA Record

These records resolve to IPv6 addresses, for example 2606:4700:20::681a:be5

### CNAME Record

These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name store.tryhackme.com which returns a CNAME record shops.shopify.com. Another DNS request would then be made to shops.shopify.com to work out the IP address.

### MX Record

These records resolve to the address of the servers that handle the email for the domain you are querying.

### TXT Record

TXT records are free text fields where any text-based data can be stored. TXT records have multiple uses, but some common ones can be to list servers that have the authority to send an email on behalf of the domain (this can help in the battle against spam and spoofed email). They can also be used to verify ownership of the domain name when signing up for third party services.

## Making a request

![image](https://user-images.githubusercontent.com/112873207/192320780-6f2a6e6a-2451-4b9c-8935-a6a458eef748.png)


Making a request with a command line : `nslookup --type=TXT website.thm`

# HTTP in detail

## What is HTTP(S)

HTTP (HyperText Transfer Protocol) is what's used whenever you view a website, developed by Tim Berners-Lee and his team between 1989-1991. 

HTTP is the set of rules used for communicating with web servers for the transmitting of webpage data, whether that is HTML, Images, Videos, etc.

What is HTTPS? (HyperText Transfer Protocol Secure)? HTTPS is the secure version of HTTP.

## Requests and responses

### What is URL (Uniforme Resources Locator)

The below image shows what a URL looks like with all of its features (it does not use all features in every request).

![image](https://user-images.githubusercontent.com/112873207/192329260-cd8c5423-f710-4ed2-937d-21e5b836580f.png)

- Scheme: This instructs on what protocol to use for accessing the resource such as HTTP, HTTPS, FTP (File Transfer Protocol).

- User: Some services require authentication to log in, you can put a username and password into the URL to log in.

- Host: The domain name or IP address of the server you wish to access.

### Making a request (with commands)

![image](https://user-images.githubusercontent.com/112873207/192331539-b74bb778-1d3b-482f-b97e-1fe8ce5deb0e.png)

Line 1: This request is sending the GET method ( more on this in the HTTP Methods task ), request the home page with / and telling the web server we are using HTTP protocol version 1.1.

Line 2: We tell the web server we want the website tryhackme.com

Line 3: We tell the web server we are using the Firefox version 87 Browser

Line 4: We are telling the web server that the web page that referred us to this one is https://tryhackme.com

Line 5: HTTP requests always end with a blank line to inform the web server that the request has finished.

- Port: The Port that you are going to connect to, usually 80 for HTTP and 443 for HTTPS, but this can be hosted on any port between 1 - 65535.

- Path: The file name or location of the resource you are trying to access.

- Query String: Extra bits of information that can be sent to the requested path. For example, /blog?id=1 would tell the blog path that you wish to receive the blog article with the id of 1.

- Fragment: This is a reference to a location on the actual page requested. This is commonly used for pages with long content and can have a certain part of the page directly linked to it, so it is viewable to the user as soon as they access the page.

## HTTP Methods

There are a lot of HTTP methods but we'll cover the most common ones, although mostly you'll deal with the GET and POST method.

- GET Request : This is used for getting information from a web server.
- POST : This is used for submitting data to the web server and potentially creating new records.
- PUT : This is used for submitting data to a web server to update information.
- DELETE : This is used for deleting information/records from a web server.

## HTTP Status Code
### HTTP Status Codes

In the previous task, you learnt that when a HTTP server responds, the first line always contains a status code informing the client of the outcome of their request and also potentially how to handle it. These status codes can be broken down into 5 different ranges:

![image](https://user-images.githubusercontent.com/112873207/192338429-008d074f-23e2-4a96-af1c-2c4ff3f2befe.png)

### Common HTTP Status Codes

There are a lot of different HTTP status codes and that's not including the fact that applications can even define their own, we'll go over the most common HTTP responses you are likely to come across: 

![image](https://user-images.githubusercontent.com/112873207/192338866-393ae1c1-f174-4d01-b10b-918bb318e9ed.png)

## Headers 

Headers are additional bits of data you can send to the web server when making requests.

Although no headers are strictly required when making a HTTP request, you’ll find it difficult to view a website properly.

### Common Request Headers

These are headers that are sent from the client (usually your browser) to the server.

- Host: Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.

- User-Agent: This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.

- Content-Length: When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.

- Accept-Encoding: Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.

### Common Response Headers

These are the headers that are returned to the client from the server after a request.

- Set-Cookie: Information to store which gets sent back to the web server on each request (see cookies task for more information).

- Cache-Control: How long to store the content of the response in the browser's cache before it requests it again.

- Content-Type: This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.

- Content-Encoding: What method has been used to compress the data to make it smaller when sending it over the internet.

## Cookies

You've probably heard of cookies before, they're just a small piece of data that is stored on your computer. 

Cookies are saved when you receive a "Set-Cookie" header from a web server. 

Then every further request you make, you'll send the cookie data back to the web server. 

Because HTTP is stateless (doesn't keep track of your previous requests), cookies can be used to remind the web server who you are, some personal settings for the website or whether you've been to the website before.

# How Websites works

## Websites

There are two major components that make up a website:

- Front End (Client-Side) - the way your browser renders a website.
- Back End (Server-Side) - a server that processes your request and returns a response.

## HTML

Websites are primarily created using:

- HTML (HyperText Markup Language), to build websites and define their structure
- CSS, to make websites look pretty by adding styling options
- JavaScript, implement complex features on pages using interactivity

![image](https://user-images.githubusercontent.com/112873207/192770847-712ee293-073b-46f4-9def-4dbe340f639f.png)
The HTML structure (as shown in the screenshot) has the following components:

- The <!DOCTYPE html> defines that the page is a HTML5 document. This helps with standardisation across different browsers and tells the browser to use HTML5 to interpret the page.
- The <html> element is the root element of the HTML page - all other elements come after this element.
- The <head> element contains information about the page (such as the page title)
- The <body> element defines the HTML document's body; only content inside of the body is shown in the browser.
- The <h1> element defines a large heading 
- The <p> element defines a paragraph
- There are many other elements (tags) used for different purposes. For example, there are tags for buttons (<button>), images (<img>), lists, and much more.

Tags can contain attributes e.g. : <p attribute1="idk1" attribute2="idk2">.
  
Tags can also have an id attribute which is unique to the element e.g. : <p id="yessir">
  
## JavaScript
  
