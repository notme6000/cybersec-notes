

## How a Packet Is Created (OSI Model – Encapsulation)

When you send data (for example, opening a website), your message travels **down the OSI layers**.
Each layer **adds its own information**. This process is called **encapsulation**.

---

## Application Layer (Layer 7)

### What happens:

* You interact with an application (browser, email, FTP, etc.)
* The application creates **data**

### Example:

```
GET /index.html HTTP/1.1
```

📌 **Output:** Raw application data


## Presentation Layer (Layer 6)

### What happens:

* Data is **formatted**
* Encryption and compression may occur

### Example:

* HTTPS encrypts data
* Converts data to a common format (ASCII/UTF-8)

📌 **Output:** Formatted/encrypted data


## Session Layer (Layer 5)

### What happens:

* Session is **established and managed**
* Synchronization and session checkpoints

📌 **Output:** Session-aware data


## Transport Layer (Layer 4)

### What happens:

* Data is broken into **segments**
* Adds **port numbers**
* Adds **sequence numbers**
* Error control and flow control

### Example (TCP):

```
Source Port: 49152
Destination Port: 80
Sequence Number: 1001
```

📌 **Output:** **Segment**


## Network Layer (Layer 3)

### What happens:

* Adds **logical (IP) addresses**
* Determines best path to destination

### Example:

```
Source IP: 192.168.1.10
Destination IP: 93.184.216.34
```

📌 **Output:** **Packet**


## Data Link Layer (Layer 2)

### What happens:

* Adds **physical (MAC) addresses**
* Frames the packet
* Error detection (CRC)

### Example:

```
Source MAC: AA:BB:CC:DD:EE:FF
Destination MAC: 11:22:33:44:55:66
```

📌 **Output:** **Frame**


## Physical Layer (Layer 1)

### What happens:

* Frame is converted into **bits**
* Bits are sent as:

  * Electrical signals
  * Light pulses
  * Radio waves

📌 **Output:** **010101010…**


## 🔁 Visual Summary (Encapsulation)

```
Data
↓
Segment  (L4 – ports, sequence)
↓
Packet   (L3 – IP addresses)
↓
Frame    (L2 – MAC addresses)
↓
Bits     (L1 – signals)
```

---

## Key Terms to Remember (Exam Gold ⭐)

| OSI Layer                            | Data Unit |
| ------------------------------------ | --------- |
| Application / Presentation / Session | Data      |
| Transport                            | Segment   |
| Network                              | Packet    |
| Data Link                            | Frame     |
| Physical                             | Bits      |

---

## One-Line Explanation

> A packet is created by **encapsulating data as it moves down the OSI layers**, with each layer adding its own header.

If you want, I can also explain the **reverse process (decapsulation)** or give you a **diagram-style explanation for exams**.

