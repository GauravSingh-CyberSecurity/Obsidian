Here’s a step-by-step guide to using **Nikto** for scanning a target with various configurations and options:

---

### **Step 1: Basic Nikto Scan**

This performs a simple scan of the target.

**Command:**

```bash
nikto -h https://staging.digicompany.in
```

**Purpose:**

- Scans the target for basic vulnerabilities, misconfigurations, and insecure files.

---

### **Step 2: Enable Verbose Output**

To get detailed output, use the verbose mode.

**Command:**

```bash
nikto -h https://staging.digicompany.in -Display V
```

**Purpose:**

- Shows detailed information about the scan, including each test being performed.

---

### **Step 3: Perform a Deep Scan (All Tests)**

Enable all available Nikto plugins and checks for a comprehensive scan.

**Command:**

```bash
nikto -h https://staging.digicompany.in -Tuning x
```

**Purpose:**

- `-Tuning x` enables all scan types, such as file upload tests, injections, and misconfigurations.

---

### **Step 4: Automated Scan Without Prompts**

Suppress all prompts for a completely automated scan.

**Command:**

```bash
nikto -h https://staging.digicompany.in -ask no
```

**Purpose:**

- Ensures that the scan runs without any manual intervention.

---

### **Step 5: Save Results to a File**

Export the results to a file in plain text or HTML for later analysis.

**Command:**

```bash
nikto -h https://staging.digicompany.in -output scan_results.txt
```

**For HTML Output:**

```bash
nikto -h https://staging.digicompany.in -output scan_results.html
```

**Purpose:**

- Saves scan results to a file for documentation or reporting.

---

### **Step 6: Scan a Specific Port**

If the web server is running on a non-standard port, specify it using the `-p` option.

**Command:**

```bash
nikto -h https://staging.digicompany.in -p 8080
```

**Purpose:**

- Scans a service running on a non-default port, such as 8080 or 8443.

---

### **Step 7: Customize Headers**

Add custom headers to the scan request, useful for bypassing WAF or simulating specific users.

**Command:**

```bash
nikto -h https://staging.digicompany.in -useragent "Mozilla/5.0"
```

**Purpose:**

- Changes the User-Agent to avoid detection or simulate a real browser.

---

### **Step 8: Perform SSL-Specific Tests**

Scan a site for SSL/TLS vulnerabilities and misconfigurations.

**Command:**

```bash
nikto -h https://staging.digicompany.in -ssl
```

**Purpose:**

- Checks SSL/TLS configurations, certificates, and potential weaknesses.

---

### **Step 9: Use Plugins for Extended Tests**

Enable specific plugins for targeted scans.

**Command:**

```bash
nikto -h https://staging.digicompany.in -Plugins tests
```

**Purpose:**

- Runs extended plugin-based scans for advanced vulnerability detection.

---

### **Step 10: Show Progress Status**

Add progress and verbose output to track the scan's status.

**Command:**

```bash
nikto -h https://staging.digicompany.in -ask no -Display PV
```

**Purpose:**

- Shows which plugins are running and their current progress.

---

### **Step 11: Use a Proxy**

Route the scan through a proxy for monitoring or anonymity.

**Command:**

```bash
nikto -h https://staging.digicompany.in -useproxy http://127.0.0.1:8080
```

**Purpose:**

- Directs the scan through tools like Burp Suite or a SOCKS proxy.

---

Would you like further help analyzing the results or creating custom Nikto configurations?