# 1. What Active Directory Actually Is

Active Directory (AD) is Microsoft’s identity and access management system used in Windows domain environments.

It provides:

* Authentication (via Kerberos / NTLM)
* Authorization (Group memberships, ACLs)
* Centralized policy enforcement (Group Policy)
* Directory services (LDAP)
* Trust relationships between domains

### Core Components

* **Domain Controller (DC)** – Hosts AD database (NTDS.dit)
* **Kerberos** – Default authentication protocol
* **LDAP** – Directory querying protocol
* **SYSVOL** – Stores policies and scripts
* **Group Policy Objects (GPOs)** – Configuration enforcement
* **Trusts** – Cross-domain authentication paths



# 2. Why Active Directory Is So Frequently Attacked

Active Directory is targeted because:

1. It centralizes identity.
2. Compromising it equals full domain control.
3. It is often poorly segmented.
4. Legacy protocols (NTLM, SMBv1) still exist.
5. Misconfigurations are extremely common.

Once an attacker controls AD, they control:

* All users
* All servers
* All endpoints
* All authentication flows



# 3. Active Directory Attack Lifecycle

Most AD attacks follow this progression:

1. Initial foothold
2. Local privilege escalation
3. Credential harvesting
4. Lateral movement
5. Privilege escalation (domain level)
6. Persistence
7. Domain dominance



# 4. Core Attack Techniques



## 4.1 Credential Dumping

Goal: Extract hashes or plaintext passwords from memory or disk.

Targets:

* LSASS memory
* SAM database
* NTDS.dit file

Common techniques:

* Mimikatz-style memory extraction
* DCSync replication abuse
* Volume shadow copy extraction

Why it works:

* Windows stores credentials in memory
* Domain controllers replicate password hashes



## 4.2 Pass-the-Hash (PtH)

Instead of cracking passwords, attackers use NTLM hashes directly to authenticate.

Mechanism:

* NTLM hash acts as the credential
* No need for plaintext password

Impact:

* Enables lateral movement across systems
* Very difficult to detect without strong monitoring



## 4.3 Pass-the-Ticket (PtT)

Abuses Kerberos tickets instead of NTLM hashes.

Attacker:

* Extracts Kerberos Ticket Granting Ticket (TGT)
* Reuses it to authenticate as the victim



## 4.4 Kerberoasting

Targets service accounts.

How it works:

1. Request service ticket for SPN
2. Extract encrypted ticket
3. Crack offline to recover service account password

Why it works:

* Service accounts often use weak passwords
* Tickets are encrypted with service account key



## 4.5 AS-REP Roasting

Targets accounts with:

* “Do not require Kerberos pre-authentication” enabled

Attacker:

* Requests AS-REP
* Gets encrypted blob
* Cracks offline



## 4.6 Golden Ticket Attack

Attacker forges a Kerberos TGT.

Requirements:

* KRBTGT account hash

Impact:

* Full domain persistence
* Can impersonate any user
* Valid until KRBTGT password is reset twice



## 4.7 Silver Ticket Attack

Attacker forges a service ticket (TGS).

Requirements:

* Service account hash

Impact:

* Access to specific services
* Harder to detect than Golden Tickets



## 4.8 DCSync Attack

Abuses replication privileges.

If attacker has:

* Replicating Directory Changes permission

They can:

* Request password hashes for any user
* Mimic domain controller behavior

This does not require domain controller login.



## 4.9 ACL Abuse & Privilege Escalation

Active Directory permissions are complex.

Attackers exploit:

* WriteDACL
* WriteOwner
* GenericAll
* GenericWrite
* AddMember
* ForceChangePassword

These can allow:

* Adding self to Domain Admins
* Resetting privileged passwords
* Taking ownership of objects



## 4.10 AdminSDHolder Abuse

AdminSDHolder protects privileged accounts.

If attacker modifies:

* AdminSDHolder ACL

They can:

* Grant themselves persistent elevated rights



## 4.11 Resource-Based Constrained Delegation (RBCD)

Modern lateral movement technique.

Attacker:

1. Creates or compromises machine account
2. Modifies delegation settings
3. Impersonates privileged user to target system

Very common in modern red team operations.



## 4.12 NTLM Relay

Abuses lack of SMB signing or LDAP signing.

Attacker:

* Captures authentication attempt
* Relays it to another service
* Gains authenticated session

Often combined with:

* Printer bug
* PetitPotam
* Coerced authentication



# 5. Active Directory Enumeration

Before attacks, enumeration happens.

Tools commonly used:

* BloodHound (relationship mapping)
* LDAP queries
* PowerShell AD modules
* SharpHound

Enumeration reveals:

* Privileged users
* Kerberoastable accounts
* Misconfigured ACLs
* Trust relationships
* Attack paths to Domain Admin



# 6. Domain Trust Abuse

If forests or domains trust each other:

Attacker can:

* Escalate across trust
* Abuse SID History
* Exploit weak trust configurations

Forest-level compromise is catastrophic.



# 7. Persistence Mechanisms in AD

Attackers maintain access via:

* Golden tickets
* AdminSDHolder backdoors
* Shadow credentials (certificate abuse)
* Skeleton key malware
* Malicious GPO
* DCShadow attack (fake domain controller registration)



# 8. Detection Challenges

AD attacks are hard to detect because:

* They often use legitimate protocols
* Many attacks don’t drop malware
* Logging is insufficient by default
* Kerberos abuse appears normal

Critical logs:

* 4624 (logon)
* 4672 (special privileges)
* 4768 / 4769 (Kerberos activity)
* 4662 (directory replication)



# 9. Defensive Architecture Against AD Attacks



## 9.1 Tiered Administration Model

Tier 0:

* Domain Controllers
* AD admin accounts

Tier 1:

* Servers

Tier 2:

* Workstations

Never mix credentials across tiers.



## 9.2 Least Privilege Enforcement

* Remove unnecessary Domain Admins
* Avoid using DA for daily tasks
* Separate admin accounts
* Disable legacy protocols



## 9.3 Kerberos Hardening

* Enforce AES only
* Rotate KRBTGT regularly
* Disable unconstrained delegation
* Monitor SPN changes



## 9.4 NTLM Mitigation

* Disable NTLM where possible
* Require SMB signing
* Enforce LDAP signing
* Block unsigned relays



## 9.5 Credential Protection

* Enable Credential Guard
* Enable LSA Protection
* Use Protected Users group
* Avoid service account passwords (use gMSA)



## 9.6 Monitoring & Detection

Deploy:

* SIEM
* Advanced threat detection
* Directory change monitoring
* Attack path analysis tools

Watch for:

* Unusual replication requests
* TGT anomalies
* Service ticket volume spikes
* ACL modifications



# 10. Modern Hybrid AD Risks

With Azure AD / Entra ID sync:

New risks:

* Compromised sync account
* Pass-through authentication abuse
* Cloud-to-on-prem escalation

Hybrid identity expands attack surface.



# 11. Red Flags That AD Is Compromised

* Unknown admin accounts
* KRBTGT not rotated in years
* Domain controllers accessible from workstations
* Unmonitored LDAP traffic
* Multiple SPNs on user accounts
* Service accounts with weak passwords



# 12. Practical Learning Path (If You’re Studying AD Attacks)

To truly understand AD attacks:

1. Build a lab domain
2. Practice attack simulations
3. Study Windows internals
4. Learn Kerberos deeply
5. Understand ACL inheritance
6. Analyze event logs
7. Study real breach case studies



# Final Reality Check

Active Directory security is not about:

* Patching alone
* Antivirus alone
* Firewall alone

It is about:

* Identity architecture
* Privilege boundaries
* Protocol hardening
* Monitoring behavior, not signatures

If AD falls, everything falls.



If you want, I can next provide:

* A visual attack flow map
* A defensive checklist for blue teams
* A red team vs blue team comparison
* A lab setup blueprint
* A deep dive into Kerberos internals
* Real-world breach breakdown

Tell me which direction you want to go.

