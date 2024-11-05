
Here's a compilation of the top 100 bugs commonly reported by newbies in bug bounty programs. These bugs are categorized by their types, focusing on commonly exploited vulnerabilities in web applications, APIs, and other software systems.

1. Cross-Site Scripting (XSS)

Reflected XSS

Stored XSS

DOM-based XSS

Blind XSS

Self XSS


2. Cross-Site Request Forgery (CSRF)

CSRF in Login

CSRF in Account Modification

CSRF in File Upload

CSRF in Sensitive Actions

Bypass CSRF Tokens


3. Broken Authentication & Session Management

Weak Password Policies

User Enumeration

Brute Force Attacks

Predictable Session Tokens

Session Fixation

Lack of Multi-Factor Authentication


4. Security Misconfiguration

Default Credentials

Exposed Admin Interfaces

Directory Listing Enabled

Misconfigured CORS (Cross-Origin Resource Sharing)

Debug Information Leaks

Misconfigured HTTP Headers (e.g., missing security headers)

Using Outdated Software


5. Sensitive Data Exposure

Information Disclosure in Error Messages

Hardcoded API Keys or Credentials

Sensitive Data in URL

Exposed Backup Files

Data Leakage via API Responses

Insecure Storage of Sensitive Data


6. Broken Access Control

IDOR (Insecure Direct Object References)

Privilege Escalation

Accessing Unrestricted Admin Functionality

Directory Traversal

Lack of Proper Role-Based Access Control (RBAC)

Access Control Bypass via Parameter Manipulation


7. File Upload Vulnerabilities

Unrestricted File Upload

File Type Bypass

Content-Type Manipulation

Local File Inclusion (LFI)

Remote File Inclusion (RFI)

Uploading Malicious Files (e.g., Web Shells)


8. Server-Side Request Forgery (SSRF)

Basic SSRF (Requesting Internal IPs)

Blind SSRF

SSRF via Error Messages

SSRF to Access Metadata Services

SSRF to Internal APIs


9. SQL Injection (SQLi)

Error-Based SQLi

Blind SQLi

Time-Based SQLi

UNION-Based SQLi

Second-Order SQLi

NoSQL Injection


10. Command Injection

OS Command Injection

Blind Command Injection

Command Injection via Parameter Tampering


11. Clickjacking

Basic Clickjacking (Framing)

Clickjacking with Hidden Elements

Clickjacking to Perform Sensitive Actions


12. Insecure Deserialization

Exploiting Insecure Deserialization in Web Apps

Exploiting Insecure Deserialization in APIs


13. Open Redirect

URL Redirection in User Input

Open Redirect in Headers

Open Redirect in URL Parameters


14. XML External Entity (XXE)

Basic XXE (File Disclosure)

Blind XXE

XXE via Error Messages

Out-of-Band XXE (OOB-XXE)


15. Business Logic Flaws

Bypassing Payment Flows

Manipulating Discounts or Prices

Abusing Account Creation/Deletion

Accessing Restricted Content


16. API Vulnerabilities

Lack of Rate Limiting

Excessive Data Exposure

Improper API Endpoint Restrictions

API Parameter Tampering

Server-Side Template Injection (SSTI)


17. Cryptographic Issues

Using Weak or Deprecated Algorithms

Poor Key Management Practices

Lack of HTTPS/TLS

Improper Certificate Validation

Missing HSTS Headers


18. Logic Flaws

Manipulating Order Quantities or Costs

Bypassing CAPTCHA

Weak Password Recovery Mechanisms


19. Race Conditions

Exploiting Race Conditions for Double-Spending

Exploiting Race Conditions for Data Manipulation


20. DNS Misconfigurations

Subdomain Takeover

DNS Zone Transfer

Misconfigured DNS Records (e.g., wildcard DNS)

DNS Cache Poisoning


21. Email-Based Vulnerabilities

Email Spoofing

Lack of SPF, DKIM, DMARC

Email Enumeration via Login or Registration


22. Third-Party Services Issues

Misconfigured Cloud Buckets (AWS S3, Azure Blob)

Outdated Third-Party Plugins/Libraries

Vulnerabilities in Integrated Services (e.g., OAuth)


23. Social Engineering & Phishing

Email-Based Phishing

Social Engineering Bypass

Abuse of Forgot Password Mechanisms


24. Network Vulnerabilities

Exposed Internal Services

Misconfigured VPN/Firewall Rules

Weak Wi-Fi Security


25. WebSocket Vulnerabilities

Lack of WebSocket Authentication

Manipulating WebSocket Data

WebSocket Information Disclosure


26. Password-Related Issues

Weak/Default Passwords

Password Guessing via Brute Force

Password Change Vulnerabilities

No Password Strength Validation


27. Cache Poisoning

Cache Poisoning via HTTP Headers

Web Cache Deception Attack


28. Denial of Service (DoS)

Application-Level DoS (e.g., Resource Exhaustion)

DoS via Large Payloads

DoS via Expensive Database Queries


29. HTML Injection

Injecting HTML Tags

HTML Injection for Phishing Purposes


30. Content Security Policy (CSP) Issues

Weak or Misconfigured CSP

CSP Bypass via Inline Scripts or Styles


31. Cookie-Based Vulnerabilities

Lack of HttpOnly or Secure Flags

Session Cookies Exposed Over HTTP

Cookie Manipulation or Poisoning


32. Logging & Monitoring Issues

Sensitive Information in Logs

Lack of Audit Logs

Insufficient Monitoring of Security Events


33. Weak or Missing Encryption

Insecure Transmission of Data

Storing Sensitive Data Without Encryption


34. Remote Code Execution (RCE)

RCE via File Upload

RCE via Deserialization

RCE via Command Injection


35. Cloud-Specific Vulnerabilities

Weak Cloud Configuration

Over-permissive IAM Roles

Cloud Service Misconfigurations (e.g., S3 Bucket ACLs)


36. Cross-Origin Resource Sharing (CORS)

Misconfigured CORS Policies

Wildcard CORS in Sensitive Endpoints


37. CRLF Injection

Manipulating Headers with CRLF Injection

Exploiting CRLF for Log Poisoning


38. Path Traversal

Simple Path Traversal

Path Traversal via Null Bytes


39. HTTP Parameter Pollution

Bypassing Validations using Parameter Pollution

Multiple Values for Same Parameter


40. SSL/TLS Vulnerabilities

Using Weak Ciphers

Deprecated SSL/TLS Versions (e.g., SSLv3)

Improper SSL Certificate Chain


These are the most common vulnerabilities typically found by beginner bug hunters, focusing on widely recognized security issues within web applications, APIs, mobile apps, and cloud environments.






Here are some reliable platforms and databases where newbies can find vulnerabilities and practice bug hunting:

1. Bugcrowd's Vulnerability Rating Taxonomy (VRT)

A comprehensive resource that lists common vulnerabilities with detailed descriptions and severity ratings.

Excellent for understanding what vulnerabilities to look for and how they are classified.


2. OWASP Top 10

A globally recognized list of the top 10 most critical web application security risks.

Great for beginners to learn about common vulnerabilities.


3. HackerOne Hacktivity

A public feed of disclosed reports and real-world vulnerabilities submitted by hackers.

A good way to see what vulnerabilities other hackers are reporting.


4. PortSwigger Web Security Academy

Free online training platform with detailed guides, labs, and challenges for learning web vulnerabilities.

Excellent hands-on practice for beginners, covering topics like XSS, SQLi, and CSRF.


5. Exploit Database (Exploit-DB)

An archive of publicly disclosed vulnerabilities and exploits.

Useful for learning about a wide range of vulnerabilities and seeing real-world examples.


6. PentesterLab

A platform offering exercises, labs, and certificates focused on web vulnerabilities.

Has beginner-friendly content and real-world scenarios to practice.


7. VulnHub

Provides a collection of intentionally vulnerable machines to download and practice penetration testing.

Ideal for hands-on practice and CTF-style challenges.


8. Red Team Labs by TryHackMe

Offers beginner to advanced levels of penetration testing, including web vulnerabilities.

A mix of theory and hands-on labs for newcomers.


9. NIST National Vulnerability Database (NVD)

A detailed and searchable database of vulnerabilities.

Good for understanding vulnerabilities' CVSS scores, details, and how they impact software.


10. Google's Vulnerability Reward Program (VRP) Bug Hunter University

A learning platform specifically for beginners aiming to hunt bugs.

Offers guidelines, case studies, and examples of common vulnerabilities.


These platforms provide a mix of educational material, real-world examples, and practice opportunities to help you become proficient in finding vulnerabilities.

