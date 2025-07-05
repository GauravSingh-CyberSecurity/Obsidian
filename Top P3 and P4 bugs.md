
Great question, Gaurav! Here's a list of 10 P3 and 10 P4 vulnerabilities that are realistically high-success and often awarded on platforms like Bugcrowd, HackerOne, and Intigriti, provided you explain and demonstrate impact clearly.


---

✅ Top 10 P3 Vulnerabilities That Are Frequently Awarded 💸

#	Vulnerability	Why It’s P3

1️⃣	Reflected XSS (with PoC)	User input reflected in page → can lead to phishing, session hijack
2️⃣	Stored XSS (low-impact area)	Comment section, profile, etc.
3️⃣	IDOR (Insecure Direct Object Reference)	Access another user’s data (like invoice, files)
4️⃣	CORS Misconfiguration (with sensitive data exposed)	Wildcard origins or missing credential validation
5️⃣	Session Fixation	Reuse of session IDs via login links
6️⃣	Sensitive Info in JavaScript files	API keys, credentials, tokens exposed
7️⃣	Misconfigured S3 buckets or open storage	Accessible private files
8️⃣	Exposed admin or debug endpoints	E.g., /debug, /admin, /console
9️⃣	Weak password reset logic	Predictable token, missing rate limit
🔟	OAuth Misconfigurations	Bypass login, redirect flaws, open redirects with redirect_uri


> 💡 Impact must be clearly demonstrated with real data access or session manipulation.




---

✅ Top 10 P4 Vulnerabilities That Are Often Awarded 🪙

#	Vulnerability	Why It’s P4

1️⃣	Missing Security Headers	No Content-Security-Policy, X-Frame-Options, etc.
2️⃣	Open Redirects	Can redirect users to phishing domains
3️⃣	Autocomplete Enabled on Password Fields	Insecure UX flaw
4️⃣	Insecure Cookie Flags	Missing HttpOnly, Secure, SameSite
5️⃣	Clickjacking	No X-Frame-Options allows clickjacking attack
6️⃣	Information Disclosure (Emails, usernames)	Seen in response or error
7️⃣	Verbose Error Messages / Stack Trace	Tech info leakage
8️⃣	Exposed Internal IPs	Found in headers, comments, responses
9️⃣	Unvalidated Redirects in OAuth Flows	Redirect URI can be attacker-controlled
🔟	Rate-Limit Missing (Low-Risk Endpoint)	No limit on login attempts, but no bypass shown


> 🔍 Even these P4s are accepted if well-documented and reported professionally.




---

📌 Pro Tip: Add These in Every Report

✅ Summary of issue
✅ PoC (Screenshot or Burp Repeater example)
✅ Clear explanation of how attacker can exploit
✅ Suggested fix or impact escalation idea


---

🚀 BONUS: Smart Strategy to Get Paid

Step	Focus

🔍 Scan URLs with Dalfox, Burp, Nuclei for quick P3/P4	
🧠 Manually test logic/roles (IDOR, OAuth redirect)	
🛠️ Use Autorize, Param Miner, Logger++	
📤 Submit only with complete PoC and context	
🗂 Track accepted bug types on HackerOne Reports and Bugcrowd Disclosures	



---

Would you like a ready-made checklist (PDF or Notion format) of these 20 bugs with tools + PoC examples for each?

