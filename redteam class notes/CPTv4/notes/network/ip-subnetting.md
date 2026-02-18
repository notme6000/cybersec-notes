# 1. IP Addresses (Internet Protocol Addresses)

An **IP address** is a logical address assigned to a device on a network. It allows devices to identify and communicate with each other.

## Purpose of IP Addresses

* Identify devices on a network
* Enable routing of data between networks
* Provide location addressing (where a device is)

## Two Main Versions

* **IPv4** (Internet Protocol version 4)
* **IPv6** (Internet Protocol version 6)



# 2. IPv4 (Internet Protocol Version 4)

## Overview

* 32-bit address
* Written in **dotted decimal format**
* Example: `192.168.1.1`

## Structure

IPv4 consists of 4 octets (8 bits each):

Example:

```
192.168.1.1
```

Binary:

```
11000000.10101000.00000001.00000001
```

Each octet ranges from:

```
0 to 255
```

Total possible IPv4 addresses:

```
2^32 = 4,294,967,296
```

## IPv4 Address Classes (Classful Addressing)

| Class | First Octet Range | Default Subnet Mask | Usage           | example      |
| ----- | ----------------- | ------------------- | --------------- | ------------ |
| A     | 1–126             | 255.0.0.0           | Large networks  | 10.1.2.3     |
| B     | 128–191           | 255.255.0.0         | Medium networks | 172.16.1.1   |
| C     | 192–223           | 255.255.255.0       | Small networks  | 192.168.1.10 |
| D     | 224–239           | N/A                 | Multicast       | 224.0.0.1    |
| E     | 240–255           | N/A                 | Experimental    | 250.1.1.1    |

Note:

* 127.0.0.1 is reserved for loopback
* 0.0.0.0 is reserved

## Private IPv4 Address Ranges

Used inside local networks (not routable on the internet):

* 10.0.0.0 – 10.255.255.255
* 172.16.0.0 – 172.31.255.255
* 192.168.0.0 – 192.168.255.255



# 3. IPv6 (Internet Protocol Version 6)

## Why IPv6?

IPv4 address exhaustion led to IPv6 development.

## Overview

* 128-bit address
* Written in hexadecimal
* Separated by colons

Example:

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

Total possible IPv6 addresses:

```
2^128
```

This is an extremely large number.

## IPv6 Address Shortening Rules

1. Remove leading zeros:

```
2001:db8:85a3:0:0:8a2e:370:7334
```

2. Replace consecutive zeros with "::" (only once per address):

```
2001:db8:85a3::8a2e:370:7334
```

## IPv6 Address Types

* **Unicast** – One-to-one communication
* **Multicast** – One-to-many
* **Anycast** – One-to-nearest

# 4. Subnetting

Subnetting is the process of dividing a network into smaller networks (subnets).

## Why Subnet?

* Improve performance
* Improve security
* Reduce broadcast traffic
* Better IP address management



# 5. Subnet Mask (IPv4)

A subnet mask defines which part of an IP address is:

* Network portion
* Host portion

Example:

```
IP:          192.168.1.10
Subnet Mask: 255.255.255.0
```

Binary mask:

```
11111111.11111111.11111111.00000000
```

1s = Network bits
0s = Host bits



# 6. CIDR Notation

CIDR = Classless Inter-Domain Routing

Instead of writing the subnet mask, we write:

```
192.168.1.0/24
```

The `/24` means:

* 24 bits are network bits
* 8 bits are host bits

Example conversions:

| CIDR | Subnet Mask     |
| - | --------------- |
| /8   | 255.0.0.0       |
| /16  | 255.255.0.0     |
| /24  | 255.255.255.0   |
| /25  | 255.255.255.128 |
| /26  | 255.255.255.192 |
| /27  | 255.255.255.224 |
| /28  | 255.255.255.240 |
| /29  | 255.255.255.248 |
| /30  | 255.255.255.252 |



# 7. Subnetting Formula

## Number of Subnets

```
2^n
```

Where:

* n = number of borrowed bits

## Number of Hosts per Subnet

```
2^h - 2
```

Where:

* h = number of host bits
* Minus 2 because:

  * One address is network address
  * One address is broadcast address



# 8. Example Subnetting

Given:

```
192.168.1.0/24
```

If we change to:

```
/26
```

Original:

* 24 network bits
* 8 host bits

New:

* 26 network bits
* 6 host bits

Hosts per subnet:

```
2^6 - 2 = 62
```

Number of subnets created:

```
2^(26 - 24) = 4
```

Subnets:

* 192.168.1.0/26
* 192.168.1.64/26
* 192.168.1.128/26
* 192.168.1.192/26



# 9. Network, Broadcast, and Host Addresses

For subnet:

```
192.168.1.0/26
```

* Network address: 192.168.1.0
* First host: 192.168.1.1
* Last host: 192.168.1.62
* Broadcast: 192.168.1.63



# 10. Key Differences: IPv4 vs IPv6

| Feature       | IPv4           | IPv6                           |
| ---------- | -------------- | ------------------------------ |
| Size          | 32-bit         | 128-bit                        |
| Format        | Decimal        | Hexadecimal                    |
| Address Space | ~4.3 billion   | Extremely large                |
| NAT Required  | Yes (commonly) | Not required                   |
| Broadcast     | Supported      | Not supported (uses multicast) |



