# Certified SOC Analyst v2 - Module 02: Understanding Cyber Threats, IoCs, and Attack Methodology - Complete Study Notes

---

## Table of Contents

1. Cyber Threats and Impact on Cybersecurity
2. Network Attack TTPs
3. Host Attack TTPs
4. Application Attack TTPs
5. Social Engineering Attack TTPs
6. Email Attack TTPs
7. Insider Attack TTPs
8. Indicators of Compromise (IoCs)
9. Attacker's Hacking Methodology
10. Module Summary

---

# PART 1: CYBER THREATS AND IMPACT ON CYBERSECURITY

## 1.1 Understanding Cyber Threats

### Definition

A cyber threat is an act in which an adversary attempts to gain unauthorized access to an organization's network by exploiting communication paths. Adversaries use cyber threats to infiltrate and steal data such as personal information, financial information, and login credentials.

### Three Components of a Threat

| Component | Description |
|-----------|-------------|
| **Intent** | The motive of an adversary behind targeting the organization |
| **Capability** | The Tactics, Techniques, and Procedures (TTPs) that an adversary can use to target the organization |
| **Opportunity** | A security vulnerability or weakness in the organization that can allow an adversary to target it |

### Categories of Cyber Threats

- Network threats
- Host threats
- Application threats

### Attack Vectors

- Viruses
- Worms
- Botnets

---

## 1.2 Cyber Security Attack Vectors

### Cloud Computing Threats
- On-demand delivery of IT capabilities
- Clients store sensitive information in the cloud
- Flaw in one client's application could allow access to another client's data

### Advanced Persistent Threat (APT)
- Focuses on stealing information without user being aware
- Targeted at large companies and government networks
- Slow in nature, negligible effects on performance
- Exploits vulnerabilities in applications, operating systems, and embedded systems

### Viruses and Worms
- Most prevalent networking threats
- Can infect a network within seconds

**Virus:**
- Self-replicating program
- Produces copies by attaching to another program, boot sector, or document

**Worm:**
- Replicates, executes, and spreads across network connections
- Enters network through malicious downloads, spam, or malicious websites

### Ransomware
- Restricts access to computer system's files and folders
- Demands ransom payment to remove restrictions
- Spread via malicious email attachments, infected software, or compromised websites

### Mobile Threats
- Increasing focus on mobile devices due to widespread adoption
- Fewer security controls compared to traditional systems
- Malware applications (APKs) can damage data and convey sensitive information
- Attackers can remotely access cameras and recording apps

### Botnet
- Huge network of compromised systems
- Used for denial-of-service attacks
- Performs tasks: uploading viruses, sending spam, stealing data
- Antivirus programs may fail to detect

### Insider Threat
- Attack launched by someone from within organization
- Has authorized access and knows network architecture

### Phishing
- Sending illegitimate emails falsely claiming to be from legitimate sites
- Acquires user's personal or account information
- Distributes malicious links via communication channels

### Web Application Threats
- SQL injection and cross-site scripting
- Result of flawed coding and improper sanitization
- Can threaten website performance and security

### IoT Threats
- Devices have little or no security
- Hardware constraints prevent complex security mechanisms
- Vulnerable to various attacks

---

## 1.3 Intent-Motive-Goal

### The Attack Formula

```
Attack = Motive (Goal) + Method (TTPs) + Vulnerability
```

### Examples of Motives Behind Cyber Attacks

| Motive | Description |
|--------|-------------|
| Disrupting business continuity | Causing operational downtime |
| Information theft | Stealing valuable data |
| Manipulating data | Altering information for malicious purposes |
| Creating fear and chaos | Disrupting critical infrastructure |
| Financial loss | Causing monetary damage |
| Propagating religious or political beliefs | Advancing ideological agendas |
| Achieving state's military objectives | Espionage and warfare |
| Damaging reputation | Harming brand image |
| Taking revenge | Personal retaliation |
| Demanding ransom | Extortion for financial gain |

---

## 1.4 Tactics, Techniques, and Procedures (TTPs)

### Overview

TTPs refer to the patterns of activities and methods associated with specific threat actors or groups of threat actors. They are helpful in analyzing threats, profiling threat actors, and strengthening security infrastructure.

### Tactics
- **Definition:** A guideline that describes the way an attacker performs the attack from beginning to end
- **Examples:** Information gathering, privilege escalation, lateral movement, deploying measures for persistent access

### Techniques
- **Definition:** Technical methods used by an attacker to achieve intermediate results during an attack
- **Examples:** Initial exploitation, setting up command and control channels, accessing infrastructure, covering tracks of data exfiltration

### Procedures
- **Definition:** Organizational approach followed by threat actors to launch an attack
- **Example:** In information gathering, an actor collects target information, identifies key targets and employees, collects contact details, identifies vulnerable systems and potential entry points, and documents all collected information

### Importance of Understanding TTPs

- Predict and detect evolving threats early
- Identify vulnerabilities and implement defensive measures
- Understand what attackers are looking for in target infrastructure

---

## 1.5 Opportunity-Vulnerability-Weakness

### Vulnerability Definition

Vulnerability is the existence of a weakness, design, or implementation error that, when exploited, leads to an unexpected and undesired event compromising the security of the system.

### Examples of Vulnerabilities

#### TCP/IP Protocol Vulnerabilities
- HTTP, FTP, ICMP, SNMP, SMTP are inherently insecure
- Hosts depend only on IP source address for authentication
- Network control mechanisms and routing protocols have less or no authentication

**Examples:** Overlapping IP fragments, SYN attack, Ping Flooding, IP spoofing

#### Operating System Vulnerabilities
- Inherently insecure operating systems
- Systems not updated with latest patches
- Memory corruption, Overflow, Remote Code Execution, DoS, CSRF File inclusion

#### Network Device Vulnerabilities
- Lack of password protection
- Lack of authentication
- Insecure routing protocols
- Firewall vulnerabilities

---

# PART 2: NETWORK ATTACK TTPS

## 2.1 Reconnaissance Attacks

### Overview

In reconnaissance attacks, attackers attempt to discover the target network's information. The aim is to gather all possible information about the target network.

### Network Information Obtained

- Domain Name
- Internal Domain Names
- Network Blocks
- IP Addresses of Reachable Systems
- Rogue Websites/Private Websites
- TCP and UDP Services Running
- Access Control Mechanisms and ACLs
- Networking Protocols
- VPN Points
- IDSs Running
- Analog/Digital Telephone Numbers
- Authentication Mechanisms
- System Enumeration

### Types of Reconnaissance Attacks

#### Active Reconnaissance Attacks
- Include port scans and operating system scans
- Attacker uses tools to send packets to target system
- Traceroute helps gather IP addresses for routers and firewalls

#### Passive Reconnaissance Attacks
- Use method of gaining information from traffic
- Perform sniffing to gain details about weaknesses in network

### Examples of Reconnaissance Attacks

| Attack Type | Description |
|-------------|-------------|
| Packet Sniffing | Monitors every packet passing through a network; captures usernames, passwords, and other user information |
| Port Scanning | Gives access to any open ports on target machine |
| Ping Sweeping | Locates open/live port in a network through ICMP request |
| DNS Footprinting | Uses DNS lookup and whois queries to get domain and IP address information |
| Social Engineering | Targets unknowingly share credentials or personal information |

---

## 2.2 Network Scanning

### Overview

In network scanning attack, the network is scanned to perform internal audits. It facilitates the attacker to extract information such as live hosts on a network, services, packet filters/firewalls, operating systems, and OS versions.

### Information Extracted

- Live hosts on network
- Services (application name and version)
- Type of packet filters/firewalls
- Operating systems and OS versions
- Network weaknesses

### Common Tools

- Nmap
- Nessus
- OpenVAS
- Qualys FreeScan

### Nmap Capabilities

- Determine what hosts are available on the network
- What services hosts are offering
- What operating systems they are running
- What type of packet filters/firewalls are in use

---

## 2.3 Port Scanning

### Overview

Port scanning is the process of checking what services are running on the target computer by sending a sequence of messages to break in. It involves connecting to or probing TCP and UDP ports on the target system.

### Purpose

- Determine if services are running or in a listening state
- Identify operating system and application in use
- Find open ports for potential exploitation

### Common Port Scanning Tools

- NMAP
- Netscan Tools Pro
- SuperScan
- PRTG Network monitor

---

## 2.4 DNS Footprinting

### Overview

DNS footprinting reveals information about DNS zones, including DNS domain names, computer names, and IP addresses.

### DNS Records

| Record Type | Description |
|-------------|-------------|
| A | Points to a host's IP address |
| MX | Points to domain's mail server |
| NS | Points to host's name server |
| CNAME | Canonical naming allows aliases to a host |
| SOA | Indicates authority for domain |
| SRV | Service records |
| PTR | Maps IP address to a hostname |
| RP | Responsible person |
| HINFO | Host information record (CPU type and OS) |
| TXT | Unstructured text records |

---

## 2.5 Network Sniffing

### Overview

Network sniffing involves capturing, decoding, inspecting, and interpreting the information inside a packet on a TCP/IP network.

### Purpose

- Steal information (user IDs, passwords, network details, credit card numbers)
- Generally referred to as a "passive" type of attack

### Ways to Sniff a Network

| Method | Description |
|--------|-------------|
| Internal Sniff | Employee hooked up to internal LAN runs tools to capture traffic |
| External Sniff | Hacker outside target network intercepts packets at firewall level |
| Wireless Sniff | Hacker sits near network to penetrate and get information |

---

## 2.6 Man-in-the-Middle Attack

### Overview

A man-in-the-middle attack (MITM) is an attack where attackers intrude into an existing connection between two systems to intercept messages and inject fraudulent information.

### Characteristics

- Snooping on a connection
- Intruding into a connection
- Intercepting messages
- Modifying data

### Communication Susceptible to MITM

- Login functionality
- Unencrypted Financial sites
- Telnet and wireless technologies

### TCP Connection Split

1. Client-to-attacker connection
2. Attacker-to-server connection

---

## 2.7 Password Attacks

### Overview

Password attacks are performed to gain unauthorized access or control over a target computer system.

### Password Attack Techniques

#### Dictionary Attack
- Attempts to crack password by guessing common words
- Uses dictionary of most used words
- Relatively faster than brute force
- Common passwords: password, root, administrator, admin, test, guest, qwerty

#### Brute Forcing Attack
- Tries every combination of characters until password is broken
- Best suited for small or not very complex passwords
- Time and resource-consuming

#### Hybrid Attack
- Works like dictionary attack
- Adds numbers and symbols to words
- Appends/prepends dates, numbers, alphanumeric characters

#### Birthday Attack
- Attacks cryptographic hash functions
- Based on probability of collisions
- Uses probability analysis to get birth dates

#### Rainbow Table Attack
- Uses huge set of pre-matched hashes
- Maps plain text passwords with hashes

---

## 2.8 Privilege Escalation

### Overview

In privilege escalation, the attacker gains access to a network using a non-admin user account and then gains administrative privileges.

### Types

#### Horizontal Privilege Escalation
- Unauthorized user accesses resources, functions, and privileges of authorized user with similar access permissions
- Example: Online banking user A accesses user B's bank account

#### Vertical Privilege Escalation
- Unauthorized user tries to gain access to resources and functions of users with higher privileges
- Example: Someone performing online banking accesses site with administrative functions

---

## 2.9 DNS Poisoning

### Overview

DNS poisoning is the unauthorized manipulation of IP addresses in the domain name system cache. A corrupted DNS redirects user requests to malicious websites.

### DNS Cache Poisoning

Altering or adding forged DNS records into the DNS resolver cache so that a DNS query is redirected to a malicious site.

**Process:**
1. DNS system uses cache memory to hold recently resolved domain names
2. Attacker targets DNS cache and makes changes or adds entries
3. Attacker replaces user-requested IP address with fake IP address
4. User is redirected to attacker's fake server

---

## 2.10 ARP Poisoning

### Overview

ARP poisoning is an attack where the attacker tries to associate their own MAC address with the victim's IP address so that traffic meant for that IP address is sent to the attacker.

### How ARP Works

- ARP resolves IP addresses to MAC (hardware) addresses
- ARP provides no means to verify authenticity of responding device
- Many operating systems accept ARP replies from devices that have not made ARP requests

### Attack Process

1. Attacker crafts malicious ARP reply containing arbitrary IP and MAC address
2. Victim's computer blindly accepts ARP entry into its ARP table
3. Attacker forces victim's computer to think IP is related to attacker's MAC address
4. Attacker broadcasts fake ARP reply to entire network

---

## 2.11 DHCP Starvation Attacks

### Overview

DHCP starvation attack floods DHCP servers with fake DHCP requests using all available IP addresses.

### Attack Process

1. Attacker broadcasts several DHCP requests with spoofed MAC addresses
2. Sending many DHCP requests consumes address space in DHCP server
3. Server cannot issue any more IP addresses
4. Valid users cannot obtain or renew IP addresses
5. Results in denial of service (DoS) attack

### Mitigation

- **Port Security:** Limits number of MAC addresses that can access port
- **DHCP Snooping:** Filters untrusted DHCP messages

---

## 2.12 DHCP Spoofing Attack

### Overview

A DHCP spoofing attack involves placing a rogue DHCP server between the client and the real DHCP server.

### Attack Process

1. Attacker introduces rogue server in network
2. Rogue server responds to DHCP discovery requests
3. Server that responds first is taken by client
4. Rogue server may assign attacker's IP address as client's default gateway
5. All traffic from client sent to attacker's IP address

### Mitigation

- Set interface to which rogue server is connected as untrusted
- Block all ingress DHCP server messages from that interface

---

## 2.13 Switch Port Stealing

### Overview

Switch port stealing is a MITM technique used to perform packet sniffing by exploiting switch ports of a user.

### Attack Process

1. Attacker floods switch ports with forged packets
2. Uses victim's spoofed MAC address as source address
3. Uses attacker's MAC address as destination address
4. Allows switch port to send traffic to attacker instead of intended recipients

---

## 2.14 MAC Spoofing/Duplicating

### Overview

MAC duplicating involves sniffing a network for MAC addresses of clients actively associated with a switch port and reusing one of those addresses.

### Attack Process

1. Attacker retrieves MAC addresses of legitimate clients connected to network
2. Attacker spoofs their own MAC address with MAC address of legitimate client
3. Attacker receives all traffic destined for the client

---

## 2.15 Network-Based Denial-of-Service (DoS) Attacks

### Overview

Network-based DoS attacks send large amounts of traffic to the target network, exhausting victim's connection resources.

### Types of Network-Based DoS

#### TCP SYN Flooding
- Attacker sends succession of SYN requests to target system
- Exploits weakness in TCP connection
- SYN flag establishes connection, FIN flag terminates
- Attacker does not respond with ACK in last step

#### UDP Flooding
- Attacker sends multiple UDP packets to targeted server
- Server validates if any program is running at port
- Spoofs source IP address of UDP packets

#### ICMP Smurf Flooding
- Attacker sends multiple ICMP Echo request packets
- Uses IP broadcast network function
- Spoofed source IP address of victim
- All hosts send ICMP Echo Reply packets to target

#### Intermittent Flooding
- Application layer DDoS attack
- Transmits intermittent floods of valid HTTP requests
- Aims to reduce quality of service (QoS), not shut down system

---

## 2.16 Distributed Denial-of-Service (DDoS) Attacks

### Overview

A DDoS attack is a large-scale, coordinated attack on the availability of services on a target's system or network resources. It is launched indirectly through many compromised computers on the Internet.

### Types of DDoS Attacks

#### Network-Centric Attack
- Targets bandwidth of a network or service
- Floods network infrastructure with immense volume of traffic
- Consumes network's bandwidth capacity

#### Application-Centric Attack
- Targets application layer of a service or server
- Sends high volume of requests or transactions
- Exhausts computing resources (CPU, memory, disk space)

### Impact of DDoS

- Loss of goodwill
- Disabled network
- Financial loss
- Disabled organizations
- Used as decoys for other attacks

---

## 2.17 Malware Attacks

### Overview

Malware is malicious software designed to perform activities intended by the attacker without user consent.

### Types of Malware

#### Virus
- Self-replicating program
- Spreads through hosts
- Can infect files from one computer to another

#### Armored Virus
- Specifically coded with mechanisms to make detection difficult
- Fools antivirus programs
- Implements complicated and confusing code

#### Trojan
- Malicious program that masquerades as legitimate software
- Consists of server (installed on infected system) and client (on attacker's computer)
- Can delete files, send files to intruder, modify files, install other programs

#### Adware
- Tracks user's browsing patterns for marketing purposes
- Collects user's data for targeted advertisements
- Legitimate software embedded with adware to generate revenue

#### Spyware
- Extracts user's information and sends to attackers
- Enables pop-up advertisements, modifies computer settings
- Keylogger is a type of spyware

#### Rootkits
- Software program that hides its activities from detection
- Performs malicious activities to get privileged access
- Hides the fact that operating system is compromised

#### Backdoors
- Small programs that bypass authentication checks
- Allows gaining administrative privileges without passwords
- Not logged, appears as if no one is online

#### Logic Bomb
- Piece of software code that performs malicious action when condition is satisfied
- Can display unauthentic message, delete data, reformat hard drives
- Used to demand money or blackmail

#### Botnets
- Collection of compromised computers connected to Internet
- Performs automated tasks without user permission
- Controlled by botmaster

#### Ransomware
- Locks or encrypts valuable files until ransom is paid
- Displays message on infected system
- Redirects victims to different sites for payment

#### Polymorphic Malware
- Changes its signature to avoid pattern matching detection
- Functionality remains same even though signature changes
- Code (payload) is encrypted to hide and make it difficult to read

---

## 2.18 Advanced Persistent Threats (APTs)

### Definition

An APT is a type of network attack where an attacker gains unauthorized access to a target network and remains undetected for a long period of time.

### Information Obtained During APT

- Classified documents
- User credentials
- Employee or customer's personal information
- Network information
- Transaction information
- Credit card information
- Organization's business strategy information
- Control system access information

### Characteristics of APTs

| Characteristic | Description |
|----------------|-------------|
| Objectives | Obtaining sensitive information or fulfilling political/strategic goals |
| Timeliness | Time from assessing target to gaining and maintaining access |
| Resources | Amount of knowledge, tools, and techniques required |
| Risk Tolerance | Level up to which attack remains undetected |
| Skills and Methods | Methods and tools used to perform attack |
| Actions | Technical "actions" that make APTs different from other attacks |
| Attack Origination Points | Numerous attempts to gain entry to target network |
| Numbers Involved | Number of host systems involved in attack |
| Knowledge Source | Gathering information through online sources about specific threats |
| Multi-Phased | Reconnaissance, gaining access, discovery, capture, data exfiltration |
| Tailored to Vulnerabilities | Target specific vulnerabilities present in victim's network |
| Multiple Points of Entries | Creates multiple points of entries through server |
| Evading Signature-based Detection | Bypasses firewall, antivirus, IDS/IPS, spam filters |
| Specific Warning Signs | Inexplicable user account activities, presence of backdoors, unusual file transfers |

### APT Lifecycle

#### 1. Preparation
- Define target
- Perform extensive research
- Organize team
- Build or attain tools
- Perform tests for detection

#### 2. Initial Intrusion
- Attempt to enter target network
- Common techniques: spear phishing emails, exploiting vulnerabilities
- Deploy malicious code or malware
- Initiate outbound connection

#### 3. Expansion
- Expand access to target network
- Obtain credentials
- Obtain administrative login credentials
- Escalate privileges

#### 4. Persistence
- Maintain access to target system
- Evade endpoint security devices
- Use customized malware
- Install malware in locations not frequently examined (routers, servers, firewalls, printers)

#### 5. Search and Exfiltration
- Gain access to resource for further attacks or financial gain
- Steal all data (documents, emails, shared drives)
- Use automated tools such as network sniffers
- Use encryption to evade DLP technologies

#### 6. Cleanup
- Prevent detection
- Remove evidence of compromise
- Hide target of attack and attacker details
- Manipulate data to mislead security analysts

---

## 2.19 Supply Chain Attack

### Overview

A supply chain attack is a cyberattack where an attacker infiltrates an organization's network by targeting its suppliers, third-party vendors, or elements within the supply chain.

### Attack Techniques

| Type of Attack | Example |
|----------------|---------|
| Malware Infection | Spyware used to steal credentials from employees |
| Social Engineering | Phishing, fake applications, typo-squatting |
| Brute-Force Attack | Guessing SSH passwords, web logins |
| Exploiting Software Vulnerability | SQL injection, buffer overflow |
| Exploiting Configuration Vulnerability | Misconfiguration/taking advantage of configuration issues |
| Physical Attack/Modification | Modify hardware, physical intrusion |
| OSINT | Search online for credentials, API keys, usernames |
| Counterfeiting | Imitations of USB with malicious purposes |

### Assets Targeted

| Asset | Example |
|-------|---------|
| Data | Video feeds, documents, payment data, emails, sales data, flight plans, intellectual property |
| People | Individuals targeted due to knowledge or position |
| Software | Modification of software, customer access to product source code |
| Processes | Documentation of internal operations, schematics |
| Personal Data | Employee records, credentials |
| Financial | Hijack bank accounts, money transfers, steal cryptocurrency |
| Bandwidth | Use bandwidth for DDoS, send spam, infect others |

---

# PART 3: HOST ATTACK TTPS

## 3.1 Common Threats Specific to Host Security

### Hosts at Risk

- **Internal Threats:** Occur within organization, can lead to great loss
- **External Threats:** Originate from outside organization

### Major Host Threats

#### 1. Malware Attack (Infection)

| Type | Description |
|------|-------------|
| Viruses | Replicate by reproducing themselves to infect host; delete files, reformat hard drives |
| Worms | Repeat without much human interaction; spread through network or Internet |
| Trojans | Complex threat; hide payload; file corruption, remote access, interrupt firewalls |
| Spyware | Used for spying on user actions; Keylogger captures keystrokes |
| Backdoor | Skips authentication steps; gains unauthorized access to remote computers |
| Ransomware | Encrypts files; demands payment for decryption key |
| Adware | Bundled with free software; displays advertisements; degrades performance |
| Rootkits | Hide existence of processes; provide continued privileged access |
| Fileless Malware | Operates without creating new files on hard drive; resides in memory |

#### 2. Accidental or Intentional Deletion of Data
- Confidential data deleted intentionally or accidentally
- Affects host security
- Compromises availability, confidentiality, and integrity

#### 3. Unauthorized Access
- Gaining access to restricted files, data, operations, services
- Bypasses security measures
- Leads to data theft, system manipulation

#### 4. Brute Force Attacks
- Systematically trying all possible password combinations
- Exploits weak passwords
- Automated tools generate and test vast numbers of passwords

#### 5. Privilege Escalation
- Gains limited user privileges
- Exploits vulnerabilities to gain administrative/root-level access
- Allows installing malware, altering configurations, stealing data

---

## 3.2 Host-Based DoS Attacks

### Overview

In host-based DoS attacks, the attacker exhausts the victim's resources by exploiting vulnerabilities in the system's OS, memory structure, algorithms, or authentication protocols.

### OS-Specific DoS Attacks

#### Ping of Death
- Maximum accepted size of IP packet is 65535 bytes
- Extremely large ICMP packet (65538 bytes) causes:
  - Crashing
  - Freezing
  - DoS
  - Rebooting
- Packet must be divided into fragments; reassembly crashes system

#### Teardrop Attack
- Exploits "fragment offset" field in IP header
- Offset specifies beginning point of fragment
- If offset and size of fragment differ from next fragmented packet, packets overlap
- Server trying to reassemble fragments crashes

---

## 3.3 Brute Force Attacks

### Overview

A brute-force attack involves systematically attempting all possible password combinations to gain unauthorized access to a system.

### Characteristics

- Trial-and-error approach
- Used to crack passwords
- Bypass authentication mechanisms
- Gain access to sensitive information

---

## 3.4 Spyware Attacks

### Overview

Spyware is designed to operate stealthily, often going undetected for extended periods.

### Capabilities

- Capture keystrokes (keylogging)
- Capture screenshots
- Monitor browser history
- Capture passwords and financial details

### Attack Methods

- Phishing emails with malicious attachments
- Exploit unpatched software vulnerabilities
- Trick users into installing legitimate-looking software

### Command and Control (C2)

- Spyware connects to C2 server
- Allows attacker to manage spyware remotely
- Issue commands
- Retrieve collected data
- Designed to be inconspicuous

---

## 3.5 Ransomware Attacks

### Overview

Ransomware attacks encrypt a victim's data and demand payment in exchange for the decryption key.

### TTPs of Ransomware

| Phase | Description |
|-------|-------------|
| Infiltration | Phishing emails, malicious attachments, drive-by downloads, exploiting vulnerabilities |
| Execution | Scans host for valuable files, encrypts using strong cryptographic algorithms |
| Propagation | Seeks to spread across network, infecting other systems |
| Coercion | Presents ransom demand, threatens data deletion or public release |

---

## 3.6 Where Do Attacks Come From?

### Vulnerabilities Exploited

| Source | Description |
|--------|-------------|
| Unpatched Computers | Lack of proper patching or outdated software creates security loopholes |
| Email | Phishing, malicious attachments, spam emails |
| Network File Sharing | Allows malware infections, exposure of sensitive information |
| Internet Downloads | Downloads from untrusted sources may contain malware |
| Social Engineering | Gain sensitive information, malware infection, unauthorized access |
| Blended Threats | Combination of multiple attack techniques |

---

# PART 4: APPLICATION ATTACK TTPS

## 4.1 SQL Injection Attacks

### Overview

SQL injection attacks use malicious SQL queries to directly manipulate a database. Attackers use vulnerable web applications to bypass normal security measures and obtain direct access to valuable data.

### How SQL Injection Works

Applications do not properly validate input before passing it to a SQL statement.

**Example:**

Original SQL:
```sql
SELECT * FROM tablename WHERE UserID = 2302
```

After SQL injection:
```sql
SELECT * FROM tablename WHERE UserID = 2302 OR (1 = 1) -- 
```

The expression `OR (1 = 1) --` evaluates to "TRUE", allowing enumeration of all user ID values.

### What Attackers Can Do

- Log into application without valid credentials
- Perform queries against data in the database
- Modify database contents or drop database
- Use trust relationships to access other databases

### Where SQL Injection Can Be Executed

- Web browser's address bar
- Form fields
- Queries
- Searches

---

## 4.2 Cross-Site Scripting (XSS) Attacks

### Overview

XSS attacks exploit vulnerabilities in dynamically generated web pages, enabling attackers to inject client-side script into web pages viewed by other users.

### How XSS Works

1. Web page consists of text and HTML markup created by server
2. Server cannot completely control client's interpretation of dynamically generated output
3. Attackers insert untrusted content into dynamic page
4. Neither server nor client recognizes it as malicious
5. Special characters in dynamic data are mistaken for HTML markup
6. Attacker's script executes in browser's security context

### What Attackers Can Do

- Malicious script execution
- Redirecting to malicious server
- Exploiting user privileges
- Ads in hidden IFRAMES and pop-ups
- Data manipulation
- Session hijacking
- Brute force password cracking
- Data theft
- Intranet probing
- Key logging and remote monitoring

### XSS Attack Scenarios

#### Attack via Email
- Attacker crafts email with link to malicious script
- Victim clicks link
- Malicious code executes on client machine
- Asks victim to enter profile information
- Attacker receives information

#### Attack in Blog Posting
- Attacker finds XSS vulnerability in blog site
- Constructs malicious script
- Adds to comment field
- Script stored on web-application database server
- When user visits website, malicious script activates

#### Attack in Comment Field
- Attacker finds vulnerable comment field
- Constructs malicious script
- Adds along with comment
- Script stored on database server
- User visits website, coded message pops up

---

## 4.3 Parameter Tampering

### Overview

Parameter tampering involves manipulation of parameters exchanged between server and client to modify application data such as price, quantity, permissions, and user credentials.

### Types of Parameter Tampering

#### Query String Tampering
- If query string visible in address bar, change string parameter
- Bypass authorization mechanisms
- Use web spidering tools like Burp Suite

**Examples:**
```
http://www.certifiedhacker.com/mail.aspx?mailbox=john&company=acme%20com
https://certifiedhackershop.com/books/download/852741369.pdf
https://certifiedhackerbank.com/login/home.jsp?admin=true
```

#### HTTP Headers
- Modify Referer header to access protected functionalities

#### Cookie Parameter Tampering
- Tamper with cookies set by web application
- When user logs in, web application sets session cookie
- Attacker modifies cookie contents

---

## 4.4 Directory Traversal

### Overview

Directory traversal (path traversal, forceful browsing) forces a web application to access unintended files and directories, disclosing valuable information.

### Attack Examples

```
http://www.example.com/process.aspx=./../some_dir/some_file
http://www.example.com/../../some_dir/some_file
```

### What Attackers Can Do

- Identify contents of files and directories
- Access pages requiring validation
- Obtain valuable information about web application structure
- Find user IDs and passwords
- View sensitive client information
- Discover source code and other important files

---

## 4.5 Cross-Site Request Forgery (CSRF)

### Overview

CSRF attacks exploit web page vulnerabilities, forcing unsuspecting users' browsers to send malicious requests they did not intend to send.

### Requirements for CSRF

1. User (victim)
2. Trusted website
3. Malicious website

### Attack Process

1. Victim logs into trusted site, creates new session
2. Trusted site stores session identifier in cookie
3. Victim visits malicious website
4. Malicious website injects HTTP request into victim's session
5. Request affects integrity of trusted site

### Effects of CSRF Attack

- **Normal user:** State changing requests (fund transfer, changing email address)
- **Administrative level:** Affects entire web application

### Also Known As

- One-click attack
- Session riding
- XSRF

---

## 4.6 Application-Level DoS Attacks

### Overview

Attackers exhaust available server resources by sending hundreds of resource-intensive requests.

### Why Web Applications Are Vulnerable to DoS

- Application environment bottlenecks
- Implementation flaws
- Poor data validation

### Examples

| Type | Description |
|------|-------------|
| User Registration DoS | Submits registration forms repeatedly, adding spurious users |
| User Enumeration | Automates process of trying common usernames from dictionary |
| Login Attacks | Overloads login process with continual login requests |
| Account Lockout Attacks | Uses valid usernames with incorrect passwords to lock accounts |

---

## 4.7 Session Attacks: Cookie Poisoning

### Overview

Cookie poisoning is a parameter tampering attack where the attacker modifies cookie contents to draw unauthorized information and perform identity theft.

### Cookie Contents

- User IDs
- Passwords
- Account numbers
- Links to shopping cart contents
- Private information
- Session IDs

### Steps of Cookie Poisoning

1. If cookie contains passwords or session identifiers, steal using script injection or eavesdropping
2. Replay cookie with same or altered passwords/identifiers
3. Trap cookies using tools like OWASP Zed Attack Proxy, Burp Suite

### Protection

- Encoding cookies gives false sense of security
- Encoding easily reversed with Base64, ROT13

---

## 4.8 Session Attacks: Session Fixation

### Overview

In a session fixation attack, the attacker tricks the user to access a genuine webserver using an explicit session ID value.

### Attack Process

1. Attacker authenticates themselves with a session ID
2. Attacker lures victim to use the same session ID
3. If victim uses session ID sent by attacker
4. Attacker hijacks user-validated session

---

## 4.9 OWASP Top 10 Web Application Security Risks

### Overview

OWASP (Open Web Application Security Project) is a non-profit organization involved in enhancing software security. It identifies the most critical vulnerabilities in web applications.

### OWASP Top 10 - 2021

| Rank | Risk | Description |
|------|------|-------------|
| A01 | Broken Access Control | Unauthorized users access restricted functionalities or data |
| A02 | Cryptographic Failures | Protecting data integrity and confidentiality failures |
| A03 | Injection | Flaws leading to loss of data or control over server |
| A04 | Insecure Design | Security issues due to lack of security in design phase |
| A05 | Security Misconfiguration | Insecure default settings, unchanged default passwords |
| A06 | Vulnerable and Outdated Components | Using components with known vulnerabilities |
| A07 | Identification and Authentication Failures | Weak authentication mechanisms enabling compromise |
| A08 | Software and Data Integrity Failures | Unverified software updates introducing backdoors |
| A09 | Security Logging and Monitoring Failures | Poor logging prevents detection of breaches |
| A10 | Server-Side Request Forgery (SSRF) | Inducing server to make requests to internal resources |

---

# PART 5: SOCIAL ENGINEERING ATTACK TTPS

## 5.1 Social Engineering Overview

### Definition

Social engineering is the art of convincing people to reveal confidential information. It involves influencing and persuading people to reveal sensitive information to perform malicious actions.

### Information Gathered Before Attack

- Official websites (employee IDs, names, email addresses)
- Job advertisements (skills, databases, servers)
- Blogs and forums (personal and organizational information)

### Types of Social Engineering

| Type | Description |
|------|-------------|
| Human-based | Physical presence required to extract personal information |
| Computer-based | Remotely extracting user credentials through other systems |

---

## 5.2 Social Engineering Techniques

### Impersonation

- Attacker pretends to be someone legitimate or authorized
- Performed in person or through communication medium (phone, email)
- Enables attackers to trick target into revealing sensitive information

### Eavesdropping

- Intercepting communication in any form (audio, video, text)
- Without consent of communicating parties
- Reading confidential messages

### Shoulder Surfing

- Secretly observing target to gain critical information
- Standing behind victim, observing computer activities
- Effective in crowded places

### Dumpster Diving

- Rummaging for information in garbage bins
- Finding phone bills, contact information, financial information
- Source code printouts, sensitive information

### Piggybacking

- Following authorized person into restricted areas
- Without proper identification

### Tailgating

- Unauthorized person follows authorized person through a secure door
- Similar to piggybacking

### Reverse Social Engineering

- Attacker creates problem, then offers solution
- Victim calls attacker for help
- Attacker gains trust and access

---

# PART 6: EMAIL ATTACK TTPS

## 6.1 Email Attacks: Phishing

### Overview

The attacker sends an email appearing legitimate, asking the victim for personal or financial information and includes a link to a seemingly genuine website.

### Attack Process

1. Attacker sends email requesting personal/financial information
2. Email includes link like that of genuine website
3. User submits form with updated details
4. Information is stored in attacker's database

### Characteristics

- Appears to be from valid organizations (banks, partner companies)
- Contains hyperlinks that may breach company security

---

## 6.2 Email Attacks: Malicious Email Attachments

### Overview

Attackers use malicious email attachments to deliver malware (viruses, worms, Trojans, rootkits, spyware) to a victim's computer when the attachment is opened.

### Types of Malicious Executables

- Viruses
- Worms
- Trojans
- Rootkits
- Spyware

### Methods

- HTML links
- Opening attachments
- May halt programs necessary for system functioning

---

## 6.3 Email Attacks: Malicious User Redirection

### Overview

An attacker sends an email containing a link that appears legitimate. When the user clicks the link, they are redirected to a malicious site.

### Types of Redirects

| Type | Description |
|------|-------------|
| Referrer based | Based on page followed from specific page |
| User agent based | Gathers information about device making request |
| Cookie based | Uses HTTP cookie stored by web browser |
| OS based | Depends on victim computer's configuration |

### Indicators of Malicious Redirection

- Website has malware warning screen or popup
- Requested website becomes invisible or displays blank page
- Browser redirected from website to some other domain
- Site cannot be accessed from Google search
- Requested website redirects user back to Google

---

## 6.4 Email Attacks: Spamming

### Overview

Spam refers to unsolicited commercial advertisements distributed online.

### Why Spam is Harmful

- Pollutes Internet, becomes less useful
- May contain fake, unreliable, worthless content
- May be illegal (trick users into revealing personal information)
- Destroys company's reputation
- Reduces productivity

### Common Spam Media

- Email (most common)
- Online message boards
- Chat rooms

---

# PART 7: INSIDER ATTACK TTPS

## 7.1 Types of Insider Threats

### 1. Malicious Insider
- Intentionally harms organization for personal gain, revenge, or other motives
- Clear motive, may plan attack meticulously
- Examples: Stealing data to sell to competitors, introducing malware, manipulating financial records

### 2. Negligent Insider
- Inadvertently causes harm through negligence, carelessness, or lack of awareness
- Does not intend to cause harm
- Examples: Sending sensitive information to wrong recipient, weak passwords, failing to follow protocols

### 3. Compromised Insider
- Credentials or access rights compromised by external attacker
- May be unaware access has been misused
- Examples: External attacker uses compromised account to steal data, spread malware

---

## 7.2 Insider Attack Examples

### Data Theft
- Insiders stealing sensitive or proprietary information
- Financial records, intellectual property
- Downloads confidential customer data to sell to competitors

### Policy Violations
- Insiders disregarding organizational policies or security measures
- Using unapproved software, sharing passwords with unauthorized individuals

### Fraud
- Insiders committing financial fraud or embezzlement
- Manipulating financial reports to cover up embezzled funds

### Sabotage Attack
- Insider intentionally damages or destroys systems, data, or applications
- Deleting critical files, corrupting databases
- Disrupting normal operations

### Espionage Attack
- Insiders leaking confidential information to external parties
- Competitors, foreign agents
- Sharing proprietary product development information

### Unauthorized Access
- Insiders accessing data or systems outside scope of duties
- Exceeding permissions
- Accessing HR files or financial records without legitimate reasons

### Malicious Software Installation
- Insiders installing malware or spyware
- Installing keyloggers to capture login credentials
- Compromising systems and stealing information

---

# PART 8: INDICATORS OF COMPROMISE (IoCs)

## 8.1 Overview

### Definition

Indicators of Compromise (IoCs) are clues, artifacts, and pieces of forensic data found on a network or operating system that indicate a potential intrusion or malicious activity.

### Types of IoCs

| Type | Description | Examples |
|------|-------------|----------|
| Atomic Indicators | Cannot be segmented into smaller parts; meaning not changed in context of intrusion | IP addresses, email addresses |
| Computed Indicators | Obtained from data extracted from security incident | Hash values, regular expressions |
| Behavioral Indicators | Grouping of atomic and computed indicators based on logic | Code injection into memory, running scripts |

### Why IoCs Are Important

- Helps detect data breaches, malware intrusion attempts
- Assists in knowing "what happened" during attack
- Improves response time and detection rate
- Provides data feeds for auto-response mechanisms
- Helps answer:
  - Does file consist of malicious content?
  - Is organization network compromised?
  - How did network get infected?
  - What is history of specific IP address?

---

## 8.2 Network Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Unusual Traffic Patterns | Irregular traffic flows indicating DDoS or data exfiltration | Network Traffic Analysis, IDS/IPS Logs |
| Anomalous DNS Requests | High frequency of requests to suspicious domains | DNS Logs, SIEM Tools |
| Port Scanning Activity | Repeated connection attempts across multiple ports | Firewall Logs, IDS/IPS Alerts |
| Unspecified Protocol Usage | Use of protocols not commonly seen in environment | Network Flow Logs, Packet Captures |
| Command and Control (C2) Traffic | Periodic control commands to suspicious IP addresses | Firewall Logs, SIEM Tools |
| Abnormal ARP Traffic | Unusual ARP requests indicating spoofing/poisoning | ARP Tables, Network Monitoring Tools |
| Suspicious VPN Activity | Multiple logins from different locations | VPN Logs, Authentication Logs |
| Unspecified Devices on Network | Unknown or unauthorized devices connected | Network Asset Management Tools, DHCP Logs |
| Malformed Packets | Packets not conforming to expected protocols | Packet Capture Tools, IDS/IPS Logs |
| Multiple Failed Login Attempts | High number of failed logins | IDS/IPS Logs, Network Access Control |
| Unusual Lateral Movement | Unexpected internal network traffic between hosts | Network Traffic Analysis, SIEM Tools |
| Rogue DHCP Servers | Unauthorized DHCP servers | DHCP Logs, Network Monitoring Tools |

---

## 8.3 Host Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Unusual Processes | Processes not typically seen, indicating malware | Task Manager, Process Monitor |
| Suspicious Network Activity | Connections to malicious IP addresses | Firewall Logs, EDR |
| File System Changes | Unexpected modifications, creations, deletions | File Integrity Monitoring, Audit Logs |
| Unauthorized User Accounts | New accounts or modifications without authorization | User Account Logs, Event Logs |
| Abnormal CPU Usage | Unexplained spikes in CPU usage | System Performance Monitor |
| Persistence Mechanisms | Techniques to maintain access (registry modifications, scheduled tasks) | Registry Logs, Task Scheduler Logs |
| Memory Modifications | Changes to system memory indicating malware/rootkits | Memory Dump Analysis, RAM Monitoring |
| Log Deletion/Alteration | Deletion or alteration of system logs | Event Logs, Security Logs |
| Remote Access Tools | Unauthorized installation of RATs | Application Logs, Security Software Alerts |
| Privilege Escalation Attempts | Attempts to gain higher system privileges | Privilege Access Management Logs |
| Suspicious Logs | Logins from unexpected locations | SIEM, Authentication Logs |
| Malware Artifacts | Presence of known malware signatures | Forensic Analysis, EDR, Antivirus Logs |

---

## 8.4 Application Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Unauthorized Changes | Modifications to application files/ configurations without authorization | File Integrity Monitoring, SIEM |
| Anomalous Authentication Events | Unusual login attempts or credential changes | SIEM, User Behavior Analytics |
| Unexpected Data Exfiltration | Large/unusual data transfers to external locations | Network Monitoring, DLP |
| Known Exploit Patterns | Signatures matching known exploits | IDS/IPS, Threat Intelligence Feeds |
| Malformed Requests | Unusual or malformed request structures | IPS/IDS, Web Application Firewalls |
| Error Messages and Stack Traces | Detailed error messages exposing internal workings | Web Server Logs, Application Code Reviews |

---

## 8.5 Social Engineering Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Pretexting Incidents | Fabricated scenarios to obtain information | Incident Reports, Security Awareness Training Feedback |
| Exploit Kits | Compromised websites targeting specific groups | Web Traffic Logs, Threat Intelligence Feeds |
| Impersonation Attempts | Pretending to be someone else | Incident Response Reports, User Reports |
| Baiting Incidents | Malware-infected physical devices left in public | Incident Reports, Security Awareness Reports |
| Social Media Posts | Offering value in exchange for information | User Reports, Social Media Monitoring |
| Unusual Help Desk Requests | Requests for password resets, access credentials | Help Desk Logs, Incident Response Reports |
| Suspicious In-Person Interactions | Attempts to gather information through conversation | Physical Security Logs, Employee Reports |
| Increased Reported Spam | Sudden rise in spam reports | Email Security Logs, User Reports |
| Fake Login Pages | Login pages imitating legitimate sites | User Reports, Email Logs |

---

## 8.6 Email Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Suspicious Email Attachments | Unusual file types, unexpected content, malware signatures | Email Gateway Logs, Antivirus Software |
| Phishing Emails | Designed to trick recipients into revealing information | Email Security Tools, User Reports |
| Spear Phishing Attempts | Targeted, personalized phishing emails | Email Logs, Incident Response Reports |
| Email Spoofing | Forged sender addresses | Email Headers Analysis, Email Gateway Logs |
| Malicious Links | URLs leading to harmful websites | URL Filtering Logs, Email Security Tools |
| Unusual Sending Patterns | Anomalies in frequency, timing, volume | Email Server Logs, SIEM Tools |
| Unauthorized Forwarding Rules | Forwarding rules configured without user knowledge | Email Configuration Logs, User Account Monitoring |
| Excessive Spam Reports | Sudden increase in spam reports | User Reports, Email Gateway Logs |
| Unknown/Obfuscated Attachments | File names with double extensions | Email Gateway Logs, Antivirus Software |
| Emails with Urgent Requests | Creating sense of urgency to bypass scrutiny | Email Content Analysis, User Reports |
| Compromised Email Accounts | Unauthorized access to email accounts | Authentication Logs, Account Activity Monitoring |
| External Emails with Internal Headers | Appear internal but sent from external sources | Email Headers Analysis, Security Awareness Training |
| Anomalous Time of Sending | Emails sent at unusual times | Email Server Logs, SIEM Tools |

---

## 8.7 Insider Attack IoCs

| IoC | Description | Source |
|-----|-------------|--------|
| Unauthorized Data Access | Access to sensitive data outside job function | Access Logs, DLP Tools |
| Exfiltration of Data | Large/unusual data transfers to external devices | Network Traffic Analysis, DLP Tools |
| Privileged Account Misuse | Using elevated permissions outside normal job | PAM Logs, SIEM Tools |
| Anomalous Account Activity | Sudden changes in user behavior | Authentication Logs, UBA |
| Unexpected File Modifications | Changes to critical files by unauthorized users | File Integrity Monitoring, Change Management Systems |
| Unusual Application Usage | Using applications not normally accessed | Application Logs, SIEM Tools |
| Disabled Security Controls | Security settings altered without authorization | Configuration Management Tools, Security Alerts |
| Multiple Login Locations | Logins from different geographic locations | Authentication Logs, SIEM Tools |
| Frequent Use of USB Devices | Increased usage of removable media | EDR Tools, DLP Tools |
| Attempts to Bypass Security Protocols | Circumventing established security protocols | Firewall Logs, IDS |
| Creation of Unauthorized Accounts | New user accounts created without authorization | User Account Management Logs, SIEM Tools |
| Increased Help Desk Requests | Rise in requests for password resets, access rights | Help Desk Logs, Access Management Systems |
| Unusual Data Queries | Database queries outside norm for user's role | Database Activity Monitoring, UBA Tools |

---

# PART 9: ATTACKER'S HACKING METHODOLOGY

## 9.1 EC-Council's Hacking Methodology

### Five Phases of Hacking

1. Reconnaissance
2. Scanning
3. Gaining Access
4. Maintaining Access
5. Clearing Tracks

---

### Phase 1: Reconnaissance

**Definition:** Preparatory phase where attacker gathers as much information as possible about target prior to launching attack.

**Techniques:**
- Competitive intelligence
- Social engineering
- Dumpster diving
- Whois database search

**Information Gathered:**
- Client information
- Employee information
- Operations information
- Network information
- System information

---

### Phase 2: Scanning

**Definition:** Phase immediately preceding attack; uses details gathered during reconnaissance to scan network for specific information.

**Tools:**
- Traceroute
- Cheops
- Dialers
- Port scanners
- Network mappers
- Ping tools
- Vulnerability scanners

**Information Extracted:**
- Live machines
- Port status
- OS details
- Device type
- System uptime

---

### Phase 3: Gaining Access

**Definition:** Phase where real hacking occurs; attackers use vulnerabilities identified to gain access to target system and network.

**Methods:**
- Password cracking
- Stack-based buffer overflows
- Denial-of-service
- Session hijacking
- Spoofing
- Packet flooding

**Access Levels:**
- Operating system level
- Application level
- Network level

---

### Phase 4: Maintaining Access

**Definition:** Phase where attacker tries to retain ownership of the system.

**Methods:**
- Installing backdoors
- Installing Trojans
- Installing rootkits
- Implementing sniffers
- Closing vulnerabilities

**Activities:**
- Upload, download, manipulate data
- Transfer usernames and passwords
- Maintain control for long time
- Use compromised system to launch further attacks

---

### Phase 5: Clearing Tracks

**Definition:** Activities carried out to hide malicious acts.

**Goals:**
- Continue access to victim's system
- Remain unnoticed and uncaught
- Delete evidence leading to prosecution

**Methods:**
- PsTools
- Netcat
- Trojans
- Steganography
- Tunneling

---

## 9.2 Lockheed Martin's Cyber Kill Chain Methodology

### Overview

The cyber kill chain methodology is a component of intelligence-driven defense for identification and prevention of malicious intrusion activities.

### Seven Phases

#### 1. Reconnaissance
- Research, identification, selection of targets
- Gathering information through social engineering, public information
- Performing Whois, DNS, network footprinting
- Scanning for open ports and services

#### 2. Weaponization
- Analysis of data to identify vulnerabilities
- Creating tailored deliverable malicious payload
- Creating phishing email campaign
- Leveraging exploit kits and botnets

#### 3. Delivery
- Transmitting weapon to intended victim
- Email attachments, malicious links, USB drives
- Phishing emails, watering hole attacks

#### 4. Exploitation
- Triggering malicious code to exploit vulnerability
- Exploiting software or hardware vulnerability
- Authentication and authorization attacks

#### 5. Installation
- Downloading and installing malicious software
- Installing backdoor for remote access
- Spreading infection to other end systems

#### 6. Command and Control (C2)
- Creating two-way communication channel
- Using web traffic, email, DNS messages
- Applying privilege escalation techniques
- Hiding evidence using encryption

#### 7. Actions on Objectives
- Controlling victim's system remotely
- Gaining access to confidential data
- Disrupting services or network
- Destroying operational capability

---

## 9.3 MITRE ATT&CK Framework

### Overview

MITRE ATT&CK is a globally accessible knowledge base of adversary tactics and techniques based on real-world observations.

### Components

- **Enterprise:** 14 categories of tactics
- **Mobile:** Mobile-specific tactics and techniques
- **PRE-ATT&CK:** Pre-exploitation tactics

### Tactics in ATT&CK for Enterprise

| Tactic | Description |
|--------|-------------|
| Reconnaissance | Gathering information for planning |
| Resource Development | Establishing resources for attack |
| Initial Access | Getting into the target environment |
| Execution | Running malicious code |
| Persistence | Maintaining foothold |
| Privilege Escalation | Gaining higher-level permissions |
| Defense Evasion | Avoiding detection |
| Credential Access | Stealing account credentials |
| Discovery | Learning about the environment |
| Lateral Movement | Moving through the network |
| Collection | Gathering data |
| Command and Control | Communicating with compromised systems |
| Exfiltration | Stealing data |
| Impact | Damaging systems and data |

---

## 9.4 Unified Kill Chain

### Overview

The Unified Kill Chain is a comprehensive framework designed to model and defend against cyberattacks by outlining 18 distinct stages.

### Three Main Phases

#### In Phase
1. **Reconnaissance** - Researching, identifying, selecting targets
2. **Resource Development** - Setting up necessary infrastructure
3. **Delivery** - Transmitting weaponized objects to target
4. **Social Engineering** - Manipulating individuals to perform unsafe actions
5. **Exploitation** - Exploiting vulnerabilities to gain unauthorized access
6. **Persistence** - Establishing persistent presence within system
7. **Defense Evasion** - Techniques to evade detection
8. **Command and Control** - Communicating with compromised systems

#### Through Phase
9. **Pivoting** - Tunneling traffic through compromised system
10. **Discovery** - Gaining knowledge about system and network
11. **Privilege Escalation** - Gaining higher permissions
12. **Execution** - Executing attacker-controlled code
13. **Credential Access** - Gaining access to credentials
14. **Lateral Movement** - Horizontally accessing other remote systems

#### Out Phase
15. **Collection** - Identifying and gathering data
16. **Exfiltration** - Removing data from target network
17. **Impact** - Manipulating, interrupting, destroying target system
18. **Objectives** - Achieving strategic goals

---

## 9.5 MITRE D3FEND Framework

### Overview

MITRE D3FEND (Detection, Denial, and Disruption Framework) is a cybersecurity framework that provides a structured approach to implementing defensive measures. It complements MITRE ATT&CK by guiding organizations on how to defend against attack techniques.

### Seven Main Tactics

#### 1. Model
- Focus on analyzing systems to build comprehensive understanding
- **Key techniques:**
  - Asset Inventory (D3-AI)
  - Network Mapping (D3-NM)
  - Operational Activity Mapping (D3-OAM)
  - System Mapping (D3-SYSM)

#### 2. Harden
- Increase opportunity cost of exploitation
- **Key techniques:**
  - Application Hardening (D3-AH)
  - Credential Hardening (D3-CH)
  - Message Hardening (D3-MH)
  - Platform Hardening (D3-PH)

#### 3. Detect
- Identify suspicious activities and potential breaches
- **Key techniques:**
  - File Analysis (D3-FA)
  - Identifier Analysis (D3-ID)
  - Message Analysis (D3-MA)
  - Network Traffic Analysis (D3-NTA)
  - Platform Monitoring (D3-PM)
  - Process Analysis (D3-PA)
  - User Behavior Analysis (D3-UBA)

#### 4. Isolate
- Create logical or physical barriers
- **Key techniques:**
  - Execution Isolation (D3-EI)
  - Network Isolation (D3-NI)

#### 5. Deceive
- Create environment that misleads adversaries
- **Key techniques:**
  - Decoy Environment (D3-DE)
  - Decoy Object (D3-DO)

#### 6. Evict
- Remove adversaries from network
- **Key techniques:**
  - Credential Eviction (D3-CE)
  - File Eviction (D3-FEV)
  - Process Eviction (D3-PE)

#### 7. Restore
- Recover access and restore objects
- **Key techniques:**
  - Restore Access (D3-RA)
  - Restore Object (D3-RO)

---

## 9.6 Diamond Model of Intrusion Analysis

### Overview

The Diamond Model provides a systematic approach to analyzing cyber intrusions by focusing on four core components.

### Four Core Components

| Component | Description |
|-----------|-------------|
| **Adversary** | Entity or individual responsible for attack |
| **Victim** | Target of the attack |
| **Capability** | Tools and techniques used to execute attack |
| **Infrastructure** | Resources and networks used to carry out attack |

### Meta-Features

| Feature | Description |
|---------|-------------|
| Timestamp | Time and date of event |
| Phase | Progress of attack |
| Result | Outcome of event |
| Direction | How adversary was routed to victim |
| Methodology | Technique used by adversary |
| Resource | External resources used |

---

## 9.7 Kill Chain Deep Dive - Spear Phishing Scenario

| Phase | Scenario | Use Cases |
|-------|----------|-----------|
| Reconnaissance | Employee posts information on social media; adversary gathers contact details | Social media monitoring |
| Weaponization | Creates malware payload; prepares C2 and drop-zone servers; drafts phishing email | AV evasion techniques |
| Delivery | Sends phishing email; email passes through AV protection | Suspicious attachment, suspicious file type |
| Exploitation | Employee opens attachment; executes malicious file; exploits vulnerability | Malware infection, execution of non-whitelisted program |
| Installation | Malware establishes persistence; sends signal to C2; spreads infection | Suspicious proxy activity, new program execution |
| Command and Control | Obtains password hashes; establishes C2 channel; performs remote exploitation | C2 blacklist, domain access, protocol vulnerabilities |
| Actions on Objectives | Searches for files; collects and encrypts files; transfers to drop-zone | Admin privilege usage, RAR file detection |

---

## 9.8 Gaining Knowledge Through Hacking Forums

### Purpose

Hacking forums provide information related to:
- Methods used to launch attacks
- Techniques and tools used to perform attacks
- Procedures followed for covering tracks

### Popular Hacking Forums

- Hack Forums (https://hackforums.net)
- Hackaday (https://hackaday.com)
- The Ethical Hacker Network (https://www.ethicalhacker.net)
- Hack This Site (https://www.hackthisite.org)
- Hak5 Forums (https://forums.hak5.org)
- Evil Zone (https://evilzone.org)
- Hack In the Box (http://www.hitb.org)
- The Hacker News (https://thehackernews.com)
- 0x00sec (https://0x00sec.org)
- Exploit Database (https://www.exploit-db.com)
- Packet Storm (https://packetstormsecurity.com)

---

## 9.9 NIST Cybersecurity Framework 2.0

### Overview

The NIST Cybersecurity Framework (CSF) is a comprehensive tool developed by the National Institute of Standards and Technology to help organizations enhance their cybersecurity programs.

### Six Core Functions

| Function | Description |
|----------|-------------|
| **Govern (GV)** | Defines and conveys organization's cybersecurity risk management strategy, expectations, and policy |
| **Identify (ID)** | Comprehend organization's existing cybersecurity risks |
| **Protect (PR)** | Put measures in place to manage cybersecurity risks |
| **Detect (DE)** | Identify and examine potential cybersecurity attacks and breaches |
| **Respond (RS)** | Respond to detected cybersecurity incidents |
| **Recover (RC)** | Recover assets and operations impacted by a cybersecurity incident |

---

# PART 10: MODULE SUMMARY

## Key Takeaways

### Cyber Threats
- Cyber threats involve attempts to gain unauthorized network access by exploiting vulnerabilities
- Three components: Intent, Capability, Opportunity
- Various attack vectors: cloud threats, APTs, viruses, worms, ransomware, mobile threats, botnets, insider threats, phishing, web application threats, IoT threats

### TTPs
- Tactics: Guidelines describing how attacker performs attack from beginning to end
- Techniques: Technical methods used to achieve intermediate results
- Procedures: Organizational approaches followed to launch attack

### Network Attacks
- Reconnaissance attacks gather detailed network information
- Network scanning, port scanning, DNS footprinting
- Sniffing, MITM attacks, password attacks
- Privilege escalation, DNS poisoning, ARP poisoning
- DHCP starvation, DHCP spoofing, MAC spoofing
- DoS and DDoS attacks
- Malware attacks (virus, Trojan, adware, spyware, rootkit, backdoor, ransomware)
- APTs and supply chain attacks

### Host Attacks
- Malware infections, data deletion, unauthorized access
- Brute force attacks, privilege escalation
- Host-based DoS, spyware, ransomware

### Application Attacks
- SQL injection, XSS, parameter tampering
- Directory traversal, CSRF
- Application-level DoS, cookie poisoning, session fixation
- OWASP Top 10 vulnerabilities

### Social Engineering
- Impersonation, eavesdropping, shoulder surfing
- Dumpster diving, piggybacking, tailgating, reverse social engineering

### Email Attacks
- Phishing, malicious attachments, malicious redirection, spamming

### Insider Attacks
- Malicious, negligent, and compromised insiders
- Data theft, policy violations, fraud, sabotage, espionage

### IoCs
- Atomic, computed, and behavioral indicators
- Network, host, application, social engineering, email, and insider attack IoCs

### Hacking Methodologies
- EC-Council: Reconnaissance, Scanning, Gaining Access, Maintaining Access, Clearing Tracks
- Cyber Kill Chain: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, C2, Actions on Objectives
- MITRE ATT&CK: 14 tactics for Enterprise
- Unified Kill Chain: 18 phases across In, Through, Out
- MITRE D3FEND: 7 defensive tactics (Model, Harden, Detect, Isolate, Deceive, Evict, Restore)
- Diamond Model: Adversary, Victim, Capability, Infrastructure
- NIST CSF 2.0: Govern, Identify, Protect, Detect, Respond, Recover

---
