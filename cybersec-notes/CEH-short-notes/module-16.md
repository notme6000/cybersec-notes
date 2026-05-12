
---

**Page 1**

**Module 16: Hacking Wireless Networks**

**Learning Objectives**

- Describe wireless concepts
- Explain different wireless encryption algorithms
- Describe wireless threats
- Describe wireless hacking methodology
- Use different wireless hacking tools
- Apply wireless hacking countermeasures
- Use different wireless security tools

---

**Wireless Concepts**

Wireless networks use radio-frequency (RF) technology instead of physical cables. Key terminology:

- **GSM (Global System for Mobile Communications):** Universal system for mobile data transmission worldwide.
- **Bandwidth:** Amount of data that can be transmitted over a connection, measured in bits per second (bps).
- **Access Point (AP):** Device that connects wireless devices to a wired network. Acts as a hub/switch between wired LAN and wireless clients.
- **BSSID (Basic Service Set Identifier):** The MAC address of an access point. Users are typically unaware of which BSS they belong to.
- **ISM Band (Industrial, Scientific, Medical):** Set of frequencies reserved for industrial, scientific, and medical communities. Used by Wi-Fi, Bluetooth, etc.
- **Hotspot:** Physical location where Wi-Fi networks are available for public use (airports, coffee shops, libraries).
- **Association:** The process of connecting a wireless device to an access point.
- **SSID (Service Set Identifier):** 32-alphanumeric-character unique name for a WLAN. Acts as the network identifier. All devices on the same WLAN must use the same SSID.
- **OFDM (Orthogonal Frequency-Division Multiplexing):** Splits a single signal into multiple orthogonal carrier frequencies. Supports higher bit rates than parallel channel operation.
- **MIMO-OFDM (Multiple Input, Multiple Output - OFDM):** Used in 4G and 5G to reduce interference and increase spectral efficiency.
- **DSSS (Direct-Sequence Spread Spectrum):** Multiplies original data signal with a pseudo-random noise code. Protects against interference and jamming.
- **FHSS (Frequency-Hopping Spread Spectrum):** Rapidly switches carrier among many frequency channels. Decreases unauthorized interception or jamming.

**Page 2**

**Wireless Networks: Advantages and Disadvantages**

| Advantages | Disadvantages |
|------------|---------------|
| Fast, easy installation without wiring through walls/ceilings | Security may not meet expectations |
| Provides connectivity where cables are difficult to lay | Bandwidth decreases as more devices connect |
| Access from anywhere within AP range | Upgrades may require new wireless cards and/or APs |
| Public spaces offer constant internet via WLAN | Some electronic equipment (microwaves, cordless phones) can interfere |

**Types of Wireless Networks**

**1. Extension to a Wired Network**
AP placed between wired network and wireless devices. Two AP types:
- **Software APs (SAPs):** Run on a computer equipped with a wireless NIC.
- **Hardware APs (HAPs):** Support most wireless features.

**2. Multiple Access Points**
When a single AP cannot cover an area, multiple overlapping APs provide seamless roaming. Users move between APs without losing connectivity.

**3. LAN-to-LAN Wireless Network**
Interconnects computers on different networks using APs. Hardware APs can interconnect with other hardware APs, though it is complex.

**4. 3G/4G/5G Hotspot**
Provides Wi-Fi access to Wi-Fi-enabled devices (MP3 players, notebooks, tablets, cameras, PDAs) using cellular data connections.

**Wireless Standards (IEEE 802.11 Family)**

| Amendment | Frequency | Modulation | Speed | Range |
|-----------|-----------|------------|-------|-------|
| 802.11 (original) | 2.4 GHz | DSSS, FHSS | 1-2 Mbps | 20-100 m |
| 802.11a | 5 GHz | OFDM | 6-54 Mbps | 35-100 m |
| 802.11b | 2.4 GHz | DSSS | 1-11 Mbps | 35-140 m |
| 802.11g | 2.4 GHz | OFDM | 6-54 Mbps | 38-140 m |
| 802.11n | 2.4/5 GHz | MIMO-OFDM | 54-600 Mbps | 70-250 m |
| 802.11ac | 5 GHz | MIMO-OFDM | Up to 3.5 Gbps | Variable |
| 802.11ax (Wi-Fi 6) | 2.4-5 GHz | 1024-QAM | Up to 9.6 Gbps | 240 m |
| 802.11be (Wi-Fi 7) | 2.4/5/6 GHz | QAM | Up to 30 Gbps | 120 m |
| 802.11d | — | — | Global portability (frequency/power variations) | — |
| 802.11e | — | — | QoS for data/voice/video (prioritization) | — |
| 802.11i | — | — | Improved encryption (WPA2) | — |
| 802.15.1 (Bluetooth) | 2.4 GHz | GFSK, DPSK | 25-50 Mbps | 10-240 m |
| 802.15.4 (ZigBee) | 868 MHz, 915 MHz, 2.4 GHz | O-QPSK, GFSK, BPSK | 20-250 Kbps | 1-100 m |
| 802.16 (WiMAX) | 2-11 GHz | SOFDMA | 34-1000 Mbps | 1-6 miles |

**Page 3**

**Service Set Identifier (SSID)**
- Case-sensitive, 32-character unique identifier for a WLAN.
- Sent in cleartext in beacons, probe requests/responses, and association requests.
- Default SSIDs are often the vendor name (e.g., "Linksys", "Netgear"), making them easy to identify.
- **Security note:** SSID hiding does NOT provide security; attackers can still discover hidden SSIDs using tools like mdk3.

**Wi-Fi Authentication Process**

**Pre-Shared Key (PSK) Mode (WPA/WPA2-Personal)**
- Single shared password used for all devices.
- Popular in homes and small offices due to simplicity.
- Security depends entirely on password complexity and secrecy.
- The password (pre-shared key) is manually entered into both router and client devices.

**Centralized Authentication Mode (WPA/WPA2-Enterprise / 802.1X)**
- Uses a RADIUS (Remote Authentication Dial-In User Service) server.
- Each user has unique credentials (username/password or digital certificate).
- Suitable for large organizations (corporate offices, schools, government).
- Provides individual accountability and easier revocation of access.

**Types of Wireless Antennas**

| Antenna Type | Characteristics | Use Case |
|--------------|----------------|----------|
| Directional | Broadcasts/receives from single direction; reduces interference | Point-to-point links |
| Omnidirectional | 360° horizontal radiation pattern | Radio stations, general coverage |
| Parabolic Grid | Highly focused radio beams; range up to 10 miles | Long-distance Wi-Fi, Layer-1 DoS/MITM attacks |
| Yagi (Yagi-Uda) | High gain, low SNR; unidirectional | VHF/UHF communications |
| Dipole | Half-wavelength straight conductor; bilaterally symmetrical | Basic RF transmission |
| Reflector | Concentrates EM energy at focal point; high manufacturing cost | Satellite communications |

---

**Page 4**

**Wireless Encryption Algorithms**

**Overview**
Wireless encryption protects against attackers who attempt to collect sensitive information by breaching RF traffic.

| Algorithm | Key Features | Status |
|-----------|--------------|--------|
| WEP | RC4 stream cipher, 24-bit IV, CRC-32 checksum | Broken, deprecated |
| WPA | TKIP (RC4 with 128-bit keys), 64-bit MIC, 48-bit IV | Weak, deprecated |
| WPA2 | AES-CCMP, 4-way handshake | Still used but being replaced |
| WPA3 | SAE/Dragonfly, GCMP-256, 192-bit security suite | Current standard |

**WEP (Wired Equivalent Privacy) - Detailed**

**What is WEP?**
- Component of IEEE 802.11 standards.
- Designed to provide confidentiality equivalent to wired LANs.
- Uses symmetric Rivest Cipher 4 (RC4) encryption algorithm.

**Key Sizes:**
- 64-bit WEP → 40-bit key + 24-bit IV
- 128-bit WEP → 104-bit key + 24-bit IV
- 256-bit WEP → 232-bit key + 24-bit IV

**How WEP Works:**
1. CRC-32 calculates a 32-bit ICV (Integrity Check Value) for the data.
2. 24-bit IV is added to the WEP key → WEP seed.
3. RC4 algorithm generates a keystream from the seed.
4. Keystream is XORed with (data + ICV) to produce ciphertext.
5. IV field is added to ciphertext to create MAC frame.

**Major Flaws of WEP:**
- No defined method for encryption key distribution (PSKs rarely changed).
- IV is only 24 bits → repeats within hours on busy APs.
- IV sent in cleartext portion of message.
- CRC-32 is not a cryptographic hash → vulnerable to bit-flipping.
- Vulnerable to FMS (Fluhrer-Mantin-Shamir) attack.
- All users share the same key.
- No protection against replay attacks.

**Page 5**

**WPA (Wi-Fi Protected Access) - Detailed**

- Defined by 802.11i standard as an expansion for increased security.
- Uses TKIP (Temporal Key Integrity Protocol) with RC4 stream cipher (128-bit keys, 64-bit MIC).
- Eliminates WEP weaknesses through:
  - Per-packet mixing functions
  - Message Integrity Check (MIC / "Michael")
  - Extended initialization vectors (48-bit)
  - Re-keying mechanisms

**TKIP (Temporal Key Integrity Protocol) Details:**
- Unicast encryption key changes for every packet.
- Uses Michael Integrity Check algorithm with MIC key.
- Client starts with 128-bit TK (Temporal Key), combines with MAC address and IV to create keystream.
- Implements sequence counter to protect against replay attacks.
- Rekeying every 10,000 packets.

**Four-Way Handshake (WPA/WPA2):**
1. AP sends ANonce to client.
2. Client constructs PTK (Pairwise Transient Key) and sends SNonce + MIC.
3. AP sends GTK (Group Temporal Key) + sequence number + MIC.
4. Client confirms keys are installed.

**WPA2 - Detailed**

- Upgrade to WPA, mandatory support for CCMP (Counter Mode Cipher Block Chaining Message Authentication Code Protocol).
- Uses AES (Advanced Encryption Standard) instead of RC4.
- FIPS 140-2 compliant.

**WPA2-Personal (PSK):**
- Same 256-bit key generated from an 8-63 character passphrase + SSID.
- Each device encrypts traffic using 128-bit key derived from passphrase.

**WPA2-Enterprise:**
- Integrates EAP standards with WPA2 encryption.
- Uses RADIUS for centralized authentication.
- Supports EAP methods: TLS, TTLS, PEAP, LEAP, etc.

**How WPA2 Works (CCMP):**
1. Additional Authentication Data (AAD) from MAC header included in encryption.
2. Nonce generated from packet number + MAC header portion.
3. AES + CCMP encrypts plaintext data.
4. Produces ciphertext + encrypted MIC value.
5. Assembled as MAC header + CCMP header + encrypted data + encrypted MIC.

**Page 6**

**WPA3 - Detailed**

- Announced January 2018 by Wi-Fi Alliance.
- Uses Simultaneous Authentication of Equals (SAE) / Dragonfly Key Exchange (replaces PSK).

**WPA3-Personal Features:**
- **Resistance to offline dictionary attacks:** Prevents brute-forcing of captured handshakes.
- **Forward secrecy:** Even if password is discovered, past session keys cannot be decrypted.
- **Natural password choice:** Allows weaker passwords without compromising security.
- **Opportunistic Wireless Encryption (OWE):** Encrypts open networks (replaces "open" authentication).

**WPA3-Enterprise Features:**
- **Authenticated encryption:** GCMP-256 (256-bit Galois/Counter Mode Protocol).
- **Key derivation:** HMAC-SHA-384.
- **Key establishment:** ECDSA-384 and ECDH-384.
- **Frame protection:** BIP-GMAC-256.

**Enhancements over WPA2:**
1. **Secured handshake:** SAE/Dragonfly prevents offline decryption.
2. **Wi-Fi Easy Connect (DPP):** QR code-based provisioning for IoT devices.
3. **Unauthenticated encryption (OWE):** Protects public hotspot users.
4. **192-bit security suite:** For government and high-security environments.

**Issues with WEP, WPA, WPA2, WPA3**

**WEP Issues (detailed):**
- 24-bit IV → exhausted in 5 hours on 11 Mbps AP.
- CRC-32 bit-flipping attacks possible.
- Weak IVs from key scheduling algorithm (KSA).
- FMS attack can recover key from ~40,000 packets.
- No centralized key management.
- No replay attack protection.

**WPA Issues:**
- Weak passwords vulnerable to dictionary attacks (e.g., Cowpatty).
- No forward secrecy.
- TKIP MIC exploit can trigger DoS (AP shuts down for 60 seconds).
- GTK predictability with poor RNG.

**Page 7**

**WPA2 Issues:**
- **KRACK (Key Reinstallation Attack):** Forces nonce reuse in 4-way handshake. Affects all modern protected Wi-Fi networks.
- **Hole196 vulnerability:** Exploits GTK to perform MITM and DoS.
- **No forward secrecy:** Capturing PSK allows decryption of all past traffic.
- **WPS PIN recovery:** WPS PIN can be brute-forced (Reaver tool) to recover PSK.

**WPA3 Issues:**
- **Dragonblood vulnerabilities (2019):**
  - Downgrade attacks (force WPA2 transition mode).
  - Timing-based side-channel attacks on SAE.
  - Cache-based side-channel attacks.
- **Implementation challenges:** Older devices cannot support WPA3.
- **Limited adoption:** Many networks still use WPA2.
- **Transition mode weakness:** Network may still be vulnerable via WPA2 clients.

---

**Wireless Threats**

**Access Control Attacks**
- **MAC Spoofing:** Change MAC address to appear as authorized AP/client.
- **AP Misconfiguration:** Default SSID, weak passwords, SSID broadcast enabled.
- **Ad Hoc Associations:** Force client into insecure ad-hoc mode.
- **Promiscuous Client:** Attacker AP with stronger signal lures clients.
- **Client Mis-association:** Client accidentally connects to neighboring rogue AP.
- **Unauthorized Association:** Malicious soft APs (virus-activated) or accidental association with overlapping networks.

**Integrity Attacks**
- **Data Frame Injection:** Forged 802.11 frames (Airpwn-ng, Wperf).
- **WEP Injection:** Forged WEP encryption keys.
- **Bit-Flipping Attacks:** Modify ICV to match altered payload.
- **Replay Attacks:** Captured EAP, RADIUS, or data frames replayed later.

**Page 8**

**Confidentiality Attacks**
- **Eavesdropping:** Capturing unprotected traffic (Wireshark, Kismet).
- **Traffic Analysis:** Inferring information from external characteristics.
- **Evil Twin:** Rogue AP with legitimate SSID (Hostapd, Wifiphisher).
- **Honeypot AP:** Attacker AP with popular SSID to lure users.
- **Session Hijacking:** Attacker appears as desired destination.
- **MITM Attack:** Intercept, read, or alter transmitted information.

**Availability Attacks**
- **De-authentication Flood:** Forged deauth/disassoc frames disconnect users (AirJack).
- **Beacon Flood:** Thousands of counterfeit beacons confuse clients.
- **Jamming Signal Attack:** High-gain amplifier drowns legitimate AP.
- **Power Saving Attack:** Spoofed TIM/DTIM forces client into DoS.
- **TKIP MIC Exploit:** Invalid TKIP data exceeds error threshold → AP suspends service (60 seconds).

**Authentication Attacks**
- **PSK Cracking:** Dictionary attack on captured handshake (Cowpatty, Fern).
- **LEAP Cracking:** Asleap cracks Cisco LEAP.
- **KRACK:** Key reinstallation on WPA2.
- **Wi-Jacking Attack:** Exploit saved router credentials in browser to extract WPA2 PSK.

**Honeypot AP Attack (detailed)**
- Attacker sets up rogue AP with same SSID as target, plus high-gain antenna.
- User's NIC automatically connects to strongest signal.
- Attacker captures identity, username, password.

**Wormhole Attack**
- Attacker tunnels RREQ/RREP messages in ad-hoc routing (AODV, DSR).
- Creates fake direct link between source and destination.
- Attacker controls data flow between nodes.

**Sinkhole Attack**
- Compromised node advertises shortest path to base station.
- Attracts all neighboring nodes' traffic.
- Often combined with wormhole attack.

**Inter-Chip Privilege Escalation (Wireless Co-existence Attack)**
- Exploits combo chips (Bluetooth + Wi-Fi on same die).
- Bluetooth chip can steal data from Wi-Fi chip or manipulate Wi-Fi traffic.

---

**Page 9**

**Wireless Hacking Methodology**

**Five Steps:**
1. Wi-Fi Discovery (footprinting)
2. Wireless Traffic Analysis
3. Launch of Wireless Attacks
4. Wi-Fi Encryption Cracking
5. Wi-Fi Network Compromising

**Step 1: Wi-Fi Discovery**

**Passive Footprinting:**
- Sniff packets from airwaves without injecting any data.
- Discovers wireless devices, APs, and SSIDs.
- No association with any AP or client.

**Active Footprinting:**
- Sends probe request with SSID (or empty SSID).
- Most APs respond with their SSID in probe response even if request is empty.
- Attacker then knows correct BSS to associate with.

**Wi-Fi Chalking Techniques:**
- **WarWalking:** Walking with Wi-Fi-enabled laptop and discovery tool.
- **WarChalking:** Drawing symbols on public places to advertise open networks.
- **WarFlying:** Using drones to detect open wireless networks.
- **WarDriving:** Driving around mapping active wireless networks.

**Common Discovery Tools:**
- inSSIDer (Metageek) – signal strength, channel visualization, GPS export.
- Sparrow-wifi – GUI tool with HackRF, Ubertooth, GPS integration.
- Wi-Fi Scanner, Acrylic WiFi Heatmaps, WirelessMon, NetSpot.
- Mobile: WiFi Analyzer, Opensignal, Net Signal Pro, WiFiMan.

**Finding WPS-Enabled APs (Wash utility):**
```bash
sudo wash -i wlan0
```
- Shows AP, ESSID, BSSID, locked/unlocked state.
- WPS locks after 5 incorrect attempts; unlocks only via admin interface.

**Page 10**

**Step 2: Wireless Traffic Analysis**

**Purpose:**
- Determine broadcasted SSID, presence of multiple APs, possibility of recovering hidden SSIDs.
- Identify authentication method and WLAN encryption algorithms.
- Find vulnerable clients and ideal attack strategy.

**Process:**
- Enable monitor mode on Wi-Fi card (not all cards support this in Windows).
- Use packet sniffer to capture 802.11 frames (management, control, data).

**Key Tools:**

**Wireshark:**
- Reads live data from 802.11 WLAN, Ethernet, Token Ring, FDDI, PPP, etc.
- Requires Npcap for full WLAN traffic analysis in Windows.
- Radiotap header fields reveal protocols, encryption, frame lengths, MAC addresses.

**CommView for Wi-Fi:**
- Monitor for 802.11 a/b/g/n networks.
- Decrypts packets with user-defined WPA-PSK keys.
- Displays per-node/per-channel statistics, signal strength, protocol charts.

**Other sniffers:** OmniPeek, Kismet, SolarWinds NPM, Acrylic Wi-Fi Analyzer.

**Choosing the Optimal Wi-Fi Card**

**Considerations:**
- Injection capability (Windows cannot inject; Linux recommended).
- Chipset compatibility (e.g., Atheros, Ralink, Realtek).
- Driver support for monitor mode and packet injection.

**Chipsets known to work:** Atheros AR9271, Ralink RT3070, Realtek RTL8812AU.

**Spectrum Analysis:**
- Detects RF interference, identifies transmission sources.
- Measures spectrum power of known and unknown signals.
- Helps detect DoS attacks, authentication/encryption attacks.
- **RF Explorer:** Handheld or PC-connected spectrum analyzer.

**Page 11**

**Step 3: Launch of Wireless Attacks**

**Aircrack-ng Suite (Key Tools):**

| Tool | Function |
|------|----------|
| airmon-ng | Enable/disable monitor mode |
| airodump-ng | Capture raw 802.11 frames, collect WEP IVs |
| aireplay-ng | Packet injection, deauth attacks, WEP IV gathering, WPA handshake capture |
| aircrack-ng | Crack WEP and WPA/WPA2-PSK |
| airbase-ng | Act as ad-hoc AP, capture handshakes |
| airdecap-ng | Decrypt WEP/WPA/WPA2, strip wireless headers |
| airdrop-ng | Rule-based de-authentication |
| airolib-ng | Store/manage ESSID and password lists |
| airtun-ng | Virtual tunnel interface for encrypted traffic injection |

**Detection of Hidden SSIDs (mdk3):**
```bash
airmon-ng start wlan0
airodump-ng wlan0mon          # hidden SSID shows blank
mdk3 wlan0mon p -b 1 -c <ch> -t <BSSID>
```
- `p` = basic probing and ESSID brute-force mode
- `-b 1` = beacon flood mode with EAPOL logoff test
- Reveals hidden SSID after brute-force.

**Denial-of-Service (DoS) Attacks**
- **Disassociation attack:** Send forged disassoc frames → victim unavailable.
- **De-authentication attack:** Flood with forged deauth frames → disconnect users from AP.
- **Jamming signal attack:** High-gain amplifier on same frequency → legitimate AP drowned out. Because 802.11 uses CSMA/CA, silence period required before transmission; jamming makes channel appear always busy.

**Man-in-the-Middle (MITM) Attack Process:**
1. Sniff victim's wireless parameters (MAC, ESSID/BSSID, channels).
2. Send DEAUTH request to victim with spoofed source address of legitimate AP.
3. Victim de-authenticated → searches all channels for new AP.
4. Attacker sets forged AP on new channel with original BSSID and ESSID.
5. Victim connects to forged AP.
6. Attacker spoofs victim to connect to original AP.
7. Attacker positioned between AP and victim, listening to all traffic.

**Page 12**

**MAC Spoofing Attack**
- **AP MAC spoofing:** Impersonate legitimate AP by changing MAC address and SSID.
- **Client MAC spoofing:** Change MAC address to bypass MAC filtering.
- Linux: `ifconfig eth0 down ; ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX ; ifconfig eth0 up`
- Tools: Technitium MAC Address Changer, LizardSystems Change MAC Address.

**ARP Poisoning Attack (Ettercap):**
1. Sniff → Unified Sniffing → select interface.
2. Hosts → Scan for Hosts → Hosts List.
3. Select target IP → Targets → Current targets.
4. MITM → ARP poisoning → Sniff remote connections → OK.
5. All traffic between victim and gateway passes through attacker.

**Rogue AP Attack**
- Unauthorized AP giving backdoor access.
- **Deployment scenarios:**
  - Pocket-sized AP plugged into Ethernet port.
  - AP connected over Wi-Fi link (requires credentials).
  - USB-based AP plugged into corporate machine.
  - Software-based AP on Windows machine.
- **Steps:** Choose location (max coverage) → Disable SSID broadcast → Place behind firewall → Deploy briefly.

**Evil Twin Attack**
- Rogue AP imitating legitimate SSID.
- **KARMA tool:** Listens to probe request frames, adopts any commonly used SSID.
- Stations automatically reconnect to SSIDs used in the past.
- Attacker can bypass enterprise security policies after association.

**Hotspot (Fake Hotspot) Setup:**
1. Enable Internet Connection Sharing (Windows) or Internet Sharing (macOS).
2. Broadcast Wi-Fi connection.
3. Run sniffer to capture passwords.

**Page 13**

**Key Reinstallation Attack (KRACK) - Detailed**
- Exploits 4-way handshake of WPA2 by forcing nonce reuse.
- Attacker captures ANonce already in use, manipulates and replays handshake messages.
- Works against WPA1, WPA2, personal, enterprise, TKIP, AES-CCMP, GCMP.
- Allows decryption of packets, session hijacking, malware injection.
- Affects Android, Linux, Windows, Apple, OpenBSD, MediaTek.

**aLTER Attack (LTE/4G)**
- Performed on devices using AES-CTR mode (encryption without integrity protection).
- Attacker installs fake communication tower between user and real tower.
- **Two phases:**
  1. **Information gathering:** Identity mapping (locate target device), website fingerprinting (record traffic patterns).
  2. **Attack:** DNS spoofing redirects victim to malicious websites.
- MITM at Layer 2 (datalink layer).

**Wi-Jacking Attack**
**Conditions required:**
- At least one active client connected to target network.
- Client previously connected to an open network with auto-reconnect.
- Chromium-based browser with stored router admin credentials.
- Router uses HTTP (not HTTPS) for admin interface.

**Steps:**
1. Deauth victim (aireplay-ng).
2. KARMA attack (hostapd-wpe) lures victim to malicious AP.
3. Inject malicious URL (dnsmasq + Python scripts).
4. Victim opens HTTP page → browser auto-fills stored admin credentials.
5. Malicious page remains in router's admin interface with credentials loaded in JavaScript.
6. XMLHttpRequest extracts WPA2 PSK and other credentials.

**RFID Cloning Attack**
- Capture data from legitimate RFID tag, copy to new chip.
- iCopy-X: Standalone device with screen and buttons.
- Other tools: RFIDler, Flipper Zero, Boscloner Pro, Mifare Cloner.

---

**Page 14**

**Step 4: Wi-Fi Encryption Cracking**

**WPA/WPA2 Cracking Techniques**

**Offline Attack:**
- Capture full authentication handshake (client + AP) → needs only seconds near AP.
- Crack offline without packet injection.
- Protocol does not send password across network; handshake occurs over insecure channels.

**De-authentication Attack:**
- Find actively connected client.
- Force client to disconnect (aireplay-ng deauth).
- Capture re-authentication packets (include PMK).
- Crack PMK via dictionary or brute-force.

**Brute-Force WPA Keys:**
- Compute-intensive; may take hours, days, or weeks.
- Tools: aircrack-ng, hashcat, cowpatty.

**Cracking WPA/WPA2 with Aircrack-ng (detailed steps):**
```bash
# 1. Enable monitor mode
airmon-ng start wlan0
airmon-ng check kill   # if processes cause trouble

# 2. Discover networks
airodump-ng wlan0mon

# 3. Target specific AP and capture
airodump-ng --bssid <BSSID> -c <CH> -w capture wlan0mon

# 4. Deauth client to force handshake
aireplay-ng -0 11 -a <BSSID> -c <Client_MAC> wlan0mon

# 5. Wait for "WPA handshake" in airodump terminal

# 6. Crack
aircrack-ng -a2 <BSSID> -w password.txt capture-01.cap
```

**Fern Wifi Cracker (GUI):**
- Select adapter → Monitor Mode → Scan for APs → Select target → Attack (deauth) → Choose wordlist → Start WPA Attack.

**WPA3 Cracking (Dragonblood)**

**Downgrade Attacks:**
- **Exploiting backward compatibility:** Rogue AP with only WPA2 forces client to use 4-way handshake.
- **Exploiting Dragonfly handshake:** Attacker AP masquerades as authentic AP, claims no WPA3 support, suggests WPA2.

**Side-Channel Attacks:**
- **Timing-based:** Analyze time taken for Dragonfly handshake to encode password → short-list possible passwords.
- **Cache-based:** Malicious JavaScript in browser observes memory access patterns → retrieves password.

**Tools:** Dragonlayer, Dragonforce, Dragonrain, Dragontime, hashcat.

**Cracking WPA3 with hashcat:**
```bash
# Convert .cap to .hccapx
hccapxconfigtool -o capture.hccapx capture.cap

# Crack
hashcat -m 22000 capture.hccapx wordlist.txt
```

**Page 15**

**Cracking WPS with Reaver:**
```bash
# Monitor mode
airmon-ng start wlan0

# Find WPS-enabled APs
wash -i mon0

# Or use airodump-ng
airodump-ng wlan0mon

# Crack WPS PIN
reaver -i wlan0mon -b <BSSID> -vv
```
- Reaver brute-forces WPS PIN (8 digits, ~11,000 attempts max).
- Once PIN found, AP reveals WPA/WPA2 passphrase.

---

**Wireless Attack Countermeasures**

**Wireless Security Layers (Defense in Depth):**
1. **Signal security:** Continuous monitoring, WIDS (Wireless Intrusion Detection System).
2. **Connection security:** Per-frame/packet authentication prevents MITM.
3. **Device security:** Vulnerability and patch management.
4. **Data protection:** WPA3, WPA2, AES.
5. **Network protection:** Strong authentication (only authorized users).
6. **End-user protection:** Personal firewalls on WLAN systems.

**Defense Against WPA/WPA2/WPA3 Cracking:**
- Use strong passwords (12-16+ characters, uppercase, lowercase, numbers, specials).
- Disable TKIP; use AES-only.
- Turn off WPS.
- Update router firmware regularly.
- Limit Wi-Fi signal range (reduce transmission power).
- Enable WPA3-SAE; disable transition mode if all devices support WPA3.
- Use VPN (IPsec, SSL/TLS).
- MAC address filtering (limited value but adds layer).
- Disable remote management.

**Defense Against KRACK Attacks:**
- Update all routers and Wi-Fi devices with latest security patches; enable auto-updates.
- Avoid public Wi-Fi networks.
- Use HTTPS Everywhere extension, 2FA, VPN.
- Disable fast roaming and 802.11r if not needed.
- Use WPA3.
- Implement 802.1X with RADIUS for enterprise.

**Page 16**

**Defense Against aLTER Attacks:**
- Encrypt DNS queries (DNS over HTTPS, DNS over TLS, DNS over DTLS).
- Use DNSCrypt protocol for authenticated communication.
- Implement DNSSEC.
- Use mutual authentication and AES-256 encryption.
- Upgrade to 5G.
- Use Cisco Security Connectors app (encrypts DNS, loads to Cisco Umbrella).

**Detection and Blocking of Rogue APs**

**Detection Methods:**
- **RF Scanning:** Dedicated sensors (repurposed APs) capture and analyze packets.
- **AP Scanning:** APs detect neighboring APs via MIBs and web interface.
- **Wired Side Inputs:** Network management software detects devices via Telnet, SNMP, CDP.
- **Comparison with authorized AP list (AirMagnet WiFi Analyzer).**
- **Signal strength analysis (Ekahau Survey).**
- **MAC address filtering (Cisco WLC built-in detection).**

**Blocking Methods:**
- Launch DoS attack against rogue AP.
- Block switch port (manually or automatically).
- Physically locate and remove AP.
- WIPS (Wireless Intrusion Prevention System) automated blocking.
- ACLs restricting to authorized MAC addresses.
- 802.1X authentication.
- Network segmentation.

**Best Practices for Configuration:**
- Change default SSID and admin password.
- Disable SSID broadcast, remote login, DHCP, SNMP.
- Enable firewall and MAC filtering.
- Use WPA3 or WPA2-AES.
- Use VLANs or separate SSIDs for traffic segmentation.
- Set up separate guest network.
- Adjust transmission power to limit signal range.
- Close unused ports.

**Page 17**

**Best Practices for SSID Settings:**
- Use SSID cloaking (but remember it's not true security).
- Do not use company name or easy-to-guess strings.
- Place firewall between AP and corporate intranet.
- Limit wireless signal strength.
- Regularly check wireless devices for configuration problems.
- Implement additional encryption (IPsec over wireless).
- Use separate SSID for guests.
- Periodically change SSIDs and passwords.

**Best Practices for Authentication:**
- Enable WPA3-Enterprise with RADIUS.
- Use 802.1X with mutual authentication (prevents MITM).
- Implement multifactor authentication.
- Disable network when not required.
- Place APs in secured physical locations.
- Keep drivers updated.
- Use centralized authentication server.
- Deploy rogue AP detection or WIPS.

**Wireless Intrusion Prevention System (WIPS)**

**Cisco Adaptive WIPS components:**
- **APs in monitor mode:** Constant channel scanning, attack detection, packet capture.
- **Mobility Services Engine (MSE):** Central alarm aggregation, forensics storage.
- **Local mode APs:** Provide client service + time-sliced rogue/location scanning.
- **Wireless LAN Controllers (WLCs):** Forward attack info to MSE, distribute config.
- **Wireless Control System (WCS):** Configure WIPS service, view alarms, reporting.

**Other WIPS solutions:**
- WatchGuard Wi-Fi Cloud WIPS (defends against rogue APs, evil twins, DoS).
- Extreme AirDefense, Arista WIPS, SonicWall Wireless Network Manager.
- Cisco Meraki, FortiGate NGFW.

**Wi-Fi Security Auditing Tools:**
- RFProtect (Aruba), OSWA-Assistant, BoopSuite, Wifite.

---

**Page 18**

**Module Summary**

This module covered:

**Wireless Concepts & Encryption:**
- Wireless terminology (SSID, BSSID, AP, OFDM, DSSS, FHSS)
- IEEE 802.11 standards (802.11a/b/g/n/ac/ax/be, Bluetooth, ZigBee, WiMAX)
- Encryption algorithms: WEP (broken), WPA (TKIP, weak), WPA2 (AES-CCMP), WPA3 (SAE/Dragonfly, GCMP-256)
- Issues with each encryption standard (IV weaknesses, KRACK, Dragonblood)

**Wireless Threats:**
- Access control attacks (MAC spoofing, misconfiguration, ad-hoc, rogue APs)
- Integrity attacks (injection, bit-flipping, replay)
- Confidentiality attacks (eavesdropping, evil twin, honeypot, MITM)
- Availability attacks (deauth flood, jamming, power saving, TKIP exploit)
- Authentication attacks (PSK/LEAP/VPN cracking, KRACK, Wi-Jacking)
- Specialized attacks: wormhole, sinkhole, inter-chip privilege escalation

**Wireless Hacking Methodology (5 steps):**
1. Wi-Fi Discovery (passive/active footprinting, war-driving, WPS detection)
2. Wireless Traffic Analysis (monitor mode, Wireshark, CommView, spectrum analysis)
3. Launch of Wireless Attacks (hidden SSID detection, DoS, MITM, MAC spoofing, ARP poisoning, rogue AP/evil twin, KRACK, aLTER, Wi-Jacking, RFID cloning)
4. Wi-Fi Encryption Cracking (WPA/WPA2 offline/deauth/brute-force, WPA3 downgrade/side-channel, WPS with Reaver)
5. Wi-Fi Network Compromising

**Tools Covered:**
- Discovery: inSSIDer, Sparrow-wifi, Wash, WiFi Analyzer
- Sniffing: Wireshark, CommView, OmniPeek, Kismet
- Attack: Aircrack-ng suite, mdk3, Ettercap, Reaver, Fern, MANA Toolkit, KARMA, hostapd-wpe
- Cracking: hashcat, Dragonblood tools, iCopy-X
- Defense: WIPS (Cisco Adaptive, WatchGuard), RFProtect

**Countermeasures:**
- Use WPA3-SAE, disable transition mode, strong passwords, disable TKIP/WPS
- Regular firmware updates, reduce signal range, LAN segmentation
- Encrypt DNS queries, use DNSCrypt/DNSSEC, mutual authentication
- Deploy WIDS/WIPS, rogue AP detection, 802.1X with RADIUS
- VPN, HTTPS Everywhere, 2FA, personal firewalls


---

