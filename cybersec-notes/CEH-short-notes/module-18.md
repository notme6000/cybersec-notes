
---

# Module 18: IoT and OT Hacking

## Learning Objectives

- Explain IoT concepts
- Understand different IoT threats and attacks
- Describe the IoT hacking methodology
- Use different IoT hacking tools
- Apply countermeasures to protect devices from IoT attacks
- Use different IoT security tools
- Explain OT concepts
- Understand different OT threats and attacks
- Describe the OT hacking methodology and use different OT hacking tools
- Apply countermeasures to protect industrial facilities from OT attacks
- Use different OT security tools

---

## IoT Concepts and Attacks

### What is the IoT?

- **Internet of Things (IoT) / Internet of Everything (IoE):** Web-enabled computing devices with sensors, communication hardware, and processors for sensing, collecting, and sending data.
- **Key features:** Connectivity, sensors, AI, small devices, active engagement.

### How the IoT Works (4 primary systems)

1.  **IoT Devices:** Sensors embedded in devices (temperature, gases, location, health data, etc.)
2.  **IoT Gateways:** Bridge between IoT device (internal network) and end-user (external network).
3.  **Cloud Server/Data Storage:** Stores and analyzes collected data.
4.  **Remote Control using Mobile App:** End-users monitor, control, and retrieve data remotely.

### IoT Architecture (Layers from top to bottom)

| Layer | Function |
|-------|----------|
| **Application Layer** | Delivers services to users (building, industrial, healthcare, security, etc.) |
| **Middleware Layer** | Data management, device management, data analysis, filtering, access control |
| **Internet Layer** | Communication between endpoints (device-to-device, device-to-cloud, device-to-gateway) |
| **Access Gateway Layer** | Message routing, identification, subscribing; initial data handling |
| **Edge Technology Layer** | Hardware components (sensors, RFID tags, readers); data collection |

### IoT Application Areas and Devices

- Buildings: HVAC, lighting, security, fire safety
- Energy: Turbines, windmills, UPS, generators, meters, pipelines
- Consumer/Home: Digital cameras, dishwashers, lights, TVs, alarms
- Healthcare: MRI machines, implants, surgical equipment, telemedicine
- Transportation: Vehicles, lights, ships, planes, traffic management
- Industrial: Pumps, valves, conveyors, fabrication, assembly
- Retail: POS terminals, vending machines, signs
- Security/Public Safety: Tanks, fighter jets, surveillance, weapons
- IT and Networks: Servers, storage, PCs, routers, switches

### IoT Technologies and Protocols

#### Short-Range Wireless Communication

| Technology | Description |
|------------|-------------|
| **Bluetooth Low Energy (BLE)** | Wireless PAN for healthcare, security, fitness |
| **Li-Fi** | Visible Light Communications using light bulbs; speed up to 224 Gbps |
| **NFC** | Magnetic field induction; contactless mobile payment, social networking |
| **QR Codes/Barcodes** | Machine-readable tags (1D/2D) |
| **RFID** | Electromagnetic fields to read tags; industrial, automotive, livestock |
| **Thread** | IPv6-based; home automation |
| **Wi-Fi (802.11n)** | 600 Mbps, range ~50 m |
| **Wi-Fi Direct** | Peer-to-peer without access point |
| **Z-Wave** | Low-power; home automation (HVAC, thermostats, garages) |
| **ZigBee (IEEE 203.15.4)** | Low data rate, 10-100 m range |
| **ANT** | Multicast wireless sensor; sports/fitness |

#### Medium-Range Wireless Communication

| Technology | Description |
|------------|-------------|
| **HaLow** | Extended range Wi-Fi; low data rate, low power |
| **LTE-Advanced** | Higher capacity, extended range |
| **6LoWPAN** | IPv6 over Low-Power WPAN; limited processing capacity |
| **QUIC** | Multiplexed over UDP; security equivalent to SSL/TLS |

#### Long-Range Wireless Communication

| Technology | Description |
|------------|-------------|
| **LPWAN** | Long-range communications |
| **LoRaWAN** | Mobile, industrial M2M, smart cities, healthcare |
| **Sigfox** | Short battery life, limited data |
| **Neu** | TV white space spectrum; high-quality, low-cost |
| **VSAT** | Small dish antennas; broadband/narrowband |
| **Cellular** | Longer distance, high-quality data; expensive, high power |
| **MQTT** | ISO standard lightweight protocol; remote locations, satellite |
| **NB-IoT** | Enhanced physical layer; M2M communication |

#### Wired Communication

| Technology | Description |
|------------|-------------|
| **Ethernet** | LAN; wired connection |
| **MoCA** | High-definition videos over coaxial cables |
| **PLC** | Electrical wires for power and data; home automation, industrial |

### IoT Operating Systems

- Windows 10 IoT, Amazon FreeRTOS, Fuchsia, RIOT, Ubuntu Core, ARM Mbed OS, Zephyr, Embedded Linux, NuttX RTOS, Integrity RTOS, Apache Mynewt, Tizen

### IoT Application Protocols

- **CoAP:** Web transfer protocol for M2M (building automation, smart energy)
- **Edge Computing:** Moves computation to network edge
- **LWM2M:** Application-layer for IoT device management
- **Physical Web:** BLE beacons broadcast URLs for nearby devices
- **XMPP:** Real-time communication for interoperable devices
- **Mihini/M3DA:** Communication between M2M server and embedded gateway

### IoT Communication Models

| Model | Description |
|-------|-------------|
| **Device-to-Device** | Interconnected devices use ZigBee, Z-Wave, Bluetooth (smart home, wearables) |
| **Device-to-Cloud** | Devices communicate directly with cloud using Wi-Fi, Ethernet, Cellular (CCTV cameras) |
| **Device-to-Gateway** | Devices communicate via gateway (smartphone/hub); ZigBee, Z-Wave |
| **Back-End Data-Sharing** | Extends device-to-cloud; authorized third parties access data (energy consumption analysis) |

### Challenges of IoT

- Lack of security and privacy
- Vulnerable web interfaces
- Default, weak, and hardcoded credentials
- Clear text protocols and unnecessary open ports
- Coding errors (buffer overflow)
- Storage issues
- Difficult-to-update firmware and OS
- Interoperability standard issues
- Physical theft and tampering
- Lack of vendor support
- Scalability, power consumption, regulatory compliance
- Integration with legacy systems

### Threat vs Opportunity

- **If misconfigured:** Unprecedented risk to personal data, privacy, safety
- **If protected:** Boosts transmissions, communications, service delivery, standard of living

**Three threat categories:** Security, Privacy, Safety (interrelated)

### IoT Security Problems (Per Layer)

- Edge Technology Layer: Physical security, device tampering
- Access Gateway Layer: Insecure communication, weak authentication
- Internet Layer: Lack of encryption, protocol vulnerabilities
- Middleware Layer: Data leakage, access control issues
- Application Layer: Insecure APIs, poor input validation

---

## OWASP Top 10 IoT Threats

| # | Threat | Description |
|---|--------|-------------|
| 1 | **Weak, Guessable, or Hardcoded Passwords** | Brute-forcing, backdoors, unauthorized access |
| 2 | **Insecure Network Services** | Buffer overflow, DoS, open ports exploited |
| 3 | **Insecure Ecosystem Interfaces** | Web, backend API, mobile, cloud interfaces lack auth/encryption/filtering |
| 4 | **Lack of Secure Update Mechanisms** | No firmware validation, no anti-rollback, insecure delivery |
| 5 | **Use of Insecure or Outdated Components** | Outdated software, compromised supply chain |
| 6 | **Insufficient Privacy Protection** | User personal information compromised |
| 7 | **Insecure Data Transfer and Storage** | No encryption/access control for data in transit/at rest |
| 8 | **Lack of Device Management** | No asset management, update management, secure decommissioning |
| 9 | **Insecure Default Settings** | Operators cannot modify configurations |
| 10 | **Lack of Physical Hardening** | Attackers acquire sensitive information via physical access |

### OWASP IoT Attack Surface Areas (Partial List)

| Attack Surface | Vulnerabilities |
|----------------|----------------|
| **Ecosystem (General)** | Interoperability standards, data governance, implicit trust, enrollment security |
| **Device Memory** | Cleartext usernames/passwords, third-party credentials, encryption keys |
| **Device Physical Interfaces** | Firmware extraction, privilege escalation, debug ports (UART, JTAG), reset to insecure state |
| **Device Web Interface** | OWASP Web Top 10, username enumeration, weak passwords, default credentials |
| **Device Firmware** | Backdoor accounts, hardcoded credentials, encryption keys, firmware downgrade |
| **Device Network Services** | Information disclosure, DoS, buffer overflow, UPnP, replay attack |
| **Local Data Storage** | Unencrypted data, static encryption keys, lack of integrity checks |
| **Update Mechanism** | Updates without encryption/signing, malicious update, missing mechanism |
| **Mobile Application** | Insecure data storage, weak passwords, lack of 2FA |
| **Network Traffic** | LAN, WLAN (Wi-Fi, Z-wave, Zigbee, Bluetooth, LoRa), protocol fuzzing |

### IoT Vulnerabilities (OWASP)

| Vulnerability | Attack Surface |
|---------------|----------------|
| Username Enumeration | Admin/Device/Cloud Interface, Mobile App |
| Weak Passwords | Admin/Device/Cloud Interface, Mobile App |
| Account Lockout | Admin/Device/Cloud Interface, Mobile App |
| Unencrypted Services | Device Network Services |
| Lack of 2FA | Admin/Cloud Interface, Mobile App |
| Poorly Implemented Encryption | Device Network Services (e.g., SSLv2) |
| Update Sent Without Encryption | Update Mechanism |
| Denial of Service | Device Network Services |
| Removal of Storage Media | Device Physical Interfaces |
| No Manual Update Mechanism | Update Mechanism |
| Firmware Version Not Displayed | Device Firmware |
| Firmware/Storage Extraction | JTAG/SWD, OTA, manufacturer website, eMMC tapping |
| Manipulating Code Execution | JTAG, side-channel attacks (glitching) |
| Obtaining Console Access | Serial interfaces (SPI/UART) |
| Insecure Third-Party Components | Outdated BusyBox, OpenSSL, SSH, web servers |

---

## IoT Threats (Specific Attacks)

| Attack | Description |
|--------|-------------|
| **DDoS** | Botnet army targets server, making it unavailable |
| **Attack on HVAC Systems** | Steal credentials via HVAC vulnerabilities |
| **Rolling Code Attack** | Jam and sniff rolling code (key fob) → unlock vehicle |
| **BlueBorne Attack** | Exploit Bluetooth vulnerabilities; no user interaction; RCE, MITM |
| **Jamming Attack** | Transmit random signals on same frequency → DoS |
| **Remote Access using Backdoor** | Exploit vulnerabilities to create backdoor |
| **Remote Access using Telnet** | Exploit open telnet port (default credentials/brute-force) |
| **Sybil Attack** | Multiple forged identities create traffic congestion illusion (VANETs) |
| **Exploit Kits** | Malicious script exploits poorly patched vulnerabilities |
| **MITM Attack** | Attacker pretends to be legitimate sender, hijacks communication |
| **Replay Attack** | Intercept legitimate messages, resend to cause DoS or crash |
| **Forged Malicious Device** | Replace authentic device with malicious device (physical access) |
| **Side-Channel Attack** | Extract encryption keys via signal emissions (power, timing) |
| **Ransomware Attack** | Encrypts user's files or locks screen; demands ransom |
| **Client Impersonation** | Masquerade as legitimate smart device/server |
| **SQL Injection** | Exploit mobile/web app vulnerabilities controlling IoT devices |
| **SDR-Based Attack** | Examine communication signals, send spam messages |
| **Fault Injection Attack** | Inject faulty program to compromise security (invasive/non-invasive) |
| **Network Pivoting** | Use malicious smart device to gain access to closed server |
| **DNS Rebinding Attack** | Malicious JavaScript on web page accesses victim's router |

### DDoS Attack on IoT (Steps)

1.  Attacker gains remote access to vulnerable devices.
2.  Injects malware to turn them into botnets.
3.  Uses C&C center to instruct botnets to send multiple requests to target server.
4.  Target server goes offline.

### Exploit HVAC (Steps)

1.  Attacker uses Shodan to search for vulnerable ICSs.
2.  Searches for default user credentials (defpass.com).
3.  Uses default credentials to access ICS.
4.  Gains access to HVAC system remotely.
5.  Controls temperature or carries out other attacks.

### Rolling Code Attack (Steps)

1.  Victim presses car remote button.
2.  Attacker uses jammer to jam reception and sniff first code.
3.  Car does not unlock; victim tries again (sends second code).
4.  Attacker sniffs second code.
5.  Attacker forwards first code → car unlocks.
6.  Attacker uses second code later to unlock and steal vehicle.
- **Tools:** HackRF One, RFCrack

### BlueBorne Attack (Steps)

1.  Attacker discovers active Bluetooth-enabled devices (even non-discoverable).
2.  Obtains MAC address.
3.  Sends probes to determine OS.
4.  Exploits Bluetooth protocol vulnerabilities → gain access.
5.  Performs RCE or MITM; takes full control.
- **Compatible with:** Android, Linux, Windows, older iOS
- **No user interaction required; only Bluetooth active.**

### Jamming Attack

- Attacker transmits random radio signals at same frequency as target device.
- Network gets jammed; endpoints cannot send/receive messages.
- **Result:** DoS.

### Hacking Smart Grid/Industrial Devices: Remote Access using Backdoor (Steps)

1.  Attacker gathers employee email IDs via social engineering.
2.  Sends phishing email with malicious attachment (e.g., Word doc).
3.  Employee opens attachment → backdoor installed.
4.  Attacker gains access to private network.
5.  Accesses SCADA network that controls grid.
6.  Replaces legitimate firmware with malicious firmware.
7.  Disables power supply by sending malicious commands.

### SDR-Based Attacks on IoT

- **Software-Defined Radio (SDR):** Implements signal processing using software/firmware instead of hardware.
- **Replay Attack:** Capture command sequence, segregate (URH), inject on same frequency.
- **Cryptanalysis Attack:** Reverse-engineer protocol to obtain original signal.
- **Reconnaissance Attack:** Obtain device specifications (chipset identification, product ID comparison).

### Identifying and Accessing Local IoT Devices

**Discovery Steps:**
1.  Attacker obtains local IP address (via malicious JS code).
2.  Requests all available devices in network.
3.  Active devices respond with reset packet; inactive devices timeout.
4.  Attacker detects all available devices.

**DNS Rebinding Attack (Access):**
1.  Malicious code performs DNS rebinding using tools like Singularity of Origin.
2.  Attacker commands and controls local IoT devices.
3.  Extracts private information (UIDs, BSSIDs, geo-location).

### Fault Injection Attacks (Perturbation Attacks)

| Type | Description |
|------|-------------|
| **Optical, EMFI, BBI** | Inject faults via lasers, electromagnetic pulses, high-voltage pulses (target RNGs) |
| **Power/Clock/Reset Glitching** | Inject glitches into power supply or clock network; skip key instructions |
| **Frequency/Voltage Tampering** | Modify power supply level or alter clock frequency |
| **Temperature Attacks** | Alter operating temperature (non-nominal conditions) |

- **Invasive:** Chip surface must be visible.
- **Non-invasive:** Attacker must be very near chip.

### Other IoT Attacks (Summary)

| Attack | Description |
|--------|-------------|
| **Sybil Attack** | Multiple forged identities in VANETs; illusion of traffic congestion |
| **Exploit Kits** | Malicious script for poorly patched vulnerabilities; auto-updates with new exploits |
| **MITM** | Pretend to be legitimate sender; hijack communication |
| **Replay** | Intercept legitimate messages; resend to cause DoS or crash |
| **Forged Malicious Device** | Replace authentic device with malicious device (physical access) |
| **Side-Channel** | Extract encryption keys via power consumption or electromagnetic emanations |
| **Ransomware** | Encrypt files or lock screen; demand ransom (via phishing, malvertising) |

### IoT Attacks in Different Sectors (Examples)

| Sector | Attack | Consequence |
|--------|--------|-------------|
| Buildings | Access Control, MITM, DoS, Eavesdropping | Loss of confidentiality, privacy, availability |
| Energy/Industrial | Reconnaissance, DoS, Spear Phishing, Bluebugging | Loss of privacy, data confidentiality, availability |
| Consumer/Home | DoS, MITM, Skill Squatting, Formjacking | Loss of data availability, privacy |
| Healthcare | Signal-Jamming, DoS, Sinkhole, Sybil, Bluesnarfing | Loss of data availability, confidentiality |
| Transportation | Impersonation, Sybil, GPS Spoofing, DoS, Wormhole, Black Hole | Loss of privacy, confidentiality, data |
| IT and Networks | Brute Force, DoS | Loss of privacy, data confidentiality, availability |

### IoT Malware

- **KmsdBot (Kmsdx):** Targets IoT devices; Telnet scanning, SSH scanning, default credentials (telnet.txt). Supports broader CPU architectures.
- **IZ1H9 (Mirai-based):** Shell script downloader to bypass security; XOR decryption (key 0xBAADF00D); spreads via HTTP, SSH, Telnet (brute-force with ~100 weak username/password combos). Uses command codes for various DDoS attack methods (TCP SYN, TCP ACK, UDP, DNS amplification, etc.).
- **Other IoT malware:** WailingCrab, P2PInfect, NKAbuse, IoTroop, XorDdos.

---

## IoT Hacking Methodology

**Phases:**
1.  Information Gathering
2.  Vulnerability Scanning
3.  Launch Attacks
4.  Gain Remote Access
5.  Maintain Access

### Information Gathering

**Tools:** Shodan, Censys, FOFA, MultiPing, FCC ID Search, Wireshark, Suphacap, Cascoda Packet Sniffer

#### Shodan Search Filters

- `webcamxpx country: US` (webcams in US)
- `webcamxpx city: paris` (webcams in Paris)
- `webcamxpx geo:-50.81,201.80` (webcam at specific coordinates)
- **Additional filters:** `net:`, `os:`, `port:`, `before/after:`

#### MultiPing (Find IP address of IoT device)

- Add Address Range → Select router gateway IP → Number of addresses = 255 → OK
- Set ping interval to 1 second for faster discovery.

#### FCC ID Search

- Label on device has unique FCC ID (grantee ID + product ID).
- Search on `https://www.fcc.gov/oet/ea/fccid` → displays summary and details (cover letter, external/internal photos, test report, user manual).

#### Information Gathering through Sniffing (Web Camera Example)

```bash
nmap -p 80,81,8080,8081 <Target IP range>   # Identify IoT devices using insecure HTTP ports
airmon-ng start wlan0                        # Put wireless card in monitor mode
airodump-ng wlan0mon                         # Scan nearby wireless networks
airmon-ng start wlan0mon 11                  # Listen on target channel (e.g., 11)
# Launch Wireshark, select wlan0mon, start capturing
```

#### Cascoda Packet Sniffer (IEEE 802.15.4, Zigbee, Thread)

- Run `sniffer -w <channel_number>` in cmd.
- Wireshark captures IoT traffic.

**Other sniffers:** Suphacap (Z-Wave), IoT Inspector 2, ZBOSS Sniffer, tcpdump, Ubiqua Protocol Analyzer, Perytons Protocol Analyzers.

### Vulnerability Scanning

**Tools:** IoTSeeker, Genzai, Nmap, beSTORM, Metasploit, IoTsploit, IoTVAS, Enterprise IoT Security

#### IoTSeeker

- Discovers IoT devices using default credentials (HTTP/HTTPS services).
- Command: `./iotseeker <options>`

#### Genzai

- IoT security toolkit; scans dashboards (routers, cameras, HMIs) for default passwords and vulnerabilities.
- Command: `./genzai <target_host> - save scan.json`

#### Nmap Commands

```bash
nmap -n -Pn -sS -pT:0-65535 -v -A -oX <Name> <IP>                    # TCP scan
nmap -n -Pn -sSU -pT:0-65535,U:0-65535 -v -A -oX <Name> <IP>        # TCP+UDP scan
nmap -6 -n -Pn -sSU -pT:0-65535,U:0-65535 -v -A -oX <Name> <IP>     # IPv6 scan
```

#### beSTORM

- Smart fuzzer; detects buffer overflow vulnerabilities; black-box auditing; no source code needed.

### Analyzing Spectrum and IoT Traffic

#### Gqrx (SDR Spectrum Analysis)

- Hardware: FunCube dongle, Airspy, HackRF, RTL-SDR, USRP.
- Command: `gqrx` (GUI displays frequencies).
- Analyze temperature/humidity sensors, light switches, car keys, M-bus transmitters.

#### ONEEKY (IoT Traffic Analysis)

- Discovers IoT devices; analyzes network traffic; projects vulnerabilities in tables/graphs.
- Records and replays all information.

#### Universal Radio Hacker (URH) (SDR-Based Attacks)

- Investigates unknown wireless protocols.
- Functions: Identify hardware interfaces, demodulation, reverse engineering protocol fields, fuzzing, modulation (inject data back).

**Other SDR tools:** BladeRF, TempestSDR, HackRF One, GP-Simulator, Gqrx.

### Launch Attacks

#### Rolling Code Attack using RFCrack

```bash
python RFCrack.py -i                            # Live replay
python RFCrack.py -r -M MOD_2FSK -F 314350000   # Rolling code bypass
python RFCrack.py -j -F 314000000               # Jamming
python RFCrack.py -k                            # Scan common frequencies
python RFCrack.py -s -u ./captures/test.cap -F 315000000 -M MOD_ASK_OOK  # Send saved payload
```

#### Hacking Zigbee Devices with Open Sniffer

- Wireshark-based analyzer for IEEE 802.15.4, Zigbee, 6LoWPAN.
- Continuously emit packets → DoS attack.
- Send user-defined frames → replay attack.

#### BlueBorne Attack using HackRF One

- Hardware/software-defined radio (1MHz to 6GHz); half-duplex.
- Sniffs GSM to Z-wave; performs replay, fuzzing, jamming.

#### Replay Attack using HackRF One (Steps)

```bash
hackrf_transfer -r connector.raw -f [device frequency]   # Record signal
# Later: replay the recorded signal
```

#### SDR-Based Attacks using RTL-SDR and GNU Radio

**RTL-SDR hardware:** USB dongle (500 kHz to 1.75 GHz). Activities: GPS decoding, spectrum analysis, GSM sniffing, cordless phone scanning.

**GNU Radio tools:**
- `uhd_fft` (spectrum analyzer)
- `uhd_rx_cfile` (store wave samples)
- `uhd_rx_nogui` (listen to incoming signals)
- `uhd_siggen_gui` (create sine, square, noise signals)
- `gr_plot` (present recorded samples)

#### Side-Channel Attack using ChipWhisperer

- Open-source toolchain for power analysis and glitching attacks.
- Extracts cryptographic keys (AES, triple DES) via power analysis.
- **Components:** Capture Board (captures small signals), Target Board (processor for secure operation).
- **Techniques:** Cache attacks, timing attacks, power-monitoring, electromagnetic attacks, acoustic cryptanalysis, fault analysis.

### Identifying IoT Communication Buses and Interfaces

- **Buses/Interfaces:** UART, SPI, JTAG, I2C.
- **Tool:** BUS Auditor (16 independent channels CHO to CH15).

#### UART Identification (using EXPLIoT framework)

```bash
run busauditor.generic.uartscan -v 3.3 -p /dev/ttyACM0 -s 0 -e 1
```

#### JTAG Identification

- Pins: TMS, TCK, TDI, TDO, TRST (optional).
```bash
run busauditor.generic.jtagscan -v 3.3 -p /dev/ttyACM0 -s 0 -e 10
```

### NAND Glitching (Attaining Root Access)

1.  Connect UART-USB converter; run `minicom -D /dev/ttyUSB0 -w -C D-link_startup.txt` to get bootlogs.
2.  Short serial I/O pin of flash memory chip to ground to interrupt booting → loads backup loader.
3.  Run `printenv` to view bootargs.
4.  Run `setenv bootargs 'noinitrd console=ttyAMO,115200 rootfstype=ubifs ubi.mtd=5 root=ubi:rootfs rw gpm init=/bin/sh'`
5.  Run `nand read ${loadaddr} app-kernel 0x00400000 && bootm ${loadaddr}` → gain root access.

### Exploiting Cameras using CamOver

- Discloses network camera administrator passwords (CCTV, GoAhead, Netwave).
```bash
camover                                    # Initialize tool
camover -a <Camera IP>                     # Exploit single camera
camover -t --shodan <Shodan API Key>       # Exploit cameras via Shodan
```

### Gain Remote Access using Telnet

1.  Identify open telnet port (Shodan, Censys, port scanning).
2.  Check if authentication required.
3.  If not → direct unauthorized access.
4.  If yes → try default credentials (root/root, system/system) or brute-force.

### Maintain Access by Exploiting Firmware (Firmware Mod Kit)

**Primary scripts:**
- `extract-firmware.sh` (extracts firmware image)
- `build-firmware.sh` (rebuilds firmware)

**Secondary scripts:**
- `ddwrt-gui-extract.sh` (extracts Web GUI files)
- `ddwrt-gui-rebuild.sh` (restores modified Web GUI files)

**Process:**
1.  Extract firmware image.
2.  Make desired modifications (file system or web UI).
3.  Rebuild firmware.
4.  Flash modified firmware onto device (may brick it).

### Firmware Analysis and Reverse Engineering (Steps)

1.  **Obtain Firmware:** Extract from device.
2.  **Analyze Firmware:**
    - `file *.bin`, verify MD5 signature, `cat *.md5`, `md5sum *.bin`
    - `strings -n 10 xyz.bin > strings.out`
    - `hexdump -C -n 512 xyz.bin > hexdump.out` (identify firmware build type)
3.  **Extract Filesystem:**
    - `binwalk xyz.bin` (identify file system type)
    - `dd if=xyz.bin bs=1 skip=922460 count=2522318 of=xyz.squashfs`
4.  **Mount Filesystem:**
    - `mkdir rootfs`
    - `sudo mount -t ext2 {filename} rootfs`
5.  **Analyze Filesystem Content:**
    - Check `etc/passwd`, `etc/shadow`, `etc/ssl`
    - `grep -rnw '/path/to/somewhere/' -e "password"`
    - `find . -name '*.conf'`, `*.pem`, `*.crt`, `*.cfg`, `.sh`, `.bin`
    - Run Firmwalker script.
6.  **Emulate Firmware for Dynamic Testing:** QEMU, Firmware Analysis Toolkit.

**CPU architecture detection:** `file` or `readelf`
**User-mode emulation:** `qemu-mipsel -L <prefix> <binary>`

### IoT Hacking Tools (Additional)

- CatSniffer (passively monitor IoT traffic)
- KillerBee (Zigbee attacks)
- JTAGULATOR, wiz_exploit, PENIOT, RouterSploit

---

## IoT Attack Countermeasures

### How to Defend Against IoT Hacking

- Disable guest/demo user accounts; use "Lock Out" feature.
- Implement strong authentication, end-to-end encryption (PKI), VPN.
- Locate control systems behind firewalls; isolate from business network.
- Use IPS/IDS, allow only trusted IP addresses.
- Disable telnet (port 23), disable UPnP port on routers.
- Protect against physical tampering; patch firmware regularly.
- Monitor port 48101 (malware propagation).
- Use CAPTCHA and account lockout to avoid brute-force.
- Isolate IoT devices on protected networks; implement secure boot (cryptographic code signing).
- Use TEE, TrustZone, SAM, TPM, HSM for secure key storage.
- Disable WebRTC to prevent IP disclosure; use ad-blockers.
- Use dnswall to filter private IP addresses from DNS replies (prevent DNS rebinding).
- Use cloud-based anti-DDoS, CDNs, smart DNS resolution.
- Change default router settings; do not use public Wi-Fi for management.
- Use centralized device management systems (monitor, update, configure).
- Adopt zero-trust security model; deploy RASP solutions.
- Use blockchain for tamper-proof audit trails.
- Run IoT apps in isolated containers/sandboxes.

### How to Prevent SDR-Based Attacks

- **Secure the signal:** Standard encryption methods.
- **Avoid command repetition:** Rolling window scheme (commands not reused).
- **Synchronization and preamble nibbles:** Segregate command sequence.
- **Anti-jamming techniques:** Detect and mitigate interference.
- **Frequency hopping (FHSS):** Rapidly switch between frequencies.
- **Secure key management:** HSMs.
- **Secure OTA updates:** Cryptographic signatures and channels.

### General Guidelines for IoT Device Manufacturers

- Use SSL/TLS, mutual check on SSL certificates and CRL.
- Encourage strong passwords; no hardcoded credentials; store separately in trusted storage.
- Simple, secure update process with chain of trust.
- Account lockout mechanism.
- Secure boot chain, whitelisting for trusted tools/apps.
- Use safe functions (`gets()`, `fgets()`) to reduce buffer overflow risk.
- Incorporate security into IoT SDLC.
- Provide transparency about security features; clear contact for researchers.
- Use secure communication protocols (MQTT, CoAP, HTTPS).
- Integrate hardware-based security (TPM, secure elements).

### OWASP Top 10 IoT Vulnerabilities Solutions

| Vulnerability | Solutions |
|---------------|-----------|
| Weak/Guessable/Hardcoded Passwords | Use APM, strong passwords, avoid hardcoded |
| Insecure Network Services | Close open ports, disable UPnP, encrypt data |
| Insecure Ecosystem Interfaces | Account lockout, periodic assessment, input filtering, 2FA |
| Lack of Secure Update Mechanism | Verify source/integrity, encrypt communication, notify users |
| Use of Insecure/Outdated Components | Monitor for unmaintained components, remove unused dependencies |
| Insufficient Privacy Protection | Minimize data collection, anonymize, user control over data |
| Insecure Data Transfer/Storage | Encrypt communication, maintain SSL/TLS, avoid proprietary encryption |
| Lack of Device Management | Blacklist malicious devices, validate asset attributes, secure decommissioning |
| Insecure Default Settings | Change default usernames/passwords, customize privacy/security settings |
| Lack of Physical Hardening | Unique BIOS/firmware password, configure boot order, minimize external ports |

### IoT Framework Security Considerations

| Component | Key Considerations |
|-----------|---------------------|
| **Edge** | Cross-platform, storage encryption, no default credentials, strong passwords |
| **Gateway** | Strong encryption, multi-directional authentication, automatic updates |
| **Cloud Platform** | Encrypted communications, strong authentication, secure web interface, encrypted storage |
| **Mobile** | Proper authentication, account lockout, local storage security, encrypted communication |

### IoT Hardware Security Best Practices

- Limit entry points (USB ports, unused ports).
- Hardware tamper protection mechanism (GPS, lid removal detection).
- Monitor secure booting (prevent glitching).
- Implement security patches (timely, secure firmware updates).
- Maintain proper interface management (avoid API/library snatching).
- Avoid open access to hardware unit (physical protection).
- Secure authentication keys (unique device ID).
- Maintain event logging mechanism (timely audits).
- Anti-malware protection.
- Isolate devices from regular supply units (prevent rowhammer attacks).
- Root-on-trust mechanism.
- Secure legacy units with modern gateways.
- Secure wireless communication (encryption, authentication, access control).
- Disable/secure debug interfaces (JTAG, UART).
- Hardware-based root of trust (TEE, secure enclaves).
- Hardware-based intrusion detection.

**TPM Countermeasures:**
- Use Bitlocker for data import authentication.
- Use TPM bind key (RSA encryption) for data binding.
- Sealing/unsealing for firmware updates/security patches.
- HMAC-key-based secure communication.
- RSA-based encryption with digital signature.
- Root-of-trust models (RTM, RTV).

### Secure Development Practices for IoT Applications

- Ensure secure boot (authenticated/validated code).
- Secure API endpoints (authentication, data validation).
- Implement threat modeling.
- Secure coding practices (prevent buffer overflows, injection attacks, XSS).
- Security testing (penetration testing, vulnerability scanning, code reviews).
- Secure OTA updates (tamper-proof).
- Device identity management (unique identifiers, digital certificates).
- Hardware security (TPM, HSM, secure elements).
- Code signing (authenticity/integrity).
- Runtime protection (code execution monitoring, stack overflow protection).
- Secure cloud integration (authentication, access control, encryption).
- Secure communication protocols (MQTT with TLS/SSL).

### IoT Device Management

- **Purpose:** Track, monitor, manage physical IoT devices from remote location.
- **Capabilities:** Remote firmware updates, permissions, security enhancement.
- **Features:** Proper authentication, accurate configuration, monitoring, secure maintenance.
- **Solutions:** Azure IoT Central, Oracle Fusion Cloud IoT, Predix, Golioth, AWS IoT Device Management, IBM Watson IoT Platform, openBalena.

### IoT Security Tools

- **SeaCat.io:** Security-first SaaS; manage connected products, remote access, malware prevention, botnet protection.
- **Armis Centrix™:** View, protect, manage, optimize IoT assets; signature-based attack detection, IOC, forensic data.
- **Other tools:** FortiNAC, Microsoft Defender for IoT, Symantec Critical System Protection, Cisco Industrial Threat Defense, AWS IoT Device Defender, Forescout, NSFOCUS Anti-DDoS, Azure Sphere, Overwatch, Barbara, Sternum, Asimily, ByteSweep, Entrust IoT Security.

---

## OT Concepts and Attacks

### What is OT?

- **Operational Technology (OT):** Software and hardware to detect or cause changes in industrial operations via direct monitoring/controlling of physical devices (switches, pumps, lights, sensors, elevators, robots, valves, HVAC).
- **Components:** Industrial Control Systems (ICS) including SCADA, RTU, PLC, DCS, and other dedicated network systems.

### Essential Terminology

| Term | Description |
|------|-------------|
| **Assets** | Physical (sensors, actuators, PLCs) and logical (program logic, database, firewall rules) components |
| **Zones and Conduits** | Network segregation technique for access control |
| **Industrial Network** | Collection of automated control systems to achieve business objective |
| **Business Network** | Information infrastructure for the business |
| **Industrial Protocols** | Proprietary (S7, CDA, SRTP) or non-proprietary (Modbus, OPC, DNP3, CIP) |
| **Network Perimeter** | Outermost boundary of a network zone |
| **Critical Infrastructure** | Systems whose failure severely impacts security, safety, economy, or public health |

### Introduction to ICS

- **Industrial Control System (ICS):** Controls and supports industrial processes (production, manufacturing, distribution).
- **Components:** Sensors, controllers, actuators (mechanical, electrical, hydraulic, pneumatic).
- **Control Modes:**
    - **Open Loop:** Output depends on preconfigured settings.
    - **Closed Loop:** Output affects input to acquire desired objective.
    - **Manual Loop:** System under human control.

### Components of an ICS

#### Distributed Control System (DCS)

- Controls production systems within same geographical location (chemical plants, nuclear plants, oil refineries, water treatment, electric power).
- Centralized supervisory control unit controls multiple local controllers.
- High redundancy; scalable; includes wireless systems, remote transmission, embedded web servers.

#### Supervisory Control and Data Acquisition (SCADA)

- Centralized supervisory control for industrial facilities and infrastructure (oil/gas transport, wastewater, power grids, building automation).
- Hardware: Control server (SCADA-MTU), communication devices, field sites (PLCs, RTUs).
- Software: HMI, data historian.
- Fault-tolerant with redundant systems.

#### Programmable Logic Controller (PLC)

- Real-time digital computer for industrial automation (steel, automobile, energy, chemical, glass, paper, cement).
- **Modules:**
    - **CPU Module:** Processor + memory (RAM for user programs, ROM for OS/drivers).
    - **Power Supply Module:** Converts AC to DC (5V for computer circuitry, 24V for sensors/actuators).
    - **I/O Modules:** Digital (ON/OFF), Analog (ADC), Communication (remote CPU).

#### Basic Process Control System (BPCS)

- Performs process control and monitoring; first layer of protection against unsafe conditions.
- Functions: Trending, alarm/event logging, HMI, production reports, batch management, safety interlocks.

#### Safety Instrumented Systems (SIS)

- Automated control system to safeguard against hazardous incidents; overrides BPCS.
- Brings system to predefined safe state (shutdown).
- **Components:** Sensors (measure parameters), Logic solvers (determine actions), Final control elements (implement actions).
- Assessed via HAZOP, LOPA, risk graphs.

### IT/OT Convergence (IIOT)

- **IT/OT Convergence:** Integration of IT computing systems and OT operation monitoring systems.
- **Industrial Internet of Things (IIoT):** Using IoT for industrial operations (supply chain, manufacturing, management).
- **Benefits:** Enhanced decision making, automation, expedited business output, minimized expenses, mitigated risks, increased agility, predictive maintenance, better quality control, compliance/reporting, scalability.

### The Purdue Model (Industrial Automation and Control System Reference Model)

| Zone | Level | Description |
|------|-------|-------------|
| **Enterprise Zone (IT)** | Level 5 | Enterprise Network (B2B, B2C, internet connectivity) |
| | Level 4 | Business Logistics Systems (SAP, ERP, file/database servers, email) |
| **Industrial Demilitarized Zone (IDMZ)** | | Barrier between OT and IT (domain controllers, database replication servers, proxy servers) |
| **Manufacturing Zone (OT)** | Level 3 | Operational Systems/Site Operations (MES/MOMS, data historians, batch management, quality assurance) |
| | Level 2 | Control Systems/Area Supervisory Controls (DCS, SCADA, HMI, engineering workstations) |
| | Level 1 | Basic Controls/Intelligent Devices (PLCs, RTUs, IEDs, PID controllers, VFDs) |
| | Level 0 | Physical Process (sensors, actuators, industrial equipment) |

### OT Technologies and Protocols (Over Purdue Model)

| Level | Protocols |
|-------|------------|
| **Level 5** | ISA/IEC 62443 |
| **Level 4** | Modbus, NTP, Profinet, SuiteLink, Tase-2, ControlNet, Profibus PA/DP |
| **Level 3** | 6LoWPAN, DNP3, DNS/DNSSEC, FTE, HART-IP, IEC 60870-5-101/104, SOAP, DeviceNet, AS-Interface |
| **Levels 0/1** | BACnet, EtherCAT, CANopen, Crimson, DeviceNet, Zigbee, ISA SP100, MELSEC-Q, Niagara Fox, Omron Fins, PCWorx, Profibus, Sercos II, S7 Communication, WiMax, FOUNDATION Fieldbus |

### Challenges of OT

- Lack of visibility, plain-text passwords, network complexity, legacy technology.
- Lack of antivirus protection, lack of skilled professionals, rapid pace of change.
- Outdated systems, haphazard modernization, insecure connections (public Wi-Fi, unencrypted).
- Rogue devices, convergence with IT (malware, malicious insiders).
- Organizational challenges, proprietary software, vulnerable communication protocols (Modbus, Profinet lack security features).
- Remote management protocols (RDP, VNC, SSH) can be exploited.
- Insufficient segmentation, physical security issues, vendor dependencies.
- Resource constraints, lack of encryption, data integrity issues.

### OT Vulnerabilities

| Vulnerability | Description |
|---------------|-------------|
| Publicly Accessible OT Systems | Direct Internet connection for remote maintenance; no modern security controls |
| Insecure Remote Connections | Exploit vulnerabilities in jump boxes to gain remote access |
| Missing Security Updates | Outdated software versions increase risk |
| Weak Passwords | Default vendor credentials not changed |
| Insecure Firewall Configuration | Misconfigured access rules between IT and OT |
| OT Systems in Corporate IT Network | Compromised IT system can gain access to OT |
| Insufficient Security for IT from OT | Insecure OT devices can compromise IT systems |
| Lack of Segmentation within OT | Flat network; compromise of one device exposes entire OT network |
| Lack of Encryption/Authentication for Wireless OT | Sniffing and authentication bypass |
| Unrestricted Outbound Internet Access | Malware and C&C attacks |

### MITRE ATT&CK for ICS (Tactics - Partial)

| Tactic | Description |
|--------|-------------|
| **Initial Access** | Drive-by compromise, exploit public-facing application, remote services, removable media |
| **Execution** | Change operating mode, CLI, APIs, GUI, modify controller tasking, user execution |
| **Persistence** | Modify program, module firmware, project file infection, system firmware, valid accounts |
| **Privilege Escalation** | Exploit software, hooking |
| **Evasion** | Remove indicators, rootkits, change operator mode, masquerading, spoofed reporting |
| **Discovery** | Enumerate network connection, network sniffing, identify remote systems, wireless sniffing |
| **Lateral Movement** | Default credentials, program download, remote services, lateral tool transfer |
| **Collection** | Automated collection, information repositories, I/O image, MITM, screen capture |
| **Command and Control** | Frequently used ports (80,443), connection proxy, standard application-layer protocols (HTTPS, Telnet, RDP) |
| **Inhibit Response Function** | Activate firmware update mode, block command/reporting messages, alarm suppression, DoS, device restart |
| **Impair Process Control** | I/O brute-forcing, alter parameters, module firmware, spoofed reporting |
| **Impact** | Damage to property, loss of availability, denial of control, loss of view, loss of productivity/revenue, manipulation of control/view |

### OT Threats

| Threat | Description |
|--------|-------------|
| **Maintenance/Admin Threat** | Exploit zero-day vulnerabilities to inject malware into IT systems, target SCADA/PLC |
| **Data Leakage** | Exploit IT systems connected to OT to steal configuration files |
| **Protocol Abuse** | Exploit legacy protocols (Modbus, CAN bus); e-stop abuse for single-packet attacks |
| **Destruction of ICS Resources** | Disrupt/degrade OT infrastructure |
| **Reconnaissance Attacks** | Minimal/no encryption or authentication allows initial scanning |
| **DoS Attacks** | Exploit CIP protocol; malicious connection request, fake IP configuration |
| **HMI-Based Attacks** | Memory corruption, code injection, privilege escalation |
| **Exploiting Enterprise Systems** | Target SIS via underlying protocols |
| **Spear Phishing** | Fake emails with malicious links/attachments |
| **Malware Attacks** | Reuse legacy malware or develop new ICS/SCADA malware |
| **Unpatched Vulnerabilities** | ICS vendors cannot patch as quickly as IT vendors |
| **Side-Channel Attacks** | Timing analysis, power analysis |
| **Buffer Overflow Attack** | Exploit HMI web interface, ICS web client, communications interfaces |
| **Exploiting RF Remote Controllers** | Lack of built-in security; production sabotage, system control, unauthorized access |

### HMI-Based Attacks (SCADA Vulnerabilities)

| Vulnerability | Description |
|---------------|-------------|
| **Memory Corruption** | Out-of-bound read/write, heap/stack buffer overflow |
| **Credential Management** | Hardcoded passwords, cleartext credentials |
| **Lack of Authorization/Authentication** | Cleartext transmission, insecure defaults, insecure ActiveX controls |
| **Code Injection** | SQL, OS, command, Gamma script injection (EvalExpression vulnerability) |
| **Buffer Overflow** | Excessive data inputs overflow allocated buffer |
| **Path Traversal** | Access directories/files outside web-root folder |

### Side-Channel Attacks (on OT)

- **Timing Analysis:** Monitor time taken for password authentication to determine correct characters.
- **Power Analysis:** Observe change in power consumption during clock cycles; compare power profile of correct vs. wrong character to retrieve password or cryptographic key. Requires oscilloscope and special hardware.

### Hacking Programmable Logic Controller (PLC)

#### PLC Rootkit Attack (Ghost Attack)

1.  Attacker gains authorized access, performs control-flow attack to guess default password, gains root-level access.
2.  Maps input/output modules and their memory locations.
3.  Manipulates I/O initialization sequence → complete control over PLC operations.
- **Requires in-depth knowledge of PLC architecture.**
- CPU modes: Programming mode (download code), Run mode (execute actual code).

#### Evil PLC Attack

1.  Attacker identifies vulnerable PLC using Shodan/Censys.
2.  Exploits firmware, changes programming logic via download procedures.
3.  Infected PLC initiates upload procedures on connected workstations to execute arbitrary code.

### Hacking Industrial Systems through RF Remote Controllers

| Threat | Description |
|--------|-------------|
| **Replay Attack** | Record commands (RF packets) and replay them |
| **Command Injection** | Reverse-engineer RF protocols, alter packets, inject own commands |
| **Abusing E-stop** | Send multiple emergency stop commands → DoS |
| **Re-pairing with Malicious RF Controller** | Hijack original controller, pair with malicious RF controller |
| **Malicious Reprogramming Attack** | Inject malware into firmware of remote controllers → persistent remote access |

### OT Supply Chain Attacks

| Attack | Description |
|--------|-------------|
| **Third-Party Software Compromise** | Inject malicious code into trusted software updates |
| **Hardware Manipulation** | Alter components during manufacturing/distribution; embed malicious firmware |
| **Service Provider Breach** | Compromise maintenance/support contractors; stolen credentials, remote access |
| **Injection of Malicious Components** | Tamper during shipping; substitute legitimate parts with compromised ones |
| **Exploitation of Trusted Relationships** | Move laterally via suppliers, subcontractors, partners |

### OT Malware

#### Fuxnet

- Destructive ICS malware for OT environments.
- Rewrites NAND chip to disable external remote access.
- Exploits weak credentials to gain root access to sensor gateways.
- Uses fuzzing (malformed packets) to corrupt sensors.

#### COSMICENERGY

- OT/ICS malware designed to disrupt power via IEC 60870-5-104 (IEC-104) devices (RTUs).
- **Components:**
    - **PIEHOP (Python):** Connects to MSSQL server, uploads files, issues remote commands to RTU.
    - **LIGHTWORK (C++):** Crafts IEC-104 ASDU messages to change RTU information object addresses (IOAs) ON/OFF (affects power-line switches, circuit breakers).
- **Commands:** `C_IC_NA_1` (station interrogation), `C_SC_NA_1` (single command for each IOA), `C_CS_NA_1` (clock synchronization).
- **No lateral movement capability** (but internal reconnaissance required).

**Other OT malware:** Kapeka, Abyss Locker, AvosLocker, INDUSTROYER.V2, Pipedream.

---

## OT Hacking Methodology

### What is OT Hacking?

- **Objective:** Damage or disrupt business processes through industrial control systems.
- **Exposure vectors:** Remote sensors, Wi-Fi enabled controllers, USB devices, cloud services (SCADA-as-a-Service).

*(Note: The PDF did not contain detailed OT hacking methodology steps/tools in the provided pages. The content ended before detailing specific OT hacking tools and step-by-step attack procedures. The notes above cover OT concepts, threats, vulnerabilities, components, malware, and attack techniques.)*

---

## Module Summary

This module covered:

- IoT concepts, architecture, technologies, protocols, communication models, and challenges
- OWASP Top 10 IoT threats and attack surface areas
- IoT vulnerabilities and specific attacks (DDoS, HVAC, Rolling Code, BlueBorne, Jamming, SDR-based, Fault Injection, etc.)
- IoT hacking methodology (information gathering, vulnerability scanning, launching attacks, gaining/maintaining access)
- IoT hacking tools (Shodan, Censys, IoTSeeker, Genzai, Nmap, beSTORM, Gqrx, URH, RFCrack, Open Sniffer, HackRF One, RTL-SDR, GNU Radio, ChipWhisperer, BUS Auditor, CamOver, Firmware Mod Kit, etc.)
- IoT attack countermeasures, OWASP solutions, framework security considerations, hardware security best practices, secure development practices
- IoT device management and security tools (SeaCat.io, Armis Centrix, etc.)
- OT concepts (ICS, SCADA, DCS, PLC, BPCS, SIS, Purdue Model)
- OT technologies, protocols, challenges, vulnerabilities
- MITRE ATT&CK for ICS (12 tactics)
- OT threats (HMI-based attacks, side-channel attacks, PLC rootkit, Evil PLC, RF remote controller attacks, supply chain attacks)
- OT malware (Fuxnet, COSMICENERGY)

**Next Module:** Likely continues with more advanced topics (not specified in provided PDF pages).

---

## Key Takeaways (Short)

1.  **IoT** connects physical devices (sensors, actuators) via gateways to cloud/mobile apps using various protocols (ZigBee, LoRa, MQTT, etc.).
2.  **OWASP Top 10 IoT threats** include weak passwords, insecure network services, insecure interfaces, lack of secure updates, and outdated components.
3.  **IoT hacking methodology:** Information gathering (Shodan), vulnerability scanning (IoTSeeker), launching attacks (rolling code, BlueBorne, jamming), gaining remote access (Telnet, backdoors), maintaining access (firmware modification).
4.  **SDR-based attacks** (replay, cryptanalysis, reconnaissance) exploit insecure wireless protocols; countermeasures include frequency hopping and encryption.
5.  **Hardware attacks:** Fault injection (glitching), side-channel (power/timing), NAND glitching, UART/JTAG identification.
6.  **OT** includes ICS, SCADA, DCS, PLC, SIS; operates at different Purdue Model levels (Level 0 physical process to Level 5 enterprise network).
7.  **OT challenges:** Legacy technology, lack of encryption/authentication, weak passwords, insecure remote connections, unpatched vulnerabilities.
8.  **MITRE ATT&CK for ICS** provides 12 tactics from Initial Access to Impact.
9.  **OT attacks:** PLC rootkit, Evil PLC, HMI-based attacks (memory corruption, code injection), side-channel attacks, RF remote controller attacks.
10. **OT malware:** Fuxnet (destroys gateways, corrupts sensors), COSMICENERGY (disrupts power via IEC-104 devices).

---

## Important Terms Summary

| Term | Definition |
|------|------------|
| **IoT** | Internet of Things; web-enabled devices with sensors |
| **IIoT** | Industrial Internet of Things; IoT for industrial operations |
| **OT** | Operational Technology; hardware/software for industrial process control |
| **ICS** | Industrial Control System; SCADA, DCS, PLC, RTU, IED |
| **SCADA** | Supervisory Control and Data Acquisition; centralized control over wide areas |
| **DCS** | Distributed Control System; localized process control |
| **PLC** | Programmable Logic Controller; real-time industrial automation |
| **SIS** | Safety Instrumented System; brings process to safe state |
| **Purdue Model** | Reference model for ICS network segmentation (Levels 0-5) |
| **IDMZ** | Industrial Demilitarized Zone; barrier between OT and IT |
| **MQTT** | Message Queuing Telemetry Transport; lightweight IoT protocol |
| **CoAP** | Constrained Application Protocol; M2M communication |
| **LoRaWAN** | Long Range Wide Area Network; LPWAN for IoT |
| **6LoWPAN** | IPv6 over Low-Power WPAN |
| **SDR** | Software-Defined Radio; radio communication via software |
| **URH** | Universal Radio Hacker; reverse-engineers wireless protocols |
| **NAND Glitching** | Shorting flash pin to interrupt boot and gain root access |
| **JTAG/UART** | Debug interfaces used to access device console |
| **RCE** | Remote Code Execution |
| **C&C** | Command and Control (server) |
| **E-stop** | Emergency stop (safety mechanism) |
| **IOA** | Information Object Address (in IEC-104) |

**End of Notes**
