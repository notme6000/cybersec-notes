# 1. WEP (Wired Equivalent Privacy)

## Overview

* First Wi-Fi security protocol
* Introduced with early 802.11 standard
* Uses RC4 (rivest cipher 4) encryption algorithm

## Key Features

* 64-bit or 128-bit key
* Static encryption key
* Uses IV (Initialization Vector)

## Problems

* Weak IV implementation
* Easy to crack (minutes)
* No proper key management
* Vulnerable to replay attacks

Status:

* Deprecated
* Should NEVER be used



# 2. WPA (Wi-Fi Protected Access)

## Overview

* Introduced as temporary fix for WEP
* Uses TKIP (Temporal Key Integrity Protocol)
* Still based on RC4

## Improvements Over WEP

* Dynamic key generation
* Message Integrity Check (MIC)
* Better authentication

## Weaknesses

* Still vulnerable to attacks
* TKIP is outdated

Status:

* Deprecated



# 3. WPA2 (Wi-Fi Protected Access 2)

## Overview

* Replaced WPA
* Based on IEEE 802.11i standard
* Uses AES encryption

## Encryption

* AES (Advanced Encryption Standard)
* Strong symmetric encryption

## Weakness

* Vulnerable to:

  * Weak passwords
  * KRACK attack (patched)
    [krack attack](https://www.krackattacks.com/)
  * Offline dictionary attacks

Status:

* Still widely used
* Considered secure if configured properly



# 4. WPA3 (Latest Standard)

## Overview

* Introduced in 2018
* Stronger security than WPA2

## Key Improvements

### 1. SAE (Simultaneous Authentication of Equals)

* Replaces PSK (pre-shared key)
* Protects against brute-force attacks
* Provides forward secrecy

### 2. Forward Secrecy

* Even if password is compromised later, past sessions remain secure

### 3. Stronger Encryption

* 192-bit encryption option (Enterprise)

### 4. Protected Management Frames (PMF)

* Prevents deauthentication attacks

Status:

* Recommended standard today



# 5. WPA2 vs WPA3 Comparison

| Feature                | WPA2 | WPA3             |
| ---------------- | ---- | ---------------- |
| Encryption             | AES  | AES              |
| Authentication         | PSK  | SAE              |
| Brute-force Protection | No   | Yes              |
| Forward Secrecy        | No   | Yes              |
| Enterprise Option      | Yes  | Stronger 192-bit |


# 8. Common Wi-Fi Attacks

## 1. Brute Force Attack

Guessing weak Wi-Fi passwords.

Prevention:

* Strong passwords
* WPA3



## 2. Deauthentication Attack

Attacker forces device to disconnect.

Prevention:

* WPA3 (PMF)
* Updated firmware



## 3. Evil Twin Attack

Fake access point mimics real network.

Prevention:

* Certificate validation
* Enterprise authentication

# 10. Summary of Wi-Fi Security Protocols

| Protocol | Encryption | Security Level | Status      |
| -- | ---------- | -------------- | ----------- |
| WEP      | RC4        | Very Weak      | Obsolete    |
| WPA      | TKIP       | Weak           | Deprecated  |
| WPA2     | AES        | Strong         | Widely Used |
| WPA3     | AES + SAE  | Very Strong    | Recommended |


---

## Extensible Authentication Protocol (EAP)

**Extensible Authentication Protocol (EAP)** is a flexible authentication framework used to verify the identity of devices and users before allowing access to a network. It does not define a single authentication method; instead, it supports multiple authentication mechanisms such as certificates, smart cards, and passwords.



## How It Works (Basic Process)

EAP typically operates within **802.1X network access control** and involves three main components:

* **Supplicant** – The user device (laptop, phone, etc.)
* **Authenticator** – Network device (switch or wireless access point)
* **Authentication Server** – Usually a RADIUS server (remote authentication dial-in user service)

### Step-by-Step Flow

1. Device connects to network.
2. Authenticator requests identity.
3. Device sends identity information.
4. Authentication server selects an EAP method (e.g., EAP-TLS).
5. Authentication credentials are exchanged.
6. Access is granted or denied.

EAP messages are carried over:

* **EAPOL (EAP over LAN)** in wired/wireless LAN
* RADIUS between authenticator and authentication server



## Common EAP Methods

### 1. EAP-TLS

* Uses digital certificates
* Mutual authentication (client and server verify each other)
* Very secure
* Used in enterprise networks



### 2. PEAP (Protected EAP)

* Creates encrypted TLS tunnel
* Uses username/password inside tunnel
* Easier to deploy than certificate-based systems



### 3. EAP-FAST

* Developed by Cisco Systems
* Uses Protected Access Credential (PAC)
* Designed as alternative to certificates



## Uses of EAP

* Enterprise Wi-Fi authentication (WPA2/WPA3-Enterprise)
* Wired network authentication (corporate LANs)
* VPN access control
* Broadband and ISP authentication
* Secure campus and government networks
* Zero Trust network environments



## Real-World Examples

### 1. Corporate Office Wi-Fi

Employees connect to secure Wi-Fi using EAP-TLS with company-issued certificates.

### 2. University Campus Network

Students log in using username/password via PEAP authentication.

### 3. Government Network

Devices authenticate using smart cards and EAP-TLS.

### 4. VPN Access

Remote workers authenticate to company VPN using EAP-based authentication.

### 5. Airport or Enterprise Secure Wi-Fi

Access points use 802.1X with EAP methods to validate users before granting access.



## Key Points (Quick Notes)

* EAP is a framework, not a single protocol.
* Works with 802.1X.
* Supports multiple authentication methods.
* Commonly used in enterprise networks.
* Provides strong security for wired and wireless access.
* Uses RADIUS server for backend authentication.




