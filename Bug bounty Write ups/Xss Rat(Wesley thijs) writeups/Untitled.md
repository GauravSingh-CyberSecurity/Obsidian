

Drop your fav polyglot

Mine is simple and does not test all contexts but is effective:
```
'"><img src=x>${{7*2}}
```

**Explanation**:

- '" : JS injection
- `'">` : html tag attribute
- `<img src=x>` : brokenimage html injection
- '" : SQLi 
- `${{7*2}}` : CSTI and SSTI



---
---

What is a polygot?


In **bug bounty hunting**, a **polyglot** (or **polyglot payload**) refers to:

> **A single piece of code or payload that is valid and executable in multiple contexts or interpreters (e.g., HTML, JavaScript, CSS, JSON, XML, SQL, etc.), allowing it to trigger vulnerabilities in multiple layers of a web application.**

---

### 🔍 Why Polyglots Matter in Bug Bounties:

Polyglots are powerful in real-world attacks because:

- They **bypass filters and WAFs** by fitting into different syntax contexts.
- They **trigger multiple types of vulnerabilities** simultaneously (e.g., XSS + SQLi).
- They **evade detection**, making exploitation stealthier and more effective.

---

### ⚔️ Common Use-Cases of Polyglots in Bug Bounty:

|Vulnerability Type|Use of Polyglot|
|---|---|
|**Cross-Site Scripting (XSS)**|Payload works inside `<script>`, event handlers, image src, etc.|
|**SQL Injection (SQLi)**|Payload can be interpreted in different DB engines like MySQL + PostgreSQL|
|**File Upload Bypass**|File that's both a valid image and a valid script (`.jpg` + `.php`)|
|**MIME Type Confusion**|Bypass upload restrictions by crafting dual-nature files|
|**Content Sniffing Attacks**|Files that trigger XSS when interpreted differently by browsers|
|**CSS Injection + XSS**|Combining HTML/CSS/JS into one payload in a stylesheet or attribute|

---

### 🧪 Example: XSS Polyglot Payload

```html
"><script>alert(1)</script>
```

Can work in:

- HTML attribute context
- JavaScript context
- URL query parameters

A more **advanced polyglot** might look like:

```html
"><svg/onload=alert(1)>'
```

This payload:

- Ends HTML attributes
- Opens SVG (valid HTML)
- Injects JS via `onload`

---

### 🛠 Tools & Resources:

- 🔧 [**XSS Polyglots**](https://portswigger.net/research/the-art-of-xss) – By James Kettle (Burp Suite)
- 💣 [`payloadsAllTheThings`](https://github.com/swisskyrepo/PayloadsAllTheThings) – Huge repo of polyglots
- ⚔️ Tools: `XSStrike`, `Dalfox`, `Fuzzing`, `Burp Suite Intruder` (for context testing)

---

### 🧠 TL;DR:

> A **polyglot** in bug bounty is a single payload that works in multiple interpreters or contexts, allowing attackers (and hunters) to **trigger or test multiple vulnerability types** simultaneously or bypass strict filters.

Let me know if you want a cheat sheet of polyglots for different bugs like XSS, LFI, SQLi, etc.