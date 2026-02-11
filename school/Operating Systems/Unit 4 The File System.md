Folder
- Organizational structure that contains files and other folders on the storage device. It also contains information about the files it contains such as their type, size, or the date they were created or last modified. 

Directory
- Old term for Folder, typically when you are referring to a Linux file system.

Root
- The root of the file system typically refers to the mass storage media or flash drive that the operating system is being run from.

Subfolders or Subdirectories
- A folder/directory within a folder/directory.

Folder Structure
- Different operating systems have different methods for organizing their Folder Structure
- On Windows, most system configuration files are contained in the `\Windows` directory
- On Linux, most config files are contained in subdirectories of the `etc` directory

Clients and Servers Organize different types of files
- Clients are focused on placing most of their files in the `/home/` directory, where they keep documents, music, pictures, and videos and so forth
- Server operating systems might have a structure based around applications and user files.

Server might contain
- Operating System Files
- User files for each specific user
- Public files that are available to all users
- Software applications
- Other administrative files

Disk contention
- Occurs when two  or more processes attempt to access the files on a disc at the same time.
- Operating System files should be on a separate hard disk than User files to solve this problem.
	- It is also useful to store user data on a separate disk because it allows for easier backup of user data in the case of emergency.
	- Administrator also has more access to tools such as compression to be used on the drive as well that contains user data.


Metadata
- Metadata is data that describes the file and its contents, but is not the actual content contained within the file.

File Attributes
- Stored with the filename on the disk and it contains storage and operational parameters like whether it is read/write or read only or perhaps it is hidden.

Analyzing file Metadata on Windows using a PowerShell command
![[Pasted image 20260211070036.png]]


Low-level format
- Marks the location of disk tracks and sectors
- Disc is divided into tracks

Tracks
- Concentric circles around the disk.
- Each track is divided into sectors.

Sectors
- Portion of a track on a storage disk.

Block allocation
- Divides disk into logical blocks called clusters, sometimes called allocation units in Windows
- Keeps track of where specific files are stored on the disk.

Clusters
- Refer o a group of sectors on a disk

File Allocation Table (FAT)
- Defines the way data is stored on the drive
- Keeps track of where a file is on the disk, and information about the file's sizeBlock allocation data is stored on the disk itself using one of two techniques. One technique uses a fixed portion of the disk to store this data—for example, the file allocation table (FAT) file system initially implemented in MS-DOS and supported by all versions of Windows and most other OSs. The other technique uses various locations on the disk to store a special type of file that is used for folder and file allocation information; examples include NTFS for Windows systems and the Linux file systems. On NTFS-formatted disks, the allocation table is called the Master File Table (MFT), which is discussed later in the module. As you can imagine, the areas of the disk in which allocation information and folder information are stored are very important; without this data, it would be impossible to access any of the files on the system without using disk repair tools.

Partitioning
- Process of reserving some or all of the disk to be used by a particular file system such as NTFS or FAT32.

High-level formatting
- Process of setting initial folder structure, and file allocation information

Volume
- A formatted partition
- Volume can be formatted with the same file system or different file system in dual-boot set ups

Partition Table
- Reserved area that stores partition information
	- Size 
	- Location
- Known as the disk label in Linux
- Provides information to the computer about how to access the disk

Master Boot Record (MBR)
- Traditional BIOS uses this
- Does not only contain partition information.
	- Also contains boot code that locate and starts the operating system
		- Bootstrap code, or master boot code

Bootstrap code
- Examines the partition table and then it determines which partition to boot from, usually the active partition. 
	- That partition typically contains its own boot code, this will find that code and execute it.

Active Partition
- This meant the partition contained boot code, and stored data for the 