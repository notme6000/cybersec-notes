# 1. Router

### Definition

A **router** is a device that connects multiple networks and forwards data packets between them.

### Functions

* Determines the best path for data transmission
* Connects LAN to WAN (e.g., internet)
* Performs NAT (Network Address Translation)
* Can provide firewall and DHCP services

### Layer

* Works at **Network Layer (Layer 3)**

### Example

* Home Wi-Fi router

---

# 2. Switch

### Definition

A **switch** connects devices within the same network and forwards data using MAC addresses.

### Functions

* Learns and stores MAC addresses
* Sends data only to the intended device
* Reduces network collisions

### Layer

* Works at **Data Link Layer (Layer 2)**
* Some advanced switches operate at Layer 3

### Example

* Office network switch

---

# 3. Hub

### Definition

A **hub** is a basic networking device that connects multiple devices and broadcasts data to all.

### Functions

* Sends incoming data to all connected devices
* No filtering or intelligence

### Layer

* Works at **Physical Layer (Layer 1)**

### Note

* Mostly obsolete, replaced by switches

---

# 4. Modem

### Definition

A **modem** converts digital signals to analog and vice versa for transmission over communication lines.

### Functions

* Modulation and demodulation
* Connects ISP to home/office network

### Layer

* Works at **Physical Layer (Layer 1)**

### Example

* Fiber ONT, DSL modem

---

# 5. Access Point (AP)

### Definition

An **Access Point** allows wireless devices to connect to a wired network.

### Functions

* Extends Wi-Fi coverage
* Connects multiple wireless clients
* Acts as a bridge between wired and wireless networks

### Layer

* Works at **Layer 2 (Data Link)**

### Example

* Office Wi-Fi access point

---

# 6. Bridge

### Definition

A **bridge** connects two LAN segments and filters traffic based on MAC addresses.

### Functions

* Reduces network traffic
* Divides network into segments

### Layer

* Works at **Data Link Layer (Layer 2)**

---

# 7. Repeater

### Definition

A **repeater** regenerates and amplifies signals to extend network distance.

### Functions

* Boosts weak signals
* Extends coverage area

### Layer

* Works at **Physical Layer (Layer 1)**

### Example

* Wi-Fi range extender

---

# 8. Firewall

### Definition

A **firewall** is a security device that monitors and controls network traffic based on rules.

### Functions

* Blocks unauthorized access
* Filters incoming and outgoing traffic
* Protects against attacks

### Layer

* Works at multiple layers (Layer 3, 4, 7)

---

# Summary Table

| Device       | Layer       | Main Function              |
| ------------ | ----------- | -------------------------- |
| Router       | Layer 3     | Connects networks, routing |
| Switch       | Layer 2     | Connects devices in LAN    |
| Hub          | Layer 1     | Broadcasts data            |
| Modem        | Layer 1     | Signal conversion          |
| Access Point | Layer 2     | Wireless connectivity      |
| Bridge       | Layer 2     | Connects LAN segments      |
| Repeater     | Layer 1     | Signal amplification       |
| Firewall     | Multi-layer | Security and filtering     |


