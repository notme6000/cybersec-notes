


# 1) What Is an IP Address?

An IP address is like a home address for a computer.

Example:

```
192.168.1.0
```

An IP address has 4 numbers.

Each number:

* Ranges from 0 to 255
* Is made of 8 bits (binary digits)

Why 0–255?

Because:

```
2^8 = 256 values
```

Since counting starts at 0:

```
0 to 255 = 256 total numbers
```

Each IP address has:

```
4 parts × 8 bits = 32 bits total
```



# 2) What Is Subnetting?

Imagine you have one big building with 256 rooms.

Subnetting means dividing that big building into smaller sections.

In networking:

Subnetting = dividing one big network into smaller networks.



# 3) Starting Network Example

We start with:

```
192.168.1.0/24
```

The “/24” is very important.



# 4) What Does /24 Mean?

It means:

24 bits are used for the network portion.

Total bits in an IP address:

```
32 bits
```

So:

```
32 total bits
- 24 network bits
= 8 host bits
```

Host bits are used for computers.



# 5) How Many Hosts in /24?

Formula:

```
2^(number of host bits) - 2
```

We subtract 2 because:

* 1 address is the network address
* 1 address is the broadcast address

For /24:

```
Host bits = 8
```

So:

```
2^8 = 256
256 - 2 = 254 usable hosts
```

So a /24 network can have 254 computers.



# 6) Now Let’s Subnet It

Suppose we want 4 smaller networks.



# 7) How Many Bits Do We Borrow?

Formula:

```
2^n ≥ number of subnets needed
```

We need 4 subnets.

Test values:

```
2^1 = 2 (not enough)
2^2 = 4 (correct)
```

So we borrow 2 bits.

Original network:

```
/24
```

After borrowing 2 bits:

```
/24 + 2 = /26
```

New subnet mask is:

```
/26
```



# 8) How Many Hosts Per Subnet?

Now we have:

```
32 total bits
- 26 network bits
= 6 host bits
```

Now calculate hosts:

```
2^6 = 64
64 - 2 = 62 usable hosts
```

Each subnet has 62 usable computers.



# 9) Find the Subnet Mask in Decimal

/26 in binary:

```
11111111.11111111.11111111.11000000
```

Last octet:

```
11000000
```

Convert to decimal:

```
128 + 64 = 192
```

So subnet mask is:

```
255.255.255.192
```



# 10) Find the Block Size

Formula:

```
256 - last octet of subnet mask
```

So:

```
256 - 192 = 64
```

Block size = 64

That means each subnet increases by 64.



# 11) List All 4 Subnets

Starting at 192.168.1.0

Increase by 64 each time:

Subnet 1:

```
Network:   192.168.1.0
Usable:    192.168.1.1 – 192.168.1.62
Broadcast: 192.168.1.63
```

Subnet 2:

```
Network:   192.168.1.64
Usable:    192.168.1.65 – 192.168.1.126
Broadcast: 192.168.1.127
```

Subnet 3:

```
Network:   192.168.1.128
Usable:    192.168.1.129 – 192.168.1.190
Broadcast: 192.168.1.191
```

Subnet 4:

```
Network:   192.168.1.192
Usable:    192.168.1.193 – 192.168.1.254
Broadcast: 192.168.1.255
```



# 12) Quick Formula Summary

1. Hosts per subnet:

```
2^(host bits) - 2
```

2. Number of subnets:

```
2^(borrowed bits)
```

3. Block size:

```
256 - subnet mask value
```



# Final Summary

Original network:

```
192.168.1.0/24
```

* 254 usable hosts

After subnetting to /26:

* 4 subnets
* 62 usable hosts each
* Subnet mask: 255.255.255.192
* Block size: 64

Subnetting means borrowing host bits to create more networks, which reduces the number of hosts per network.


