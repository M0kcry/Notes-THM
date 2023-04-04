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


