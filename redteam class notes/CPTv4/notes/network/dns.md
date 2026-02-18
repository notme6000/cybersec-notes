

# 1. What is DNS?

**DNS (Domain Name System)** is a distributed system that translates human-readable domain names (like `example.com`) into IP addresses (like `93.184.216.34`) that computers use to communicate.

It works like the **phonebook of the internet**.


# 2. Why DNS is Needed

Humans remember domain names easily.
Computers communicate using IP addresses.

DNS resolves:

```
www.example.com → 93.184.216.34
```


# 3. Key Components of DNS

## 1. DNS Resolver (Recursive Resolver)

* Usually provided by your ISP or a public service (e.g., Google DNS 8.8.8.8).
* Receives your request and finds the correct IP address.

## 2. Root Name Servers

* Top-level DNS servers.
* Direct queries to the correct Top-Level Domain (TLD) servers.

## 3. TLD (Top-Level Domain) Servers

* Handle domain extensions like:

  * .com
  * .org
  * .net
  * .edu
* Direct requests to the authoritative name server.

## 4. Authoritative Name Server

* Holds the actual DNS records for the domain.
* Provides the final IP address.


# 4. Step-by-Step DNS Resolution Process

When you type `www.example.com` in your browser:

### Step 1: Check Local Cache

* Browser checks its own cache.
* OS checks its DNS cache.
* If found, process stops.

### Step 2: Query Recursive Resolver

* Request sent to DNS resolver.

### Step 3: Query Root Server

* Resolver asks root server.
* Root replies: “Ask the .com TLD server.”

### Step 4: Query TLD Server

* Resolver asks .com TLD server.
* TLD replies: “Ask this domain’s authoritative server.”

### Step 5: Query Authoritative Server

* Resolver asks authoritative server.
* Server returns the IP address.

### Step 6: Return IP to Client

* Resolver sends IP back to your computer.
* Browser connects to the web server using that IP.


# 5. DNS Record Types

Common DNS records:

* **A Record** – Maps domain to IPv4 address
* **AAAA Record** – Maps domain to IPv6 address
* **CNAME** – Alias of one domain to another
* **MX** – Mail server record
* **NS** – Name server record
* **TXT** – Text information (SPF, verification, etc.)
* **PTR** – Reverse DNS lookup


# 6. Caching in DNS

DNS responses are cached to improve speed.

Each record has a:

* **TTL (Time To Live)** – How long it can be cached

Benefits:

* Faster responses
* Reduced server load
* Lower network traffic


# 7. DNS Hierarchy Structure

DNS is hierarchical:

```
                Root (.)
                  |
          -------------------
          |        |        |
         .com     .org     .net
          |
      example.com
          |
      www.example.com
```


# 8. Recursive vs Iterative Query

## Recursive Query

* Resolver must return final answer.
* Client asks resolver once.

## Iterative Query

* Server responds with best info it has.
* Client/resolver continues querying other servers.


# 9. DNS Uses UDP and TCP

* **UDP port 53** – Default (fast, lightweight)
* **TCP port 53** – Used when:

  * Response is large
  * Zone transfers occur


# 10. DNS Security (Brief Overview)

DNS is vulnerable to:

* DNS spoofing
* Cache poisoning
* DDoS attacks

Security improvements:

* **DNSSEC** – Adds cryptographic verification
* DoH (DNS over HTTPS)
* DoT (DNS over TLS)


# 11. Summary

DNS:

* Converts domain names to IP addresses
* Works through a hierarchical system
* Uses caching for performance
* Relies on resolvers, root servers, TLD servers, and authoritative servers
* Is critical to how the internet functions


