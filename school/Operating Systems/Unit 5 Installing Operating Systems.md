# Windows Server 2019
- Install Windows Server 2019
- In this project, you install Windows Server 2019
- When installing Windows Server 2019, you must open the storage menu and click the disk icon, then select the iso file in order for the installation to be successful.
- **Description:** Your Windows Server 2019 computer is ready for you to perform post installation tasks. Based on the description of these tasks in this module, configure your server. Assume it’s a test server for the IT department, and give it a suitable name. Do the following:

• List the configuration tasks you performed and the values and settings you used:
- Setting the Time Zone and Date
	- Opened Settings
	- Under Time Zone, I selected Central Time (US & Canada)
- Assigning an IP Address
	- First I checked to see what was currently set:
		- Opened powershell, ran `netsh`, then ran `interface`, then `ipv4`, then, `show config`.
		- It listed the following configuration:
			- DHCP enabled: Yes
			- IP Address: 10.0.2.15
			- Subnet Prefix: 10.0.2.0/24 (mask 255.255.255.0)
			- Default Gateway 10.0.2.2
			- DNS servers configured through DHCP: 192.168.4.1
			- WINS servers configured through DHCP: None.
		- I decided this will be the domain controller, so I changed the IP address using the following command after navigating to `netsh interface ipv4` again:
			- `set address name="Ethernet" static 192.168.0.1 255.255.255.0`
		- Then set the DNS to itself so that it checks its own database when looking up a computer name
			- Inside the `netsh interface ipv4`:
				- `set dns name="Ethernet" static 127.0.0.1`
				- This actually failed and so I tried using the GUI next
			- In Server Manager, I selected Local Server, and in the Local Server Properties section I selected 192.168.0.1 which was under Ethernet, and it opened up Network Connections.
				- Here, I right clicked, selected properties.
					- I double clicked Internet Protocol Version 4 (TCP/IPv4), and it opened up it's properties.
						- Here I was able to check to see what the preferred DNS server was and it was already `127.0.0.1` so operation success.
		- set the DNS server address to 127.0.0.1
- Assigning a Computer Name
	- For this I chose to use PowerShell:
		- `Rename-Computer -NewName "DC01-WS19"`
		- I chose this name because it follows a naming convention I thought made sense. "Domain Control 1, Windows Server 2019" would be the long version of the name. It is concise and scalable.
	- I had to restart the server to change the name:
		- `Restart-Computer`
- Configuring and Installing Updates
	- I selected the link next to Windows Update and checked for updates.


	- Windows Server configures the network interface to use DHCP by default, server may already haven an IP address assigned via DHCP.
	- I can use the GUI, the `netsh` command, or the `New-NewIPaddress` PowerShell cmdlet to set your IP address.
	- You'll see the address of your default gateway and DNS servers as well.
		- If this server will be a DNS server, you can set the DNS server address to 127.0.0.1 and the server will use its own DNS service.
		- if this server will be a domain member, the DNS server address is usually one of the domain controller addresses.
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
	- Upon further use I actually had to allocate a bit more ram to the machine to get it to run smoothly as it was hanging up a bit with the default settings.

# Case Project 5-1 Determining Preliminary Steps
- Merlinos Mills is a company that produces flours and grains for grocery stores. It owns mills and distribution centers in the Northwestern and Midwestern United States. The headquarters in Bend, Oregon employs more than 400 people, most of whom use computers. Also, the headquarters has 28 servers, all running Microsoft Windows Server 2012 R2 Standard Edition. The company employees use Windows 7, Windows 8.1, and Mac OS X El Capitan.

- The management of Merlinos Mills wants each department to upgrade to newer OSs. Also, they are very concerned about network security, and they want to install new servers and upgrade their current servers to OS versions that take better advantage of security features. Your role in the process is to work with each department to help ensure that the installations and upgrades go smoothly.

- The master distribution center in Bend, Oregon houses 42 employees, including 22 people using Windows 7 Professional and 20 people using Windows 8.1. The distribution center is slated to upgrade its computers to Windows 10 Pro. What preliminary steps should be taken before starting the upgrades on these computers? In general, are there any problems involved in upgrading to Windows 10 from each of these OSs?


Master Distribution Center in Bend, Oregon Current Operating Systems
- Windows 7 Professional - 22 people
- Windows 8.1 - 20 people

Distribution center wants to upgrade to Windows 10 Pro.

What preliminary steps should be taken before starting the upgrades on these computers?
- The first thing is to make sure the PCs meet the minimum requirement for Windows 10:
	- 1 GHz
	- 2 GB RAM for 64-bit
	- 20 GB free disk space
- I would argue these machines need at least 8 GB of ram and an SSD for modern computing tasks.
- Should preform a full data backup as well, to create a safety net for the machine so we can roll back if necessary.
- Taken inventory of all proprietary software being used in the distribution center, and try these on a testing Windows 10 machine to see how everything works, may potentially need to run virtual machines to support legacy software.

What problems are involved in upgrading to Windows 10 from each of these OS's?
- Windows 7 does not have a direct upgrade path to Windows 10 Pro and an activation key will have to be purchased.
- The hardware on the Windows 7 machine is likely not compatible with modern drivers Windows 10 uses, and may cause potential problems.
- Depending o