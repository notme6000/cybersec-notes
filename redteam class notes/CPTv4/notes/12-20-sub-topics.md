
| sub-topic no.| content                                     |
|--------------|---------------------------------------------|
| 13           | [Eavesdropping](#Eavesdropping)             |
| 14           | [Replay attack](#Replay-attack)             |
| 15           | [Man-In-The-Middle](#Man-In-The-Middle)     |
| 16           | [Session Hijacking](#Session-Hijacking)     |
| 17           | [Drive by download](#Drive-by-download)     |
| 18           | [Ransomware](#Ransomware)                   |
| 19           | [Loss of Assets](#Loss-of-Assets)           |
| 20           | [Stolen credentials](#Stolen-Credentials)   |


---

## Eavesdropping

- Eavesdropping is a passive security attack where an attacker secretly listens to, intercepts, or monitors communication without altering it.
- Types of Eavesdropping
    - Network Eavesdropping
        - Packet sniffing
        - Monitoring Wi-Fi traffic
    - Communication Eavesdropping
        - Phone tapping
        - VoIP interception
    - Wireless Eavesdropping
        - Public Wi-Fi Monitoring
        - Bluetooth sniffing

- Real-World Examples
    - sniffing passwords on unsecured Wi-Fi
    - capturing emails sent over HTTP
    - listening to unencrypted VoIP calls    

---

## Replay-attack 

- A replay attack is a network attack where an attacker captures valid data transmissions and re-sends (replays) them later to trick a system into granting unauthorized access.

- __How the Attack is Done__
    1. Attacker eavesdrops on a network.
    2. Captures valid data (login tokens, authentication messages, session keys)
    3. Stores the captured transmissions
    4. Replays the same messages at a later time.
    5. System accepts it as genuine and grants access.

- __How it works__
    - many systems trust messages that are correctly formatted and cryptographically valid
    - If there is no timestamp, nonce, or session check, the system cannot tell:
        - whether the message is new or replayed
    - the attacker doesn"t need to know the password or key only to resend the valid data

- __Real-World Attack Examples__
    - _Wireless network authentication_
        - older Wi-Fi security protocols (e.g., WEP)
        - Attackers captured authentication packets and replayed them to give access
    - _RFID & smart cards_
        - Attacker records a valid RFID unlock signal
        - Replays it to unlock doors without the card

- __Prevention / Defense__
    - Use nonces
    - use timestamps
    - implement challenge-response authentication
    - use session IDs with expiration
    - Encryption and authentication messages

---

## Man-In-The-Middle

- A Man-In-The-Middle attack is a network attack where an attacker secretly intercepts and possibly alters communication between two parties who believe they are communication directly with each other.

- __How the Attack is Done__
    1. victim connects to a network (often public Wi-Fi)
    2. Attacker inserts themselves between the victim and the server.
    3. victim sends data -> attacker intercepts it
    4. Attacker forwards the data to the server (optionally modified)
    5. Responses from the server also pass through the attacker 

- __How it works__
    - The attacker impersonates the server to the client
    - Simultaneously impersonates the client to the server
    - Communication continues normally, but all data flows through the attacker
    - the attacker may: 
        - read sensitive data
        - modify messages
        - inject malicious content

- __Common types of MITM attacks__
    - ARP spoofing
    - DNS spoofing
    - Evil Twin Wi-Fi
    - SSL stripping

- __Real-World Attack Examples__
    - _Public Wi-Fi Attacks_
        - Attacker create a fake Wi-Fi hotspots (e.g., "Free Public Wi-Fi")
        - Users connect and unknowingly send credentials through the attacker
    - _Banking credentials Theft
        - Attackers intercept online banking sessions
        - Modify transaction details before forwarding to the banking

- __Prevention / Defense__
    - Use HTTPS with valid certificates
    - Implement TLS certificate validation
    - Avoid unsecured public Wi-Fi
    - Use VPNs
    - Enable HSTS

---

## Session-Hijacking 

- Session hijacking is an attack where an attacker takes control of a valid user sssion by stealing or prediction the session ID, allowing them to impersonate the user without knowing their login credentials.

- __How the Attack is Done__
    1. User logs in and receives a session ID
    2. Session ID is stored in cookes or URLs
    3. Attacker steals or predicts the session ID
    4. Attacker sends the requests using the stolen session ID
    5. Server treats the attacker as the legitimate user

- __How it works__
    - Web applications rely on session tokens to maintain user state
    - if a session ID is:
        - unencrypted 
        - exposed via XSS
        - reused for too long

- __Types of Session Hijacking__
    - _Passive hijacking_ : Monitoring traffic to steal session IDs
    - _Active hijacking_ : taking over and issuing commands
    - _Client-side hijacking_ : XSS stealing cookies
    - _Network-level hijacking_ : TCP session hijacking

- __Real-World Attack Examples__
    - _Public Wi-Fi cookie theft_
        - user logs into social media on open Wi-Fi 
        - Attacker captures unencrypted cookies
        - Attacker logs in as the user

    - _XSS-Based session hijacking_
        - Malicious scripts steals session cookies
        - Sends then to attacker's server

- __Prevention / Defense__
    - Use HTTPS everywhere
    - Set cookes as secure, HttpOnly, and samesite
    - Regenerate session IDs after login
    - Implement session timeouts
    - Protect against XSS 

---

## Drive-by-download 

- A drive-by download attack occurs when a user's system is infected with malware just by visiting a web page, without clicking or downloading anything intentionally

- __How the Attack is Done__
    1. Attacker compromises a legitimate website or creates a malicious one 
    2. Malicious code (javascript, exploit kit) is embedded in the webpage
    3. user visits the website
    4. Browser or plugin vulnerability is exploited
    5. Malware is silently downloaded and installed

- __How it works__
    - The attack exploits vulnerabilities in browers, plugins, or OS
    - Common targets:
        - Outdated browers
        - Flash, java, PDF readers
    - Exploit kits automatically:
        - scan the visitor's system
        - chose the right exploit
        - Deliver malware (spyware, ransomware, trojans) 

- __Types of Drive-by downloads__
    - _Zero-Click Drive-By_
        - no user action at all
        - fully automatic exploitation
    - _Click-Based Drive-By_
|        - User clicks a fake pop-up or ad 
        - Still appears legitimate
    
- __Real-World Attack Examples__
    - _Compromised Legitimate Websites_
        - Popular news or blog sites hacked
        - Visitors unknowingly infected
    - _Malvertising campaigns_
        - Malicious ads on trusted websites
        - Malware delivered via ad networks
    - _Ransomware Distribution_
        - Drive-By downloads used to install ransomware 
        - users locked out of their systems

- __Prevention / Defense__
    - Keep browsers and plugins updated
    - Disabled unnecessary plugins (Flash, java)
    - Use ad blockers
    - Enable browser sandboxing
    - user antivirus and endpoint protection

---

## Ransomware 

- A ransomware attack is a type of malware attack where an attacker encrypts a victim's data or locks their system and then demands a ransom payment in exchange for restoring access

- __How the Attack is Done__
    1. Attacker delivers ransomware via:
        - Phishing email attachments
        - Drive-by downloads
        - Malicious links
        - Exploited vulnerabilities
    2. Victims opens the file or visits a compromised site
    3. Malware installs and executes
    4. Files are encrypted using strong cryptography
    5. Ransom note is displayed demanding payment

- __How it works__
    - Ransomware generates an encryption key
    - Victim's files are encrypted (often using AES)
    - The key is encrypted with the attacker's public key (RSA) 
    - Without the attacker's private key:
        - Decryption is nearly impossible
    - Some variants also steal data defore encryption (double extrotion)

- __Real-World Attack Examples__
    - _WannaCry (2017)_
        - Exploited windows SMB vulnerabilities
        - Affected hospitals, companies, governments worldwide
    - _Colonial Pipeline Attack (2021)_
        - Disrupted fuel supply in the U.S
        - Forced shutdown of pipeline operations

- __Types of Ransomware__
    - _Crypto-ransomware_ - encrypts files
    - _Locker ransomware_ - locks system access
    - _Double extortion ransomware_ - encrypts + data theft

- __Prevention / Defense__
    - Regular offline backups
    - Email filtering & phishing awareness
    - Patch systems regularly
    - Disable macros
    - Endpoint detection and response (EDR)

---

## Loss-of-Assets

- Loss of assets is a security consequence in which data, hardware, software, money, or services are destroyed, stolen, corrupted, or made unavailable as a result of a security attack.

- __How the loss of assets is caused__ 
    1. Attackers cause asset loss through attacks such as
        - Ransomware 
        - Data breaches
        - Insider attacks
        - Physical theft
        - Sabotage or system destruction
    - _Typical Steps_
        1. Attacker gains unauthorized access
        2. Exploits vulnerabilities
        3. Steals, deletes, encrypts or damages assets
        4. Victim loses access, value, or ownership
    
- __How it works__
    - Digital assets (data, systems) depend on:
        - Storage integrity
        - Availability
        - Access control
    - Attacks compromise one or more of these
        - Deletion -> permanent data loss
        - Encryption -> temprary or permanent unavailability
        - Exfiltration -> loss of confidentiality
    - Physical assets may be lost through
        - Sabotage
        - Theft
        - Hardware damage

- __Types of Assets Lost__
    - _Information assets_ - databases, customer records
    - _Financial assets_ - money, crypto, revenue
    - _Physical assets_ - servers, laptops
    - _Operational assets_ - services, uptime
    - _Reputation_ - trust and brand value

- __Real-World Attack Examples__
    - _Ransomware Attacks_
        - File Encryption
        - Asset lost: data availability
    - _Insider Data Deletion_
        - Employee deletes critical databases
        - Asset lost: information & operational continuity
    - _Cloud storage breach_ 
        - Sensitive data stolen or leaked
        - Asset lost: confidentiality information

- __Prevention / Defense__
    - Regular backups (offline & immutable)
    - Strong access controls
    - Monitoring and logging
    - Employee awareness
    - Incident response plans

---

## Stolen-Credentials

- Stolen credentials refer to a security attack where attackers obtain legitimate authentication information and use it to access systems, applications, or networks as a authorized user. 

- __How the Attack is Done__
    1. Attacker targets users or systems 
    2. credentials are stolen using: 
        - Phishing emails
        - Malware / keyloggers
        - Fake login pages
        - Data breaches
    3. Attacker collects username & passwords
    4. Stolen credentials are used to log in 
    5. Attackers accesses data, services, or systems

- __How it works__
    - Most systems rely on credentials for authentication
    - if credentials are:
        - reused across services
        - weak 
        - not protected by MFA
    - the system cannot distinguish the attacker from the real user
    - Attackers may automate login attempts (credential stuffing)

- __Common ways credentials are stolen__
    - _Phishing_ : fake emails and websites
    - _Keyloggin malware_ : records keystrokes
    - _Data breaches_ : leaked password databases
    - _Man-in-the-middle attacks_
    - _Social engineering_

- __Real-World Attack Examples__
    - _Large-Scale Data breaches_
        - Stolen username and passwords sold online
        - Used in further attacks
    - _Credential stuffing attacks_
        - Attackers use leaked credentials
        - automatically try them on banking, email, social media sites

- __Prevention / Defense__
    - enable Multi-Factor Authentication (MFA)
    - Use strong, unique, passwords
    - Password managers
    - Phishing awareness training
    - Monitor for unusual login behavior



