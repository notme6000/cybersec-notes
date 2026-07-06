
## Thick Client Architecture

A **thick client** (also called a fat client) is an application where most of the business logic runs on the user's computer rather than on the server. Examples include desktop banking software, ERP systems, POS software, and many Windows applications.

### Architecture

```text
+-------------------+
|    User           |
+---------+---------+
          |
          v
+-------------------+
| Thick Client App  |
| - UI              |
| - Business Logic  |
| - Local Storage   |
| - Config Files    |
| - DLLs/Libraries  |
+---------+---------+
          |
     HTTP/HTTPS
     TCP/UDP
          |
          v
+-------------------+
| Application Server|
| Authentication    |
| APIs              |
| Database Access   |
+---------+---------+
          |
          v
+-------------------+
| Database Server   |
+-------------------+
```

### Components

* **Client Application** – User interface and business logic.
* **Configuration Files** – Store server URLs, credentials, API keys, etc.
* **Local Database** – SQLite or local cache.
* **Application Server** – Handles authentication and requests.
* **Database** – Stores application data.

---

# Thick Client Penetration Testing Methodology

### 1. Information Gathering

* Identify application type (.exe, .jar, .NET, Electron)
* Determine technologies used
* Find installation directory
* Check dependencies

**Tools**

* Process Explorer
* PEStudio
* Detect It Easy (DIE)
* ExifTool

---

### 2. Static Analysis

Analyze the application without executing it.

Look for:

* Hardcoded credentials
* API keys
* Encryption keys
* Server URLs
* Hidden functionality
* SQL queries

**Tools**

* Ghidra
* IDA Free
* dnSpy
* ILSpy
* jadx
* Strings
* PE-bear

---

### 3. Dynamic Analysis

Run the application and monitor its behavior.

Check:

* Files created
* Registry modifications (Windows)
* Processes
* Memory
* Network traffic

**Tools**

* Process Monitor
* Process Explorer
* Wireshark

---

### 4. Network Analysis

Intercept communication between client and server.

Look for:

* HTTP requests
* Tokens
* Cookies
* JSON/XML
* WebSockets
* Custom protocols

**Tools**

* Burp Suite
* mitmproxy
* Wireshark

---

### 5. Authentication Testing

Check for:

* Weak login
* Password policy
* MFA bypass
* Session handling
* Token validation

---

### 6. Authorization Testing

Verify whether users can:

* Access other users' data
* Perform admin functions
* Modify IDs
* Bypass role restrictions

---

### 7. Local Storage Testing

Inspect:

* SQLite databases
* XML/JSON files
* Log files
* Registry
* Cached credentials
* Temporary files

---

### 8. Reverse Engineering

Analyze:

* Program flow
* Encryption routines
* License validation
* Business logic
* Security checks

---

### 9. Memory Analysis

Look for:

* Passwords
* Tokens
* API keys
* Encryption keys

**Tools**

* x64dbg
* WinDbg

---

### 10. Reporting

Document:

* Vulnerability
* Risk
* Impact
* Proof of concept
* Recommendation

---

# Common Thick Client Attacks

### 1. Hardcoded Credentials

Developers leave:

* Database passwords
* API keys
* Admin credentials

---

### 2. Insecure Local Storage

Sensitive data stored in:

* Plaintext files
* Registry
* SQLite databases

---

### 3. Weak Encryption

* Hardcoded encryption keys
* Reversible encryption
* Weak algorithms
* Custom cryptography

---

### 4. DLL Hijacking

Replace or inject malicious DLLs loaded by the application.

---

### 5. Binary Patching

Modify executable files to:

* Remove license checks
* Bypass authentication
* Skip security controls

---

### 6. Memory Extraction

Read sensitive data directly from RAM:

* Passwords
* Session tokens
* Keys

---

### 7. Network Manipulation

Intercept or modify traffic:

* Replay requests
* Tamper with parameters
* Remove client-side checks

---

### 8. SQL Injection

If the client sends unsanitized data to the server, test for SQL injection in requests.

---

### 9. XML External Entity (XXE)

If XML is used, test whether the server processes external entities insecurely.

---

### 10. Insecure Deserialization

Exploit unsafe handling of serialized objects to execute unintended actions.

---

### 11. Insecure File Permissions

Sensitive configuration files or executables can be modified by low-privileged users.

---

### 12. Client-side Business Logic Manipulation

Modify values such as:

* Prices
* Discounts
* User roles
* Account balances

---

### 13. Certificate Validation Bypass

If the application does not properly validate TLS certificates, an attacker may intercept encrypted traffic.

---

### 14. Session Hijacking

Steal or reuse session tokens to impersonate users.

---

### 15. Directory Traversal

Attempt to access unintended files if the client accepts file paths from users.

---

## Typical Thick Client Testing Workflow

```text
Recon
   ↓
Static Analysis
   ↓
Dynamic Analysis
   ↓
Network Traffic Analysis
   ↓
Authentication Testing
   ↓
Authorization Testing
   ↓
Local Storage Review
   ↓
Reverse Engineering
   ↓
Memory Analysis
   ↓
Exploit Validation
   ↓
Reporting
```

