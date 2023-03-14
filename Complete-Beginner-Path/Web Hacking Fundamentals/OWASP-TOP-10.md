![image](https://user-images.githubusercontent.com/112873207/221611816-c0d07227-a656-4999-857c-74a29cc3f50e.png)

# Severity 1 : injection

## Injection : intro

![image](https://user-images.githubusercontent.com/112873207/221610203-b45c96ee-1724-466c-9b9f-b34df79ccee0.png)


What an attacker can do if he infiltrates your device :

![image](https://user-images.githubusercontent.com/112873207/221610346-8fea3c99-28e9-4378-a4b4-e77f523ff2cf.png)

How can it be countered : 

![image](https://user-images.githubusercontent.com/112873207/221610464-1f417f3f-7448-4e66-b853-8b1049a45340.png)

## OS Command Injection 

Having access to a machine can be bad but not always. If the intruder only reads files or input simple commands like `whoami` this isn't too too bad.

But it can quickly become more dangerous if he tries to reverse shell (take control of) your machine. This can be made really easily by a simple command : `;nc -e /bin/bash`.

Some variants of netcat don't support the -e option. There is a list of the differents reverse shell techniques : https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md 

## Command injection : practical 

Refer to the room for the complete exercise. 

### What is active command injection ?

**Blind** Command Injection occurs when the system command made to the server does not return the response to the user in an HTML doc. 

**Active** Command Injection, in the other hand, will return the response to the user.

### Ways to detect Active Command Injection 

![image](https://user-images.githubusercontent.com/112873207/221799898-43229b3d-ef92-4209-93dc-305fcc4d158e.png)

### Linux Interesting Commands

- Type `getent passwd [user]` and press submit to obtain the user’s shell. The 7th field of an entry in etc/passwd file is the home directory of the user (user’s     shell).

- Type `lsb_release -a` to check the ubuntu version.

# Severity 2 : Broken Authentication

Authentication and session management constitute core components of modern web applications. Authentication allows users to gain access to web applications by verifying their identities. The most common form of authentication is using a username and password mechanism. A user would enter these credentials, the server would verify them. If they are correct, the server would then provide the users’ browser with a session cookie. A session cookie is needed because web servers use HTTP(S) to communicate which is stateless. Attaching session cookies means that the server will know who is sending what data. The server can then keep track of users' actions. 

If an attacker is able to find flaws in an authentication mechanism, they would then successfully gain access to other users’ accounts. This would allow the attacker to access sensitive data (depending on the purpose of the application). Some common flaws in authentication mechanisms include:

- **Brute force attacks**: If a web application uses usernames and passwords, an attacker is able to launch brute force attacks that allow them to guess the username and passwords using multiple authentication attempts. 
- **Use of weak credentials**: web applications should set strong password policies. If applications allow users to set passwords such as ‘password1’ or common passwords, then an attacker is able to easily guess them and access user accounts. They can do this without brute forcing and without multiple attempts.
- **Weak Session Cookies**: Session cookies are how the server keeps track of users. If session cookies contain predictable values, an attacker can set their own session cookies and access users’ accounts. 

![image](https://user-images.githubusercontent.com/112873207/221824696-0ca8d1d1-2eb3-44c4-a30c-627573a42b4f.png)

## Practical example 

Refer to the room to see the complete exercise.

# Severity 3 : Data Exposure

## Intro 

When a webapp accidentally divulges sensitive data, we refer to it as "Sensitive Data Exposure". This is often data directly linked to customers (e.g. names, dates-of-birth, financial information, etc), but could also be more technical information, such as usernames and passwords. 

At more complex levels this often involves techniques such as a "Man in The Middle Attack", whereby the attacker would force user connections through a device which they control, then take advantage of weak encryption on any transmitted data to gain access to the intercepted information (if the data is even encrypted in the first place...). Of course, many examples are much simpler, and vulnerabilities can be found in web apps which can be exploited without any advanced networking knowledge. Indeed, in some cases, the sensitive data can be found directly on the webserver itself...

## Supporting Material 

The most common way to store data is in a database which can be managed by SQL. 

Also, this is common to see database set up on dedicated server such as MySQL or MariaDB but data can also be stored as files (called flat-file and stored as a single file in the computer).

Flat-files are simpler to set up than a complete database server.

As mentioned previously, flat-file databases are stored as a file on the disk of a computer. Usually this would not be a problem for a webapp, but what happens if the database is stored underneath the root directory of the website (i.e. one of the files that a user connecting to the website is able to access)? Well, we can download it and query it on our own machine, with full access to everything in the database. Sensitive Data Exposure indeed!

The most common (and simplest) format of flat-file database is an sqlite database. These can be interacted with in most programming languages, and have a dedicated client for querying them on the command line. This client is called "sqlite3", and is installed by default on Kali.

To access it we use: `sqlite3 <database-name>`

we can see the tables in the database by using the `.tables command` 

we won't necessarily know what each column means unless we look at the table information. 

We can use `PRAGMA table_info(customers)` ; to see the table information, then we can use `SELECT * FROM customers` ; to dump the information from the table.

We saw how to query an SQLite database for sensitive data. We found a collection of password hashes, one for each user. In this task we will briefly cover how to crack these.

When it comes to hash cracking, Kali comes pre-installed with various tools -- if you know how to use these then feel free to do so; however, they are outwith the scope of this material.

Instead we will be using the online tool: Crackstation. This website is extremely good at cracking weak password hashes. For more complicated hashes we would need more sophisticated tools; however, all of the crackable password hashes used in today's challenge are weak MD5 hashes, which Crackstation should handle very nicely indeed.

![image](https://user-images.githubusercontent.com/112873207/221870725-bb168cc6-2836-4f52-a8ee-91bb55af22b4.png)

# Severity 4 : XML (Extensible Markp Language) External Entity (XXE)

An XML External Entity (XXE) attack is a vulnerability that abuses features of XML parsers/data. It often allows an attacker to interact with any backend or external systems that the application itself can access and can allow the attacker to read the file on that system. They can also cause Denial of Service (DoS) attack or could use XXE to perform Server-Side Request Forgery (SSRF) inducing the web application to make requests to other applications. XXE may even enable port scanning and lead to remote code execution.

![image](https://user-images.githubusercontent.com/112873207/221895351-3f0f8890-7fee-4353-ae6c-31bb82a56345.png)

## Now what is XML ?

XML (eXtensible Markup Language) is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable. It is a markup language used for storing and transporting data. 

## Why do we use it ? 

1. XML is platform-independent and programming language independent, thus it can be used on any system and supports the technology change when that happens.

2. The data stored and transported using XML can be changed at any point in time without affecting the data presentation.

3. XML allows validation using DTD (Document Type Definition) and Schema. This validation ensures that the XML document is free from any syntax error.

4. XML simplifies data sharing between various systems because of its platform-independent nature. XML data doesn’t require any conversion when transferred between different systems.

Every XML document mostly starts with what is known as XML Prolog ; `<?xml version="1.0" encoding="UTF-8"?>`

This line is not compulsory to use but it is considered a `good practice` to put that line in all your XML documents.

![image](https://user-images.githubusercontent.com/112873207/221897592-35c16c56-3078-463c-bc8b-55480e372c14.png)

In the above example the `<mail>` is the ROOT element of that document and `<to>`, `<from>`, `<subject>`, `<text>` are the children elements. If the XML document doesn't have any root element then it would be considered **wrong or invalid** XML doc.
  
![image](https://user-images.githubusercontent.com/112873207/221898286-4723a447-1118-4d72-8790-2f18ce839643.png)

![image](https://user-images.githubusercontent.com/112873207/221898667-fcb64a30-b6c7-487a-99ca-b1d26572c3e2.png)

# Severity 5 : Broken Access Control 

![image](https://user-images.githubusercontent.com/112873207/223431549-11ae28df-29f4-446c-9418-66369412832c.png)

![image](https://user-images.githubusercontent.com/112873207/223431421-74c5e62d-9944-4bbd-8ac8-ac747c2f0071.png)

# Severity 6 : Security Misconfiguration

Security misconfigurations include:

- Poorly configured permissions on cloud services, like S3 buckets
- Having unnecessary features enabled, like services, pages, accounts or privileges
- Default accounts with unchanged passwords
- Error messages that are overly detailed and allow an attacker to find out more about the system
- Not using HTTP security headers, or revealing too much detail in the Server: HTTP header
- This vulnerability can often lead to more vulnerabilities, such as default credentials giving you access to sensitive data, XXE or command injection on admin pages.

## Default Password 

Specifically, this VM focusses on default passwords. These are a specific example of a security misconfiguration. You could, and should, change any default passwords but people often don't.

It's particularly common in embedded and Internet of Things devices, and much of the time the owners don't change these passwords.

It's easy to imagine the risk of default credentials from an attacker's point of view. Being able to gain access to admin dashboards, services designed for system administrators or manufacturers, or even network infrastructure could be incredibly useful in attacking a business. From data exposure to easy RCE, the effects of default credentials can be severe.

# Severity 7 : XSS (Cross Site Scripting)

XSS is a security vulnerability typically found in web applications. It’s a type of injection which can allow an attacker to execute malicious scripts and have it execute on a victim’s machine.

A web application is vulnerable to XSS if it uses unsanitized user input. XSS is possible in Javascript, VBScript, Flash and CSS. There are three main types of cross-site scripting:

1) Stored XSS - the most dangerous type of XSS. This is where a malicious string originates from the website’s database. This often happens when a website allows user input that is not sanitised (remove the "bad parts" of a users input) when inserted into the database.

2) Reflected XSS - the malicious payload is part of the victims request to the website. The website includes this payload in response back to the user. To summarise, an attacker needs to trick a victim into clicking a URL to execute their malicious payload.

3) DOM-Based XSS - DOM stands for Document Object Model and is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style and content. A web page is a document and this document can be either displayed in the browser window or as the HTML source.

## XSS Payloads

![image](https://user-images.githubusercontent.com/112873207/225035592-093195d9-09d8-4472-9c4d-b27ec8883e9d.png)

XSS-Payloads.com (http://www.xss-payloads.com/) is a website that has XSS related Payloads, Tools, Documentation and more. You can download XSS payloads that take snapshots from a webcam or even get a more capable port and network scanner.

# Severity 8 : Insecure Deserialization

"Insecure Deserialization is a vulnerability which occurs when untrusted data is used to abuse the logic of an application" (Acunetix., 2017)

Simply, insecure deserialization is replacing data processed by an application with malicious code; allowing anything from DoS (Denial of Service) to RCE (Remote Code Execution) that the attacker can use to gain a foothold in a pentesting scenario.

Specifically, this malicious code leverages the legitimate serialization and deserialization process used by web applications.

**OWASP rank this vulnerability as 8 out of 10 because of the following reasons:**

![image](https://user-images.githubusercontent.com/112873207/225045637-ba835616-d030-4304-b048-519b4654126c.png)

![image](https://user-images.githubusercontent.com/112873207/225048973-24dfc799-e14b-41e1-9618-cf6406a4ee4d.png)

## Objects 

![image](https://user-images.githubusercontent.com/112873207/225049127-0c7b232c-1c57-43de-bd30-af2f96b0ddbd.png)

## Deserializations

*Learning is best done through analogies*

A Tourist approaches you in the street asking for directions. They're looking for a local landmark and got lost. Unfortunately, English isn't their strong point and nor do you speak their dialect either. What do you do? You draw a map of the route to the landmark because pictures cross language barriers, they were able to find the landmark. Nice! You've just serialised some information, where the tourist then deserialised it to find the landmark.µ

*Continued*

Serialisation is the process of converting objects used in programming into simpler, compatible formatting for transmitting between systems or networks for further processing or storage.

Alternatively, deserialisation is the reverse of this; converting serialised information into their complex form - an object that the application will understand.

*What does this means ?*

![image](https://user-images.githubusercontent.com/112873207/225050378-5cfbe6db-37bb-40d5-b616-196f07da559e.png)

*How can we leverage this?*

Simply, insecure deserialization occurs when data from an untrusted party (I.e. a hacker) gets executed because there is no filtering or input validation; the system assumes that the data is trustworthy and will execute it no holds barred.









