# Week 6 Lab Task — Threat Modeling Report

## Threat Modeling Report – SafeBank Online Banking System

---

## 1. Threat Model Diagram

The system was modeled using **Microsoft Threat Modeling Tool 2016** to identify possible security risks in the architecture.

### System Components

* Browser (External User)
* Web Application Server
* Authentication Service (MFA)
* SQL Database
* External Payment Gateway

### Trust Boundaries

* Internet ↔ Web Application Server
* Web Application ↔ Internal Services
* SafeBank System ↔ External Payment Gateway

<br>

<img src="../Week 5/Screenshot/week6.png" width="800" alt="Threat Model Diagram">

## 2. Threat Report (Critical Findings)

The model generated multiple threats using the **STRIDE framework**. The most critical threats are summarized below.

---

### Threat 1 — SQL Injection

* **Category:** Tampering
* **Location:** Web Application → SQL Database

### Observation

User input in login and account queries may be directly used in SQL statements without proper sanitization.

### Impact

* Unauthorized access to database
* Data modification or deletion
* Privilege escalation

<br>

 
---

### Threat 2 — Cross-Site Scripting (XSS)

* **Category:** Tampering
* **Location:** User Input → Web Application

### Observation

Untrusted input may allow attackers to inject malicious scripts executed in the user’s browser.

### Impact

* Session hijacking
* Account takeover
* Sensitive data exposure

<br>

 
---

### Threat 3 — Replay Attack on MFA

* **Category:** Tampering
* **Location:** Web App ↔ Authentication Service

### Observation

Multi-Factor Authentication tokens may be reused if they are not time-limited or uniquely validated.

### Impact

* Authentication bypass
* Unauthorized account access

<br>

 
---

### Threat 4 — Payment Gateway Spoofing

* **Category:** Spoofing
* **Location:** Web App ↔ External Payment Gateway

### Observation

Attackers may impersonate the payment gateway and send fake responses to the application.

### Impact

* Fraudulent transactions
* Financial loss
* Loss of user trust

<br>

 
---

### Threat 5 — Denial of Service (DoS)

* **Category:** Denial of Service
* **Location:** Web Application / Authentication Service

### Observation

Attackers may flood the system with excessive requests, making services unavailable.

### Impact

* System downtime
* Service unavailability
* Reputational damage

<br>

 
---

## 3. Mitigation Recommendations

### SQL Injection

* Use parameterized queries
* Input validation
* Least privilege database access

### XSS

* Output encoding
* Content Security Policy (CSP)

### Replay Attack

* Use time-based OTP (TOTP)
* Implement nonce values
* Token expiration mechanisms

### Payment Spoofing

* Use TLS encryption
* Certificate validation
* Secure API authentication

### DoS Attacks

* Rate limiting
* Web Application Firewall (WAF)
* Load balancing

---

## Conclusion

Threat modeling of the SafeBank Online Banking System identified several high-risk security threats early in the design phase. These include SQL injection, XSS, MFA replay attacks, payment spoofing, and denial of service attacks.

By applying proper security controls such as secure coding practices, strong authentication mechanisms, and network-level protections, the system can significantly reduce its attack surface and improve overall resilience against real-world cyber threats.
