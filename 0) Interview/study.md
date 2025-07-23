

 

- Xss(reflected, stored , Blind(stored), DOM)

- ssrf(open redirect, fetch/call/get parameter that fetch by making request to server)

- idor

- sqli(in-band(classic), Boolean(blind), time based, union select, errorbased, out of bounds).


- token manipulation 

- csrf

- access control vuln

+ **auth vuln**(Bypass): bruteforcing , using compromised credentials DB/rainbow table attack, common or weak pw attack, in-band, Boolean SQLi on login if no blacklist or whitelist, response code manipulation.

+ **Authorization/access control bypass:** manipulate id/email in change pw/email request, manipulate identifiers in jwt token, test IDOR, analyse the response body and if feature available, forge a request 'is_admin=true' .


- bruteforce using osint/otp

- session hijacking:
  Xss>malicious js to extract cookie and send to evil.com>session don't expire or concurrent session allowed>session hijacking


- reflected xss>csrf>xss.cookie.extract.exploit>session hijacking 


- Subdomain takeover:
  deleted cloud instance(EC2, S3 or ALB)>dns records still present(cname or NS record still present)>a CNAME record subdomain.yourdomain.com pointing to old-instance-name.cloudprovider.com or an A record pointing to a now unassigned IP)>host cloud instance of same cloud-instance-name/ip>subdomain takeover{attacker has the cloud instance(i.e server back-end) where he creates/hosts an identical login page , victim input ID PW and compromised}

- info disclosure: api, ui, access control, auth, cryptography compromise or weakness or misconfiguration.


- Vulnerable & outdated components: all tech stack vuln scan using the cve DB.


- SSTI: injecting web shell in file uploaders or user input fields to execute a cmd.

- Remote OS command injection: test user input fields in the request going on server by injecting them with OS command, web shell>OS command to verify if Command injection.

- Html code manipulation on client side to change functionality like read only input fields(xss), non clickable button (to submit unauth only admin is allowed to change things)

- Html code injection (dom xss)

- Response manipulation: json body, html body, response code.

- Request headers , body, token, cookie manipulation 


- LFI>inject web shell>RCE
  LFI: eg- if a page have a feature language "drop down", if user changes eng to hindi, the same web page is returned in hindi but the directory/folder is changing from where the hindi page is fetching.
If attacker can control this path they can access sensitive folder like /etc/passwd

And can inject web shell <php. [Get CMD] >



- rce : using web shells

- Jwt token manipulation/cookie manipulation:
- token expiration test(not invalidate
 or  
- changing parameter of token(email, user-id) lead to access of other users 
or 
- manipulation  of unencrypted tokens time-stomp result in invalidated token becoming valid)


- session fixation: if session id doesn't regenerate/change when login success and doesn't expire/invalidate and if session id is suppose sent via url param.
  The attacker uses session id and login, sends the same link of login page with the same session id to victim, victim logs in> attacker re-uses the session cookie and get access to the victims account.

- XXE(XML external entity) : 
    Xxe>LFI>rce



- BOLA(broken object level auth): there are no auth check and attacker can do things like this: 
   Get /api/user/123/profile

   Get /api/users/456/profile
   


- DNS records explain:
   
   A(address) record:- maps a domain name to its ipv4.

   AAA(IPV6) record :maps a domain name to its ipv6

   CNAME(canonical name record) :- maps one domain name to another domain name.
   Eg: www.eg.com to eg.com 

   NS(name server) record: tells which name server/hosting service (cloudflare,Godaddy, google cloud , aws)

   MX(mail exchange) record: tells  which mail server will receive email for that domain (gmail, outlook)



revise:

NStar
cryptography reverse engineer

BNHS backdoor



BML idor (LC (/lc/customer) user able to access SME (/sme/customer) users path and see the customer report 
(/sme/customer/report/20)



Paytonic: (paytonic otp bypass)
Email recon using osint> OTP auth bypass> login>change pw and account takeover


Athena: (Athena sqli and idor)
Sqli on strong pw policy and input validation on id param. >
But no blacklist and whitelist of SQL query input, user generated input was directly included in the SQL query that app makes to ita db. It was classic in-band.
