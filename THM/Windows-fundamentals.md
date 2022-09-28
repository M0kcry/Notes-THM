# Windows fundamentals 1

## The File System

The file system used in modern versions of Windows is the New Technology File System or simply NTFS.

Before NTFS, there was FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System). 

You still see FAT partitions in use today. For example, you typically see FAT partitions in USB devices, MicroSD cards, etc. but traditionally not on personal Windows computers/laptops or Windows servers.

NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT.

On NTFS volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:

- Full control
- Modify
- Read & Execute
- List folder contents
- Read
- Write

![image](https://user-images.githubusercontent.com/112873207/192795479-47289362-70eb-43dd-a386-f17748d46d20.png)

Another feature of NTFS is Alternate Data Streams (ADS).

Alternate Data Streams (ADS) is a file attribute specific to Windows NTFS (New Technology File System).

Every file has at least one data stream ($DATA), and ADS allows files to contain more than one stream of data. Natively Window Explorer doesn't display ADS to the user. 

There are 3rd party executables that can be used to view this data, but Powershell gives you the ability to view ADS for files.

From a security perspective, malware writers have used ADS to hide data.

Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.

## System 32 Folders

The Windows folder (C:\Windows) is traditionally known as the folder which contains the Windows operating system. 

This is where environment variables, more specifically system environment variables, come into play. Even though not discussed yet, the system  environment variable for the Windows directory is %windir%.

The System32 folder holds the important files that are critical for the operating system.

To protect the local user of high elevated privileges hacking, Microsoft introduced User Account Control (UAC). This concept was first introduced with the short-lived Windows Vista and continued with versions of Windows that followed.

Note: UAC (by default) doesn't apply for the built-in local administrator account. 





