# CEHv13 - Module 02: Footprinting and Reconnaissance - Complete Study Notes

---

## Table of Contents

1. Footprinting Concepts
2. Footprinting through Search Engines
3. Footprinting through Internet Research Services
4. Footprinting through Social Networking Sites
5. Whois Footprinting
6. DNS Footprinting
7. Network and Email Footprinting
8. Footprinting through Social Engineering
9. Footprinting Tools
10. AI-Powered OSINT Tools
11. Footprinting Countermeasures
12. Module Summary

---

# PART 1: FOOTPRINTING CONCEPTS

## 1.1 Introduction to Reconnaissance

### Definition

Reconnaissance (also known as footprinting) refers to the preparatory phase where an attacker seeks to gather as much information as possible about a target of evaluation prior to launching an attack. It is the first step in ethical hacking and refers to the process of collecting information about a target network and its environment.

### Importance of Footprinting

- Helps identify the level of risk associated with the organization's publicly accessible information
- Provides opportunities to penetrate and assess the target organization's network
- Creates a "blueprint" of the security profile of the target organization
- Uncover vulnerabilities existing in the target network
- Identify different ways of exploiting these vulnerabilities

### What is the Blueprint?

The term "blueprint" refers to the unique system profile of the target organization acquired by footprinting. After completing the footprinting process in a methodological manner, you obtain the blueprint of the security profile of the target organization.

### Key Points About Footprinting

- There is no single methodology for footprinting
- Information can be traced in multiple ways
- Activity is important as you need to gather crucial information before beginning the hacking phase
- Footprinting needs to be carried out in an organized manner

---

## 1.2 Types of Reconnaissance

### 1.2.1 Passive Footprinting

**Definition:** Passive footprinting involves gathering information about the target without direct interaction.

**Characteristics:**
- Mainly useful when information gathering activities should not be detected by the target
- Technically difficult
- No active traffic is sent to the target organization
- Only archived and stored information is collected

**Methods:**
- Open-source Intelligence (OSINT) gathering
- Proprietary databases and paid services
- Sharing intelligence with partner organizations or industry groups

**Sources:**
- Search engines
- Social networking sites
- Public records
- News articles
- Press releases

---

### 1.2.2 Active Footprinting

**Definition:** Active footprinting involves gathering information about the target with direct interaction.

**Characteristics:**
- Target may recognize the ongoing information gathering process
- Requires more preparation than passive footprinting
- May leave traces that could alert the target organization

**Methods:**
- DNS interrogation
- Social engineering
- Network/port scanning
- User and service enumeration

**Difference Between Passive and Active:**

| Aspect | Passive | Active |
|--------|---------|--------|
| Interaction | No direct interaction | Direct interaction with target |
| Detection | Not detectable | May be detected |
| Preparation | Less preparation | More preparation required |
| Risk Level | Lower risk | Higher risk |
| Information Type | Archived/stored information | Current information |

---

## 1.3 Information Obtained in Footprinting

### 1.3.1 Organization Information

**Sources:**
- Company website
- Whois database queries
- News articles
- Press releases
- Legal documents

**Information Collected:**
- Employee details (names, contact addresses, designations, work experience)
- Addresses and mobile/telephone numbers
- Branch and location details
- Partners of the organization
- Web links to other company-related sites
- Background of the organization
- Web technologies used
- News articles, press releases, and related documents
- Legal documents related to the organization
- Patents and trademarks related to the organization

**Use by Attackers:**
- Identify key personnel
- Launch social engineering attacks
- Extract sensitive data about the entity

---

### 1.3.2 Network Information

**Sources:**
- Whois database analysis
- Trace routing
- DNS interrogation

**Information Collected:**
- Domain and sub-domains
- Network blocks
- Network topology
- Trusted routers and firewalls
- IP addresses of reachable systems
- Whois records
- DNS records and related information

---

### 1.3.3 System Information

**Sources:**
- Network footprinting
- DNS footprinting
- Website footprinting
- Email footprinting

**Information Collected:**
- Web server OS
- Location of web servers
- Publicly available email addresses
- Usernames and passwords

---

## 1.4 Objectives of Footprinting

### Primary Objectives

1. **Build a hacking strategy** - Gather information to identify easiest ways to break through security perimeter
2. **Identify security posture** - Placement of firewalls, proxies, and other security solutions
3. **Identify vulnerabilities** - Find loopholes in security posture to build hacking plan

### What Attackers Can Achieve

- Take an unknown entity and reduce it to specific range of domain names
- Identify network blocks
- Identify individual IP addresses of systems connected to Internet
- Build information database regarding security weaknesses
- Identify weakest link in organization's security perimeter

---

## 1.5 Footprinting Threats

### 1.5.1 Social Engineering
- Attackers directly and indirectly collect information through persuasion
- Gather crucial information from willing employees unaware of hackers' intent
- No intrusion methods required

### 1.5.2 System and Network Attacks
- Gather information about system configuration
- Identify operating system running on machines
- Find vulnerabilities in target system
- Exploit vulnerabilities to take control

### 1.5.3 Information Leakage
- Sensitive information falls into hands of attackers
- Mount attacks based on information
- Use information for monetary benefit

### 1.5.4 Privacy Loss
- Access systems and networks
- Escalate privileges up to admin levels
- Result in loss of privacy for organization and personnel

### 1.5.5 Corporate Espionage
- Competitors aim to acquire sensitive data
- Launch similar products in market
- Alter prices
- Undermine market position of target organization

### 1.5.6 Business Loss
- Major effect on online businesses
- Impact on e-commerce websites
- Banking and finance-related businesses
- Billions of dollars lost yearly

---

## 1.6 Footprinting Methodology

The footprinting methodology is a procedure for collecting information about a target organization from all available sources. It involves gathering information such as:

- URLs
- Locations
- Establishment details
- Number of employees
- Specific range of domain names
- Contact information

### Common Techniques for Information Collection

1. **Search Engines** - Google, Bing, Yahoo, Baidu, Yandex
2. **Social Networking Sites** - LinkedIn, Facebook, Twitter, Instagram
3. **Whois Databases** - ARIN, APNIC, RIPE, AFRINIC, LACNIC
4. **DNS Records** - A, MX, NS, CNAME, SOA, TXT
5. **Network Tools** - Traceroute, Ping, Port scanning
6. **Email Tracking** - Email headers, tracking tools
7. **Social Engineering** - Eavesdropping, shoulder surfing, dumpster diving

---

# PART 2: FOOTPRINTING THROUGH SEARCH ENGINES

## 2.1 Introduction to Search Engine Footprinting

### How Search Engines Work

1. Use automated software (crawlers) to continuously scan active websites
2. Add retrieved results to search engine index
3. Store results in massive database
4. When user queries, returns Search Engine Results Pages (SERPs)

### Types of Results Returned
- Web pages
- Videos
- Images
- Various file types

### Information Extractable from Search Engines
- Technology platforms
- Employee details
- Login pages
- Intranet portals
- Contact information

### Major Search Engines
- Google
- Bing
- Yahoo
- Ask
- Aol
- Baidu
- Yandex
- WolframAlpha
- DuckDuckGo

---

## 2.2 Advanced Google Hacking Techniques

### What is Google Hacking?

Google hacking refers to the use of advanced Google search operators for creating complex search queries to extract sensitive or hidden information. The accessed information is then used by attackers to find vulnerable targets.

### Syntax for Advanced Search Operators

```
operator: search_term
```

**Note:** Do not enter any spaces between the operator and the query.

### Popular Google Advanced Search Operators

| Search Operator | Purpose |
|-----------------|---------|
| `site:` | Restricts results to specified site or domain |
| `allinurl:` | Restricts results to pages containing all query terms in URL |
| `inurl:` | Restricts results to pages containing specified word in URL |
| `intext:` | Displays results containing specific keyword within body of webpage |
| `allintitle:` | Restricts results to pages containing all query terms in title |
| `intitle:` | Restricts results to pages containing specified term in title |
| `inanchor:` | Restricts results to pages containing query terms in anchor text |
| `allinanchor:` | Restricts results to pages containing all query terms in anchor text |
| `cache:` | Displays Google's cached version of a web page |
| `link:` | Searches websites or pages that contain links to specified website |
| `related:` | Displays websites similar or related to URL specified |
| `info:` | Finds information for specified web page |
| `location:` | Finds information for specific location |
| `filetype:` | Searches for results based on file extension |
| `source:` | Displays information from specific website in Google News |
| `phonebook:` | Finds residential and business phone numbers |
| `before:` | Filters results to content published before specified date |
| `after:` | Finds information published after certain date |

---

### Detailed Explanation of Key Operators

#### `site:` Operator
Restricts search results to the specified site or domain.

**Example:** `games site:www.certifiedhacker.com`
- Gives information on games from the certifiedhacker site

#### `allinurl:` Operator
Restricts results to only pages containing all query terms specified in the URL.

**Example:** `allinurl: google career`
- Returns only pages containing "google" and "career" in URL

#### `inurl:` Operator
Restricts results to only pages containing specified word in URL.

**Example:** `inurl: copy site:www.google.com`
- Returns Google pages where URL has word "copy"

#### `intext:` Operator
Displays results containing specific keyword within body of webpage.

**Example:** `intext:"vpn configuration"`
- Returns pages containing phrase "vpn configuration" in body text

#### `allintitle:` Operator
Restricts results to only pages containing all query terms specified in title.

**Example:** `allintitle: detect malware`
- Returns pages containing "detect" and "malware" in title

#### `intitle:` Operator
Restricts results to only pages containing specified term in title.

**Example:** `malware detection intitle:help`
- Returns pages with "help" in title and "malware" and "detection" anywhere in page

#### `inanchor:` Operator
Restricts results to pages containing query terms in anchor text on links to page.

**Example:** `Anti-virus inanchor:Norton`
- Returns pages with anchor text containing "Norton" and page containing "Anti-virus"

#### `allinanchor:` Operator
Restricts results to pages containing all query terms in anchor text.

**Example:** `allinanchor: best cloud service provider`
- Returns pages where anchor text contains "best," "cloud," "service," "provider"

#### `cache:` Operator
Displays Google's cached version of a web page.

**Example:** `cache:www.eff.org`
- Shows Google's cached version of EFF home page

#### `link:` Operator
Searches websites or pages that contain links to specified website.

**Example:** `link:www.googleguide.com`
- Finds pages that point to Google Guide's home page

**Note:** Cannot combine `link:` with regular keyword search

#### `related:` Operator
Displays websites similar or related to specified URL.

**Example:** `related:www.microsoft.com`
- Provides websites similar to microsoft.com

#### `info:` Operator
Finds information for specified web page.

**Example:** `info:gothotel.com`
- Provides information about Gothotel.com home page

#### `location:` Operator
Finds information for specific location.

**Example:** `location: 4 seasons restaurant`
- Gives results based on the term "4 seasons restaurant"

#### `filetype:` Operator
Allows you to search for results based on a file extension.

**Example:** `jasmine:jpg`
- Provides jpg files based on jasmine

#### `source:` Operator
Displays information from a specific website in Google News.

**Example:** `Malware news source:"Hacker News"`
- Returns articles from Hacker News containing "Malware"

#### `phonebook:` Operator
Finds residential and business phone numbers of a person or organization.

**Example:** `phonebook:Sundar Pichai`
- Provides Sundar Pichai's phone number

#### `before:` Operator
Filters search results to include only content published before specified date.

**Example:** `ransomware before:2020-06-29`
- Gives results about ransomware before June 29, 2020

#### `after:` Operator
Finds information published after a certain date.

**Example:** `site:wikipedia.org after:2023-01-01 artificial intelligence`
- Retrieves Wikipedia articles about AI published after January 1, 2023

---

## 2.3 What Can a Hacker Do with Google Hacking?

### Information Extraction

Attackers can create complex search-engine queries to filter large amounts of search results to obtain computer security-related information.

### Sensitive Information Found on Public Servers

- Error messages containing sensitive information
- Files containing passwords
- Sensitive directories
- Pages containing logon portals
- Pages containing network or vulnerability data (IDS, firewall logs, configurations)
- Advisories and server vulnerabilities
- Software version information
- Web application source code
- Connected IoT devices and their control panels (if unprotected)
- Hidden web pages (intranet, VPN services)

### Example Google Dork

`intitle:intranet inurl:intranet +intext:"human resources"`

**Purpose:** Find sensitive information about target organization and its employees. Attackers use gathered information to perform social engineering attacks.

---

## 2.4 Google Hacking with AI

### Using ShellGPT for Advanced Google Hacking

Attackers can use AI-powered technologies like ShellGPT to automate footprinting tasks.

**Example Prompt:**
"Use filetype search operator to obtain pdf files on the target website eccouncil.org and store the result in the recon1.txt file"

**Generated Shell Command:**
```bash
lynx --dump "http://www.google.com/search?q=site:ecouncil.org+filetype:pdf" | grep "http" | cut -d "=" -f2 | grep -o "http[^&]*" > recon1.txt
```

**Command Breakdown:**

| Component | Description |
|-----------|-------------|
| `lynx --dump` | Initiates Lynx web browser in dump mode |
| `"http://www.google.com/search?q=site:ecouncil.org+filetype:pdf"` | Accesses Google search results for PDF files in eccouncil.org |
| `\| grep "http"` | Filters lines containing "http" |
| `\| cut -d "=" -f2` | Splits lines using "=" delimiter, selects second field |
| `\| grep -o "http[^&]*"` | Searches for patterns starting with "http" followed by any characters except "&" |
| `> recon1.txt` | Redirects output to recon1.txt file |

---

## 2.5 Google Hacking Database (GHDB)

### Overview

The Google Hacking Database (GHDB) is an authoritative source for querying the ever-widening reach of the Google search engine. It is a subset of Exploit-DB and focuses on using Google search queries (often referred to as "Google Dorks") to find sensitive information inadvertently exposed on the web.

### What GHDB Queries Can Uncover

- **Sensitive files:** Configuration files, database dumps, log files containing usernames, passwords, or confidential data
- **Exposed directories:** Open directories on web servers containing sensitive information
- **Error messages:** Web server or application error messages revealing server configurations or vulnerabilities
- **Vulnerable devices:** Specific types of devices or software versions known to have vulnerabilities

### GHDB Categories

- Footholds
- Files Containing Usernames
- Files Containing Passwords
- Sensitive Directories
- Sensitive Online Shopping Info
- Web Server Detection
- Vulnerable Files
- Vulnerable Servers
- Network or Vulnerability Data
- Error Messages
- Pages Containing Login Portals
- Various Online Devices
- Advisories and Vulnerabilities

### How Attackers Use GHDB

1. **Reconnaissance** - Gather information about potential targets
2. **Exploiting Misconfigurations** - Identify sensitive information exposed through misconfigured web servers
3. **Finding Vulnerable Systems** - Locate systems running outdated or vulnerable software
4. **Credential Harvesting** - Find usernames and passwords for credential stuffing or brute force attacks
5. **Identifying Open Ports and Services** - Map potential entry points

### SearchSploit

SearchSploit is a command-line search tool for Exploit-DB that allows offline searches through a locally checked-out copy of the repository. Useful for security assessments of segregated or air-gapped networks without Internet access.

---

## 2.6 VPN Footprinting Through Google Hacking Database

### Google Dorks for VPN Footprinting

| Google Dork | Description |
|-------------|-------------|
| `inurl:"/sslvnp_login.shtml" intitle:"User Authentication" "WatchGuard Technologies"` | Finds pages containing login portals |
| `inurl: /sslvpn/Login/Login` | Finds VPN login portals |
| `site:vpn.*.*/intitle:"login" inurl:weblogin` | Finds various VPN login pages |
| `intitle:"USG20-VPN" "USG20W-VPN" "USG40" "USG60" ...` | Finds hosts with Zyxel hardcoded password vulnerability |
| `intext:Please Login SSL VPN inurl:remote/login intext:FortiClient` | Finds Fortinet VPN login pages |
| `site:vpn.*.*/intext:"login" intitle:"login"` | Retrieves various VPN login pages |
| `intitle:"index of" /etc/openvpn/` | Retrieves sensitive directories |
| `"---BEGIN OpenVPN Static key V1---" ext:key` | Finds OpenVPN static keys |
| `intitle:"index of" "vpn-config.*"` | Retrieves juicy information about vpn-config file |
| `Index of /*.ovpn` | Finds OpenVPN configuration files, certificates, and keys |
| `inurl:"/vpn/tmindex.html" vpn` | Finds Netscaler and Citrix Gateway VPN login portals |
| `intitle:"SSL VPN Service" + intext:"Your system administrator provided..."` | Finds Cisco ASA login web pages |

### VPN Footprinting with AI

**Example Prompt:**
"Use inurl search operator to obtain the Fortinet VPN login pages"

**Generated Command:**
```bash
Lynx -dump http://www.google.com/search?q=inurl:%22remote+login%22+fortinet+OR+fortigate+OR+%22ssl+vpn%22 | grep "http" | cut -d "=" -f2 | grep -o "http[^&]*"
```

**Command Breakdown:**
- Searches for web pages containing "remote login" in URL and either "Fortinet", "Fortigate", or "ssl vpn" in content
- Filters out lines containing "http"
- Splits each line using "=" delimiter, selects second field
- Searches for patterns starting with "http" followed by any characters except "&"

---

## 2.7 Footprinting Through SHODAN Search Engine

### Overview

Shodan is a search engine that enables attackers to perform footprinting at various levels. It is used to detect devices and networks with vulnerabilities.

### What Shodan Can Find

- Connected devices (routers, servers, IoT devices)
- Devices with open ports and services
- Geographic location of devices
- Operating systems
- Manufacturer details
- Known vulnerabilities

### Common Shodan Searches

- **VoIP footprinting** - Find VoIP devices and systems
- **VPN footprinting** - Find VPN devices and configurations
- **SCADA/ICS devices** - Identify industrial control systems
- **IoT devices** - Find Internet-connected devices

---

## 2.8 Other Search Engine Footprinting Techniques

### Google Advanced Search

Google's Advanced Search feature helps attackers perform complex web searching more precisely and accurately.

**How to Access:**
1. Click Settings at bottom-right of Google home page
2. Choose Advanced Search
3. Or directly type: https://www.google.com/advanced_search

**Benefits:**
- Search more precisely and accurately
- Same precision as advanced operators without typing/remembering them
- Find sites that link back to target organization's website
- Extract partner, vendor, client, and affiliation information

### Google Advanced Image Search

Allows users to search based on image color, domain, file type, size, keyword, etc.

**How to Access:**
https://www.google.com/advanced_image_search

**Uses for Attackers:**
- Acquire images of target
- Images of location
- Employee photographs
- Facility images

### Reverse Image Search

Allows users to use an image as a search query.

**How to Access:**
https://www.google.com/imghp

**Purpose:**
- Track original source of images
- Find details of photographs, profile pictures, memes
- Verify authenticity of images

**Tools:**
- Google Image Search
- TinEye Reverse Image Search
- Yahoo Image Search
- Bing Image Search
- Pinterest Reverse image search

---

### Video Search Engines

Video search engines crawl the web for video content.

**Examples:**
- YouTube
- Google videos
- Yahoo videos
- Bing videos

**Information Gathered:**
- Time/date of videos
- Thumbnails
- Video content analysis

**Video Analysis Tools:**
- YouTube Metadata
- YouTube DataViewer
- MW Metadata
- EZGif
- VideoReverser.com

### Meta Search Engines

Meta search engines use other search engines to produce their own results.

**Examples:**
- Startpage
- MetaGer
- eTools.ch

**Advantages:**
- Retrieve more results with same effort
- Privacy features (hide IP address)
- Filter identical search results

**Information Gathered:**
- Shopping sites (Amazon, eBay, BestBuy)
- Images, videos, blogs
- News and articles

### FTP Search Engines

FTP search engines search for files located on FTP servers.

**Examples:**
- NAPALM FTP Indexer
- FreewareWeb FTP File Search
- Mamont
- Globalfilesearch.com

**Information Gathered:**
- Business strategies
- Tax documents
- Employee records
- Financial records
- Licensed software
- Confidential information

### Google Search Queries for Finding FTP Servers

| Google Dork | Description |
|-------------|-------------|
| `site::in | .com | .net intitle:"index of" ftp` | Finds files containing juicy information |
| `intitle:"index of" * /ftp.txt"` | Finds files containing juicy information |
| `intext:"index of" "ftp"` | Finds files containing juicy information |
| `inurl:WS_FTP.log` | Finds files containing juicy information |
| `intitle:index.of /cfp /robots.txt` | Finds files containing juicy information |
| `intitle:"Index of ftp passwords"` | Finds files containing passwords |
| `inurl: /ftp intitle:"office"` | Detects the web server |
| `inurl: /web-ftp.cgi` | Finds pages containing login portals |
| `site:sfpt.*.*/ intext:"login" intitle:"server login"` | Finds pages containing login portals |
| `intitle:"Index of" ws_ftp.ini` | Finds ws_ftp.ini file containing usernames and passwords |
| `inurl:ftp -inurl:http` | Finds archived email conversations |
| `allintitle:"CrushFTP WebInterface"` | Detects CrushFTP WebInterface pages |
| `"ws_ftp.log" ext:log` | Finds sensitive directories |
| `intitle:"Monsta ftp" intext:"Lock session to IP"` | Shows websites using Monsta FTP service |
| `"index of" /ftp/logs` | Finds potential log files |
| `intitle:"index of" inurl:ftp intext:admin` | Lists admin folders on FTP servers |

### IoT Search Engines

IoT search engines crawl the Internet for IoT devices that are publicly accessible.

**Examples:**
- Shodan
- Censys
- ZoomEye

**Information Gathered:**
- Manufacturer details
- Geographical location
- IP address
- Hostname
- Open ports

**Targets:**
- SCADA systems
- Traffic control systems
- Internet-connected household appliances
- Industrial appliances
- CCTV cameras

**Risks:**
- Many IoT devices are unsecured (no passwords or default credentials)
- Can be exploited easily by attackers
- Can establish backdoors
- Launch further attacks

---

# PART 3: FOOTPRINTING THROUGH INTERNET RESEARCH SERVICES

## 3.1 Finding a Company's Top-Level Domains and Sub-domains

### Introduction

A company's top-level domains (TLDs) and sub-domains can provide a large amount of useful information to an attacker.

### Public Websites

- Designed to show presence of organization on Internet
- Available for free public access
- Designed to attract customers and partners
- May contain: organizational history, services/products, contact information

### Sub-Domains

- Available to limited audience
- Often used for testing new technologies
- Generally insecure (testing stage)
- More vulnerable to exploitation
- Provide insights into different departments and business units

### Finding Sub-Domains

**Google Advanced Search Operator:**
```
site: microsoft.com - inurl: www
```

### Tools for Sub-Domain Discovery

#### Netcraft
https://www.netcraft.com

**Features:**
- Internet security services
- Anti-fraud and anti-phishing services
- Application testing
- PCI scanning
- Market share analysis

#### DNSdumpster
https://dnsdumpster.com

**Features:**
- Domain research tool
- Discover hosts related to a domain
- Find subdomains, IP addresses, DNS servers

#### Pentest-Tools Find Subdomains
https://pentest-tools.com

**Features:**
- Discover subdomains and IP addresses
- Network information
- HTTP servers
- Operating systems
- Technology used
- Web platform
- Page titles

### Finding Sub-Domains with AI

**Example Prompt:**
"Discover all the subdomains of 'google.com' using dig command"

**Generated Command:**
```bash
dig +short google.com NS | xargs -I{} dig +nocmd +noall +answer @{} google.com | grep -E 'CNAME|AAAA'
```

**Command Breakdown:**
- `dig +short google.com NS` - Retrieves name server records
- `xargs -I{}` - Takes each name server as argument
- `dig +nocmd +noall +answer @{} google.com` - Performs DNS lookup for A records

**Another Example Prompt:**
"Use Sublist3r to gather a list of subdomains of the target organization eccouncil"

**Generated Command:**
```bash
sublist3r -d eccouncil.org -o eccouncil_subdomains.txt
```

**Command Breakdown:**
- `sublist3r` - Invokes the tool
- `-d eccouncil.org` - Specifies target domain
- `-o eccouncil_subdomains.txt` - Specifies output file

---

## 3.2 Extracting Website Information from Archive.org

### Internet Archive's Wayback Machine

https://archive.org

### Purpose
Explores archived versions of websites, allowing attackers to gather information on organization's web pages since creation.

### Information Retrievable
- Web pages
- Audio files
- Video files
- Images
- Text
- Software programs
- Removed/deleted content

### Using Photon Tool

**Command to retrieve archive.org links:**
```bash
photon.py -u <URL of Target Website> -1 3 -t 200 -wayback
```

**Command to retrieve archived URLs:**
```bash
python photon.py -u <URL of Target Website> -1 3 -t 200 -only-urls
```

---

## 3.3 Footprinting Through People Search Services

### Overview

People search services can provide critical information about a person or organization.

**Examples:**
- Spokeo
- Intelius
- Pipl
- BeenVerified
- Whitepages
- Instant Checkmate
- PeekYou

### Information Retrieved

- Names
- Addresses
- Contact details
- Date of birth
- Photographs
- Videos
- Profession
- Family and friends information
- Social networking profiles
- Property information
- Criminal background checks
- Business information
- Websites and blogs
- Company email addresses
- Cell phone numbers
- Fax numbers
- Personal e-mail addresses

### Spokeo Example

Attackers can use Spokeo people search online service to search for people belonging to the target organization.

**Information Obtained:**
- Phone numbers
- Email addresses
- Address history
- Age
- Date of birth
- Family members
- Social profiles
- Court records

---

## 3.4 Footprinting Through Job Sites

### Overview

Job sites can reveal details about a company's infrastructure.

**Examples:**
- Dice
- LinkedIn
- Glassdoor
- Simply Hired

### Information Gathered from Job Postings

- Operating system information
- Software versions
- Network-related information
- Technologies used (firewalls, internal server type, OS used, network appliances, hypervisors, VMs)
- Key employee list with email addresses

### Information from Employee Resumes

- Individual's expertise
- Educational qualifications
- Job history
- Technical information about target organization

### How Attackers Use This Information

- Detect underlying vulnerabilities in target IT infrastructure
- Plan attacks based on technology stack
- Identify security products used

---

## 3.5 Dark Web Footprinting

### Layers of the Internet

#### Surface Web
- Outer layer of online cyberspace
- Accessible using regular web browsers
- Search engines use crawlers to index
- Examples: Google, Chrome, Firefox, Opera

#### Deep Web
- Layer consisting of hidden and unindexed web pages
- Cannot be located using traditional browsers and search engines
- Size is incalculable (almost entire WWW)
- Contains official government/federal databases
- Can be accessed using Tor Browser, WWW Virtual Library
- Used for both legal and illegal activities

#### Dark Web/Darknet
- Deeper layer, subset of deep web
- Enables anonymous navigation without being traced
- Accessible only through specialized tools
- Search engines: Tor Browser, ExoneraTor

### Dark Web Searching Tools

#### Tor Browser
https://www.torproject.org

**Features:**
- Acts as default VPN
- Bounces network IP through several servers
- Access hidden content, unindexed websites, encrypted databases

#### Advanced Search Parameters for Dark Web

| Type of Information | Search Query | Explanation |
|---------------------|--------------|-------------|
| Personal profiles | "John Doe" site:facebook.com OR site:linkedin.com | Search social media profiles |
| Scientific publications | "John Doe" site:scholar.google.com | Search academic papers |
| Court records | "John Doe" court records | Search legal documents |
| Member directories | "John Doe" site:example.com "employee directory" | Search employee directories |
| Medical records | "John Doe" medical records | Search health information |
| Location records | "John Doe" location history | Search location/GPS information |

### Dark Web Search Queries for Sensitive Information

| Type of Information | Search Query |
|---------------------|--------------|
| Sensitive PDFs | `filetype:pdf site:onion confidential` |
| Passwords in Config Files | `inurl:config filetype:txt password` |
| Financial Documents | `filetype:xls site:onion financial` |
| Database Dumps | `filetype:sql site:onion dump` |
| Email Lists | `filetype:csv site:onion email` |
| Login Credentials | `intitle:"login credentials" filetype:docx` |
| Server Configurations | `filetype:xml inurl:config server` |
| Private Keys | `filetype:key site:onion private` |
| Medical Records | `filetype:pdf site:onion "medical records"` |
| Business Plans | `filetype:ppt site:onion "business plan"` |
| Source Code | `filetype:py site:onion "def"` |
| Legal Documents | `filetype:docx site:onion "legal document"` |
| Bank Statements | `filetype:pdf site:onion "bank statement"` |
| Intellectual Property | `filetype:pdf inurl:patent confidential` |
| Security Vulnerabilities | `filetype:txt inurl:exploit "security vulnerability"` |

---

## 3.6 Determining the Operating System

### Tools for OS Detection

#### Netcraft
https://www.netcraft.com

**Features:**
- Identify sites associated with target domain
- Show operating system running at each site
- OS fingerprinting capabilities

#### SHODAN
https://www.shodan.io

**Features:**
- Discover devices connected to Internet
- Device location information
- Operating system information
- Search for known vulnerabilities across Exploit DB, Metasploit, CVE, OSVDB, Packetstorm

#### Censys
https://censys.io

**Features:**
- Monitors infrastructure
- Discovers unknown assets anywhere on Internet
- Full view of every server and device exposed to Internet
- Operating system information
- IP address, protocols used, geographical location

---

## 3.7 Competitive Intelligence Gathering

### Definition

Competitive intelligence gathering is the process of identifying, gathering, analyzing, verifying, and using information about competitors from resources such as the Internet.

### Characteristics

- Non-interfering and subtle in nature
- Focuses on external business environment
- Information gathered ethically and legally
- Helps managers and executives make strategic decisions

### What Competitive Intelligence Determines

- What competitors are doing
- How competitors position their products and services
- What customers say about competitors' strengths and weaknesses

### Sources of Competitive Intelligence

#### Direct Approach
- Trade shows
- Social engineering of employees and customers

#### Indirect Approach
- Company websites and employment ads
- Support threads and reviews
- Search engines, Internet, and online databases
- Social media postings
- Press releases and annual reports
- Trade journals, conferences, and newspapers
- Patent and trademarks
- Product catalogs and retail outlets
- Analyst and regulatory reports
- Customer and vendor interviews
- Agents, distributors, and suppliers
- Industry-specific blogs and publications
- Legal databases (LexisNexis)
- Business information databases (D&B Hoovers)
- Online job postings
- Financial filings
- Technology solutions (Crunchbase)
- Intellectual property analysis

### Key Questions Answered

1. **When did it begin?** - Company history, establishment date
2. **How did it develop?** - Strategies, advertisement, customer relationship management
3. **Who leads it?** - Decision-makers
4. **Where is it located?** - Location, branches, operations

### Information Resource Sites

#### EDGAR Database
https://www.sec.gov/edgar

**Purpose:** Automated collection, validation, indexing, acceptance, forwarding of company submissions to SEC

#### D&B Hoovers
https://www.dnb.com

**Features:**
- Commercial database of 120 million business records
- Sales intelligence solution
- Prospect targeting

#### LexisNexis
https://www.lexisnexis.com

**Features:**
- Content-enabled workflow solutions
- Electronic database of legal and public records
- Access to documents and records of legal, news, and business sources

#### Business Wire
https://www.businesswire.com

**Features:**
- Press release distribution
- Regulatory disclosure
- Full-text news releases, photos, multimedia

#### Factiva
https://www.dowjones.com

**Features:**
- Global news database
- Licensed content provider
- Access to 33,000+ sources in 28 languages

### Company Business Plans Information

#### MarketWatch
https://www.marketwatch.com

**Features:**
- Business news
- Personal finance information
- Real-time commentary
- Investment tools and data

#### The Wall Street Transcript
https://www.twst.com

**Features:**
- Paid subscription-based publication
- Industry reports
- Money managers and equity analysts views
- CEO interviews

#### Euromonitor
https://www.euromonitor.com

**Features:**
- Strategy research capabilities for consumer markets
- Industry, consumer, and demographic reports
- Market research and surveys

#### Experian
https://www.experian.com

**Features:**
- Competitor search, affiliate, display, social marketing insights
- Benchmark customer acquisition strategies
- Historical consumer data for trend forecasting

#### The Search Monitor
https://www.thesearchmonitor.com

**Features:**
- Track brand and trademark use
- Monitor affiliate compliance
- Track paid search, organic search, local search, social media, mobile

#### USPTO
https://www.uspto.gov

**Features:**
- Patent and trademark registration information
- Patent and trademark database search

### Expert Opinions Information

#### SEMRush
https://www.semrush.com

**Features:**
- Competitive keyword research
- Google keywords and AdWords for any site
- Competitor list in organic and paid search results

#### ABI/INFORM Global
https://www.proquest.com

**Features:**
- Business and financial information database
- Business conditions, management techniques, business trends
- Corporate strategy and tactics

#### SimilarWeb
https://www.similarweb.com

**Features:**
- Traffic, geography, and referral data
- Browser extension for anonymous tracking
- Mobile app analytics

#### SERanking
https://seranking.com

**Features:**
- Complete view of website traffic dynamics
- Competitor analysis
- PPC competitor research

---

## 3.8 Other Internet Research Techniques

### Finding Geographical Location

**Tools:**
- Google Earth
- Google Maps
- Wikimapia

**Information Gathered:**
- Entrances to buildings
- Security cameras
- Gates
- Places to hide
- Weak spots in perimeter fences
- Utility resources

### Gathering Financial Information

**Tools:**
- Google Finance
- MSN Money
- Yahoo! Finance
- Investing.com

**Information Gathered:**
- Market value of company shares
- Company profile
- Competitor details
- Stock exchange rates
- Corporate press releases
- Financial reports

### Gathering Business Profile Information

**Tools:**
- opencorporates
- Crunchbase
- corporationwiki

**Information Gathered:**
- Location
- Addresses
- Contact information
- Employee database
- Department names
- Type of service provided
- Type of industry

### Monitoring Targets Using Alerts

**Tools:**
- Google Alerts
- X Alerts
- Giga Alerts

**Information Gathered:**
- Mentions of organization's name
- Member names
- Website mentions
- People or projects mentions

### Tracking Online Reputation

**Tools:**
- Mention
- ReviewPush
- Reputology

**Information Gathered:**
- Search engine ranking information
- Email notifications when company is mentioned online
- Conversations
- Social news about company

### Gathering Information from Groups, Forums, and Blogs

**Platforms:**
- Google Groups
- LinkedIn Groups

**Information Gathered:**
- Public network information
- System information
- Employee personal information

**Employee Information That Can Be Gathered:**
- Full name of employee
- Place of work and residence
- Home telephone, cell number, office number
- Personal and organizational email address
- Pictures of employee residence or work location
- Pictures of employee awards and rewards

### Gathering Information from Public Source-Code Repositories

**Platforms:**
- GitHub
- GitLab
- SourceForge
- BitBucket

**Information Gathered:**
- Configuration files
- Private SSH and SSL keys
- Source-code files
- Dynamic libraries
- Software tools developed by contributors

**Tool Used:**
- Recon-ng

---

# PART 4: FOOTPRINTING THROUGH SOCIAL NETWORKING SITES

## 4.1 Introduction

### Overview

Social networking services are online platforms that focus on facilitating the building of social networks or social relations among people.

### Key Points

- Contains information provided by users in their profiles
- Helps relate people directly or indirectly through common interests, work locations, education
- Allows people to share information quickly in real-time
- Can update personal details in real-time
- Great platform for finding people and related information

### What Attackers Can Gather

- Personal information (name, position, organization name, current location, educational qualifications)
- Professional information (company, business, current location, phone number, email ID)
- Photos and videos
- Advice, news, concerns, opinions, rumors, facts

### Social Media Platforms Used

- Facebook
- Twitter (X)
- LinkedIn
- Instagram
- Pinterest
- YouTube

---

## 4.2 Gathering Information from LinkedIn

### Overview

LinkedIn is a social networking website for professionals that connects the world's human resources.

### Information Available

- Name
- Position
- Organization name
- Current location
- Educational qualifications
- Professional history

### Tool: theHarvester

https://github.com

**Purpose:** Tool designed for open-source intelligence gathering in early stages of penetration test.

**Command to Enumerate LinkedIn Users:**
```bash
theHarvester -d microsoft -l 200 -b linkedin
```

**Parameters:**
- `-d` - Domain or company name to search
- `-l` - Number of results to retrieve
- `-b` - Data source (LinkedIn)

---

## 4.3 Harvesting Email Lists

### Importance

Gathering email addresses related to the target organization acts as an important attack vector during later phases of hacking.

### Tools

#### theHarvester

**Command to Extract Email Addresses:**
```bash
theHarvester -d microsoft.com -l 200 -b baidu
```

**Parameters:**
- `-d` - Domain used for harvesting emails
- `-l` - Limit results to 200
- `-b` - Search engine source (baidu, google, bing, etc.)

### Harvesting Email Lists with AI

**Example Prompt:**
"Use theHarvester to gather email accounts associated with 'microsoft.com', limiting results to 200, and leveraging 'baidu' as a data source"

**Generated Command:**
```bash
theHarvester -d microsoft.com -l 200 -b Baidu -f Microsoft_emails.xml
```

**Parameters:**
- `-f` - Output file name (XML format)

---

## 4.4 Analyzing Target Social Media Presence

### Tools

#### BuzzSumo
https://buzzsumo.com

**Features:**
- Advanced social search engine
- Find most shared content for topic, author, or domain
- Shows shared activity across major social networks (Twitter, Facebook, LinkedIn, Google Plus, Pinterest)

**Information Gathered:**
- Social media account information
- URLs
- Email addresses

---

## 4.5 Tools for Social Networking Footprinting

### Sherlock
https://github.com

**Purpose:** Search a vast number of social networking sites for a target username.

**Command:**
```bash
sherlock SundarPichai --output recon2
```

### Social Searcher
https://www.social-searcher.com

**Purpose:** Search for content on social networks in real-time.

**Information Gathered:**
- Complete URLs to profiles
- Postings
- Other personal information

---

# PART 5: WHOIS FOOTPRINTING

## 5.1 Introduction to Whois

### Definition

Whois is a query and response protocol used for querying databases that store the registered users or assignees of an Internet resource, such as a domain name, an IP address block, or an autonomous system.

### Protocol Details

- Listens to requests on port 43 (TCP)
- Maintained by Regional Internet Registries (RIRs)

### Types of Whois Data Models

1. **Thick Whois (Distributed Model)** - Stores complete Whois information from all registrars for a particular set of data
2. **Thin Whois (Centralized Model)** - Stores only name of Whois server of registrar of a domain, which holds complete details
3. **Decentralized Whois** - Stores complete Whois information with multiple independent entities managing database

### Information Returned by Whois Query

- Domain name details
- Domain registrar
- Contact details of domain owner
- Domain name servers
- NetRange
- When domain was created
- Expiry records
- Last updated record
- Domain status (available, registered, suspended)
- IP address information

### Regional Internet Registries (RIRs)

| Registry | Website | Region |
|----------|---------|--------|
| ARIN | https://www.arin.net | North America |
| AFRINIC | https://www.afrinic.net | Africa |
| APNIC | https://www.apnic.net | Asia Pacific |
| RIPE | https://www.ripe.net | Europe, Middle East, Central Asia |
| LACNIC | https://www.lacnic.net | Latin America and Caribbean |

### How Attackers Use Whois Information

- Create a map of organization's network
- Mislead domain owners with social engineering
- Obtain internal details of network

---

## 5.2 Whois Lookup Tools

### Online Whois Services

#### DomainTools Whois
https://whois.domaintools.com

#### Tamos Whois
https://www.tamos.com

#### Batch IP Converter
http://www.sabsoft.com

**Features:**
- Information about IP address, hostname, domain
- Country, state/province, city
- Phone number, fax number
- Network provider information
- Administrator and technical-support contact
- Supports IDNs and IPv6

### Other Whois Tools

- WHOIS Domain Lookup
- Active Whois

---

## 5.3 Finding IP Geolocation Information

### What IP Geolocation Provides

- Country
- Region/state
- City
- Latitude and longitude
- ZIP/postal code
- Time zone
- Connection speed
- ISP (hosting company)
- Domain name
- IDD country code
- Area code
- Weather station code and name
- Mobile carrier
- Elevation
- Usage type

### How Attackers Use IP Geolocation

- Gather more information through social engineering
- Surveillance
- Non-technical attacks (dumpster diving, hoaxing, technical expert impersonation)
- Set up compromised web server near victim's location
- Infect victims with malware designed for specific area
- Gain unauthorized access to target device

### IP Geolocation Lookup Tools

#### IP2Location
https://www.ip2location.com

**Features:**
- Identify visitor's geographical location
- Country, region, city
- Latitude and longitude
- ZIP code, time zone
- Connection speed
- ISP, domain name
- IDD country code, area code
- Weather station code and name
- Mobile carrier, elevation
- Usage type information

---

# PART 6: DNS FOOTPRINTING

## 6.1 Introduction to DNS Footprinting

### Purpose

After collecting Whois records, attackers perform DNS footprinting to gather information about DNS servers, DNS records, and types of servers used by target organization.

### Why DNS Footprinting Matters

- Reveals DNS zone data
- Domain names, computer names, IP addresses
- Helps determine key hosts in network
- Enables social engineering attacks

### DNS Records

| Record Type | Description |
|-------------|-------------|
| A | Points to a host's IP address |
| AAAA | Points to a host's IPv6 address |
| MX | Points to domain's mail server |
| NS | Points to host's name server |
| CNAME | Canonical naming allows aliases to a host |
| SOA | Indicate authority for a domain |
| SRV | Service records |
| PTR | Maps IP address to a hostname |
| RP | Responsible person |
| HINFO | Host information record (CPU type and OS) |
| TXT | Unstructured text records |

---

## 6.2 DNS Interrogation Tools

### SecurityTrails
https://securitytrails.com

**Features:**
- Advanced DNS enumeration tool
- Create DNS map of target domain network
- Enumerate current and historical DNS records (A, AAAA, NS, MX, SOA, TXT)
- Enumerate subdomains using brute-force techniques

### Fierce
https://github.com

**Purpose:** DNS reconnaissance tool for scanning and collecting crucial information about target domain.

**Commands:**

**Basic Scan:**
```bash
fierce --domain certifiedhacker.com
```

**Scan for Specific Subdomains:**
```bash
fierce --domain certifiedhacker.com --subdomains write admin mail
```

**Scan Domains Near Discovered Records:**
```bash
fierce --domain certifiedhacker.com --subdomains mail --traverse 10
```

**Attempt HTTP Connection on Discovered Domains:**
```bash
fierce --domain certifiedhacker.com --subdomains mail --connect
```

**Full Detailed Scan:**
```bash
fierce --domain certifiedhacker.com --wide
```

### DNS Lookup with AI

**Example Prompt:**
"Install and use DNSRecon to perform DNS enumeration on the target domain www.certifiedhacker.com"

**Generated Command:**
```bash
sudo apt-get update && sudo apt-get install -y dnsrecon && dnsrecon -d certifiedhacker.com -t std
```

**Command Breakdown:**
- `sudo apt-get update` - Updates package lists
- `&&` - Executes commands sequentially
- `sudo apt-get install -y dnsrecon` - Installs dnsrecon tool
- `dnsrecon -d certifiedhacker.com -t std` - Performs DNS enumeration using standard techniques

---

## 6.3 Reverse DNS Lookup

### Definition

Reverse DNS lookup is performed to obtain the domain name of a given IP address.

### Purpose

- Locate DNS PTR record for IP addresses
- Convert IP address back to domain name

### Tools

#### DNSRecon
https://github.com

**Command for Reverse DNS Lookup:**
```bash
dnsrecon -r 162.241.216.0-162.241.216.255
```

**Parameter:**
- `-r` - Range of IP addresses (first to last) for reverse lookup by brute force

#### Reverse Lookup
https://mxtoolbox.com

**Features:**
- Performs reverse IP lookup
- Takes IP address
- Locates DNS PTR record

---

# PART 7: NETWORK AND EMAIL FOOTPRINTING

## 7.1 Locating Network Range

### Overview

To perform network footprinting, attackers need to gather basic and important information about the target organization.

### Information Needed

- What the organization does
- Who works there
- What type of work it does
- Internal structure of target network

### Private IP Address Ranges (IANA Reserved)

| IP Range | Prefix |
|----------|--------|
| 10.0.0.0 - 10.255.255.255 | 10/8 |
| 172.16.0.0 - 172.31.255.255 | 172.16/12 |
| 192.168.0.0 - 192.168.255.255 | 192.168/16 |

### How to Find Network Range

1. Enter server IP address (gathered from Whois footprinting)
2. Use ARIN Whois database search tool
3. Visit ARIN website: https://www.arin.net
4. Enter server IP in search box
5. Yields network range of target network

### What Network Range Provides

- How network is structured
- Which machines in network are alive
- Network topology
- Access control device
- OS used in target network

### ARIN Whois Database Search

Attackers can determine subnet mask of domain and trace route between system and target system.

---

## 7.2 Traceroute

### Definition

Traceroute uses ICMP protocol and Time to Live (TTL) field of IP header to find the path of target host in network.

### How Traceroute Works

1. Exploits TTL field in IP header
2. Each router decrements TTL count by one
3. When count reaches zero, router discards packet
4. Router transmits ICMP error message to originator
5. Utility records IP address and DNS name of router
6. Sends another packet with TTL value of two
7. Continues until packet reaches target host
8. Records time for each packet to make round trip

### Information Revealed

- Number of routers packets travel through
- Round-trip time between routers
- Names of routers and network affiliation
- Geographic locations

### Types of Traceroute

#### ICMP Traceroute (Windows)
Windows operating system by default uses ICMP traceroute.

**Command:**
```
C:\>tracert 216.239.36.10
```

#### TCP Traceroute (Linux)
Used when devices block ICMP traceroute messages.

**Command:**
```bash
sudo tcp traceroute www.google.com
```

#### UDP Traceroute (Linux)
Linux built-in traceroute uses UDP protocol.

**Command:**
```bash
traceroute www.google.com
```

---

## 7.3 Traceroute Analysis

### Purpose

Find IP addresses of intermediate devices such as routers and firewalls present between source and destination.

### Example Analysis

**Traceroute Results:**
```
traceroute 1.10.10.20, second to last hop is 1.10.10.1
traceroute 1.10.20.10, third to last hop is 1.10.10.1
traceroute 1.10.10.20, second to last hop is 1.10.10.50
traceroute 1.10.20.15, third to last hop is 1.10.10.1
traceroute 1.10.20.15, second to last hop is 1.10.10.50
```

**Analysis:**
By compiling this information, attackers can identify intermediate devices or hosts in path to target network.

### Traceroute Tools

#### NetScanTools Pro
https://www.netscantools.com

**Features:**
- Hop-by-hop traceroutes
- ICMP, UDP, TCP traceroute methods
- Identify intermediate devices
- Locate country assigned to each IPv4 address

#### PingPlotter
https://www.pingplotter.com

**Features:**
- Collect traceroute data using ICMP, UDP, TCP
- Automatically discover network hops
- Track latency and packet loss over time
- Visualize traceroute data in graphs
- Identify bandwidth bottlenecks, WiFi interference, hardware faults

---

## 7.4 Tracking Email Communications

### Overview

Email tracking monitors email messages of a particular user through digitally time-stamped records that reveal when target receives and opens specific email.

### Information Gathered

| Information | Description |
|-------------|-------------|
| Recipient's System IP address | Allows tracking of recipient's IP address |
| Geolocation | Estimates and displays location on map |
| Email Received and Read | Notifies when email is received and read |
| Read Duration | Time spent reading the email |
| Proxy Detection | Information about server type used |
| Links | Checks whether links have been checked |
| Operating System and Browser | Reveals OS and browser information |
| Forward Email | Determines if email was forwarded |
| Device Type | Type of device used (desktop, mobile, laptop) |
| Path Traveled | Path through email transfer agents |

### Collecting Information from Email Header

**Email Header Contains:**
- Sender's mail server
- Date and time of receipt
- Authentication system used
- Time of sending message
- Unique number assigned to identify message
- Sender's full name
- Sender's IP address
- Address from which message was sent

### Email Tracking Tools

#### eMailTrackerPro
http://www.emailtrackerpro.com

**Features:**
- Analyze email headers
- Extract sender's geographical location
- Extract sender's IP address
- Save past traces for review

#### IP2LOCATION's Email Header Tracer
https://www.ip2location.com

**Features:**
- Open-source service
- Analyze and trace email paths
- Trace back target location
- Identify mail servers
- Utilize IP addresses in email header

### Other Email Tracking Tools

- MxToolbox
- DNS Checker Email Header Analyzer
- Social Catfish
- Holehe

---

# PART 8: FOOTPRINTING THROUGH SOCIAL ENGINEERING

## 8.1 Introduction to Social Engineering

### Definition

Social engineering is a non-technical process in which an attacker misleads a person into providing confidential information inadvertently. It is the art of exploiting human behavior to extract confidential information.

### Key Concept

Social engineers depend on the fact that people are unaware of their valuable information and are careless about protecting it.

### Information Gathered Through Social Engineering

- Credit card details and social security numbers
- Usernames and passwords
- Security products in use
- Operating systems and software versions
- Network layout information
- IP addresses and names of servers

### How It Works

1. Gain confidence of authorized user
2. Mislead user into revealing confidential information
3. Use information for malicious purposes (unauthorized access, identity theft, industrial espionage, network intrusion, fraud)

### Social Engineering Techniques

- Eavesdropping
- Shoulder surfing
- Dumpster diving
- Impersonation
- Tailgating
- Third-party authorization
- Piggybacking
- Reverse social engineering

---

## 8.2 Collecting Information Through Social Engineering on Social Networking Sites

### What Users Do vs What Attackers Get

| What Users Do | What Attacker Gets |
|---------------|-------------------|
| Maintain profile | Contact info, location, etc. |
| Connect to friends, chat | Friends list, friends' info, etc. |
| Share photos and videos | Identity of family members, interests, etc. |
| Play games, join groups | Interests |
| Create events | Activities |

### What Organizations Do vs What Attackers Get

| What Organizations Do | What Attacker Gets |
|----------------------|-------------------|
| User surveys | Business strategies |
| Promote products | Product profile |
| User support | Social engineering |
| Recruitment | Platform/technology information |
| Background check | Type of business |

---

## 8.3 Social Engineering Techniques

### Eavesdropping

**Definition:** Intercepting communication in any form (audio, video, text) without consent of communicating parties.

**Methods:**
- Tapping phone conversations
- Intercepting audio, video, written communications
- Reading confidential messages from communication media

### Shoulder Surfing

**Definition:** Secretly observing the target to gain critical information.

**What Attackers Look For:**
- Keystrokes while entering usernames
- Passwords
- Personal identification numbers
- Security codes
- Account numbers
- Credit card information

**Where It's Effective:**
- Crowded places
- Easy to stand behind and watch without knowledge

### Dumpster Diving

**Definition:** Rummaging for information in garbage bins.

**What Attackers Find:**
- Phone bills
- Contact information
- Financial information
- Operations-related information
- Printouts of source codes
- Printouts of sensitive information
- Account information from ATM trash bins

**Where:**
- Target company's trash bins
- Printer waste bins
- Sticky notes at users' desks

### Impersonation

**Definition:** Pretending to be a legitimate or authorized person.

**Methods:**
- Personal impersonation
- Phone impersonation
- Communication media impersonation

**Who Attackers Might Impersonate:**
- Courier/delivery person
- Janitor
- Businessman
- Client
- Technician
- Visitor

**What Attackers Do:**
- Scan terminals for passwords
- Search important documents on desks
- Rummage bins
- Overhear confidential conversations
- "Shoulder surf" to obtain sensitive information

---

# PART 9: FOOTPRINTING TOOLS

## 9.1 Maltego

https://www.maltego.com

**Purpose:** Automated tool used to determine relationships and real-world links between people, groups, organizations, websites, Internet infrastructure, documents, etc.

**Features:**
- Different entities available for information gathering
- Obtain email addresses
- Obtain list of phone numbers
- Target's Internet infrastructure (domains, DNS names, Netblocks, IP addresses)

---

## 9.2 Recon-ng

https://github.com

**Purpose:** Web Reconnaissance framework with independent modules and database interaction for open-source web-based reconnaissance.

**Features:**
- Modular architecture
- Database interaction
- Web reconnaissance capabilities

---

## 9.3 FOCA (Fingerprinting Organizations with Collected Archives)

https://www.elevenpaths.com

**Purpose:** Tool used mainly to find metadata and hidden information in documents.

**Supported Document Types:**
- Microsoft Office
- Open Office
- PDF files

**Features:**
- **Web Search** - Searches for hosts and domain names through URLs
- **DNS Search** - Checks each domain for host names in NS, MX, SPF servers
- **IP Resolution** - Resolves each host name to obtain IP address
- **PTR Scanning** - Finds more servers in same segment
- **Bing IP** - Search process for new domain names associated with IP address
- **Common Names** - Performs dictionary attacks against DNS

---

## 9.4 subfinder

https://github.com

**Purpose:** Subdomain discovery tool.

**Features:**
- Find valid subdomains for websites
- Uses passive online sources
- Supports multiple output formats (JSON, file, stdout)

---

## 9.5 OSINT Framework

https://osintframework.com

**Purpose:** Open source intelligence gathering framework focused on gathering information from free tools or resources.

**Features:**
- Simple web interface
- OSINT tools arranged by category
- OSINT tree structure

**Tool Indicators:**
- **(T)** - Link to a tool that must be installed and run locally
- **(D)** - Google dork
- **(R)** - Requires registration
- **(M)** - URL contains search term that must be edited manually

---

## 9.6 Recon-Dog

https://www.github.com

**Purpose:** All-in-one tool for basic information gathering needs using APIs.

**Features:**
- **Censys** - Gathers information about IP address
- **NS lookup** - Performs name server lookup
- **Port scan** - Scans most common TCP ports
- **Detect CMS** - Can detect 400+ content management systems
- **Whois lookup** - Performs Whois lookup
- **Detect honeypot** - Checks if target is a honeypot
- **Find subdomains** - Uses findsubdomains.com
- **Reverse IP lookup** - Finds domains associated with IP address
- **Detect technologies** - Uses wappalyzer.com to detect 1000+ technologies
- **All** - Runs all utilities against target

---

## 9.7 BillCipher

https://www.github.com

**Purpose:** Information gathering tool for website or IP address.

**Compatibility:**
- Python 2
- Python 3
- Ruby

**Features:**
- DNS lookup
- Whois lookup
- Port scanning
- Zone transfer
- Host finder
- Reverse IP lookup

---

## 9.8 Additional Footprinting Tools

- **Sudomy** - https://github.com
- **theHarvester** - https://www.edge-security.com
- **whatweb** - https://github.com
- **Raccoon** - https://github.com
- **Orb** - https://github.com
- **Web Check** - https://web-check.xyz
- **OSINT.SH** - https://osint.sh

---

# PART 10: AI-POWERED OSINT TOOLS

## 10.1 Introduction to AI-Powered OSINT

### How AI Revolutionizes OSINT

- Advanced data collection
- Advanced data analysis
- Predictive capabilities
- Automates data processing
- Extracts relevant insights
- Delivers actionable intelligence more efficiently

### Key Use Cases for AI in OSINT

#### Web Scraping
- Utilize online data from social media, blogs, forums, deep web databases
- Track entities over time
- Monitor public behavior
- Automate extraction of specific information (social media comments and replies)

#### Pattern Recognition
- Identify entities within large datasets
- Analyze files to identify relationships between entities
- Names, company details, addresses, emails, phone numbers

#### Content Summarization
- NLP algorithms summarize large volumes of data
- Extract pertinent information from extensive datasets
- Example: Extract company names from hundreds of PDF pages

#### Sentiment Analysis
- Interpret human emotions through text analysis
- Understand public sentiment
- Assess emotional state of users based on social media posts
- Predict consumer behavior based on reviews

#### Image Recognition
- Analyze digital media files (images, videos)
- **Face Recognition** - Identify and track individuals
- **Metadata Analysis** - Extract metadata from digital files
- **Reverse Image Search** - Enhance image search capabilities
- **Deepfake Detection** - Identify AI-generated content

#### AI Detection
- Identify content generated by other AI tools
- Detect malicious activities facilitated by AI

### Benefits of Integrating AI in OSINT

1. **Improved Efficiency** - Automates web scraping and data extraction, accelerates collection and analysis, allows focus on higher-level analysis, expedites investigations

2. **Greater Scope** - Analyzes vast data from surface web, deep web, and dark web, ensures comprehensive intelligence coverage, uncovers hidden patterns and relationships

3. **Enhanced Visibility** - Connects billions of seemingly unrelated data points, identifies suspicious activities, establishes connections between threat actors, user-friendly graphical interfaces

4. **Increased Investigator Safety** - Enables anonymized and automated investigations, reduces risk of exposing identity, conducts investigations without direct human involvement in dangerous environments

---

## 10.2 Taranis AI

https://taranis.ai

**Purpose:** Advanced OSINT tool that uses AI to enhance information gathering and situational analyses.

**Features:**
- **Advanced OSINT Capabilities** - Searches multiple data sources, collects unstructured news articles
- **AI-Enhanced Analysis** - Enhances collected articles using AI and NLP
- **Multi-Format Output** - Creates structured reports, PDF files
- **Seamless Publishing** - Enables easy publication of intelligence products

---

## 10.3 OSS Insight

https://ossinsight.io

**Purpose:** AI-powered GitHub ecosystem analysis tool.

**Features:**
- **GPT-Powered Data Exploration** - Query GitHub data using natural language, generate SQL queries, visualize results
- **Technical Fields Analytics** - Curates GitHub collections in technical domains (web frameworks, AI, Web3)
- **Developer Analytics** - Monitors commits, pull requests, code contributions, collaboration behaviors
- **Repository Analytics** - Assesses popularity (stars, forks), update frequency, community engagement
- **Compare Projects** - Enables easy comparison of metrics from different GitHub projects

**Importance in OSINT:**
- Analyze over 5 billion GitHub events
- Gather intelligence on software vulnerabilities
- Identify popular frameworks and emerging trends
- Access real-time and historical data
- AI-powered querying simplifies complex dataset queries

---

## 10.4 Additional AI-Powered OSINT Tools

### DorkGPT
https://dorkgpt.com

**Purpose:** AI-powered tool to assist Google Dorking.
**Features:** Generate and refine search queries, uncover sensitive information, hidden pages

### DorkGenius
https://dorkgenius.com

**Purpose:** AI-powered tool that automates Google Dorking.
**Features:** Generate advanced search queries, find hidden files, directories, sensitive information

### Google Word Sniper
https://googlewordsniper.eu

**Purpose:** Refine search queries for more effective Google results.
**Features:** Identify targeted keywords and phrases, find specific information, hidden content

### Cyclet.io
**Purpose:** Advanced AI-powered OSINT tool.
**Features:** Integrates multiple databases, user-friendly interface, efficient and confident OSINT investigations

### ChatPDF
https://chatpdf.com

**Purpose:** AI-powered PDF analysis tool.
**Features:** Analyze and extract information from PDF documents through conversational interface

### Bardeen.ai
https://www.bardeen.ai

**Purpose:** Automation tool for OSINT.
**Features:** Automate data collection and analysis, enhance speed and accuracy

### DarkGPT
https://github.com/lujiait/DarkGPT

**Purpose:** AI assistant using GPT-4-200K.
**Features:** Query leaked databases, efficient targeted searches within compromised data

### PenLink Cobwebs
https://cobwebs.com

**Purpose:** Advanced AI-powered OSINT tool.
**Features:** Gather and analyze data from various online sources, comprehensive capabilities

### Explore AI
https://exploreai.vercel.app

**Purpose:** AI-powered YouTube search engine.
**Features:** Search and extract information from YouTube videos

### AnyPicker
https://app.anypicker.com

**Purpose:** Visual web scraper and AI OSINT tool.
**Features:** Extract data without coding, scrape multiple pages simultaneously, real-time preview

---

## 10.5 Creating Custom Python Scripts for Footprinting with AI

### Using ChatGPT to Generate Scripts

**Example Prompt:**
"Develop a Python script which will accept domain name www.microsoft.com as input and execute a series of website footprinting commands, including DNS lookups, WHOIS records retrieval, email enumeration, and more, to gather information about the target domain"

**Generated Python Script:**
```python
import subprocess

def dns_lookup(domain):
    return subprocess.getoutput(f"dig {domain} ANY +noall +answer")

def whois_lookup(domain):
    return subprocess.getoutput(f"whois {domain}")

def email_enumeration(domain):
    return subprocess.getoutput(f"theHarvester -d {domain} -b all -l 100")

def run_footprinting(domain):
    print("Performing DNS Lookup...")
    dns_info = dns_lookup(domain)
    print(dns_info)
    
    print("\nPerforming Whois Lookup...")
    whois_info = whois_lookup(domain)
    print(whois_info)
    
    print("\nEnumerating Emails...")
    emails = email_enumeration(domain)
    print(emails)

domain = 'www.microsoft.com'
run_footprinting(domain)
```

**Functions Defined:**
- `dns_lookup(domain)` - Performs DNS lookup using dig command
- `whois_lookup(domain)` - Retrieves Whois records using whois command
- `email_enumeration(domain)` - Enumerates emails using theHarvester
- `run_footprinting(domain)` - Executes all footprinting commands

---

# PART 11: FOOTPRINTING COUNTERMEASURES

## 11.1 Overview

Countermeasures are measures or actions taken to prevent or offset information disclosure.

## 11.2 Organizational Countermeasures

### Employee Restrictions
- Restrict employees' access to social networking sites from organization's network
- Educate employees to use pseudonyms on blogs, groups, and forums
- Conduct security awareness training periodically
- Train employees to thwart social engineering techniques

### Information Management
- Configure web servers to avoid information leakage
- Do not reveal critical information in press releases, annual reports, product catalogs
- Limit amount of information published on website or Internet
- Use footprinting techniques to discover and remove sensitive information publicly available
- Prevent search engines from caching web pages
- Use anonymous registration services

### Security Policies
- Develop and enforce security policies (information security, password policies)
- Regulate information employees can reveal to third parties
- Place critical documents offline (business plans, proprietary documents)
- Sanitize details provided to Internet registrars

### Technical Countermeasures

#### DNS Configuration
- Set apart internal and external DNS or use split DNS
- Restrict zone transfer to authorized servers
- Disable directory listings in web servers
- Implement VPN or keep server behind secure proxy to hide IP address
- Use TCP/IP and IPsec filters for defense in depth

#### Security Mechanisms
- Implement multi-factor authentication mechanisms
- Implement captchas and rate limiting on public-facing services
- Do not enable protocols that are not required
- Configure IIS to avoid information disclosure through banner grabbing
- Deploy honeypots or honeynets within network

#### Account Management
- Disable or delete accounts of employees who left the organization
- Configure mail servers to ignore mails from anonymous individuals

### Personal Privacy Measures
- Disable geo-tagging functionality on cameras
- Avoid revealing location or travel plans on social networking sites
- Turn off geolocation access on all mobile devices when not required
- Do not display critical information (strategic plans, product information, sales projections) on notice boards or walls

### Data Protection
- Encrypt and password-protect sensitive information
- Request archive.org to delete website history from archive database
- Keep domain name profile private

### Additional Countermeasures

- Identify possible disclosure of sensitive information about the organization
- Go through all sources where attackers can obtain information
- Identify potential sensitive information disclosure
- Search for company information to check if any data leakage occurs
- Remove sensitive information from publicly accessible websites
- Educate staff about the need for privacy policies

---

# PART 12: MODULE SUMMARY

## Key Takeaways

### Footprinting Concepts
- Footprinting is the first step in ethical hacking
- Two types: passive and active
- Information gathered: organizational, network, system
- Objectives: build hacking strategy, identify security posture, find vulnerabilities

### Techniques Covered
1. **Search Engines** - Google advanced operators, GHDB, Shodan
2. **Internet Research** - People search, job sites, dark web
3. **Social Networking** - LinkedIn, Facebook, Twitter
4. **Whois** - Domain and IP information
5. **DNS** - Records and interrogation tools
6. **Network** - Traceroute analysis
7. **Email** - Header analysis and tracking
8. **Social Engineering** - Eavesdropping, shoulder surfing, dumpster diving, impersonation

### Tools Used
- Maltego, Recon-ng, FOCA, subfinder
- OSINT Framework, Recon-Dog, BillCipher
- theHarvester, Sherlock, BuzzSumo
- DNSRecon, Fierce, SecurityTrails
- NetScanTools Pro, PingPlotter
- eMailTrackerPro, IP2LOCATION
- Taranis AI, OSS Insight

### AI-Powered OSINT
- Web scraping, pattern recognition, content summarization
- Sentiment analysis, image recognition
- Benefits: efficiency, scope, visibility, safety

### Countermeasures
- Employee restrictions
- Information management
- Security policies
- Technical measures
- Personal privacy

---
