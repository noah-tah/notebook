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
		- Bootstrap code, or master boot codeGPT is more reliable than MBR because multiple copies of the partition data are stored in various places on the disk, so if one copy of the table is corrupted, it can be rebuilt using other copies.

Bootstrap code
- Examines the partition table and then it determines which partition to boot from, usually the active partition. 
	- That partition typically contains its own boot code, this will find that code and execute it.

Active Partition
- This meant the partition contained boot code, and stored data for the PC system, and contained the operating system.

Extended partition
- Divided into one or more logical drives before disk space can be accessed, can not be marked active and contain an OS volume

Logical drives
- Sections of an extended partition that can contain data, but can not be an active partition containing a bootable os.

GUID Partition Table (GPT)
- More reliable than MBR because  multiple copies of the partition data are stored in multiple places on the disk, creating redundancy.
- Can be rebuilt using other copies.


Cyclic Redundancy Check (CRC) 
- Ensure no unauthorized changes have happened to the table.
- A CRC is a formula calculated by using the data bytes of a file or other data object and calculates its 32-bit signature to verify the integrity of the data.
	- If data changes in a non-standard manner, CRC check will fail.

Basic Disks
- Default type and been around since the IBM PC.
- Either MBR or GPT 
- Volumes are defined by their config
- Once volume is created on disk, can only be increased in size.
- Basic disks do not support the following:
	- RAID config
	- Disk striping
	- Disk spanning

Dynamic Disks
- Uses a database to store volume information about dynamic disks on the system.
- Stores volume information not only for all volumes on that disk but about all volumes on all the disks.
- If one database gets corrupted,  it can be repaired using the database information from another disk.

Mount
- Process that makes a disk partition or volume available for use by the OS

Volume mount point
- Empty folder where the volume is mounted.

Formatting
- After partitioning the disk, formatting is the act of implementing the filesystem on the drive

Boot Block
- first sector on the disk
- Contains information needed to boot the OS

Disk Cluster
- Group of one or more sectors used to store files.

Linked List
- Method used in FAT32 filesystems that store data in a cluster that points to the next cluster

Bad Clusters
- Sectors of the disk that are never used by the FAT32 filesystem

Master File Table (MFT)
- Storage organization system used with NTFS
- Located within the beginning of the partition
- A file on the system
- Second file on the system contains the first 3 records so that the MFT can be reproduced in the event of catastrophic failure.
- When a file is created in NTFS, Metadata about that file is stored in the MFT.
	- If there is not enough space on the MFT, a cluster is utilized and the sequential clusters are noted in the MFT

Hard Linking
- Permits multiple folder entries to point to the same file

Disk Quotas
- Specific amount of disk space allocated for an application that it should not exceed on the disk.

Journaling
- Tracks file changes in case of an unexpected crash so it is possible to roll back or reconstruct files.

Hot fix
- NTFS can copy data from a bad disk area to an undamaged area of the disk.

CD-ROM File System (CDFS) 
- Supported so that OS and read/write to DVD/CD-ROM drives.


Universal Disk Format (UDF)
- Allows for larger file storage for movies and games to be contained on CD-ROM 

UNIX File System (UFS)
- Uses hierarchical tree structure that can be expanded.
- Many qualities of NTFS are modeled after UFS.

Extended File System (EXT)
- Default Linux File System



