# 🗂️ Active Directory (AD) - Complete Notes with Terms Defined

---

## 1. **What is Active Directory?**

**Active Directory (AD)** is a **directory service** developed by Microsoft for **Windows domain networks**. It manages and stores information about network resources and enables administrators to assign permissions and access rights.

---

## 2. **Key Components of Active Directory**

| Term                         | Definition                                                                                                                    |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Domain**                   | A logical group of network objects (users, computers, devices) that share the same AD database.                               |
| **Domain Controller (DC)**   | A server that responds to security authentication requests (logins, permissions, etc.) and holds a copy of the AD database.   |
| **Forest**                   | The top-level container in AD. A collection of one or more domain trees that share a common schema and global catalog.        |
| **Tree**                     | A collection of one or more domains connected in a transitive trust hierarchy, sharing a contiguous namespace.                |
| **Organizational Unit (OU)** | A container within a domain used to organize users, groups, and computers. Useful for applying Group Policies.                |
| **Global Catalog**           | A distributed data repository that contains a searchable, partial representation of every object in every domain in a forest. |
| **Schema**                   | The set of rules that define object types and attributes in the directory (e.g., what constitutes a user object).             |
| **Site**                     | Represents the physical structure of your network. Sites are used to control replication traffic and logon traffic.           |
| **Replication**              | The process of synchronizing data between domain controllers to ensure consistency.                                           |
| **Trusts**                   | Relationships between domains or forests that allow users to access resources in another domain.                              |

---

## 3. **AD Objects and Attributes**

| Term                   | Definition                                                                         |
| ---------------------- | ---------------------------------------------------------------------------------- |
| **Object**             | Any item stored in AD (e.g., user, group, computer, printer).                      |
| **Attribute**          | Properties of an object (e.g., a user object has a username, email, phone number). |
| **User Object**        | Represents a real user in AD; has credentials for logon.                           |
| **Computer Object**    | Represents a computer joined to the domain.                                        |
| **Group**              | Collection of users or computers. Can be used to assign permissions.               |
| **Security Group**     | Used to assign permissions to shared resources.                                    |
| **Distribution Group** | Used only for email distribution lists, not for security permissions.              |

---

## 4. **Group Types and Scopes**

| Type                   | Definition                                                                                |
| ---------------------- | ----------------------------------------------------------------------------------------- |
| **Security Group**     | Used to assign permissions to resources.                                                  |
| **Distribution Group** | Used for email distribution; cannot assign permissions.                                   |
| **Domain Local**       | Can grant access to resources in the same domain.                                         |
| **Global**             | Used to group users from the same domain.                                                 |
| **Universal**          | Can include users/groups from any domain in the forest. Best for multi-domain membership. |

---

## 5. **Active Directory Services**

| Service                                     | Function                                                                                     |
| ------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **AD DS (Directory Services)**              | Core service that stores directory information and manages communication.                    |
| **AD LDS (Lightweight Directory Services)** | A lighter version of AD DS without domain features; used for directory-enabled applications. |
| **AD FS (Federation Services)**             | Provides single sign-on (SSO) to authenticate users across trusted partners.                 |
| **AD CS (Certificate Services)**            | Creates and manages public key infrastructure (PKI) certificates.                            |
| **AD RMS (Rights Management Services)**     | Protects sensitive information through encryption and rights enforcement.                    |

---

## 6. **Authentication and Authorization**

| Term                                             | Definition                                                                                    |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| **Kerberos**                                     | Default authentication protocol in AD, providing strong encryption and mutual authentication. |
| **NTLM**                                         | Older authentication protocol used for backward compatibility.                                |
| **LDAP (Lightweight Directory Access Protocol)** | Protocol used to query and modify items in directory services like AD.                        |
| **Group Policy (GPO)**                           | A set of rules that control the working environment of users and computers in AD.             |
| **Logon Script**                                 | Script executed during user logon, often used to map drives or set environment variables.     |

---

## 7. **Important Tools and Utilities**

| Tool                                                  | Description                                                                                |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Active Directory Users and Computers (ADUC)**       | Main console for managing users, groups, OUs, etc.                                         |
| **Active Directory Domains and Trusts**               | Tool to manage domain and trust relationships.                                             |
| **Active Directory Sites and Services**               | Used to manage sites, subnets, and replication.                                            |
| **Group Policy Management Console (GPMC)**            | Central console to manage Group Policies.                                                  |
| **DS Commands** (`dsadd`, `dsquery`, `dsmod`, `dsrm`) | Command-line tools for managing AD objects.                                                |
| **PowerShell**                                        | Modern tool for scripting and automating AD management (e.g., `Get-ADUser`, `New-ADUser`). |

---

## 8. **FSMO (Flexible Single Master Operations) Roles**

These are special roles assigned to one or more DCs to handle specific AD tasks:

| Role                      | Description                                                                                    |
| ------------------------- | ---------------------------------------------------------------------------------------------- |
| **Schema Master**         | Controls updates to the AD schema (one per forest).                                            |
| **Domain Naming Master**  | Controls addition/removal of domains in the forest (one per forest).                           |
| **RID Master**            | Allocates RID pools to DCs (one per domain).                                                   |
| **PDC Emulator**          | Emulates a primary domain controller; handles password changes and time sync (one per domain). |
| **Infrastructure Master** | Updates group memberships across domains (one per domain).                                     |

---

## 9. **Best Practices**

* Use **OUs** to structure your domain logically (by department, function, etc.).
* Apply **Group Policies** at OU level for better control.
* Keep **Global Catalog** servers at each site.
* Monitor **replication** and ensure time synchronization.
* Backup your **AD regularly** and test restores.
* Limit the number of **Domain Admins**.

---
Here's a clear explanation of **Single Domain** vs **Multiple Domain** in Active Directory, including definitions, differences, advantages, and when to use each:

---
# 🏢 **Single Domain vs Multiple Domain in Active Directory**

---

## 🔹 **Single Domain**

### ✅ **Definition:**

A **Single Domain** is a setup where the entire organization's Active Directory structure is managed under **one domain** name (e.g., `company.com`).

### ✅ **Features:**

* One AD database.
* Centralized management of all users, groups, and resources.
* One set of domain policies.
* Simple trust management (only internal).
* Flat or OU-based organizational structure.

### ✅ **Advantages:**

* Easy to manage and administer.
* Lower overhead (fewer DCs needed).
* Centralized security and policy enforcement.
* Simplified replication and maintenance.
* Less complex trust relationships (none needed internally).

### ✅ **Use When:**

* Organization is small to medium-sized.
* No strict isolation or regulatory boundaries are required.
* Central IT can manage everything efficiently.

---

## 🔸 **Multiple Domain**

### ✅ **Definition:**

A **Multiple Domain** environment has more than one domain (e.g., `sales.company.com`, `hr.company.com`) within the same forest or across different forests.

### ✅ **Features:**

* Separate AD databases per domain.
* Each domain can have its own policies, admins, and replication.
* Trusts must be established between domains (automatically in a forest, manually between forests).
* Allows organizational autonomy.

### ✅ **Advantages:**

* Better isolation and security boundaries.
* Useful for large or global enterprises.
* Can support different policies per domain.
* Delegated administration possible.

### ✅ **Use When:**

* Organizations are large or span multiple countries.
* Different departments/divisions need strict control.
* Mergers or acquisitions require separate AD environments.
* Regulatory or compliance isolation is required.

---

## 🔁 **Comparison Table**

| Feature                | Single Domain        | Multiple Domain                    |
| ---------------------- | -------------------- | ---------------------------------- |
| **Complexity**         | Low                  | High                               |
| **Trusts Required**    | No (single domain)   | Yes (inter-domain or inter-forest) |
| **Replication**        | Simplified           | More complex                       |
| **Administration**     | Centralized          | Delegated/Decentralized            |
| **Security Isolation** | Low                  | High                               |
| **Cost & Maintenance** | Lower                | Higher                             |
| **Use Case**           | Small to medium orgs | Large, complex orgs                |

---

## 🧠 Summary

| **Single Domain**   | Best for centralized, simple environments with unified policies.                     |
| ------------------- | ------------------------------------------------------------------------------------ |
| **Multiple Domain** | Best for large, complex, or distributed organizations needing isolation or autonomy. |

---
# 🌳 **Tree vs Forest in Active Directory**

---

## 🔹 **What is a Tree?**

### ✅ **Definition:**

A **Tree** is a **collection of one or more domains** that share a **contiguous namespace** (e.g., `company.com`, `sales.company.com`, `hr.company.com`) and are connected through a **transitive trust**.

### ✅ **Key Features:**

* Domains are hierarchically arranged.
* Share a **namespace** (parent-child domain relationship).
* Trusts are **automatically created** between parent and child domains.
* Share the same **schema** and **global catalog**.

### ✅ **Example:**

```
company.com
├── sales.company.com
└── hr.company.com
```

---

## 🔸 **What is a Forest?**

### ✅ **Definition:**

A **Forest** is the **highest-level container** in Active Directory. It is a **collection of one or more Trees** that **do not necessarily share a contiguous namespace** but share a common **schema**, **configuration**, and **global catalog**.

### ✅ **Key Features:**

* Can contain multiple trees with **different namespaces**.
* All trees/domains in a forest share:

  * The **same schema** (structure of AD objects).
  * The **same global catalog** (partial object info).
  * **Trust relationships** (transitive and automatic within the forest).
* **Logical security boundary** – objects in one forest are not visible in another without a trust.

### ✅ **Example:**

```
Forest: 
├── Tree 1: company.com
│   ├── sales.company.com
│   └── hr.company.com
├── Tree 2: business.org
└── Tree 3: retail.net
```

---

## 🔁 **Tree vs Forest – Comparison Table**

| Feature               | Tree                                                     | Forest                                                      |
| --------------------- | -------------------------------------------------------- | ----------------------------------------------------------- |
| **Definition**        | One or more domains with the same namespace              | One or more trees with different namespaces                 |
| **Namespace**         | Contiguous (e.g., subdomains)                            | Non-contiguous (e.g., completely different names)           |
| **Schema**            | Shared across the tree                                   | Shared across the entire forest                             |
| **Global Catalog**    | Shared                                                   | Shared                                                      |
| **Trusts**            | Automatic between parent and child domains               | Automatic between trees in the same forest                  |
| **Security Boundary** | No (within same forest)                                  | Yes (between forests)                                       |
| **Use Case**          | Organizations with logical structure in one domain space | Merged companies or multi-org environments needing autonomy |

---

## 🧠 Summary

| Concept    | Best Use                                                                                                                  |
| ---------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Tree**   | When you need a hierarchy of domains (e.g., `region.company.com`) with shared namespace.                                  |
| **Forest** | When different organizations/domains with unique namespaces need to cooperate under a shared structure but with autonomy. |

---

## 📊 Visual Analogy (Textual)

### Tree:

```
company.com
│
├── sales.company.com
└── hr.company.com
```

### Forest:

```
[Forest Root]
├── Tree 1: company.com
│   └── sales.company.com
├── Tree 2: business.org
└── Tree 3: retail.net
```

---
Here's a detailed, easy-to-understand explanation of how **Kerberos** and **NTLM** authentication protocols work in Active Directory environments:

---

# 🔐 **Kerberos vs NTLM** – Working Explained

---

## ✅ **What is Kerberos?**

**Kerberos** is the **default authentication protocol** used in Active Directory since **Windows 2000**. It is more secure, faster, and supports **mutual authentication** (client and server verify each other).

---

### 🔄 **How Kerberos Works – Step-by-Step**

> 🔧 Key Components:

* **Client** – User's device trying to access a service.
* **KDC (Key Distribution Center)** – Runs on the **Domain Controller**, includes:

  * **AS (Authentication Service)**
  * **TGS (Ticket Granting Service)**
* **TGT (Ticket Granting Ticket)** – Used to request service tickets.
* **Service Ticket** – Grants access to a specific service/server.

---

### 🔁 Kerberos Authentication Flow:

#### 1. **Login Request (AS-REQ)**

* Client sends a request to the **Authentication Service (AS)** with username.
* Sent in **plain text** (no password is sent).

#### 2. **AS Issues TGT (AS-REP)**

* AS verifies the user and sends back a **TGT**, encrypted using a secret key derived from the user's password.
* Only the client can decrypt it.

#### 3. **TGT Used to Request Service Ticket (TGS-REQ)**

* Client sends the TGT to the **Ticket Granting Service (TGS)**, requesting access to a specific service (e.g., file server).

#### 4. **TGS Sends Service Ticket (TGS-REP)**

* TGS returns a **service ticket** encrypted with the service’s secret key.

#### 5. **Access to Service**

* Client sends the service ticket to the target server.
* The server decrypts it and grants access if valid.

---

### ✅ **Benefits of Kerberos:**

* Strong encryption (uses symmetric cryptography).
* Mutual authentication (server also proves identity).
* No passwords sent over the network.
* Faster authentication (ticket reuse).
* Supports SSO (Single Sign-On).

---

## 🔸 **What is NTLM?**

**NTLM (NT LAN Manager)** is an **older, less secure** authentication protocol. It’s used when:

* The server or client is not part of a domain.
* The server doesn't support Kerberos.
* Backward compatibility is needed.

---

### 🔄 **How NTLM Works – Step-by-Step**

> 🧠 NTLM uses a **challenge-response** mechanism.

---

### 🔁 NTLM Authentication Flow:

#### 1. **Client Sends Username**

* Client sends the **username** to the server.

#### 2. **Server Sends Challenge**

* Server sends a random number (called a **nonce**) as a challenge.

#### 3. **Client Responds with Encrypted Challenge**

* Client encrypts the challenge using a **hash of the user's password** and sends it back.

#### 4. **Server Verifies with Domain Controller**

* The server forwards the response to the **Domain Controller (DC)**.
* DC compares the hash with its own calculation.
* If they match, access is granted.

---

### ⚠️ **Drawbacks of NTLM:**

* No mutual authentication (client can’t verify server).
* Vulnerable to **pass-the-hash** and **relay attacks**.
* Password hashes are often stored and reused.
* Slower and less secure than Kerberos.

---

## 🔁 **Kerberos vs NTLM – Comparison Table**

| Feature                   | Kerberos                       | NTLM                          |
| ------------------------- | ------------------------------ | ----------------------------- |
| **Introduced**            | Windows 2000                   | Windows NT                    |
| **Authentication Type**   | Ticket-based                   | Challenge-response            |
| **Security**              | High (mutual auth, encryption) | Lower (one-way auth)          |
| **Performance**           | Faster (SSO, fewer trips)      | Slower                        |
| **Password Sent?**        | No                             | No, but hash can be reused    |
| **Preferred In**          | Domain environments            | Legacy systems, workgroups    |
| **Mutual Authentication** | ✅ Yes                          | ❌ No                          |
| **Vulnerabilities**       | Fewer                          | Pass-the-hash, replay attacks |

---

## 🎯 Summary:

* Use **Kerberos** wherever possible — it's secure, modern, and efficient.
* **NTLM** is a fallback protocol used only when Kerberos is unavailable or not supported.

---

