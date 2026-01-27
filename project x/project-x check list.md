## Prerequisite
---

# LEVEL 0 — Absolute Computing Basics

### You must **understand**, not just use:

- How a computer boots
    
- User space vs kernel space
    
- Processes vs threads
    
- Memory, heap, stack (basic)
    
- File descriptors
    
- Signals
    

 Why: scanners, exploits, agents all rely on this.

---

# LEVEL 1 — Linux & Networking Foundations

_(Your operating environment)_

## Linux

- Filesystem layout
    
- Permissions, ACLs
    
- Capabilities
    
- `/proc`, `/sys`
    
- systemd basics
    
- Logs & auditing
    

## Networking

- OSI vs TCP/IP
    
- TCP handshake
    
- UDP behavior
    
- DNS resolution
    
- TLS handshake
    
- Proxies
    

 Why: scanners are **network programs**.

---

#  LEVEL 2 — Web & HTTP Fundamentals

_(Most security tools live here)_

### Protocols

- HTTP/1.1 vs HTTP/2
    
- Request lifecycle
    
- Headers
    
- Cookies
    
- Sessions
    
- CORS
    

### Auth

- Basic auth
    
- JWT
    
- OAuth2
    
- SSO
    
- Token rotation
    

 Why: bugs live in auth logic.

---

#  LEVEL 3 — Core Web Security

_(Your first real “hacker” layer)_

### OWASP Top 10 (deep, not surface)

- SQLi
    
- XSS
    
- IDOR
    
- CSRF
    
- SSRF
    
- Auth bypass
    
- File upload issues
    

### Concepts

- Input validation
    
- Output encoding
    
- Trust boundaries
    
- Attack surface mapping
    

 Why: detection logic comes from patterns.

---

#  LEVEL 4 — Programming for Security Tools

_(Now you stop being “just a hacker”)_

### Go (primary)

- Goroutines
    
- Channels
    
- Contexts
    
- Custom HTTP clients
    
- Binary building
    

### Python (secondary)

- Scripting
    
- Prototyping
    
- Glue code
    

### Secure coding

- Memory safety
    
- Race conditions
    
- Error handling
    

 Why: your tool must be fast, safe, and auditable.

---

#  LEVEL 5 — Vulnerability Research

_(Understand bugs before exploiting)_

- Reading CVEs
    
- Diffing patches
    
- Root cause analysis
    
- Writing PoCs
    
- Fuzzing basics
    

 Why: scanners must detect _root causes_, not signatures.

---

#  LEVEL 6 — Exploitation (Controlled & Ethical)

_(You need to know this, even if you restrict it)_

- RCE basics
    
- Deserialization flaws
    
- Command injection
    
- Logic exploits
    
- Sandbox escapes (conceptual)
    

⚠️ Focus on **understanding**, not weaponizing.

---

#  LEVEL 7 — Plugin & Architecture Design

_(This separates tools from platforms)_

- Plugin systems
    
- IPC (STDIN/STDOUT, sockets)
    
- Versioning
    
- Sandboxing
    
- WASM basics
    

 Why: your platform must scale beyond you.

---

#  LEVEL 8 — API Security

_(Modern apps = APIs)_

- REST design flaws
    
- OpenAPI parsing
    
- GraphQL abuse
    
- Rate limiting logic
    
- Schema validation
    

---

#  LEVEL 9 — Android Security

_(Only after web is solid)_

- APK structure
    
- Android permissions
    
- Secure storage
    
- Static analysis
    
- Dynamic hooks (Frida)
    

---

#  LEVEL 10 — Cloud & Infra Security

_(This is where money is)_

- AWS/GCP/Azure basics
    
- IAM models
    
- Privilege escalation paths
    
- Metadata services
    
- Terraform scanning
    

---

#  LEVEL 11 — CI/CD & Supply Chain

_(Very underrated)_

- Secrets in pipelines
    
- Dependency confusion
    
- Artifact poisoning
    
- Git security
    

---

#  LEVEL 12 — Detection, Scoring & Reporting

_(Enterprise-grade thinking)_

- Risk scoring
    
- CVSS vs contextual risk
    
- False positive reduction
    
- Report generation
    
- Compliance mapping
    

---

#  LEVEL 13 — Platform Engineering

_(Now you’re a vendor)_

- Backend APIs
    
- Auth & RBAC
    
- Multi-tenant design
    
- Queues & workers
    
- Scaling scans
    

---

#  LEVEL 14 — Legal, Ethics & Trust

_(Without this, you fail)_

- Authorization models
    
- Logging
    
- EULA constraints
    
- Abuse prevention
    
- Responsible disclosure
    

---

#  LEVEL 15 — Community & Open Source

_(Your ideology advantage)_

- Writing docs
    
- Maintainer mindset
    
- Reviewing PRs
    
- Backward compatibility
    
- Governance
    

---

##  How to Use This List

- Don’t rush levels
    
- Build **something small at each level**
    
- Your project will naturally evolve with you
    

---

