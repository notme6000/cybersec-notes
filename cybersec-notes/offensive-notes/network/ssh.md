# 1. What is SSH?

**SSH (Secure Shell)** is a cryptographic network protocol used to securely access and manage remote systems over an unsecured network.

Default port:

```
TCP 22
```

SSH replaces insecure protocols like:

* Telnet
* rlogin
* FTP (for remote shell access)



# 2. Why SSH is Needed

Older remote access protocols:

* Sent passwords in plain text
* Were vulnerable to sniffing
* Had no encryption

SSH provides:

* Encryption
* Authentication
* Data integrity



# 3. What SSH Provides

## 1. Confidentiality

All communication is encrypted.

## 2. Authentication

Verifies server and client identity.

## 3. Integrity

Prevents data tampering.



# 4. SSH Architecture

SSH uses a **client-server model**:

* SSH Client → Initiates connection
* SSH Server → Accepts connection

Example:

```
ssh user@192.168.1.10
```



# 5. How SSH Works (Simplified Process)

## Step 1: TCP Connection

Client connects to server on port 22.

## Step 2: Version Exchange

Client and server exchange SSH versions.

## Step 3: Key Exchange

They negotiate:

* Encryption algorithm
* Key exchange method
* Hash algorithm

Common key exchange:

* Diffie-Hellman
* ECDH

They generate a shared secret.

## Step 4: Server Authentication

Server sends its public key.
Client verifies it using:

* Known_hosts file
* Certificate (if used)

## Step 5: User Authentication

Client authenticates using:

* Password
* Public key
* Multi-factor authentication

## Step 6: Secure Session Established

Encrypted communication begins.



# 6. SSH Encryption

SSH uses hybrid encryption:

## Asymmetric Cryptography

Used during key exchange and authentication.
Examples:

* RSA
* ECDSA
* Ed25519

## Symmetric Encryption

Used for session data.
Examples:

* AES
* ChaCha20

## Hashing

Used for integrity.
Examples:

* SHA-2 family



# 7. SSH Authentication Methods

## 1. Password Authentication

User enters password.
Less secure than key-based authentication.

## 2. Public Key Authentication (Recommended)

User generates key pair:

* Private key (kept secret)
* Public key (stored on server)

Process:

1. Server stores public key in:

   ```
   ~/.ssh/authorized_keys
   ```
2. Client proves it owns private key.
3. No password transmitted.

More secure and commonly used in servers.



# 8. SSH Keys

Common key types:

* RSA
* ECDSA
* Ed25519 (modern, recommended)

Generate key example:

```
ssh-keygen -t ed25519
```

Files created:

* id_ed25519 (private key)
* id_ed25519.pub (public key)



# 9. SSH Services

SSH supports more than remote login.

## 1. Remote Command Execution

Run commands on remote system.

## 2. Secure File Transfer

### SCP (Secure Copy)

```
scp file.txt user@server:/home/user/
```

### SFTP (SSH File Transfer Protocol)

Secure alternative to FTP.

## 3. Port Forwarding (Tunneling)

### Local Port Forwarding

Forwards local port to remote server.

### Remote Port Forwarding

Forwards remote port to local machine.

### Dynamic Port Forwarding

Creates SOCKS proxy.



# 10. SSH Port Forwarding Example

Example:

```
ssh -L 8080:localhost:80 user@server
```

Meaning:

* Local port 8080 forwards to server's port 80.

Used for:

* Secure database access
* Bypassing firewalls
* Secure internal services



# 11. SSH vs Telnet

| Feature           | SSH       | Telnet     |
| -------------- | --------- | ---------- |
| Encryption        | Yes       | No         |
| Password Security | Encrypted | Plain text |
| Port              | 22        | 23         |
| Security          | High      | Very low   |

SSH replaced Telnet.



# 12. SSH Security Best Practices

* Disable password authentication
* Use key-based authentication
* Disable root login
* Change default port (optional)
* Use firewall rules
* Enable multi-factor authentication
* Use strong key types (Ed25519)



# 13. Common SSH Attacks

## 1. Brute Force Attack

Automated password guessing.

Prevention:

* Disable password login
* Use fail2ban
* Strong passwords

## 2. Man-in-the-Middle (MITM)

Attacker intercepts connection.

Prevention:

* Verify server fingerprint
* Use known_hosts file



# 14. SSH Configuration Files

Client config:

```
~/.ssh/config
```

Server config:

```
/etc/ssh/sshd_config
```

Common server settings:

* PermitRootLogin no
* PasswordAuthentication no
* Port 22



# 15. Summary

* SSH = Secure remote access protocol.
* Uses TCP port 22.
* Provides encryption, authentication, integrity.
* Uses hybrid cryptography.
* Supports remote login, file transfer, tunneling.
* Key-based authentication is recommended.
* Replaces insecure Telnet and FTP.




