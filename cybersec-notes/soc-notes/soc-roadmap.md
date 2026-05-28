
# SOC Analyst Roadmap (Beginner → Advanced)

## 1. Computer & Networking Fundamentals

Before SOC, you need strong basics.

### Operating Systems

* Windows internals

  * Processes, services, registry
  * Event Viewer
  * Active Directory basics
  * PowerShell
* Linux fundamentals

  * File permissions
  * Systemd/services
  * Bash scripting
  * Log files
  * Networking commands

### Networking

* OSI Model
* TCP/IP
* DNS
* HTTP/HTTPS
* DHCP
* VPN
* SSH
* SMB
* Email protocols (SMTP, IMAP, POP3)

### Practical Skills

* Wireshark
* tcpdump
* netstat / ss
* nmap

### Learn

* Packet analysis
* Traffic flow
* Common ports
* How attacks travel through networks

---

# 2. Cybersecurity Foundations

## Core Security Concepts

* CIA Triad
* Authentication vs Authorization
* Hashing vs Encryption
* Firewalls
* IDS/IPS
* VPN
* Zero Trust
* IAM

## Attack Fundamentals

Understand how attackers operate:

* Phishing
* Malware
* Ransomware
* Brute force
* Credential stuffing
* Web attacks
* Privilege escalation
* Persistence
* Lateral movement

## Frameworks

* MITRE ATT&CK
* Cyber Kill Chain
* OWASP Top 10

### Important Concepts

* IOC
* IOA
* TTPs
* Risk
* Vulnerability vs Threat vs Exploit

---

# 3. Logging & Monitoring

This is the heart of SOC work.

## Learn Log Sources

### Windows Logs

* Security logs
* Sysmon
* PowerShell logs

### Linux Logs

* auth.log
* syslog
* journalctl

### Network Logs

* Firewall logs
* Proxy logs
* DNS logs
* VPN logs

### Cloud Logs

* AWS CloudTrail
* Azure logs
* GCP logs

---

# 4. SIEM (Most Important SOC Skill)

## Learn SIEM Concepts

* Log ingestion
* Parsing
* Correlation
* Alerting
* Dashboards
* Use cases

## Learn At Least One SIEM Well

### Popular Choices

* Splunk
* Microsoft Sentinel
* Elastic Stack
* QRadar
* Wazuh

## Query Languages

* SPL
* KQL
* Lucene
* Elasticsearch DSL

## Practice

* Create alerts
* Detect brute force
* Detect PowerShell abuse
* Detect suspicious logins

---

# 5. Endpoint Security

## EDR/XDR Concepts

* Process monitoring
* Behavioral detection
* Endpoint telemetry
* Threat containment

## Tools

* Microsoft Defender for Endpoint
* CrowdStrike Falcon
* Velociraptor
* Sysmon

## Learn

* Parent-child process relationships
* LOLBins
* Suspicious PowerShell
* Persistence mechanisms

---

# 6. Incident Response (SOC Core)

## IR Process

1. Preparation
2. Identification
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned

## Important Skills

* Alert triage
* Incident classification
* Escalation
* Documentation
* Timeline creation
* Evidence handling
* Chain of custody

## Learn

* Playbooks
* SOPs
* Runbooks

---

# 7. Threat Intelligence

## Learn

* IOC analysis
* Threat actor profiling
* Malware families
* Campaign tracking

## Platforms

* VirusTotal
* MISP
* ANY.RUN

## Study

* APT groups
* Ransomware operations
* Initial access brokers

---

# 8. Threat Hunting

Move from reactive → proactive defense.

## Learn

* Hypothesis-driven hunting
* Behavioral analytics
* Baseline analysis
* Hunt queries

## Focus Areas

* PowerShell abuse
* Lateral movement
* Credential dumping
* Beaconing
* Persistence

## Learn MITRE ATT&CK deeply

Map:

* Tactics
* Techniques
* Procedures

---

# 9. Malware Analysis Basics

## Static Analysis

* Hashes
* Strings
* PE structure

## Dynamic Analysis

* Sandbox analysis
* Network behavior
* Registry changes

## Tools

* Procmon
* Process Explorer
* Wireshark
* Ghidra

---

# 10. Detection Engineering

This separates advanced analysts from beginner analysts.

## Learn

* Sigma rules
* YARA rules
* Detection logic
* False positive reduction

## Topics

* ATT&CK mapping
* Detection coverage
* Alert tuning
* Behavioral detections

## Practice

Write detections for:

* Credential dumping
* Ransomware behavior
* Suspicious PowerShell
* Reverse shells

---

# 11. SOAR & Automation

## Learn

* Playbooks
* Workflow automation
* Auto-enrichment
* Ticketing integration

## Tools

* Shuffle
* Cortex XSOAR
* TheHive

## Automation Skills

* Python
* APIs
* JSON
* Regex

---

# 12. Cloud Security SOC

Very important for modern SOC roles.

## AWS

* IAM
* CloudTrail
* GuardDuty
* Security Groups

## Azure

* Sentinel
* Azure AD
* Defender

## Containers

* Docker security
* Kubernetes basics

---

# 13. Purple Teaming & Advanced Defense

## Learn

* Adversary emulation
* ATT&CK simulations
* Detection validation
* Red vs Blue collaboration

## Tools

* Atomic Red Team
* Caldera

---

# 14. Home Lab (Extremely Important)

Build your own SOC lab.

## Setup

### Machines

* Kali Linux
* Windows 10/11
* Ubuntu Server

### Add

* Sysmon
* Wazuh
* ELK Stack
* Splunk Free
* Velociraptor

## Practice

* Generate attacks
* Analyze logs
* Create alerts
* Investigate incidents

---

# 15. Programming & Scripting

## Must Learn

* Python
* Bash
* PowerShell

## Useful Topics

* Log parsing
* API automation
* IOC extraction
* Detection automation

---

# 16. Certifications Path

## Beginner

* CompTIA Security+
* Google Cybersecurity Certificate

## Intermediate

* EC-Council CSA
* CompTIA CySA+
* INE eJPT

## Advanced

* GIAC GCIH
* GIAC GCIA
* OffSec SOC-200
* Microsoft SC-200

---

# 17. Real-World Practice Platforms

## Blue Team Labs

* TryHackMe
* Hack The Box
* LetsDefend
* BlueTeamLabs Online

## DFIR Practice

* Malware traffic analysis
* Splunk Boss of the SOC
* CyberDefenders

---

# 18. Career Progression

## SOC L1

* Alert monitoring
* Basic triage
* Ticket escalation

## SOC L2

* Investigation
* Threat hunting
* Advanced analysis

## SOC L3

* Incident response
* Malware analysis
* Detection engineering

## Beyond SOC

* Threat Hunter
* DFIR Analyst
* Detection Engineer
* Security Engineer
* SOC Manager
* Purple Team Operator

---

# Suggested Learning Order

## Phase 1

1. Linux
2. Networking
3. Security fundamentals
4. Wireshark
5. Windows logs

## Phase 2

6. SIEM
7. SOC workflows
8. Incident response
9. MITRE ATT&CK

## Phase 3

10. Threat hunting
11. Detection engineering
12. Malware basics
13. Cloud SOC

## Phase 4

14. Automation
15. SOAR
16. Purple teaming
17. Advanced detections

---

### linked

[[os-basics]]
