# 1. What are SSL and TLS?

**SSL (Secure Sockets Layer)** and **TLS (Transport Layer Security)** are cryptographic protocols used to secure communication over a network.

They provide:

* Confidentiality (encryption)
* Integrity (data not modified)
* Authentication (verify identity)

TLS is the modern, secure version of SSL.



# 2. SSL vs TLS

## SSL

* Developed by Netscape
* Versions:

  * SSL 2.0 (insecure)
  * SSL 3.0 (deprecated)
* No longer considered secure

## TLS

* Successor to SSL
* Versions:

  * TLS 1.0 (deprecated)
  * TLS 1.1 (deprecated)
  * TLS 1.2 (widely used)
  * TLS 1.3 (recommended)

Today, when people say "SSL," they usually mean TLS.



# 3. Where TLS is Used

* HTTPS (secure websites)
* Email (SMTPS, IMAPS, POP3S)
* VPNs
* Secure APIs
* VoIP
* Secure file transfers

Example:

```
https://example.com
```

HTTPS = HTTP over TLS.



# 4. Goals of TLS

1. Confidentiality – Data is encrypted.
2. Integrity – Data cannot be modified without detection.
3. Authentication – Server (and sometimes client) identity is verified.



# 5. How TLS Works (Simplified Handshake Process)

TLS uses **hybrid cryptography**:

* Asymmetric encryption for key exchange
* Symmetric encryption for data transfer



## Step 1: Client Hello

Client sends:

* TLS version supported
* Supported cipher suites
* Random number



## Step 2: Server Hello

Server responds with:

* Chosen TLS version
* Chosen cipher suite
* Server certificate
* Random number



## Step 3: Certificate Verification

Client:

* Verifies server certificate
* Checks Certificate Authority (CA)
* Validates domain name
* Checks expiration

If valid → Continue



## Step 4: Key Exchange

Client and server:

* Generate shared secret
* Often use:

  * RSA
  * Diffie-Hellman
  * ECDHE (modern)

This creates a session key.



## Step 5: Secure Communication Begins

All further data:

* Encrypted using symmetric encryption (e.g., AES)
* Verified using MAC or AEAD



# 6. Cryptography Used in TLS

## 1. Asymmetric Encryption

Used during handshake.

Examples:

* RSA
* ECDHE

## 2. Symmetric Encryption

Used for actual data transfer.

Examples:

* AES
* ChaCha20

## 3. Hashing

Used for integrity.

Examples:

* SHA-256
* SHA-384



# 7. TLS 1.2 vs TLS 1.3

| Feature         | TLS 1.2      | TLS 1.3    |
| ------------ | ------------ | ---------- |
| Handshake Speed | Slower       | Faster     |
| Cipher Suites   | Many options | Simplified |
| Security        | Strong       | Stronger   |
| Forward Secrecy | Optional     | Mandatory  |

TLS 1.3 removes weak algorithms and improves performance.



# 8. Digital Certificates

TLS relies on X.509 certificates.

Certificate contains:

* Public key
* Domain name
* Issuer (CA)
* Expiration date
* Digital signature

Certificate Authorities:

* Verify identity
* Issue certificates
* Create trust chain



# 9. Public Key Infrastructure (PKI)

PKI includes:

* Certificate Authority (CA)
* Registration Authority (RA)
* Certificates
* Revocation systems (CRL, OCSP)

PKI enables trust in TLS.



# 10. Common TLS Cipher Suite Example

Example:

```
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
```

Breakdown:

* ECDHE → Key exchange
* RSA → Authentication
* AES_256_GCM → Encryption
* SHA384 → Hash algorithm



# 11. TLS vs SSL Summary

| Feature         | SSL          | TLS      |
| ------------ | ------------ | -------- |
| Security        | Weak         | Strong   |
| Supported Today | No           | Yes      |
| Encryption      | Yes          | Yes      |
| Handshake       | Older design | Improved |

SSL is obsolete.
TLS is the current secure standard.



# 12. TLS vs HTTPS

* TLS = Security protocol
* HTTPS = HTTP running over TLS

HTTPS uses TLS to encrypt web traffic.



# 13. Advantages of TLS

* Protects data in transit
* Prevents eavesdropping
* Prevents tampering
* Verifies server identity
* Supports forward secrecy



# 14. Limitations

* Does not protect data at rest
* Requires certificate management
* Misconfiguration can weaken security
* Does not prevent malware



# 15. Summary

* SSL is deprecated; TLS replaced it.
* TLS secures communication using encryption.
* Uses hybrid cryptography.
* Relies on digital certificates and PKI.
* TLS 1.3 is the most secure modern version.
* Widely used in HTTPS and secure communication systems.


