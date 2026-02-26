## Active Directory Hierarchy – Structured Notes

### 1. Forest (Highest Level)

* The forest is the top-level container in Active Directory.
* It is the ultimate security boundary.
* Contains one or more domain trees.
* Shares:

  * Schema (object definitions)
  * Configuration partition
  * Global Catalog
* Domains within a forest trust each other automatically (transitive trust).

Security relevance:

* Forest-level compromise results in full control over all domains.
* Enterprise Admins operate at the forest level.



### 2. Tree

* A tree is a collection of domains sharing a contiguous DNS namespace.
* Example:

  * corp.local
  * sales.corp.local
  * hr.corp.local
* Domains inside a tree have automatic two-way transitive trusts.

Purpose:

* Namespace organization
* Logical grouping of related domains

Security relevance:

* Trust relationships allow authentication across domains in the same tree.



### 3. Domain

* Core administrative and authentication boundary.
* Stores directory data in NTDS.dit.
* Contains:

  * Users
  * Groups
  * Computers
  * Service accounts
  * Organizational Units
* Authentication handled via:

  * Kerberos (default)
  * NTLM (legacy)

Security relevance:

* Domain Admins control the domain.
* Compromise of a domain controller results in domain compromise.
* Password hashes stored on domain controllers.



### 4. Organizational Units (OUs)

* Containers within a domain.
* Used for:

  * Delegation of administrative control
  * Group Policy application
  * Logical organization
* Can be nested.

Important:

* OUs are not security boundaries.
* Permissions can be delegated at the OU level.

Security relevance:

* Misconfigured OU permissions often lead to privilege escalation.
* GPO abuse frequently originates at the OU level.



### 5. Objects

Objects are the lowest-level elements in Active Directory.

Examples:

* User objects
* Computer objects
* Security groups
* Service accounts

Each object contains:

* Attributes (e.g., SID, SPN, email, group membership)
* Access Control Lists (ACLs)

Security relevance:

* ACL misconfigurations enable attacks such as:

  * Password reset abuse
  * Group membership manipulation
  * DCSync permissions abuse



## Logical Structure Summary

Forest
└── Tree
└── Domain
└── Organizational Unit
└── Object



## Security Boundary Summary

Strong security boundaries:

* Forest
* Domain

Not security boundaries:

* Organizational Units
* Groups



## Key Examination Points for Security Professionals

* Forest = ultimate control layer
* Domain Controller = highest-value asset
* OUs = delegation tool, not security isolation
* ACLs = common privilege escalation vector
* Trusts = lateral movement paths

If needed, I can provide next:

* Notes on physical AD structure
* Notes on trust relationships
* Notes on privilege escalation paths
* Notes on how attackers traverse this hierarchy

