Owasp top 10 business logic flaws:

https://owasp.org/www-project-top-10-for-business-logic-abuse/?utm_source=chatgpt.com






Here’s a comprehensive list of Business Logic Vulnerabilities (BLVs) commonly found in VAPT (Vulnerability Assessment and Penetration Testing) engagements — especially for web applications, mobile apps, and APIs.


---

🔍 What are Business Logic Bugs?

Business Logic Vulnerabilities arise when an attacker abuses legitimate application flows to achieve unintended behavior, without exploiting typical technical flaws like XSS, SQLi, etc.
They bypass rules, restrictions, or workflows in ways developers didn’t anticipate.


---

📋 Common Business Logic Bugs in VAPT

Category	Vulnerability / Issue	Example

Authentication & Authorization		
Insecure Direct Object Reference (IDOR)	Accessing others’ resources via predictable ID/URL	Changing /order/123 to /order/124
Broken Access Control	Performing admin actions as a normal user	Accessing /admin/delete_user directly
Missing Step Enforcement	Skipping required steps like OTP, Captcha, verification	Placing order without OTP verification
Privilege Escalation	Upgrading user role without proper checks	Modifying role=user to role=admin
Business Workflow Abuse		
Sequence Bypass	Skipping steps in a multi-step process	Skipping cart validation to checkout directly
Logic Flow Manipulation	Changing parameters to alter execution flow	Switching plan=free to plan=premium with payment bypass
Reusing Tokens or Sessions	Abusing temporary tokens beyond intended use	Reusing reset password link multiple times
Inconsistent State Handling	Conflicting behavior due to asynchronous updates	Canceling a paid order and still receiving the product
Financial / Payment Manipulation		
Price Manipulation	Changing item price or total in requests	Modifying price from ₹999 to ₹1
Quantity Bypass	Ordering negative or excessive quantities	Setting quantity = -100 to gain balance
Coupon / Discount Abuse	Using same coupon multiple times or stacking discounts	Applying SAVE20 multiple times
Currency Manipulation	Exploiting exchange rate conversions	Forcing price from USD to INR via tampered conversion
Free Trial Abuse	Creating multiple accounts to exploit trial logic	Registering 100 accounts with 1-month free trials
Order / Inventory Issues		
Race Conditions	Making parallel requests to duplicate items or skip limits	Buying limited stock product multiple times
Inventory Overbooking	Ordering out-of-stock items via direct POST requests	Ordering 100 items even when stock = 0
Refund / Cancellation Loopholes	Getting refund after successful delivery	Canceling item just before it ships
Account / Subscription Abuse		
Email Change Exploit	Changing email without re-verification	Hijacking account by updating email
Subscription Downgrade Abuse	Downgrading plan and still accessing premium features	Keeping access even after subscription cancel
Auto-renewal Exploitation	Cancelling after benefit is received but before charge	Using service and immediately cancelling trial
Data Exposure / Leakage		
Misaligned API Permissions	Exposing sensitive info in response	API returns email, phone even for other users
Excessive Data Fetching	Dumping large data via misconfigured parameters	/api/user?limit=10000 returns full DB
Trust / Reward System Abuse		
Referral Abuse	Creating fake users to farm rewards	Self-referring multiple accounts
Loyalty Point Exploits	Multiplying points via broken logic	Earning double points by replaying requests
Poll / Vote Manipulation	Voting multiple times via forged requests	Multiple votes on same poll entry
Gamification Logic Flaws	Leveling up without effort	Replaying add_score=10 requests



---

🧪 How to Test for Business Logic Bugs

1. Understand the business flow deeply

Read the docs, follow the happy path, explore edge cases.



2. Use proxy tools like Burp Suite to:

Manipulate requests.

Replay actions (e.g., using Intruder, Repeater).



3. Ask: What if I...

Skip steps?

Replay tokens?

Change parameters?

Act like a user/admin/developer?



4. Try automation + manual fuzzing

Sometimes automation misses logic flaws—manual analysis is essential.





---

✅ Pro Tips

Always test for non-technical exploits that violate business rules.

Coordinate with product owners during VAPT to understand logic constraints.

These issues often have high impact but low detectability.



---

Want a Burp Suite extension list to help find business logic bugs or a checklist template (.md) for VAPT reports?



