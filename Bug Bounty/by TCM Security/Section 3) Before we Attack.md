# Video 2) understanding Scope , Ethics , Code of Conduct in Bug bounty hunting
==
====**Scope , Ethics , Code of Conduct in Bug bounty hunting**==




Understanding Scope:
---
Scope : Defines  the range of assets that organisation is explicitly inviting security   researchers to assess for vulnerabilities.

---
Out of scope :  Refers to the assets that are explicitly off limits for security researchers participating in bug bounty programs.

these Scopes (domains / subdomains & things that we are allowed to test goes out of scope and comes in the scope all the time by the organisations need for the security testing so we should always keep an eye out to see if any new scope are added or been removed in a bug bounty program.)

---




Why is Scope important ?
---
- sets Legal and ethical boundaries 
- Resource allocation 
- practical reasons
- Fairness


![[Screenshot from 2024-03-22 15-49-35.png]]


Can you submit Out of scope(OOS) bugs ?
---
- Sometimes , hunters stumble upon bugs on OOS assets.

- most of the time ***triage*** (process of determining the ***severity*** and ***validity*** of each reported issue, as well as its ***potential impact*** on the security of the system. when a bug is submitted by researchers . this process is done by org who held bounty program. ) will reject these submissions and you wont get any bounty on that bug as well as you velocity ratio of  finding bugs will  have a negative impact(i.e it will decrease) because you didn't submit a valid bug.
- this is imp because good velocity ration is how you get invited to private programs.

- but its Not always the case  - if there is a clear severe business impact they'll acknowledge it .(they might reward with bonus or reputation points but no bounties for OOS)

- No bounty will be awarded for OOS submission .




Duplicate Bugs 
---

- Occurs when multiple researchers/hunters report the same bugs .
- Organisation award the bounty to initial/first person who reported the bug.
- Knowingly reporting a duplicate bug is unethical.  Because it wastes Triage teams time . 


 
Structural issues for bounties 
---
==There is one fix , one reward policy in bug bounty== 
(i.e two or more different types bug submissions can be marked duplicate if they have same underlying root cause in the code. )

So if multiple fixes are required for the single or multiple submissions of bugs then it is not marked as a duplicate 

but if the fix for first report have fixed the other bugs , then all the other bugs are marked duplicate.

so basically every bug that you report should have a different kind of fix ,  
so if you submitted bug A , B , C , D  and A,B,C have same root cause and same/single fix is required and the D bug has a different fix , then you will be rewarded bounty for A , D  bugs and B, C will be marked duplicate  

So to clear this doubt just ask yourself if the fix for the previous bug that you reported will fix this bug as well , if yes no need to submit 

the Summary is :
- [ ] One fix, One reward
- [ ] if multiple fixes are required , it is not a duplicate
- [ ] would the fix for the first report have fixed the others?



Community Code of Conduct
---
These terms should be followed while bug bounty hunting:

1. **Disclosure Terms**:
    
    - Follow the program's guidelines on reporting vulnerabilities, including when and how to disclose them.
    - Respect the program's disclosure timeline and keep vulnerabilities confidential until authorised to disclose.
2. **Collaboration**:
	  collaboration needs companies permission
    - Work openly and transparently with other researchers and the program to share knowledge and avoid duplicate efforts.
    - Respect other researchers' work and give credit where due.
    - refrain from sharing info outside of the bounty programs
3. **Asking for Update**:
    - Check the program's communication channels for updates regularly.
    - Avoid spamming or repeatedly asking for updates; instead, be patient and wait for a response till the reply time that is specified by the programs/organisation . 
4. **OOS Submission** (Out of Scope Submission):
    
    - Follow the program's scope and guidelines; only submit vulnerabilities within the defined scope.
    - If unsure, ask the program for clarification before submitting.
5. **Use of Illegal or Cracked Software**:
    
    - Do not use illegal or cracked software in your bug hunting activities.
    - Use legitimate tools and methods to find vulnerabilities.
    - Respect intellectual property rights and licensing agreements.
6. **Out of Bound Communication**:
    
    - Avoid communicating about the program or vulnerabilities outside of the designated bounty channels/platform or unauthorised  parties.
    - report bugs from the official channel/platform only.
7. **Hoarding of Vulnerabilities**:
    
    - Report vulnerabilities promptly and do not withhold them for personal gain or exploit.
    - report vulnerabilities in given time frame after discovery
8. **Data Exposure and PII** (Personally Identifiable Information):
    
    - Protect sensitive data and personally identifiable information, ensuring it is not exposed during testing.
    - access minimal amount of data required to verify bug/vulnerability
9. **Third-Party Services for vulnerability reporting**:
    
    - Obtain permission before testing or interacting with services or systems not explicitly included in the program scope. ![[Screenshot from 2024-03-22 17-02-18.png]]
    
	- dont host/upload proof of concepts & videos externally(eg: gdrive and then submitting its link) , only upload vulnerabilities on bounty platform and if that is not possible use PW protected zip file to send it via provided email to the program hosters
10. **Intrusive Testing**:
    
    - Conduct testing within the agreed-upon boundaries to avoid causing harm or disruptions to the target system.
11. **Pivoting**:
    
    - Avoid using one vulnerability to gain unauthorised access to other systems or areas within the target environment and trying to find more vulnerablities.











---




---





# Video 3) Scoping mistakes


Scoping mistakes :
---

- Not thoroughly reading the scope before testing
- Not strictly following the scope
- Misunderstanding the importance of scope
- Reviewing asset scope , while forgetting bug scope
- Assuming all Subdomains are in Scope
- Not verifying if third-party services are in-scope
- Improperly configuring tools to adhere to scope
- Reporting out of scope findings


Commonly out-of-scope vulnerabilities
---
***Security Impact*** : Question is if attacker exploits the vulnerability what impact will it have on business or the users  , a valid bug is not always a security issue , eg :-

- Physical attack
- Social engineering
- Denial of service (DOS)
- Outdated software
- missing headers / cookie flags
- Brute-forcing attacks/credentials
- Username enumeration(ability to determining/guessing valid username on the system/application) - not always out-of-scope.
- Fingerprinting
- Theoretical attacks
- Leaked credentials(eg: leaked from dark web)

these vulnerabilities are not valid bugs

SO Stick to the scope given in bounty program and stick to the requirements of the program.


Eg of a bugbounty program on intigriti platform :
red-bull : https://app.intigriti.com/researcher/programs/redbull/redbull/detail
innogames : https://app.intigriti.com/researcher/programs/innogames/innogames/detail