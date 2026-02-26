# 1. What is a VPN?

A **VPN (Virtual Private Network)** is a technology that creates a secure, encrypted connection over a public network (like the Internet).

It allows users or networks to:

* Securely access remote resources
* Protect data from interception
* Hide IP addresses
* Bypass geographic restrictions



# 2. Why VPN is Needed

When you send data over the Internet:

* It can be intercepted
* It may be monitored
* Your real IP address is visible

A VPN provides:

* Encryption (confidentiality)
* Authentication
* Data integrity
* Secure remote access



# 3. Basic Idea of VPN

A VPN creates a **secure tunnel** between:

* User ↔ VPN Server
  or
* Site A ↔ Site B

All traffic inside the tunnel is encrypted.



# 4. How VPN Works (Step-by-Step)

Example: User connecting to company network remotely.

## Step 1: VPN Client Initiates Connection

The user opens VPN software and connects to VPN server.

## Step 2: Authentication

User verifies identity using:

* Username/password
* Digital certificate
* Multi-factor authentication

## Step 3: Tunnel Creation

A secure encrypted tunnel is created using VPN protocols.

## Step 4: Encryption

All outgoing data:

* Is encrypted before leaving the device
* Sent through the secure tunnel

## Step 5: Decryption

VPN server:

* Decrypts the data
* Forwards it to the destination

Return traffic:

* Is encrypted by VPN server
* Decrypted by client



# 5. VPN Tunneling

Tunneling means:

Original packet is encapsulated inside another packet.

Example:

```
Original Data → Encrypted → Wrapped inside VPN packet → Sent over Internet
```

Common tunneling protocols:

* PPTP
* L2TP
* IPsec
* SSL/TLS
* OpenVPN
* WireGuard



# 6. Types of VPN

## 1. Remote Access VPN

* Individual user connects to company network
* Common for remote workers

Example:
Home laptop → Company VPN Server



## 2. Site-to-Site VPN

Connects two networks together.

Example:
Branch office ↔ Head office

Two routers create a VPN tunnel.



# 7. Common VPN Protocols

## 1. PPTP (Point-to-Point Tunneling Protocol)

* Older protocol
* Fast but not secure
* Mostly obsolete

## 2. L2TP/IPsec

* L2TP handles tunneling
* IPsec handles encryption
* More secure than PPTP

## 3. IPsec

* Works at Network Layer
* Provides strong encryption
* Used in site-to-site VPNs

Modes:

* Transport Mode
* Tunnel Mode

## 4. SSL/TLS VPN

* Uses HTTPS
* Common in browsers
* Used in OpenVPN

## 5. WireGuard

* Modern VPN protocol
* Faster and simpler
* Strong cryptography



# 8. IPsec VPN Working

IPsec provides:

* Authentication Header (AH)
* Encapsulating Security Payload (ESP)

Most VPNs use ESP.

IPsec Process:

1. IKE (Internet Key Exchange) negotiates keys.
2. Secure channel is created.
3. Data is encrypted using symmetric encryption (AES).



# 9. VPN Encryption

VPN typically uses:

For encryption:

* AES

For key exchange:

* RSA or Diffie-Hellman

For integrity:

* SHA-256

Hybrid encryption:

* Symmetric key encrypts data
* Public key encrypts symmetric key



# 10. What Happens to IP Address?

Without VPN:

* Your real public IP is visible.

With VPN:

* Websites see VPN server’s IP.
* Your real IP is hidden.



# 11. Advantages of VPN

* Secure communication over Internet
* Protects data from hackers
* Remote access to internal resources
* IP masking
* Bypass geographic blocks



# 12. Limitations of VPN

* Slower speed due to encryption
* Requires trust in VPN provider
* Does not guarantee anonymity
* Cannot protect against malware



# 13. VPN vs Proxy

| Feature             | VPN  | Proxy           |
| ---------------- | ---- | --------------- |
| Encryption          | Yes  | Usually No      |
| Security            | High | Low             |
| Covers whole device | Yes  | Often app-based |
| IP masking          | Yes  | Yes             |

VPN is more secure than proxy.



# 14. Summary

* VPN creates encrypted tunnel over public network.
* Protects confidentiality and integrity.
* Uses tunneling and encryption.
* Types: Remote access and Site-to-site.
* Common protocols: IPsec, SSL/TLS, WireGuard.
* Hides real IP address.




