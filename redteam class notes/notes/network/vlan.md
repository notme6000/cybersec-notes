# 1. What is a VLAN?

A **VLAN (Virtual Local Area Network)** is a logical grouping of devices within a network, regardless of their physical location.

It allows network administrators to divide a physical network into multiple separate broadcast domains.



# 2. Why Use VLANs?

* Improve network security
* Reduce broadcast traffic
* Improve performance
* Logical segmentation of departments
* Easier network management
* Separate voice, data, and management traffic

Example:

* VLAN 10 → HR Department
* VLAN 20 → Finance
* VLAN 30 → IT

Even if devices are connected to the same switch, VLANs keep them logically separated.



# 3. Broadcast Domains

A **broadcast domain** is a network segment where broadcast traffic is forwarded to all devices.

Without VLANs:

* Entire switch = one broadcast domain

With VLANs:

* Each VLAN = separate broadcast domain

Devices in different VLANs cannot communicate without a Layer 3 device (router or Layer 3 switch).



# 4. VLAN Range and Types

## VLAN ID Range

| VLAN Range | Description       |
| ------- | ----------------- |
| 1          | Default VLAN      |
| 2–1001     | Normal VLANs      |
| 1002–1005  | Reserved (legacy) |
| 1006–4094  | Extended VLANs    |

Total possible VLANs:

```
4096 (0–4095)
```

(VLAN 0 and 4095 are reserved)



# 5. VLAN Types

## 1. Default VLAN

* VLAN 1
* All ports belong to VLAN 1 by default

## 2. Data VLAN

* Carries user-generated traffic

## 3. Management VLAN

* Used for switch management (SSH, Telnet, SNMP)

## 4. Voice VLAN

* Dedicated to VoIP traffic
* Helps prioritize voice packets

## 5. Native VLAN

* Used in trunk ports
* Carries untagged traffic



# 6. Access Ports vs Trunk Ports

## Access Port

* Belongs to only one VLAN
* Connects end devices (PCs, printers)
* Frames are untagged

Example:

```
Switch Port → PC
```

## Trunk Port

* Carries traffic for multiple VLANs
* Used between switches or switch-to-router
* Uses VLAN tagging

Example:

```
Switch ↔ Switch
Switch ↔ Router
```



# 7. VLAN Tagging (802.1Q)

IEEE 802.1Q is the standard for VLAN tagging.

When a frame passes through a trunk port:

* A VLAN tag is added
* Tag contains VLAN ID

Tag size:

```
4 bytes
```

Access ports remove tags before sending frames to end devices.



# 8. Inter-VLAN Communication

Devices in different VLANs cannot communicate directly.

To enable communication:

* Router (Router-on-a-Stick)
* Layer 3 Switch

## Router-on-a-Stick

* Single physical interface
* Multiple subinterfaces
* Each subinterface assigned to a VLAN



# 9. VLAN Configuration Example (Cisco)

Create VLAN:

```
Switch(config)# vlan 10
Switch(config-vlan)# name HR
```

Assign port to VLAN:

```
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

Configure trunk:

```
Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk
```



# 10. VLAN Advantages

* Reduces broadcast traffic
* Improves security (isolation)
* Flexible network design
* Easier troubleshooting
* Supports QoS for voice traffic



# 11. VLAN Disadvantages

* Requires configuration and management
* Misconfiguration can cause communication issues
* VLAN hopping attacks if not secured properly



# 12. VLAN Hopping (Security Issue)

Attackers may try to access other VLANs using:

* Switch spoofing
* Double tagging

Prevention:

* Disable unused ports
* Set native VLAN to unused VLAN
* Disable DTP
* Use port security



# 13. Summary

* VLAN = Logical segmentation of network
* Each VLAN = Separate broadcast domain
* Access port = One VLAN
* Trunk port = Multiple VLANs
* Inter-VLAN communication requires Layer 3 device
* 802.1Q handles tagging




