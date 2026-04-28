# Week 4 Lab Task — Vulnerability Analysis

## Vulnerability Assessment Report – Metasploitable

---

## 1. Introduction

This assessment was conducted on a vulnerable machine (**Metasploitable**) in an isolated virtual lab environment. The main objective was to identify security weaknesses in network services and web applications and evaluate their potential impact.

---

## 2. Methodology

The following tools and techniques were used:

* **Nmap** — Port scanning and service detection
* **Nmap NSE Scripts** — Automated vulnerability identification
* **Nikto** — Web server vulnerability scanning
* **Manual Web Testing** — Browser-based inspection of services

---

## 3. Findings

### FTP Anonymous Login (Port 21)

Anonymous login is enabled on the FTP service, allowing access without authentication.

* **Risk:** Unauthorized file access and data exposure

<br>

 
---

### Telnet Service Enabled (Port 23)

Telnet service is active on the system.

* **Risk:** Credentials transmitted in plain text (easily intercepted)

<br>

 
---

### Outdated Apache Web Server (Port 80)

The web server is running outdated Apache and PHP versions.

* **Risk:** Known vulnerabilities can be exploited

<br>

 
---

### Directory Listing Enabled

Directory indexing is enabled on the web server.

* **Risk:** Sensitive files and directories exposed

<br>

 
---

### Missing Security Headers

Important HTTP security headers are not configured.

* **Missing Headers:**

  * Content Security Policy (CSP)
  * X-Frame-Options

* **Risk:** XSS and clickjacking attacks

<br>

 
---

### HTTP TRACE Method Enabled

The HTTP TRACE method is active on the server.

* **Risk:** Potential Cross-Site Tracing (XST) attacks

<br>

 
---

### phpMyAdmin Exposure

Database administration panel is publicly accessible.

* **Risk:** Possible database compromise if credentials are weak or guessed

<br>

 
---

## 4. Risk Analysis Table

| Vulnerability            | Severity | CVSS | Recommended Fix                         |
| ------------------------ | -------- | ---- | --------------------------------------- |
| FTP Anonymous Login      | Critical | 9.8  | Disable anonymous FTP access            |
| Telnet Enabled           | High     | 8.0  | Disable Telnet, use SSH                 |
| Outdated Apache Server   | High     | 7.5  | Update Apache and PHP versions          |
| Directory Listing        | Medium   | 5.0  | Disable directory indexing              |
| Missing Security Headers | Medium   | 5.5  | Configure CSP and X-Frame-Options       |
| HTTP TRACE Enabled       | Medium   | 5.0  | Disable TRACE method                    |
| phpMyAdmin Exposure      | High     | 7.0  | Restrict access + enable authentication |

---

## 5. Conclusion

The system contains multiple **critical and high-risk vulnerabilities**, including insecure services (FTP, Telnet), outdated software, and misconfigurations in the web server.

If this were a real production environment, these issues could lead to:

* Unauthorized access
* Data leakage
* Remote exploitation
* Full system compromise

Immediate mitigation steps such as disabling insecure services, applying updates, and strengthening web server configurations are required to secure the system.
