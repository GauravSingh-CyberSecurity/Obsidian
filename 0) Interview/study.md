

 

- Xss(reflected, stored , Blind(stored), DOM)

- ssrf(open redirect, fetch/call/get parameter that fetch )
idor

sqli(in-band(classic), Boolean(blind), time based, union select, errorbased, out of bounds).

token manipulation 
csrf
access control vuln
auth vuln(Bypass)
bruteforce using osint/otp

session hijacking:
Xss>malicious js to extract cookie and send to evil.com>session don't expire or concurrent session allowed>session hijacking


reflected css>csrf>xss.cookie.extract.exploit>session hijacking 


Subdomain takeover:
deleted cloud instance(EC2, S3 or ALB)>dns records still present(cname or NS record still present)>a CNAME record subdomain.yourdomain.com pointing to old-instance-name.cloudprovider.com or an A record pointing to a now unassigned IP)>host cloud instance of same cloud-instance-name/ip>subdomain takeover{attacker has the cloud instance(i.e server back-end) where he creates/hosts an identical login page , victim input ID PW and compromised}

info disclosure: api, ui, access control, auth, cryptography compromise or weakness or misconfiguration.


Vulnerable & outdated components: all tech stack vuln scan using the cve DB.


SSTI: injecting web shell in file uploaders or user input fields to execute a cmd.

Remote OS command injection: test user input fields in the request going on server by injecting them with OS command, web shell>OS command to verify if Command injection.

Html code manipulation on client side to change functionality like read only input fields(xss), non clickable button (to submit unauth only admin is allowed to change things)

Html code injection 

Response manipulation: json body, html body, response code.

Request headers , body, token, cookie manipulation 


LFI>inject web shell>RCE
LFI: eg- if a page have switch language drop down, if user changes eng to hindi, the same web page is returned in hindi but the directory/folder is changing from where the hindi page is fetching.
If attacker can control this path they can access sensitive folder like /etc/passwd

And can inject web shell <php. [Get CMD] >



rce : using web shells

Jwt token manipulation/cookie manipulation:
token expiration test(not invalidate
 or  
changing parameter of token(email, user-id) lead to access of other users 
or 
manipulation  of unencrypted tokens time-stomp result in invalidated token becoming valid)



revise:
cryptography reverse engineer
BNHS backdoor
Athena sqli and idor
paytonic otp bypass

BML idor (LC (/lc/customer) user able to access SME (/sme/customer) users path and see the customer report 
(/sme/customer/report/20)