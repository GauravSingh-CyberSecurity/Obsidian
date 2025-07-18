
### Study : 


Tools :   

==Recon== : Nmap, Nuclei, amass , whois, Dig, dnsrecon, nslookup , subfinder, GAU, WaybackMachine, Linkfinder, Js miner, WPscanner, harvester
Burp Pro : Active scan/Live Audit/ Crawling & spidering , Burp Bounty Bro to find potential hidden vulnerable endpoint/parameter eg: for sqli, xss, idor, ssrf 


Testing : burp pro, Owasp zap, browser & it's dev tools

Exploit creation: exploit.db , hackerone Hacktify , bugcrowd blogs, articles on medium.

Xss automation: linkfinder, js-beautifier, dalfox scan, xss strike fuzz and manual testing. (Dom)

Sqli : Burp pro , burp bounty pro, Sqlmap.

Subdomain takeover: Subfinder(find subdomain)> nuclei with its template (http/takeover/)

Idor: burp crawl & audit, burp active scan, burp bug bounty pro active & smart scan>gather all idor input parameters> Ai for analysis of ids and creating guessable IDs; Burp intruder and seclists/payload all things for fuzzing/brute the idor parameter.


1) XSS : XSS is a vuln that occurs when user-generated input is not properly Sanitised or No input validation is done in the application , Like there is no Encoding of user input, NO whitelisting and Black listing of tags, characters, scripts etc in the user input parameters.     
     
     a) ==DOM XSS==(Document Object Models - look for DOM identifiers(eg: Location.hash) in Applications .JS ; and analyse its code to verify if its Using Input validation and Sanitation like base64 Encoding , whitelisting , blacklisting the tags, characters and scripts etc
      
        

     b) ==Reflected XSS== (When user generated input is not validated or Sanitised , also its immediately reflected back by server in the servers response; eg: ==search parameter==) ,     
     c) ==Stored XSS==(When the user generated input is stored in the applications DB and retrieved back to the ClientSide when victim visit the page; Eg: ) ,     
     d) ==Blind XSS==(Stored but not visible to user/attacker Eg: Support Ticket Form) , 
     
	 
	 
	 
	 
	 
	 2) SQLi : Happens when there is no form of input validation , Sanitation , Blacklisting, Whitelisting, Encoding etc of User-input and the user's input is directly included in the SQL query that the Application makes to its DB; Which directly allows the attacker to manipulate & interfere with the SQL Queries that Application makes to its DB. I.e : It Happens when Untrusted/malicious user input is directly included in the SQL Queries that apps make to its DB, allowing attacker to craft malicious query that lets them ==read, modify or delete data in Applications DB without authorization.==     
     
      a) ==In-Band==(Classic) SQLi : Directly display the result of SQLi on the Web Page.     
      b) ==Boolean== SQLi : Uses True/False (1 | 0) conditions to check the application behaviour in both Scenarios to analyse the application & DB in order to extract data/do malicious activity.     
      
      c) ==Time based== SQli : Use Delays like SLEEP() Operator to extract or analyse app behaviour and response delay and leads to information.     
      d) ==Union Select== SQli : Uses `UNION` / `UNION SELECT` operator to combine Queries and extract data.     
      
      e) ==Error Based== SQLi : Deliberately creating SQL Queries that will throw SQL errors and Using SQL error messages to gain info about the DB.     
      
      f) OOB (Out of Bounds) SQLi : Using External Channels (Eg: DNS/Web request ) to extract data or perform malicious activity on DB.