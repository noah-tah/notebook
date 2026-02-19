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
				- This actually failed because we haven't installed the DNS service yet, and it will resolve itself when the DNS service is installed more than likely.
- Assigning a Computer Name
	- 


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