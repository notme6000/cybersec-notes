
 

# NTLM Authentication in Active Directory (Step-by-Step)

## 1. User Initiates Login

* The user enters:

  * Username
  * Password
* The client machine does **not send the password in plaintext**.
* Instead, the password is converted into an **NT hash** using a hashing algorithm (MD4).

 

## 2. Client Sends Authentication Request

* The client sends a request to the server (Domain Controller or application server):

  * Username
  * Domain name
* This is called a **Negotiate message**.

 

## 3. Server Responds with Challenge

* The server generates a **random number (challenge)**, typically 8 bytes.
* The server sends this challenge back to the client.
* This is called a **Challenge message**.

 

## 4. Client Creates Response

* The client:

  1. Uses the NT hash of the password.
  2. Encrypts the server's challenge using this hash.
* This produces the **NTLM response**.
* The client sends:

  * Username
  * Domain
  * Encrypted challenge (response)
* This is called an **Authenticate message**.

 

## 5. Server Verifies Credentials

There are two cases:

### Case A: Local Authentication

* The server already has the user's NT hash.
* It:

  1. Encrypts the same challenge using the stored hash.
  2. Compares it with the client’s response.
* If both match → authentication succeeds.

### Case B: Domain Authentication (Active Directory)

* The server forwards the request to the **Domain Controller**.
* The Domain Controller:

  1. Retrieves the user's NT hash from Active Directory.
  2. Repeats the encryption of the challenge.
  3. Compares results.
* If matched → authentication successful.

 

## 6. Authentication Result

* If verification is successful:

  * The user is authenticated.
  * Access is granted.
* If not:

  * Access is denied.

 

# Key Concepts

## NT Hash

* A hash of the password (not salted).
* Stored in Active Directory.

## Challenge-Response Mechanism

* Prevents sending passwords over the network.
* Uses:

  * Server-generated challenge
  * Client-generated response

## No Mutual Authentication

* NTLM only authenticates the client to the server.
* The server is not authenticated to the client.

 

# NTLM Message Flow Summary

1. Client → Server: Negotiate (username, domain)
2. Server → Client: Challenge (random number)
3. Client → Server: Response (encrypted challenge)
4. Server/Domain Controller → Verify
5. Access Granted or Denied

 

# Limitations of NTLM

* Vulnerable to:

  * Pass-the-hash attacks
  * Relay attacks
* No mutual authentication
* Less secure compared to Kerberos

 


