# TRANSPORT LAYER PROTOCOLS


## 1. TCP (Transmission Control Protocol)

**Purpose:** Reliable communication

### How TCP Works:

### Three-Way Handshake:

1. SYN
2. SYN-ACK
3. ACK

Connection established.

### Data Transfer:

* Data divided into segments.
* Each segment numbered.
* Receiver sends acknowledgement.

### Connection Termination:

* FIN handshake.

### Features:

* Reliable
* Ordered delivery
* Error checking
* Flow control
* Congestion control


## 2. UDP (User Datagram Protocol)

**Purpose:** Fast communication

### How UDP Works:

1. Data sent as packets.
2. No handshake.
3. No acknowledgement.
4. No guarantee of delivery.

### Features:

* Faster than TCP
* Used in streaming, gaming, VoIP




# APPLICATION LAYER PROTOCOLS



## 1. HTTP (HyperText Transfer Protocol)

**Purpose:** Transfers web pages between client and server
**Port:** 80
**Type:** Stateless protocol

### How HTTP Works:

1. User enters URL in browser.
2. Browser sends **HTTP Request** (GET/POST) to web server.
3. Server processes request.
4. Server sends **HTTP Response** (status code + data).
5. Browser displays webpage.

### HTTP Message Structure:

* Request Line (GET /index.html)
* Headers
* Body (optional)

### Features:

* Stateless (no memory of previous requests)
* Uses TCP for reliable delivery


## 2. HTTPS (HTTP Secure)

**Purpose:** Secure web communication
**Port:** 443

### How HTTPS Works:

1. Client contacts server.
2. Server sends **SSL/TLS certificate**.
3. Client verifies certificate.
4. Encryption keys are exchanged.
5. Secure encrypted communication begins.

### Features:

* Uses SSL/TLS encryption
* Prevents hacking & data theft
* Used in banking, shopping



## 3. FTP (File Transfer Protocol)

**Purpose:** Transfers files
**Port:** 21 (control), 20 (data)

### How FTP Works:

1. Client connects to FTP server.
2. Authentication (username/password).
3. Two connections created:
   * Control connection (commands)
   * Data connection (file transfer)
4. File uploaded/downloaded.

### Features:

* Uses TCP
* Not secure (data sent in plain text)



## 4. SMTP (Simple Mail Transfer Protocol)

**Purpose:** Sends emails
**Port:** 25

### How SMTP Works:

1. Sender composes email.
2. Email client sends mail to SMTP server.
3. SMTP server forwards to receiver's mail server.
4. Receiver downloads using POP3/IMAP.

### Features:

* Only sends emails
* Uses TCP



## 5. POP3 (Post Office Protocol v3)

**Purpose:** Downloads emails
**Port:** 110

### How POP3 Works:

1. Client connects to mail server.
2. Downloads emails.
3. Usually deletes from server.

### Feature:

* Stores mail locally
* Not good for multiple devices



## 6. IMAP (Internet Message Access Protocol)

**Purpose:** Access emails from server
**Port:** 143

### How IMAP Works:

1. Client connects to server.
2. Emails remain stored on server.
3. Synchronizes across devices.

### Feature:

* Better for multiple devices
* Keeps emails on server



## 7. DNS (Domain Name System)

**Purpose:** Converts domain name → IP address
**Port:** 53 (UDP mostly)

### How DNS Works:

1. User types domain name.
2. DNS resolver checks cache.
3. If not found → queries root server.
4. Root → TLD server → Authoritative server.
5. Returns IP address.

### Feature:

* Uses UDP for speed
* TCP used for large queries



## 8. DHCP (Dynamic Host Configuration Protocol)

**Purpose:** Automatically assigns IP address
**Port:** 67, 68

### How DHCP Works (DORA Process):

1. **Discover** – Client broadcasts request.
2. **Offer** – Server offers IP address.
3. **Request** – Client requests offered IP.
4. **Acknowledge** – Server confirms assignment.



## 🔹 11. IP (Internet Protocol)

**Purpose:** Logical addressing and routing

### 🔎 How IP Works:

* Each device has IP address.
* Data packet contains:

  * Source IP
  * Destination IP
* Routers forward packet to destination.

### ⚡ Versions:

* IPv4 (32-bit)
* IPv6 (128-bit)



## 🔹 12. ICMP (Internet Control Message Protocol)

**Purpose:** Error reporting

### 🔎 How ICMP Works:

* Used by ping.
* Sends Echo Request.
* Receives Echo Reply.



## 🔹 13. ARP (Address Resolution Protocol)

**Purpose:** IP → MAC conversion

### 🔎 How ARP Works:

1. Device broadcasts: “Who has this IP?”
2. Target replies with MAC address.
3. MAC stored in ARP table.



# 📊 Important Comparison

| Feature    | TCP        | UDP               |
| ---- | ---------- | ----------------- |
| Reliable   | Yes        | No                |
| Speed      | Slower     | Faster            |
| Connection | Yes        | No                |
| Used in    | Web, Email | Streaming, Gaming |



# 🎯 Interview Tip Summary

* HTTP → Stateless
* HTTPS → Encrypted HTTP
* FTP → Two connections
* SMTP → Send email
* POP3 → Download email
* IMAP → Sync email
* DNS → Name resolution
* DHCP → DORA process
* TCP → 3-way handshake
* UDP → No handshake
* ARP → IP to MAC






# 1. What is MIME?

**MIME (Multipurpose Internet Mail Extensions)** is a standard that extends the format of email to support:

* Text in different character sets
* Non-text attachments (images, audio, video, PDF, etc.)
* Multiple parts in a single message

Originally, email supported only **7-bit ASCII text**. MIME was created to allow richer content.



# 2. Why MIME is Needed

Basic email (SMTP) originally supported only:

* Plain text
* 7-bit ASCII characters
* No attachments

MIME enables:

* File attachments
* HTML email
* Multimedia content
* International character sets (UTF-8, etc.)



# 3. Where MIME is Used

MIME is used in:

* Email systems (SMTP, POP3, IMAP)
* HTTP (web content types)

For example, web browsers use MIME types to determine how to handle files.



# 4. How MIME Works

MIME adds **extra headers** to email messages.

Key MIME headers:

* `MIME-Version`
* `Content-Type`
* `Content-Transfer-Encoding`
* `Content-Disposition`



# 5. Important MIME Headers

## 1. MIME-Version

Indicates MIME is used:

```
MIME-Version: 1.0
```



## 2. Content-Type

Specifies the type of data being sent.

Format:

```
Content-Type: type/subtype
```

Examples:

* `text/plain`
* `text/html`
* `image/jpeg`
* `application/pdf`
* `multipart/mixed`



## 3. Content-Transfer-Encoding

Since SMTP supports only 7-bit ASCII, binary data must be encoded.

Common encodings:

* `base64`
* `quoted-printable`
* `7bit`
* `8bit`

Example:

```
Content-Transfer-Encoding: base64
```



## 4. Content-Disposition

Specifies whether content is displayed inline or as attachment.

Examples:

```
Content-Disposition: inline
Content-Disposition: attachment; filename="file.pdf"
```



# 6. MIME Types (Media Types)

MIME types are categorized into major types:

| Type        | Description    | Example         |
| ----- | -------------- | --------------- |
| text        | Text files     | text/plain      |
| image       | Images         | image/png       |
| audio       | Audio files    | audio/mpeg      |
| video       | Video files    | video/mp4       |
| application | Binary data    | application/pdf |
| multipart   | Multiple parts | multipart/mixed |



# 7. Multipart Messages

MIME allows multiple parts in one message.

Example:

```
Content-Type: multipart/mixed; boundary="abc123"
```

Each section is separated by a boundary string.

Example structure:

* Part 1 → Text message
* Part 2 → Attachment
* Part 3 → Image



# 8. Example of a MIME Email

```
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="boundary123"

--boundary123
Content-Type: text/plain

Hello, this is the message.

--boundary123
Content-Type: application/pdf
Content-Transfer-Encoding: base64
Content-Disposition: attachment; filename="file.pdf"

JVBERi0xLjQKJcfs...
--boundary123--
```



# 9. MIME in HTTP

Web servers use MIME types to tell browsers how to handle files.

Example HTTP header:

```
Content-Type: text/html
```

If server sends:

```
Content-Type: image/jpeg
```

Browser knows to display an image.



# 10. Common MIME Types

| File Type  | MIME Type              |
| ---- | ---------------------- |
| HTML       | text/html              |
| CSS        | text/css               |
| JavaScript | application/javascript |
| JSON       | application/json       |
| PNG        | image/png              |
| JPEG       | image/jpeg             |
| PDF        | application/pdf        |
| ZIP        | application/zip        |



# 11. MIME vs SMTP

* SMTP = Transfers email
* MIME = Defines format of email content

MIME works on top of SMTP.



# 12. Limitations

* Increases email size (due to base64 encoding)
* Not encryption
* Not compression
* Only formatting and content extension

For security:

* TLS (encryption)
* S/MIME or PGP (email encryption)



# 13. Summary

* MIME extends email to support multimedia and attachments.
* Adds headers like Content-Type and Content-Transfer-Encoding.
* Enables HTML emails and file attachments.
* Used in both email systems and HTTP.
* Does not provide security by itself.




# 1. What is S/MIME?

**S/MIME (Secure/Multipurpose Internet Mail Extensions)** is a security extension of MIME that provides:

* Encryption (confidentiality)
* Digital signatures (authentication and integrity)

It is used to secure email communication.

S/MIME works on top of:

* SMTP (email transport)
* MIME (email format)



# 2. Why S/MIME is Needed

Normal email:

* Is not encrypted
* Can be intercepted
* Can be modified
* Sender identity can be forged

S/MIME solves this by adding:

* Public key encryption
* Digital certificates
* Cryptographic signatures



# 3. Security Services Provided by S/MIME

## 1. Confidentiality

Encrypts email so only the intended recipient can read it.

## 2. Authentication

Verifies the sender’s identity.

## 3. Integrity

Ensures the message has not been altered.

## 4. Non-repudiation

Sender cannot deny sending the message.



# 4. How S/MIME Works

S/MIME uses **public key cryptography**.

Each user has:

* A public key
* A private key
* A digital certificate issued by a Certificate Authority (CA)



# 5. Digital Certificates

A digital certificate contains:

* User’s public key
* User identity information
* CA’s digital signature
* Expiration date

Certificates follow the **X.509 standard**.

Certificate Authorities (CAs):

* Issue and verify certificates
* Ensure trust



# 6. S/MIME Email Process

## A. Sending an Encrypted Email

1. Sender gets recipient's public key.
2. Message is encrypted using recipient’s public key.
3. Recipient decrypts using their private key.

Only recipient can read the message.



## B. Sending a Digitally Signed Email

1. Sender creates message hash.
2. Hash is encrypted with sender’s private key.
3. This becomes the digital signature.
4. Recipient verifies using sender’s public key.

If verification succeeds:

* Sender is authentic
* Message was not modified



# 7. Combined: Signed and Encrypted Email

Most secure option:

1. Message is digitally signed.
2. Then entire message is encrypted.

This provides:

* Confidentiality
* Authentication
* Integrity



# 8. Cryptographic Algorithms Used

S/MIME typically uses:

For hashing:

* SHA-256

For digital signatures:

* RSA
* ECDSA

For encryption:

* AES (symmetric encryption)

Hybrid encryption is used:

* Message encrypted with symmetric key (AES)
* Symmetric key encrypted with recipient’s public key



# 9. S/MIME Message Types

S/MIME supports:

1. Enveloped data (encrypted message)
2. Signed data (digitally signed message)
3. Clear-signed data
4. Signed and enveloped data



# 10. S/MIME vs MIME

| Feature           | MIME | S/MIME          |
| ----------- | ---- | --------------- |
| Attachments       | Yes  | Yes             |
| Encryption        | No   | Yes             |
| Digital Signature | No   | Yes             |
| Security          | None | Strong security |

MIME handles formatting.
S/MIME adds security.



# 11. S/MIME vs PGP

| Feature        | S/MIME                        | PGP                    |
| -------- | ----------------------------- | ---------------------- |
| Trust Model    | Certificate Authority (CA)    | Web of Trust           |
| Standard       | X.509                         | OpenPGP                |
| Enterprise Use | Common                        | Less common            |
| Integration    | Built into many email clients | Often requires plugins |



# 12. Advantages of S/MIME

* Strong email security
* Widely supported (Outlook, Apple Mail, etc.)
* Uses trusted CA model
* Provides encryption and signatures



# 13. Limitations

* Requires digital certificates
* Certificate management can be complex
* Depends on trusted Certificate Authorities
* Does not protect subject line (in most cases)



# 14. Summary

* S/MIME = Secure version of MIME.
* Provides encryption and digital signatures.
* Uses public key cryptography.
* Requires X.509 digital certificates.
* Ensures confidentiality, integrity, authentication, and non-repudiation.
* Commonly used in enterprise email environments.


---

# Part 1: SFTP (SSH File Transfer Protocol)

# 1. What is SFTP?

**SFTP (SSH File Transfer Protocol)** is a secure file transfer protocol that runs over **SSH (Secure Shell)**.

It is used to:

* Upload files
* Download files
* Manage files remotely
* Securely transfer data

Default port:

```
TCP 22
```

SFTP is not the same as FTP or FTPS.



# 2. Why SFTP is Needed

Traditional FTP:

* Sends data in plain text
* Sends passwords unencrypted
* Not secure

SFTP provides:

* Encrypted communication
* Secure authentication
* Data integrity



# 3. How SFTP Works

SFTP uses SSH to create a secure tunnel.

Process:

1. Client connects to server on port 22.
2. SSH handshake occurs.
3. Authentication (password or SSH key).
4. Secure encrypted channel established.
5. File transfer commands are executed.

All data is encrypted.



# 4. SFTP vs FTP vs FTPS

| Feature       | FTP | FTPS      | SFTP      |
| ---------- | --- | --------- | --------- |
| Encryption    | No  | Yes (TLS) | Yes (SSH) |
| Port          | 21  | 21        | 22        |
| Secure Login  | No  | Yes       | Yes       |
| Protocol Base | FTP | FTP + TLS | SSH       |

Important:

* SFTP is completely different from FTP.
* It does not use FTP protocol at all.



# 5. SFTP Features

* Secure file upload/download
* Directory browsing
* File deletion
* File renaming
* File permissions management
* Resume interrupted transfers



# 6. SFTP Authentication Methods

* Password authentication
* Public key authentication (recommended)
* Multi-factor authentication

Public key authentication is more secure.



# 7. Advantages of SFTP

* Strong encryption
* Single port (22)
* Firewall-friendly
* Secure authentication
* Reliable file transfer



# 8. Limitations of SFTP

* Slightly slower due to encryption
* Requires SSH server
* Not anonymous (like FTP can be)



# 9. SFTP Security Best Practices

* Use SSH key-based authentication
* Disable password authentication if possible
* Restrict user permissions
* Use chroot jail for isolation
* Monitor logs



# Part 2: DNSSEC (Domain Name System Security Extensions)

# 1. What is DNSSEC?

**DNSSEC (Domain Name System Security Extensions)** is a security extension for DNS.

It protects DNS from:

* Spoofing
* Cache poisoning
* Man-in-the-middle attacks

DNSSEC provides:

* Data integrity
* Authentication of DNS responses

It does NOT provide encryption.



# 2. Why DNSSEC is Needed

Normal DNS:

* Uses UDP
* No verification
* Vulnerable to forged responses

Attack example:

* Attacker sends fake DNS response
* User redirected to malicious website

DNSSEC prevents this.



# 3. How DNSSEC Works

DNSSEC uses:

* Digital signatures
* Public key cryptography
* Hashing

Each DNS record is digitally signed.



# 4. DNSSEC Key Types

## 1. ZSK (Zone Signing Key)

* Signs DNS records

## 2. KSK (Key Signing Key)

* Signs the ZSK
* Creates trust chain



# 5. DNSSEC Record Types

DNSSEC introduces new DNS records:

* RRSIG → Digital signature of DNS record
* DNSKEY → Public key
* DS → Delegation Signer (links parent and child zones)
* NSEC / NSEC3 → Authenticated denial of existence



# 6. Chain of Trust

DNSSEC builds trust from:

Root Zone
↓
Top-Level Domain (.com)
↓
Domain (example.com)

Each level verifies the next using digital signatures.

If any level fails verification → DNS response rejected.



# 7. DNSSEC Validation Process

1. User requests DNS record.
2. Resolver receives:

   * DNS record
   * RRSIG (signature)
   * DNSKEY
3. Resolver verifies signature.
4. If valid → Accept.
5. If invalid → Reject.



# 8. What DNSSEC Protects Against

* DNS spoofing
* Cache poisoning
* Man-in-the-middle attacks
* Fake DNS responses



# 9. What DNSSEC Does NOT Do

* Does not encrypt DNS traffic
* Does not hide domain names
* Does not provide confidentiality

For encryption, use:

* DNS over HTTPS (DoH)
* DNS over TLS (DoT)



# 10. DNSSEC vs DNS over HTTPS (DoH)

| Feature        | DNSSEC | DoH |
| ----------- | ------ | --- |
| Encryption     | No     | Yes |
| Integrity      | Yes    | Yes |
| Authentication | Yes    | Yes |
| Privacy        | No     | Yes |

DNSSEC ensures authenticity.
DoH ensures privacy.



# 11. Advantages of DNSSEC

* Prevents DNS spoofing
* Improves trust in DNS
* Protects users from fake websites
* Strengthens internet infrastructure



# 12. Limitations of DNSSEC

* Complex to configure
* Requires key management
* Larger DNS responses
* Not universally deployed



# Final Summary

SFTP:

* Secure file transfer protocol
* Runs over SSH (port 22)
* Encrypts all file transfers

DNSSEC:

* Secures DNS responses
* Uses digital signatures
* Prevents spoofing and cache poisoning
* Does not encrypt traffic




