

I recently received a €250 bounty in a public Bug Bounty program on Intigriti. This outcome reinforces that effective asset enumeration and reconnaissance are crucial for significant discoveries and impacts.

In less than 15 minutes of analyzing the scope, I identified Firewall and Endpoint Management Server (EMS) panels publicly exposed on a subdomain of an in-scope asset.

The particularity of this discovery lies in the fact that these endpoints were not indexed on Google and were not accessible via conventional dorking techniques. The identification was made possible through an in-depth SSL/TLS certificate enumeration analysis, a methodology that often reveals hidden assets that remain invisible through superficial recon approaches.

The public exposure of these critical administrative interfaces represents a security misconfiguration with inherent risks. Initially, the report was classified with low criticality by the company's team. However, after a subsequent re-evaluation, the team confirmed that the actual criticality was Medium. Despite platform limitations to adjust the severity, a bonus was granted, reflecting the recognition of the revised severity.

***==Name vuln, how he find, what exactly he did that was rewarded==*** :-


Here's a breakdown of what happened — including **the vulnerability, the method used to find it,** and **what exactly was rewarded**:

---

### ✅ **VULNERABILITY**

**Public Exposure of Firewall and Endpoint Management Server (EMS) Admin Panels**

- This falls under:
    - **Security Misconfiguration (CWE-16 / OWASP A05:2021)**
    - **Exposed Administrative Interfaces**
    - **Unnecessary Services Running Publicly**

These admin panels should **never be publicly accessible**. If found by attackers, they could:

- Attempt login brute force
- Exploit known CVEs on the EMS/Firewall
- Gain insight into the internal infrastructure
- Lead to lateral movement or full compromise if further vulnerabilities are present

---

### 🔍 **HOW HE FOUND IT**

**Not via Google Dorking or OSINT.** Instead, he used **SSL/TLS Certificate Enumeration** — an **advanced reconnaissance technique**.

#### ⚙️ Likely Steps Taken:

1. **Scope Mapping** — Take the in-scope domain (e.g., `company.com`) or IP range.
2. **Enumerated SSL/TLS Certificates** using:
    - `crt.sh` or `Censys.io` or `Shodan` with `ssl.cert.subject.CN` filters
    - `Subfinder` / `Amass` with `-active` or custom resolvers
    - Tools like:
        - `tls-scan`
        - `zgrab2`
        - `certstream`
        - `masscan` with `443` and then grabbing banners with `nmap` or `httprobe`
3. **Found Hostnames / Subdomains** from SSL Cert fields (CN or SAN)
    - Example: `fw-admin.company.com`, `ems-panel.company.com`
4. **Manual Visit** — Confirmed presence of firewall/EMS login pages on HTTP(S)
    - These panels were **not indexed on Google**, so wouldn’t show up with dorks.

---

### 🎯 **WHAT EXACTLY WAS REWARDED**

- **Discovery of public, sensitive administrative interfaces** (Firewall + EMS)
- These were **meant to be internal-only** — and **exposing them is a misconfiguration** with real-world risk
- Even if **no RCE or login bypass was attempted**, the **identification and responsible disclosure of these sensitive endpoints** was impactful

---

### 💶 Bounty Breakdown

- **Initial Severity**: Low (since no exploit shown)
- **Re-evaluated Severity**: Medium (due to the risk and sensitivity of the assets exposed)
- **€250 bounty + bonus** granted — reflecting acknowledgment of:
    - Smart recon methodology
    - Asset discovery skill
    - Security impact

---

### 🧠 Takeaway (What You Can Learn)

- **Hidden assets ≠ secure assets**
- **SSL/TLS cert enumeration** can expose **undiscovered subdomains and infrastructure**
- Don’t rely only on dorks or passive recon — active probing + creative cert analysis = gold

---

Would you like me to show the full toolchain or command examples for doing this type of SSL enumeration and asset discovery?
