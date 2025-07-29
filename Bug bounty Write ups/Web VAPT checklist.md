✅ Subdomain enumeration
✅ Directory brute-forcing
✅ Session/Cookie auditing
✅ SSL/TLS checks
✅ Authentication and authorization flaws
✅ Business logic bypasses (cart, voucher, order tampering)
✅ Password reset vulnerabilities
✅ OAuth open redirection
✅ HTTP verb tampering & header tricks
✅ Real-world bug bounty examples (GitLab privilege escalation, etc.)


Here's your complete **VAPT Testing Checklist** rewritten in `.md` (Markdown) format for better readability and structured documentation:

---

# VAPT Testing Checklist

## 1. Fingerprinting Application

|Activity|Tools/Technique|Remarks|
|---|---|---|
|Bruteforce Subdomains|`Dnsdumpster.com`, `BuiltWith`, `Sublist3r`, `Subfinder`, `Assetfinder`, `Amass`, `Altdns`, `crt.sh`, `hakrawler`, `gospider`|Example: `python3 sublist3r.py -d chintan.com -p80,443,...`  <br>Check for 3rd level domains|
|Check Subdomain URLs in Content|`hakrawler`, `httpx`, `assetfinder`|Chain: assetfinder ➝ httpx ➝ hakrawler|

## 2. Directory Enumeration

|Activity|Tools|Remarks|
|---|---|---|
|Directory Brute-force|`Dirb`, `Dirbuster`, `Gobuster`, `BurpSuite`, `ZAP`|Use latest wordlists|

## 3. Identify Tech Stack

|Activity|Tools|Remarks|
|---|---|---|
|Identify Web Client & Server Tech|`Wappalyzer`, Response Headers||

## 4. HTTP Services on Non-standard Ports

|Activity|Tools|Remarks|
|---|---|---|
|Discover Services|`nmap`||

## 5. Leaked Info & OSINT

|Activity|Tools|Remarks|
|---|---|---|
|Leak Search|`Breach Compilation`, `WeLeakInfo`, `Hunter.io`||

## 6. Google Dorking

|Activity|Tool|Remarks|
|---|---|---|
|Dorks|[https://dorks.faisalahmed.me](https://dorks.faisalahmed.me)||

## 7. Sensitive Info Keywords in Source

|Activity|Tool|Remarks|
|---|---|---|
|Crawl & Search Keywords|`BurpSuite Engagement Tools`|Look for: `password`, `admin`, `todo`, `http://` endpoints|

## 8. Network Testing

|Activity|Tool|Remarks|
|---|---|---|
|Ping Test|`ping` command||

## 9. Censys Scanning

|Activity|Tool|Remarks|
|---|---|---|
|Domain Info Discovery|`censys.io`|Look for MX, exposed services|

## 10. DNS Testing

|Activity|Technique|Remarks|
|---|---|---|
|Zone Transfer, DNSSEC, CAA Records|WHOIS (Local), Dig|Prefer local WHOIS over global|

## 11. Vulnerability Scanning

|Activity|Tool|Remarks|
|---|---|---|
|Web/App Vulnerability Scanning|`Nessus`||
|Known Vulnerabilities in Components|`Nessus`, `Nexpose`, `Exploit Suggestor`||

## 12. Banner Disclosure

|Activity|Tool|Remarks|
|---|---|---|
|Banner Grabbing|`nmap`|Ports other than 80, 443|

## 13. Find All Web Servers

|Activity|Tool|Command|
|---|---|---|
|Web Server Discovery|`nmap`|`nmap -sS -n -Pn -p [list of ports] -iL target.txt -oA web_result -vvv –open`|

## 14. UDP Protocol Scanning

|Activity|Tool|Command|
|---|---|---|
|UDP Proto Scan|`perl udp-proto-scanner.pl`|`--file target.txt`|

## 15. Application Mapping

|Activity|Tool|Remarks|
|---|---|---|
|Site Structure Mapping|`Manual`, `Freemind`||

## 16. SSL/TLS Testing

|Activity|Tool|Remarks|
|---|---|---|
|Certificate Testing|`Qualys SSL Labs`||

---

## 17–93. Application Security Testing

Each test case below includes methods and tools like **BurpSuite**, **Manual Testing**, and browser-based inspection. Key areas include:

- **Session Management**
- **Cookie Security**
- **Authentication Bypass**
- **Registration Logic**
- **Password Reset Weaknesses**
- **Access Control**
- **CSRF & XSS Testing**
- **OTP Bypass**
- **Directory Traversal & File Upload**
- **IDOR (Insecure Direct Object Reference)**
- **Product Purchase / Cart Tampering**
- **Voucher/Gift Card Manipulation**
- **Payment Tampering**
- **Tracking/Booking Systems Testing**
- **OAuth Redirection**
- **HTTP Verb Tampering & Header Bypass Techniques**

Example Payloads and Bypass Tricks:

```
example.com/admin        → 403
example.com/admin/.      → 200
example.com//admin//     → 200
example.com/./admin/./   → 200
example.com/admin ..;/   → 200
```

### Common Headers for Bypass:

```
X-Original-URL: /admin
X-Custom-IP-Authorization: 127.0.0.1
Host: google.com
```

---

## 94. Booking App Testing (Flights/Rail/Hotels/Cabs)

- **Tampering Booking Details**
- **Reusing Vouchers**
- **Tracking Others' Orders**
- **Insecure APIs**
- **Price Manipulation**

---

If you'd like this in `.md` file format for download or GitHub README, I can generate it and provide a downloadable link.
