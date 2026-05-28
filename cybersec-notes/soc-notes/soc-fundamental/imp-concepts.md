## 🔍 Indicators of Compromise (IOCs) vs. Indicators of Attack (IOAs)

Both are essential for threat detection, but they look at security from two different timelines: the **past** (what happened) and the **present** (what is happening right now).

### 1. Indicators of Compromise (IOC)

IOCs are evidence that an attack **has already occurred** or is currently underway. They are reactive, acting like digital forensics or "fingerprints" left behind at a crime scene.

* **Characteristics:** Concrete, static, and relatively easy to share (e.g., via threat intelligence feeds).
* **Examples:**
* A known malicious file hash (MD5/SHA256).
* IP addresses or domains associated with known command-and-control (C2) servers.
* Unusual registry changes or unauthorized system files.
* A massive spike in outbound network traffic to an unfamiliar foreign country.



### 2. Indicators of Attack (IOA)

IOAs focus on the **intent and behavior** of the attacker in real-time. They are proactive and look for the sequential steps an adversary takes to achieve their goal, regardless of the specific malware or tools they use.

* **Characteristics:** Dynamic, behavioral, and focused on the *strategy* rather than the specific file.
* **Examples:**
* An internal account suddenly attempting to execute code on multiple servers simultaneously (lateral movement).
* A legitimate system tool (like PowerShell) being used to download an executable from an external site (living off the land).
* Repeated, rapid failed login attempts across multiple distinct service accounts (brute-forcing/credential stuffing).



> 💡 **The Difference:** An **IOC** tells you, *"We found a known malware file on this computer."* An **IOA** tells you, *"An unknown process is trying to inject code into a critical system service right now."*

---

## 🛠️ Tactics, Techniques, and Procedures (TTPs)

TTPs describe the **behavior, methods, and patterns** of a specific threat actor or group. Understanding TTPs allows security analysts to profile adversaries (like APT groups) and defend against their specific operational habits.

* **Tactics:** The *strategic objective* of the attacker (the "What"). What are they trying to accomplish? (e.g., Initial Access, Persistence, Exfiltration).
* **Techniques:** The *method* used to achieve that objective (the "How"). How will they accomplish the tactic? (e.g., Spearphishing with an attachment to gain Initial Access).
* **Procedures:** The *specific step-by-step implementation* or toolset used (the "Details"). This is the exact script, custom malware, or sequence of commands they execute.

---

## ⚖️ Vulnerability vs. Threat vs. Exploit

These three terms form the foundational equation of cybersecurity risk. They are distinct concepts that depend entirely on one another.

```
[Vulnerability] + [Threat] + [Exploit] = RISK

```

### 1. Vulnerability

A **vulnerability** is a flaw, weakness, or bug in a system, software, or network design that *could* be taken advantage of by a malicious actor.

* *Analogy:* A broken window lock on the ground floor of a house.
* *Example:* A buffer overflow bug in a software application.

### 2. Threat

A **threat** is any potential danger or actor that has the *intent and capability* to cause harm, loss, or disruption by targeting a vulnerability.

* *Analogy:* A burglar walking through the neighborhood looking for empty houses.
* *Example:* A ransomware group or a malicious insider.

### 3. Exploit

An **exploit** is the specific input, piece of software, or sequence of commands designed to take advantage of a vulnerability to cause unauthorized behavior. It is the tool that bridges the threat to the vulnerability.

* *Analogy:* The act of the burglar physically pushing open the unlocked window to crawl inside.
* *Example:* A specific script or payload (like EternalBlue) that uses a code flaw to grant remote access.

---

## 📉 Risk

**Risk** is the probability or likelihood that a threat actor will successfully use an exploit against a specific vulnerability, combined with the resulting **impact** (harm or financial loss) to the organization.

$$\text{Risk} = \text{Likelihood} \times \text{Impact}$$

* **High Risk:** A critical software vulnerability (Vulnerability) exists on an internet-facing production server, public exploit code is widely available on GitHub (Exploit), and active hacking groups are scanning for it (Threat).
* **Low Risk:** A vulnerability exists in a software package, but the server is completely air-gapped (isolated from the network), meaning no remote threat actor can access or exploit it.
