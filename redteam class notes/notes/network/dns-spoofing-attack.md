# 1. What is DNS Spoofing?

**DNS Spoofing (DNS Cache Poisoning)** is a cyber attack where an attacker provides a fake DNS response to redirect users from a legitimate website to a malicious website.

It tricks users into visiting a fake site without them realizing it.


# 2. Why DNS Spoofing is Dangerous

DNS translates domain names into IP addresses.
If DNS is compromised:

```
www.bank.com → attacker’s fake IP address
```

Users think they are visiting the real website, but they are actually on a malicious server.

# 3. How DNS Spoofing Works (Step-by-Step)

### Step 1: User Requests a Website

User enters:

```
www.example.com
```

### Step 2: DNS Resolver Sends Query

The resolver asks for the IP address.

### Step 3: Attacker Sends Fake Response

The attacker:

* Sends a forged DNS reply faster than the real DNS server
* Provides a malicious IP address

### Step 4: Cache Poisoning

The resolver stores the fake IP in its cache.

### Step 5: Users Get Redirected

Future users are redirected to the attacker’s site until cache expires.


# 4. Types of DNS Spoofing

## 1. DNS Cache Poisoning

* Fake DNS data stored in resolver cache.

## 2. Man-in-the-Middle (MITM)

* Attacker intercepts DNS communication and modifies response.

## 3. Local DNS Spoofing

* Malware changes DNS settings on victim’s device.

## 4. Router DNS Hijacking

* Attacker compromises router and changes DNS server settings.

# 5. Goals of DNS Spoofing

* Steal login credentials
* Phishing attacks
* Spread malware
* Redirect traffic
* Advertising fraud

# 6. Example Scenario

1. User types: `www.bank.com`
2. Attacker poisons DNS cache.
3. User is redirected to a fake banking site.
4. User enters login credentials.
5. Attacker steals information.


# 7. Signs of DNS Spoofing

* Website looks slightly different
* HTTPS certificate warning
* Redirects to unknown pages
* Login not working properly
* Multiple users reporting same issue


# 8. Prevention Methods

## 1. DNSSEC (DNS Security Extensions)

* Adds digital signatures to DNS responses.
* Verifies authenticity of DNS data.

## 2. Use HTTPS

* Ensures encrypted communication.
* Helps detect fake websites.

## 3. Secure Routers

* Change default passwords.
* Update firmware regularly.

## 4. Use Trusted DNS Providers

* Google DNS (8.8.8.8)
* Cloudflare (1.1.1.1)

## 5. Enable DNS over HTTPS (DoH) or DNS over TLS (DoT)

* Encrypts DNS queries.

# 9. Difference Between DNS Spoofing and DNS Hijacking

DNS Spoofing:

* Fake DNS response injected.

DNS Hijacking:

* DNS settings are permanently changed to malicious DNS server.


# 10. Summary

DNS Spoofing:

* Is a redirection attack
* Manipulates DNS responses
* Can poison resolver cache
* Used for phishing and data theft
* Prevented using DNSSEC, HTTPS, and secure DNS practices



