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

- Brute force attacks: If a web application uses usernames and passwords, an attacker is able to launch brute force attacks that allow them to guess the username and passwords using multiple authentication attempts. 
- Use of weak credentials: web applications should set strong password policies. If applications allow users to set passwords such as ‘password1’ or common passwords, then an attacker is able to easily guess them and access user accounts. They can do this without brute forcing and without multiple attempts.
- Weak Session Cookies: Session cookies are how the server keeps track of users. If session cookies contain predictable values, an attacker can set their own session cookies and access users’ accounts. 






