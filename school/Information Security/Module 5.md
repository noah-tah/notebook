adverse events
	An event with negative consequences that could threaten the organization’s information assets or operations; also referred to as an incident candidate.

contingency planning (CP)
- The actions taken by senior management to specify the organization’s efforts and actions if an adverse event becomes an incident or disaster; CP typically includes incident response, disaster recovery, and business continuity efforts, as well as preparatory business impact analysis.
	- Consists of four major components:
		- Business impact analysis (BIA)
		- Incident response plan (IR) plan)
		- Disaster recovery plan (DR plan)
		- Business continuity plan (BC plan)
- What communities of interest are associated with contingency planning?
	- contingency planning management team (CPMT)
		- consists of four teams to manage each part of the plan:
			- incident response planning team
			- disaster recovery planning team
			- business continuity planning team
			- crisis management planning team
	- This could also be interpreted as the two communities of interest: the Information Security/Information Technology and the Senior Management Community. The Senior Management community would oversee the process.

contingency planning management team (CPMT)
	The group of senior managers and project members organized to conduct and lead all CP efforts.

- To ensure continuity during the creation of the CP components, a seven-step process is used:
	1. Develop the contingency planning policy statement. A formal policy provides guidance.
	2. Conduct the BIA. Prioritize information systems and components critical to supporting the organization.
	3. Identify preventive controls. Reduce the effects of system distruptions, increasing system availability.
	4. Create contingency strategies. Recovery strategies to efficiently recover the system.
	5. Develop a contingency plan. Procedures for restoring damaged organizational facilities unique to the recovery requirements.
	6. Ensure plan testing, training and exercises. Validate recovery capabilities.
	7. Ensure plan maintenance. Living document that is updated regularly.

List and describe the teams that perform the planning and execution of the CP plans and processes. What is the primary role of each?
- Four teams are involved in contingency planning and contingency operations: the [[CP team]], the [[IR team]], the [[DR team]], and the [[BC team]]. The [[IR team]] ensure that the [[CSIRT]] is formed.

Define the term incident as used in the context or [[IRP]]. How is it related to the concept of incident response?
- An InfoSec incident is defined as the following
- It is directed against information assets.
- It has a realistic chance of success.
- It threatens the confidentiality, integrity, or availability of information resources and assets.
It relates to the concept of incident response in that you must clearly define the threats facing the organization in order to protect against them.


# The following types of incident candidates are considered possible indicators of actual incidents:

- _Presence of unfamiliar files_—Users might discover unfamiliar files in their home directories or on their office computers. Administrators might also find unexplained files that do not seem to be in a logical location or are not owned by an authorized user.
    
- _Presence or execution of unknown programs or processes_—Users or administrators might detect unfamiliar programs running, or processes executing, on office machines or network servers. Users should become familiar with accessing running programs and processes (usually through the Windows Task Manager shown in [Figure 5-8](https://ebooks.cengage.com/reader/a8ff6564-41f1-45ba-b286-90b49510b74c/content-bd_ch_05_sect_03_04?code=pqz8UNuKal3NXRO_s7EfW-3x5xim2FT0qMNWxT1gw_8&state=919e601f-943b-4e33-9f1c-642a621f4dc0&sidepanel=contents#RFYZ5G10BG01HHA0Q317)) so they can detect rogue instances.
    
- _Unusual consumption of computing resources_—An example would be a sudden spike or fall in consumption of memory or hard disk space. Many computer operating systems, including Windows, Linux, and UNIX variants, allow users and administrators to monitor CPU and memory consumption. The Windows Task Manager has a Performance tab that provides this information, also shown in [Figure 5-8](https://ebooks.cengage.com/reader/a8ff6564-41f1-45ba-b286-90b49510b74c/content-bd_ch_05_sect_03_04?code=pqz8UNuKal3NXRO_s7EfW-3x5xim2FT0qMNWxT1gw_8&state=919e601f-943b-4e33-9f1c-642a621f4dc0&sidepanel=contents#RFYZ5G10BG01HHA0Q317). Most computers also have the ability to monitor hard drive space. In addition, servers maintain logs of file creation and storage.
    
- _Unusual system crashes_—Computer systems can crash. Older operating systems running newer programs are notorious for locking up or spontaneously rebooting whenever the operating system is unable to execute a requested process or service. You are probably familiar with system error messages such as “Unrecoverable Application Error,” “General Protection Fault,” and the infamous Windows “Blue Screen of Death.” However, if a computer system seems to be crashing, hanging, rebooting, or freezing more frequently than usual, the cause could be an incident candidate.

- Activities at unexpected times—If traffic levels on the organization’s network exceed the measured baseline values, an incident candidate is probably present. If this activity surge occurs outside normal business hours, the probability becomes much higher. Similarly, if systems are accessing drives and otherwise indicating high activity when employees aren’t using them, an incident may also be occurring.

- Presence of new accounts—Periodic review of user accounts can reveal accounts that the administrator does not remember creating or that are not logged in the administrator’s journal. Even one unlogged new account is an incident candidate. An unlogged new account with root or other special privileges has an even higher probability of being an actual incident.

- Reported attacks—If users of the system report a suspected attack, there is a high probability that an incident has occurred, whether it was an attack or not. The technical sophistication of the person making the report should be considered. If systems administrators are reporting attacks, odds are that additional attacks are occurring throughout the organization.

- Notification from an IDPS—If the organization has installed and correctly configured a host- or network-based intrusion detection and prevention system (IDPS), then a notification from the IDPS indicates that an incident might be in progress. However, IDPSs are difficult to configure perfectly, and even when they are, they tend to issue false positives or false alarms. The administrator must then determine whether the notification is real or the result of a routine operation by a user or other administrator. 

- Use of dormant accounts—Many network servers maintain default accounts, and there are often accounts from former employees, employees on a leave of absence or sabbatical without remote access privileges, or dummy accounts set up to support system testing. If any of these accounts activate and begin accessing system resources, querying servers, or engaging in other activities, an incident is certain to have occurred.

- Changes to logs—Smart systems administrators back up system logs as well as system data. As part of a routine incident scan, systems administrators can compare these logs to the online versions to determine whether they have been modified. If they have, and the systems administrator cannot determine explicitly that an authorized individual modified them, an incident has occurred.


- Use of dormant accounts—Many network servers maintain default accounts, and there are often accounts from former employees, employees on a leave of absence or sabbatical without remote access privileges, or dummy accounts set up to support system testing. If any of these accounts activate and begin accessing system resources, querying servers, or engaging in other activities, an incident is certain to have occurred.

- Changes to logs—Smart systems administrators back up system logs as well as system data. As part of a routine incident scan, systems administrators can compare these logs to the online versions to determine whether they have been modified. If they have, and the systems administrator cannot determine explicitly that an authorized individual modified them, an incident has occurred.

- Presence of hacker tools—Network administrators sometimes use system vulnerability and network evaluation tools to scan internal computers and networks to determine what a hacker can see. These tools are also used to support research into attack profiles. All too often, however, they are used by individuals with local network access to hack into systems or just “look around.” To combat this problem, many organizations explicitly prohibit the use of these tools without permission from the CISO, making any unauthorized installation a policy violation. Most organizations that engage in penetration testing require that all tools in this category be confined to specific systems and that they not be used on the general network unless active penetration testing is under way. Finding hacker tools, or even legal security tools, in places they should not be is an indicator that an incident has occurred.

- Notifications by partner or peer—If a business partner or another integrated organization reports an attack from your computing systems, then an incident has occurred. It’s quite common for an attacker to use a third party’s conscripted systems to attack another system rather than attacking directly.

- Notification by hacker—Some hackers enjoy taunting their victims. If an organization’s Web pages are defaced, it is an incident. If an organization receives an extortion request for money in exchange for its stolen data, an incident is in progress. Note that even if an actual attack has not occurred—for example, the hacker is just making an empty threat—the reputational risk is real and should be treated as such.
Once an actual incident has been confirmed and properly classified, the IR plan moves from the detection phase to the reaction phase.
- Once an actual incident has been confirmed and properly classified, the IR plan moves from the detection phase to the reaction phase.

- List and describe the sets of procedures used to detect, contain, and resolve an incident.
	- The set of procedures used to detect and incident are:
		- Incident classification and incident detection
		- alert roster  is used to deliver the alert message, which organizes a team to respond to the incident.
		- documentation must begin immediately, and serves as a case study to determine if the correct actions were taken, and if they were effective.
		- the containment procedures focus on stopping the incident and recovering control of the affected systems. the simplest and most straightforward way to stop the incident is to simply disconnect the affected communication circuit, essentially moating that part of the system off, although it obviously is not always going to be that simple. 