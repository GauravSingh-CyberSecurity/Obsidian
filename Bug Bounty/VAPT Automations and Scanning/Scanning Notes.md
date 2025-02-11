
There isn’t a single place that has every scanner’s commands in one document, but there are a few solid resources where you can find cheat sheets and command lists for most commonly used security scanners. Here are the best options:

1. GitHub Repositories (Best for Cheat Sheets & Command Lists)

PayloadsAllTheThings – GitHub Link(https://github.com/swisskyrepo/PayloadsAllTheThings)

Contains scanning, exploitation, and enumeration commands for tools like Nmap, Nikto, Gobuster, etc.


Red Teaming & Pentesting Notes – GitHub Link ( )

Has scanner commands for Nmap, Nessus, Burp Suite, Nikto, OpenVAS, etc.


HackTricks – Website( https://book.hacktricks.wiki/en/index.html)

Great for security scanning and enumeration commands.



2. Penetration Testing Cheat Sheets (Websites & PDFs)

SANS Penetration Testing Cheat Sheets – Link

HighOn.Coffee Security Cheat Sheets – Link https://highon.coffee/blog/

GTFOBins – Link (Great for privilege escalation) https://gtfobins.github.io/


1. Kali Linux Command Cheatsheet (Covers Most Scanners)

If you use Kali Linux, it has built-in cheatsheets under /usr/share/doc/

You can also check Kali Tools Website ( https://www.kali.org/tools/for) a categorized list of scanners and their commands.


2. Create Your Own Centralized Document

If you want a single place for all commands, create your own Markdown or Notion page where you keep:

Common commands for Nmap, Nikto, Burp Suite, Nessus, OpenVAS, etc.

Useful one-liners for automation.

Output analysis tips.


Would you like me to generate a customized cheat sheet for the scanners you use most?



# Server Scanners


To scan a server, you’ll need different types of scanners based on what you’re looking for. Here’s a categorized list of the best tools:


---

1. Network & Port Scanning (Find open ports, services, and firewall rules)

Nmap – The best general-purpose network scanner

nmap -sC -sV -A -T4 <server-ip> (Comprehensive scan)


Masscan – Faster alternative to Nmap for large networks

masscan -p1-65535 <server-ip> --rate=10000 (Full port scan)


Unicornscan – Used for stealthy scanning

unicornscan -mT -v -I <server-ip>




---

2. Web Application Scanning (Find web vulnerabilities)

Nikto – Basic web vulnerability scanner

nikto -h <server-ip>


Burp Suite – Advanced web application testing (manual + automated)

Use Burp Scanner for automated checks


OWASP ZAP – Open-source web vulnerability scanner

zap-cli quick-scan -r -s all <server-ip>


Dirb/Dirbuster/Gobuster – Directory and file brute-forcing

gobuster dir -u http://<server-ip> -w /usr/share/wordlists/dirb/common.txt




---

1. Vulnerability Scanning (Automated security assessments)

Nessus – Industry-standard vulnerability scanner (requires setup)

Run a Basic Network Scan in the GUI


OpenVAS (Greenbone Security Manager) – Open-source alternative to Nessus

openvas-cli --target <server-ip>


Qualys SSL Labs Scanner – Check SSL/TLS misconfigurations

Use the web tool: https://www.ssllabs.com/ssltest/




---

2. Exploit Scanning (Checking if the server has known exploits)

Metasploit Framework – Find and exploit vulnerabilities

msfconsole → use auxiliary/scanner/http/title


SearchSploit – Check for publicly available exploits

searchsploit <software/version>


Shodan/Censys – Find exposed servers and services

shodan search <server-ip>




---

3. Cloud & API Security Scanning

AWS Prowler – Security assessment for AWS

prowler -c all -M csv


GCP ScoutSuite – Security assessment for Google Cloud

scout gcp


Postman/OWASP ZAP API Scanner – API vulnerability scanning



---

Best Approach for Server Scanning:

4. Start with Nmap – Find open ports/services


5. Use Nikto or ZAP for web scanning


6. Run Nessus/OpenVAS for vulnerability assessment


7. Use Metasploit/SearchSploit to check for known exploits


8. For cloud servers, use Prowler (AWS) or ScoutSuite (GCP)



Want me to create a cheat sheet with exact commands for your workflow?

