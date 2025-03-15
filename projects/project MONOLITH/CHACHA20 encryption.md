ChaCha20 is a **stream cipher** designed by Daniel J. Bernstein as a more secure and efficient alternative to AES in software implementations. It is widely used for encryption in modern applications, including VPNs, secure messaging, and TLS.

### **Key Features of ChaCha20**

1. **Security**:
    
    - Uses a 256-bit key and a 96-bit nonce.
    - Resistant to timing attacks due to its design (unlike AES, which relies on lookup tables that can leak information through side channels).
2. **Speed & Efficiency**:
    
    - Performs well on CPUs without hardware acceleration for AES.
    - More efficient in software implementations, especially on embedded systems and mobile devices.
3. **Nonce-Based Encryption**:
    
    - Uses a 96-bit nonce to ensure unique encryption for each message.
    - The nonce must not be reused with the same key to maintain security.
4. **Used in Modern Cryptography**:
    
    - Employed in **WireGuard VPN** for encryption.
    - Used in **TLS 1.3** (as an alternative to AES-GCM).
    - Google's **Adiantum** encryption uses ChaCha20 for disk encryption on low-power devices.

### **How ChaCha20 Works**

- Operates on a **512-bit state** consisting of:
    - A constant (128 bits)
    - The 256-bit encryption key
    - A 32-bit counter
    - A 96-bit nonce
- Uses a series of **20 rounds of mixing operations** (additions, rotations, and XORs) to transform plaintext into ciphertext.

### **ChaCha20-Poly1305**

ChaCha20 is often combined with **Poly1305**, an authentication algorithm, to provide **authenticated encryption** (AEAD). This ensures both confidentiality (encryption) and integrity (protection against tampering).

