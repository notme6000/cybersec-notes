#notes

## How Active Directory Authentication Works (Kerberos-Based)


Active Directory authentication is mainly based on the **Kerberos protocol**. It uses a secure ticket-based system so passwords are not repeatedly sent over the network.

---

# 1. Key Players

* **Client** → User’s computer
* **Domain Controller (DC)** → Authentication server
* **KDC (Key Distribution Center)** → Runs on DC (handles Kerberos)

  * AS (Authentication Service)
  * TGS (Ticket Granting Service)

---

# 2. Step-by-Step Authentication Flow

### Step 1: User Login

* User enters username + password
* Password is converted into a **hash** (not sent as plain text)

---

### Step 2: AS Request (Authentication Service)

* Client sends request to DC:

  * “I want to log in”
* Includes:

  * Username
  * Timestamp

---

### Step 3: DC Verifies User

* DC checks credentials in Active Directory database
* If valid → generates:

### Ticket Granting Ticket (TGT)

* Encrypted using the DC’s secret key
* Contains:

  * User identity
  * Permissions
  * Expiration time

---

### Step 4: Client Receives TGT

* Client decrypts part of response using its password hash
* Stores the **TGT in memory**

Important:

* Password is **never sent over the network**
* TGT proves identity

---

### Step 5: Requesting Access to a Service (TGS Request)

When user tries to access something (e.g., file server):

* Client sends:

  * TGT
  * Request for specific service

---

### Step 6: DC Issues Service Ticket (TGS Response)

* DC verifies TGT
* Issues **Service Ticket** for that resource

---

### Step 7: Accessing the Resource

* Client sends service ticket to server
* Server verifies ticket
* Access granted (no password needed again)

---

# 3. Simple Analogy

Think of it like an airport:

* Login = Show passport
* TGT = Boarding pass
* Service Ticket = Gate-specific pass
* You don’t show your passport again at every gate

---

# 4. Important Concepts

### Single Sign-On (SSO)

* User logs in once
* Access multiple services without re-entering password

---

### Mutual Authentication

* Client verifies server
* Server verifies client

---

### Ticket Expiry

* TGT and service tickets expire (security)

---

# 5. What About NTLM?

Sometimes AD uses **NTLM** instead of Kerberos.

### When NTLM is used:

* Older systems
* No domain trust
* DNS issues

### Differences:

| Kerberos      | NTLM               |
| ------------- | ------------------ |
| Ticket-based  | Challenge-response |
| More secure   | Less secure        |
| Default in AD | Fallback           |

---

# 6. Behind the Scenes (Technical Details)

* Encryption uses:

  * Symmetric keys
  * Session keys
* Tickets contain:

  * SID (Security Identifier)
  * Group memberships
* Time synchronization is critical (Kerberos fails if clocks differ)

---

# 7. Why This Is Secure

* Password never travels across network
* Tickets are encrypted
* Replay attacks are limited via timestamps
* Mutual authentication prevents spoofing

---

# 8. Common Attacks (Important for Learning)

* Pass-the-Hash
* Pass-the-Ticket
* Golden Ticket attack
* Kerberoasting

(All exploit tickets or hashes, not plaintext passwords)

---


