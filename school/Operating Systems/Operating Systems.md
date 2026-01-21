# 01/21/2026

- An Introduction To Operating Systems
	A computer's functions and features can be broken down into three basic tasks all computers perform:
		Input
		Processing
		Output
	The functions above involve some type of computer hardware
		But the hardware is controlled and coordinated by the operating system (OS)

CPN
	operating system?
	IBM-based operating system
	Xerox made the decision
		they were the first in the desktop 
	An OS is a specialized computer program that provides the following features:
		User Interface
			the user interface provides a method for users to interact with the computer
		Storage Management
			the file system is a method by which an OS stores and organizes files and manages access to files
		Process and service management
			a process is a program that is loaded into memory and run by the CPI; a service is a type of process that runs in the background

An OS is a specialized computer program that provides the following features
	memory and I/O management
		the OS must determine if sufficient memory exists to load an application and where in memory it should be loaded
			the OS also ensures that I/O devices such as USB ports and video cards are accessed by only one process at a time
	security and resource protection
		OSs used on business systems provide methods for securing access to resources
	Kernel
		the kernel is the heart of the OS and runs with the highest priority


Operating System Categories
	Single-tasking versus mutlitasking
	single-user versus multiusers
	general-purpose versus real-time

Single-Tasking Versus Multitasking Operating Systems
	A single-tasking operating system can execute only a single process at a time
		Apple iOS 3 are examples
		An embedded system is a computing device designed for a specific task and uses a single-tasking OS
	A multitasking operating system quickly switches between all the processes that are loaded nto memory
	There are two general types of multitasking
		cooperative multitasking
			the os gives cpu control to a process and waits for it to terminate or enter a waiting state
				if the program does not gives control back to the OS, it may hog the CPU until its operations are complete
				No other program can run until control is given back to the OS
				found in early windows versions
		preemptive	multitasking
			the os is in control of the computer at all times
				the running process can be replaced with another process at any time based on a system interrupt, a higher-priority task requriing the CPI, or the time-slice timer expiring
				The OS has control over how much of the computer's resource are allocatedto each program
				Computers must use more of their CPI and memory to suport the OS, but the be