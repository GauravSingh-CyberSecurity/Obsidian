
how to Report Bugs that you found

Video 1) Understanding CVSS (Part 1)
---
CVSS (Common Vulnerability scoring system)
![[Screenshot from 2024-04-05 10-30-56.png]]


**CVSS introduction**
![[Screenshot from 2024-04-05 10-32-30.png]]








==CVSS Overview== : 
![[Screenshot from 2024-04-05 10-50-41.png]]
**1) what is CVSS?** 
-> CVSS is a security assessment framework that provides a standardised method for rating the severity of vulnerabilities . 

**2) what is the purpose of CVSS?**
-> It helps organisation prioritise vulnerabilities and enables consistent communication between different stakeholders.

**3) CVE vs CVSS**
-> while CVE (common vulnerability exposures ) are used for tracking vulnerability 
CVSS is for assessing & rating the severity of vulnerability . 

**4) where and how is CVSS used?**
-> its applied i vulnerability reporting management , bug bounty programs , penetration testing, risk assessment and incident respond.

**5) How many versions of CVSS are there?**
-> CVSS version 1 was released in 2005, version 2 in 2007, version 3 in 2015, version 3.1 in 2019, version 4 in 2023.

CVSS is owned and managed by  [https://www.first.org/cvss/v3.1/use-design](https://www.first.org/cvss/v3.1/use-design) (first.org)
which is a USA based non profit Organization.






==CVSS Components :== ( it has 3 metrics : **Base , Temporal , Environmental** )
![[Screenshot from 2024-04-05 10-51-16.png]]



Each metric further have their own groups/types : 
![[Screenshot from 2024-04-05 10-54-58.png]]





**1) Base metrics types/groups** : Exploit-ability metrics , impact metrics , Scope metrics 

==Exploitability metrics  :==  AV, AC, PR, UI
in this screenshots the==severity of vulnerabilities goes High-to-low from Up-to-down==

![[Screenshot from 2024-04-05 11-02-21.png]]
NOTE: in this pic the severity of vulnerability reduces as we move down 
i.e high to low = AV -> AC -> PR -> UI . (severity of AV highest & UI Lowest)

For eg: in AC the severity goes high-to-low i.e up-to-down i.e 
**(** high-to-low = Low(L) -> High(H)
therefore higher the AC lower the severity of vulnerability **)**   





==(AV)== : describes how a vulnerability can be exploited 

==(AC)== : measures the level of complexity required to exploit the vulnerability i.e how hard it is to exploit the vulnerability (higher the AC lower the severity of vulnerability)

==(PR)== : indicates the privileges attacker needs to exploit the vulnerability. 

(UI) : shows if users interaction is required or not and how much UI is required to exploit the vulnerability.


==Impact Metrics:==  C, I, A
![[Screenshot from 2024-04-05 13-27-28.png]]
```
Confidentiality: 
This ensures that only authorized users can access and view sensitive information. It involves measures like access control, encryption, and data classification.  comprimise if data gets unauthorised access

Integrity: 
This guarantees that data remains accurate and unaltered. It involves techniques like data validation, checksums, and tamper-evident controls.
compromise if data gets tampered without authorization

Availability: 
This guarantees that authorized users can access information and resources whenever needed. It involves measures like system uptime, redundancy, and disaster recovery planning.
compromise when denial of service(DOS).
```

in impact metrics : 
(H) : means if the vulnerability get exploited then C/I/A gets totally compromise
(L) : means Low compromise
(N) : means no compromise.

==Scope metrics :==
![[Screenshot from 2024-04-05 13-59-09.png]]
In the context of bug bounty hunting and vulnerability assessment, the Base metric "scope" in the Common Vulnerability Scoring System (CVSS) measures the impact of a vulnerability on the confidentiality, integrity, and availability of the system or data. Here's a simplified explanation using a bug hunting scenario:

**Scope (CVSS Metric)**:
- **Changed**: A vulnerability is considered to have a changed scope if it can impact more than just the originally identified component or area of the system. For example, if a bug hunter discovers a vulnerability in a specific feature of a web application, but further investigation reveals that the same vulnerability exists in other parts of the application or can be used to access sensitive data, the scope of the vulnerability is considered changed.

- **Unchanged**: A vulnerability is considered to have an unchanged scope if its impact is limited to the originally identified component or area of the system and does not extend to other parts. For instance, if a vulnerability in a login page only allows an attacker to bypass authentication for that page and does not provide access to other parts of the application, the scope is unchanged.

Understanding the scope of a vulnerability is important for assessing its potential impact on the overall security of the system. Vulnerabilities with a changed scope are typically more severe and require immediate attention, as they can lead to broader security breaches.




**2) Temporal metrics :**  E, RL, RC
![[Screenshot from 2024-04-05 14-13-19.png]]

Temporal metrics reflects the characteristics of vulnerabilities that may change  over time
it has (E) , (RL) , (RC)

==(E)== : measures the likelihood/probability of exploit being developed to successfully being used against vulnerability.

==(RL)== : indicates the availability of an official fix or a workaround

==(RC)== : level of confidence in the accuracy & completeness of the vulnerability report



**3) Environmental Metrics  types/groups :   Modified metrics , Requirement metrics**


==**Modified metrics :**==
![[Screenshot from 2024-04-05 14-52-11.png]]


==**Requirement metrics :**==
![[Screenshot from 2024-04-05 14-54-47.png]]














**CVSS role in Bug bounty:**
![[Screenshot from 2024-04-05 14-56-26.png]]
 

![[Screenshot from 2024-04-05 14-58-41.png]]




video 2) Understanding CVSS (part 2)
---

