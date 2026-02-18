## TCP vs UDP

Both **TCP** and **UDP** are Transport Layer (Layer 4) protocols, but they work very differently.

---

## TCP (Transmission Control Protocol)

### Characteristics:

* **Connection-oriented** (uses 3-way handshake)
* **Reliable**
* Guarantees:

  * Data delivery
  * Correct order
  * No duplication
* Has:

  * Error checking
  * Flow control
  * Congestion control
* Slower than UDP

### Used for:

* Web browsing (HTTP/HTTPS)
* Email (SMTP)
* File transfer (FTP)
* SSH

### Think of TCP as:

A **registered courier service** — reliable, tracked, confirmed delivery.

---

## UDP (User Datagram Protocol)

### Characteristics:

* **Connectionless**
* **Unreliable** (no guarantee of delivery)
* No sequencing
* No retransmission
* Very fast
* Lightweight header

### Used for:

* Video streaming
* Online gaming
* VoIP (calls)
* DNS queries

### Think of UDP as:

A **regular postcard** — fast, but no guarantee it arrives.

---

## Side-by-Side Comparison

| Feature        | TCP                   | UDP            |
| -------------- | --------------------- | -------------- |
| Connection     | Yes (3-way handshake) | No             |
| Reliability    | Guaranteed            | Not guaranteed |
| Speed          | Slower                | Faster         |
| Ordering       | Yes                   | No             |
| Error recovery | Yes                   | No             |
| Header size    | 20+ bytes             | 8 bytes        |
| Best for       | Accuracy              | Speed          |

---

## When to Use Which?

* Use **TCP** when data accuracy is critical.
* Use **UDP** when speed is more important than reliability.

---

## Simple Summary

* **TCP = Reliable but slower**
* **UDP = Fast but unreliable**

If you want, I can also explain how TCP ensures reliability internally (ACKs, sliding window, retransmission).

