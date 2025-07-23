Here’s a **comprehensive list of common web attack vectors** along with **clear and actionable remediations** for each one:

---

### ✅ 1. **SQL Injection (SQLi)**

**Remediation:**

- Use **parameterized queries** or **ORMs** (e.g., SQLAlchemy, Django ORM).
- **Validate and sanitize inputs** (whitelist where possible).
- Use **least privilege** for database accounts.
- Enable **Web Application Firewalls (WAF)**.

---

### ✅ 2. **Cross-Site Scripting (XSS)**

**Remediation:**

- **Escape output** in HTML, JS, URLs, and attributes (`<%= %>` instead of `<% %>` in templates).
- Implement **Content Security Policy (CSP)**.
- Use **frameworks** that auto-sanitize (e.g., React, Angular).
- **Sanitize user inputs** on both client and server.

---

### ✅ 3. **Server-Side Request Forgery (SSRF)**

**Remediation:**

- **Whitelist allowed domains/IPs** for outgoing requests.
- Block access to **internal metadata/IP ranges** (`169.254.x.x`, `localhost`, `127.0.0.1`).
- Use **network segmentation** and **firewall rules**.
- Log and alert on suspicious requests.

---

### ✅ 4. **Remote Code Execution (RCE)**

**Remediation:**

- Avoid using user input in system commands.
- Use **safe APIs** (no `eval`, `exec`, or `os.system`).
- Run services with **minimum privileges**.
- Use **input validation** and **sandboxing**.

---

### ✅ 5. **Insecure Direct Object Reference (IDOR)**

**Remediation:**

- Implement **authorization checks** for every object access.
- Use **indirect references** (e.g., UUIDs instead of numeric IDs).
- Use **access control mechanisms** server-side only.

---

### ✅ 6. **File Inclusion (LFI/RFI)**

**Remediation:**

- Never pass user input directly to file paths.
- Disable **`allow_url_include`** in PHP.
- **Validate file names/paths** strictly (use allowlists).
- Isolate file access to **designated safe directories**.

---

### ✅ 7. **Auth and Access Control Bypass**

**Remediation:**

- Enforce **server-side session/token validation**.
- Implement **role-based access controls (RBAC)**.
- Never rely on client-side controls for auth.
- Regularly **test all endpoints** for auth bypass.

---

### ✅ 8. **XML External Entity (XXE)**

**Remediation:**

- **Disable external entity resolution** in XML parsers.
- Use **JSON instead of XML** when possible.
- Use **secure libraries** (e.g., `defusedxml` in Python).
- Validate content-type headers.

---

### ✅ 9. **Command Injection**

**Remediation:**

- Avoid direct shell calls using user input.
- Use **safe command libraries** (e.g., Python's `subprocess.run()` with `args` list).
- Apply **input validation and escaping**.
- Run services with **limited OS privileges**.

---

### ✅ 10. **API Misconfiguration**

**Remediation:**

- Implement **rate limiting** and **authentication**.
- Disable unused endpoints and methods.
- Enforce **schema validation**.
- Do not expose **internal error messages**.

---

### ✅ 11. **Broken Object-Level Authorization (BOLA)**

**Remediation:**

- Check if the user is **authorized** for every object access.
- Use **context-aware access checks** (user ID, role, etc.).
- Avoid relying on client-side object IDs.

---

### ✅ 12. **Broken Authentication**

**Remediation:**

- Use **MFA** (multi-factor authentication).
- Use **secure password policies** and **hashing** (`bcrypt`, `argon2`).
- Implement **brute-force protections** (lockouts, rate limits).
- Validate session tokens thoroughly.

---

### ✅ 13. **Cross-Site Request Forgery (CSRF)**

**Remediation:**

- Use **anti-CSRF tokens** in forms and headers.
- Use **SameSite cookies** (`SameSite=Lax/Strict`).
- Validate the **`Origin`** and **`Referer`** headers.
- Prefer **secure methods like JWTs with double submit tokens**.

---

### ✅ 14. **Subdomain Takeover**

**Remediation:**

- Remove **dangling DNS entries** (CNAME pointing to non-existent services).
- Regularly **audit DNS records**.
- Use **tools like `Subjack`** to detect vulnerable subdomains.
- Set **proper DNS TTLs** and access control on DNS providers.

---

### ✅ 15. **Clickjacking**

**Remediation:**

- Use `X-Frame-Options: DENY` or `SAMEORIGIN`.
- Implement **Content Security Policy (CSP)** frame-ancestors directive.
- Employ **frame busting JavaScript** (secondary measure).

---

### ✅ 16. **Session Fixation**

**Remediation:**

- **Regenerate session ID** upon login.
- Use **secure cookies** (`HttpOnly`, `Secure`, `SameSite`).
- Invalidate old sessions when credentials change.

---

### ✅ 17. **CORS Misconfiguration**

**Remediation:**

- Set **specific allowed origins**, not `*`.
- Disable **`Access-Control-Allow-Credentials`** if not needed.
- Use **strict CORS headers** based on endpoint sensitivity.

---

### ✅ 18. **Insecure Deserialization**

**Remediation:**

- **Avoid deserializing user input**; use formats like JSON.
- Implement **integrity checks** (e.g., HMAC or digital signatures).
- Use **safe libraries** that enforce type checks.
- Sanitize input before passing to deserialization logic.

---

### ✅ 19. **Web Shells**

**Remediation:**

- **Restrict file uploads** to safe file types and paths.
- Scan uploaded files with **AV and YARA rules**.
- **Disable execution** of files in upload directories.
- Regularly monitor for **suspicious file activity**.

---

🔐 **General Defenses for All Above:**

- Implement **WAF** and **runtime security agents** (e.g., CrowdStrike, Falco).
- Use **Security Headers** (`CSP`, `HSTS`, `X-Frame-Options`, etc.).
- Apply **regular patching**, **dependency scanning**, and **SAST/DAST**.
- Implement **logging and alerting** on security events.

---

Would you like a PDF/visual chart of these for quick reference in an interview or report?