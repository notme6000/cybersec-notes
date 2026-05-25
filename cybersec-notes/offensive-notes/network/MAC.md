## MAC Address (Media Access Control Address)

A **MAC address** is a unique physical address assigned to a network interface card (NIC) of a device. It is used to identify devices within a **local area network (LAN)**.



### Key Features

* Works at the **Data Link Layer (Layer 2)** of the OSI model
* 48-bit address (6 bytes)
* Written in hexadecimal format
* Usually permanently assigned by the manufacturer



### Format of a MAC Address

Example:

```
00:1A:2B:3C:4D:5E
```

It may also appear as:

```
00-1A-2B-3C-4D-5E
```

* The first 3 bytes (00:1A:2B) → **OUI (Organizationally Unique Identifier)**
  Identifies the manufacturer.
* The last 3 bytes (3C:4D:5E) → Unique number assigned by the manufacturer.



### Types of MAC Addresses

1. **Unicast** – Identifies a single device
2. **Broadcast** – Sent to all devices in a network
   Example: FF:FF:FF:FF:FF:FF
3. **Multicast** – Sent to a group of devices



### Functions of MAC Address

* Identifies devices within a LAN
* Used by switches to forward frames
* Helps in ARP (Address Resolution Protocol)
* Supports network security (MAC filtering)





### Important Points

* A device can have multiple MAC addresses if it has multiple network interfaces (Wi-Fi, Ethernet).
* MAC addresses are mainly used for communication inside a local network.
* IP addresses are used for communication across different networks (Internet).


