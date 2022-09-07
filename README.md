# Notes-THM

VULNERABILITY SEARCHING
 
A quick remembrering of the session : 

CVE.mitre is a good site to search for CVE codes. NVD is also a good place to look at.

Searching via Linux : searchsploit <name of program>

MANUAL PAGES

Man is a feature in Linux for searching tools command. It is used like this : man <name of tool> and will directly show the manual pages on the terminal.
The Man command also describes how to use the switches (like -V (what does it do? etc..)).

UBUNTU 

echo <text> output the text we write between "".

whoami </> output the user id

Navigating in the file system :

-ls <see using man ls> lists infos about the files. It is possible to list the content of a directory /w going into it by doing -ls <full name of the directory>.
-cd <i.e. Pictures> change directory. Once in the desired directory type -ls to show everything in that directory.
-cat concatenate/output files/files content. By writing -cat in a file that contains some .txt or pictures, it will output it. Shortcut : cat /home/Ubuntu/Documents/.txt
-pwd prints the full name of the actual working directory.

-find *.txt -> searchs for every .txt in the current directory. i.e. -find passwords.txt.

-grep <"IP adress"> <name of what he searched> i.e. -grep "123.5.4.5.5" access.log or -grep -r THM (-r is an option that allows to search in the sub-directories.

SHELL OPERATORS

& : allows you to run a command in the background 
&& : allows you to combine commands in one line of code. i.e. command1 && command2 (command2 will only run if command1 was successful).
">" : redirector. i.e. echo hey > Welcome(file name). If then I do : cat Welcome -> it will show me "Hey". If a file named Welcome already existed, it would have been overwritten.
">>" : same as > but doesn't replace the output, it copies it. Let's say that in the file "Welcome" the word "hey" is in. Now if I do echo >> Welcome the Welcome file now has in it : hey + hello (displayed under hey). So > replaces a file content and >> adds content to a file.





