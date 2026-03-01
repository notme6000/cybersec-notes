## Classification of Network Ports

Network ports are logical communication endpoints used by transport layer protocols such as TCP and UDP to identify specific processes or services on a device. Port numbers range from **0 to 65535** and are classified into three main categories.



### 1. Well-Known Ports (0–1023)

* Also called **system ports**
* Reserved for widely used and standardized services
* Managed by the Internet Assigned Numbers Authority (IANA)
* Typically require administrative or root privileges to use

**Examples:**

* Port 20/21 – FTP (File Transfer Protocol)
* Port 22 – SSH (Secure Shell)
* Port 23 – Telnet
* Port 25 – SMTP (Simple Mail Transfer Protocol)
* Port 53 – DNS (Domain Name System)
* Port 80 – HTTP (Hypertext Transfer Protocol)
* Port 443 – HTTPS (Secure HTTP)



### 2. Registered Ports (1024–49151)

* Assigned to user processes or specific applications
* Can be registered with IANA
* Used by application software and proprietary services

**Examples:**

* Port 1433 – Microsoft SQL Server
* Port 1521 – Oracle Database
* Port 3306 – MySQL
* Port 3389 – Remote Desktop Protocol (RDP)
* Port 8080 – Alternative HTTP



### 3. Dynamic / Private / Ephemeral Ports (49152–65535)

* Also called **ephemeral ports**
* Not assigned to specific services
* Temporarily used by client applications
* Automatically allocated by the operating system during communication sessions

**Example:**

* When a web browser connects to a server on port 80, the client system assigns a temporary port (e.g., 52345) for the session.



## Classification Based on Protocol

Ports are also classified based on the transport protocol:

### TCP Ports

* Connection-oriented
* Reliable data transfer
* Example: HTTP (Port 80), HTTPS (Port 443)

### UDP Ports

* Connectionless
* Faster but less reliable
* Example: DNS (Port 53), DHCP (Port 67/68)



## Summary Table

| Port Range  | Category          | Usage Type                            |
| -------- | ----------------- | ------------------------------------- |
| 0–1023      | Well-Known Ports  | Standard system services              |
| 1024–49151  | Registered Ports  | User or application-specific services |
| 49152–65535 | Dynamic/Ephemeral | Temporary client-side communication   |



## Key Points

* A port number combined with an IP address forms a socket.
* Ports allow multiple services to run on a single device simultaneously.
* Firewalls use port numbers to filter traffic.
* Proper port management enhances network security.


