# 1. What is Network Segmentation?

**Network segmentation** is the practice of dividing a large network into smaller, isolated segments (subnets or zones).

Each segment:

* Has controlled communication with other segments
* Limits broadcast traffic
* Improves security and performance



# 2. Why Network Segmentation is Important

## 1. Security

* Limits attack spread
* Isolates sensitive systems
* Reduces lateral movement

## 2. Performance

* Reduces broadcast traffic
* Improves network efficiency

## 3. Compliance

* Required for standards like PCI-DSS, HIPAA

## 4. Access Control

* Different departments have different access policies



# 3. Types of Network Segmentation

## 1. Physical Segmentation

Uses separate physical devices:

* Separate switches
* Separate routers
* Separate cabling

Advantages:

* Strong isolation

Disadvantages:

* Expensive
* Less flexible



## 2. Logical Segmentation

Uses configuration instead of physical separation.

Examples:

* VLANs
* Subnets
* Firewalls
* Access Control Lists (ACLs)

More flexible and cost-effective.



# 4. Segmentation Methods

## 1. VLAN Segmentation

* Creates logical broadcast domains
* Devices grouped by function
* Requires Layer 3 device for communication between VLANs

Example:

* VLAN 10 → HR
* VLAN 20 → Finance
* VLAN 30 → IT



## 2. Subnetting

Divides IP network into smaller networks.

Example:

* 192.168.1.0/24 divided into:

  * 192.168.1.0/26
  * 192.168.1.64/26
  * etc.

Each subnet is a separate broadcast domain.



## 3. Firewall-Based Segmentation

Firewalls control traffic between segments.

Example:

* Internal network
* DMZ
* External network

Policies define:

* What traffic is allowed
* What traffic is blocked



## 4. ACL (Access Control Lists)

ACLs filter traffic based on:

* IP address
* Protocol
* Port number

Used in:

* Routers
* Layer 3 switches
* Firewalls



## 5. Micro-Segmentation

Advanced form of segmentation.

* Applied at workload or server level
* Often used in virtualized or cloud environments
* Enforced using software-defined networking (SDN)

Limits communication even within the same subnet.



# 5. Network Zones

Common segmented zones:

## 1. LAN (Internal Network)

Trusted internal users.

## 2. DMZ (Demilitarized Zone)

Public-facing servers:

* Web servers
* Mail servers
* DNS servers

Isolated from internal network.

## 3. Guest Network

Internet-only access.

## 4. Management Network

Used for:

* Switch management
* Server management
* SSH access



# 6. Example of Segmentation Design

Company Network:

* VLAN 10 → HR
* VLAN 20 → Finance
* VLAN 30 → IT
* VLAN 40 → Guest
* VLAN 50 → Servers
* DMZ → Public Web Server

Firewall rules:

* Guest → Internet only
* HR → Server access allowed
* DMZ → No direct access to LAN



# 7. Benefits of Network Segmentation

* Reduces attack surface
* Limits malware spread
* Improves traffic control
* Enhances compliance
* Better monitoring and logging



# 8. Risks Without Segmentation

Flat network (no segmentation):

* One large broadcast domain
* If attacker gains access → entire network exposed
* Easy lateral movement
* Higher congestion



# 9. Segmentation vs VLAN vs Subnet

| Feature         | VLAN                 | Subnet                | Segmentation       |
| ------------ | -------------------- | --------------------- | ------------------ |
| Layer           | Layer 2              | Layer 3               | Layer 2–7          |
| Purpose         | Broadcast control    | IP division           | Security & control |
| Requires Router | Yes (for inter-VLAN) | Yes (between subnets) | Usually yes        |

Segmentation is the broader concept.
VLAN and subnetting are tools used to implement it.



# 10. Best Practices

* Use least privilege principle
* Separate sensitive systems
* Protect management network
* Place public servers in DMZ
* Monitor inter-segment traffic
* Disable unused ports
* Use firewall rules between segments



# 11. Summary

* Network segmentation divides a network into smaller secure zones.
* Improves security, performance, and compliance.
* Can be physical or logical.
* Implemented using VLANs, subnets, firewalls, and ACLs.
* Micro-segmentation provides fine-grained control.
* Prevents lateral movement and reduces risk.




