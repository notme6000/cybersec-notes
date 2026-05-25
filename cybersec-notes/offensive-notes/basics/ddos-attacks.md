Distributed Denial-of-Service (**DDoS**) attacks come in several categories, depending on how they overwhelm a target system. Broadly, they fall into three main types:



## 1. Volumetric Attacks (Bandwidth Exhaustion)

These aim to **flood the network with massive traffic**, consuming all available bandwidth.

### Common examples:

* **UDP Flood** – sends huge numbers of UDP packets to random ports.
* **ICMP Flood (Ping Flood)** – overwhelms with ping requests.
* **DNS Amplification** – uses open DNS servers to amplify traffic toward a victim.

### Key idea:

Overload the network pipe so legitimate traffic can’t get through.



## 2. Protocol Attacks (State Exhaustion)

These target **server resources or network equipment** by exploiting weaknesses in protocols.

### Common examples:

* **SYN Flood** – abuses the TCP handshake by sending many half-open connections.
* **Ping of Death** – sends malformed or oversized packets.
* **Smurf Attack** – uses ICMP broadcast to flood a victim.

### Key idea:

Exhaust server resources like connection tables, firewalls, or load balancers.



## 3. Application Layer Attacks (Layer 7 Attacks)

These mimic **legitimate user behavior**, making them harder to detect.

### Common examples:

* **HTTP Flood** – sends massive GET/POST requests to a website.
* **Slowloris** – keeps connections open as long as possible to exhaust server threads.
* **DNS Query Flood** – overwhelms DNS servers with requests.

### Key idea:

Target specific applications (web servers, APIs) instead of the whole network.



## 4. Multi-Vector Attacks

Modern attacks often combine multiple methods.

### Example:

* A mix of **SYN flood + HTTP flood + DNS amplification**

### Key idea:

Harder to defend because multiple layers are attacked simultaneously.




