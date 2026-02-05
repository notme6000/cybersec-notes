
| sub-topic | content                                                    |
| --------- | ---------------------------------------------------------- |
| 21        | [Pretexting (Identity Theft)](#Pretexting(Identity-Theft)) |
| 22        | [Vulnerability Exploitation](#Vulnerability-Exploitation)  |
| 23        | [Mistakes & Errors](#Mistakes-&-Errors)                    |
| 24        | [Malwares](#Malwares)                                      |


---

## Pretexting(Identity-Theft)

- Social engineering attack
- A Pretexting attack occurs when an attacker pretends to be a trusted person or authority (IT support, bank staff, manager, police, etc.) and uses that false identity to manipulate the victim into giving confidential information.

- __How the attack is done__
    1. Attacker research the target (company, role, contacts)
    2. Create a convincing scenarios (the pretext)
    3. Contacts the victim via phone, email, or message
    4. Gains trust using authority, urgency, or fear
    5. Extracts information or convinces the victim to act

- __How it works__
    - Humans tens to trust:
        - Authority figures
        - Familiar process
        - Urgent requests
    - Pretexting exploits psychology, not software bugs
    - Often combined with
        - Phishing
        - Stolen credentials
        - Insider-style access

- __Common Pretexting scenarios__
    - "I'm from IT, I need your login to fix an issue"
    - "This is the bank verify your account now"
    - "Police investigation confirm employee details"

- __Real-World Attack Examples__
    - _help-desk pretexting_
        - Attacker poses as an employee
        - Requests password reset from IT support
    - _Corporate data theft_
        - Fake auditor requests employee or financial records
        - Company unknowingly leaks sensitive data
    - _Banking & call center scams_
        - Attacker impersonate bank officials
        - Victims reveal account details or OTPs

- __Prevention / Defense__
    - Verify identity through official channels
    - Never share passwords or OPTs
    - Security awareness training
    - Least-privilege access
    - Clear verification procedures

---

## Vulnerability-Exploitation 

- Vulnerability exploitation occurs when an attacker identifies and uses a system flaw or security weakness to compromise confidentiality, integrity, or availability

- __How the attack is done__
    1. Reconnaissance
        - Scan the system/network for weakness
        - Identify outdated software or misconfiguration
    2. Find a Vulnerability
        - unpatched software
        - weak passwords
        - open ports
        - coding errors
    3. Exploit the weakness
        - Run malicious code 
        - inject commands
        - Escalate privilege
    4. Gain Access or control
        - install Malwares
        - steal data
        - disrupt services

- __How it works__
    - Every system has potential security flaws
    - if not patched or properly configured, attackers can:
        - execute arbitary code
        - bypass authentication
        - escalate privilege
    - Exploit are often automated using:
        - exploit kits
        - pre-written scripts
        - public exploit databases

- __Types of Vulnerability executed__
    - _software bugs_ (buffer overflow, SQL injection)
    - _zero-day vulnerabilities (unknown to vendor)_ 
    - _Misconfiguration_
    - _Weak authentication mechanisms_
    - _outdated systems_ 

- __Real-World Attack Examples__
    - _wannacry ransomware (2017)_
        - exploited a windows SMB vulnerability
        - Spread rapidly across networks
    - _Equifax Data Breach (2017)_
        - Exploited an unpatched web application vulnerability
        - millions of records exposed
    - _log4shell_
        - Exploited a critical logging librarey vulnerability 
        - Allowed remote code execution

- __Prevention / Defense__
    - regular patch management
    - vulnerability scanning
    - penetration testing
    - proper system configuration
    - princliple of least privilege

---

## Mistakes-&-Errors 

- __How the attack is done__
    - Mistakes and errors are accidental actions, misconfiguration, or oversighs by users, administrators, or developers that result in security vulnerabilities or system failures 

- __How they happen__ 
    - lack of awareness
    - misconfiguration of systems
    - poor coding practices
    - negligence
    - weak password choices
    - failure to apply security patches

- __How they lead to security problems__
    1. A user or admin makes an error 
    2. A vulnerability is introduced
    3. The system becomes exposed 
    4. Attackers detect and exploit the weakness

- __Common types of security mistakes & errors__
    - _Human errors_
        - click phishing links
        - sending sensitive data to wrong recipient
        - Using weak passwords
    - _Configuration Errors_
        - open database exposed to the internet
        - misconfigured cloud storage (public access enabled)
    - _software development errors_
        - coding bugs (buffer overflow, injection flaws)
        - Improper input validation
    - _Operational Errors_
        - not updating systems
        - poor backup management

- __Real-World Attack Examples__
    - _Misconfiguration cloud storage_
        - public accessible cloud buckets exposing sensitive data
    - _Equifax Breach (2017)_
        - Failure to patch known vulnerability
    - _Accidental data leaks_
        - employee emails confidential data to wrong person

- __Prevention / Defense__
    - security awareness training
    - regular patching and updates
    - strong configuration management
    - code reviews and testing
    - access control policies

---

## Malwares (Malicious Software) 

- Malware is any software intentionally designed to damage, disrupt, steal data, or gain unauthorized access to computer systems.

- __Types of Malware__
    1. _Virus_   
        - A virus is malware that attaches itself to a legitimate file or program and spreads when the file is executed.
        - _how it spreads_
            - infected files 
            - USB drives
            - Email attachments
        - _Example_ : 
            - ILOVEYOU virus
    2. _Worm_
        - A worm is self-replicating malware that spreads authomatically accross networks without user interaction
        - _How it spreads_ 
            - Network vulnerabilities
        - _Example_:
            - [wannacry](https://en.wikipedia.org/wiki/WannaCry_ransomware_attack)
    3. _Trojan horse_
        - A trojan disguises itself as legitimate software but contains malicious code.
        - _how it works_
            - user installs fake software
            - malware execute in background
        - _Example_ : 
            - fake anitivirus software 
    4. _Ransomware_
        - Encrypts files and demands payment for decryption
        - _Example_
            - [wannacry](https://en.wikipedia.org/wiki/WannaCry_ransomware_attack)
            - [cryptolocker](https://en.wikipedia.org/wiki/CryptoLocker)
    5. _Spyware_
        - secretly monitors user activity and colletcs information
        - _What is steals_
            - passwords
            - browsing habits
            - credit card info
        - _Example_ : 
            - [pegasus spyware](https://en.wikipedia.org/wiki/Pegasus_(spyware))
    6. _Adware_ 
        - Displays unwanted advertisements and may track user behavior.
        - _Example_ : 
            - browser pop-up ad software
    7. _Rootkit_
        - Designed to hide malware and maintain privilege access to a system
        - _Purpose_ :
            - Avoid detection
            - Maintain long-term control
    8. _Keylogger_
        - Records keystrokes to steal passwords and sensitive information
        - _Example_
            - banking credentials thefi malware
    9. Bot / Botnet
        - Infected computer becomes part of a network controlled by attacker
        - _used for_
            - DDoS attacks
            - Spam campaigns
        - _Example_ :
            - [mirai botnet](https://en.wikipedia.org/wiki/Mirai_(malware)) 
    10. Logic Bomb
        - Malicious code that activates when a specific condition is met.
        - _Example_ : 
            - Activates when employee is terminated


---


