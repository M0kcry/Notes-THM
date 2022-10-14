# Notes-THM

## VULNERABILITY SEARCHING

[CVE.mitre](https://cve.mitre.org/) is a good site to search for `CVE` codes. [NVD](https://nvd.nist.gov/) is also a good place to look at.

Searching via Linux : 
```shell
searchsploit <name of program>
```
## MANUAL PAGES

__Man__ is a feature in Linux for searching tools command. It is used as follow to output the manual pages on the terminal : 
```shell
man [name of tool] 
```
The `Man` command also describes how to use the switches (like -V (what does it do? etc..)).

## LINUX COMMANDS
```shell
# Creates a file.
touch [name of the file]

# Creates a directory.
mkdir [name of the directory]

# <see using man ls> lists infos about the files. 
# It is possible to list the content of a directory /w going into it by doing -ls [full name of the directory].
ls
 
# Changes directory. Once in the desired directory type -ls to show everything in that directory.
cd /home/Mockry/Pictures
cd .. # changes to the parent directory

# Prints the full name of the actual working directory
pwd
 
# Concatenates/outputs files or files content. By writing -cat in a file that contains some .txt or pictures, it will output it. 
cat /home/Ubuntu/test.txt
cat /home/Ubuntu/Documents/*.txt # can display more than 1 file by using the wildcard
 
# Removes a file. Can also remove a directory by using the -R switch.
rm test.txt
rm -R /home/Ubuntu/Trash/

# Transfers files between two computers using the SSH protocol
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt # transfer from our pc to a remote one
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt # copy a file from a remote pc to ours

# Copies files. The first path or filename is the file to copy, and the second path is the destination
cp original.txt /home/Ubuntu/Backup/backup.txt
 
# Move a file to another location, often used for rename operation. Also works for folders/directories
mv note2 note3 
 
**Similarly to using cat, we can provide full file paths, i.e. directory1/directory2/note for all of these commands above.**

# Downloads files from a URL
wget https://ubuntu.org/Ubuntu_Server.iso
wget https://ubuntu.org/Ubuntu_Server.iso -O /home/Ubuntu/Server.iso # -O specifies the output path for the downloaded file

# Performs a web query. TO DO: complete page related to cURL, as this is such an IMPORTANT tool
curl http://microsoft.com
curl -k https://microsoft.com -vvv 
curl -X HEADERS -vvv -k https://microsoft.com
 
# Echo text to the tesrminal, usefull to redirect to other commands
echo "Hello World"
echo "Hello World" >> MyText.txt

# Outputs the current logged in username
whoami

# searchs for every .txt in the current directory. 
find passwords.txt
sudo find / -name passwords* # searches everywhere for a file starting with keyword passwords

# GREP to search for pattern in a file (filter output)
cat access.log | grep "123.5.4.5"

# Determines the type of a given file, whether it's a .txt or else.
file test.txt

# Manage Contrab (special file with formatting that is recognised by the cron process to execute each line step-by-step at the boot of the computer.)
crontab -e # edit the crontab file (you can do it with Nano i.e.).
crontab -l # list current crontab entries

# Help with generating contrabs : https://crontab-generator.org/
```

## SHELL OPERATORS
`&` : allows you to run a command in the background 
```shell
sudo systemctl restart apache2& 
```
`&&` : allows you to combine commands in one line of code. 
command1 && command2 (command2 will only run if command1 was successful).
```shell
ip a && cat proof.txt && whoami
```
`>` : redirector. i.e. echo hey > Welcome(file name). If then I do : cat Welcome -> it will show me "Hey". If a file named Welcome already existed, it would have been overwritten. 

`>>` : same as > but doesn't replace the output, it copies it. Let's say that in the file "Welcome" the word "hey" is in. Now if I do echo >> Welcome the Welcome file now has in it : hey + hello (displayed under hey).
```shell
cat file1.txt > file2.txt # overwrites file2's content with file1's
cat file2.txt >> file1.txt # appends file2's content at the end of file1's (merge)
```

## PACKAGE MANAGEMENT

-add-apt-repository is a command that adds a repository to apt

To start downloading programs (like Sublime Text 3) we first need to get the GPG key (security key provided by the creators of the program).

So i.e. : wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add - 
The last part with sudo apt-key is a line to tell the server it can trust this key.

Then let's create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information. (touch Sublime-text.list i.e.)

After we have added this entry, we need to update apt to recognise this new entry -- this is done using the apt update command

Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using apt install sublime-text


