## TCP/IP Model

The TCP/IP model is a practical networking model used on the Internet.
It explains how data moves from one computer to another in 4 layers.

---

## Layers of the TCP/IP Model

### 1) Application Layer

(Combines OSI Layers 7, 6, 5)

What it does:

* Provides network services to applications
* Handles data formatting and session management

Protocols:

* HTTP / HTTPS
* FTP
* SMTP
* DNS
* SSH

---

### 2) Transport Layer

(Same as OSI Layer 4)

What it does:

* End-to-end communication
* Uses port numbers
* Provides reliability and flow control

Protocols:

* TCP – reliable, connection-oriented
* UDP – fast, connectionless

---

### 3) Internet Layer

(Same as OSI Layer 3)

What it does:

* Logical addressing
* Routing packets between networks

Protocols:

* IP (IPv4 / IPv6)
* ICMP
* ARP
* IPsec

---

### 4) Network Access Layer

(Combines OSI Layers 2 and 1)

What it does:

* Physical transmission of data
* Framing and MAC addressing

Technologies:

* Ethernet
* Wi-Fi
* ARP
* MAC addressing

---

## TCP/IP vs OSI Model

| OSI Model (7 layers) | TCP/IP Model (4 layers) |
| -------------------- | ----------------------- |
| Application          | Application             |
| Presentation         | Application             |
| Session              | Application             |
| Transport            | Transport               |
| Network              | Internet                |
| Data Link            | Network Access          |
| Physical             | Network Access          |

---

## Data Flow (Encapsulation)

Application Data
↓
Segment (TCP / UDP)
↓
Packet (IP)
↓
Frame (Ethernet)
↓
Bits

---

## Key Points

* TCP/IP is the practical model used on the Internet.
* OSI is mainly a conceptual reference model.
* TCP/IP has 4 layers.
* The Internet operates using the TCP/IP protocol suite.

---

One-line definition:

The TCP/IP model is a four-layer networking model that defines how data is transmitted over the Internet.

