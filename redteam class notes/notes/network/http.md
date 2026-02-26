
# 1. What is HTTP?

**HTTP (HyperText Transfer Protocol)** is an application-layer protocol used for communication between web browsers (clients) and web servers.

It is the foundation of data communication on the World Wide Web.

It follows a **request–response model**.


# 2. Where HTTP Works in Networking

HTTP operates at:

* **Application Layer** of the OSI model
* Runs on top of **TCP**
* Default port:

  * Port 80 → HTTP
  * Port 443 → HTTPS


# 3. Basic HTTP Workflow

When you enter a URL in a browser:

### Step 1: DNS Resolution

* Domain name is converted to IP address.

### Step 2: TCP Connection

* Browser establishes a TCP connection with the server.

### Step 3: HTTP Request

* Browser sends an HTTP request.

### Step 4: Server Processing

* Server processes the request.

### Step 5: HTTP Response

* Server sends back an HTTP response.

### Step 6: Connection Close or Reuse

* Connection may close or stay open (persistent connection).


# 4. HTTP Request Structure

An HTTP request has:

### 1. Request Line

```
GET /index.html HTTP/1.1
```

* Method (GET, POST, etc.)
* Path
* HTTP version

### 2. Headers

Provide metadata:

```
Host: example.com
User-Agent: Chrome
Accept: text/html
```

### 3. Body (Optional)

Used mainly with POST, PUT:

* Form data
* JSON data
* File uploads


# 5. HTTP Response Structure

### 1. Status Line

```
HTTP/1.1 200 OK
```

* HTTP version
* Status code
* Status message

### 2. Headers

```
Content-Type: text/html
Content-Length: 1024
```

### 3. Body

* HTML
* JSON
* Images
* Files


# 6. Common HTTP Methods

* **GET** – Retrieve data
* **POST** – Send data
* **PUT** – Update data
* **DELETE** – Remove data
* **PATCH** – Partial update
* **HEAD** – Get headers only
* **OPTIONS** – Check allowed methods


# 7. HTTP Status Codes

Grouped into categories:

### 1xx – Informational

* 100 Continue

### 2xx – Success

* 200 OK
* 201 Created

### 3xx – Redirection

* 301 Moved Permanently
* 302 Found

### 4xx – Client Errors

* 400 Bad Request
* 401 Unauthorized
* 403 Forbidden
* 404 Not Found

### 5xx – Server Errors

* 500 Internal Server Error
* 503 Service Unavailable


# 8. Stateless Nature of HTTP

HTTP is **stateless**:

* Each request is independent.
* Server does not remember previous requests.

To maintain state:

* Cookies
* Sessions
* Tokens (JWT)


# 9. HTTP vs HTTPS

HTTP:

* Data sent in plain text
* Not secure

HTTPS:

* HTTP over TLS/SSL
* Encrypted communication
* Uses port 443
* Provides confidentiality and integrity


# 10. HTTP Versions

### HTTP/1.0

* One request per connection

### HTTP/1.1

* Persistent connections
* Pipelining

### HTTP/2

* Multiplexing (multiple requests over one connection)
* Header compression
* Faster performance

### HTTP/3

* Uses QUIC (runs over UDP instead of TCP)
* Faster and improved reliability


# 11. Summary

HTTP:

* Is a web communication protocol
* Works on request–response model
* Runs over TCP
* Is stateless
* Uses methods and status codes
* HTTPS adds encryption and security


