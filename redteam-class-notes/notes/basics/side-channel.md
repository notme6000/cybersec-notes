## Side-Channel Attacks

### Definition

A side-channel attack extracts sensitive information from a system by analyzing indirect information such as timing, power consumption, electromagnetic leaks, or acoustic signals rather than exploiting software vulnerabilities directly.

### How It Works

Instead of attacking the encryption algorithm itself, attackers observe how the system behaves during cryptographic operations.

### Common Side Channels

* Timing attacks
* Power analysis attacks
* Cache attacks
* Electromagnetic analysis

### Example (Timing Attack)

If a system compares a password character-by-character and stops when a mismatch occurs, an attacker can measure response times to determine correct characters one at a time.

### Example (Power Analysis)

An attacker measures the power consumption of a smart card while it performs encryption to deduce the secret key.

### Impact

* Cryptographic key extraction
* Bypassing secure hardware protections
* Compromising secure devices

### Prevention

* Constant-time algorithms
* Noise generation
* Hardware shielding
* Secure cryptographic implementations



