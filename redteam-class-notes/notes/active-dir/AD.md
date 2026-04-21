#notes

## Active Directory — Basics

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Computer-and-Networks-Active-Directory-Diagrams-Active-Directory-Structure-Diagram.png)

**Active Directory (AD)** is a directory service developed by Microsoft that helps organizations **manage users, computers, permissions, and resources in a network**. It is mainly used in **Windows Server environments** to centralize authentication and management.

Think of it as a **central database + management system for everything in a company’s network**.



# 1. What Active Directory Does

Active Directory helps administrators:

* Manage **users and passwords**
* Control **access to files, printers, and applications**
* Apply **security policies**
* Organize computers and servers
* Provide **centralized authentication**

Example:
When you log into an office computer using your company username and password, **Active Directory verifies who you are**.



# 2. Core Components of Active Directory

## 1. Domain

A **Domain** is the main logical group of users, computers, and resources.

Example domain name:

```
company.local
```

Everything inside the domain shares:

* Common database
* Security policies
* Authentication system



## 2. Domain Controller (DC)

A **Domain Controller** is a server that runs Active Directory services.

Functions:

* Stores the **Active Directory database**
* Authenticates users
* Enforces policies

Typical server:

* Windows Server with **Active Directory Domain Services (AD DS)** installed.



## 3. Objects

Everything in Active Directory is stored as an **object**.

Examples:

* Users
* Computers
* Groups
* Printers
* Shared folders

Example:

```
User: john
Computer: HR-PC01
Printer: OfficePrinter
```



## 4. Organizational Units (OU)

OUs are **folders used to organize objects**.

Example structure:

```
Company
 ├── HR
 │   ├── Users
 │   └── Computers
 ├── IT
 └── Sales
```

Benefits:

* Easier management
* Apply policies to specific departments



## 5. Groups

Groups are used to **assign permissions to multiple users at once**.

Example:

```
HR_Group
Sales_Group
IT_Admins
```

Instead of giving permission to 50 users individually, you **add them to a group**.



# 3. Authentication in Active Directory

When a user logs in:

1. User enters **username + password**
2. Computer contacts **Domain Controller**
3. Domain Controller verifies credentials
4. If correct → user gets **access token**
5. User can access network resources

Protocols used:

* **Kerberos** (default)
* **LDAP**
* **NTLM** (legacy)



# 4. Group Policy (GPO)

**Group Policy** allows administrators to control settings across many computers.

Examples:

* Disable USB drives
* Force password complexity
* Install software automatically
* Lock screen after 10 minutes

Policies are applied to:

* Domains
* Organizational Units



# 5. Active Directory Structure (Hierarchy)

Typical hierarchy:

```
Forest
 └── Domain
      └── Organizational Units
            └── Objects
```

### Forest

Top-level structure that can contain multiple domains.

### Tree

Group of domains sharing namespace.

Example:

```
company.com
sales.company.com
hr.company.com
```



# 6. Common Active Directory Tools

Admins use these tools:

* **Active Directory Users and Computers (ADUC)**
* **Group Policy Management**
* **Active Directory Administrative Center**
* **PowerShell**

All are part of **Windows Server management tools.



# 7. Real-World Example

Company with 500 employees:

Active Directory manages:

* 500 user accounts
* 500 computers
* Shared printers
* File servers
* Security policies
* Login authentication

Everything is controlled **centrally from the Domain Controller**.



# 8. Why Companies Use Active Directory

Advantages:

* Centralized management
* Strong authentication
* Security policy enforcement
* Scalability for large organizations
* Integration with Microsoft services




