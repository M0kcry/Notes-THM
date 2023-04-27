Room  ![image](https://user-images.githubusercontent.com/112873207/231710600-d5d3f350-e4c2-4a8a-8c51-ca02089c86bf.png)

# John Who ?

John the Ripper is one of the most well known, well-loved and versatile hash cracking tools out there.

It combines a fast cracking speed, with an extraordinary range of compatible hash types. 

This room will assume no previous knowledge, so we must first cover some basic terms and concepts before we move into practical hash cracking.

## What are hashes ? 

A hash is a way of taking a piece of data of any length and  representing it in another form that is a fixed length. This masks the original value of the data. This is done by running the original data through a hashing algorithm. There are many popular hashing algorithms, such as MD4,MD5, SHA1 and NTLM. Lets try and show this with an example:

If we take "polo", a string of 4 characters- and run it through an MD5 hashing algorithm, we end up with an output of: b53759f3ce692de7aff1b5779d3964da a standard 32 character MD5 hash.

Likewise, if we take "polomints", a string of 9 characters- and run it through the same MD5 hashing algorithm, we end up with an output of: 584b6e4f4586e136bc280f27f9c64f3b another standard 32 character MD5 hash.

## What makes hashes secure ?

Hashing algorithms are designed so that they only operate one way. This means that a calculated hash cannot be reversed using just the output given. This ties back to a fundamental mathematical problem known as the P vs NP relationship .

While this is an extremely interesting mathematical concept that proves fundamental to computing and cryptography I am in no way qualified to try and explain it in detail here; but abstractly it means that the algorithm to hash the value will be "NP" and can therefore be calculated reasonably. However an un-hashing algorithm would be "P" and intractable to solve- meaning that it cannot be computed in a reasonable time using standard computers.

## Where John comes in ...

Even though the algorithm itself is not feasibly reversible. That doesn't mean that cracking the hashes is impossible. If you have the hashed version of a password, for example- and you know the hashing algorithm- you can use that hashing algorithm to hash a large number of words, called a dictionary. 

You can then compare these hashes to the one you're trying to crack, to see if any of them match. If they do, you now know what word corresponds to that hash- you've cracked it!

This process is called a dictionary attack and John the Ripper, or John as it's commonly shortened to, is a tool to allow you to conduct fast brute force attacks on a large array of different hash types.

# Setting up John the Ripper (Kali/Parrot)

If you're using Parrot OS, Kali Linux or TryHackMe's own AttackBox- you should already have Jumbo John installed. You can double check this by typing john into the terminal.

You should be met with a usage guide for john, with the first line reading: "John the Ripper 1.9.0-jumbo-1" or similar with a different version number. 

If not, you can use `sudo apt install john` to install it.

# Wordlists

As we explained in the first task, in order to dictionary attack hashes, you need a list of words that you can hash and compare, unsurprisingly this is called a wordlist. 

There are many different wordlists out there, a good collection to use can be found in the **SecLists** repository. There are a few places you can look for wordlists on your attacking system of choice, we will quickly run through where you can find them.

Wordlists can be found here : `/usr/share/wordlists` directory.

If not, use this : `sudo apt get seclists` to download the seclists repository.

If you are not using any of the above distributions, you can get the rockyou.txt wordlist from the SecLists repository under the `/Passwords/Leaked-Databases` subsection. You may need to extract it from `.tar.gz` format, using `tar xvzf rockyou.txt.tar.gz`. 

# Cracking basic hashes

## John basic syntax

The basic syntax of John the Ripper commands is as follows. We will cover the specific options and modifiers used as we use them.

`john [options] [path to file]`

`john` - Invokes the John the Ripper program

`[path to file]` - The file containing the hash you're trying to crack, if it's in the same directory you won't need to name a path, just the file.

## Automatic cracking

John has built-in features to detect what type of hash it's being given, and to select appropriate rules and formats to crack it for you, this isn't always the best idea as it can be unreliable- but if you can't identify what hash type you're working with and just want to try cracking it, it can be a good option! 

To do this we use the following syntax:

`john --wordlist=[path to wordlist]` [path to file]

`--wordlist=` - Specifies using wordlist mode, reading from the file that you supply in the following path...

`[path to wordlist]` - The path to the wordlist you're using, as described in the previous task.

**Example Usage** :

`john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

## Identifying hashes

Sometimes John won't play nicely with automatically recognising and loading hashes, that's okay! We're able to use other tools to identify the hash, and then set john to use a specific format. 

There are multiple ways to do this, such as using an online hash identifier like this one : https://hashes.com/en/tools/hash_identifier. 

I like to use a tool called hash-identifier, a Python tool that is super easy to use and will tell you what different types of hashes the one you enter is likely to be, giving you more options if the first one fails.

To use hash-identifier, you can just pull the python file from gitlab using: `wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py`.

Then simply launch it with `python3 hash-id.py` and then enter the hash you're trying to identify- and it will give you possible formats!

## Format-Specific Cracking

Once you have identified the hash that you're dealing with, you can tell john to use it while cracking the provided hash using the following syntax:

`john --format=[format] --wordlist=[path to wordlist] [path to file]`

`--format=` - This is the flag to tell John that you're giving it a hash of a specific format, and to use the following format to crack it

`[format]` - The format that the hash is in

**Example usage** : `john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

**NB** :  When you are telling john to use formats, if you're dealing with a standard hash type, e.g. md5 as in the example above, you have to prefix it with `raw-` to tell john you're just dealing with a standard hash type, though this doesn't always apply. 

To check if you need to add the prefix or not, you can list all of John's formats using john `--list=formats` and either check manually, or grep for your hash type using something like `john --list=formats | grep -iF "md5"`.

# Cracking Windows Authentication Hashes

## Cracking windows hashes

Now that we understand the basic syntax and usage of John the Ripper- lets move on to cracking something a little bit more difficult, something that you may even want to attempt if you're on a real Penetration Test or Red Team engagement. 

Authentication hashes are the hashed versions of passwords that are stored by operating systems, it is sometimes possible to crack them using the brute-force methods that we're using. 

To get your hands on these hashes, you must often already be a privileged user- so we will explain some of the hashes that we plan on cracking as we attempt them.

## NTHash / NTLM

NThash is the hash format that modern Windows Operating System machines will store user and service passwords in. It's also commonly referred to as "NTLM" which references the previous version of Windows format for hashing passwords known as "LM", thus "NT/LM".

A little bit of history, the NT designation for Windows products originally meant "New Technology", and was used- starting with Windows NT, to denote products that were not built up from the MS-DOS Operating System. Eventually, the "NT" line became the standard Operating System type to be released by Microsoft and the name was dropped, but it still lives on in the names of some Microsoft technologies. 

You can acquire NTHash/NTLM hashes by dumping the SAM database on a Windows machine, by using a tool like Mimikatz or from the Active Directory database: NTDS.dit. You may not have to crack the hash to continue privilege escalation- as you can often conduct a "pass the hash" attack instead, but sometimes hash cracking is a viable option if there is a weak password policy.

# Cracking /etc/shadow hashes

## Cracking hashes from /etc/shadow

The /etc/shadow file is the file on Linux machines where password hashes are stored. 

It also stores other information, such as the date of last password change and password expiration information. 

It contains one entry per line for each user or user account of the system. 

This file is usually only accessible by the root user- so in order to get your hands on the hashes you must have sufficient privileges, but if you do- there is a chance that you will be able to crack some of the hashes.

## Unshadowing

John can be very particular about the formats it needs data in to be able to work with it, for this reason- in order to crack /etc/shadow passwords, you must combine it with the /etc/passwd file in order for John to understand the data it's being given. To do this, we use a tool built into the John suite of tools called unshadow

The basic syntax of unshadow is as follows:

`unshadow [path to passwd] [path to shadow]`

`unshadow` - Invokes the unshadow tool

`[path to passwd]` - The file that contains the copy of the /etc/passwd file you've taken from the target machine

`[path to shadow]` - The file that contains the copy of the /etc/shadow file you've taken from the target machine

**Example Usage** :

`unshadow local_passwd local_shadow > unshadowed.txt`

## Cracking 

Once the unshadowing step is done, we're then able to feed the output from unshadow, in our example use case called "unshadowed.txt" directly into John. 

We should not need to specify a mode here as we have made the input specifically for John, however in some cases you will need to specify the format as we have done previously using: `--format=sha512crypt`

`john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt`

# Single crack mode

So far we've been using John's wordlist mode to deal with brute forcing simple, and not so simple hashes. But John also has another mode, called Single Crack mode. 

In this mode, John uses only the information provided in the username, to try and work out possible passwords heuristically, by slightly changing the letters and numbers contained within the username.

## Word mangling

The best way to show what Single Crack mode is,  and what word mangling is, is to actually go through an example:

If we take the username: Markus

Some possible passwords could be:

- Markus1, Markus2, Markus3 (etc.)
- MArkus, MARkus, MARKus (etc.)
- Markus!, Markus$, Markus* (etc.)
- 
This technique is called word mangling. John is building it's own dictionary based on the information that it has been fed and uses a set of rules called "mangling rules" which define how it can mutate the word it started with to generate a wordlist based off of relevant factors for the target you're trying to crack. 

This is exploiting how poor passwords can be based off of information about the username, or the service they're logging into.

## GECOS

John's implementation of word mangling also features compatibility with the Gecos fields of the UNIX operating system, and other UNIX-like operating systems such as Linux. So what are Gecos? Remember in the last task where we were looking at the entries of both /etc/shadow and /etc/passwd? Well if you look closely You can see that each field is seperated by a colon ":". 

Each one of the fields that these records are split into are called Gecos fields. John can take information stored in those records, such as full name and home directory name to add in to the wordlist it generates when cracking /etc/shadow hashes with single crack mode.

## Using single crack mode

To use single crack mode, we use roughly the same syntax that we've used to so far, for example if we wanted to crack the password of the user named "Mike", using single mode, we'd use:

`john --single --format=[format] [path to file]`

`--single` - This flag lets john know you want to use the single hash cracking mode.

**Example Usage** :

`john --single --format=raw-sha256 hashes.txt`

**A Note on File Formats in Single Crack Mode** :

If you're cracking hashes in single crack mode, you need to change the file format that you're feeding john for it to understand what data to create a wordlist from. You do this by prepending the hash with the username that the hash belongs to, so according to the above example- we would change the file hashes.txt

**From** :

1efee03cdcb96d90ad48ccc7b8666033

**To**

mike:1efee03cdcb96d90ad48ccc7b8666033

# Custom Rules


As we journeyed through our exploration of what John can do in Single Crack Mode- you may have some ideas about what some good mangling patterns would be, or what patterns your passwords often use- that could be replicated with a certain mangling pattern.

The good news is you can define your own sets of rules, which John will use to dynamically create passwords. This is especially useful when you know more information about the password structure of whatever your target is. 

## Common custom rules

Many organisations will require a certain level of password complexity to try and combat dictionary attacks, meaning that if you create an account somewhere, go to create a password and enter: 

polopassword

You may receive a prompt telling you that passwords have to contain at least one of the following:

    - Capital letter
    - Number
    - Symbol

This is good! However, we can exploit the fact that most users will be predictable in the location of these symbols. For the above criteria, many users will use something like the following:

Polopassword1!

A password with the capital letter first, and a number followed by a symbol at the end. This pattern of the familiar password, appended and prepended by modifiers (such as the capital letter or symbols) is a memorable pattern that people will use, and reuse when they create passwords. 

This pattern can let us exploit password complexity predictability.

Now this does meet the password complexity requirements, however as an attacker we can exploit the fact we know the likely position of these added elements to create dynamic passwords from our wordlists.

## How to create custom rules

Custom rules are defined in the `john.conf`  file, usually located in `/etc/john/john.conf` if you have installed John using a package manager or built from source with make and in `/opt/john/john.conf` on the TryHackMe Attackbox.









