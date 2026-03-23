## How NAT Assigns a Public IP to Private IPs

**NAT (Network Address Translation)** allows multiple devices using private IP addresses (like 192.168.x.x) to access the internet using **one public IP address**.

It is usually performed by a router or firewall.



## Basic Idea

* Devices inside your network use **private IPs**
* Your router has:

  * 1 private IP (inside interface)
  * 1 public IP (outside interface)
* The router translates private addresses into the public address when sending traffic out



## Step-by-Step: How NAT Works (Outbound Traffic)

![Image](https://www.vmware.com/media/blt8c9a8aaca0ffd4ac/blt1b4d43cfd751feb5/66d1a48342d82e12814163ad/network-address-translation-diagram.png)

![Image](https://www.researchgate.net/publication/320322146/figure/fig1/AS%3A548239512018944%401507721893582/Typical-configuration-of-a-home-network-using-NAT.png)

![Image](https://www.watchguard.com/help/docs/help-center/en-us/Content/en-US/Fireware/configuration_examples/images/NAT_email_topology.jpg)

![Image](https://cdn-forum.networklessons.com/uploads/default/original/1X/318f9f8aa9d6db10d8e849c06a68772886caed19.png)

### Example:

* Laptop: **192.168.1.10**
* Router public IP: **203.0.113.5**
* Website: 8.8.8.8

### 1️⃣ Device Sends Request

Laptop sends:

```
Source: 192.168.1.10:5000
Destination: 8.8.8.8:80
```

### 2️⃣ Router Translates (NAT happens)

Router changes the source address:

```
Source: 203.0.113.5:40001
Destination: 8.8.8.8:80
```

It also stores this in a NAT table:

| Private IP   | Private Port | Public IP   | Public Port |
| --------- | ------------ | ----------- | ----------- |
| 192.168.1.10 | 5000         | 203.0.113.5 | 40001       |

### 3️⃣ Internet Replies

Server responds to:

```
203.0.113.5:40001
```

### 4️⃣ Router Looks at NAT Table

Router sees:

```
40001 → 192.168.1.10:5000
```

It changes the address back and sends it to the laptop.



# Types of NAT

### 1. Static NAT

* One private IP ↔ One public IP
* Permanent mapping
* Used for servers

Example:

```
192.168.1.100 → 203.0.113.10
```



### 2. Dynamic NAT

* Private IPs are assigned a public IP from a pool
* First come, first served



### 3. PAT (Port Address Translation) – Most Common

Also called **NAT Overload**

* Many private IPs share one public IP
* Differentiates devices using port numbers
* Used in homes and offices



# Why Ports Matter

Without port numbers, the router wouldn’t know which internal device should receive the reply.

Ports allow thousands of devices to share one public IP.



# What NAT Does NOT Do

* It does not give devices public IPs permanently (unless static NAT is used).
* It does not replace firewall security (though it adds some isolation).
* It does not encrypt traffic.



# Simple Analogy

Think of NAT like a company’s main phone number:

* Many employees (private IPs)
* One company phone number (public IP)
* The receptionist (router) tracks extensions (ports)




