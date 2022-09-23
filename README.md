# Notes-THM

## VULNERABILITY SEARCHING
 
A quick remembrering of the session : 

CVE.mitre is a good site to search for CVE codes. NVD is also a good place to look at.

Searching via Linux : searchsploit <name of program>

## MANUAL PAGES

 Man is a feature in Linux for searching tools command. It is used like this : man [name of tool] and will directly show the manual pages on the terminal.
The Man command also describes how to use the switches (like -V (what does it do? etc..)).

## UBUNTU/LINUX COMMANDS

-touch [name of the file]. Creates a file.
 
-mkdir [name of the directory]. Creates a directory.
 
-ls <see using man ls> lists infos about the files. It is possible to list the content of a directory /w going into it by doing -ls [full name of the directory].
 
-cd [i.e. Pictures] change directory. Once in the desired directory type -ls to show everything in that directory.
 
-cat [File,etc...] concatenate/output files or files content. By writing -cat in a file that contains some .txt or pictures, it will output it. Shortcut : cat /home/Ubuntu/Documents/*.txt
 
-rm [name of the file]. If you want to remove a directory the -R switch.
 
-scp [SOURCE][DESTINATION]. This command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption. i.e. scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt would be the command to transfer from our pc to a remote one. This command can be reversed. It would be like : scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt (we copy a file from a remote pc to ours).
 
-cp [name of the file(notf) you want to copy] [name of the copied file]
 
-mv [notf you want to move] [where you want to move it]. Can also be used to rename a folder/file. i.e. move note2 note3. 
 
**Similarly to using cat, we can provide full file paths, i.e. directory1/directory2/note for all of these commands above.**

-wget [URL or Breadcrumb trail]. Downloads a file from a specified URL.
 
-curl [URL]. curl is a tool for transferring data from or to a server.
 
-echo [text]. outputs the text we write between after the command.

-whoami [/]. outputs the user id.
 
-pwd prints the full name of the actual working directory.

-find *.txt -> searchs for every .txt in the current directory. i.e. -find passwords.txt.

-grep ["IP adress"] [name of what he searched] i.e. -grep "123.5.4.5.5" access.log or -grep -r THM (-r is an option that allows to search in the sub-directories.)
 
-file [notf] determines the extension of this file, whether it's a .txt or else.

-crontab -e is a command to edit the crontab file (you can do it with Nano i.e.). crontab is simply a special file with formatting that is recognised by the cron process to execute each line step-by-step at the boot of the computer. Crontabs require 6 specific values -> min hour dayofthemonth(dom) mon(th) DoW cmd(command that will be executed).

 

## SHELL OPERATORS

& : allows you to run a command in the background 
 
&& : allows you to combine commands in one line of code. i.e. command1 && command2 (command2 will only run if command1 was successful).
 
">" : redirector. i.e. echo hey > Welcome(file name). If then I do : cat Welcome -> it will show me "Hey". If a file named Welcome already existed, it would have been overwritten.
 
">>" : same as > but doesn't replace the output, it copies it. Let's say that in the file "Welcome" the word "hey" is in. Now if I do echo >> Welcome the Welcome file now has in it : hey + hello (displayed under hey).

So > replaces a file content and >> adds content to a file.

## PACKAGE MANAGEMENT

-add-apt-repository is a command that adds a repository to apt

To start downloading programs (like Sublime Text 3) we first need to get the GPG key (security key provided by the creators of the program).

So i.e. : wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add - 
The last part with sudo apt-key is a line to tell the server it can trust this key.

Then let's create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information. (touch Sublime-text.list i.e.)

After we have added this entry, we need to update apt to recognise this new entry -- this is done using the apt update command

Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using apt install sublime-text

## NETWORKING

### NETWORKING TOPOLOGIES
 
Star topology : *, this topology is at a higher cost than the others but have advantages such as : very scalable in nature (you can add devices easily), ..
And disadvantages : If the centralised hardware that connects devices fails, these devices will no longer be able to send or receive data. Thankfully, these centralised hardware devices are often robust.
 

