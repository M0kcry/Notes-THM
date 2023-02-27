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





