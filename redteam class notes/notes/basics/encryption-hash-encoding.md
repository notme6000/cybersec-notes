## 1) Encryption

### Definition

Encryption is the process of converting readable data (plaintext) into unreadable data (ciphertext) using an algorithm and a key. It is designed to protect confidentiality. The original data can be restored using the correct decryption key.

### Purpose

* Protect sensitive data (passwords, credit card numbers, messages)
* Secure communication over networks
* Protect stored data (files, databases)

### Types

#### Symmetric Encryption

* Same key is used for encryption and decryption
* Faster and commonly used for large data

Examples:

* AES (Advanced Encryption Standard)
* DES (Data Encryption Standard)

Example:
Plaintext: `HELLO`
Key: `K`
Ciphertext (conceptual): `RIJVS`
Using the same key restores `HELLO`.

#### Asymmetric Encryption

* Uses two keys: public key and private key
* Public key encrypts, private key decrypts

Examples:

* RSA
* ECC (Elliptic Curve Cryptography)

Example:
If Alice encrypts a message using Bob’s public key, only Bob’s private key can decrypt it.

### Real-World Uses

* HTTPS (SSL/TLS)
* Secure email
* VPNs



## 2) Hashing

### Definition

Hashing is the process of converting data into a fixed-length string (hash value or digest). It is a one-way function, meaning it cannot be reversed to retrieve the original data.

### Purpose

* Verify data integrity
* Store passwords securely
* Detect file changes

### Characteristics

* Deterministic (same input gives same output)
* Fixed output length
* Small change in input produces large change in output
* One-way (not reversible)

### Examples

#### MD5 (not secure today)

Input: `hello`
Output: `5d41402abc4b2a76b9719d911017c592`

#### SHA-256

Input: `hello`
Output:
`2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`

### Password Storage Example

Instead of storing:
Password: `mypassword123`

Store:
Hash: `SHA-256(mypassword123)`

When user logs in, the system hashes the entered password and compares it with the stored hash.



## 3) Encoding

### Definition

Encoding is the process of converting data from one format to another so it can be properly stored or transmitted. It is not meant for security.

### Purpose

* Data transmission
* Data representation
* Compatibility between systems

### Common Types

#### Base64 Encoding

Used to represent binary data in text format.

Example:
Text: `Hello`
Base64 Encoded: `SGVsbG8=`

It can easily be decoded back to `Hello`.

#### URL Encoding

Used in web URLs.

Example:
Space character → `%20`

#### ASCII Encoding

Character: `A`
ASCII value: `65`

--

## Key Differences

| Feature       | Encryption      | Hashing                 | Encoding               |
| ------------- | --------------- | ----------------------- | ---------------------- |
| Reversible    | Yes (with key)  | No                      | Yes                    |
| Purpose       | Confidentiality | Integrity, verification | Data format conversion |
| Key Required  | Yes             | No                      | No                     |
| Output Length | Varies          | Fixed                   | Varies                 |
| Security Use  | Yes             | Yes                     | No                     |




