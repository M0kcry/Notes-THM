Room ![image](https://user-images.githubusercontent.com/112873207/228523075-d7527468-9751-478c-a9a7-f52f45e80fb9.png)

![image](https://user-images.githubusercontent.com/112873207/228523141-7fbce85d-32f4-4223-9305-478c44522d6d.png)

# Key terms

Here's a list of terms that are going to be used in this room : 

![image](https://user-images.githubusercontent.com/112873207/228523748-74d8a752-65d9-4f3b-ac6c-d20f132d4ccf.png)

# Why is encryption important ?

![image](https://user-images.githubusercontent.com/112873207/228527539-d5603f20-36e9-4d5c-abad-388777434301.png)

# Crucial crypto maths 

Explains here the modulo operation. 

# Types of encryption

`Symmetric encryption` uses the same key to encrypt and decrypt the data. Examples of Symmetric encryption are DES (Broken) and AES. These algorithms tend to be faster than asymmetric cryptography, and use smaller keys (128 or 256 bit keys are common for AES, DES keys are 56 bits long).

`Asymmetric encryption` uses a pair of keys, one to encrypt and the other in the pair to decrypt. Examples are RSA and Elliptic Curve Cryptography. Normally these keys are referred to as a public key and a private key. Data encrypted with the private key can be decrypted with the public key, and vice versa. Your private key needs to be kept private, hence the name. Asymmetric encryption tends to be slower and uses larger keys, for example RSA typically uses 2048 to 4096 bit keys.

For a better understanding :  https://www.youtube.com/watch?v=w0QbnxKRD0w

# RSA - Rivest Shamir Adleman

## The maths side 

RSA is based on the mathematically difficult problem of working out the factors of a large number. It’s very quick to multiply two prime numbers together, say 17x23 = 391, but it’s quite difficult to work out what two prime numbers multiply together to make 14351 (113x127 for reference).

## The attacking side

The maths behind RSA seems to come up relatively often in CTFs, normally requiring you to calculate variables or break some encryption based on them. The wikipedia page for RSA seems complicated at first, but will give you almost all of the information you need in order to complete challenges.

There are some excellent tools for defeating RSA challenges in CTFs, and my personal favorite is https://github.com/Ganapati/RsaCtfTool

The key variables that you need to know about for RSA in CTFs are p, q, m, n, e, d, and c.

- “p” and “q” are large prime numbers, “n” is the product of p and q.

- The public key is n and e, the private key is n and d.

- “m” is used to represent the message (in plaintext) and “c” represents the ciphertext (encrypted text).

## CTFs involving RSA

Crypto CTF challenges often present you with a set of these values, and you need to break the encryption and decrypt a message to retrieve the flag.

There’s a lot more maths to RSA, and it gets quite complicated fairly quickly. If you want to learn the maths behind it, I recommend reading MuirlandOracle’s blog post here: https://muirlandoracle.co.uk/2020/01/29/rsa-encryption/.

# Establishing keys using asymmetric cryptography

A very common use of asymmetric cryptography is exchanging keys for symmetric encryption.

Asymmetric encryption tends to be slower, so for things like HTTPS symmetric encryption is better.

But the question is, how do you agree a key with the server without transmitting the key for people snooping to see?

## Metaphor Time

Imagine you have a secret code, and instructions for how to use the secret code. If you want to send your friend the instructions without anyone else being able to read it, what you could do is ask your friend for a lock.

Only they have the key for this lock, and we’ll assume you have an indestructible box that you can lock with it.

If you send the instructions in a locked box to your friend, they can unlock it once it reaches them and read the instructions.

After that, you can communicate in the secret code without risk of people snooping.

In this metaphor, the secret code represents a symmetric encryption key, the lock represents the server’s public key, and the key represents the server’s private key.

You’ve only used asymmetric cryptography once, so it’s fast, and you can now communicate privately with symmetric encryption.

## The real world

In reality, you need a little more cryptography to verify the person you’re talking to is who they say they are, which is done using digital signatures and certificates. 

You can find a lot more detail on how HTTPS (one example where you need to exchange keys) really works from this excellent blog post. https://robertheaton.com/2014/03/27/how-does-https-actually-work/

# Digital signatures and certificates

## What's a digital signature ? 

Digital signatures are a way to prove the authenticity of files, to prove who created or modified them. Using asymmetric cryptography, you produce a signature with your private key and it can be verified using your public key. 

As only you should have access to your private key, this proves you signed the file. Digital signatures and physical signatures have the same value in the UK, legally.

The simplest form of digital signature would be encrypting the document with your private key, and then if someone wanted to verify this signature they would decrypt it with your public key and check if the files match.

## Certificates - Prove who you are 

Certificates are also a key use of public key cryptography, linked to digital signatures. A common place where they’re used is for HTTPS. How does your web browser know that the server you’re talking to is the real tryhackme.com?

The answer is certificates. The web server has a certificate that says it is the real tryhackme.com. The certificates have a chain of trust, starting with a root CA (certificate authority). 

Root CAs are automatically trusted by your device, OS, or browser from install. 

Certs below that are trusted because the Root CAs say they trust that organisation. 

Certificates below that are trusted because the organisation is trusted by the Root CA and so on. There are long chains of trust. 

Again, this blog post explains this much better than I can. https://robertheaton.com/2014/03/27/how-does-https-actually-work/

You can get your own HTTPS certificates for domains you own using Let’s Encrypt for free. If you run a website, it’s worth setting it up.

# SSH Authentication

## Encryption and SSH authentication

By default, SSH is authenticated using usernames and passwords in the same way that you would log in to the physical machine.

At some point, you’re almost certain to hit a machine that has SSH configured with key authentication instead. 

This uses public and private keys to prove that the client is a valid and authorised user on the server. 

By default, SSH keys are RSA keys. You can choose which algorithm to generate, and/or add a passphrase to encrypt the SSH key. 

`ssh-keygen` is the program used to generate pairs of keys most of the time.













