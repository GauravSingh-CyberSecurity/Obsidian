
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



### **💡 Alternative Tools to Test WAF**

If WAFW00F fails, try:

1. **Nmap WAF detection**:
    
    ```bash
    nmap -p 80,443 --script=http-waf-detect www.bnhs.org
    ```
    
2. **Nikto (Web scanner that detects WAFs)**:
    
    ```bash
    nikto -h https://www.bnhs.org/
    ```
    
3. **Burp Suite**
    - Send normal traffic through Burp.
    - If you see **403 Forbidden** or **429 Too Many Requests**, the WAF is blocking you.

Let me know what the results show! 🚀



**The Error:** 
[*] Checking https://www.bnhs.org/ ERROR:wafw00f:Something went wrong HTTPSConnectionPool(host='www.bnhs.org', port=443): Read timed out. (read timeout=7)

Your `curl -I` response confirms that **the website is up**, but WAFW00F is failing due to a timeout. This suggests that:

1. The site **takes longer than 7 seconds** to respond to WAFW00F.
2. The **WAF might be blocking automated scanning** tools.
3. There is **some network filtering or rate-limiting** in place.

---

### **🔍 How to Troubleshoot & Bypass This?**

#### ✅ **1. Increase Timeout & Use a Proxy**

Try increasing the timeout and routing traffic through **Burp Suite** or **a proxy**:

```bash
wafw00f -a --timeout 20 --proxy http://127.0.0.1:8080 https://www.bnhs.org/
```

🔹 This will:

- Increase the timeout to **20 seconds** (instead of default 7).
- Send traffic through **Burp Suite** (if running on port 8080), allowing you to inspect responses.

---

#### ✅ **2. Check with Nmap (Alternative to WAFW00F)**

Since WAFW00F is struggling, use `nmap` with the WAF detection script:

```bash
nmap -p 80,443 --script=http-waf-detect www.bnhs.org
```

🔹 If a WAF is present, **this will fingerprint it**.

---

#### ✅ **3. Test Manually with Different User-Agents**

Some WAFs block specific **user-agents** used by scanning tools. Try:

```bash
wafw00f -a -H "User-Agent: Mozilla/5.0" https://www.bnhs.org/
```

🔹 This makes the request look like **a normal browser visit** instead of a scanner.

---

#### ✅ **4. Look for WAF Headers in Your `curl` Output**

From your `curl -I` response, the site includes **security headers** like:

- **X-Frame-Options: SAMEORIGIN**
- **Strict-Transport-Security**
- **Content-Security-Policy**

But **no obvious WAF headers** like `X-Sucuri-ID`, `X-CDN`, or `Server: cloudflare`.  
This means **either there's no WAF**, or it's **not revealing itself**.

---

#### ✅ **5. Check for Rate Limiting (Potential Block)**

Try sending **multiple `curl` requests** and see if the site blocks you:

```bash
for i in {1..10}; do curl -I https://www.bnhs.org/; sleep 2; done
```

🔹 If **some requests fail** (403, 429), then **rate limiting is active**.

---

### **🛠️ Alternative Tools for WAF Detection**

If WAFW00F is failing, try:

1️⃣ **Nmap WAF Detection**

```bash
nmap -p 443 --script=http-waf-detect https://www.bnhs.org/
```

2️⃣ **Nikto (WAF + Security Scanner)**

```bash
nikto -h https://www.bnhs.org/
```

3️⃣ **Burp Suite Passive Analysis**

- Send a request to the site via **Burp Suite** and check the headers for **WAF clues**.

---

### **🔚 Summary: What to Do Next?**

- **Increase timeout:** `--timeout 20`
- **Use a proxy (Burp Suite):** `--proxy http://127.0.0.1:8080`
- **Test with Nmap:** `nmap -p 80,443 --script=http-waf-detect www.bnhs.org`
- **Check manually for blocking (Rate Limit Test)**

Try these and let me know what results you get! 🚀





**The error:**
```
C:\home\kali> wafw00f -a --timeout 20 --proxy http://127.0.0.1:8080 https://www.bnhs.org/ ______ / \ ( Woof! ) \ ____/ ) ,, ) (_ .-. - _______ ( |__| ()``; |==|_______) .)|__|` / (' /|\ ( |__| ( / ) / | \ . |__| \(_)_)) / | \ |__| ~ WAFW00F : v2.3.1 ~ The Web Application Firewall Fingerprinting Toolkit [*] Checking https://www.bnhs.org/ [+] Generic Detection results: ERROR:wafw00f:Something went wrong HTTPSConnectionPool(host='www.bnhs.org', port=443): Read timed out. (read timeout=20) [*] The site https://www.bnhs.org/ seems to be behind a WAF or some sort of security solution [~] Reason: Blocking is being done at connection/packet level. [~] Number of requests: 2 

C:\home\kali>
```

The error confirms that **BNHS.org is blocking WAFW00F at the connection/packet level**, meaning:

✅ **A WAF or security solution is present.**  
❌ **Requests are likely being dropped or rate-limited.**

---

### **🔍 Next Steps: Bypassing WAF Blocking**

Since **requests are being blocked before a response is received**, try these **WAF evasion techniques**:

#### **1️⃣ Use a Different User-Agent**

Some WAFs block requests based on **user-agent strings**. Try:

```bash
wafw00f -a -H "User-Agent: Mozilla/5.0" https://www.bnhs.org/
```

🔹 **Mimics a normal browser request** instead of a scanner.

---

#### **2️⃣ Use a Tor Proxy (Hides IP)**

If your IP is **rate-limited**, use **Tor** as a proxy:

```bash
tor & # Start Tor
wafw00f -a --proxy socks5h://127.0.0.1:9050 https://www.bnhs.org/
```

🔹 **Masks your IP and rotates requests** through different Tor nodes.

---

#### **3️⃣ Try a Manual WAF Test (Nmap)**

Since WAFW00F **can't fingerprint the WAF**, try **Nmap's WAF detection script**:

```bash
nmap -p 443 --script=http-waf-detect www.bnhs.org
```

🔹 **Checks for WAF behavior** using various detection techniques.

---

#### **4️⃣ Use Burp Suite to Identify Blocking**

1. **Intercept a request to BNHS.org in Burp Suite.**
2. **Change the request method & headers** (e.g., remove `User-Agent`).
3. **Check if certain patterns trigger blocking.**

🔹 **If some requests pass and others don’t, it's likely a signature-based WAF.**

---

#### **5️⃣ Use Nikto for Passive Analysis**

Nikto might reveal **server misconfigurations and security headers**:

```bash
nikto -h https://www.bnhs.org/
```

🔹 **Can detect WAF-related behaviors and security features.**

---

### **🔚 Conclusion**

- ✅ **BNHS.org has a WAF blocking active scans.**
- 🛠️ **Bypass using a different User-Agent, Tor, or manual testing.**
- 🔍 **Use Nmap, Burp Suite, or Nikto for further analysis.**

Try these steps and let me know what results you get! 🚀




To check if a WAF if present:
#### **Send Malicious Payloads**

Use **Burp Suite Intruder** or **SQLmap** to send WAF-detecting payloads:
```
sqlmap -u "https://www.bnhs.org/?id=1" --level=5 --risk=3

```

If **requests get blocked**, a WAF is active.


















