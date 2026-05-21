
---

# Module 20: Cryptography

## Learning Objectives

- Describe cryptography concepts
- Understand different encryption algorithms
- Use different cryptography tools
- Apply various applications of cryptography
- Describe various cryptography attacks
- Use different cryptanalysis tools

---

## Cryptography Concepts and Encryption Algorithms

### Cryptography

- **Definition:** Practice of concealing information by converting plaintext (readable) into ciphertext (unreadable) using a key or encryption scheme.
- **Origin:** Greek *kryptos* (hidden) + *graphia* (writing) = "art of secret writing".
- **Purpose:** Protects confidential data (email, web transactions, personal/corporate data, e-commerce).

### Objectives of Cryptography

| Objective | Description |
|-----------|-------------|
| **Confidentiality** | Information accessible only to authorized parties |
| **Integrity** | Trustworthiness of data; prevents improper/unauthorized changes |
| **Authentication** | Assurance that communication/document/data is genuine |
| **Non-repudiation** | Sender cannot deny sending; recipient cannot deny receiving |

### Cryptography Process

Plaintext → **Encryption Algorithm (RSA, DES, AES)** → Ciphertext → **Decryption** → Plaintext

### Types of Cryptography

#### Symmetric Encryption (Secret-key, Shared-key, Private-key)

- Same key for encryption and decryption.
- **Strengths:** Faster, less processing power, can be implemented in ASIC.
- **Weaknesses:** Lack of secure channel to exchange key; difficult to manage many shared keys; widespread compromise if key is stolen; no assurance of origin/authenticity.
- **Vulnerable to:** Dictionary, brute-force attacks.

#### Asymmetric Encryption (Public-key)

- Different keys: **Public key** (available to anyone) and **Private key** (held only by owner).
- **Process:**
  1. Sender finds recipient's public key.
  2. Encrypts message with public key.
  3. Recipient decrypts with private key.
- **Strengths:** No key distribution required; enhanced security (private key never shared); provides digital signatures (non-repudiation).
- **Weaknesses:** Slow, requires high processing power; if private key compromised, widespread compromise possible; vulnerable to MITM and brute-force.

### Government Access to Keys (GAK)

- Statutory obligation to disclose cryptographic keys to government agencies.
- **Key escrow:** Third party (usually government) stores keys; can use under warrant.
- **Risks:** Privacy concerns; single key protecting other keys; agency may not know value of protected information.

---

## Ciphers

- **Cipher:** Algorithm for performing encryption/decryption.
- **Encipherment:** Plaintext → cipher/code.
- **Decipherment:** Reverse process.

### Classification of Ciphers

| Category | Sub-category | Examples |
|----------|--------------|----------|
| **Classical Ciphers** | Substitution cipher | Beale, autokey, Gronsfeld, Hill ("HELLO WORLD" → "PSTER HGFST") |
| | Transposition cipher | Rail fence, route, Myszkowski ("CRYPTOGRAPHY" → "AOYCRGPTYRHP") |
| **Modern Ciphers** | By key type: Symmetric-key, Asymmetric-key | - |
| | By input data: Block cipher, Stream cipher | - |

#### Block Cipher vs. Stream Cipher

| Feature | Block Cipher | Stream Cipher |
|---------|--------------|---------------|
| Operation | Fixed-size block of bits | One bit at a time |
| Key type | Symmetric | Symmetric |
| Examples | DES, AES, IDEA | RC4, SEAL |

---

## Symmetric Encryption Algorithms

| Algorithm | Cipher Type | Key Size (bits) | Block Size (bits) | Application Areas |
|-----------|-------------|-----------------|-------------------|-------------------|
| **DES** | Block | 56 | 64 | Legacy systems |
| **3DES** | Block | 112, 168 | 64 | Financial services, payment systems |
| **AES** | Block | 128, 192, 256 | 128 | Secure comms, storage encryption, government |
| **RC4** | Stream | 40-2048 (variable) | - | HTTPS, WEP/WPA, streaming |
| **RC5** | Block | 0-2048 (variable) | 32,64,128 | Cryptographic libraries |
| **RC6** | Block | 128,192,256 | 128 | AES competition finalist |
| **Blowfish** | Block | 32-448 (variable) | 64 | Replacement for DES |
| **Twofish** | Block | 128,192,256 | 128 | File/disk encryption |
| **IDEA** | Block | 128 | 64 | PGP |
| **Serpent** | Block | 128,192,256 | 128 | High-security, AES finalist |
| **Camellia** | Block | 128,192,256 | 128 | Japanese encryption standard |
| **TEA** | Block | 128 | 64 | Lightweight encryption, embedded |
| **CAST-128** | Block | 40-128 | 64 | GPG, PGP |
| **ChaCha20** | Stream | 256 | - | Modern encryption protocols |

### DES (Data Encryption Standard)

- 64-bit secret key (56 bits random + 8 bits error detection).
- Block cipher operating on 64-bit blocks.
- **Weakness:** Inherent weakness against today's technologies.

### 3DES (Triple DES)

- Performs DES three times with three keys (K1, K2, K3).
- **Process:** Encrypt with K1 → Decrypt with K2 → Encrypt with K3.
- **Key options:**
  - All three keys independent (most secure).
  - K1 and K3 identical.
  - All three keys same (least secure).

### AES (Advanced Encryption Standard)

- NIST specification; symmetric-key block cipher.
- Block size: 128 bits.
- Key sizes: 128 (AES-128), 192 (AES-192), 256 (AES-256).
- **AES Pseudocode (simplified):**
  ```
  state = in
  AddRoundKey(state, w[0])
  for round = 1 to Nr-1:
      SubBytes(state)
      ShiftRows(state)
      MixColumns(state)
      AddRoundKey(state, w[round*Nb])
  SubBytes(state)
  ShiftRows(state)
  AddRoundKey(state, w[Nr*Nb])
  out = state
  ```

### RC4, RC5, RC6

- **RC4:** Variable key-size stream cipher; byte-oriented; used in SSL.
- **RC5:** Parameterized block cipher; variable block size (32,64,128 bits), key size (0-2040 bits), rounds (0-255). Operations: integer addition, bitwise XOR, variable rotation.
- **RC6:** Derived from RC5; uses integer multiplication; four 4-bit registers (vs two 2-bit in RC5).

### Blowfish

- 16-round Feistel cipher; 64-bit blocks; key size 32-448 bits.
- **Two parts:** Key expansion (P-array of 18 32-bit subkeys + four 32-bit S-boxes of 256 entries each) and data encryption.

### Twofish

- 128-bit block cipher; key sizes up to 256 bits; Feistel cipher.
- Finalist in AES contest.

### Threefish

- Part of Skein algorithm (NIST SHA-3 contest).
- Block/key sizes: 256, 512, 1024 bits.
- Uses only ARX (Addition-Rotation-XOR); no S-boxes (prevents cache timing attacks).

### Serpent

- 128-bit block cipher; key sizes 128,192,256 bits; 32 rounds.
- One of the most secure AES finalists, but slower (more rounds).

### TEA (Tiny Encryption Algorithm)

- Feistel cipher; 64 rounds (implemented in pairs called cycles).
- 128-bit key operating on 64-bit block.
- Uses constant **delta** = 2³² / golden ratio.

### CAST-128 (CAST5)

- 12- or 16-round Feistel network; 64-bit blocks; key size 40-128 bits.
- Uses 8×32-bit S-boxes based on bent functions.
- Default cipher in GPG and PGP.

### GOST Block Cipher (Magma)

- 32-round Feistel network; 64-bit blocks; 256-bit key.
- Key scheduling: 256-bit key broken into eight 32-bit subkeys, each used four times.

### Camellia

- 18 rounds (128-bit keys) or 24 rounds (256-bit keys); Feistel cipher; 128-bit blocks.
- Part of TLS protocol; cannot be brute-forced even with 128-bit key.

---

## Asymmetric Encryption Algorithms

| Algorithm | Key Size (bits) | Application Areas |
|-----------|-----------------|-------------------|
| **RSA** | Variable | Encryption, digital signatures, key exchange |
| **DSA** | Variable | Digital signatures |
| **Diffie-Hellman** | Variable | Key exchange, secure communication |
| **ECC** | 160-521 | Encryption, digital signatures, key exchange |
| **ElGamal** | Variable | Encryption, key exchange |

### DSA (Digital Signature Algorithm)

- FIPS for digital signatures; creates 320-bit signature with 512-1024-bit security.
- **Processes:** Signature Generation (private key), Signature Verification (public key).

**DSA Algorithm (Key Generation for entity A):**
1. Select prime q (2¹⁵⁹ < q < 2¹⁶⁰)
2. Select t (0≤t≤8), prime p with 2⁵¹¹⁺⁶⁴ᵗ < p < 2⁵¹²⁺⁶⁴ᵗ such that q divides (p-1)
3. Select generator α = g⁽ᵖ⁻¹⁾/ᵠ mod p (g ∈ Zᵖ*, α ≠ 1)
4. Select random d (1 ≤ d ≤ q-1)
5. Compute y = αᵈ mod p
6. Public key: (p,q,α,y); Private key: d

### RSA (Rivest-Shamir-Adleman)

- Public-key cryptosystem for encryption and authentication.
- Security depends on difficulty of factoring large primes.

**RSA Key Generation:**
1. Generate two large distinct primes p, q
2. Compute n = p×q and φ = (p-1)(q-1)
3. Choose e (1 < e < φ) with gcd(e, φ) = 1
4. Compute d such that e×d ≡ 1 (mod φ)
5. Public key: (n, e); Private key: d
6. Destroy p and q

**RSA Signature Scheme:**
- Sign: s = m̄ᵈ mod n (where m̄ = R(m))
- Verify: m̄ = sᵉ mod n

**RSA Example:**
- P=61, Q=53 → PQ=3233
- E=17, D=2753
- Encrypt(123) = 123¹⁷ mod 3233 = 855
- Decrypt(855) = 855²⁷⁵³ mod 3233 = 123

### Diffie-Hellman (Key Exchange)

- Allows two parties to establish a shared key over insecure channel.
- **Parameters:** Prime p and generator g (integer < p).
- **Process (Alice & Bob):**
  - Alice: private a, public gᵃ mod p
  - Bob: private b, public gᵇ mod p
  - Shared secret: gᵃᵇ mod p
- **Does NOT provide authentication** (vulnerable to MITM).

### Elliptic Curve Cryptography (ECC)

- Public-key cryptography using elliptic curves (algebraic structure).
- **Key size comparison:**
  | ECC Key Size | RSA Key Size |
  |--------------|--------------|
  | 160-223 | 1024 |
  | 224-255 | 2048 |
  | 256-383 | 3072 |
  | 384-511 | 7680 |
  | 512+ | 15360 |

### YAK (Authenticated Key Exchange Protocol)

- Public-key based; requires PKI.
- Variant of HMQV using zero-knowledge proofs (ZKP).
- **Objectives:** Private key security, full forward secrecy, session key security.

---

## Message Digest (One-Way Hash) Functions

- **Definition:** Calculates unique fixed-size bit string (message digest) from arbitrary block of information.
- **Properties:**
  - Changing one input bit → 50% chance each output bit changes.
  - Computationally infeasible to find two files with same message digest (collision-resistant).
  - Cannot be reversed (one-way).
- **Role:** Provides integrity, used in digital signatures and MACs.

### Message Digest Functions (Summary Table)

| Algorithm | Output Size (bits) | Block Size (bits) | Rounds | Security (bits) | Applications |
|-----------|-------------------|-------------------|--------|-----------------|---------------|
| MD2 | 128 | 128 | 18 | 128 | Legacy, checksum |
| MD4 | 128 | 512 | 48 | 64 | Obsolete |
| MD5 | 128 | 512 | 64 | 64 | File verification, checksum |
| MD6 | 224-512 | 512 | Variable | 128-256 | Cryptographic apps |
| SHA-0 | 160 | 512 | 80 | 0 | Obsolete |
| SHA-1 | 160 | 512 | 80 | 80 | Legacy systems, TLS |
| SHA-2 (224,256,384,512) | 224-512 | 512-1024 | 64-80 | 112-256 | Secure apps, SSL |
| SHA-3 (224-512) | 224-512 | 1088-576 | Variable | 112-256 | Next-gen crypto |
| RIPEMD-160 | 160 | 512 | 160 | 80 | Crypto apps |
| WHIRLPOOL | 512 | 512 | 10 | 256 | Secure hashing |
| Tiger | 192 | 512 | 24 | 192 | High-speed apps |
| BLAKE2 | 256-512 | 512-1024 | 10-14 | 128-256 | High-speed hashing |

### MD5

- Takes arbitrary length input → 128-bit fingerprint.
- Widely used but **not collision-resistant** (use MD6, SHA-2, SHA-3 instead).

### MD6

- Uses Merkle-tree-like structure for parallel computation.
- Resistant to differential cryptanalysis.

### SHA (Secure Hash Algorithm)

- Developed by NIST (FIPS PUB 180).
- **SHA-0:** Original 160-bit (withdrawn due to flaw).
- **SHA-1:** 160-bit digest; maximum message length 2⁶⁴-1 bits. No longer approved (cryptographic weaknesses).
- **SHA-2:** Family: SHA-256 (32-bit words), SHA-512 (64-bit words); truncated: SHA-224, SHA-384.
- **SHA-3:** Uses sponge construction; internal structure differs significantly.

### RIPEMD-160

- 160-bit hash; developed by Hans Dobbertin, Antoon Bosselaers, Bart Preneel.
- Compression function: 80 stages (5 blocks × 16 times); repeated twice, combined with modulo 32 addition.

### HMAC

- **HMAC (Hash-based Message Authentication Code):** Combines cryptographic key with cryptographic hash function.
- Provides both integrity and authentication.

### Multilayer Hashing (Nested/Recursive Hashing)

- Hash function applied multiple times to input or previous hash output.
- Makes reverse engineering and brute-force more difficult.
- **Tool:** CyberChef.

---

## Hardware-Based Encryption

- Uses computer hardware to assist/replace software encryption.
- **Advantages:** Rapid processing, tamper-resistant key storage, prevents unauthorized code.
- **Types:**

| Device | Description |
|--------|-------------|
| **TPM** (Trusted Platform Module) | Crypto-processor on motherboard; stores encryption keys; authenticates platform integrity, full disk encryption, password storage, software license protection |
| **HSM** (Hardware Security Module) | External device; manages, generates, stores keys; enhanced encryption for keys >256 bits |
| **USB Encryption** | Onboard encryption; requires credentials; prevents malware distribution and data leakage |
| **Hard Drive Encryption** | Internal drive; requires TPM or HSM; military-grade AES-256 |

---

## Quantum Cryptography

- Based on quantum mechanics (Quantum Key Distribution - QKD).
- Uses **photons** with spinning traits; photons change shape through filters.
- **Polarization:**
  - Horizontal (-): 0
  - Vertical (|): 1
  - Backslash (/): 1
  - Forward slash (\): 0
- Attackers can eavesdrop but **cannot manipulate** data (photons transferred through arbitrary filters; wrong filter choice distorts polarization).

---

## Other Encryption Techniques

### Homomorphic Encryption

- Allows mathematical operations on ciphertext while data remains encrypted.
- **Key holder** performs both encryption and decryption.
- Allows untrusted entity to manipulate data without decryption.

### Post-Quantum Cryptography (Quantum-Resistant)

- Designed to protect against attacks from both conventional and quantum computers.
- Replaces current vulnerable cryptosystems.

### Lightweight Cryptography

- Aimed at low-powered devices (RFID tags, sensors, IoT).
- Uses less power/resources without compromising security.

---

## Cipher Modes of Operation (Block Cipher Modes)

| Mode | Description | Issue |
|------|-------------|-------|
| **ECB** (Electronic Code Book) | Plaintext divided into fixed blocks; each block encrypted separately with same key | Same plaintext blocks produce same ciphertext → analysts can predict plaintext |
| **CBC** (Cipher Block Chaining) | Each plaintext block XORed with previous ciphertext block; uses IV for first block | Error in one ciphertext block propagates to subsequent blocks |
| **CFB** (Cipher Feedback) | Previously generated ciphertext used as feedback; uses shift register | Data loss due to shift registers makes cryptanalysis difficult |
| **Counter Mode** | Uses counter value XORed with encrypted counter; no error propagation | Requires synchronized counters |

### Modes of Authenticated Encryption (AE)

- Provides **integrity + confidentiality**.
- Combines ciphertext with MAC → prevents chosen ciphertext attacks.

| Mode | Process |
|------|---------|
| **Encrypt-then-MAC (EtM)** | Encrypt plaintext → generate MAC from ciphertext → transmit both (highest security) |
| **Encrypt-and-MAC (E&M)** | Generate MAC from plaintext → encrypt plaintext → transmit both |
| **MAC-then-encrypt (MtE)** | Generate MAC from plaintext → combine with plaintext → encrypt |

### AEAD (Authenticated Encryption with Associated Data)

- Adds additional data to ciphertext (header unencrypted for source verification; payload encrypted for confidentiality).
- Thwarts chosen ciphertext attacks.

---

## Cryptography Tools

| Tool | Description |
|------|-------------|
| **BCTextEncoder** | Encodes/decodes text data; uses public key and password-based encryption |
| **CryptoForge, AxCrypt, Concealer, SensiGuard, Cypherix** | Additional cryptography tools |

---

## Applications of Cryptography

### Public Key Infrastructure (PKI)

- Set of hardware, software, people, policies, procedures to create, manage, distribute, use, store, and revoke digital certificates.
- Binds public keys to user identities via Certification Authority (CA).

**PKI Components:**
- **Certificate Management System:** Generates, distributes, stores, verifies certificates
- **Digital Certificates:** Establishes credentials for online transactions
- **Validation Authority (VA):** Stores certificates with public keys
- **Certification Authority (CA):** Issues and verifies digital certificates
- **End User:** Requests, manages, uses certificates
- **Registration Authority (RA):** Verifier for CA

**PKI Process:**
1. Subject applies to RA for certificate.
2. RA verifies identity, requests CA to issue public key certificate.
3. CA issues certificate, sends updated info to VA.
4. User signs message with private key, sends to client (including public key certificate).
5. Client inquires with VA about certificate validity.
6. VA compares with CA information → determines valid/invalid.

### Certification Authorities (CAs)

| CA | Description |
|----|-------------|
| **Comodo** | PKI digital certificates, SSL encryption (128/256), SGC, Comodo Certificate Manager, EPKI Manager |
| **IdenTrust** | CA for banks, corporates, governments, healthcare; digital signing, NIST SP 800-171 compliance |
| **DigiCert CertCentral** | TLS/SSL certificate lifecycle management |
| **GoDaddy** | SHA-2 hash algorithm, 2048-bit encryption, unlimited servers |

### Signed Certificate vs. Self-Signed Certificate

| Feature | Signed Certificate (CA) | Self-Signed Certificate |
|---------|------------------------|-------------------------|
| Issuer | Trusted CA | User (using tools like Adobe Acrobat Reader, Java keytool, Apple Keychain) |
| Contents | Certificate holder name, serial number, expiration, public key, CA digital signature | User name, user's public key, user's digital signature |
| Verification | VA verifies | User verifies directly |

### Digital Signature

- Uses asymmetric cryptography to simulate handwritten signature in digital form.
- **Process:**
  - Hash function creates unique fingerprint (hash value).
  - Sender encrypts hash with private key → digital signature.
  - Receiver decrypts with sender's public key and compares hash values.
- May be further protected by encrypting signed email.

### Secure Sockets Layer (SSL)

- Application layer protocol; provides secure authentication between client and server.
- Uses RSA asymmetric encryption.
- **Three properties:** Private channel, Authenticated channel, Reliable channel.
- **SSL Handshake Protocol (steps):**
  1. Client hello → Server hello (protocol version, session ID, cipher suite, compression method)
  2. Server sends certificate (and optionally server-key exchange)
  3. Server sends "hello done"
  4. Client responds with certificate (if requested) and client-key exchange
  5. Client sends "Change cipher spec" → finished
  6. Server sends "Change cipher spec" → finished → application data exchange

### Transport Layer Security (TLS)

- Establishes secure connection; ensures privacy and integrity.
- Uses symmetric key for bulk encryption, asymmetric for authentication/key exchange, MAC for message integrity.
- **Two layers:**
  1. **TLS Record Protocol:** Fragments, compresses, applies MAC, encrypts outgoing data; reassembles, decrypts, verifies incoming data.
  2. **TLS Handshake Protocol:** Authenticates peers, selects encryption algorithm/cryptographic keys.

### Cryptography Toolkits

| Toolkit | Description |
|---------|-------------|
| **OpenSSL** | Open-source SSL/TLS implementation; command-line tool for private/public keys, X.509 certificates, CSRs, CRLs |
| **wolfSSL, AES Crypto Toolkit, Libsodium, Crypto++, PyCrypto** | Additional toolkits |

### Pretty Good Privacy (PGP)

- Protocol for encryption/decryption with authentication and cryptographic privacy.
- **Hybrid cryptosystem:** Combines conventional (faster) and public-key cryptography.
- **Encryption:** Compress data → generate random one-time secret key → encrypt plaintext → encrypt random key with recipient's public key → send both.
- **Decryption:** Recipient's private key recovers random key → decrypts ciphertext.
- Uses RSA (key transport) + IDEA (bulk encryption).

### GNU Privacy Guard (GPG)

- Free implementation of OpenPGP standard.
- Uses both symmetric and asymmetric cryptography.
- **Encryption:** Sign file with sender's private key → encrypt with receiver's public key.
- **Decryption:** Decrypt with receiver's private key → verify signature with sender's public key.

### Web of Trust (WOT)

- Trust model for PGP, OpenPGP, GPG.
- **Decentralized:** Everyone in network is a CA; signs for other trusted entities.
- Users have ring of public keys; introduces other trusted users.

### Encrypting Email Messages

**Outlook S/MIME Encryption:**
- File → Options → Trust Center → Trust Center Settings → Email Security → Settings → Choose S/MIME certificate for Signing and Encryption certificates.

**Microsoft 365 Message Encryption (OME):**
- Options → Encrypt → Choose constraints (Encrypt-Only, Do Not Forward).

**Apple Mail:**
- Blue tick (✓) = digitally signed.
- Closed lock (🔒) = encrypted.

**OpenPGP (FlowCrypt for Gmail):**
- Configure browser extension → Secure Compose → Encrypt, Sign and Send.

### Email Encryption Tools

- RMail (open tracking, delivery proof, encryption, e-signatures)
- Mailvelope, Virtru, Webroot, Proofpoint, Paubox

### Disk Encryption

- Encrypts every bit of data on a disk/disk volume.
- Converts data into unreadable code using software/hardware.

#### Disk Encryption Tools

| Tool | Description |
|------|-------------|
| **VeraCrypt** | On-the-fly encryption; entire file system encrypted (file names, folder names, free space, metadata) |
| **Rohos Disk Encryption** | Hidden encrypted partitions on computer, USB, cloud (Google Drive, OneDrive, Dropbox); AES-256 |
| **BitLocker** | Uses TPM; encrypts entire Windows volume; protects offline data and OS |
| **FileVault (macOS)** | XTS-AES-128 encryption with 256-bit key; startup disk encryption |
| **Cryptsetup (Linux)** | DMCrypt kernel module; LUKS, TrueCrypt, VeraCrypt, BitLocker formats |

### Blockchain

- Distributed ledger technology (DLT); records transaction history in blocks.
- **Elements per block:** Data (transaction details), Hash, Hash of previous block.
- **First block:** Genesis block (hash of previous = 0).
- **Security:** Hash comparison + Proof of Work (mining).

**Blockchain Variants:**
| Type | Characteristics |
|------|-----------------|
| **Public (Permissionless)** | No central authority; decentralized; anyone can join (Bitcoin, Ethereum) |
| **Private (Permissioned)** | Central authority decides participants (Hyperledger, Ripple) |
| **Federated (Consortium)** | Group of organizations manage blockchain (EWF, R3) |
| **Hybrid** | Combination of public and private; selected records public (IBM Food Trust) |

---

## Cryptanalysis

- **Definition:** Study of ciphers, ciphertext, or cryptosystems to identify vulnerabilities and extract plaintext without knowing key.

### Cryptanalysis Methods

| Method | Description |
|--------|-------------|
| **Linear Cryptanalysis** | Known plaintext attack; uses linear approximations of block cipher behavior; Matsui's Algorithm; DES: 2⁵⁶ brute-force vs 2⁴³ known plaintexts |
| **Differential Cryptanalysis** | Examines differences in input and how they affect output differences; originally chosen plaintext, now known plaintext/ciphertext |
| **Integral Cryptanalysis** | Extension of differential; holds b-k bits constant, runs other k bits through all 2ᵏ possibilities; for k>1 |
| **Quantum Cryptanalysis** | Uses quantum computer; Shor's algorithm (factoring), Grover's algorithm (faster brute-force) |

### Cryptography Attacks

| Attack | Description |
|--------|-------------|
| **Ciphertext-only** | Attacker has only ciphertexts; analyzes patterns |
| **Adaptive Chosen-plaintext** | Interactive queries; chooses subsequent plaintexts based on previous encryptions |
| **Chosen-plaintext** | Attacker obtains ciphertexts for plaintexts of own choosing |
| **Related-Key** | Obtains ciphertexts encrypted under two different (closely related) keys |
| **Dictionary** | Builds dictionary of plaintext-ciphertext pairs |
| **Known-plaintext** | Has some plaintext blocks and corresponding ciphertext |
| **Chosen-ciphertext** | Obtains plaintexts for arbitrary chosen ciphertexts (Lunchtime/Midnight, Adaptive) |
| **Rubber Hose** | Extracts secrets via coercion or torture |
| **Chosen-key** | Breaks n-bit key cipher into 2ⁿ/² operations |
| **Timing** | Measures execution times of modular exponentiation operations |
| **MITM** | Intercepts communication between client and server; decrypts encrypted content |

### Code Breaking Methodologies

| Method | Description |
|--------|-------------|
| **Brute Force** | Tries every possible key combination; success depends on key length, time, system security mechanisms |
| **Frequency Analysis** | Studies frequency of letters/groups in ciphertext (e.g., "e" most common in English) |
| **Trickery and Deceit** | Social engineering to extract keys |
| **One-Time Pad** | Unbreakable with infinite resources; key length = message length; each key used once and discarded |

### Brute-Force Attack - Estimated Time

| Power/Cost | 40 bits | 56 bits (DES) | 64 bits | 128 bits (AES) |
|------------|---------|---------------|---------|----------------|
| $2K (individual) | 1.4 min | 73 days | 50 years | 10²⁰ years |
| $100K (company) | 2 sec | 35 hours | 1 year | 10¹⁹ years |
| $1M (state) | 0.2 sec | 3.5 hours | 37 days | 10¹⁸ years |

### Birthday Attack

- Based on **birthday paradox**: With 23 people, 50% chance two share same birthday.
- For 128-bit hash (MD5): need 2¹²⁸ attempts for collision; birthday attack reduces to ≈1.17 × √2¹²⁸.

### Brute-Forcing VeraCrypt Encryption (hashcat)

```bash
# Extract first 512 bytes of hash
dd.exe if=<container> of=<hashfile.tc> bs=512 count=1

# Brute-force numeric password (4 digits)
hashcat.exe -a 3 -w 1 -m 13721 <hashfile.tc> ?d?d?d?d

# Brute-force with wordlist
hashcat.exe -w 1 -m 13721 hash.tc wordlist.txt
```

### Meet-in-the-Middle Attack (on Digital Signature Schemes)

- Works by encrypting from one end and decrypting from the other, meeting in the middle.
- Reduces brute-force permutations for multiple-key encryption.
- Example (Double DES): 2⁵⁶ operations to find both keys (vs 2¹¹² for brute-force).

### Side-Channel Attack

- Physical attack on cryptographic device; monitors environmental factors:

| Channel | Description |
|---------|-------------|
| **Power Consumption** | SPA (instruction timing), DPA (statistical methods) |
| **Electromagnetic Field** | Variations over chip surface correlate to computation/data |
| **Light Emission** | CRT diffuse reflection, LED optical radiation |
| **Timing and Delay** | Time variations infer secret information |
| **Sound** | Acoustic emissions from keyboards, CPU, memory |

**Mitigation Techniques:**
- DPA-proof protocols, fixed-time algorithms (no data-dependent delays)
- Masking/blinding with random nonces
- Differential matching, amplitude/temporal noise
- Power-line conditioning, signal-attenuating materials
- Hardware isolation, monitoring, constant-time algorithms, HSMs, PUFs
- Cache partitioning/locking, error detection/correction

### Hash Collision Attack

- Finding two different input messages that produce same hash output (hash(a₁) = hash(a₂)).
- Allows forging digital signatures.

### DUHK Attack (Don't Use Hard-Coded Keys)

- Cryptographic vulnerability affecting ANSI X9.31 Random Number Generator (RNG).
- Hard-coded seed key + ANSI X9.31 → attacker can decrypt VPN/web session data.

### DROWN Attack (Decrypting RSA with Obsolete and Weakened eNcryption)

- Cross-protocol weakness affecting SSLv3/TLS.
- Server vulnerable if: permits SSLv2 connection, or same private key used on server that allows SSLv2.
- Attacker decrypts TLS connection by launching malicious SSLv2 probes.

### Rainbow Table Attack

- Precomputed table of word lists (dictionary, brute-force) and their hash values.
- Uses time-memory trade-off; faster than other techniques.
- Attacker compares captured password hash with precomputed table → recovers password.

### Related-Key Attack

- Exploits mathematical relationship between keys in a cipher.
- Example: WEP using RC4 with 24-bit IV; same key repeated (birthday paradox: every 4096 packets, same IV and RC4 key).

### Padding Oracle Attack (Vaudenay Attack)

- Exploits padding validation of encrypted message (CBC mode).
- Server (oracle) reveals whether padding was correct.
- Allows attacker to decrypt and optionally encrypt messages using server's key.

### Attacks on Blockchain

| Attack | Description |
|--------|-------------|
| **51% Attack (Majority Attack)** | Attacker controls >50% of computational/staking power; can double-spend, DoS, reverse transactions, manipulate blockchain |
| **Finney Attack** | Attacker pre-mines block with transaction to self; sends same coins to victim; broadcasts pre-mined block → transaction reversed |
| **Eclipse Attack** | Attacker isolates target node by surrounding with malicious nodes; controls node's view of blockchain |
| **Race Attack** | Double-spending; attacker broadcasts two conflicting transactions quickly; exploits network latency |
| **DeFi Sandwich Attack** | Exploits time delay in DEXs; front-run victim's transaction (buy low), back-run (sell high); profits from price manipulation |

### Quantum Computing Risks

- **Breaking classical cryptography:** Shor's algorithm (RSA, DSA, ECC); Grover's algorithm (reduces symmetric key strength)
- **Transition challenges:** Deploying quantum-resistant algorithms complex
- **Harvest-now, decrypt-later:** Collect encrypted data now, decrypt with future quantum computers
- **Threat to blockchain:** Derive private keys from public keys; break hashes/digital signatures
- **Quantum malware:** Predict/reconstruct keys in real-time

---

## Cryptanalysis Tools

| Tool | Description |
|------|-------------|
| **CrypTool** | E-learning program; supports classical/modern crypto algorithms; cryptanalysis (Vigenère, RSA, AES); CT1 (Windows), CT2 (visual programming), JCryptTool (Linux/macOS), CryptoOnline (browser) |
| **RsaCtfTool, Msiieve, Cryptol, CryptoSMT, MTP** | Additional cryptanalysis tools |

### Online MD5 Decryption Tools

- MD5 Decrypter (dcode.fr), MD5 Decrypt (iotools.cloud), MD5Hashing.net, Online Hash Crack, Cmd5, Hashes.com

---

## Cryptography Attack Countermeasures

### How to Defend Against Cryptographic Attacks

- Grant cryptographic keys directly to application/user.
- Deploy IDS to monitor key exchange/access.
- Use passphrases/passwords to encrypt keys stored on disk.
- Do not store keys in source code or binaries.
- For symmetric: prefer 256-bit key size.
- For asymmetric: at least 2048-bit key size.
- For hash: at least 256-bit hash length.
- Use recommended tools/products, not self-engineered crypto.
- Limit operations per key.
- Use key derivation functions (KDF) for simple encryption key relationships.
- Upgrade to latest security standards.
- Use strong key schedules to mitigate related-key attacks.
- Enforce hardware-backed security (HSMs).
- Do not use single cryptographic key for multiple purposes.
- Use redundant cryptosystems (encrypt data multiple times).
- Implement regular key rotation.
- Use digital signatures; verify before processing.
- Use hardware-based RNGs or diverse entropy sources.
- Adopt quantum-resistant algorithms (lattice-based, hash-based, code-based).
- Use zero-knowledge proof protocols (zk-SNARKs).
- Use AES algorithms (resistant to cryptanalysis).
- Use key stretching and salting.
- Use TLS for encrypted communication and identity verification.
- Use probabilistic encryption methods.
- Use combined confidentiality+integrity schemes (GCM, Encrypt-then-MAC).
- Use collision-resistant hash functions (SHA-256, SHA-3).

### How to Defend Against Blockchain Attacks

- Implement decentralized identifiers (DIDs).
- Use zero-knowledge proofs for transaction/identity verification.
- Store cryptographic keys in HSMs.
- Use multi-signature wallets.
- Implement real-time monitoring/ML for abnormal transaction patterns.
- Combine PoW + PoS.
- Implement DDoS protection (decentralized DDoS mitigation networks).
- Formal verification methods for smart contracts.
- Regular code audits.
- Secure interoperability protocols, atomic swaps.
- Boost mining pool surveillance.
- Do not store blockchain keys in unsecured files.
- Use trusted encryption program for key storage.
- Randomized peer selection, timeouts, secondary trusted communication channels.
- Out-of-band verification methods.
- Reputation systems, trusted bootstrapping nodes.
- Wait for multiple confirmations.
- Increase transaction propagation speed.
- Hide pending transaction details.
- Batch processing and fair sequencing.
- Secure consensus and order-matching algorithms.
- Randomize transaction submission times.

### How to Defend Against Quantum Computing Attacks

- Use quantum-resistant algorithms (lattice-based, hash-based, code-based).
- Use quantum key distribution (QKD).
- Combine classical + quantum-resistant algorithms during transition.
- Use larger symmetric keys.
- Regularly change cryptographic keys.
- Implement side-channel protection.
- Develop VPNs with quantum-resistant encryption.
- Use quantum-resistant digital signatures in blockchain.
- Encrypt stored data with quantum-resistant algorithms.
- Break data into fragments distributed across multiple locations.
- Isolate critical systems; implement multiple security layers.
- Use cloud-based key management with quantum-resistant algorithms.
- Use secure multi-party computation (MPC) in cloud.
- Develop quantum-specific firewalls.
- Use quantum-resistant zero-knowledge proofs.
- Apply quantum-resistant threshold cryptography.
- Use TPMs with quantum-resistant algorithms.
- Implement RBAC/ABAC with quantum-safe protection.
- Integrate quantum-resistance checks into SDLC and CI/CD pipelines.
- Use HSMs with quantum-safe firmware.

---

## Key Stretching

- **Definition:** Process of strengthening a weak key, usually by making it longer.
- **Purpose:** Defend against brute-force attacks.
- **Techniques:**
  - **PBKDF2** (Password-Based Key Derivation Function 2): Part of PKCS #5 v2.01; applies hash/HMAC + salt.
  - **Bcrypt:** Uses Blowfish variant as hashing algorithm + salt.

---

## Module Summary

This module covered:

- Cryptography concepts and objectives (confidentiality, integrity, authentication, non-repudiation)
- Symmetric encryption algorithms (DES, 3DES, AES, RC4, RC5, RC6, Blowfish, Twofish, Serpent, TEA, CAST-128, GOST, Camellia)
- Asymmetric encryption algorithms (DSA, RSA, Diffie-Hellman, ECC, YAK)
- Message digest functions (MD5, MD6, SHA-1, SHA-2, SHA-3, RIPEMD-160, HMAC)
- Hardware-based encryption (TPM, HSM, USB encryption, hard drive encryption)
- Quantum cryptography and post-quantum cryptography
- Cipher modes of operation (ECB, CBC, CFB, Counter, EtM, E&M, MtE, AEAD)
- Cryptography tools (BCTextEncoder)
- Applications: PKI, digital signatures, SSL/TLS, PGP, GPG, Web of Trust, email encryption, disk encryption, blockchain
- Cryptanalysis methods and attacks (linear, differential, integral, quantum, ciphertext-only, chosen-plaintext, related-key, dictionary, MITM, side-channel, hash collision, DUHK, DROWN, rainbow table, padding oracle, blockchain attacks)
- Countermeasures against cryptographic attacks
- Key stretching (PBKDF2, bcrypt)

**End of Module 20**
