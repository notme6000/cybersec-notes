# OSI Model (Open Systems Interconnection)

The OSI model has **7 layers**.
It explains how data moves from one computer to another over a network.

---

## **7. Application Layer**

**Purpose:** Provides network services to end users.

**What happens here:**

* User interacts with network applications
* File transfer, email, web browsing
* Network services like HTTP, FTP, SMTP

**Examples:**

* Web browser
* Email client

**Protocols:**

* HTTP
* HTTPS
* FTP
* SMTP
* DNS

**Devices:**

* No specific device
* Gateway (sometimes considered here)

---

## **6. Presentation Layer**

**Purpose:** Data formatting and translation.

**What happens here:**

* Data encryption/decryption
* Compression
* Format conversion (e.g., JPEG, MP4)

**Example:**

* SSL/TLS encryption

**Devices:**

* No specific physical device

---

## **5. Session Layer**

**Purpose:** Manages sessions (connections).

**What happens here:**

* Starts session
* Maintains session
* Ends session
* Authentication

**Example:**

* Login session
* Video call session

**Devices:**

* No specific device

---

## **4. Transport Layer**

**Purpose:** End-to-end communication and reliability.

**What happens here:**

* Breaks data into segments
* Error checking
* Flow control
* Port numbers used
* Reliable (TCP) or fast (UDP) delivery

**Protocols:**

* TCP
* UDP

**Devices:**

* Firewall
* Load Balancer

---

## **3. Network Layer**

**Purpose:** Routing and logical addressing.

**What happens here:**

* IP addressing
* Packet forwarding
* Path determination

**Protocols:**

* IP
* ICMP
* Routing protocols (RIP, OSPF)

**Devices:**

* Router
* Layer 3 Switch

---

## **2. Data Link Layer**

**Purpose:** Physical addressing and error detection.

**What happens here:**

* MAC addressing
* Frame formation
* Error detection
* Controls access to media

**Protocols:**

* Ethernet
* ARP

**Devices:**

* Switch
* Bridge
* NIC (Network Interface Card)

---

## **1. Physical Layer**

**Purpose:** Transmits raw bits over physical medium.

**What happens here:**

* Converts data into electrical/optical signals
* Defines cables, voltages, connectors

**Examples:**

* Ethernet cable
* Fiber cable

**Devices:**

* Hub
* Repeater
* Cables
* Connectors

---


