## DoS attack (Denial of service attack)

- A DoS attack is a cyberattack where a single source overwhelms a system, server, or network to make it unavailable to legitimate users.

## DDoS attack (Distributed Denial of service attack)

- same as DoS but uses multiple sources for attack (eg: botnets)

### The logic behind a DoS attack

- Every system has limited resources, such as:
    - CPU
    - memory
    - bandwith

- A DoS attack works by:
    1. Sending excessive or malicious requests
    2. Forcing the system to consume all its resources
    3. Preventing legitimate users from accessing services
- _it does not steal data_   
- _it does not modify data_
- _it mainly targets Availability (CIA triad)_

### Example:

- A server can handle 100 requests per second
- An attacker sends 10,000 fake requests per second

- _Result_ : 
    - Server gets overloaded
    - Legitimate requests are dropped
    - Website crashes or slows down

### Types of DoS Attacks

1. volume-based attacks (traffic flodding)
    - _Logic_
        - The attacker floods the target with massive traffic to consume bandwidth
    - _working_
        - target has limited internet capacity
        - attacker sends huge amounts of data
        - network becomes congested
        - legitimate users cannot connect
    - _Examples_
        - UDP flood
        - ICMP (ping) Flood
2. Protocol-based attacks (resource exhaustion)
    - _Logic_
        - Exploit weaknesses in network protocol (like TCP) to consume server resources
    - _working_
        - attacker sends many TCP connection requests
        - server replies and waits for confirmation
        - attacker never responds
        - server memory fills with half-open connections
    - _Examples_
        - SYN flood
        - Ping of Death
        - Smurf Attack
3. Logical Attacks
    - _Logic_
        - Exploit software bugs or vulnerabilities to crash the system
    - _working_
        - send malformed packets
        - exploit unpatched vulnerabilities
        - trigger system crash
    - _Examples_
        - buffer overflow crash
4. Permanenet DoS 
    - _Logic_
        - damage hardware or firmware permanently
    - _working_
        - send malicious firmware updates
        - corrupt device memory
    - _Examples_
        - bricking routers or IoT devices

---

1. SYN flood
    - uses the TCP three-way handshake
    - _normal TCP handshake_
        1. client -> server: SYN
        2. server -> client: SYN-ACK 
        3. client -> server: ACK
        - connection established
    - _how SYN flood works_
        1. attacker sends many SYN requests
        2. server responds with SYN-ACK
        3. attacker never sends the final ACK

        - the server: 
            - keeps each half-open connection in memory
            - waits for an ACK that never comes
            - eventually runs out of connection slots
        - result:
            - legitimate users cannot connect
            - server becomes slow or unavailable




2. UDP flood
3. ICMP flood
4. smurf attack
    
