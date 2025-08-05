Here’s your complete **100% open-source, free roadmap to skip OSWA (WEB-200)** and become proficient in **web app hacking from beginner to intermediate level** — without paying for any OffSec course.

---

## 🧠 Goal: Match & Surpass OSWA Skill Level (Beginner Web Hacking)

### 🔥 What OSWA Covers (and What You Need to Replicate for Free):

|OSWA Topic|Free Open-Source Alternative|
|---|---|
|Web basics (HTTP, cookies, sessions, headers)|PortSwigger Web Academy (beginner labs)|
|OWASP Top 10 (2021)|PortSwigger + Juice Shop + HackTricks|
|Recon, brute force, input validation|TryHackMe + FFUF + Gobuster|
|XSS, CSRF, IDOR, SQLi, Command Injection|PortSwigger + DVWA + bWAPP|
|Simple authentication bypass|HackTricks + bWAPP + Authentication Labs|
|Basic file upload vulnerabilities|Juice Shop + PayloadsAllTheThings|
|Manual web app testing|OWASP Testing Guide + Bug Bounty Notes|
|Reporting vulnerabilities|Bugcrowd/VRT + sample writeups|

---

## ✅ 🔓 Open-Source + Free Resources to Learn All This

### 🏁 1. **PortSwigger Web Security Academy** (100% Free)

🧩 [https://portswigger.net/web-security](https://portswigger.net/web-security)  
**Do all labs from these categories:**

- SQLi
- XSS (Reflected, Stored, DOM)
- CSRF
- File upload
- Authentication
- Access control
- Business logic flaws
- Web cache poisoning
- SSRF, XXE _(if going beyond OSWA)_

---

### ⚙️ 2. **Practice Labs (Free & Open Source)**

#### 🔹 Damn Vulnerable Web App (DVWA)

🔗 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)  
Covers: XSS, SQLi, CSRF, File Inclusion, Command Injection

#### 🔹 bWAPP (Buggy Web App)

🔗 [https://sourceforge.net/projects/bwapp/](https://sourceforge.net/projects/bwapp/)  
Has over 100+ vulnerabilities including OSWA-style ones.

#### 🔹 OWASP Juice Shop

🔗 [https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/)  
Modern frontend app with a wide range of vulnerabilities and scoring system. Perfect for XSS, IDOR, business logic, and advanced auth bypasses.

#### 🔹 WebGoat

🔗 [https://owasp.org/www-project-webgoat/](https://owasp.org/www-project-webgoat/)  
Very structured — maps well to OWASP Top 10.

#### 🔹 TryHackMe (Free Rooms)

🔗 [https://tryhackme.com](https://tryhackme.com)  
Rooms:

- **OWASP Top 10**
- **Burp Suite Basics**
- **Intro to Web Hacking**

#### 🔹 HackTricks

🔗 [https://book.hacktricks.xyz](https://book.hacktricks.xyz)  
One of the best free resources for cheat sheets and exploitation logic.

---

### 🔍 3. **Real-World Recon & Enumeration Tools**

|Tool|Use|
|---|---|
|**FFUF**|Directory/file brute-forcing|
|**Gobuster**|Directory brute-forcing|
|**WhatWeb / Wappalyzer**|Technology fingerprinting|
|**Burp Suite Community**|Manual testing proxy|
|**Nikto**|Web server scanning|
|**Waybackurls**|Discover archived URLs|
|**Arjun**|Parameter discovery|
|**Dalfox / XSStrike**|Automated XSS tools|

---

### 📄 4. **Vulnerability Reporting & Documentation**

- **Bugcrowd VRT** → [https://bugcrowd.com/vulnerability-rating-taxonomy](https://bugcrowd.com/vulnerability-rating-taxonomy)
- **Sample reports** → [https://github.com/nahamsec/Resources-for-Beginner-Bug-Bounty-Hunters](https://github.com/nahamsec/Resources-for-Beginner-Bug-Bounty-Hunters)
- Learn to write good reports: use **Markdown** and include:
    - Summary
    - Vulnerability description
    - Steps to reproduce
    - Impact
    - Remediation suggestions

---

### 📚 5. **Books & Guides (Free & Open License)**

|Book/Guide|Link|
|---|---|
|Web Application Hacker’s Handbook (search for PDF)|🧠 Classic|
|OWASP Testing Guide v4|[https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)|
|PayloadsAllTheThings|[https://github.com/swisskyrepo/PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)|
|HackTricks Web Hacking|[https://book.hacktricks.xyz/pentesting-web](https://book.hacktricks.xyz/pentesting-web)|

---

## 🛠️ Setup Your Lab (Local + Online)

1. Install **XAMPP/LAMP**, **Docker**, or **Vagrant**.
2. Deploy:
    - DVWA
    - bWAPP
    - Juice Shop (via Docker)
    - WebGoat + WebWolf
3. Use **Burp Suite Community Edition** for traffic analysis and fuzzing.

---

## 🚀 Suggested Learning Roadmap

|Week|Focus|
|---|---|
|1–2|HTTP basics, Burp Suite, basic PortSwigger labs|
|3–4|DVWA + bWAPP → OWASP Top 10 (XSS, SQLi, IDOR, CSRF)|
|5–6|PortSwigger (Authentication, Access Control, File Upload)|
|7–8|Juice Shop + WebGoat|
|9–10|HackTricks + real bug bounty writeups|
|11–12|Review labs, test custom vulnerable apps from GitHub|

---

## 🧠 Bonus Projects (to strengthen OSWA-level skills)

- Build your own **mini vulnerable login page** and try to break it (SQLi, bypass, cookie tampering).
- Review GitHub projects like:
    - [https://github.com/s0md3v/Web-Bugs](https://github.com/s0md3v/Web-Bugs)
    - [https://github.com/infoslack/awesome-web-hacking](https://github.com/infoslack/awesome-web-hacking)
    - [https://github.com/pr0xylife/Web-Application-Hacking](https://github.com/pr0xylife/Web-Application-Hacking)

---

## 💡 Final Thought

You **do not need OSWA or WEB-200** if:

- You’re consistent with PortSwigger + DVWA + Juice Shop.
- You do practical testing via Burp.
- You document your findings in a proper report format.

---

### Want me to turn this into a Notion page or Markdown guide for easy tracking?