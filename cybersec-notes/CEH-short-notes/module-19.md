
---

# Module 19: Cloud Computing

## Learning Objectives

- Understand cloud computing concepts
- Understand container technology and serverless computing
- Understand cloud computing threats
- Understand different cloud hacking concepts
- Understand AWS hacking, Microsoft Azure hacking, Google Cloud hacking, container hacking
- Apply cloud computing security measures
- Use various cloud computing security tools

---

## Cloud Computing Concepts

### Introduction to Cloud Computing

- **Definition:** On-demand delivery of IT capabilities (infrastructure, applications) as metered services over a network.
- **Examples:** Gmail, Facebook, Dropbox, Salesforce.com

### Characteristics of Cloud Computing

| Characteristic | Description |
|----------------|-------------|
| On-demand self-service | Provision resources without human interaction with provider |
| Distributed storage | Better scalability, availability, reliability (but security/compliance concerns) |
| Rapid elasticity | Instant scaling up/down according to demand |
| Automated management | Reduces labor costs and human error |
| Broad network access | Available via laptops, mobile phones, PDAs |
| Resource pooling | Multi-tenant environment; resources dynamically assigned/reassigned |
| Measured service | Pay-per-use metering (subscription or usage-based) |
| Virtualization technology | Enables rapid scaling |

### Limitations of Cloud Computing

- Limited control and flexibility
- Outages and technical issues
- Security, privacy, compliance issues
- Contracts and lock-ins
- Dependence on network connections
- Vulnerability to attacks (every component online)
- Difficulty migrating between providers

---

## Types of Cloud Computing Services

| Service | Description | Examples | Advantages | Disadvantages |
|---------|-------------|----------|------------|----------------|
| **IaaS** (Infrastructure-as-a-Service) | On-demand IT resources (computing power, virtualization, storage, network) | Amazon EC2, Microsoft OneDrive, Rackspace | Dynamic scaling, guaranteed uptime, ELB, global accessibility | Software security risk, performance issues |
| **PaaS** (Platform-as-a-Service) | Development tools, configuration management, deployment platforms | Google App Engine, Salesforce, Microsoft Azure | Simplified deployment, lower security risk than IaaS, scalability | Vendor lock-in, data privacy |
| **SaaS** (Software-as-a-Service) | Application software on-demand over Internet | Google Docs, Salesforce CRM | Low cost, easy administration, global accessibility | Security/latency issues, Internet dependency |
| **IDaaS** (Identity-as-a-Service) | Authentication services (SSO, MFA, IGA) | OneLogin, Microsoft Azure AD, Okta | Low cost, improved security, central management | Account hijacking vulnerability |
| **SECaaS** (Security-as-a-Service) | Security services (pen testing, IDS, anti-malware, SIEM) | eSentire MDR, Foundstone | Low cost, continuous protection, updated tools | Increased attack surfaces, insecure APIs |
| **CaaS** (Container-as-a-Service) | Containers and clusters as service; virtualization of container engines | Amazon ECS, Google Kubernetes Engine (GKE) | Portable, low cost, high scalability, improved security | High operational overhead |
| **FaaS** (Function-as-a-Service) | Serverless architecture; develop/run/manage app functionalities | AWS Lambda, Google Cloud Functions, Azure Functions | Pay-per-use, low cost, easy deployment, high scalability | High latency, memory limitations, vendor lock-in |
| **XaaS** (Anything-as-a-Service) | Anything as service over Internet based on demand | NetApp, AWS Elastic Beanstalk | Highly scalable, fault tolerance, reduced CAPEX | Service outage risk, performance issues |
| **FWaaS** (Firewalls-as-a-Service) | Filter network traffic; malware detection, packet filtering, IPsec | Zscaler Cloud Firewall, Fortinet | Blocks malicious web traffic, improved network visibility | Network latency issues |
| **DaaS** (Desktop-as-a-Service) | On-demand virtual desktops and apps | Amazon WorkSpaces, Azure Windows Virtual Desktop | Global accessibility, simplified management, low cost | Security issues, network connectivity |
| **MBaaS** (Mobile Backend-as-a-Service) | Integrate front-end apps with backend via API/SDK | Google Firebase, AWS Amplify | Improved development efficiency, flexibility, scalability | Security issues, high initial costs |
| **MaaS** (Machines-as-a-Service/EaaS) | Sell or lease machines; receive percentage of profits | Various industrial implementations | Low investment cost, improved adaptability | Expensive maintenance |

---

## Shared Responsibilities in Cloud

- **Separation of duties** prevents conflict of interest, fraud, abuse, error.
- **IaaS:** Customer responsible for OS, apps, data; provider responsible for infrastructure.
- **PaaS:** Customer responsible for apps, data; provider responsible for OS, runtime, infrastructure.
- **SaaS:** Customer only responsible for data; provider responsible for everything else.

---

## Cloud Deployment Models

| Model | Description | Advantages | Disadvantages |
|-------|-------------|------------|----------------|
| **Public Cloud** | Provider makes services available to public over Internet | Simplicity, low cost, no maintenance | Security not guaranteed, lack of control, slow speed |
| **Private Cloud** | Single organization; within corporate firewall | Security enhancement, high performance, customizable | High cost, on-site maintenance |
| **Community Cloud** | Shared among organizations with common concerns | Less expensive than private, flexible, scalable | Competition for resources, moderate security |
| **Hybrid Cloud** | Combination of two or more clouds (private, public, community) | High scalability, high security, cost management | Network communication conflicts, complex SLAs |
| **Multi Cloud** | Combines workloads across multiple cloud vendors | High reliability, low latency, cost optimization, low vendor lock-in | Operational overhead, security risks |
| **Distributed Cloud** | Geographically distributed public/private clouds on single control plane | High performance, reduced latency, edge computing | High cost, limited software assistance |
| **Poly Cloud** | Holds several types of cloud services supplied to different clouds | High flexibility, cost effective, specialized AI/ML services | Time-consuming initial setup, not affordable for small/medium companies |

---

## NIST Cloud Deployment Reference Architecture

**Five significant actors:**

| Actor | Description |
|-------|-------------|
| **Cloud Consumer** | Person/organization that uses cloud computing services |
| **Cloud Provider** | Acquires/manages computing infrastructure for providing services |
| **Cloud Carrier** | Intermediary providing connectivity and transport services |
| **Cloud Auditor** | Independent examiner of cloud service controls |
| **Cloud Broker** | Manages cloud services (use, performance, delivery); maintains relationship between CSP and consumer |

**Cloud Broker services:**
- **Service Intermediation:** Improves function by specific capability
- **Service Aggregation:** Combines multiple services into new services
- **Service Arbitrage:** Chooses services from multiple agencies (similar to aggregation without fixing)

---

## Cloud Storage Architecture

- **Layers:** Front-end (API for data management), Middleware (de-duplication, replication), Back-end (hardware)
- **Fault-tolerant** through redundancy, data replication, high durability
- **Object storage services:** Amazon S3, Oracle Cloud Storage, Microsoft Azure Storage, OpenStack Swift

---

## Cloud vs. Fog Computing vs. Edge Computing

| Feature | Cloud Computing | Fog Computing | Edge Computing |
|---------|----------------|---------------|----------------|
| Architecture | Centralized | Decentralized (millions of nodes) | Distributed/decentralized (billions of endpoints) |
| Speed | Higher access speed than fog | Higher speed than cloud | Higher speed than fog |
| Latency | High latency | Low latency | Low latency |
| Security | Less secure than fog | Highly secure | Customized security |
| Responsiveness | Low | High | High |

**Fog Computing:** Distributed environment between data sources and cloud; intelligent gateway; used for smart cities, smart grids, connected cars, real-time analytics.

**Edge Computing:** Subset of fog computing; processing at edge devices (programmable automation controllers); used for millisecond-response operations.

---

## Cloud Computing vs. Grid Computing

| Feature | Cloud Computing | Grid Computing |
|---------|----------------|----------------|
| Architecture | Client-server | Distributed computing |
| Scalability | Higher | Standard |
| Resource usage | Centralized | Collaborative |
| Ownership | Infrastructure providers | Organization owns/manages grids |
| Payment | Pay-as-you-go | No payment for usage |
| Interoperability | Not supported (vendor lock-in) | Supported |

---

## Cloud Service Providers

| Provider | Description |
|----------|-------------|
| **Amazon Web Services (AWS)** | On-demand cloud computing; CPU, GPU, RAM, HDD storage, OS, applications, networking |
| **Microsoft Azure** | Building, testing, deploying, managing applications; SaaS, PaaS, IaaS; computing, mobile storage, ML, IoT |
| **Google Cloud Platform (GCP)** | IaaS, PaaS, serverless; computing, data storage/analytics, ML, networking, big data, AI, IoT |
| **IBM Cloud** | IaaS, SaaS, PaaS; public, private, hybrid; computing, networking, storage, AI, IoT, blockchain |

---

## Container Technology

### What is a Container?

- Package of application/software including all dependencies (libraries, config files, binaries)
- Runs independently of other processes in cloud environment
- Delivered as **CaaS** (Container-as-a-Service)

**Features:**
- **Portability and consistency:** Runs on various platforms, private/public cloud
- **Security:** Infections don't extend across containers
- **High efficiency & cost effectiveness:** Fewer resources than VMs; no independent OS needed
- **Scalability:** Integrate more similar containers under same cluster
- **Robustness:** Generated, deployed, destroyed in seconds

### Container Technology Architecture (5 tiers)

1. Developer machines (image creation, testing)
2. Testing/accreditation systems (verification, validation, signing)
3. Registries (storing, disseminating images)
4. Orchestrators (transforming images to containers, deploying to hosts)
5. Hosts (operating/managing containers)

**Container Lifecycle Phases:**
1. Image Creation, Testing, Accreditation
2. Image Storage and Retrieval (registries: Docker Hub, Amazon ECR, Docker Trusted Registry)
3. Container Deployment and Management (orchestrators: Kubernetes, Docker Swarm, Nomad, Mesos)

### Containers vs. Virtual Machines

| Feature | Containers | Virtual Machines |
|---------|------------|------------------|
| OS | Share host OS kernel | Each VM has its own OS |
| Size | MBs | GBs |
| Boot time | Seconds | Minutes |
| Isolation | Process-level | Full hardware isolation |

---

## Docker

### What is Docker?

- Open-source technology for developing, packaging, running applications in containers
- Provides PaaS through OS-level virtualization
- Containers isolated from each other; communicate via well-defined channels

### Docker Engine Components

- **Server:** Daemon process (dockerd)
- **Rest API:** Communication with daemon
- **Client CLI:** Command-line interface for Docker commands

### Docker Swarm

- Docker engine supports swarm mode for managing multiple Docker engines
- Features: container communication, scaling, health checks, failover/redundancy, timely updates

### Docker Architecture

| Component | Description |
|-----------|-------------|
| **Docker Daemon (dockerd)** | Processes API requests; handles containers, volumes, images, networks |
| **Docker Client** | Primary user interface; communicates via Docker API |
| **Docker Registries** | Store images (Docker Hub, Docker Cloud) |
| **Docker Objects** | Images (read-only templates), Containers (runnable instances), Services (swarm), Networking (communication), Volumes (persistent storage) |

### Docker Operations

- Building new image from Dockerfile
- Listing local images
- Tagging existing image
- Pulling/pushing images from/to registry
- Searching for existing images

---

## Microservices vs. Docker

- **Monolithic applications** broken down into **microservices** (each performs unique task)
- Each microservice packaged into Docker container with required libraries, frameworks, config files
- Microservices belonging to single application can be developed/managed using multiple platforms

---

## Docker Networking

- **Container Network Model (CNM):** Provides application portability across heterogeneous infrastructures

**CNM constructs:**
- **Sandbox:** Container network stack configuration (interfaces, routing tables, DNS)
- **Endpoint:** Connected to network; abstracted from application
- **Network:** Interconnected collection of endpoints

**CNM driver interfaces:**
- **Network Drivers:** Native (host, bridge, overlay, macvlan, none) and remote (Contiv, Weave, Kuryr)
- **IPAM Drivers:** Assign default subnet and IP addresses

**Native network drivers:**
| Driver | Description |
|--------|-------------|
| Host | Container uses host networking stack |
| Bridge | Creates Linux bridge managed by Docker |
| Overlay | Container communication over physical network |
| MACVLAN | Uses Linux MACVLAN bridge mode |
| None | Own networking stack; isolated from host |

---

## Container Orchestration

- **Definition:** Automated process of managing lifecycles of software containers and dynamic environments
- **Tasks automated:**
  - Provisioning/deployment of containers
  - Failover/redundancy
  - Creating/destroying containers for load distribution
  - Moving containers between hosts
  - Automatic resource allocation
  - Load balancing, traffic routing, service discovery
  - Health checks
  - Securing container communication

---

## Kubernetes (K8s)

- Open-source, portable, extensible orchestration platform by Google
- Provides resilient framework for managing distributed containers, deployment patterns, failover/redundancy

**Features:**
- Service discovery (DNS name or IP)
- Load balancing
- Storage orchestration (local/public cloud storage)
- Automated rollouts/rollbacks
- Automatic bin packing (allocate/deallocate resources)
- Self-healing (health checks, replace failed containers)
- Secret/configuration management (credentials, SSH keys, OAuth tokens)

### Kubernetes Cluster Architecture

**Master Components:**
- **Kube-apiserver:** Front-end for control panel; only component that interacts with etcd cluster
- **Etcd cluster:** Distributed key-value storage for cluster data, service discovery, API objects
- **Kube-scheduler:** Scans new pods, allocates nodes based on resource requirements, locality, restrictions
- **Kube-controller-manager:** Runs controllers (node, endpoint, replication, service account/token)
- **cloud-controller-manager:** Runs controllers for cloud provider communication

**Node Components:**
- **Kubelet:** Service agent on each node; ensures containers in pods are healthy
- **Kube-proxy:** Network proxy; maintains network rules for pod connections
- **Container Runtime:** Docker, rktlet, container, cri-o

### Clusters

- **Definition:** Set of two or more connected nodes running in parallel
- **Types:**
  - **Highly Available (Fail-over):** Multiple nodes; if one fails, another assumes responsibility
  - **Load Balancing:** Workload distributed among nodes; health checks
  - **High-Performance Computing (HPC):** Parallelized tasks for extreme performance

### Container Security Challenges

- Inflow of vulnerable source code
- Large attack surface
- Lack of visibility
- Compromising secrets
- DevOps speed (containers executed and removed quickly)
- Noisy neighboring containers (resource exhaustion → DoS)
- Container breakout to host (privilege escalation)
- Network-based attacks
- Bypassing isolation
- Ecosystem complexity (multiple vendors/sources)
- Misconfigurations
- Isolation breakdowns
- Insecure communication
- Insufficient logging/monitoring
- Patch management difficulties
- Persistent storage security
- Container orchestration security
- Kernel exploits (shared host OS kernel)
- Cgroups misconfiguration (resource contention, DoS)
- Pod Security Policies (PSP) configuration complexity
- Compliance audit risks

### Container Management Platforms

- Portainer, Apache Mesos, Amazon ECS, Microsoft Azure Container Instances, Red Hat OpenShift, Docker CLI

### Kubernetes Platforms

- Mirantis Kubernetes Engine (MKE), Google Kubernetes Engine (GKE), Amazon EKS, IBM Cloud Kubernetes Service, Docker Kubernetes Service (DKS)

---

## Serverless Computing (FaaS)

- **Definition:** Cloud-based application architecture where infrastructure and supporting services provided by cloud vendor as needed
- Developer only develops and uploads code; provider handles provisioning, scaling, load balancing, security, patch management

**Advantages:**
- High scalability, faster deployment
- Reduced infrastructure cost
- No server management, pay-per-use
- Reduced latency, quicker provisioning, low failure risk

**Disadvantages:**
- Increased security vulnerability
- Vendor lock-in
- Difficulty managing statelessness
- Complex end-to-end testing
- Unsuitable for long-running processes

### Serverless vs. Containers

| Feature | Containers | Serverless |
|---------|------------|------------|
| Configuration | Developer defines OS, software, libraries, storage, networking | Developer only develops/upload code |
| Runtime | Runs continuously until stopped | Destroyed automatically after execution |
| Server support | Needs server even when idle | No charges when not in use |
| Time restriction | No timeout | Timeout enabled |
| Temporary storage | Supported | Not supported; uses object storage |
| Language selection | Developer chooses | Restricted by CSP |

### Serverless Computing Frameworks

- Microsoft Azure Functions (fully automated, scaling based on workload)
- AWS Lambda, Google Cloud Functions, Serverless Framework, AWS Fargate, Alibaba Cloud Function Compute

---

## Cloud Computing Threats

### OWASP Top 10 Cloud Security Risks

| Risk | Description |
|------|-------------|
| R4 - Business Continuity & Resiliency | Risk if cloud provider handles business continuity improperly |
| R5 - User Privacy & Secondary Data Usage | Social websites store data in cloud; default share features jeopardize privacy |
| R6 - Service & Data Integration | Unsecured data in transit susceptible to eavesdropping/interception |
| R7 - Multi-tenancy & Physical Security | Inadequate logical segregation leads to tenant interference |
| R8 - Incident Analysis & Forensic Support | Event logs distributed across multiple hosts/countries; forensic recovery problems |
| R9 - Infrastructure Security | Misconfiguration allows network scanning, default passwords, open ports |
| R10 - Non-Production Environment Exposure | Unauthorized access, information disclosure via non-production environments |

### OWASP Top 10 Kubernetes Risks

| Risk | Description |
|------|-------------|
| K01: Insecure Workload Configurations | Running containers with root privileges, no resource limits, excessive network access |
| K02: Supply Chain Vulnerabilities | Vulnerabilities in container images, dependencies, CI/CD pipelines |
| K03: Overly Permissive RBAC Configurations | Excessive permissions to users/services → privilege escalation |
| K04: Lack of Centralized Policy Enforcement | Inconsistent security policies across clusters |
| K05: Inadequate Logging & Monitoring | Difficulty detecting, investigating, responding to incidents |
| K06: Broken Authentication Mechanisms | Weak password policies, improper MFA configuration |
| K07: Missing Network Segmentation Controls | Lack of isolation between components → lateral movement |
| K08: Secrets Management Failures | Hardcoded secrets, unsecured storage |
| K09: Misconfigured Cluster Components | Default settings, lack of hardening, manual errors |
| K10: Outdated & Vulnerable Kubernetes Components | Known vulnerabilities in outdated components |

### OWASP Top 10 Serverless Security Risks

| Risk | Description |
|------|-------------|
| A1: Injection | SQL/NoSQL/OS/code injection via various event sources (cloud storage, stream data, database, email, IoT) |
| A2: Broken Authentication | Serverless functions stateless; accessing functions without authentication |
| A3: Sensitive Data Exposure | Plaintext storage, weak encryption, writing to /tmp without removal |
| A4: XML External Entities (XXE) | Affects designated container where function is running |
| A5: Broken Access Control | Over-privileged functions grant unauthorized access |
| A6: Security Misconfiguration | Long timeout, low concurrency limit → DoS |
| A7: Cross-Site Scripting (XSS) | Untrusted input from emails, logs, cloud storage, IoT |
| A8: Insecure Deserialization | Python, NodeJS, JSON deserialization vulnerabilities |
| A9: Using Components with Known Vulnerabilities | Vulnerable third-party libraries |
| A10: Insufficient Logging & Monitoring | Complex auditing; late security incident identification |

---

## Cloud Computing Threats (Detailed)

### Data Security

**Data Breach/Loss:**
- Causes: Data erased/modified/lost, encryption keys lost/stolen, improper authentication, CSP data misuse
- **Countermeasures:** Encrypt data at rest and in transit; strong key generation/storage/management; MFA; secure backups; DLP software; CASBs; micro-segmentation; perimeter firewall

**Loss of Operational/Security Logs:**
- **Countermeasures:** Effective policies; regular monitoring; safe log management system; restrict file-level access; secure log transfer protocols

**Malicious Insiders:**
- **Countermeasures:** Strict supply chain management; comprehensive supplier assessment; transparency in security practices; security breach notification processes

**Illegal Access to Cloud Systems:**
- **Countermeasures:** Robust IS policy; permit clients to audit CSP policies

**Loss of Business Reputation Due to Co-tenant Activities:**
- **Countermeasures:** Choose well-known CSP; check virtualization/isolation techniques; assess multi-tenant risks

**Loss of Encryption Keys:**
- **Countermeasures:** Don't store keys with encrypted data; use AES/RSA; restrict key store access; role separation; secure backup/recovery; don't reuse keys; use HSM

**Theft of Computer Equipment:**
- **Countermeasures:** Physical security (guards, CCTV, alarms, ID cards, fencing); biometric entries; intrusion alarms; locked server rooms; rack-mounted servers; off-site backup storage

**Loss/Modification of Backup Data:**
- **Countermeasures:** Data restoration procedures; 3-2-1 backup model

**Improper Data Handling and Disposal:**
- **Countermeasures:** VPN for client data; encrypt data; set data storage period; data destruction process; data sanitization; document sanitization steps

### Cloud Service Misuse

**Abuse/Nefarious Use of Cloud Services:**
- **Countermeasures:** Robust registration/validation; monitor client traffic; monitor/block malicious networks; advanced credit-card fraud monitoring; per-tenant firewalls

**Undertaking Malicious Probes or Scans:**
- **Countermeasures:** Firewalls, IDS; don't place hypervisor and VMs on same network; separate hypervisor management via VLAN; block ping/traceroute replies; properly configure management interfaces

### Interface and API Security

**Insecure Interfaces and APIs:**
- Risks: Circumvent user-defined policies, non-credential leakproof, breach in logging, unknown API dependencies, reusable passwords/tokens, insufficient input validation
- **Countermeasures:** Analyze security model; secure authentication/access controls; encrypt data in transit; use OCCI/CIMI frameworks; network monitoring; never reuse API keys; encrypt all API traffic; authenticate all API calls

### Operational Security

**Insufficient Due Diligence:**
- **Countermeasures:** Research risks and CSP due diligence; train employees; CSP incident response plan; communication regarding DR plans, encryption strategies, security policies; stringent security policies with top management

**Shared Technology Issues:**
- **Countermeasures:** Security best practices for installation/configuration; monitor environment; secure authentication/access control; enforce SLA for patching; vulnerability scanning; strict security at every level; per-tenant firewalls; proper file permissions

**Unknown Risk Profile:**
- **Countermeasures:** Disclosure of logs/data to customers; partial/full disclosure of infrastructure details; monitoring and alerting

**Unsynchronized System Clocks:**
- **Countermeasures:** NTP; time server within firewall; network time system

**Inadequate Infrastructure Design & Planning:**
- **Countermeasures:** Forecast demand; plan sufficient infrastructure; rely on workload reliability/uptime requirements

**Conflicts between Client Hardening Procedures and Cloud Environment:**
- **Countermeasures:** Clear segregation of responsibilities; client visibility of workload/data; periodic cloud VAPT testing

**Cloud Provider Acquisition:**
- **Countermeasures:** Choose reputed CSP; verify data policies; review security capabilities; ensure SLAs cover mission objectives, success measures, data collection

**Network Management Failure:**
- **Countermeasures:** Adequate security policy; proactive network management; update technologies; network design following IT governance; stringent network monitoring; secured VPN for Wi-Fi traffic; cloud network security monitoring tools

**Loss of Governance:**
- **Countermeasures:** Persistent efforts for SLA execution; strict governance rules; unified governance policy for on-premises and cloud operations; automation for compliance verification

**Compliance Risks:**
- **Countermeasures:** CSP ensure client data not compromised; review CSP internal audit processes

**Economic Denial of Sustainability (EDoS):**
- **Countermeasures:** Reactive/on-demand in-cloud EDoS mitigation service (scrubber service); client-puzzle approach

**Limited Cloud Usage Visibility:**
- **Countermeasures:** Cloud-native monitoring/logging; frequent audits; strict access policies and MFA; automated alerts; CSPM tools

### Infrastructure and System Configuration

**Natural Disasters:**
- **Countermeasures:** Safe area location; backups at different locations; mitigation measures; business continuity/disaster recovery plan

**Hardware Failure:**
- **Countermeasures:** Physical security programs; pre-installed standby hardware; automate identification/backup; redundant workload components

**Supply-Chain Failure:**
- **Countermeasures:** Controls to mitigate risks; containment plan; visibility mechanisms; procuring third parties with security posture info; dedicated skilled professionals; blockchain/Hyperledger; digital signatures, MFA, secure session management; zero-trust architecture

**Isolation Failure:**
- **Countermeasure:** Keep memory, storage, network access isolated

**Cloud Service Termination or Failure:**
- **Countermeasures:** CSP define auditable termination procedures; secure data transfer; cleansing process; stringent service agreements for exit process; secured data deletion procedure

**Weak Control Plane:**
- **Countermeasures:** Enforce MFA; continuous monitoring/auditing; secure APIs; regular secure configurations; RBAC

### Network Security

**Modifying Network Traffic:**
- **Countermeasure:** Network traffic analysis with special tools

**Management Interface Compromise:**
- **Countermeasures:** Keep memory, storage, network access isolated; secure protocols for remote access; regular patches; dedicated VLAN for management interfaces; jump servers

**Authentication Attacks:**
- **Countermeasures:** Strong password policies; two-factor authentication; IP whitelisting; least privilege; robust IAM

**VM-Level Attacks:**
- **Countermeasures:** IDS/IPS, firewall; highly configured/updated hypervisors; sandboxes; High Assurance Platform (HAP); ensure no valid VM user shares hardware

**Hijacking Accounts:**
- **Countermeasures:** Minimal access privileges; defense-in-depth; IAM solutions; encrypt sensitive information; MFA; remove unused credentials; third-party access control; cloud tokenization; password manager

### Governance and Legal Risks

**Lock-in:**
- **Countermeasures:** Standardized cloud API; multi-cloud/hybrid cloud strategy; portable and loosely coupled applications; DevOps tools; clear exit strategy

**Licensing Risks:**
- **Countermeasures:** Review CSP licensing state; centralized platform for cost/licensing management; eliminate unused cloud resources

**Risks from Changes of Jurisdiction:**
- **Countermeasure:** Gain insight about jurisdictions; assess risks

**Subpoena and E-Discovery:**
- **Countermeasures:** Carefully select CSP; review service agreement; coordinated eDiscovery plan; exit strategy

### Development and Resource Management

**Privilege Escalation:**
- **Countermeasures:** Good privilege separation scheme; regular software updates; audit IAM regulations; scan for exposed APIs (Shodan); monitor suspicious traffic

**Insecure Software Development Practices:**
- **Countermeasures:** Integrate security via SDLC; developer training in secure coding; code reviews, automated testing; access controls; secure coding guidelines

**Resource Exhaustion:**
- **Countermeasures:** Monitor resource usage; auto-scaling/load balancing; rate limiting; firewalls/anti-DoS tools; optimize application performance

**Lack of Security Architecture:**
- **Countermeasures:** Align security architecture with business goals; update threat model; periodic security assessment

---

## Container Vulnerabilities

| Vulnerability | Description |
|---------------|-------------|
| Impetuous Image Creation | Careless creation without security safeguards |
| Insecure Image Configurations | Outdated/unnecessary software increases attack surface |
| Unreliable Third-Party Resources | Untrusted resources vulnerable to malicious attacks |
| Unauthorized Access | Leads to privilege escalation |
| Insecure Container Runtime Configurations | Improper configuration, mounting sensitive directories |
| Data Exposure in Docker Files | Passwords, SSH keys exposed |
| Embedded Malware | Malware embedded after creation or downloaded after deployment |
| Non-Updated Images | Security loopholes and bugs |
| Hijacked Repository & Infected Resources | Unauthorized access alters/deletes files |
| Hijacked Image Registry | Mismanaged configurations compromise registry |
| Exposed Services due to Open Ports | Port scanning reveals sensitive information |
| Exploited Applications | SQLi, XSS, RFI |
| Mixing of Workload Sensitivity Levels | Public web server vulnerability threatens sensitive containers |

---

## Kubernetes Vulnerabilities

| Vulnerability | Description |
|---------------|-------------|
| No Certificate Revocation | Must regenerate entire certificate chain; attackers exploit before replacement |
| Unauthenticated HTTPS Connections | PKI used but TLS authentication not proper; unauthorized access to kubectl-managed Pods |
| Exposed Bearer Tokens in Logs | Bearer tokens logged in kube-apiserver; attackers with log access impersonate legitimate users |
| Exposure of Sensitive Data via Environment Variables | Attackers access stored values via environment logging |
| Secrets at Rest not Encrypted by Default | Attackers accessing etcd retrieve unencrypted secrets |
| Non-constant Time Password Comparison | Kube-apiserver doesn't perform secure comparison; timing attacks |
| Hardcoded Credential Paths | Attackers insert malicious token and root CA if stored in different locations |
| Log Rotation is not Atomic | Kubelet logs erased if restarted during rotation; attackers monitor and remove logs |
| No Back-off Process for Scheduling | Tight loop as scheduler continuously schedules rejected pods |
| No Non-repudiation | Debug mode disabled → no user action recording; attackers directly interact with kube-apiserver |

---

## Cloud Attacks

### Service Hijacking using Social Engineering

- Attacker steals CSP/client credentials via phishing, pharming, social engineering, software vulnerabilities
- **Process:** Create fake cloud login page → send malicious link → user enters credentials → attacker receives credentials → page redirects to real login page → attacker uses stolen credentials
- **Countermeasures:** Don't share credentials; MFA; train staff; follow security policies; encrypt data; least privilege; divide responsibilities

### Service Hijacking using Network Sniffing

- Intercept/monitor network traffic between cloud nodes
- **Countermeasures:** Encrypt sensitive data over network and in config files; detect NICs in promiscuous mode; SSL/TLS for web traffic

### Side-Channel Attacks (Cross-guest VM Breaches)

- Attacker places malicious VM near target cloud server on same physical host
- Exploits shared physical resources (processor cache) to steal cryptographic keys/plaintext secrets
- **Techniques:** Timing attack, data remanence, acoustic cryptanalysis, power monitoring, differential fault analysis
- **Countermeasures:** Virtual firewall; random encryption/decryption (RSA, 3DES, AES); lockdown OS images; monitor repeated access attempts; code applications for consistent shared resource access

### Wrapping Attack

- Performed during SOAP message translation in TLS layer
- Attacker duplicates message body and sends to server as legitimate user
- Server checks signature value (duplicated) and verifies integrity
- **Countermeasures:** XML schema validation; authenticated encryption in XML encryption; improve interface between signature verification and business logic; WS-SecurityPolicy "SignedParts"; CryptoCoverageChecker interceptor

### Man-in-the-Cloud (MITC) Attack

- Advanced version of MITM
- Abuses cloud file synchronization services (Google Drive, Dropbox) for data compromise, C&C, data exfiltration, remote access
- **Process:** Victim installs malware → malware plants attacker's synchronization token on victim's drive → victim's Drive syncs with attacker's account → attacker steals victim's token → accesses victim's files → restores original token (stays undetected)
- **Countermeasures:** Email security gateway; harden token expiration policies; antivirus; CASB; monitor employee activities; encrypt data; don't store keys in same cloud; 2FA

### Cloud Hopper Attack

- Triggered at Managed Service Providers (MSPs) and their customers
- Attackers gain remote access to intellectual property of MSP and global users
- **Methods:** Spear-phishing with custom malware; PowerShell scripting for reconnaissance; C&C sites spoofing legitimate domains; file-less malware
- **Countermeasures:** MFA; mutual coordination between customers and CSPs; follow cloud service policies; data categorization; jump servers

### Cloud Cryptojacking

- Unauthorized use of victim's computer to stealthily mine digital currency
- Leverages: cloud misconfigurations, compromised websites, client/server-side vulnerabilities
- **Process:** Embed malicious crypto-mining script → victim connects to compromised cloud service → script executes → victim mines cryptocurrency for attacker → attacker gets reward
- **Countermeasures:** Strong password policy; 3-2-1 backup; patch webservers/devices; encrypted SSH key pairs; CoinBlocker URL/IP blacklist; real-time monitoring of DOM/JS; latest antivirus/adblocker; browser extensions for miner script scanning; endpoint security management; review third-party components; network monitoring for CPU misuse; monitor sudden price surges in bills; terminate unused cloud instances

### Cloudborne Attack

- Vulnerability in bare-metal cloud server enabling attacker to implant malicious backdoor in firmware
- Backdoor persists even if server reallocated to new clients
- **Target:** Baseboard Management Control (BMC) via IPMI
- **Countermeasures:** Keep firmware up-to-date; sanitize server firmware before reassigning; validate for implants/backdoors; check for firmware vulnerabilities; verify hardware not tampered

### Instance Metadata Service (IMDS) Attack

- IMDS provides information about instance, network, software
- Attacker exploits zero-day vulnerability or reverse proxy leak
- Gains sensitive information (user data, roles) → accesses cloud resources
- **Countermeasures:** Use IMDSv2; turn off IMDS when not required; assign least privileges to roles; restrict IMDS access of suspected users

### Cache Poisoned Denial of Service (CPDoS)/CDN Cache Poisoning Attack

- Attacker creates malformed/oversized HTTP requests → origin web server returns error content → cached at CDN servers → legitimate users receive error pages → DoS
- **Steps:** Attacker requests resource with malicious HTTP header → CDN forwards to origin server → server returns error → error page cached → users receive error page → CDN broadcasts error to other users
- **Countermeasures:** Configure CDN to avoid caching HTTP error pages; WAF; monitor and eliminate error pages from cache

### Cloud Snooper Attack

- Triggered at AWS Security Groups (SGs)
- Exploits weakness in SGs (allow traffic only on ports 80/443)
- **Process:** Attacker sends C2 packets with destination ports 80/443 → firewall allows → rootkit intercepts, recreates packets with source ports 1010,2020,6060,7070,8080,9999 → backdoor executes C2 commands → rootkit reconstructs packets with source ports 80/443 → exfiltrates data
- **Countermeasures:** Regular network traffic analysis; regular patching; layered security model

### Golden SAML Attack

- Targets identity providers on cloud networks (ADFS using SAML)
- Attacker gains administrative access to identity provider → exploits token signing certificates → generates forged SAML tokens/responses
- **Process:** Gain access to ADFS server → steal certificate/encryption key → intercept redirect request → send SAML response with forged assertion using stolen keys → service provider allows access to federated services
- **Countermeasures:** Constantly monitor user activities; MFA; strong passwords; least-privilege access; timely certificate updates

### Living Off the Cloud (LotC) Attack

- Evolution of "living off the land"
- Targets victim's SaaS/IaaS applications for malicious activities (data exfiltration, crypto mining, DDoS)
- **Process:** Gain initial access → lateral movement using native tools (CMD, PowerShell, Certutil) → deliver malware via cloud storage (Dropbox, Google Drive) → C2 using Ngrok → perform malicious activities → blend traffic with legitimate cloud traffic
- **Countermeasures:** Cloud-native single-pass architecture; zero-trust security; allow only corporate instances of cloud storage; employee training; detailed logging; ML/behavioral analytics; application whitelisting; network segmentation; MFA; RBAC

### Other Cloud Attacks

**Session Hijacking using XSS:**
- Attacker hosts malicious script on cloud server → user views page → script runs on user's browser → collects cookies → redirects to attacker's server
- **Countermeasures:** SSL, firewalls, antivirus, code scanners

**Session Hijacking using Session Riding:**
- Attacker "rides" active session via cross-site request forgery → sends email or malicious webpage during login to target site
- **Countermeasures:** Don't save login details in browser; check HTTP referrer header; ignore URL parameters for POST

**DNS Attacks:**
- **DNS Poisoning:** Divert users to spoofed website
- **Cybersquatting:** Register domain name similar to CSP
- **Domain Hijacking:** Steal CSP domain name
- **Domain Snipping:** Register elapsed domain name
- **Countermeasure:** DNSSEC

**SQL Injection Attacks:**
- **Countermeasures:** Filtering techniques (sanitize user input); validate input length, range, format, type; regular updates/patches; database monitoring, IPS; cloud-based WAF

**Cryptanalysis Attacks:**
- Insecure/obsolete encryption; weak random number generation; monitoring client's query access patterns
- **Countermeasures:** Cryptographically secure random number generators; avoid faulty algorithms; latest strongest encryption (salting, hashing)

**DoS/DDoS Attacks:**
- Attacker floods server with multiple requests or malicious input
- **Countermeasures:** Least privilege concept; IDS in physical and virtual machines

**Man-in-the-Browser Attack:**
- Inject malware into user's web browser → monitor information between browser and cloud application → exfiltrate credentials
- **Countermeasures:** Limit access to cloud services; integrate with controlled IDS; limit IP address range; offer services only via VPN

**Metadata Spoofing Attack:**
- Modify service metadata in WSDL file → cloud users redirected to unknown places
- **Countermeasures:** Encrypt and store application/service details; hash-based integrity checking; deactivate unsafe metadata versions; host-based firewalls to restrict instance metadata API access

**Cloud Malware Injection Attack:**
- Install malicious service implementations or VMs into cloud services (SaaS, PaaS, IaaS)
- **Countermeasures:** Encrypt data; verify AWS IaaS instance IDs and user signatures; create separate virtual zones for different user segments

**Multi-Cloud Attack:**
- Leverage vulnerabilities across multiple CSPs (misconfigurations, weak access controls, compromised credentials)
- **Countermeasures:** Secure APIs; encrypted channels; standardized access control models; MFA; automated policy synchronization; regular audits, continuous monitoring

**Privilege Escalation with CSR API:**
- Attacker creates CSR requesting certificate from service account with elevated permissions → leverages poorly configured security controls → obtains CSR approval → Kubernetes issues certificate → attacker authenticates with elevated permission
- **Countermeasures:** Enable Kubernetes auditing; enforce strict RBAC policies; manual review/approval of CSRs

**Privilege Escalation by Abusing Elevation Control Mechanism (JIT access):**
- Abuse permission configurations (just-in-time access, impersonation, resource role assignment, temporary role access)
- Example: AWS PassRole permission; GCP iam.serviceAccountUser role
- **Countermeasures:** Limit privileges to necessary roles/policies; manual approval for temporary elevation; segment/isolate critical resources

---

## Cloud Malware

### Cuttlefish Zero-Click Malware

- Packet-sniffing malware; masquerades as legitimate software
- Infiltrates SOHO/enterprise routers
- Spreads via bash script to collect host-based data → sends to C2 server
- Installs packet filter to inspect outbound connections, monitor cloud traffic
- Hijacks DNS and HTTP traffic going to private IP addresses
- Activates cloud sniffer to steal credentials

**Other cloud malware:** Denonia, LemonDuck, RansomCloud, DBatLoader/ModiLoader, Goldbackdoor

---

## Cloud Hacking Methodology

**Four phases:**
1. Information Gathering
2. Vulnerability Assessment
3. Exploitation
4. Post-Exploitation

| Phase | Description |
|-------|-------------|
| **Information Gathering** | Collect data about target cloud infrastructure (network topology, IP addresses, domains, subdomains, user accounts). Tools: Nmap, Shodan, Reconng |
| **Vulnerability Assessment** | Identify/evaluate security weaknesses (misconfigurations, unpatched software, flaws). Tools: Tenable Nessus, OpenVAS, Qualys |
| **Exploitation** | Actively exploit vulnerabilities to gain unauthorized access. Tools: Metasploit, sqlmap, thc-hydra |
| **Post-Exploitation** | Maintain access, cover tracks, explore deeper. Create backdoors, escalate privileges, C2 channels. Tools: Cobalt Strike, Metasploit |

**Note:** Ethical hacking in cloud environment typically feasible only through internal means; notify cloud provider before operations.

---

## Identifying Target Cloud Environment

**Shodan search filters:**

| Filter | Purpose |
|--------|---------|
| `port:443` | HTTPS services for web services in cloud |
| `ssl.cert.issuer.cn:Amazon` | AWS-hosted services |
| `cloud.region:<region_code>` | Specific cloud region |
| `org:Microsoft` | Microsoft devices/services (Azure) |
| `product:Kubernetes` | Kubernetes instances |
| `org:Amazon` | AWS-hosted services |
| `ssl.cert.subject.cn:azure` | Azure-hosted services |
| `tag:cloud` | Any cloud asset (enterprise only) |
| `net:52.0.0.0/8` | AWS IP range |
| `http.html:"s3.amazonaws.com"` | AWS S3 buckets |
| `Amazon web services Facebook` | AWS services used by Facebook |

---

## Discovering Open Ports and Services using Masscan

- Network port scanner for large networks; scans entire Internet in minutes
- **Command:**
  ```bash
  sudo masscan -p0-65535 <target_IP> --rate=<rate>
  ```
- **Save results:**
  ```bash
  sudo masscan -p0-65535 <target_IP> --rate=<rate> -oX <scan_results>.xml
  sudo masscan -p0-65535 <target_IP> --rate=<rate> -oJ scan_results.json
  ```

---

## Vulnerability Scanning using Prowler

- Contains 240+ controls (CIS, NIST, PCI-DSS, GDPR, HIPAA, SOC2, etc.)
- **Commands:**
  ```bash
  prowler <provider>                          # Start scanning
  prowler <provider> -M csv json-asff json-ocsf html   # Generate report
  prowler azure --checks storage_blob_public_access_level_is_disabled
  prowler aws --services s3 ec2
  prowler gcp --services iam compute
  prowler kubernetes --services etcd apiserver
  prowler aws --profile custom-profile --filter-region <region1> <region2>
  prowler azure --az-cli-auth --subscription-ids <id1> <id2>
  prowler gcp --project-ids <Project_ID1> <Project_ID2>
  ```

---

## Identifying Misconfigurations using CloudSploit

- Identifies misconfigurations: permissive IAM policies, exposed storage buckets, unsecured databases, misconfigured network security groups
- **Configuration files:**
  - AWS: `{"accessKeyId":"...", "secretAccessKey":"..."}`
  - Azure: `{"ApplicationID":"...", "KeyValue":"...", "DirectoryID":"...", "SubscriptionID":"..."}`
  - GCP: `{"type":"service_account", "project":"...", "client_email":"...", "private_key":"..."}`
- **Commands:**
  ```bash
  ./index.js                                    # Standard scan
  ./index.js --compliance=hipaa                 # HIPAA scan
  ./index.js --compliance=pci                   # PCI scan
  ./index.js --compliance=cis                   # CIS scan
  ./index.js --console=text                     # Plain text output
  ./index.js --csv=file.csv --console=table     # CSV + table
  ```

---

## Cleanup and Maintaining Stealth

**Methods:**
- **Log manipulation:** Delete or modify logs to remove malicious entries
- **Removing credentials/access management:** Remove temporary tokens/keys; create hidden backdoors
- **Manipulating system/service configurations:** Eliminate visible changes; disable/modify alerts
- **Implementing persistence mechanisms:** Hide malicious code through legitimate processes/services; use built-in cloud tools/scripts

---

## Enumerating S3 Buckets

### Techniques:

1. **Inspecting HTML:** Analyze source code for URLs to target S3 buckets
2. **Brute-forcing URL:** Use Burp Suite to brute-force bucket names (`http://s3.amazonaws.com/[bucket_name]`)
3. **Advanced Google Hacking:**
   ```
   inurl:s3.amazonaws.com
   inurl:s3.amazonaws.com/audio/
   site:s3.amazonaws.com inurl:facebook
   site:s3.amazonaws.com intitle:facebook
   ```

### S3Scanner
```bash
s3scanner --bucket <filename>
s3scanner --bucket-file <filename>.txt --enumerate
s3scanner --bucket-file names.txt
s3scanner --bucket <filename> --threads 8
```

### BucketLoot (S3 bucket inspector)
```bash
python bucketloot.py -l <file_with_bucket_names>   # List publicly accessible buckets
python bucketloot.py -c <file_with_bucket_names>   # Check permissions
python bucketloot.py -d <file_with_bucket_names>   # Download data
```

### CloudBrute
```bash
cd CloudBrute
./cloudbrute -d <target.com> -k <keyword> -t 80 -T 10 -w </path/to/wordlist>.txt
```
- `-d` target domain
- `-k` keyword
- `-t` threads
- `-T` timeout
- `-w` wordlist

---

## Enumerating EC2 Instances

**AWS CLI commands:**
```bash
aws ec2 describe-instances
aws ec2 describe-instances --filters Name=metadata-options.http-tokens,Values=optional   # Check Metadata API version 1
aws ec2 describe-instance-attribute --instance-id <id> --attribute userData --output text --query "UserData.Value" | base64 --decode
aws ec2 describe-volumes
aws ec2 describe-snapshots
aws ec2 describe-security-groups
aws ec2 describe-security-groups --filters Name=ip-permission.from-port,Values=22 Name=ip-permission.to-port,Values=22 Name=ip-permission.cidr,Values='0.0.0.0/0'
aws ec2 describe-fleet-instances
aws ec2 describe-fleets
aws ec2 describe-hosts
aws ec2 describe-iam-instance-profile-associations
aws iam get-instance-profile --instance-profile-name <profile name>
aws ec2 describe-key-pairs
aws ec2 describe-internet-gateways
aws ec2 describe-local-gateways
aws ec2 describe-nat-gateways
aws ec2 describe-transit-gateways
aws ec2 describe-vpn-gateways
aws ec2 describe-vpcs
aws ec2 describe-subnets
aws ec2 describe-vpc-endpoints
aws ec2 describe-vpc-peering-connections
```

---

## Enumerating AWS RDS Instances

**Permissions required:** `rds:DescribeDBInstances`

```bash
aws rds describe-db-instances
aws rds describe-db-instances --db-instance-identifier mydbinstancecf
aws rds describe-db-security-groups
aws rds describe-db-instance-automated-backups
aws rds describe-db-snapshots
aws rds describe-db-snapshots --include-public --snapshot-type public   # Public snapshots shared across accounts
```

---

## Enumerating AWS Account IDs and IAM Roles

**AWS account ID sources:**
- Publicly shared resources (S3 buckets)
- ARNs in documentation, error messages, logs
- IAM policies/roles shared with external parties

**IAM role enumeration:**
- Failed role assumption attempts reveal existence of roles
- Error message for existent role vs non-existent role

### Principal Mapper (PMapper)
- Visualizes IAM users and roles through directional graph
- Identifies privilege escalation opportunities and attack paths

---

## Enumerating Weak IAM Policies using Cloudsplaining

```bash
# Export IAM policy details
aws iam get-account-authorization-details --output json > account-auth-details.json

# Scan and generate report
cloudsplaining scan --input-file account-auth-details.json --output ./cloudsplaining-report
```
- Generates HTML report highlighting excessive permissions
- **Note:** Doesn't require admin privileges; requires read-only access to IAM policies

---

## Enumerating AWS Cognito

**User Pools:**
```bash
aws cognito-idp list-user-pools
aws cognito-idp describe-user-pool --user-pool-id <UserPoolId>
```

**Identity Pools:**
```bash
aws cognito-identity list-identity-pools
aws cognito-identity describe-identity-pool --identity-pool-id <IdentityPoolId>
```

**Check existing users:**
```bash
aws cognito-idp sign-up --client-id <ClientId> --username <username> --password <password> --user-attributes Name=email,Value=<email>
```

**Permissions required:**
- User Pools: `cognito-idp:ListUserPools`, `cognito-idp:DescribeUserPool`
- Identity Pools: `cognito-identity:ListIdentityPools`, `cognito-identity:DescribeIdentityPool`

---

## Enumerating DNS Records using Ghostbuster

```bash
ghostbuster scan aws --profile <AWS CLI profile name>
```
- Gathers all DNS records from targeted AWS accounts (Amazon Route 53)
- Imports DNS records from CSV or Cloudflare
- Crosschecks DNS records with IPs owned by organization

---

## Enumerating Serverless Resources in AWS (Lambda & DynamoDB)

```bash
aws lambda list-functions
aws lambda get-function --function-name <function_name>
aws lambda get-function-configuration --function-name <function_name>
aws lambda list-function-url-configs --function-name <function_name>
aws lambda get-function-url-config --function-name <function_name>
aws lambda list-event-source-mappings --function-name <function_name>
aws iam list-attached-role-policies --role-name <role_name>
aws dynamodb list-tables
aws dynamodb describe-table --table-name <table_name>
aws dynamodb list-global-tables
aws apigateway get-rest-apis
aws apigateway get-rest-api --rest-api-id <api_id>
```

---

## Discovering Attack Paths using CloudFox

```bash
cloudfox aws --profile <profile-name> all-checks              # Automated enumeration for exploitable attack paths
cloudfox aws -p <profile-name> eni -v2                        # Identify all elastic network interfaces
cloudfox aws --profile <profile-name> -v2 endpoints           # Enumerate vulnerable endpoints
cloudfox aws --profile <profile-name> permissions -v2         # List all IAM permissions available to a principal
cloudfox aws --profile <profile-name> -v2 secrets             # Secrets from SecretsManager and SSM
cloudfox aws --profile <profile-name> workloads               # Workloads with admin permissions
```

---

## Identify Security Groups Exposed to the Internet

**Using AWS CLI:**
```bash
aws ec2 describe-security-groups --filter Name=ip-permission.cidr,Values=0.0.0.0/0,::/0 --filter Name=ip-permission.from-port,Values=<port numbers>
```
- **Permission required:** `ec2:DescribeSecurityGroups` (AmazonEC2ReadOnlyAccess or higher)

**Define unrestricted network access:**
```bash
aws ec2 authorize-security-group-ingress --group-id <security group ID> --protocol <protocol> --port <port number> --cidr 0.0.0.0/0
```

---

## AWS Threat Emulation using Stratus Red Team

- "Atomic Red Team" for cloud; emulates offensive attack techniques
- Supports AWS, GCP, Azure, Kubernetes; maps to MITRE ATT&CK

**Commands:**
```bash
export AWS_PROFILE=my-profile
stratus list --platform AWS --mitre-attack-tactic persistence      # List attack techniques
stratus show <Attack technique>                                    # View details
stratus warmup <Attack technique>                                  # Spin up prerequisite infrastructure
stratus detonate <Attack technique>                                # Detonate attack
stratus status                                                     # Display current state
stratus cleanup <Attack technique>                                 # Clean up
stratus cleanup --all                                              # Clean up all
```

---

## Gathering Cloud Keys Through IMDS Attack

```bash
# Access instance and identify roles
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/

# Add role name as suffix to obtain cloud keys
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/<IAM-Role-Name>
```
- **IPv6 for Nitro EC2 instances:** `fd00:ec2::254`

---

## Exploiting Misconfigured AWS S3 Buckets

**Steps:**
1. **Identify S3 buckets:** Tools: S3Scanner, lazy3, Bucket Finder, s3-buckets-bruteforcer
2. **Setup AWS CLI:** `aws configure`
3. **Extract access keys:** IAM → Users → Add User → Download CSV
4. **Configure aws-cli:** `aws configure`
5. **Identify vulnerable S3 buckets:** `aws s3 ls s3://[bucket_name] --no-sign-request`
6. **Exploit S3 buckets:**
   ```bash
   aws s3 ls s3://[bucket_name] --no-sign-request
   aws s3 mv FileName s3://[bucket_name]/test-file.txt --no-sign-request
   aws s3 cp FileName s3://[bucket_name]/test-file.svg --no-sign-request
   aws s3 rm s3://[bucket_name]/test-file.svg --no-sign-request
   ```

---

## Compromising AWS IAM Credentials

**Vulnerabilities exploited:**

| Vulnerability | Description |
|---------------|-------------|
| Repository Misconfigurations | AWS keys hosted in shared storage (Git repository) exposed |
| Social Engineering | Fake emails, calls, SMSs to trick users into revealing credentials |
| Password Reuse | Same password for multiple services |
| Vulnerabilities in AWS-Hosted Applications | SSRF, reading local files (configs, logs) |
| Exploiting Third-Party Software | Compromise software used to manage cloud services |
| Insider Threat | Disgruntled employees with trusted access |

---

## Hijacking Misconfigured IAM Roles using Pacu

- Open-source AWS exploitation framework
- Contains 1100+ wordlist of commonly used role names
- **Script:**
  ```bash
  assume_role_enum.py [-h] [-p PROFILE] [-w WORD_LIST] -I ACCOUNT_ID
  ```
- Automatically alerts when role identified; auto-assumes misconfigured roles; exposes role credentials

---

## Scanning AWS Access Keys using DumpsterDiver

```bash
DumpsterDiver.py -p /path/to/scan                           # Scan directory
dumpsterDiver -p /path/to/scan -e AWS_KEY                   # Scan for AWS keys
```
- Scans for hardcoded secret keys (AWS access keys, SSL keys, Azure keys)
- Generates report of potential secrets found

---

## Exploiting Docker Containers on AWS using CCAT

**Steps:**
1. **Abuse AWS credentials:** "Enumerate ECR" module to list available ECR repositories
2. **Pull target Docker image:** "Pull Repos from ECR" module
3. **Create backdoor image:** "Docker Backdoor" module (replace default CMD with reverse shell)
4. **Push backdoor Docker image:** "Push Repos to ECR" module

---

## Exploiting Shadow Admins in AWS

- **Shadow admins:** User accounts with specific permissions allowing attackers to penetrate cloud network
- **Techniques:**
  - Elevating Access Permissions: Abuse `Microsoft.Authorization/elevateAccess/Action`
  - Modifying Existing Roles: Abuse `Microsoft.Authorization/roleDefinitions/write`
  - Creating New Accounts: Abuse `Microsoft.Authorization/roleAssignments/write`

### SkyArk
- Contains AwStealth and AzureStealth modules
- Discovers entities with most sensitive and risky permissions

---

## Gaining Access by Exploiting SSRF Vulnerability

**Steps:**
1. **Exploit SSRF** in web application with GET variable `url` to access cloud metadata services (AWS EC2) → retrieve AWS access keys for role
2. **Add credentials to local aws-cli:** `aws configure`
3. **Verify setup:** `aws sts get-caller-identity --profile stolen_profile`
4. **List buckets:** `aws s3 ls --profile stolen_profile`
5. **Download data:** `aws s3 sync s3://bucket-name /home/attacker/localstash/targetcloud/ --profile stolen_profile`

---

## Module Summary

This module covered:

- Cloud computing concepts (characteristics, limitations, service types, deployment models)
- NIST reference architecture (actors: consumer, provider, carrier, auditor, broker)
- Shared responsibilities in cloud (IaaS, PaaS, SaaS)
- Container technology (Docker, container architecture, orchestration, Kubernetes)
- Serverless computing (FaaS, advantages/disadvantages, vs. containers)
- Cloud computing threats (OWASP Top 10 Cloud, Kubernetes, Serverless risks)
- Cloud attacks (service hijacking, side-channel, wrapping, MITC, cloud hopper, cryptojacking, cloudborne, IMDS, CPDoS, cloud snooper, golden SAML, LotC, and others)
- Cloud hacking methodology (information gathering, vulnerability assessment, exploitation, post-exploitation)
- Cloud enumeration techniques (S3 buckets, EC2, RDS, AWS account IDs, IAM roles, Cognito, DNS records, serverless resources)
- Cloud exploitation tools (Masscan, Prowler, CloudSploit, CloudFox, Stratus Red Team, Pacu, DumpsterDiver, CCAT, SkyArk)
- Countermeasures for various cloud attacks

**End of Module 19**
