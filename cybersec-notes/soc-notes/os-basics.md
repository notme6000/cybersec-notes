
# Micro Syllabus — Operating Systems for SOC

# Module 1 — Windows Fundamentals

## 1.1 Windows Architecture Basics

### Topics

* User mode vs Kernel mode
* Windows boot process
* Processes vs Threads
* DLL basics
* Windows file system (NTFS)

### Practical

* Open Task Manager and inspect processes
* Use:

```powershell
tasklist
systeminfo
wmic process list brief
```

### Outcome

Understand how Windows runs applications and services.

---

# Module 2 — Windows Processes & Services

## 2.1 Processes

### Topics

* PID
* Parent-child relationship
* Suspicious processes
* Common Windows processes

  * explorer.exe
  * lsass.exe
  * svchost.exe
  * winlogon.exe

### Tools

* Process Explorer
* Task Manager

### Practical

* Identify parent-child process chains
* Detect abnormal process spawning

---

## 2.2 Windows Services

### Topics

* What services are
* Service startup types
* Service abuse

### Commands

```powershell
services.msc
sc query
Get-Service
```

### Practical

* Start/stop services
* Identify suspicious services

---

# Module 3 — Windows Registry

## 3.1 Registry Basics

### Topics

* Registry structure
* Hives

  * HKLM
  * HKCU
  * HKCR
* Persistence locations

### Tools

* regedit
* reg query

### Practical

* Navigate registry
* Find startup entries

### SOC Focus

Learn how malware achieves persistence.

---

# Module 4 — Event Viewer & Windows Logs

## 4.1 Event Viewer

### Topics

* Windows logging architecture
* Security logs
* System logs
* Application logs

### Important Event IDs

* 4624 → Successful login
* 4625 → Failed login
* 4688 → Process creation

### Tools

* Event Viewer
* Sysmon

### Practical

* Analyze login events
* Track process execution
* Detect failed brute-force attempts

---

# Module 5 — PowerShell for SOC

## 5.1 PowerShell Basics

### Topics

* Cmdlets
* Variables
* Pipelines
* Execution policy

### Commands

```powershell
Get-Process
Get-Service
Get-EventLog
Get-ChildItem
```

### Practical

* Enumerate processes
* Search logs
* Automate basic tasks

---

## 5.2 Defensive PowerShell

### Topics

* PowerShell logging
* Encoded commands
* Suspicious PowerShell indicators

### Practical

* Decode Base64 commands
* Identify malicious PowerShell usage

---

# Module 6 — Active Directory Basics

## 6.1 AD Fundamentals

### Topics

* Domain
* Domain Controller
* Users & Groups
* Organizational Units
* Authentication basics

### Practical

* Create users/groups in a lab
* Explore AD Users and Computers

### SOC Focus

Understand attacker movement in enterprise networks.

---

# Module 7 — Linux Fundamentals

## 7.1 Linux File System

### Topics

* Directory structure
* Important directories

  * /etc
  * /var
  * /home
  * /tmp

### Commands

```bash
ls
cd
pwd
find
locate
```

### Practical

* Navigate Linux system
* Search files

---

# Module 8 — Linux Permissions

## 8.1 Permissions

### Topics

* Read/write/execute
* Users/groups
* chmod
* chown
* SUID/SGID

### Commands

```bash
chmod
chown
ls -l
```

### Practical

* Modify permissions
* Identify dangerous SUID binaries

### SOC Focus

Learn privilege escalation concepts.

---

# Module 9 — Linux Services & Systemd

## 9.1 Services

### Topics

* systemd basics
* Daemons
* Startup services

### Commands

```bash
systemctl
service
ps aux
```

### Practical

* Start/stop services
* Inspect running daemons

---

# Module 10 — Linux Logging

## 10.1 Logs

### Topics

* syslog
* auth.log
* journalctl
* Application logs

### Commands

```bash
journalctl
tail
grep
cat
less
```

### Practical

* Track SSH logins
* Investigate failed login attempts

---

# Module 11 — Bash Scripting

## 11.1 Bash Basics

### Topics

* Variables
* Loops
* Conditions
* Functions

### Practical

Create scripts to:

* Monitor processes
* Search logs
* Automate repetitive tasks

### Example

```bash
#!/bin/bash
ps aux | grep ssh
```

---

# Module 12 — Linux Networking Commands

## 12.1 Networking Basics

### Commands

```bash
ip a
ss -tulnp
netstat
ping
curl
wget
dig
nslookup
```

### Topics

* Interfaces
* Open ports
* DNS resolution
* Connectivity troubleshooting

### Practical

* Inspect active connections
* Identify listening services

---

# Module 13 — SOC-Centric OS Skills

## Windows

### Learn to Investigate

* Suspicious logins
* New services
* PowerShell abuse
* Scheduled tasks

## Linux

### Learn to Investigate

* SSH brute force
* Suspicious cron jobs
* Unauthorized users
* Suspicious processes

---

# Suggested Study Timeline

## Week 1

* Windows basics
* Processes
* Services

## Week 2

* Registry
* Event Viewer
* PowerShell basics

## Week 3

* Active Directory basics
* Linux navigation
* Permissions

## Week 4

* Linux logs
* Bash scripting
* Networking commands

---

# Mini Projects

## Windows

* Create a failed login detection checklist
* Analyze Event Viewer logs
* Track process trees

## Linux

* Create a log monitoring script
* Detect failed SSH logins
* Enumerate open ports

---

### linked

[[windows]]
