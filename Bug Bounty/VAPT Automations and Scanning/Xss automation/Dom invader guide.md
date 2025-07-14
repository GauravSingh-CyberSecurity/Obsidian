Here you go, Gaurav — a **step-by-step guide to using DOM Invader in Burp Suite Pro** to detect **DOM-based XSS**, including automatic payload injection and source-to-sink tracing.

---

# ✅ DOM Invader — Step-by-Step Usage Guide

> **Goal**: Detect DOM-based XSS vulnerabilities by tracing untrusted input (sources) into dangerous functions (sinks) and auto-injecting payloads.

---

## 🔹 Step 1: Launch Burp Embedded Browser

- Open Burp Suite Pro
- Go to:
    
    ```
    Proxy → Intercept → Open Browser
    ```
    

This browser is Chromium-based and pre-instrumented with DOM Invader.

---

## 🔹 Step 2: Enable DOM Invader Features

Go to:

```
Project Options → Misc → DOM Invader
```

Make sure the following are enabled:

|Option|Status|
|---|---|
|✅ Enable DOM Invader|✔️|
|✅ Show DOM Invader tab in DevTools|✔️|
|✅ Inject test payloads into known sources|✔️|
|✅ Set breakpoints on DOM sinks|(Optional ✔️)|

---

## 🔹 Step 3: Visit the Target Page

Using the Burp browser, navigate to:

```
https://target.com/page
```

DOM Invader will automatically:

- Inject XSS test payloads into:
    - `location.search` → `?input=<svg onload=alert(1)>`
    - `location.hash` → `#<img src=x onerror=alert(1)>`
    - `document.referrer`, `window.name`, etc.
- Highlight **DOM sinks** like `innerHTML`, `eval`, `document.write`

---

## 🔹 Step 4: Open DevTools and Use DOM Invader Tab

- Right-click → **Inspect**
- You’ll see a **DOM Invader tab** inside DevTools

This tab shows:

- List of **input sources** (e.g., hash, query)
- **DOM sinks** reached (e.g., innerHTML)
- Whether the input flows to the sink (taint tracking)
- Payloads that were auto-tested

---

## 🔹 Step 5: Interpret Visual Indicators

|Icon|Meaning|
|---|---|
|⚠️ Red exclamation|Dangerous sink reached with tainted input (possible XSS)|
|✅ Green check|Input reached sink but appears safe or sanitized|
|⚡ Lightning bolt|Execution triggered (e.g., alert popped, breakpoint hit)|

---

## 🔹 Step 6: Set Breakpoints (Optional)

If breakpoints are enabled:

- When tainted input hits a sink like `element.innerHTML`, the browser **will pause**
- You can inspect the stack and see **what code is responsible**

---

## 🔹 Step 7: Customize Payloads (Optional)

You can define custom payloads in:

```
Project Options → Misc → DOM Invader → Payloads
```

Examples:

```html
<script>alert(document.domain)</script>
"><img src=x onerror=alert(1)>
<svg/onload=alert(1337)>
```

---

## 🔹 Step 8: Confirm DOM-based XSS

- If DOM Invader shows input reaching a sink without encoding/sanitization
- And payload is rendered as executable JS or HTML ✅ You’ve likely found **DOM XSS**

---

## 🧪 Bonus Tip: Combine with LinkFinder

Before using DOM Invader, you can run:

```bash
python3 linkfinder.py -i https://target.com/app.js -o cli
```

To extract possible input-sink flows for manual testing.

---

## ✅ Summary Flow

```
Launch Burp Browser
→ Enable DOM Invader
→ Visit URL
→ Injects payloads automatically
→ Highlights DOM sinks
→ Confirms XSS if executed
→ Optional breakpoints & payload customization
```

---

Would you like a Mermaid flowchart or printable `.md` guide for your bug bounty toolkit?