
## 🗂️ 1. Different Types of Logs

Logs are categorized by their source and the type of data they track.

| Log Type | Primary Purpose | Key Data Captured |
| --- | --- | --- |
| **System Logs** | Tracks OS health and core infrastructure performance. | Driver initialization, kernel panics, hardware errors, uptime. |
| **Application Logs** | Monitored by developers to debug software. | Unhandled exceptions, stack traces, database query timeouts. |
| **Security Logs** | Used by SOC analysts for threat detection and compliance. | Successful/failed logins, firewall drops, privilege escalations. |
| **Access/Web Logs** | Records inbound traffic hitting web services (e.g., Nginx, Apache). | Client IP, HTTP status codes, requested URLs, User-Agent strings. |
| **Audit Logs** | Tracks modification histories for compliance and accountability. | File changes, configuration edits, user account creation. |

---

## 🏗️ 2. The Anatomy of a Log Structure

Regardless of the format, a well-structured log contains specific structural metadata elements to ensure it can be parsed effectively by SIEMs or analytics engines.

```
[Timestamp] [Hostname] [Service/Process ID] [Severity Level] [Message]

```

* **Timestamp:** High-resolution time of the event. Standardized using ISO 8601 format (e.g., `2026-06-01T09:52:00Z`) to prevent timezone confusion.
* **Hostname/Device ID:** The specific server, endpoint, or container where the event occurred.
* **Source/Component:** The application or process name (and often its Process ID or PID) that generated the log.
* **Severity/Log Level:** Dictates the urgency of the log. Standard Syslog levels include:
* `DEBUG` (Verbosely tracking program flow)
* `INFO` (Routine operational messages)
* `WARN` (Potential issues that don't break functionality yet)
* `ERROR` (A component failed, but the app keeps running)
* `CRITICAL/FATAL` (System crash or unrecoverable failure)


* **Message Payload:** The actual text description of the event.

---

## 📂 3. Types of Log Formats

Log formats dictate how data is encoded and arranged inside a file.

### A. Structured Log Formats (Machine-Readable)

Ideal for automated ingestion, parsing, and searching within SIEM platforms.

* **JSON (JavaScript Object Notation):** The modern industry standard. Highly flexible, supporting key-value pairs and nested objects.
```json
{"timestamp": "2026-06-01T09:52:00Z", "level": "ERROR", "user": "admin", "event": "Failed password", "src_ip": "192.168.1.45"}

```



```
* **CEF (Common Event Format) / LEEF (Log Event Extended Format):** Standardized, tab- or pipe-delimited formats developed by enterprise security vendors (ArcSight/QRadar) specifically for security devices like firewalls and IDSs.
  ```text
  CEF:0|Vendor|Product|Version|SignatureID|Name|Severity|ExtensionData

```

### B. Unstructured & Semi-Structured Log Formats (Human-Readable)

Traditional flat-text formats. They require Regular Expressions (Regex) to extract data fields.

* **Syslog (RFC 5424):** The standard message logging format for network devices and Linux systems.
```text
<34>1 2026-06-01T09:52:00Z myhost sshd 2415 - - Failed password for invalid user root

```



```
* **Nginx/Apache Common Log Format (CLF):** Used almost universally by web servers.
  ```text
  127.0.0.1 - frank [01/Jun/2026:09:52:00 +0000] "GET /index.html HTTP/1.1" 200 2326

```

---

## 💾 4. Log Storage Types & Architectures

Where and how logs are saved depends on the required access speed, data retention policies, and compliance overhead.

### Hot Storage vs. Cold Storage

* **Hot Storage (Indexed / Active):** Logs are stored in fast-access databases or search clusters (like Elasticsearch/OpenSearch) where they are fully indexed.
* *Use Case:* Real-time alerts, current incident triage, dashboarding. Keep here for 14–30 days.


* **Cold Storage (Archive / Compressed):** Logs are compressed (e.g., `.tar.gz`) and moved to cheap cloud object storage (like AWS S3 or Azure Blob) or offline backups.
* *Use Case:* Long-term compliance retention (e.g., keeping logs for 1 year to meet regulatory requirements). Slow to query.



### Local vs. Centralized Storage

* **Local Logging:** Logs stay on the endpoint that generated them (e.g., `/var/log/` or Windows Event Viewer).
* *Risk:* If an attacker compromises the server, they can clear or alter local logs to hide their tracks.


* **Centralized Logging (SIEM/Log Aggregator):** Logs are instantly shipped off the endpoint using agents (like Filebeat, Logstash, or Fluentd) to a hardened centralized data lake or SIEM platform.
* *Benefit:* Protects log integrity. Analysts can correlate events across thousands of servers simultaneously.
