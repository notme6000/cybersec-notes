## TCP 3-Way Handshake (Connection Establishment)

The **3-way handshake** is how TCP creates a **reliable connection** between a client and a server before sending data.

It ensures:

* Both sides are ready
* Sequence numbers are synchronized
* The connection is reliable

![3 way](../../../images/3-way.jpeg)
---

## Step-by-Step Process

### SYN (Client → Server)

* Client wants to connect.
* Sends a **SYN** (synchronize) packet.
* Includes its **initial sequence number (ISN)**.

Example:

```
SYN
Seq = 1000
```

Meaning: “I want to start communication, my sequence number starts at 1000.”


### SYN-ACK (Server → Client)

* Server receives SYN.
* Replies with:

  * **SYN** (its own sequence number)
  * **ACK** (acknowledges client’s sequence number + 1)

Example:

```
SYN
ACK = 1001
Seq = 5000
```

Meaning:

* “I received your SYN.”
* “My sequence number starts at 5000.”


### ACK (Client → Server)

* Client acknowledges the server’s sequence number.

Example:

```
ACK = 5001
```

Meaning: “Connection confirmed.”

---

## Visual Representation

```
Client                         Server
  | ---- SYN (Seq=1000) ---->  |
  | <--- SYN-ACK (Seq=5000, Ack=1001) --- |
  | ---- ACK (Ack=5001) ---->  |
```

✅ Connection established
Now data transfer begins.

---

## Why 3 Steps?

It ensures:

* Both sides agree on sequence numbers
* Both sides confirm readiness
* Prevents old duplicate connections

---

## Important Exam Points

* Uses **SYN and ACK flags**
* Synchronizes **sequence numbers**
* Happens **before data transfer**
* Works at **Transport Layer (Layer 4)**

---

## Simple Analogy

Client: “Can we talk?” (SYN)
Server: “Yes, I hear you. Ready?” (SYN-ACK)
Client: “Yes, let’s start.” (ACK)

---

## One-Line Definition

> The TCP 3-way handshake is a three-step process (SYN, SYN-ACK, ACK) used to establish a reliable connection between client and server.

If you want, I can also explain **4-way termination (connection closing)** next.

