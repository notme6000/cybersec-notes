## 📡 How DHCP Works — A Deep Technical Dive

**DHCP (Dynamic Host Configuration Protocol)** automatically assigns IP configuration to devices on a network so they can communicate without manual setup.

It operates at the **Application Layer (Layer 7)** but relies heavily on **UDP (Layer 4)** and interacts closely with **IP (Layer 3)**.



# 1️⃣ Why DHCP Exists

Before DHCP, administrators manually configured:

* IP address
* Subnet mask
* Default gateway
* DNS servers

This does not scale in large or dynamic networks.

DHCP solves:

* Address automation
* IP conflict prevention
* Centralized configuration management
* Lease-based temporary addressing



# 2️⃣ DHCP Architecture

### Core Components

* **DHCP Client** → Device requesting configuration
* **DHCP Server** → Assigns and manages IP addresses
* **DHCP Relay Agent** → Forwards DHCP messages across subnets



# 3️⃣ Where DHCP Lives in the Stack

| Layer       | Protocol                          |
| -------- | --------------------------------- |
| Application | DHCP                              |
| Transport   | UDP (ports 67 server / 68 client) |
| Network     | IP                                |
| Data Link   | Ethernet / Wi-Fi                  |

Because the client initially has **no IP address**, DHCP uses:

* **Broadcast traffic**
* Source IP: `0.0.0.0`
* Destination IP: `255.255.255.255`



# 4️⃣ The DHCP DORA Process (Core Handshake)

## Step 1 — DHCP Discover


![Image](https://media.licdn.com/dms/image/v2/D4D12AQEK5ZzE2SbT4Q/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1688885346955?e=2147483647\&t=_XG2JlhvEp5XOrKpeIIgL6wNEtbhkEpaxMYlICauXcA\&v=beta)

* Client broadcasts a **DHCPDISCOVER**
* Sent to UDP port 67
* Source IP: `0.0.0.0`
* Destination IP: `255.255.255.255`

The message includes:

* Client MAC address
* Transaction ID (XID)
* Parameter request list (DNS, router, etc.)



## Step 2 — DHCP Offer

* Server replies with **DHCPOFFER**
* Contains:

  * Proposed IP address
  * Subnet mask
  * Default gateway
  * Lease time
  * DNS servers
  * Server identifier

This may still be broadcast because client does not yet have a valid IP.



## Step 3 — DHCP Request

* Client selects one offer (if multiple servers respond)
* Broadcasts **DHCPREQUEST**
* Includes selected server identifier
* Other servers withdraw their offers



## Step 4 — DHCP Acknowledgment (ACK)

* Server sends **DHCPACK**
* Lease officially begins
* Client configures interface

If invalid, server may send **DHCPNAK**



# 5️⃣ DHCP Packet Structure (Inside the Message)

DHCP is built on **BOOTP format**.

Key fields:

| Field   | Purpose                      |
| ---- | ---------------------------- |
| op      | Request or reply             |
| htype   | Hardware type (Ethernet = 1) |
| hlen    | Hardware address length      |
| xid     | Transaction ID               |
| secs    | Seconds since request        |
| flags   | Broadcast flag               |
| ciaddr  | Client IP (if known)         |
| yiaddr  | Your (assigned) IP           |
| siaddr  | Server IP                    |
| giaddr  | Relay agent IP               |
| chaddr  | Client MAC                   |
| options | Configuration parameters     |

### The "Magic Cookie"

`0x63825363` marks start of DHCP options.



# 6️⃣ DHCP Lease Lifecycle

## Lease States

1. INIT
2. SELECTING
3. REQUESTING
4. BOUND
5. RENEWING (T1)
6. REBINDING (T2)

### Timers

* **T1 (50%)** → Client renews with original server (unicast)
* **T2 (87.5%)** → Broadcast to any DHCP server
* **Lease Expiry** → Address released



# 7️⃣ DHCP Relay (Cross-Subnet DHCP)

Normally broadcasts do not cross routers.

To solve this:

A router configured with:

```
ip helper-address <dhcp-server-ip>
```

The relay:

* Receives broadcast
* Converts to unicast
* Inserts **giaddr** field
* Forwards to DHCP server
* Server replies to relay
* Relay forwards to client

Used heavily in enterprise VLAN designs.



# 8️⃣ Advanced DHCP Concepts

### 1. DHCP Reservations

Bind MAC → fixed IP.

### 2. DHCP Options (Powerful Feature)

Examples:

* Option 3 → Default gateway
* Option 6 → DNS
* Option 66/67 → TFTP server (used in PXE boot)
* Option 82 → Relay agent info



### 3. DHCP Failover

Two servers share:

* Lease database
* State synchronization

Modes:

* Hot standby
* Load balancing



### 4. DHCP Snooping (Security)

Switch feature that:

* Blocks rogue DHCP servers
* Builds trusted MAC/IP binding table

Prevents:

* DHCP starvation attacks
* Rogue gateway injection



# 9️⃣ Security Weaknesses

DHCP is inherently insecure because:

* No authentication
* Broadcast-based
* Trusts first server response

Common attacks:

* Rogue DHCP server
* Starvation attack (exhaust pool)
* Man-in-the-middle via fake gateway

Mitigations:

* DHCP Snooping
* Port security
* 802.1X



# 🔟 DHCP vs BOOTP

DHCP extends:

* BOOTP

Adds:

* Lease times
* Options field
* Dynamic allocation




