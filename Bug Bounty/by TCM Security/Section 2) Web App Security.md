
# Video 1) Importance of web app security
- Data Protection
- Maintaining customer trust
- Legal and regulatory compliance
- preventing business disruption
- protecting brand reputation
- preventing financial loss
- avoiding IP(intellectual property (codes, patents , personal and sensitive data etc)) theft
- preventing identity theft

# Video 2) Web app Security Standards & Best Practices

**Best Practices:**
- Regular Patching/Update
- Least Privilege
- secure coding (ESP.  Input validation and sanitation)
- secure data storage
- multi-factor authentication
- logging & monitoring
- user training
- and so much more...

**Web Security Standards:**
1. **OWASP TOP 10 (https://owasp.org/www-project-top-ten/)**
2. **COMMON WEAKNESS ENUMERATION (CWE)   (https://cwe.mitre.org/data/index.html)**
3. **SANS TOP 25 (https://www.sans.org/top25-software-errors/)**
4. **Common Vulnerability Exposure (CVE)  (https://cve.mitre.org/)** 
5. **MITRE ATTACK https://attack.mitre.org/  
6. **National Vulnerability Database (NVD): [https://nvd.nist.gov/](https://nvd.nist.gov/)**
7. **CVE Details: [https://www.cvedetails.com/](https://www.cvedetails.com/)**
8. **CVSS : https://www.first.org/cvss/  |  https://nvd.nist.gov/vuln-metrics/cvss

# Video 3) Bug Bounty Hunting Vs Penetration Testing

- Impact is everything (in Bug Bounty)   depends on the severity of the impact of the bug/vulnerability how big a bounty you would receive.
- Partial Vs whole Application
- Compliance

**web app Pen-testing** :  is looking at the whole web application and finding all vulnerabilities we can , even if it don't have an impact/small impact on security.(finding every weakness)

**Bug Bounty** : is finding bug or weakness that can impact security of web app in some way
(trying to find particular bugs (OWASP top 10 or SANS 25) that can cause an impact on security of Web application)

So basically in bug bounty you need to show that you hacked the system and how you did it instead of showing that there is a possibility to get hacked. 
and you need to show the severity i.e how high is the impact of all the bugs you find when combined together or separately .



**==" NON-IMPACT " Findings in Bug bounty hunting ==**  :

- Weak password Policy
- No Lockout Policy
- Unlimited Login Attempts
- User account Enumeration
- Out-of-Date Software
- Cookies(Flags, Expiration, etc)
- Ciphers
- Certificates

eg: in bug bounty don't go on and submit weak pw policy, user account enumeration or unlimited login attempts that will just get rejected, instead of that you need to see is :
if you can use weak password policy, user account enumeration, unlimited logins and
it is within scope to do brute-force attacks against accounts and you can login to something sensitive maybe then you can have an impact and prove something there and you need to prove that impact along the way.

just because you find a weakness/vulnerability  like out of date software doesn't mean you will get the bounty because it does not prove that the weakness directly leads to some sort of exploit.
Now if you were able to exploit something on web application because of the vulnerability/weakness that was present in the  software than you will get a bounty.


==scanner to find vulnerabilities in a web application using the web application link/domain :-==
**Security Headers  ( https://securityheaders.com/ )**
**Qualys SSL Labs (https://www.ssllabs.com/ssltest/)**

these scanner helps to find low level vulnerabilities in web applications



# Video 4)  Phases of web Application penetration testing 

**==Engagement Steps ==**  :-
- SOW(statement of work) & MSA(Master Service Agreement) agreement gets signed
- ROE(rules of engagement) agreement gets signed
- SCOPE VERIFIED
- PENTESTING OCCURS
- REPORT WRITTEN & DELIVERED
- CLIENT DEBRIEF
- RETESTING (IF NECESSARY)





