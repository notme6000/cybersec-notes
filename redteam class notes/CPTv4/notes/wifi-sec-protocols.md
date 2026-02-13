# 1. WEP (Wired Equivalent Privacy)

## Overview

* First Wi-Fi security protocol
* Introduced with early 802.11 standard
* Uses RC4 encryption algorithm

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
* Uses CCMP (Counter Mode with CBC-MAC Protocol)

## Encryption

* AES (Advanced Encryption Standard)
* Strong symmetric encryption

## Weakness

* Vulnerable to:

  * Weak passwords
  * KRACK attack (patched)
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

* Replaces PSK
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
| ------------------- | ---- | ---------------- |
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
| ----- | ---------- | -------------- | ----------- |
| WEP      | RC4        | Very Weak      | Obsolete    |
| WPA      | TKIP       | Weak           | Deprecated  |
| WPA2     | AES        | Strong         | Widely Used |
| WPA3     | AES + SAE  | Very Strong    | Recommended |




