
# wafw00f

To test if a **WAF (Web Application Firewall)** is implemented and working properly, you can use the following tools:

### **🔍 1. WAFW00F (WAF Fingerprinting)**

- **Purpose:** Detects if a WAF is present and identifies its type (e.g., Cloudflare, AWS WAF, ModSecurity).
- **Command:**
    
    ```bash
    wafw00f -a https://target.com
    ```
    
- **Installation:**
    
    ```bash
    pip install wafw00f
    ```
    
- **GitHub:** [https://github.com/EnableSecurity/wafw00f](https://github.com/EnableSecurity/wafw00f)

---

### **🚀 2. Nmap (WAF Detection via NSE Scripts)**

- **Purpose:** Uses HTTP response analysis to detect WAF presence.
- **Command:**
    
    ```bash
    nmap -p 80,443 --script=http-waf-detect target.com
    ```
    
- **Alternative (for fingerprinting WAF type):**
    
    ```bash
    nmap -p 80,443 --script=http-waf-fingerprint target.com
    ```
    

---

### **🛠 3. Burp Suite (Manual & Automated Testing)**

- **Purpose:**
    - Send various payloads to check if the WAF blocks/filters them.
    - Use **Intruder** to automate repeated requests to check for rate limiting.
    - Inspect headers like `Server`, `X-WAF-Bypass`, or responses like `403 Forbidden` or `429 Too Many Requests`.

---

### **💣 4. Nikto (Basic WAF Detection)**

- **Purpose:** Scans for web vulnerabilities and detects WAF presence via unusual responses.
- **Command:**
    
    ```bash
    nikto -h https://target.com
    ```
    

---

### **🕵️ 5. testcookie (Bypass Cloudflare & Other WAFs)**

- **Purpose:** Checks if Cloudflare or other WAFs challenge/block automation.
- **Installation:**
    
    ```bash
    pip install testcookie
    ```
    
- **Command:**
    
    ```python
    import testcookie
    session = testcookie.Session()
    response = session.get("https://target.com")
    print(response.text)
    ```
    

---

### **🔥 6. TIDoS Framework (All-in-One WAF & Security Testing)**

- **Purpose:** Analyzes WAFs, firewalls, and misconfigurations.
- **Command:**
    
    ```bash
    git clone https://github.com/0xInfection/TIDoS-Framework.git
    cd TIDoS-Framework
    python3 tidos.py
    ```
    

---

## **📌 Next Steps:**

1. **First, use WAFW00F** to confirm if a WAF exists.
2. **Then, use Burp Suite Intruder** to test how it responds to automated traffic.
3. **Finally, use Nmap & Nikto** for deeper analysis.

Let me know if you want a step-by-step guide for WAF bypass testing! 🚀




#### **WAF is Blocking Automated Requests**

- Some WAFs **detect automated tools** and block them (e.g., Cloudflare, Akamai).
- Try using a **different user-agent** or **rate-limit your requests**:
    
```
    wafw00f -a --proxy http://127.0.0.1:8080 --timeout 15 https://www.bnhs.org/

```


#### **The Site is Rate Limiting Connections**

- Try sending **a single request instead of aggressive scanning**:
```
wafw00f -r https://www.bnhs.org/

```

