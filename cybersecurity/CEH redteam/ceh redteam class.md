### 27-09-2025
- apt 
- kill chain
    - recon
    - weaponization
    - delivery
    - exploitation
---
#### 04-10-2025

- __module 1__
	- CIA triad.
	- red team and blue team.
		- red team - APT ( advanced persistance threat ).
		- blue team - SOC analysts.
	- hacking and hackers
		- types of hackers
			1. white hat hackers.
			2. black hat hackers.
			3. gray hat hackers.
			4. suicide hackers.
			5. script kiddies.
			6. cyber terrorists.
			7. state sponsored hackers.
			8. hacktivists.
	- attacks classification
		- passive attacks
		- active attakcs
		- close-in attacks
		- insider attacks
		- distribution ( supply chain )
	- information warfare :  concepts and strategies
		- command and control warfare
		- intelligence based warfare
		- electronic warfare
		- psychological warfare
		- hacker warfare
		- echonomic warfare
		- cyber warfare
	- hacking methodology
		- EC council methodology
			- planning and recon
			- scanning
			- gaining access
			- maintaining access
			- clearing tracks
	- Nmap firewall evasion
		- -f - fragmentation
		- -D - decoy
		- -S - spoof source address
		- -g - use given port number
	-  cyber kill chain methodologyy
		1. reconn
		2. weaponizationn
		3. deliveryy
		4. exploitaionn
		5. installationn
		6. command and controll
		7. actions andon objectivee
	- MITRE attack frameworkk
		1. recon  
		2. weapnoizationn
		3. deliveryy
		4. exploitt
		5. controll
		6. executee
		7. maintain
	- diamond model of intrusion analysis
	- risk management
	- cyber threat intelligence
		- threat intelligence cycle
	- incident management
		- incident handling and response
			1. preparation
			2. incident recording and assignment
			3. incident triage
			4. notification
			5. containment
			6. evidence gathering and forensic analysis
			7. eradication
			8. recovery
			9. post incident ativities
	- standards
		- payment card industry data security standard ( PCI DSS )
		- HIPPA ( helath insurance portability and accountability ).
		- iso/iec standards.
		- Sarbanes oxley act ( SOX )   
		- DMCA 
		- GDPR ( general data protection regulation )
		- DPA ( data protection act )
- __module 2__
	- recon and footprinting
	- footprinting
		- passive and active
	- types of info gathered during footprinting
		- system info
		- network info
		- organizational info
	- google dorking
	
---
#### 11-10-2025

- __module 3__
	- scanning
		- Host discovery
			- ICMP echo requests
			- ARP requests
				- `nmap -PR <target>`
				- `sudo arp-scan <options>`
			- TCP SYN pings
			- UDP probes
			- PING
			- Angry IP SCANNER
			- Nmap
		- Port and service scanning
			- total ports 65,536
			- `imp ports in network`
		- vulnerability scanning
		- other scanners
			- unicorn scan
			- masscan
			- Hping3
			- Metasploit framework
			- nmap
			- administrative and commercial tools.
				- solar winds network scanner
		- port scanning countermeasures.
			- firewall and ids rules
			- routing and filtering
			- disable unnecessary ports
- __module 4__
	- __enumeration__
		1. __network enumeration
			1. __netBIOS enumeration
				- _enum info :_
					- netBIOS names of hosts on the network
					- MAC address workgroup or domain names
				- _tools and commands :_
					- NBTstat (windows command-line tool)
					- NBTscan (linux tools)
					- nmap with nbstat.nse script
					- hyena
			2. __SMB enumeration
				- _enum info :_
					- shared folder and their permissions
					- user accounts and groups
					- system info
				- _tools and commands :_
					- nmap with aggressive scan (A flag)
					- net view (windows command)
					- SMBClient (linux cli tool)
					- Enum4linux
			3. __SNMP (simple network management protocol) enumeration
				- _enum info_
					- system uptime and services
					- network interfaces and their config
					- running processes
					- network connections and routing tables
					- user accounts
					- hardware and software details
				- _tools and commands :_
					- SNMP-check
					- nmap with SNMP scripts (s_nmp-win32-users.nse)
					- SNMPWalk
			4. __LDAP (lightweight directory access protocol) enumeration
				- _enum info :_
					- user accounts and their attributes
					- group membership
					- organizational units
					- computer accounts
					- domain controller and their details
					- other directory objects
				- _tools and commands :_
					- active directory 
					- AD explorer (sysinternal tool)
					- softera LDAP
					- LDAPsearch
					- nmap LDAP script (ldap-search.nse)
		2. Network Enumeration protocols and tools
			1. __NTP (Network Time Protocol) enumeration
				- sync the clocks of computer systems over a network
					- _enum info :_
						- presence of NTP servers
						- NTP server version
						- peer info
					- _tools and command :_
						- nmap 
						- ntpdate
						- ntptrace
						- ntpq
			2. __NFS (Network File System) enumeration__
				- NFS is a distributed file system protocol that allows a user on a client computer to acces files over a computer network much like local storage is accessed.
				- _enum info :_
					- exported dir of an NFS SERVER
					- permission on these exported dir
					- potentially sensitive files within accessable files
				- _tools and commands :_
					- showmount
					- nmap
					- RPC scan
					- Mounting NFS shares (linux command)
					
			3. __SMTP emueration__
				- mail transfer protocol
				- _enum info :_
					- valid user accounts or email addresses
					- expansion of mailing lists or aliases
				- _tools and commands :_
					- VRFY ( verify )
					- EXPN (expand)
					- RCPT TO (recipient to)
					- nmap
					- netcat or telnet
					- SMTP user-enum
					- metasploit
					- Nmap scripting engine (nse) script smtp-enum-users.nse
- __module 5__
	- __vulnerability analysis__
		- _vulnerability assessment, management, and classification
			- _popular tools :_
				- nessus
				- openvas
			- _vuln metrics and databases :_
				- CVSS (common vulnerability scoring system)
				- CVE (common vulnerability exposure)
				- NVD (national vulnerability database)
				- CWE (common weakness enumeration)
			- _vulnerability management lifecycle :_
				1. pre-assessment phase
					- identify and categorize assets
					- understand business processes
					- manage security controls
					- adhere to standards and policies
					- define scope
				2. assessment phase
					- physical security checks
					- identify security misconfig
					- run vuln scanning software
					- validate findings
				3. post-assessment phase
					- present findings
					- conduct risk assessment
					- recommend and prioritize remediations
					- perform training
					- 'lesson learned' review
					- verify fixes
					- implement continuous monitoring and logging
			- _vulnerability classification :_
				- misconfigurations
				- missing patches adn updates
				- application flaws / design flaws
				- cloud vulnerabilities
				- open services
				- buffer overflows
				- operating system flaws
		- _vulnerability assessment : types, models, tools, and reports_
			- 
				



 ---