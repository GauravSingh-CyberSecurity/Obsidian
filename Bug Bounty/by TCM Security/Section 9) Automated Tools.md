video 1) Automated Scanners
---
![[Pasted image 20240402112030.png]]

==**free tier:**== 
- OWASP ZAP
- Arachni
- wapiti
- vega
- Sqlmap
- skipfish

**==commercial/paid/try to get a cracked version if possible:==**
- BurpSuite
- Nessus
- Acunetix
- AppScan
- VeraCode
- NetsParker
- Qualys web application scanning (WAS)






Video 2) Scripting & Automation
---
in this we are going to do automation of domain/subdomain enumeration, so we are going to do enumeration against a website.

in this case website : tcm-sec.com

```
website: tcm-sec.com

try to find: 
1)do we have any subdomains on the targer?|Using:(subfinder,assetfinder,amaas)
2)are those subdomains alive? |Using:(httprobe)
3)if we can, then take screenshots of alive subdomains |Using:(gowitness)
4)nmap alive subdomains? |Using:(open ports - nmap)
```

==we can automate these enumeration processes using Bash scripting.==

**in terminal:**
create a .sh file :
```
mousepad recon.sh
```
![[Screenshot from 2024-04-05 08-25-30.png]]
so this is my first time writing a bash script , just need to follow heath adams instructions .

the code/script we have to write in recon.sh :
```
#!/bin/bash

domain=$1
RED="\033[1;31m"
RESET="\033[0m"

subdomain_path="$domain/subdomains"
screenshot_path="$domain/screenshots"
scan_path="$domain/scans"

if [ ! -d "$domain" ]; then
    mkdir "$domain"
fi

if [ ! -d "$subdomain_path" ]; then
    mkdir "$subdomain_path"
fi

if [ ! -d "$screenshot_path" ]; then
    mkdir "$screenshot_path"
fi

if [ ! -d "$scan_path" ]; then
    mkdir "$scan_path"
fi

echo -e "${RED} [+] Launching subfinder ... ${RESET}"
subfinder -d $domain > $subdomain_path/found.txt

echo -e "${RED} [+] Launching assetfinder ... ${RESET}"
assetfinder $domain | grep $domain >> $subdomain_path/found.txt

#echo -e "${RED} [+] Launching amass ... ${RESET}"
#amass enum -d $domain >> $subdomain_path/found.txt

echo -e "${RED} [+] Finding alive Subdomains ... ${RESET}"
cat $subdomain_path/found.txt | grep $domain | sort -u | httprobe -prefer-https | grep https |sed 's/https\?:\/\///' | tee -a $subdomain_path/alive.txt 

echo -e "${RED} [+] Taking screenshots of alive Subdomains ... ${RESET}"
gowitness file -f $subdomain_path/alive.txt -P $screenshot_path/ --no-http

echo -e "${RED} [+] running nmap on alive Subdomains ... ${RESET}"
nmap -iL $subdomain_path/alive.txt -T4 -p- -oN $scan_path/nmap.txt

```

then save and exit the file.

make the file executable:
```
chmod +x recon.sh
```

then run this in terminal
```
./recon.sh tcm-sec.com
```

there is a new folder named tcm-sec.com created :-
![[Screenshot from 2024-04-05 08-48-31.png]]

output after running recon.sh:
![[Screenshot from 2024-04-05 09-35-17.png]]



to edit the recon.sh file we can open it using gedit editor :
```
gedit recon.sh
```



So this script that i made recon.sh is automating the task of domain/subdomain enumeration, i have written the script to do things i want to do while enumeration so that i dont need to run the tools again and again with same settings instead i can just automate it using the recon.sh .

this is why writing scripts for automating the tasks while hacking is so important, we dont need to do same thing again and again and it saves a lot of our time. 

so i must learn and make as many scripts as i can to reduce my work and be more efficient.

The more i can automate in bug hunting the better because then i'll have more time to find bug instead of just running tools for recon

