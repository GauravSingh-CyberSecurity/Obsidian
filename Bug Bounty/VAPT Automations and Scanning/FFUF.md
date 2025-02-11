FFUF tutorial: https://www.freecodecamp.org/news/web-security-fuzz-web-applications-using-ffuf/

```
ffuf -u http://localhost:3000/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt

```

Note: Here, the “FUZZ” keyword is used as a placeholder. Ffuf will try to hit the URL by replacing the word “FUZZ” with every word in the wordlist.




# FFUF

The best **wordlist database** for **FFUF** depends on what you're fuzzing. Here are some **recommended wordlists** based on your target:

---

### 🔍 **1️⃣ Directory & File Discovery (Web Paths)**

**Best for:** Finding hidden directories, admin panels, login pages, backups, etc.

📌 **Top Wordlists:**

- **SecLists** (Common paths & files)
    
    ```bash
    /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt
    /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
    ```
    
- **FFUF Default Wordlist:**
    
    ```bash
    /usr/share/wordlists/dirb/common.txt
    ```
    

🔹 **FFUF Command Example:**

```bash
ffuf -u https://target.com/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt
```

---

### 🔑 **2️⃣ Subdomain Enumeration**

**Best for:** Finding subdomains of a target domain.

📌 **Top Wordlists:**

- **SecLists - Subdomains:**
    
    ```bash
    /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt
    /usr/share/wordlists/seclists/Discovery/DNS/fierce-hostlist.txt
    ```
    
- **OneListForAll - Best Subdomain List**
    
    ```bash
    https://github.com/six2dez/OneListForAll
    ```
    

🔹 **FFUF Command Example:**

```bash
ffuf -u https://FUZZ.target.com -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Host: FUZZ.target.com"
```

---

### 🔓 **3️⃣ Username & Password Bruteforce**

**Best for:** Fuzzing login pages, admin portals, or API authentication.

📌 **Top Wordlists:**

- **SecLists - Usernames & Passwords:**
    
    ```bash
    /usr/share/wordlists/seclists/Usernames/top-usernames-shortlist.txt
    /usr/share/wordlists/seclists/Passwords/Common-Credentials/10-million-password-list-top-10000.txt
    ```
    
- **RockYou (Most common passwords)**
    
    ```bash
    /usr/share/wordlists/rockyou.txt
    ```
    

🔹 **FFUF Command Example (Login Brute Force):**

```bash
ffuf -u https://target.com/login -w /usr/share/wordlists/rockyou.txt -X POST -d "username=admin&password=FUZZ"
```

---

### 📂 **4️⃣ API & Parameter Discovery**

**Best for:** Finding API endpoints & hidden parameters.

📌 **Top Wordlists:**

- **SecLists - API & Parameters:**
    
    ```bash
    /usr/share/wordlists/seclists/Discovery/Web-Content/api/api-endpoints.txt
    /usr/share/wordlists/seclists/Discovery/Web-Content/burp-parameter-names.txt
    ```
    

🔹 **FFUF Command Example (API Endpoint Fuzzing):**

```bash
ffuf -u https://target.com/api/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/api/api-endpoints.txt
```

---

### 🔥 **5️⃣ LFI, RFI & SSRF Testing**

**Best for:** Exploiting file inclusion vulnerabilities.

📌 **Top Wordlists:**

- **SecLists - LFI:**
    
    ```bash
    /usr/share/wordlists/seclists/Fuzzing/LFI/LFI-Jhaddix.txt
    ```
    
- **PayloadAllTheThings - LFI & SSRF:**
    
    ```bash
    https://github.com/swisskyrepo/PayloadsAllTheThings
    ```
    

🔹 **FFUF Command Example (LFI Testing):**

```bash
ffuf -u https://target.com/index.php?file=FUZZ -w /usr/share/wordlists/seclists/Fuzzing/LFI/LFI-Jhaddix.txt
```

---

### ✅ **Final Recommendation (Best All-in-One Wordlists)**

If you're unsure which wordlist to use, **start with these:**

```bash
/usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt
/usr/share/wordlists/rockyou.txt
/usr/share/wordlists/seclists/Fuzzing/LFI/LFI-Jhaddix.txt
```

---

### 🚀 **Pro Tip: Use `--fw` (Filter Words) to Remove False Positives**

Example:

```bash
ffuf -u https://target.com/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt --fw 0
```

This **filters out** results with **0 words** in response.

---

### 🔥 **Want More Wordlists?**

Download the latest **Seclists & Payloads:**

```bash
git clone https://github.com/danielmiessler/SecLists.git
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git
```

Hope this helps! 🚀