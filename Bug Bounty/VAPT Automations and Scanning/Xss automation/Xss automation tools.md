- Xss strike (fuzzer)

- Dalfox (scanner)

- Dom invader

- deep scrub 

Here’s a complete and categorized list of **tools used for XSS discovery, analysis, and exploitation**, covering **Reflected, Stored, DOM-based, and Blind XSS** — both automated and manual.

---

# 🛡️ Complete XSS Toolkit (Offensive & Analysis)

---

## 🔍 Recon & Parameter Discovery

|Tool|Use Case|
|---|---|
|`gau`|Get all URLs from archive (Wayback, Common Crawl)|
|`waybackurls`|Fetch historical URLs from Wayback Machine|
|`hakrawler`|Crawls and finds endpoints from a URL|
|`httpx`|Check which URLs are alive|
|`subfinder`|Discover subdomains|
|`ParamSpider`|Find parameters in discovered URLs|
|`Arjun`|Discover hidden GET/POST parameters|
|`GF` + XSS pattern|Filter out endpoints with injectable parameters|

---

## 📄 JavaScript Static Analysis (DOM XSS)

|Tool|Use Case|
|---|---|
|`LinkFinder`|Extract JS URLs, sources & sinks|
|`grep`, `ripgrep`|Manually find `innerHTML`, `eval`, etc.|
|`Retire.js`|Detect vulnerable JS libraries|
|`DeepScrub`|Static taint tracking in JS + optional GPT|
|`jsbeautifier`|Beautify JS code for easier review|

---

## 🤖 Automated XSS Scanners

|Tool|Use Case|
|---|---|
|**Burp Suite Pro**|Industry-standard; DOM/Reflected/Stored XSS detection|
|`OWASP ZAP`|Open-source scanner; supports scripting|
|`Nuclei`|Fast scanning with custom XSS templates|
|`XSStrike`|Intelligent, context-aware fuzzing & payload gen|
|`Dalfox`|XSS scanner focused on fast, accurate payload testing|
|`XSS-Scanner`|CLI scanner for quick testing|

---

## 🧠 DOM-based XSS Testing Tools

|Tool|Use Case|
|---|---|
|**Burp DOM Invader**|Trace source → sink, inject payloads (Burp browser)|
|`DeepScrub`|Analyze JS files statically|
|`xsser`|DOM XSS support (older but useful)|
|`Puppeteer`|Automate rendering & payload execution check|
|`Chrome DevTools`|Inspect source → sink behavior manually|

---

## 🕵️ Blind XSS Tools

|Tool|Use Case|
|---|---|
|`Interact.sh`|Receive OOB payload callbacks (JS, DNS, HTTP)|
|`Burp Collaborator`|Built-in to Burp Pro; detect blind XSS|
|`bxss.me`|Free blind XSS service|
|`XSS Hunter Legacy`|Self-hosted blind XSS platform|

---

## 📦 Payload Libraries & Fuzzers

|Tool/File|Use Case|
|---|---|
|`SecLists`|Huge list of XSS payloads|
|`PayloadsAllTheThings`|XSS payloads by context (attr, tag, js)|
|`FuzzDB`|XSS and WAF bypass payloads|
|`XSStrike`|Also generates custom payloads|
|`Dalfox -w`|Use with wordlists|

---

## 🔬 Manual Testing Tools

|Tool|Use Case|
|---|---|
|**Burp Repeater**|Manual request crafting and rendering|
|`curl`, `httpie`|Test reflected payloads from CLI|
|`Chrome DevTools`|Inspect JS context, HTML rendering|
|`DOMPurify`|Compare sanitized vs. raw output|
|`xsshunter.xss.ht`|Third-party payload catchers|

---

## 🧰 Utility Helpers

|Tool|Use Case|
|---|---|
|`js-xss-ai-scanner`|Custom AI-assisted JS XSS review|
|`JSPayloadGen`|Encode/obfuscate XSS payloads|
|`xsser-gui`|UI for XSStrike and classic xsser|
|`WebSorrow`|Multi-vector scanner (XSS, LFI, etc)|
|`XSS Radar (browser ext)`|Legacy DOM scanner in browser|

---

## 🧪 Testing Environments

|Tool / Project|Use Case|
|---|---|
|`bWAPP` / `DVWA`|Practice XSS locally|
|`HackTheBox Web Challenges`|Realistic XSS scenarios|
|`PortSwigger Labs`|Free lab to test XSS types|
|`PayloadBox XSS`|Ready-made payload generators|

---

## 🧠 Want Everything in One CLI Pipeline?

Run this:

```bash
gau example.com | httpx | gf xss | dalfox pipe --deep-dive
```

💥 That’s full pipeline:

- Recon → Live links → XSS params → Auto scan

---

Would you like this exported as:

- 📄 Markdown file
- 🧠 Obsidian vault
- ✅ JSON config for your Burp/Nuclei scans
- 🗺️ Mindmap format?

Let me know how you want to use this toolkit.