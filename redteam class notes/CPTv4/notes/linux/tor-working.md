## How the Tor Network Works

![Image](https://upload.wikimedia.org/wikipedia/commons/e/e1/Onion_diagram.svg)



The Tor network (short for *The Onion Router*) is designed to improve privacy and anonymity online. It routes your internet traffic through multiple volunteer-operated servers around the world to conceal your identity and location.

Here is how it works step by step:



## 1. Onion Routing (Layered Encryption)

When you use Tor (typically through the Tor Browser), your data is:

* Wrapped in multiple layers of encryption
* Sent through a chain of three random servers called relays

Each layer of encryption corresponds to one relay in the path.



## 2. The Three Relays

A typical Tor circuit includes:

**Entry Node (Guard Node)**

* Knows your real IP address
* Does not know your final destination

**Middle Relay**

* Passes traffic between entry and exit
* Cannot see the origin or the final destination

**Exit Node**

* Sends your request to the final website
* Knows the destination
* Does not know who originally sent the request

Because no single relay knows both who you are and where you are going, your identity is protected.



## 3. Circuit Creation

When you connect:

1. Tor selects three relays from its directory of available nodes.
2. Your device negotiates encryption keys with each relay.
3. A secure circuit is built.
4. Your traffic flows through this circuit.

The circuit changes periodically to maintain anonymity.



## 4. What the Website Sees

The destination website only sees:

* The IP address of the exit node
* Not your real IP address

To the website, it appears that the traffic is coming from wherever the exit node is located.



## 5. Hidden Services (.onion Sites)

Tor also allows services that exist only inside the Tor network. These are called onion services and use .onion addresses.

In this case:

* The user’s location is hidden
* The server’s location is hidden
* Traffic never leaves the Tor network

This provides stronger anonymity for both parties.



## 6. Limitations

Tor improves privacy, but it is not perfect:

* It is slower than normal browsing due to multiple relays.
* Exit nodes can see unencrypted traffic (if the site does not use HTTPS).
* It does not protect against malware or careless user behavior.

Tor protects network identity, not everything about your digital footprint.


