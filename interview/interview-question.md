### **Networking Fundamentals (The Backbone)**

1.  Explain the OSI model and its layers.

	- The OSI ( open systems interconnection ) model is a conceptual framework used to understand how network protocols and communications work. It was developed by the international Organization for Standardization ( ISO ) in the 1980s.
	- It is a universal rulebook or a blueprint that standardizes the functions of a telecommunication or computing system into seven distinct, abstract layers.Each layer has a specific job and serves the layer above it, while receiving services from the layer below it.
	- __7 layers of osi model__
		- "all people seem to need data processing"
			- application
			- presentation
			- session
			- transport
			- network
			- data link
			- physical	
			-  __Layer 7 : Application Layer__
				- layer that  users and applications interact with directly.
				- provides network services to the end-user applications ( like your web browser or email client ).
				- __function__: Provides interfaces and services for applications to access the network.
					- It's not the application itself, but the services it uses ( eg: HTTP for web browsing, SMTP for email, FTP  for file transfer).
				- __key protocols__: HTTP, HTTPS, FTP, SMTP, DNS
			- __Layer 6 : Presentation Layer__
				- This layer acts as the translator for the network. It ensures that the data sent from the application layer of one system is readable by the application layer of another system.
				- __function :__ Responsible for data translation, encryption and compression.
					- translation : converting between different data fromats ( eg : ASCII to Unicode )
					- encryption : securing data using protocols like SSL/TLS
					- compression : Reducing the number of bits needed to represent the data.
				- __key protocols:__ SSL/TLS ( for encryption ), JPEG, MPEG.
			- __Layer 5 : session Layer__
				- This layer is the "dialog controller" It establishes, manages, and terminates connections ( sessions ) between applications.
				- __function__ : Controls the dialogues ( sessions ) between computers. It sets up, coordinates and terminates the conversations, exchanges, and dialogues between the applications at each end.
				- __Key protocols :__ NetBIOS, RPC
			- __Layer 4 : Transport Layer__
				- This Layer is responsible for end-to-end communication and data transfer between the two end systems ( eg: your laptop and web server )
				- __Function :__ manages teh reliability of communication
					- segmentation : Breaking down data from the session layer into smaller pieces called segments.
					- flow control : ensures the sending device does not overwhelm the receiving device.
					- error control : uses acknowledgements and retransmissions to ensure all segments are received correctly ( in TCP ).
					- __Key Protocols :__ TCP ( transmission control protocol - connection oriented and reliable ) and  UPD ( user datagram protocl - connectionless and fast )
			- __Layer 3 : Network Layer__
				- This layer is responsible for logical addressing and path determination- essentially, getting data from one network to another.
				- __Funcion__
					- Logical Addressing : Assigns IP addresses to packets.
					- Routing : Determines the best path across the network to forward the packets. Routers operate at this layer.
					- Packet Forwarding : Takes the segments from the Transport Layer and encapsulates them into packets.
				- __Key Protocols :__ IP ( IPv4, IPv6), ICMP, ROUTERS.
			- __Layer 2 : Data Link Layer__
				- This layer is responsible for node-to-node data transfer and error detection on the same physical network segments (e.g., within the same LAN )
				- __Funcion__
					- Physical Addressing : Adds the source and destination MAC (Media Access Control)addresses to the data, creating a frame.
					- Error Detection : Checks for errors in the transmitted frames using methods like CRC (Cyclic Redundancy Check)
					- Access Control : Controls which device has access to the network medium at any given time (e.g., CSMA/CD)
				- __Key Devices :__ Switches, Bridges.
			- __Layer 1 : Physical Layer__
				- This is the lowest layer and deals with the physical connection between devices. It defines the electrical, mechanical, and procedural ascpects of the physical network.
				- __Funcion__
					- Transmits raw, unstructured bit streams (1s and 0s) over the physical medium. It defines characteristics like:
						- voltages, cable specifications, data rates, maximum transmission distances.
						- connectors, pin layouts, and hubs and repeater functionality.
				- __key devices :__ Hubs, Repeaters, Cables, Network Interface Cards (NICs).

---

2.  What is the TCP/IP model? How does it differ from the OSI model?

	- Certainly. The TCP/IP model, also known as the Internet Protocol Suite, is the conceptual model that the actual internet is built on. It's not just a theoretical framework: it's the set of rules that govers modern internet communication.
	- While the OSI model has seven layers, the TCP/IP model is condensed into four layers:
		1. __Application Layer__ : This is a combination of the OSI's Application, Presentation, and Session layers. It handles high-level protocols like HTTP for web browsing, SMTP for email, and DNS for domain name resolution. Essentially, it's where the network applications operate.
		2. __Transport Layer :__ This maps directly to the OSI transport layer. Its job is end-to-end communication and data flow. The two key protocols here are TCP, which is connection-oriented and reliable, and UDP, which is connectionless and faster.
		3. __Internet Layer__ : This corresponds to the OSI Network Layer. Its core function is logical addressing and routing-getting packets from the source network to the destination network. The star protocol here is the Internet Protocol, or IP.
		4. __Network Access Layer (or Link Layer) :__ This is a fusion of the OSI's Data Link and Physical Layers. It's concerned with the physical transmission of data over the network medium, like Ethernet or Wi-Fi. It deals with hardware addressing and getting data onto the local network.

---

3.  What are the differences between TCP and UDP? Give an example of a protocol that uses each.

	- The primary difference lies in their approach to reliablility and connection management. We can think of TCP like registered, tracked courier service, and UDP like standard, first-class mail.
	- __TCP__
		- __TCP (Transmission Control Protocol)__ is connection-oriented. This means it establishes a formal connection using a three-way handshake before any data is sent. 
			- __Reliability__ : It guarantees delivery. It uses acknowledgements and retransmissions to ensure all data packets arrive.
			- __Ordering :__ It sequences the data packets so they are reassembled in the correct order at the destination.
			- __Error Checking__ : It has robust error-checking to confirm data integrity.
			- __Flow Control :__ It manages the data flow to prevent overwhelming a slower receiver.
		- Because of this, TCP is heavier, with more overhead due to all the built-in control mechanisms.
		- A classic example of a protocol that uses TCP is HTTP/HTTPS. When you load a website, you need every part of the page-the HTML, the images, the code-to arrive completely and in the correct order. A missing or out-of-order piece would break the page.
	- __UDP__
		- __UDP (User Datagram Protocol)__ is connection-less. It sends data without establishing a prior connection. Its characteristics are:
			- __Speed :__ It has much lower latency and overhead because it forgoes the handshake, acknowledgements, and sequencing. 
			- __No Guaranteed Delivery :__ It's a "fire-and-forget" protocol. It will send the data, but won't check if it arrived.
			- __No Ordering :__ Packets can arrive out of order.
			- __Efficiency :__ It's lightweight, making it ideal for applications where speed is more critical than perfect accuracy.
		- A prime example of a protocol that uses UDP is DNS (Domain Name System). When your computer asks a DNS server for the IP address of "google.com," it's a very short, single request. It's faster to send a quick UDP packet and hope for a reply than to set up a full TCP connection for such a small query. If the request gets lost, it will simply time out and be retried.

---

4.  What is the three-way handshake in TCP?
	- The three-way handshake is a three-step process that two computers use to establish a reliable TCP connection before they start transmitting actual data. It's like a formal introduction and agreement to talk before starting a important conversation.
	- The three step are
		1. __SYN (Synchronize) :__ The client who wants to initiate a connection sends a TCP packet to the server with a special flag called SYN set to 1. This is essentially the client saying, "Hello, server. Are you open to a new? My initial sequence number is X." 
		2. __SYN-ACK (Synchronize-Acknowledge) :__ The server, if it's open and accepting connections, responds with a packet that has two flags set: SYN and ACK. This means: "Hello, client. I acknowledge your request(ACK)". I am open for a connection. My initial sequence number is Y."
		3. __ACK (Acknowledge) :__ Finally, the client sends an ACK packet back to the server. This confirms the server's sequence number. It's the client saying, "Great! I acknowledge you. Let's start transmitting data.". 

---

5.  Explain what ARP (Address Resolution Protocol) is and its purpose.
	- __ARP, of Address Resolution Protocol__, is a critical layer 2 protocol used to map a known IP address to an unknown MAC address on a local area network (LAN).
	- Its core purpose is to resolve a logical Layer 3 address (the IP address) into a physical Layer 2 address (the MAC address). This is necessary because for two devices to communicate on the same local network segment, the data must be encapsulated in a frame that uses MAC addresses for delivery, even if the application started with just an IP address.
	- __The process__
		1. A host checks its local ARP cache to see if it already has the mapping.
		2. If not, it broadcasts an ARP Request packet to the entire local network, asking, in essence, "who has IP address 192.168.1.5? Please tell me your MAC address."
		3. Only the device with that specific IP address will respond with a unicast ARP Reply containing its MAC address.
		4. The original host then stores this mapping in its ARP cache for future communication and can now correctly address the data link layer frames.

---

6.  What is a DNS and how does it work?
	- __DNS or Domain Name System, is essentially the phonebook of the internet__. It's a distributed, hierarchical database that translate human-friendly domain names, like "google.com", into machine-readable IP addresses, like "142.251.42.46", which are necessary to locate and connect to web servers.
	- __How DNS works__
		1. __User Request__ : A user types a domain name (e.g., www.google.com) into their browser. The browser first checks its own cache and the local operating system's hosts file to see if it already knows the corresponding IP address.
		2. __Recursive Resolver__ : If the answer isn't cached locally, the query is sent to a __Recursive Resolver__. This is typically a server operated by the user's Internet Service Provider (ISP). The resolver acts like a librarian who does the legwork of finding the answer for you.
		3. __Root Name Server :__ The recursive resolver doesn't know the answer either, so it first queries one of the 13 logical __Root Servers.__ There servers don't have the final answer but know where to direct the query for the top-level domain (TLD)- in this case, for `.com`. The root server responds with the address of a TLD name server for `.com`.
		4. __TLD Name Server :__ The resolver then queries the `.com` TLC server. This server manages information for all `.com` domains. It doesn't know the specific IP for `www.example.com`, but it knows the authoritative name servers for the `example.com` domain. It returns the addresses of those servers to the resolver.
		5. __Authoritative Name Server__ : Finally, the resolver queries one of the __Authoritative Name Servers__ for `example.com`. These servers hold the definitive DNS records for that specific domain. The authoritative server looks up the "A record" for `www.example.com` and returns the final IP address (e.g., `93.184.216.34`) to the recursive resolver.
		6. __Response to Client :__ The recursive resolver receives the IP address, stores it in its local cache for a period of time (defined by the TTL- Time to Live) for future requests, and then sends the final answer back to the user's operating system, which gives it to the browser.
		7. __Website Connection :__ The browser can now initiate a TCP connection to the IP address `93.184.216.34` and load the website.

---

7.  What is the difference between a router and a switch?
	- 

---
7.  Explain the concepts of IP Address, Subnet Mask, and Default Gateway.
8.  What is a VLAN and why is it used for security?
9. What is a VPN and how does it provide security?
10. What is the difference between HTTP and HTTPS?
11. What are the common TCP and UDP port numbers for services like SSH, FTP, DNS, HTTP, HTTPS, and RDP?
12. What is a MAC address and how is it different from an IP address?
13. What is a DDoS attack and how does it work from a network perspective?
14. What is a Man-in-the-Middle (MitM) attack?

### **Core Cybersecurity Concepts**

16. Explain the CIA Triad.
17. What is the difference between authentication, authorization, and accounting (AAA)?
18. What is multi-factor authentication (MFA) and why is it important?
19. What is the principle of least privilege?
20. What is defense in depth?
21. Explain the difference between a vulnerability, a threat, and a risk.
22. What is a Zero-Day vulnerability?
23. What is the difference between symmetric and asymmetric encryption?
24. Explain how public-key cryptography (like RSA) works.
25. What is a hash function? What are its properties? Name a common hashing algorithm (e.g., SHA-256).
26. What is a digital signature?
27. What is a PKI (Public Key Infrastructure)?
28. What is the difference between encoding, encryption, and hashing?
29. What is a Security Misconfiguration and why is it dangerous?
30. What is Social Engineering? Give a few examples.

### **Blue Team (Defense & Operations)**

31. What is a SIEM and what is its primary function?
32. What is an IDS? How is it different from an IPS?
33. Explain the difference between signature-based and anomaly-based detection.
34. What is a firewall and what are the different types (e.g., Stateful, Next-Gen)?
35. What is the process of incident response? Name the key phases (e.g., NIST framework).
36. What are the different types of malware (Virus, Worm, Trojan, Ransomware, Spyware)?
37. What is EDR (Endpoint Detection and Response) and how is it better than traditional antivirus?
38. What is log analysis and why is it critical for a Blue Team?
39. What is patch management and why is it a crucial security practice?
40. What is network segmentation and how does it improve security?
41. What is a honeypot?
42. What is threat intelligence and how is it used?
43. What are Indicators of Compromise (IoCs)?
44. How would you investigate a potential phishing email?
45. What is the role of a SOC (Security Operations Center) analyst?
46. What is file integrity monitoring (e.g., using tools like Tripwire)?
47. What is the concept of "Assume Breach"?
48. What is User and Entity Behavior Analytics (UEBA)?
49. What is the difference between a false positive and a false negative in alerting?
50. What are some common web application firewall (WAF) rules?

### **Red Team (Offensive Security)**

51. What are the phases of the Cyber Kill Chain?
52. What is the MITRE ATT&CK framework and why is it useful?
53. Explain the stages of a penetration test (e.g., Reconnaissance, Scanning, Gaining Access, Maintaining Access, Covering Tracks).
54. What is the difference between a penetration test and a vulnerability assessment?
55. What is OSINT and what kind of information can you gather with it?
56. What is the difference between black-box, white-box, and gray-box testing?
57. What is network scanning? What is the difference between a TCP SYN scan and a TCP Connect scan?
58. What is vulnerability scanning? Name a common tool.
59. What is Metasploit and what is its primary use?
60. What is the difference between a reverse shell and a bind shell?
61. What is password cracking? What are the different methods (dictionary, brute-force, rainbow tables)?
62. What is SQL Injection and how does it work?
63. What is Cross-Site Scripting (XSS)?
64. What is a buffer overflow attack?
65. What is privilege escalation? Difference between vertical and horizontal?
66. What is lateral movement?
67. What is pivoting?
68. What are some common ways to maintain persistence on a system?
69. What is social engineering and how is it used in a red team engagement?
70. What is the purpose of exfiltration in an attack?

### **System & Application Security**

71. What is the difference between Windows and Linux from a security perspective?
72. What is the SAM database in Windows and what does it store?
73. What are Linux file permissions (read, write, execute) and how do you change them?
74. What is the principle of "Secure by Design"?
75. What is the OWASP Top 10? Name a few items from the current list.
76. What is input validation and why is it important for application security?
77. What is a CSRF (Cross-Site Request Forgery) attack?
78. What is a DMZ (Demilitarized Zone) in network architecture?
79. What is container security? What are some best practices for securing Docker?
80. What is cloud security? What is the "Shared Responsibility Model"?

### **Cryptography & Identity**

81. What is the difference between AES, DES, and RSA?
82. What is SSL/TLS and what is it used for?
83. What happens during a TLS handshake?
84. What is a digital certificate and what does it contain?
85. What is a Certificate Authority (CA)?
86. What is the difference between salting and peppering a password hash?
87. What is OAuth and how is it used for authorization?
88. What is Single Sign-On (SSO)?
89. What is the difference between RADIUS and TACACS+?
90. What is Kerberos and how does it work for authentication in a Windows domain?

### **Governance, Risk, & Compliance (GRC)**

91. What is the difference between a policy, a standard, and a procedure?
92. What is a Business Impact Analysis (BIA)?
93. What is a Disaster Recovery Plan (DRP) and how is it different from a Business Continuity Plan (BCP)?
94. What is Risk Management? Explain the process of identifying, assessing, and treating risk.
95. What are security frameworks? Name a few (e.g., NIST CSF, ISO 27001, CIS Controls).
96. What is GDPR and why is it important?
97. What is the purpose of a Security Awareness Training program?
98. What is Third-Party Risk?
99. What is the difference between qualitative and quantitative risk analysis?
100. What is an SLA (Service Level Agreement) and an MOU (Memorandum of Understanding)?

