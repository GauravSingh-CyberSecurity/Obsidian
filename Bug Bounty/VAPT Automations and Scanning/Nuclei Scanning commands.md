Your **Nuclei scan is stopping at 21%** due to a high number of **errors (1044+)**, which might be causing the process to halt or slow down. Here’s how you can troubleshoot and ensure it runs **100%**:

---

### 🔎 **Possible Reasons & Fixes**

#### **1️⃣ Network Issues (Timeouts or Blocking)**

📌 **Problem:** The target website may be **blocking your requests** due to high traffic or rate limiting.  
🔧 **Fix:**

- Reduce concurrency (`-c`) to avoid getting blocked:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 10 -stats
    ```
    
- Use a **proxy** or **rotate IPs** using Tor:
    
    ```bash
    proxychains nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/
    ```
    

---

#### **2️⃣ Server-Side Rate Limiting**

📌 **Problem:** The WAF or server is **throttling** or **blocking** multiple requests.  
🔧 **Fix:**

- Use the **throttle (`-rate-limit`)** option:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 10 -rate-limit 2
    ```
    

---

#### **3️⃣ SSL/TLS Issues**

📌 **Problem:** SSL misconfigurations or **invalid certificates** could cause errors.  
🔧 **Fix:**

- Force **insecure mode** to ignore SSL/TLS errors:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 40 -stats -ni
    ```
    
    `-ni` = **No TLS verification**

---

#### **4️⃣ WAF Blocking Requests**

📌 **Problem:** The site might have a **Web Application Firewall (WAF)** blocking automated scans.  
🔧 **Fix:**

- Use **random user-agents** to evade detection:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 20 -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
    ```
    
- **Try a delay (`-delay 500ms`)**:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 20 -delay 500ms
    ```
    

---

#### **5️⃣ Template or Request Errors**

📌 **Problem:** Some **Nuclei templates** might be outdated or broken.  
🔧 **Fix:**

- Update your **Nuclei templates**:
    
    ```bash
    nuclei -ut
    ```
    
- Run a **scan with only critical templates**:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/vulnerabilities/ -target https://www.bnhs.org/
    ```
    

---

#### **6️⃣ Debugging Errors**

📌 **Problem:** Need to see what’s causing errors in detail.  
🔧 **Fix:**

- Run in **verbose mode (`-debug`)** to check errors:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 40 -debug
    ```
    
- Save logs to a file:
    
    ```bash
    nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 40 -o scan.log
    ```
    

---

### ✅ **Final Recommended Command**

If the site is **blocking you**, try:

```bash
nuclei -t /home/kali/.local/nuclei-templates/ -target https://www.bnhs.org/ -c 10 -rate-limit 3 -ni -H "User-Agent: Mozilla/5.0" -o results.txt
```

This reduces **errors**, avoids **WAF detection**, and ensures **full execution**.




















To display the percentage of progress during scanning with **Nuclei**, you can use the **`-stats`** flag. Here's the command optimized for an 8 GB RAM device and includes progress statistics:

### Command:
```
nuclei -t /home/kali/.local/nuclei-templates/ -target <target> -o nuclei_results.txt -c 40 -stats
```


### Explanation:

1. **`-stats`**: Displays live statistics, including the percentage of scan completion and request rate.
2. **`-c 20`**: Limits concurrency to 40 threads, optimal for 8 GB RAM.
3. **`-o nuclei_results.txt`**: Saves the output to a file.



### For Multiple Targets with Progress Stats:
```
nuclei -t /home/kali/.local/nuclei-templates/ -list targets.txt -o nuclei_results.txt -c 40 -stats
```


# Nuclei WAF detection

nuclei -t /home/kali/.local/nuclei-templates/http/technologies/waf-detect.yaml,/home/kali/.local/nuclei-templates/http/technologies/secui-waf-detect.yaml,/home/kali/.local/nuclei-templates/dns/dns-waf-detect.yaml,/home/kali/.local/nuclei-templates/http/fuzzing/waf-fuzz.yaml,/home/kali/.local/nuclei-templates/cloud/aws/cloudfront/cloudfront-integrated-waf.yaml,/home/kali/.local/nuclei-templates/http/vulnerabilities/wordpress/wordpress-wordfence-waf-bypass-xss.yaml -target <target> -o nuclei_results.txt -c 40 -stats





















