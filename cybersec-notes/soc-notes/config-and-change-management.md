
# Configuration and Change Management in SOC

## 1. Introduction

Configuration and Change Management are critical components of Security Operations Centers (SOC). They help organizations maintain secure, stable, and auditable IT environments.

Many cyberattacks succeed because:

* Security controls were misconfigured
* Systems were changed without authorization
* Monitoring tools were disabled
* Firewall rules were modified incorrectly
* Privileges were escalated silently

SOC teams use configuration and change management processes to:

* Detect unauthorized changes
* Ensure systems follow security baselines
* Monitor risky modifications
* Investigate incidents efficiently
* Maintain compliance requirements

---

# 2. What is Configuration Management?

Configuration Management is the process of:

* Maintaining consistent system settings
* Defining secure baselines
* Monitoring system configurations
* Detecting configuration drift
* Verifying systems remain compliant

It ensures systems stay in an approved and secure state.

---

# 3. Examples of Configurations

## Operating Systems

* Password policies
* Firewall settings
* Logging settings
* User account permissions
* USB restrictions

## Network Devices

* Router ACLs
* Switch VLAN settings
* VPN configurations
* IDS/IPS rules

## Security Tools

* SIEM correlation rules
* EDR policies
* Antivirus signatures
* WAF rules

## Cloud Platforms

* IAM policies
* Security groups
* Storage permissions
* MFA settings

---

# 4. What is Change Management?

Change Management is the process of:

* Requesting changes
* Assessing risk
* Approving changes
* Testing modifications
* Deploying updates safely
* Monitoring impact
* Documenting everything

The main goal is:

"Prevent security incidents and outages caused by uncontrolled changes."

---

# 5. Change Management Lifecycle

## Step 1 — Change Request

A user or admin requests a modification.

Examples:

* Open a firewall port
* Update EDR policy
* Deploy new software
* Modify IAM permissions

---

## Step 2 — Risk Assessment

Security and IT teams evaluate:

* Security impact
* Operational impact
* Compliance risks
* Rollback possibility

---

## Step 3 — Approval

Managers or change advisory boards approve or reject the change.

---

## Step 4 — Testing

Changes should first be tested in:

* Staging environments
* Test labs
* Sandbox networks

---

## Step 5 — Deployment

The approved change is applied.

---

## Step 6 — Monitoring

SOC teams monitor:

* Logs
* Alerts
* Service health
* Security events

---

## Step 7 — Documentation

All changes are recorded for:

* Auditing
* Compliance
* Incident investigation

---

# 6. Why SOC Teams Care About Changes

Attackers often modify systems after gaining access.

Common attacker activities:

* Disabling EDR
* Modifying firewall rules
* Creating admin accounts
* Changing logging settings
* Installing persistence mechanisms

SOC analysts investigate:

* What changed?
* Who changed it?
* Was it approved?
* When did it happen?
* Did it trigger security alerts?

---

# 7. Configuration Drift

Configuration Drift occurs when systems gradually move away from approved configurations.

Example:

Baseline:

* USB disabled
* Strong password policy
* PowerShell logging enabled

Current state:

* USB enabled
* Logging disabled
* Weak passwords allowed

The system has drifted from the secure baseline.

---

# 8. Secure Baselines

A Secure Baseline is a predefined secure configuration standard.

Examples:

* CIS Benchmarks
* NIST hardening guides
* Organization security policies

SOC teams compare systems against baselines continuously.

---

# 9. Types of Changes Monitored by SOC

## Network Changes

* Firewall rule updates
* VPN modifications
* Router configuration changes
* DNS modifications

## Endpoint Changes

* EDR disabled
* Antivirus stopped
* New software installed
* Registry modifications

## Identity Changes

* New admin users
* MFA disabled
* Privilege escalation
* Password policy changes

## Cloud Changes

* Public S3 buckets
* Open security groups
* IAM policy modifications
* API key creation

---

# 10. Indicators of Suspicious Changes

SOC analysts investigate:

## High-Risk Events

* EDR service stopped
* Logging disabled
* Security rules removed
* Unexpected admin account creation
* New scheduled tasks
* Unauthorized PowerShell scripts

## Persistence Mechanisms

* Registry Run keys
* Startup folder changes
* Scheduled tasks
* Services created

---

# 11. Configuration Management Database (CMDB)

A CMDB stores:

* Devices
* Applications
* Software versions
* Owners
* Relationships
* Approved configurations

Used for:

* Asset tracking
* Incident response
* Change validation
* Risk analysis

---

# 12. Audit Trails

Audit trails record:

* Who made changes
* What changed
* When changes happened
* Source IP/device

Examples:

* Windows Event Logs
* Linux auditd logs
* CloudTrail logs
* SIEM records

---

# 13. Role of SIEM in Change Management

SIEM platforms collect and correlate change events.

Example alerts:

* Firewall policy changed
* New admin account created
* GPO modified
* EDR agent removed
* Privileged login detected

SOC analysts compare alerts with approved change tickets.

No approved ticket = suspicious activity.

---

# 14. Role of EDR in Change Monitoring

EDR solutions monitor endpoints for:

* Service modifications
* Registry changes
* Process executions
* Persistence techniques
* Security tool tampering

Example:

winword.exe → powershell.exe → disables Defender

EDR flags this as suspicious behavior.

---

# 15. Common Tools Used

## SIEM Tools

### Splunk

Purpose:

* Log analysis
* Correlation
* Alerting
* Threat hunting

Website:
[https://www.splunk.com/](https://www.splunk.com/)

---

### Microsoft Sentinel

Purpose:

* Cloud-native SIEM
* Incident detection
* Automated response

Website:
[https://learn.microsoft.com/en-us/azure/sentinel/](https://learn.microsoft.com/en-us/azure/sentinel/)

---

### Wazuh

Purpose:

* Open-source SIEM/XDR
* File integrity monitoring
* Log analysis
* Configuration assessment

Website:
[https://wazuh.com/](https://wazuh.com/)

---

## EDR/XDR Tools

### CrowdStrike Falcon

Purpose:

* Endpoint monitoring
* Threat detection
* Incident response

Website:
[https://www.crowdstrike.com/](https://www.crowdstrike.com/)

---

### Microsoft Defender for Endpoint

Purpose:

* Endpoint security
* Threat detection
* Behavioral monitoring

Website:
[https://www.microsoft.com/en-us/security/business/endpoint-security/microsoft-defender-endpoint](https://www.microsoft.com/en-us/security/business/endpoint-security/microsoft-defender-endpoint)

---

## Configuration Management Tools

### Ansible

Purpose:

* Infrastructure automation
* Configuration management
* Security hardening

Website:
[https://www.ansible.com/](https://www.ansible.com/)

---

### Puppet

Purpose:

* Infrastructure consistency
* Automated configuration enforcement

Website:
[https://www.puppet.com/](https://www.puppet.com/)

---

### Chef

Purpose:

* Infrastructure automation
* Baseline management

Website:
[https://www.chef.io/](https://www.chef.io/)

---

### Terraform

Purpose:

* Infrastructure as Code (IaC)
* Cloud configuration deployment

Website:
[https://www.hashicorp.com/products/terraform](https://www.hashicorp.com/products/terraform)

---

## Change Management Platforms

### ServiceNow

Purpose:

* ITSM
* Change approvals
* CMDB management
* Ticket workflows

Website:
[https://www.servicenow.com/](https://www.servicenow.com/)

---

### Jira Service Management

Purpose:

* Ticketing
* Change tracking
* Workflow management

Website:
[https://www.atlassian.com/software/jira/service-management](https://www.atlassian.com/software/jira/service-management)

---

# 16. File Integrity Monitoring (FIM)

FIM monitors important files for unauthorized changes.

Examples:

* /etc/passwd
* Windows registry hives
* Security configuration files

Popular FIM tools:

* Wazuh
* OSSEC
* Tripwire

---

# 17. Real SOC Scenario

Scenario:

1. Attacker compromises VPN credentials
2. Gains admin access
3. Disables EDR
4. Opens firewall port 3389
5. Creates hidden admin account
6. Installs persistence

SOC detects:

* EDR service stopped
* Firewall configuration modified
* New local administrator account
* Registry persistence changes

Incident responders:

* Isolate endpoint
* Rollback changes
* Remove persistence
* Reset credentials
* Restore secure baseline

---

# 18. Compliance and Standards

Configuration and Change Management are required in:

## NIST

Important controls:

* CM (Configuration Management)
* AU (Audit and Accountability)
* SI (System Integrity)

---

## ISO 27001

Focuses on:

* Asset management
* Change control
* Security operations

---

## CIS Controls

Important controls:

* Secure configurations
* Continuous vulnerability management
* Audit logging

---

## PCI-DSS

Requires:

* Logging
* Change tracking
* Secure configurations
* Access monitoring

---

# 19. Important SOC Concepts

## Unauthorized Change

Any modification without approval.

## Emergency Change

Urgent fix requiring immediate deployment.

## Rollback

Reverting to previous stable configuration.

## Hardening

Securing systems by reducing attack surface.

## Least Privilege

Users receive minimum required permissions.

## Asset Inventory

Tracking all systems and devices.

---

# 20. Detection Techniques Used by SOC

## Log Analysis

Analyzing logs for:

* User changes
* Service modifications
* Policy updates

## Correlation Rules

Example:

* Admin account created + EDR disabled = High severity alert

## Threat Hunting

Searching manually for suspicious configuration changes.

## Baseline Comparison

Comparing current configuration against approved standards.

---

# 21. Practical Hands-On Labs and Rooms

## TryHackMe

### SOC Level 1

Good beginner SOC learning path.

[https://tryhackme.com/path/outline/soclevel1](https://tryhackme.com/path/outline/soclevel1)

Topics:

* SIEM
* Log analysis
* Incident response
* Threat detection

---

### Wazuh Room

Learn:

* Log monitoring
* File integrity monitoring
* Configuration assessment

[https://tryhackme.com/room/wazuhct](https://tryhackme.com/room/wazuhct)

---

### Windows Event Logs

Learn:

* Event IDs
* Security logs
* Change tracking

[https://tryhackme.com/room/windowseventlogs](https://tryhackme.com/room/windowseventlogs)

---

### Splunk Room

Learn:

* SIEM searches
* Correlation
* Detection engineering

[https://tryhackme.com/room/splunk101](https://tryhackme.com/room/splunk101)

---

## Hack The Box Academy

### SOC Analyst Path

[https://academy.hackthebox.com/path/preview/soc-analyst](https://academy.hackthebox.com/path/preview/soc-analyst)

Learn:

* SIEM
* Detection engineering
* Threat hunting
* Incident handling

---

### Windows Event Logs & Finding Evil

[https://academy.hackthebox.com/module/details/81](https://academy.hackthebox.com/module/details/81)

---

## LetsDefend

Very good SOC simulation platform.

Website:
[https://letsdefend.io/](https://letsdefend.io/)

Practice:

* Investigating alerts
* Change analysis
* Incident response
* SIEM dashboards
* EDR workflows

---

## Blue Team Labs Online

Website:
[https://blueteamlabs.online/](https://blueteamlabs.online/)

Practice:

* SOC investigations
* Log analysis
* Windows forensics
* Detection engineering

---

## RangeForce Community Edition

Website:
[https://www.rangeforce.com/community-edition/](https://www.rangeforce.com/community-edition/)

Practice:

* Blue team operations
* SOC monitoring
* Detection workflows

---

# 22. Home Lab Setup Recommendation

Beginner SOC Home Lab:

## Virtual Machines

* Kali Linux
* Windows 10/11
* Ubuntu Server

## Tools to Install

* Wazuh
* Splunk Free
* Sysmon
* ELK Stack
* Velociraptor

## Practice Activities

* Create admin users
* Modify registry keys
* Generate failed logins
* Disable Defender
* Change firewall rules
* Analyze SIEM logs

---

# 23. Suggested Learning Roadmap

## Beginner

* Learn Windows Event Logs
* Learn Linux logs
* Understand SIEM basics
* Practice Wazuh

## Intermediate

* Build detection rules
* Learn Sysmon
* Threat hunting
* File integrity monitoring

## Advanced

* Detection engineering
* SOAR automation
* Purple teaming
* Cloud configuration monitoring
* Threat intelligence integration

---

# 24. Important Windows Event IDs

## User/Authentication

* 4624 — Successful login
* 4625 — Failed login
* 4720 — User account created
* 4728 — User added to privileged group

## Service Changes

* 7045 — New service installed

## Audit Policy Changes

* 4719 — Audit policy changed

## Log Clearing

* 1102 — Audit logs cleared

These are extremely important for SOC monitoring.

---

# 25. Sysmon Events Useful for Change Monitoring

## Process Creation

* Event ID 1

## Network Connections

* Event ID 3

## Registry Modifications

* Event ID 13

## File Creation

* Event ID 11

## Service Creation

* Event ID 6

---

# 26. Final Notes

Configuration and Change Management are foundational SOC skills.

Strong SOC analysts must understand:

* System baselines
* Log analysis
* Event correlation
* Windows/Linux internals
* Detection engineering
* Incident response

The best way to learn is:

1. Build a home lab
2. Generate logs intentionally
3. Monitor changes using SIEM/EDR tools
4. Investigate your own attack simulations
5. Practice repeatedly on SOC platforms
