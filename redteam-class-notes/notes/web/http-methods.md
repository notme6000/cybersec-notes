
 

# 1. What are HTTP Methods?

HTTP methods (also called **verbs**) define the **type of action** a client (browser, script, API tool like Burp Suite) wants to perform on a resource on a web server.

They are part of the **HTTP protocol** (Hypertext Transfer Protocol).

 

# 2. Common HTTP Methods

## 2.1 GET

**Purpose:** Retrieve data from the server

**Characteristics:**

* No modification of data (read-only)
* Parameters sent in URL (query string)
* Cached by browsers
* Can be bookmarked
* Length limited (URL size)

**Example:**

```
GET /products?id=10 HTTP/1.1
```

**Security Notes:**

* Sensitive data should NOT be sent (visible in URL)
* Often used in enumeration attacks

 

## 2.2 POST

**Purpose:** Send data to the server (create resource)

**Characteristics:**

* Data sent in request body
* Not cached
* Cannot be bookmarked
* No strict size limit

**Example:**

```
POST /login HTTP/1.1
Body: username=admin&password=1234
```

**Security Notes:**

* Used in login forms
* Vulnerable to:

  * SQL Injection
  * CSRF
  * Command Injection

 

## 2.3 PUT

**Purpose:** Update or replace a resource

**Characteristics:**

* Sends full resource data
* Idempotent (same request = same result)

**Example:**

```
PUT /users/1 HTTP/1.1
Body: { "name": "John" }
```

**Security Notes:**

* Misconfigured servers may allow file upload (web shell risk)

 

## 2.4 PATCH

**Purpose:** Partial update of a resource

**Characteristics:**

* Only modifies specific fields
* Not necessarily idempotent

**Example:**

```
PATCH /users/1 HTTP/1.1
Body: { "email": "new@mail.com" }
```

 

## 2.5 DELETE

**Purpose:** Delete a resource

**Characteristics:**

* Idempotent
* Removes specified resource

**Example:**

```
DELETE /users/1 HTTP/1.1
```

**Security Notes:**

* Improper authentication → data loss vulnerability

 

## 2.6 HEAD

**Purpose:** Same as GET but returns only headers

**Use Cases:**

* Check if resource exists
* Get metadata (content-type, size)

**Example:**

```
HEAD /file.zip HTTP/1.1
```

 

## 2.7 OPTIONS

**Purpose:** Show supported methods for a resource

**Example:**

```
OPTIONS /api HTTP/1.1
```

**Response Example:**

```
Allow: GET, POST, PUT
```

**Security Notes:**

* Useful in recon during penetration testing
* Helps identify allowed methods

 

## 2.8 TRACE

**Purpose:** Echo back the request

**Use Cases:**

* Debugging

**Security Risk:**

* Can lead to **Cross Site Tracing (XST)** attacks

 

## 2.9 CONNECT

**Purpose:** Establish a tunnel (used in HTTPS via proxies)

**Example:**

```
CONNECT example.com:443 HTTP/1.1
```

 

# 3. Important Concepts

## 3.1 Safe Methods

Methods that do NOT modify server data:

* GET
* HEAD
* OPTIONS

 

## 3.2 Idempotent Methods

Repeated requests produce the same result:

* GET
* PUT
* DELETE
* HEAD
* OPTIONS

 

## 3.3 Non-Idempotent Methods

* POST
* PATCH

 

# 4. HTTP Methods in REST APIs

In REST architecture:

| Method | Action           |
|  --- | ---------------- |
| GET    | Read             |
| POST   | Create           |
| PUT    | Update (full)    |
| PATCH  | Update (partial) |
| DELETE | Delete           |

 

# 5. HTTP Methods in Cybersecurity

## 5.1 Common Attack Vectors

* **GET → Information leakage**
* **POST → Injection attacks**
* **PUT → Arbitrary file upload**
* **DELETE → Unauthorized deletion**
* **OPTIONS → Reconnaissance**
* **TRACE → XST attacks**

 

## 5.2 Testing with Tools

Tools commonly used:

* Burp Suite
* curl
* Postman

 

## 5.3 Example curl Commands

```
curl -X GET http://example.com
curl -X POST -d "user=admin" http://example.com
curl -X PUT -d "data=test" http://example.com/resource
curl -X DELETE http://example.com/resource
```

 

# 6. Practical Notes for CPT / Pentesting

* Always check allowed methods using:

  * OPTIONS request
  * Burp Suite proxy
* Look for:

  * Unused but enabled methods (PUT, DELETE)
  * Misconfigured APIs
  * Method override headers:

    ```
    X-HTTP-Method-Override: PUT
    ```
* Test each endpoint with multiple methods

 

# 7. Summary

* HTTP methods define **actions on resources**
* Each method has **specific behavior, risks, and use cases**
* Understanding them is critical for:

  * Web development
  * API design
  * Penetration testing

 

