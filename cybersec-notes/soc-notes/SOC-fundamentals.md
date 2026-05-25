# Detailed Notes: Defensive Security & SOC Fundamentals

---

## 1. Introduction to Defensive Security

### What is Defensive Security?

Defensive security (also called **blue teaming**) refers to all activities, controls, and processes designed to **protect an organization's assets** from cyber threats. Unlike offensive security (red teaming), which focuses on finding and exploiting vulnerabilities, defensive security focuses on **prevention, detection, and response**.

### Core Objectives of Defensive Security:

| Objective | Description |
|-----------|-------------|
| **Prevention** | Stop attacks before they succeed (firewalls, patching, hardening) |
| **Detection** | Identify attacks that bypass preventive controls (SIEM, EDR, IDS) |
| **Response** | Contain, eradicate, and recover from successful attacks |
| **Recovery** | Restore normal operations with minimal downtime |
| **Improvement** | Learn from incidents to strengthen security posture |

### Defensive Security vs Offensive Security:

| Aspect | Defensive (Blue Team) | Offensive (Red Team) |
|--------|----------------------|----------------------|
| Goal | Protect and defend | Find and exploit weaknesses |
| Mindset | Preventative and reactive | Proactive and adversarial |
| Metrics | MTTD, MTTR, false positives | Vulnerabilities found, time to compromise |
| Typical Roles | SOC Analyst, Forensics, IR | Penetration Tester, Red Teamer |

### Key Defensive Security Activities:
- **Monitoring** logs, network traffic, and endpoints 24/7
- **Vulnerability management** – Scanning and patching
- **Incident response** – Handling breaches when they occur
- **Threat hunting** – Proactively searching for hidden threats
- **Security awareness training** – Educating employees
- **Backup and recovery** – Ensuring business continuity

---

## 2. SOC Fundamentals

### What is a SOC?

A **Security Operations Center (SOC)** is a centralized unit that employs people, processes, and technology to continuously monitor and improve an organization's security posture while preventing, detecting, analyzing, and responding to cybersecurity incidents.

### The Three Pillars of a SOC:

```
                    ┌─────────────┐
                    │   PEOPLE    │
                    │ (Analysts,  │
                    │  Managers,  │
                    │  Engineers) │
                    └──────┬──────┘
                           │
            ┌──────────────┼──────────────┐
            │              │              │
     ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
     │  PROCESS   │ │  TECHNOLOGY│ │  GOVERNANCE │
     │ (Playbooks,│ │ (SIEM, EDR,│ │ (Compliance,│
     │  SOPs, IR) │ │  SOAR, NDR)│ │  Policies)  │
     └────────────┘ └────────────┘ └────────────┘
```

### SOC Functions in Detail:

| Function | Description |
|----------|-------------|
| **Monitoring** | 24/7 observation of security alerts and logs |
| **Triage** | Prioritizing alerts based on severity and impact |
| **Investigation** | Deep analysis to confirm or dismiss threats |
| **Response** | Containing and eradicating confirmed threats |
| **Reporting** | Documenting incidents and producing metrics |
| **Hunting** | Proactively searching for undetected threats |
| **Tool Management** | Maintaining and tuning security tools |

### SOC Maturity Levels:

| Level | Name | Characteristics |
|-------|------|-----------------|
| 1 | Initial | Reactive, no formal processes, high false positives |
| 2 | Managed | Defined processes, basic metrics, some automation |
| 3 | Defined | Standardized playbooks, proactive hunting, SLAs |
| 4 | Optimized | Continuous improvement, advanced automation (SOAR) |

### Common SOC KPIs:
- **Mean Time to Detect (MTTD)** – Average time from attack to detection
- **Mean Time to Respond (MTTR)** – Average time to contain and recover
- **Alert Volume** – Number of alerts generated per day
- **False Positive Rate** – Percentage of alerts that are benign
- **Incident Closure Rate** – Percentage of incidents fully resolved

---

## 3. Intro to Defensive Security (Concepts Only)

This section reinforces core defensive security concepts without hands-on labs.

### The Defensive Security Lifecycle:

```
   ┌──────────┐
   │ PREPARE  │ ← Hardening, training, tool deployment
   └────┬─────┘
        ▼
   ┌──────────┐
   │ PREVENT  │ ← Firewalls, patching, access controls
   └────┬─────┘
        ▼
   ┌──────────┐
   │ DETECT   │ ← SIEM alerts, EDR detections, IDS signs
   └────┬─────┘
        ▼
   ┌──────────┐
   │ RESPOND  │ ← Containment, eradication, recovery
   └────┬─────┘
        ▼
   ┌──────────┐
   │ IMPROVE  │ ← Lessons learned, control updates
   └──────────┘
```

### Key Defensive Frameworks:

| Framework | Purpose |
|-----------|---------|
| **NIST CSF** | Identify, Protect, Detect, Respond, Recover |
| **MITRE ATT&CK** | Mapping adversary tactics and techniques |
| **Cyber Kill Chain** | Stages of an attack (recon → exfiltration) |
| **Diamond Model** | Adversary, infrastructure, capability, victim |

### Defense in Depth (Layered Security):

```
                    ┌─────────────────────────┐
                    │   Physical Security     │ ← Layer 5
                    ├─────────────────────────┤
                    │   Policies & Procedures │ ← Layer 4
                    ├─────────────────────────┤
                    │   Application Security  │ ← Layer 3
                    ├─────────────────────────┤
                    │   Network Security      │ ← Layer 2
                    ├─────────────────────────┤
                    │   Endpoint Security     │ ← Layer 1
                    └─────────────────────────┘
```

The principle: **No single control is perfect.** Multiple layers ensure that if one fails, others still protect.

### The 5 Pillars of NIST Cybersecurity Framework (CSF):
1. **Identify** – Understand assets, risks, and vulnerabilities
2. **Protect** – Implement safeguards (access control, awareness)
3. **Detect** – Continuous monitoring and anomaly detection
4. **Respond** – Incident handling, analysis, and mitigation
5. **Recover** – Restore capabilities and improve resilience

---

## 4. Asset Inventory (Information Assets and Tools)

### What is an Asset Inventory?

An **asset inventory** is a comprehensive, continuously updated list of all hardware, software, data, and cloud resources within an organization. You **cannot protect what you do not know exists.**

### Types of Assets to Inventory:

| Category | Examples |
|----------|----------|
| **Hardware** | Servers, workstations, laptops, mobile devices, routers, switches, firewalls, IoT devices |
| **Software** | Operating systems, applications, databases, security tools, custom code |
| **Data** | Customer PII, financial records, intellectual property, trade secrets, employee data |
| **Cloud Assets** | AWS EC2, S3 buckets, Azure VMs, GCP instances, SaaS applications (Office 365, Salesforce) |
| **Network Assets** | IP ranges, subnets, domains, SSL certificates, API endpoints |
| **Identities** | User accounts, service accounts, admin accounts, privileged access |

### Information Assets vs Tools:

| Asset Type | Definition | Examples |
|------------|------------|----------|
| **Information Asset** | Data or knowledge valuable to the organization | Customer database, source code, financial spreadsheets |
| **Tool** | Software/hardware used to manage or protect assets | SIEM, antivirus, firewall, ticketing system |

### Asset Inventory Attributes (Minimum):

For each asset, document:
- **Unique ID** – Internal tracking number
- **Asset Type** – Hardware, software, data, cloud
- **Owner** – Department or person responsible
- **Location** – Physical (rack, room) or logical (VPC, subnet)
- **Criticality** – High/Medium/Low based on business impact
- **Sensitivity** – Public, internal, confidential, restricted
- **Custodian** – Person who maintains the asset
- **Purchase/Deployment Date**
- **End of Life / Retirement Date**

### Methods for Building an Asset Inventory:

| Method | Description |
|--------|-------------|
| **Network Scanning** | Tools like Nmap, Shodan, or Nessus discover live hosts |
| **Agent-based** | Deploy agents on endpoints to report inventory |
| **Configuration Management** | Tools like SCCM, Ansible, or Puppet |
| **Cloud APIs** | AWS Config, Azure Resource Graph, GCP Asset Inventory |
| **Manual Entry** | Spreadsheets (not recommended for scale) |
| **CMDB** | Configuration Management Database (ServiceNow, Jira) |

### Why Asset Inventory is Critical for SOC:
- **Alert enrichment** – Knowing which asset is affected helps prioritize
- **Vulnerability management** – You can only patch what you know
- **Incident response** – Faster containment when you know asset location and owner
- **Compliance** – PCI DSS, ISO 27001, HIPAA all require asset inventories
- **Shadow IT detection** – Finding unauthorized assets

---

## 5. Security Baselines

### What is a Security Baseline?

A **security baseline** is a set of minimum security controls and configuration standards that must be applied to all assets within a specific category (e.g., all Windows servers, all employee laptops, all cloud storage buckets).

### Purpose of Baselines:
- Ensure **consistent security** across similar assets
- Reduce **attack surface** by disabling unnecessary features
- Simplify **compliance** audits
- Enable **automated configuration checking**

### Examples of Baseline Configurations:

| Asset Type | Baseline Requirement |
|------------|---------------------|
| Windows 10 Workstation | Password min 8 chars, lockout after 5 attempts, disable guest account, enable BitLocker |
| Linux Server | Disable root SSH login, enforce key-based auth, install fail2ban, auditd enabled |
| Web Server (Apache/Nginx) | Disable directory listing, remove default pages, HSTS enabled, TLS 1.2+ only |
| S3 Bucket | Block public access by default, enable versioning, enable server-side encryption |

### Common Baseline Frameworks:

| Framework | Description |
|-----------|-------------|
| **CIS Benchmarks** | Center for Internet Security – Industry standard for 100+ technologies |
| **NIST SP 800-171** | Protecting Controlled Unclassified Information (CUI) |
| **DISA STIGs** | Security Technical Implementation Guides (US DoD) |
| **Microsoft Security Baselines** | For Windows, Office, Edge |
| **ISO 27001 Annex A** | International standard controls |

### Baseline Implementation Process:

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   SELECT    │ →  │  DOCUMENT   │ →  │   DEPLOY    │ →  │   MONITOR   │
│ (Choose CIS │    │ (Write SOP, │    │ (GPO, Ansible│    │ (Scan for   │
│  or STIG)   │    │  exceptions)│    │  PowerShell) │    │  drift)     │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
```

### Baseline vs Hardening (Clarification):

| Term | Meaning |
|------|---------|
| **Baseline** | The "minimum standard" you require |
| **Hardening** | The *act* of applying that baseline |

You cannot have hardening without a baseline. The baseline defines *what* to do; hardening is *doing* it.

---

## 6. Standard Operating Procedures (SOP)

### What is an SOP?

A **Standard Operating Procedure (SOP)** is a documented, step-by-step instruction set that describes how to perform a routine security task consistently and correctly.

### Why SOPs are Critical in a SOC:
- **Consistency** – Different analysts handle the same alert the same way
- **Speed** – No time wasted figuring out what to do
- **Quality** – Prevents missed steps or mistakes
- **Training** – New analysts can learn quickly
- **Audit trail** – Demonstrates due diligence
- **Reduced cognitive load** – Follow steps, not guess

### Examples of SOC SOPs:

| SOP Title | Purpose |
|-----------|---------|
| Alert Triage SOP | How to review, prioritize, and tag incoming alerts |
| Phishing Investigation SOP | Steps to analyze reported phishing emails |
| Malware Detection SOP | Process for handling an antivirus alert |
| Escalation SOP | When and how to escalate to L2, L3, or management |
| Evidence Collection SOP | How to preserve forensic evidence (chain of custody) |
| False Positive SOP | How to document and tune false positives |
| Endpoint Isolation SOP | Steps to quarantine a compromised host |

### Anatomy of a Good SOP:

```
┌─────────────────────────────────────────────┐
│ 1. TITLE: Phishing Email Investigation SOP │
├─────────────────────────────────────────────┤
│ 2. PURPOSE: Investigate user-reported       │
│    phishing emails within 30 minutes        │
├─────────────────────────────────────────────┤
│ 3. SCOPE: All user email reports to soc@    │
├─────────────────────────────────────────────┤
│ 4. ROLES: L1 Analyst (primary), L2 (if URL  │
│    is malicious)                            │
├─────────────────────────────────────────────┤
│ 5. PREREQUISITES: Access to email gateway   │
│    logs, EDR, URL sandbox                   │
├─────────────────────────────────────────────┤
│ 6. PROCEDURE (Numbered Steps):              │
│    1. Extract sender email address          │
│    2. Check sender against known domains    │
│    3. Extract URLs and attachments          │
│    4. Submit URLs to sandbox (VirusTotal)   │
│    5. Check EDR for any existing detections │
│    6. If malicious → escalate to L2         │
│    7. Document findings in ticket           │
├─────────────────────────────────────────────┤
│ 7. EXCEPTIONS: CEO emails require immediate │
│    L2 notification                          │
├─────────────────────────────────────────────┤
│ 8. VERSION: 2.1 | LAST UPDATED: 2025-01-15 │
└─────────────────────────────────────────────┘
```

### SOP vs Playbook vs Runbook:

| Term | Description |
|------|-------------|
| **SOP** | Broad, routine task (e.g., onboarding a user) |
| **Playbook** | Incident-specific response (e.g., ransomware playbook) |
| **Runbook** | Technical automation steps (often for SOAR) |

---

## 7. Preparation and Preventive Maintenance

### Preparation (Proactive Security)

Preparation refers to all activities performed **before an incident occurs** to ensure the SOC is ready to respond effectively.

### Key Preparation Activities:

| Activity | Description |
|----------|-------------|
| **Incident Response Plan (IR Plan)** | Documented strategy for handling incidents |
| **IR Team Formation** | Roles, contact lists, and escalation paths |
| **Tool Deployment** | SIEM, EDR, SOAR installed and configured |
| **Training & Drills** | Tabletop exercises, purple teaming, simulations |
| **Communication Plan** | Internal (legal, PR, IT) and external (MSSP, law enforcement) |
| **Backup Strategy** | Regular, tested, offline/immutable backups |
| **Documentation** | SOPs, network diagrams, asset lists, playbooks |
| **Retainer Agreements** | Incident response vendors, legal counsel, PR firms |

### Preventive Maintenance

Preventive maintenance is the **ongoing, scheduled upkeep** of security controls to ensure they remain effective.

### Types of Preventive Maintenance:

| Type | Frequency | Examples |
|------|-----------|----------|
| **Patch Management** | Weekly/Monthly | OS updates, application patches, firmware upgrades |
| **Rule/Signature Updates** | Daily/Real-time | Antivirus definitions, IDS/IPS rules, YARA rules |
| **Log Review** | Daily | Reviewing failed logins, admin actions, anomalies |
| **Access Review** | Monthly/Quarterly | Remove stale accounts, review privilege escalations |
| **Backup Testing** | Weekly/Monthly | Restore a random backup to verify integrity |
| **Tool Health Checks** | Daily | Is SIEM ingesting logs? Is EDR reporting? |
| **Vulnerability Scans** | Weekly/Monthly | Internal and external scanning |
| **Compliance Audits** | Quarterly/Annually | Internal audits against baselines |

### The Preventive Maintenance Cycle:

```
     ┌─────────────┐
     │   SCHEDULE  │ ← Plan maintenance windows
     └──────┬──────┘
            ▼
     ┌─────────────┐
     │   TEST      │ ← Apply changes in non-production first
     └──────┬──────┘
            ▼
     ┌─────────────┐
     │   DEPLOY    │ ← Apply to production during window
     └──────┬──────┘
            ▼
     ┌─────────────┐
     │   VERIFY    │ ← Confirm changes work as expected
     └──────┬──────┘
            ▼
     ┌─────────────┐
     │  DOCUMENT   │ ← Record what was done, when, and by whom
     └─────────────┘
```

### Consequences of Poor Preparation & Maintenance:

| Failure | Consequence |
|---------|-------------|
| No IR plan | Chaos during an incident, delayed response |
| No backups | Ransomware = permanent data loss |
| Unpatched systems | Exploitable vulnerabilities (e.g., EternalBlue, Log4j) |
| Stale detection rules | Attackers bypass security unnoticed |
| Untrained analysts | Slow, incorrect response decisions |

---

## 8. Asset Hardening (Security Baselines)

### What is Asset Hardening?

**Hardening** is the process of applying security baselines to an asset to reduce its attack surface by **removing unnecessary services, disabling default accounts, enforcing secure configurations, and applying the principle of least privilege.**

### Hardening vs Baseline (Refresher):

| Concept | Role |
|---------|------|
| **Baseline** | The *standard* you want to achieve |
| **Hardening** | The *action* of applying that standard |

### The Hardening Process:

```
Raw Asset → Identify Unnecessary Features → Disable/Remove → Apply Secure Configurations → HARDENED ASSET
(Default OS)   (Telnet, guest account, etc.)   (Firewall, encryption, logging)
```

### Hardening Categories with Examples:

| Category | Hardening Actions |
|----------|-------------------|
| **Operating System** | Remove unused software, disable unnecessary services (print spooler, SMBv1), enforce secure boot, full disk encryption |
| **Network** | Disable unused ports, block ICMP, implement 802.1X, disable Telnet (use SSH), disable unused protocols (SMBv1, LLMNR) |
| **Application** | Remove default credentials, disable dangerous functions (eval, exec), enforce input validation, enable logging |
| **Database** | Remove default accounts (sa), enforce least privilege, encrypt data at rest and in transit |
| **User Accounts** | Disable guest, enforce MFA, remove stale accounts, enforce password policy |
| **Cloud Resources** | Disable public access (S3 buckets), enable encryption, enforce VPC flow logs |

### Popular Hardening Guides & Frameworks:

| Framework | Best For |
|-----------|----------|
| **CIS Benchmarks** | Level 1 (basic) and Level 2 (defense-in-depth) hardening |
| **DISA STIGs** | Government and military environments |
| **NSA Hardening Guides** | Specific OS and application guidance |
| **NIST SP 800-123** | General server hardening |
| **Microsoft Security Baselines** | Windows and Office products |

### Hardening Levels (CIS Example):

| Level | Description | Impact |
|-------|-------------|--------|
| **Level 1** | Basic, low-impact hardening (must have) | Minimal operational impact |
| **Level 2** | Defense-in-depth, may impact functionality | Potential compatibility testing needed |

### Example: Hardening a Windows 10 Workstation (Partial CIS Level 1)

| Action | Why |
|--------|-----|
| Disable Guest account | Prevents anonymous access |
| Set minimum password length to 14 chars | Harder to brute force |
| Enable Windows Defender | Built-in AV |
| Disable SMBv1 | Prevents EternalBlue style attacks |
| Enable BitLocker | Protects data if device stolen |
| Disable AutoRun | Prevents USB malware |
| Set UAC to always notify | User confirms privilege escalations |
| Enable Windows Firewall | Blocks unauthorized inbound traffic |
| Disable LLMNR and NetBIOS | Prevents NTLM relay attacks |

### Example: Hardening a Linux Server (Ubuntu)

| Action | Command / Config |
|--------|------------------|
| Disable root SSH login | `PermitRootLogin no` in /etc/ssh/sshd_config |
| Use SSH key only | `PasswordAuthentication no` |
| Install and configure UFW | `ufw default deny incoming; ufw allow ssh` |
| Remove unused packages | `apt autoremove --purge` |
| Enable auditd | `systemctl enable auditd` |
| Set secure umask | `umask 027` in /etc/profile |
| Disable IPv6 (if not used) | `net.ipv6.conf.all.disable_ipv6=1` |
| Harden kernel parameters | `/etc/sysctl.conf` (disable IP forwarding, source routing) |

### Hardening Validation (Checking Your Work):

| Method | Tools |
|--------|-------|
| Automated scanning | OpenSCAP, Lynis, CIS-CAT, Nessus |
| Manual verification | Check config files, run benchmark scripts |
| Continuous monitoring | EDR, SIEM rules for configuration drift |

### Configuration Drift:

**Configuration drift** occurs when a hardened asset gradually deviates from its baseline due to updates, manual changes, or software installations.

**Prevention:**
- Use **Infrastructure as Code (IaC)** – Terraform, Ansible, Puppet
- Regular **compliance scanning** (daily/weekly)
- **Immutable infrastructure** – Replace, don't patch

---

# Summary Table: Topics at a Glance

| Topic | Core Purpose | Key Output |
|-------|--------------|-------------|
| Defensive Security | Protect, detect, respond to threats | Reduced risk, faster response |
| SOC Fundamentals | Centralized security operations | 24/7 monitoring and incident handling |
| Asset Inventory | Know what you own | Complete asset list with owners |
| Security Baselines | Minimum security standards | Documented configuration requirements |
| SOPs | Consistent, repeatable tasks | Step-by-step procedures |
| Preparation & Maintenance | Proactive readiness | IR plan, backups, tool health |
| Asset Hardening | Reduce attack surface | Securely configured assets |


