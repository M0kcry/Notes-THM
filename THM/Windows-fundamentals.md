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

What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path) UserAccountControlSettings.exe

## Computer management

The Computer Management (compmgmt) utility has three primary sections: 

- System Tools
- Storage
- Services and Applications.

### System tools

Let's start with Task Scheduler. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

#### Task scheduler 

A task can run an application, a script, etc., and tasks can be configured to run at any point. 

A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.

To create a basic task, click on Create Basic Task under Actions (right pane).

#### Event Viewer

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. 

Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.

There are five types of events that can be logged.

![image](https://user-images.githubusercontent.com/112873207/192826289-de32d635-35cd-4c4b-8c0f-0a6c385de4c0.png)

The standard logs are visible under Windows Logs

![image](https://user-images.githubusercontent.com/112873207/192826520-4c785047-3fe0-4a5c-b3b8-b05a3c85ffc4.png)

#### Shared Folders

This is where you will see a complete list of shares and folders shared that others can connect to. 

#### Performance

In Performance, you'll see a utility called Performance Monitor (perfmon).

**Perfmon** is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote. 

**Device Manager** allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

#### Storage

Under Storage is Windows Server Backup and Disk Management. We'll only look at Disk Management in this room.

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:) 

#### Service and Applications

Recall from the previous task; a service is a special type of application that runs in the background. Here you can do more than enable and disable a service, such as view the Properties for the service. 

WMI Control configures and controls the Windows Management Instrumentation (WMI) service.

## System informations 

We're continuing with Tools that are available through the System Configuration panel.

msinfo32 : This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues.

The  information in System Summary is divided into three sections:

- Hardware Resources
- Components
- Software Environment

## Resource monitor (Resmon)

As some of the other tools mentioned in this room, this utility is geared primarily to advanced users who need to perform advanced troubleshooting on the computer system.

In the Overview tab, Resmon has four sections:

- CPU
- Disk
- Network
- Memory

## Command prompt (cmd)

In this task, we'll only cover a few commands that a computer user can run in the command prompt to obtain information about the computer system.

Let's start with a few simple commands, such as `hostname` and `whoami`.

- The command hostname will output the computer name.

- The command whoami will output the name of the logged-in user.

A command used often is ipconfig. This command will show the network address settings for the computer.

The next command is `netstat`, this command will display protocol statistics and current TCP/IP network connections. 

The `net` command is primarily used to manage network resources. This command supports sub-commands.

If you type net without a sub-command, the output will show the syntax for the root command showing a few of the sub-commands you can use.

If you wish to see the help information for `net user` , the command is `net help user`. 

## Registry Editor

This is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

**Warning**: The registry is for advanced computer users. Making changes to the registry can affect normal computer operations. 

There are various ways to view/edit the registry. One way is to use the Registry Editor (`regedit`).






