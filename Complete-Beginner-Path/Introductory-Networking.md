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

# Networking Tools 

## Ping command

Command used to ping a server. To see every switch refer to the manual pages.

## Traceroute

The logical follow-up to the ping command is 'traceroute'. Traceroute can be used to map the path your request takes as it heads to the target machine.

The basic syntax for traceroute on Linux is this: 

`traceroute <destination>`

*Lateral Thinking* Which layer of the TCP/IP model will traceroute run on by default (Windows)? Internet (Layer 2)

## Whois

Whois essentially allows you to query who a domain name is registered to. In Europe personal details are redacted; however, elsewhere you can potentially get a great deal of information from a whois search.

## Dig

You make a request to a website. The first thing that your computer does is check its local cache to see if it's already got an IP address stored for the website; if it does, great. If not, it goes to the next stage of the process.

Assuming the address hasn't already been found, your computer will then send a request to what's known as a recursive DNS server.

If the website you've requested isn't stored in the cache, the recursive server will pass the request on to a root name server.

The root name servers essentially keep track of the DNS servers in the next level down, choosing an appropriate one to redirect your request to. These lower level servers are called Top-Level Domain servers.

As with root name servers, TLD servers keep track of the next level down: Authoritative name servers. When a TLD server receives your request for information, the server passes it down to an appropriate Authoritative name server.

Authoritative name servers are used to store DNS records for domains directly. In other words, every domain in the world will have its DNS records stored on an Authoritative name server somewhere or another; they are the source of the information. When your request reaches the authoritative name server for the domain you're querying, it will send the relevant information back to you, allowing your computer to connect to the IP address behind the domain you requested.

Dig allows us to manually query recursive DNS servers of our choice for information about domains: 

`dig <domain> @<dns-server-ip>`




