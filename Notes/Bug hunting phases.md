

In web penetration testing, the process is generally divided into several key phases to systematically identify and exploit vulnerabilities. Starting with subdomain enumeration, the phases are as follows:

1. Information Gathering (Reconnaissance):

Subdomain Enumeration: Identifying subdomains of the target website (e.g., using tools like Sublist3r, Amass).

DNS Enumeration: Gathering DNS records (e.g., nslookup, dig).

WHOIS Lookup: Collecting domain registration info.

Port Scanning: Scanning open ports and services (e.g., Nmap).

Technology Stack Detection: Identifying the tech stack like frameworks, languages, and software used by the web app.



2. Vulnerability Scanning:

Automated Scanning: Using tools like Nikto, OpenVAS, Burp Suite for a general scan of known vulnerabilities.

Fingerprinting: Identifying versions of software running on the web app to check for known exploits.



3. Enumeration and Analysis:

Directory Enumeration: Finding hidden directories (e.g., DirBuster, gobuster).

Parameter Enumeration: Discovering sensitive parameters in URLs and forms (e.g., Burp Suite's Intruder).

Session Management Testing: Testing for weak session IDs or poor token management.



4. Exploitation:

SQL Injection: Testing database vulnerabilities (e.g., sqlmap).

Cross-Site Scripting (XSS): Injecting malicious scripts.

File Inclusion Attacks: Testing for Local File Inclusion (LFI) or Remote File Inclusion (RFI).

Authentication and Authorization: Testing for weak passwords, broken authentication, or unauthorized access to protected areas.



5. Post-Exploitation:

Privilege Escalation: Attempting to gain higher-level access on the web application or underlying system.

Data Exfiltration: Testing the extent to which sensitive data can be accessed and extracted.



6. Reporting:

Documenting Findings: Clearly outlining vulnerabilities found, exploitation techniques, and the impact of the findings.

Remediation Recommendations: Providing suggestions for fixing the identified vulnerabilities.




These phases cover the standard methodology for web application penetration testing, though certain cases might require more specialized techniques based on the nature of the target.










Here is a more exhaustive, detailed list of phases in web application penetration testing, from subdomain enumeration through reporting:

1. Reconnaissance (Information Gathering)

Passive Recon:

WHOIS Lookup: Collect domain ownership and registrar information (e.g., whois, rdap).

DNS Enumeration: Identify DNS records (A, MX, TXT, etc.) and name servers (e.g., dig, dnsenum).

Subdomain Enumeration: Identify subdomains associated with the target (e.g., Sublist3r, Amass, Assetfinder).

SSL/TLS Information: Check SSL/TLS configurations, certificate details (e.g., sslyze, SSL Labs).

Public Data Collection: Gather information from publicly available sources, including social media, code repositories (e.g., GitHub, LinkedIn).

Website Content Crawling: Crawl the target site for information (e.g., Wayback Machine, wget, HTTrack).


Active Recon:

Port Scanning: Identify open ports and services (e.g., Nmap, Masscan).

Service Version Detection: Identify versions of services running on open ports (e.g., Nmap, WhatWeb).

Technology Stack Fingerprinting: Identify technologies used by the web application (e.g., Wappalyzer, BuiltWith).

OSINT: Use Open Source Intelligence tools for gathering data (e.g., Maltego, theHarvester).

Social Engineering: Engage in techniques such as phishing or pretexting to gather sensitive information (if allowed).



2. Mapping the Application

Spidering: Automatically explore and map all available pages and endpoints (e.g., Burp Suite's Spider, OWASP ZAP).

Directory and File Enumeration: Identify hidden directories and files (e.g., gobuster, dirb, ffuf).

Identify Input Points: Determine all input points, such as forms, URL parameters, HTTP headers.

Parameter Discovery: Map out all parameters and hidden fields (e.g., ParamSpider, Burp Suite).


3. Vulnerability Discovery

Automated Vulnerability Scanning:

General Vulnerability Scanners: Run web vulnerability scanners (e.g., Nikto, OpenVAS, Nessus, Burp Suite Scanner).

SSL/TLS Misconfigurations: Scan for weak SSL/TLS ciphers, certificates (e.g., testssl.sh).

Software Version Scanning: Identify outdated software with known vulnerabilities (e.g., Nmap, whatweb).


Manual Testing:

SQL Injection (SQLi): Test for SQL injection vulnerabilities manually and automatically (e.g., sqlmap).

Cross-Site Scripting (XSS): Test for stored, reflected, and DOM-based XSS manually (e.g., payload injection, XSStrike).

Cross-Site Request Forgery (CSRF): Test for CSRF vulnerabilities (e.g., Burp Suite, custom requests).

File Upload Vulnerabilities: Test for unrestricted file uploads, which may lead to Remote Code Execution (RCE).

Insecure Direct Object Reference (IDOR): Check if object identifiers can be manipulated for unauthorized access.

Authentication Testing: Test for weak passwords, bypassing authentication mechanisms, default credentials.

Authorization Testing: Test for horizontal and vertical privilege escalation by manipulating roles and permissions.

Business Logic Testing: Evaluate application logic for flaws that could result in security issues (e.g., manipulating price values).

Security Misconfigurations: Check for improper security settings like misconfigured headers, poor session management, exposed sensitive files.

Server-Side Request Forgery (SSRF): Test if the web server can make requests to arbitrary domains or internal resources.

Command Injection: Test for executing arbitrary commands on the underlying OS (e.g., using payloads in form inputs, headers).

Path Traversal: Test for directory traversal vulnerabilities to access files outside the web root.

Local File Inclusion (LFI)/Remote File Inclusion (RFI): Test for vulnerabilities allowing the inclusion of files via user input.

Broken Session Management: Analyze session ID predictability, session fixation, and improper session expiration.

API Testing: Test REST/SOAP APIs for authentication, authorization, and input handling issues (e.g., Postman, Burp Suite).

Insecure Deserialization: Test for insecure deserialization vulnerabilities that could lead to RCE or DoS.

Information Leakage: Look for unintended data exposure in headers, error messages, or debug information.

Password Reset Testing: Evaluate the security of the password reset process for flaws such as token reuse.



4. Exploitation

Exploitation of Discovered Vulnerabilities:

Privilege Escalation: Gain higher-level privileges after gaining low-level access (e.g., vertical or horizontal privilege escalation).

Remote Code Execution (RCE): Exploit vulnerabilities like file uploads or command injections for executing code remotely.

Database Extraction: Use SQL Injection to dump sensitive data from databases (e.g., sqlmap).

Session Hijacking: Steal active sessions using weak session tokens or cookies.

Cross-Site Scripting (XSS) Exploitation: Deliver malicious payloads through stored or reflected XSS attacks to compromise users.

Password Cracking: Crack hashes or weak passwords (e.g., John the Ripper, hashcat).

Man-in-the-Middle (MITM) Attacks: Intercept and modify communications (e.g., ettercap, Wireshark).



5. Post-Exploitation

Maintaining Access: Establish backdoors, web shells, or persistent access points after exploitation.

Privilege Escalation: Escalate privileges from a low-level user to an admin or root user.

Data Exfiltration: Extract sensitive information such as credentials, database dumps, or files from the server.

Lateral Movement: Pivot from the compromised server to other internal servers or systems.

Covering Tracks: Delete logs, modify timestamps, or clear history to avoid detection.


6. Reporting

Vulnerability Documentation:

Detailed Findings: Document each discovered vulnerability with screenshots, proof of concept (PoC), and steps to reproduce.

Risk Assessment: Assess the impact, likelihood, and severity of vulnerabilities using a standardized scoring system (e.g., CVSS).

Exploitation Proofs: Provide evidence of successful exploitation where applicable (e.g., screenshots, extracted data).


Remediation Recommendations:

Provide actionable recommendations for addressing the vulnerabilities, such as patches, configuration changes, or code fixes.


Executive Summary: Summarize key findings for non-technical stakeholders, including risk assessments and business impacts.

Technical Report: Provide detailed technical findings for the development and security teams to implement the fixes.

Compliance & Regulatory Considerations: If necessary, tie findings to relevant compliance requirements (e.g., GDPR, PCI-DSS, HIPAA).



---

This exhaustive list covers the complete process from reconnaissance through exploitation and reporting, ensuring a thorough and methodical approach to web penetration testing.






