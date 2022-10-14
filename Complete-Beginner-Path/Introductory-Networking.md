# The OSI Model : an overview

A mnemonic helper for the 7 layers of the OSI model : All People Seem To Need Data Processing.

![image](https://user-images.githubusercontent.com/112873207/195881276-395e40e4-3edd-4033-ac56-d175b49334a1.png)

# Encapsuation

![image](https://user-images.githubusercontent.com/112873207/195910830-01ffa545-6047-4e06-98e5-642ad5157112.png)

Headers (and trailer at layer 2) are added for each layer.
The data link layer also adds a piece on at the end of the transmission, which is used to verify that the data has not been corrupted on transmission; this also has the added bonus of increased security

# TCP/IP model

![image](https://user-images.githubusercontent.com/112873207/195913341-4ecabbaa-5b47-4e05-95a6-8f44c7c2c2b6.png)

***Note**: Some recent sources split the TCP/IP model into five layers -- breaking the Network Interface layer into Data Link and Physical layers (as with the OSI model). This is accepted and well-known; however, it is not officially defined (unlike the original four layers which are defined in RFC1122). It's up to you which version you use -- both are generally considered valid.*

You would be justified in asking why we bother with the OSI model if it's not actually used for anything in the real-world. The answer to that question is quite simply that the OSI model (due to being less condensed and more rigid than the TCP/IP model) tends to be easier for learning the initial theory of networking.

![image](https://user-images.githubusercontent.com/112873207/195913506-d778589a-fc74-4a2f-a80d-962bafcafbf8.png)

The processes of encapsulation and de-encapsulation work in exactly the same way with the TCP/IP model as they do with the OSI model. At each layer of the TCP/IP model a header is added during encapsulation, and removed during de-encapsulation.


