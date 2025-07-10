

# 🔐 API – Full Detailed Notes (CEH Focused)

---

## 📌 What is an API?

* **API** (Application Programming Interface) is a **set of protocols and tools** that allows different software components to communicate.
* APIs are used in **web, mobile, and desktop** applications to interact with back-end services or third-party systems.

### Example:

A weather app calls a **weather API** to get temperature data.

---

## 🔧 Types of APIs

| Type                      | Description                                           |
| ------------------------- | ----------------------------------------------------- |
| **Web APIs (REST, SOAP)** | Used for internet-based communication.                |
| **Open APIs (Public)**    | Available to external developers (e.g., Twitter API). |
| **Partner APIs**          | Shared with specific partners with authentication.    |
| **Internal APIs**         | Used within a company, not exposed to the public.     |
| **Composite APIs**        | Combine multiple services into a single call.         |

---

## 🌐 Common API Protocols

| Protocol                                   | Description                                                |
| ------------------------------------------ | ---------------------------------------------------------- |
| **REST** (Representational State Transfer) | Most popular, uses HTTP methods (GET, POST, PUT, DELETE).  |
| **SOAP** (Simple Object Access Protocol)   | XML-based, more rigid, enterprise use.                     |
| **GraphQL**                                | Modern API querying standard developed by Facebook.        |
| **gRPC**                                   | Uses HTTP/2 and Protocol Buffers, very fast and efficient. |

---

## 🛠️ Common API Components

* **Endpoints**: URLs where APIs are accessed (`api.example.com/users`)
* **Methods**: HTTP verbs (`GET`, `POST`, `PUT`, `DELETE`)
* **Headers**: Additional metadata (like `Authorization`)
* **Body**: Payload/data (usually in JSON or XML format)
* **Status Codes**: Server response (e.g., `200 OK`, `404 Not Found`)

---

## 🎯 Importance in CEH

From an **ethical hacking** perspective, APIs are **prime attack surfaces** because:

* They often expose **backend logic**.
* May contain **sensitive data**.
* Are sometimes poorly secured or misconfigured.
* Are widely used in **mobile, web, and IoT apps**.

---

## ⚠️ Common API Vulnerabilities (CEH-Aligned)

### 1. **Broken Object Level Authorization (BOLA)**

* Attackers can access unauthorized resources by changing object IDs.
* **Example**: `/user/123` → change to `/user/124`

### 2. **Broken Authentication**

* Poor or missing authentication mechanisms allow attackers to impersonate users.

### 3. **Excessive Data Exposure**

* APIs expose more data than necessary.
* Mitigation: Server-side filtering.

### 4. **Lack of Rate Limiting**

* No restrictions → enables brute force, scraping, or DoS attacks.

### 5. **Mass Assignment**

* When attackers send unexpected parameters to manipulate objects (e.g., setting admin=true).

### 6. **Injection Attacks**

* SQL, NoSQL, Command, or Code Injection via API parameters.
* Example: Passing SQL code in a JSON body.

### 7. **Security Misconfiguration**

* Default keys, verbose error messages, or improper CORS settings.

### 8. **Improper Asset Management**

* Old/hidden APIs left exposed.

### 9. **Insufficient Logging & Monitoring**

* Attacks go unnoticed if there's no alerting or log analysis.

---

## 🔐 API Security Best Practices (Important for CEH)

| Practice                 | Details                                     |
| ------------------------ | ------------------------------------------- |
| **Authentication**       | Use OAuth 2.0, API keys, JWT.               |
| **Authorization**        | Implement RBAC (Role-Based Access Control). |
| **Input Validation**     | Sanitize and validate all inputs.           |
| **Rate Limiting**        | Throttle requests to prevent abuse.         |
| **Logging & Monitoring** | Detect anomalies and intrusion attempts.    |
| **Use HTTPS**            | Encrypt data in transit.                    |
| **Least Privilege**      | Restrict API functionality per user role.   |
| **Patch Management**     | Keep APIs and dependencies up to date.      |

---

## 🧪 API Testing Tools (for CEH Practice)

| Tool           | Use                                             |
| -------------- | ----------------------------------------------- |
| **Postman**    | Manual API testing.                             |
| **Burp Suite** | Intercept, manipulate, and analyze API traffic. |
| **OWASP ZAP**  | API vulnerability scanner.                      |
| **Insomnia**   | Similar to Postman, for testing RESTful APIs.   |
| **Fiddler**    | HTTP debugging and traffic analysis.            |

---

## 🔍 API Hacking Techniques (Ethical Hacking)

| Technique                    | Description                                         |
| ---------------------------- | --------------------------------------------------- |
| **Fuzzing**                  | Sending random or malformed data to test stability. |
| **Parameter Tampering**      | Changing API inputs to bypass checks.               |
| **Enumeration**              | Guessing object IDs or parameters.                  |
| **Replay Attacks**           | Resending old requests to manipulate state.         |
| **Man-in-the-Middle (MITM)** | Sniffing API data if HTTPS is not enforced.         |
| **Token Manipulation**       | Forging or modifying JWT or API tokens.             |

---

## 📚 CEH Topics That Link With APIs

* Web Application Hacking
* Injection Attacks
* Authentication & Session Hijacking
* Sniffing & MITM Attacks
* Cloud & Mobile Security
* Vulnerability Scanning

---

## 🔗 OWASP API Top 10 (Highly Relevant for CEH)

You must **memorize and understand** this list for CEH:

1. Broken Object Level Authorization
2. Broken Authentication
3. Broken Object Property Level Authorization
4. Unrestricted Resource Consumption
5. Broken Function Level Authorization
6. Unrestricted Access to Sensitive Business Flows
7. Server-Side Request Forgery (SSRF)
8. Security Misconfiguration
9. Improper Inventory Management
10. Unsafe Consumption of APIs

---


