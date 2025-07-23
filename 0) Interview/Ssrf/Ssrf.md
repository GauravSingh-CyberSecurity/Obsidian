# SSRF to RCE Exploit Chain Pipeline

## 📘 Introduction

**SSRF (Server-Side Request Forgery)** occurs when a web application fetches a remote resource based on user-supplied input **without proper validation**, allowing attackers to manipulate internal or external requests.

While **SSRF** by itself may not always be dangerous, it becomes critical when **chained with other internal services** to achieve **Remote Code Execution (RCE)**.

---

## 🔍 Common SSRF Scenarios

- **Image Proxy/Thumbnail Generator**: Accepts a URL and fetches the image on behalf of the user.
- **Webhook Integrations**: Callback mechanisms that POST to user-defined URLs (e.g., Slack webhooks).
- **PDF Generators**: Convert provided URLs to PDFs.
- **XXE with External DTDs**: Can be abused to trigger SSRF.

---

## 🎯 SSRF Capabilities

- **Scan Internal Networks**  
  Discover live hosts and open ports (e.g., `127.0.0.1`, `192.168.x.x`, `10.x.x.x`).
- **Access Internal Services**  
  Reach services not exposed publicly (e.g., admin panels, databases).
- **Access Cloud Metadata Services**  
  e.g., `http://169.254.169.254/latest/meta-data/` on AWS to obtain IAM credentials.
- **Read Local Files**  
  If `file://` is allowed.
  
---

## 🚀 Escalation from SSRF to RCE

### 1. **Accessing Internal Services**

#### 🔸 Redis / Memcached (Unauthenticated)
- **Protocol**: `gopher://`
- **Technique**:
  - Change Redis config:
    - `CONFIG SET dir /var/www/html/`
    - `CONFIG SET dbfilename shell.php`
  - Set a key with PHP code:
    - `SET x "<?php system($_GET['cmd']); ?>"`
  - Save:
    - `SAVE`

#### 🔸 FastCGI (PHP-FPM)
- **Port**: Usually `9000`
- **Tool**: [Gopherus](https://github.com/tarunkant/Gopherus)
- **Technique**: Send crafted FastCGI payload to trigger code execution.

#### 🔸 SMTP
- **Abuse**: Send spoofed/phishing emails via SSRF.

#### 🔸 Databases (MySQL/PostgreSQL)
- **Technique**:
  - Use SSRF to send SQL commands.
  - Exploit functions like `LOAD_FILE`, `INTO OUTFILE`.

#### 🔸 Internal APIs / Admin Panels
- **Technique**:
  - Trigger admin actions
  - Upload files
  - Execute commands via insecure internal endpoints

---

### 2. **File Inclusion Chaining**

#### 🔸 `file://` Protocol
- Read sensitive files such as:
  - `/etc/passwd`
  - Source code files

#### 🔸 LFI + Log Poisoning
- Poison access logs with PHP payload
- Trigger LFI to include poisoned logs

---

## 🧠 SSRF Filter Bypass Techniques

| Technique              | Description |
|------------------------|-------------|
| **IP Encoding**        | Decimal: `2130706433` for `127.0.0.1`, Octal: `017700000001` |
| **DNS Rebinding**      | Use domains that resolve to internal IPs after initial DNS |
| **Open Redirects**     | Redirect from a trusted domain to internal target |
| **Obscure Protocols**  | `gopher://`, `dict://`, `ftp://`, `file://`, `php://` |
| **URL Obfuscation**    | `http://evil.com@127.0.0.1`, double encoding, mixed case |

---

## 🔄 General Exploitation Pipeline

1. **Identify SSRF**
   - Look for parameters like `url`, `image`, `target`, `next`, `callback`
   - Try internal IPs, `localhost`, `127.0.0.1`, cloud metadata URLs

2. **Bypass SSRF Filters**
   - Try encodings, protocol smuggling, redirect chains

3. **Internal Recon**
   - Perform port scans using SSRF payloads
   - Infer open/closed ports by timing/different error responses

4. **Discover Vulnerable Internal Services**
   - Redis, FastCGI, MySQL, admin panels, file uploaders, etc.

5. **Craft Payloads**
   - Use tools like:
     - `Gopherus` (gopher payloads)
     - `SSRFmap`, `SSRFProbe`
   - Know target protocol structure (Redis, FCGI)

6. **Send SSRF Payload**
   - Use vulnerable endpoint to deliver crafted payload

7. **Trigger RCE**
   - Validate execution by reverse shell, command output, etc.

8. **Establish Persistence**
   - Web shell, SSH key injection, cron jobs, etc.

---

## 🛡️ Prevention and Mitigation

### ✅ Input Validation

- Whitelist allowed hosts/domains
- Reject all protocols except `http`/`https`

### ✅ URL Scheme Restrictions

- Block:
  - `gopher://`
  - `file://`
  - `ftp://`
  - `php://`
  - `dict://`

### ✅ DNS and IP Validation

- Resolve DNS and validate resulting IP is allowed
- Beware of DNS rebinding

### ✅ Network Segmentation

- Internal services should not be accessible to the web application layer

### ✅ Service Hardening

- Redis, MySQL, etc. should require auth, and bind only to localhost with firewall rules

### ✅ Least Privilege

- Run web apps with minimal OS permissions

### ✅ Auditing

- Perform regular VAPT and code review
- Enable SSRF detection rules in WAF

---

## 🧰 Tools for SSRF/RCE Testing

| Tool         | Use Case |
|--------------|----------|
| **Gopherus** | Craft gopher payloads for Redis, FCGI |
| **SSRFmap**  | SSRF scanning and internal enumeration |
| **SSRFProbe**| Detect SSRF behavior and exfiltration |
| **Burp Suite**| Intercept and tamper SSRF parameters |
| **Interact.sh**| Receive SSRF callbacks |

---

## 🔚 Conclusion

SSRF to RCE is a **powerful and stealthy** attack chain. Proper input validation, network segmentation, and protocol restrictions are **critical** defenses.

Never trust user input—especially when it can dictate **server-side** behavior.