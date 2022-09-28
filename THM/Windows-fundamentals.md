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

# Windows fundamentals part 2

##System configuration

The System Configuration utility (MSConfig) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues. 

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
2. Boot
3. Services
4. Startup
5. Tools

1. In the General tab, we can select what devices and services for Windows to load upon boot. The options are: Normal, Diagnostic, or Selective. 

2. In the Boot tab, we can define various boot options for the Operating System. 

3. The Services tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.  

4. In the Startup tab, you won't see anything interesting in the attached VM.  Below is a screenshot of the Startup tab for MSConfig from my local machine. 

5. There is a list of various utilities (tools) in the Tools tab that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for. 
To run a tool, we can use the command to launch the tool via the run prompt, command prompt, or by clicking the Launch button. 

## Change UAC settings

We're continuing with Tools that are available through the System Configuration panel.

The UAC settings can be changed or even turned off entirely (not recommended).



