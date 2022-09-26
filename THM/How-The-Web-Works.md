# DNS in detail

## What is DNS ?

NS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers.

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
