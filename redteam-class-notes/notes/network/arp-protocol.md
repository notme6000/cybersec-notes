

# 1. What is ARP?

**ARP (Address Resolution Protocol)** is used to map an **IPv4 address** to a **MAC address** inside a local network (LAN).

* IP address → Logical address (Layer 3)
* MAC address → Physical address (Layer 2)

ARP operates between:

* Network Layer (Layer 3)
* Data Link Layer (Layer 2)



# 2. Why ARP is Needed

When a device wants to send data on a local network:

1. It knows the destination **IP address**.
2. But Ethernet requires a **MAC address** to deliver the frame.
3. ARP finds the MAC address associated with that IP.

Without ARP, devices cannot communicate on Ethernet networks.



# 3. Basic Example Scenario

Device A:

* IP: 192.168.1.10
* MAC: AA-AA-AA-AA-AA-AA

Device B:

* IP: 192.168.1.20
* MAC: BB-BB-BB-BB-BB-BB

Both are in subnet:

```
192.168.1.0/24
```

Device A wants to send data to 192.168.1.20.



# 4. Step-by-Step ARP Process

## Step 1: Check ARP Cache

Device A checks its ARP table:

```
Do I already know the MAC for 192.168.1.20?
```

If yes → Use stored MAC
If no → Send ARP Request



## Step 2: ARP Request (Broadcast)

Device A sends an ARP Request:

* Destination MAC: FF-FF-FF-FF-FF-FF (broadcast)
* Message:
  "Who has 192.168.1.20? Tell 192.168.1.10"

This is sent to all devices in the local network.

Important:
ARP requests are broadcasts.



## Step 3: ARP Reply (Unicast)

Device B sees the request and recognizes its IP address.

It sends an ARP Reply:

* Destination MAC: AA-AA-AA-AA-AA-AA (Device A)
* Message:
  "192.168.1.20 is at BB-BB-BB-BB-BB-BB"

ARP replies are unicast.



## Step 4: ARP Cache Update

Device A stores this mapping in its ARP table:

```
192.168.1.20 → BB-BB-BB-BB-BB-BB
```

Now it can send Ethernet frames directly to Device B.



# 5. ARP Table (ARP Cache)

Each device maintains an ARP table.

Example:

```
IP Address        MAC Address
192.168.1.1       00-11-22-33-44-55
192.168.1.20      BB-BB-BB-BB-BB-BB
```

Entries:

* Dynamic (learned automatically)
* Static (manually configured)

Entries expire after a certain time.



# 6. ARP Packet Structure (Simplified)

An ARP message contains:

* Hardware type (Ethernet)
* Protocol type (IPv4)
* Sender MAC address
* Sender IP address
* Target MAC address
* Target IP address
* Operation (Request = 1, Reply = 2)



# 7. ARP Only Works in Local Network

Important rule:

ARP does NOT cross routers.

If destination is outside the subnet:

1. Device sends traffic to default gateway.
2. ARP resolves MAC address of the router.
3. Router handles forwarding.

Example:
If 192.168.1.10 sends to 8.8.8.8:

* It ARPs for router's MAC address, not for 8.8.8.8.



# 8. Gratuitous ARP

A device may send ARP for its own IP address.

Purpose:

* Detect IP conflicts
* Update other devices' ARP tables
* Used in failover systems



# 9. ARP Problems

## 1. ARP Spoofing (ARP Poisoning)

An attacker sends fake ARP replies:

```
"I am 192.168.1.1"
```

Victims update ARP table incorrectly.

Result:

* Man-in-the-middle attacks
* Traffic interception

Prevention:

* Dynamic ARP Inspection (DAI)
* Static ARP entries
* Port security
* VLAN segmentation



# 10. ARP vs RARP

* ARP → IP to MAC
* RARP (Reverse ARP) → MAC to IP (obsolete, replaced by DHCP)



# 11. Summary

* ARP resolves IPv4 addresses to MAC addresses.
* ARP Request = Broadcast.
* ARP Reply = Unicast.
* Works only inside local network.
* ARP table stores mappings.
* Routers stop ARP broadcasts.
* Vulnerable to spoofing attacks.



