

---

### **Web Penetration Testing:**

1. ✅ **Nmap** - Network scanning & reconnaissance (Already Implemented)
2. ✅ **Amass** - Subdomain enumeration (Already Implemented)
3. **Nikto** - Web server scanner to find vulnerabilities ( used nmap vuln scnner instead)
    - **Command:** `nikto -h <target>`
4. **Gobuster** - Brute-force directories & subdomains
    - **Command:** `gobuster dir -u <target> -w wordlist.txt`
5. **SQLmap** - Automatic SQL injection tool
    - **Command:** `sqlmap -u "http://target.com/page.php?id=1" --dbs`

---

### **OSINT (Open-Source Intelligence):**

6. **theHarvester** - Collect emails, subdomains, and names from public sources
    - **Command:** `theHarvester -d target.com -b google`
7. **Sherlock** - Find social media accounts by username
    - **Command:** `python3 sherlock <username>`
8. **Metagoofil** - Extract metadata from public documents
    - **Command:** `metagoofil -d target.com -t pdf -o output/`
9. **GHunt** - Gather OSINT data from Google services
    - **Command:** `python3 ghunt.py email@example.com`
10. **Holehe** - Check if an email is registered on multiple websites
    - **Command:** `holehe email@example.com`

---
