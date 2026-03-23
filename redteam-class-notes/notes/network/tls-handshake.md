# TLS Protocol — Deep Technical Breakdown

**TLS (Transport Layer Security)** secures communication over untrusted networks.
It provides:

* **Confidentiality** (encryption)
* **Integrity** (tamper detection)
* **Authentication** (server, optionally client)

TLS sits **above TCP** and below application protocols like HTTPS, SMTP, IMAP, etc.



# 1️⃣ Where TLS Lives in the Stack

| Layer          | Protocol          |
| ----------- | ----------------- |
| Application    | HTTPS, SMTP, etc. |
| Security Layer | TLS               |
| Transport      | TCP               |
| Network        | IP                |

TLS requires a reliable transport → **TCP**.



# 2️⃣ Evolution of TLS

TLS evolved from:

* SSL (deprecated)
* TLS 1.0 (obsolete)
* TLS 1.2 (still widely used)
* TLS 1.3 (modern standard)

TLS 1.3 dramatically simplifies the handshake and improves security.



# 3️⃣ Core Cryptographic Concepts Used in TLS

TLS combines multiple cryptographic primitives:

### 1. Asymmetric Cryptography

Used during handshake for:

* Authentication
* Key exchange

Examples:

* RSA
* ECDSA (Elliptic Curve Digital Signature Algorithm)
* ECDHE (Elliptic Curve Diffie-Hellman Ephemeral)

### 2. Symmetric Cryptography

Used after handshake for data encryption:

* AES-GCM
* ChaCha20-Poly1305

### 3. Hashing & HMAC

* SHA-256 / SHA-384
* Used for integrity and key derivation



# 4️⃣ TLS 1.2 Handshake — Step-by-Step

## Full Handshake Flow


![Image](https://www.researchgate.net/publication/234811497/figure/fig1/AS%3A299814349754368%401448492719291/TLS-key-transport-with-RSA.png)


### Step 1 — ClientHello

Client sends:

* TLS version supported
* Random number (Client Random)
* Supported cipher suites
* Supported extensions (SNI, ALPN, etc.)



### Step 2 — ServerHello

Server responds with:

* Selected TLS version
* Server random
* Selected cipher suite
* Session ID



### Step 3 — Certificate

Server sends:

* X.509 certificate
* Public key
* CA signature

Certificate validation ensures:

* Trusted CA
* Valid domain
* Not expired



### Step 4 — ServerKeyExchange (if needed)

If using ECDHE:

* Server sends ephemeral public key



### Step 5 — ClientKeyExchange

Client:

* Generates premaster secret
* Encrypts with server public key (RSA)
  OR
* Sends its ECDHE public key



### Step 6 — Key Derivation

Both sides compute:

```
Master Secret = PRF(premaster, client_random, server_random)
```

Then derive:

* Encryption keys
* MAC keys
* IVs



### Step 7 — ChangeCipherSpec

Both sides switch to encrypted communication.



### Step 8 — Finished

Each side sends a hash of handshake messages (encrypted).

Handshake complete.



# 5️⃣ TLS 1.3 Handshake (Modern Version)

TLS 1.3 removes:

* RSA key exchange
* Static DH
* Weak ciphers
* Multiple round trips

## Simplified Flow

![Image](https://supertokens.com/static/9cff8404dcf549f68f947fc906ae76a9/29007/tls1.3.png)

### Step 1 — ClientHello

Includes:

* Supported cipher suites
* Key share (ECDHE public key)
* Supported groups
* Extensions



### Step 2 — ServerHello

Includes:

* Selected cipher
* Server key share

At this point:

* Shared secret computed
* Encrypted communication begins



### Step 3 — Encrypted Extensions

Server sends encrypted:

* Configuration parameters



### Step 4 — Certificate + CertificateVerify

Server proves ownership of private key.



### Step 5 — Finished

Handshake complete.

TLS 1.3 requires only **1 round-trip (1-RTT)**.



# 6️⃣ TLS Key Schedule (Deep Dive)

TLS 1.3 uses HKDF-based key derivation:

```
Early Secret
Handshake Secret
Master Secret
```

Each stage derives:

* Traffic secrets
* Application keys
* Resumption keys

All derived from:

* Diffie-Hellman shared secret
* Transcript hash



# 7️⃣ Cipher Suite Structure

In TLS 1.2 example:

```
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
```

Breakdown:

* ECDHE → Key exchange
* RSA → Authentication
* AES_256_GCM → Encryption
* SHA384 → Hash

TLS 1.3 simplifies:

```
TLS_AES_128_GCM_SHA256
```

Key exchange & auth are separate.



# 8️⃣ Forward Secrecy

Achieved with:

* ECDHE

Even if server private key is later compromised:

* Past sessions remain secure

TLS 1.3 enforces forward secrecy.



# 9️⃣ Session Resumption

Avoids full handshake.

Methods:

* Session IDs (TLS 1.2)
* Session Tickets
* Pre-Shared Keys (TLS 1.3)

Allows:

* 0-RTT data (TLS 1.3)



# 🔟 Certificate Trust Model

Certificates chain up to:

* DigiCert
* Let's Encrypt
* GlobalSign

Browsers ship with trusted root CAs.

Validation checks:

* Signature
* Domain match
* Expiration
* Revocation (CRL/OCSP)



# 1️⃣1️⃣ TLS Record Layer

After handshake, TLS uses:

* Record protocol
* Fragments data
* Encrypts
* Adds MAC or AEAD tag

Structure:

* Content Type
* Version
* Length
* Encrypted payload



# 1️⃣2️⃣ Common TLS Attacks (Historical)

* BEAST
* POODLE
* Heartbleed
* Lucky13

Most mitigated in TLS 1.3.



# 1️⃣3️⃣ TLS in Real Life

Used in:

* HTTPS
* VPNs
* Email encryption
* Secure APIs
* HTTP/2 & HTTP/3 (QUIC uses TLS 1.3 internally)



# 1️⃣4️⃣ Wireshark View of a TLS Handshake

Typical capture shows:

1. ClientHello
2. ServerHello
3. Certificate
4. ServerHelloDone
5. ClientKeyExchange
6. ChangeCipherSpec
7. Finished

After that → Encrypted Application Data



# Final Summary

TLS is:

* A hybrid cryptographic protocol
* Designed for authentication + confidentiality + integrity
* Complex in TLS 1.2
* Streamlined and hardened in TLS 1.3
* Foundational to secure internet communication




