# Week 2 Lab Task — Information Gathering (OSINT)

## Recon Report – Tesla

---

## 1. Domain Ownership (WHOIS)

| Field | Details |
|-------|---------|
| Registrar | MarkMonitor |
| Organization | DNStination Inc. (privacy protected) |
| Created | 1992 |
| Status | Transfer & update protected |

Indicates strong domain security.

<br>

<img src="Screenshots/week2_1.png" width="800" alt="WHOIS Lookup">

---

## 2. IP Addresses

- `23.7.244.207`
- `23.40.100.207`
- `2.18.48.207` – `2.18.55.207`

Multiple IPs indicate CDN usage via **Akamai Technologies** — not the real origin server.

<br>

<img src="Screenshots/week2_2.png" width="800" alt="IP Address Lookup">

---

## 3. Emails & Subdomains

- **Mail Server:** `tesla-com.mail.protection.outlook.com`
- Uses **Microsoft (Outlook/Exchange Online)** for email hosting
- No subdomains discovered in this step

<br>

<img src="Screenshots/week2_3.png" width="800" alt="Mail Server Info">

<br>

<img src="Screenshots/week2_4.png" width="800" alt="Subdomain Scan 1">

<br>

<img src="Screenshots/week2_5.png" width="800" alt="Subdomain Scan 2">

---

## 4. Shodan (Services)

- No direct backend services visible
- Only CDN-related HTTP/HTTPS traffic expected
- Real infrastructure is hidden behind the CDN

---

## 5. Suspicious Indicators

- No major misconfigurations found
- CDN effectively conceals real infrastructure
- Large attack surface likely exists in subdomains

<br>

<img src="Screenshots/week2_6.png" width="800" alt="Shodan Results">

---

## Conclusion

The main domain is well protected with privacy measures and CDN shielding.

Further recon should focus on **subdomains** and **hidden/backend services**.
