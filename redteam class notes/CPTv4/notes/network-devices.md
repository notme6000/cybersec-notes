# Network devices

## 1. Repeater

- OSI Layer 1 - physical layer

- A repeater is a device that regenerates and amplifies weak signals

- _working_
    - receives weak or distorted signals
    - cleans and regenerates it
    - sends it forward
    - does not understand data or address

## 2. Hub

- OSI Layer 1 - physical layer 

- A hub is a multiport repeater that connects multiple devices in a LAN

- _working_
    - receives data from one port
    - broadcasts it to all other ports
    - no filtering
    - no MAC address learining

## 3. Bridge

- OSI Layer 2 - Data link layer

- A bridge connects two LAN segments and filters traffic

- _working_
    - learns MAC addresses
    - forwards frames only if needed
    - reduces collisions

- smarter than a Hub

## 4. Switch

- OSI Layer 2 (some operate at layer 3)

- A switch connects devices within a LAN and forwards data intelligently

- _working_
    - maintains MAC address table
    - sends frame only to destination port
    - each port = separate collision domain
    - Layer 3 switches can route IP traffic

## 5. Router

- OSI Layer 3 - Network Layer 

- A router connects different networks together

- _working_
    - uses IP addresses
    - maintains routing table
    - chooses best path
    - separates broadcast domains

## 6. Gateway

- OSI Layer - can operate at multiple layers (often layer 7)

- Gateway connects networks using different protocols

- _working_ 
    - translates one protocol to another
    - converts formats 
    - used in email, VoIP, etc.
- Example: Email gateway, IoT gateway

## 7. Modem

- OSI Layer 1 - physical layer 

- Modem - modulator/Demodulator. Connects digital devices to analog lines

- _working_
    - converts digital signals to analog  (for transmission)
    - converts analog back to digital 
    - used in DSL, cable internet

## 8. Access Point (AP)

- OSI Layer 2 - Data link layer

- Provides wireless connectivity to wired network

- _working_ 
    - connects wifi devices to LAN
    - uses SSID
    - forwards frames like a switch

## 9. Firewall

- OSI Layer 3,4,7

- security device that controls network traffic

- _working_
    - filers traffic based on rules
    - can inspect IP, ports, protocols 
    - advanced firewalls inspect application data

## 10. Proxy server

- OSI Layer 7 - application layer

- Acts an intermediary between client and internet

- _working_
    - receives requests from client
    - forwards to internet 
    - returns response
    - can cache data
    - can filter websites

## 11. Network Interface Card (NIC)

- OSI Layer 1 & 2

- hardware that connects a device to a network

- _working_ 
    - has unique MAC address
    - converts data to electricat signals
    - handles frame creation


| Device       | OSI Layer | Main Function               |
| ------------ | --------- | --------------------------- |
| Repeater     | Layer 1   | Regenerates signals         |
| Hub          | Layer 1   | Broadcasts data             |
| Bridge       | Layer 2   | Filters using MAC           |
| Switch       | Layer 2   | Intelligent forwarding      |
| Router       | Layer 3   | Routes using IP             |
| Gateway      | Layer 7   | Protocol translation        |
| Modem        | Layer 1   | Digital ↔ Analog conversion |
| Access Point | Layer 2   | Wireless connectivity       |
| Firewall     | 3,4,7     | Traffic filtering           |
| Proxy        | Layer 7   | Intermediary server         |
| NIC          | 1 & 2     | Connects device to network  |





