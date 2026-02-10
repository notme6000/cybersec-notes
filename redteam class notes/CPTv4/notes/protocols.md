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

---


# APPLICATION LAYER PROTOCOLS

---

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

---

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

---

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

---

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

---

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

---

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

---

## 8. DHCP (Dynamic Host Configuration Protocol)

**Purpose:** Automatically assigns IP address
**Port:** 67, 68

### How DHCP Works (DORA Process):

1. **Discover** – Client broadcasts request.
2. **Offer** – Server offers IP address.
3. **Request** – Client requests offered IP.
4. **Acknowledge** – Server confirms assignment.

---

# TRANSPORT LAYER PROTOCOLS

---

## 9. TCP (Transmission Control Protocol)

**Purpose:** Reliable communication

### 🔎 How TCP Works:

### 1️⃣ Three-Way Handshake:

1. SYN
2. SYN-ACK
3. ACK

Connection established.

### 2️⃣ Data Transfer:

* Data divided into segments.
* Each segment numbered.
* Receiver sends acknowledgement.

### 3️⃣ Connection Termination:

* FIN handshake.

### ⚡ Features:

* Reliable
* Ordered delivery
* Error checking
* Flow control
* Congestion control

---

## 🔹 10. UDP (User Datagram Protocol)

**Purpose:** Fast communication

### 🔎 How UDP Works:

1. Data sent as packets.
2. No handshake.
3. No acknowledgement.
4. No guarantee of delivery.

### ⚡ Features:

* Faster than TCP
* Used in streaming, gaming, VoIP

---

# 🌐 NETWORK LAYER PROTOCOLS

---

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

---

## 🔹 12. ICMP (Internet Control Message Protocol)

**Purpose:** Error reporting

### 🔎 How ICMP Works:

* Used by ping.
* Sends Echo Request.
* Receives Echo Reply.

---

## 🔹 13. ARP (Address Resolution Protocol)

**Purpose:** IP → MAC conversion

### 🔎 How ARP Works:

1. Device broadcasts: “Who has this IP?”
2. Target replies with MAC address.
3. MAC stored in ARP table.

---

# 📊 Important Comparison

| Feature    | TCP        | UDP               |
| ---------- | ---------- | ----------------- |
| Reliable   | Yes        | No                |
| Speed      | Slower     | Faster            |
| Connection | Yes        | No                |
| Used in    | Web, Email | Streaming, Gaming |

---

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

---

If you want, I can next give:

* 📌 Complete protocol flow diagrams
* 📘 Real-life example of data traveling through all layers
* 🔥 Viva questions & answers
* 📊 Protocols mapped to OSI layers

Just tell me what you need 😊

