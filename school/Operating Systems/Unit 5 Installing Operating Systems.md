# Windows Server 2019
- Install Windows Server 2019
- In this project, you install Windows Server 2019
- When installing Windows Server 2019, you must open the storage menu and click the disk icon, then select the iso file in order for the installation to be successful.


# Fedora Workstation

• What virtual machine settings did you choose?
	- The virtual machine settings that I chose:
		- Base Memory: 2048 MB
		- Boot Order: Floppy, Optical, Hard Disk
		- Video Memory: 16 MB
		- Graphics Controller: VMSVGA
		- Controller: IDE
			- IDE Primary Device 0: [Optical Drive] Fedora-Workstation-Live-43-1.6x86_64.iso (2.55 GB)
		- SATA Port 0: Fedora Workstation.vdi (Normal, 15.00GB)
• Where did you get the Fedora Workstation ISO file?
	- I got the ISO file from fedoraproject.org, more specifically the following link:
		- https://www.fedoraproject.org/workstation/download/
• What setting did you need to change on the virtual machine before you could begin the installation?
	- No setting needed changing for me, I was able to install this while running Windows Server 2019 in another VM and had no problems at all with installation. Installing Windows Server 2019 wasn't as straightforward though, and had to open the settings and point to the ISO file
	- Upon further use I actually had to allocate a bit more ram and 