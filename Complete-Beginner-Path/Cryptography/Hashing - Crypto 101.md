Room ![image](https://user-images.githubusercontent.com/112873207/225943219-d814dae2-85d7-4604-9e2a-d56e9fc248c7.png)

# Hash Function

## Key Terms

Before we start, we need to get some jargon out of the way.
Read these, and take in as much as you can. We'll expand on some of them later in the room.

`Plaintext` - Data before encryption or hashing, often text but not always as it could be a photograph or other file instead.

`Encoding` - This is NOT a form of encryption, just a form of data representation like base64 or hexadecimal. Immediately reversible.

`Hash` - A hash is the output of a hash function. Hashing can also be used as a verb, "to hash", meaning to produce the hash value of some data.

`Brute force` - Attacking cryptography by trying every different password or every different key

`Cryptanalysis` - Attacking cryptography by finding a weakness in the underlying maths

## What is a hash function ? 

Hash functions are quite different from encryption. There is no key, and it’s meant to be impossible (or very very difficult) to go from the output back to the input.

A hash function takes some input data of any size, and creates a summary or "digest" of that data. The output is a fixed size. It’s hard to predict what the output will be for any input and vice versa. Good hashing algorithms will be (relatively) fast to compute, and slow to reverse (Go from output and determine input). Any small change in the input data (even a single bit) should cause a large change in the output.

The output of a hash function is normally raw bytes, which are then encoded. Common encodings for this are base 64 or hexadecimal. Decoding these won’t give you anything useful.

## Why should I care ? 

Hashing is used very often in cyber security. When you logged into TryHackMe, that used hashing to verify your password. When you logged into your computer, that also used hashing to verify your password. You interact indirectly with hashing more than you would think, mostly in the context of passwords.

## What's a hash collision ?

![image](https://user-images.githubusercontent.com/112873207/228499519-277600c5-dd74-4f58-a6af-909bc9788f44.png)

# Uses for hashing

## What can we do with hashing ?

Hashing is used for 2 main purposes in Cyber Security. To verify integrity of data (More on that later), or for verifying passwords.

## Hashing for password verification

![image](https://user-images.githubusercontent.com/112873207/228502482-3e41112d-2cc0-4329-99af-d04ebc347023.png)

![image](https://user-images.githubusercontent.com/112873207/228502554-7f830e4d-ca6b-4199-832a-9274a55707da.png)

![image](https://user-images.githubusercontent.com/112873207/228502618-bffb63c7-17fb-4308-b9a6-65ff2d562856.png)

## Protecting against rainbow tables

![image](https://user-images.githubusercontent.com/112873207/228502734-f97ff0be-62f4-4634-b40f-5ee1a2984ee5.png)

# Recognising password hashes

![image](https://user-images.githubusercontent.com/112873207/228504016-020e6968-374f-49bf-9ea3-3bf95c8d078a.png)

![image](https://user-images.githubusercontent.com/112873207/228504100-69669edb-727e-45a5-9732-4dfef45f2ef7.png)

![image](https://user-images.githubusercontent.com/112873207/228504213-7d0545ce-dd01-4bbc-9d8d-d9d5f2c32a0a.png)

# Password cracking

![image](https://user-images.githubusercontent.com/112873207/228505847-d51cc78d-2577-4fd0-92ae-51053622fd1e.png)

## Why crack on GPU's ?

![image](https://user-images.githubusercontent.com/112873207/228506025-880feef2-2404-4b3c-b7d8-6bf0d801a2e9.png)

## Cracking on VM's ?

![image](https://user-images.githubusercontent.com/112873207/228506556-2c16c07c-f476-40d7-917e-dbaa0278396d.png)

# Hashing for integrity checking

## Integrity checking

Hashing can be used to check that files haven't been changed. If you put the same data in, you always get the same data out. If even a single bit changes, the hash will change a lot. 

This means you can use it to check that files haven't been modified or to make sure that they have downloaded correctly. 

You can also use hashing to find duplicate files, if two pictures have the same hash then they are the same picture.

## HMAC's

HMAC is a method of using a cryptographic hashing function to verify the authenticity and integrity of data. 

The TryHackMe VPN uses HMAC-SHA512 for message authentication, which you can see in the terminal output. 

A HMAC can be used to ensure that the person who created the HMAC is who they say they are (authenticity), and that the message hasn’t been modified or corrupted (integrity). 

They use a secret key, and a hashing algorithm in order to produce a hash.





