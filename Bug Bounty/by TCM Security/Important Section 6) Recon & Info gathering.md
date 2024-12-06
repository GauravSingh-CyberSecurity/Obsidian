

Video 1) Fingerprinting web technologies  : 
---
this is very important

if your recon is good and you can find things that others cant then you'll be a very good pentester.




we are using this Azena program for practicing recon:
https://app.intigriti.com/researcher/programs/azena/azenaresponsibledisclosure/detail




Find out what websites are built with : 
Tool : https://builtwith.com/
we just go to this website and look up azena.com

or we can use extension called Wappalyzer in browser :
https://www.wappalyzer.com/installed/ (extension tutorial link)



```
in terminal we use :

curl -I -L https://store.azena.com/shop/    

(I is used to find any additional info about website using curl)  (-L is used to follow any redirects)

by using -I  we get this code( HTTP/2 302) 

by using -L redirect we get the main website of azena(HTTP/2 200 )
```


Output 
```
C:\home\kali> curl -I -L  https://store.azena.com:443/

HTTP/2 302 
date: Tue, 26 Mar 2024 01:51:47 GMT
set-cookie: AWSALB=ki1x0ZIOIYNqjfNTGRBmIoZXg+OrnVMWtG/QBLg9RpRAcDq/t91lmNWNDeIpE+aqYVUenuAtNwEEW9r1fY71/RaK0m+DoJCSMGhRw4Vs5faKnjEHb2jLYer6Pk2V; Expires=Tue, 02 Apr 2024 01:51:47 GMT; Path=/
set-cookie: AWSALBCORS=ki1x0ZIOIYNqjfNTGRBmIoZXg+OrnVMWtG/QBLg9RpRAcDq/t91lmNWNDeIpE+aqYVUenuAtNwEEW9r1fY71/RaK0m+DoJCSMGhRw4Vs5faKnjEHb2jLYer6Pk2V; Expires=Tue, 02 Apr 2024 01:51:47 GMT; Path=/; SameSite=None; Secure
location: /shop/

HTTP/2 200 
date: Tue, 26 Mar 2024 01:51:48 GMT
content-type: text/html;charset=UTF-8
set-cookie: AWSALB=3LlbWPjLYaT/WVheLZRmAcBeQi2lHsexaCh4R53CuUTuR7ksTwwQ7WqM0q1d+go26vTmJfhRD0UQ7ddR7cWwEtkOmc1gUeYWDnq5AS1WlsMr9eBkxv4wQslTQEk0; Expires=Tue, 02 Apr 2024 01:51:48 GMT; Path=/
set-cookie: AWSALBCORS=3LlbWPjLYaT/WVheLZRmAcBeQi2lHsexaCh4R53CuUTuR7ksTwwQ7WqM0q1d+go26vTmJfhRD0UQ7ddR7cWwEtkOmc1gUeYWDnq5AS1WlsMr9eBkxv4wQslTQEk0; Expires=Tue, 02 Apr 2024 01:51:48 GMT; Path=/; SameSite=None; Secure
x-frame-options: SAMEORIGIN
strict-transport-security: max-age=31536000 ; includeSubDomains
content-security-policy: default-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com *.google-analytics.com *.googletagmanager.com *.googleadservices.com api.hubapi.com stats.g.doubleclick.net; script-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com dock.ui.bosch.tech btm.bosch.com js-agent.newrelic.com bam-cell.nr-data.net *.google-analytics.com *.googletagmanager.com https://tagmanager.google.com *.googleapis.com *.gstatic.com *.googleadservices.com googleads.g.doubleclick.net www.youtube.com https://s.ytimg.com js.usemessages.com merch.directpos.de www.computop-paygate.com 'unsafe-inline' 'unsafe-eval'; font-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com *.gstatic.com data:; style-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com https://googletagmanager.com https://tagmanager.google.com https://fonts.googleapis.com *.googleapis.com 'unsafe-inline'; img-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com *.google-analytics.com *.googletagmanager.com https://ssl.gstatic.com https://www.gstatic.com *.google.com https://i.ytimg.com data:; frame-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com www.youtube.com www.youtube-nocookie.com merch.directpos.de www.computop-paygate.com; connect-src 'self' *.securityandsafetythings.com *.azena.com *.store.boschaftermarket.com *.boschmarketplace.com https://noembed.com https://cdn.plyr.io dock.ui.bosch.tech btm.bosch.com js-agent.newrelic.com bam-cell.nr-data.net *.google.de *.google-analytics.com https://*.analytics.google.com https://*.googletagmanager.com api.hubapi.com *.googleadservices.com stats.g.doubleclick.net merch.directpos.de www.computop-paygate.com
x-xss-protection: 1; mode=block
vary: origin,access-control-request-method,access-control-request-headers,accept-encoding
set-cookie: JSESSIONID=9A23993173B1E8393AFAEDBE9A6411B3; Path=/shop; Secure; HttpOnly
set-cookie: st_selected_lang=en; Max-Age=31536000; Expires=Wed, 26 Mar 2025 01:51:48 GMT; Path=/; Secure
set-cookie: st_selected_country=; Max-Age=31536000; Expires=Wed, 26 Mar 2025 01:51:48 GMT; Path=/; Secure
set-cookie: anonymous-consents=%5B%5D; Max-Age=31536000; Expires=Wed, 26 Mar 2025 01:51:48 GMT; Path=/; HttpOnly
cache-control: no-cache, no-store, max-age=0, must-revalidate
pragma: no-cache
expires: 0
x-content-type-options: nosniff
content-language: en


```

above provides this info
- **Date:** Tue, 26 Mar 2024 01:51:48 GMT
- **Content-Type:** text/html;charset=UTF-8
- **Set-Cookie:** Various cookies set with expiration dates and paths
- **X-Frame-Options:** SAMEORIGIN (protects against clickjacking attacks)
- **Strict-Transport-Security:** max-age=31536000; includeSubDomains (enforces HTTPS for the specified duration)
- **Content-Security-Policy:** Defines allowed sources for various content types (script, font, style, image, frame, connect)
- **X-XSS-Protection:** 1; mode=block (enables XSS protection)
- **Vary:** origin, access-control-request-method, access-control-request-headers, accept-encoding (specifies which request headers can be used to determine the response)
- **Cache-Control:** no-cache, no-store, max-age=0, must-revalidate (specifies caching directives)
- **Pragma:** no-cache (specifies no caching)
- **Expires:** 0 (specifies an expiration date in the past, effectively disabling caching)
- **X-Content-Type-Options:** nosniff (prevents browsers from MIME-sniffing a response away from the declared content-type)
- **Content-Language:** en (specifies the language of the content)












a cleaner way to do this without terminal and Curl is using this website :
https://securityheaders.com/

and third way is using nmap :
```
nmap -p443 -A azena.com
```

mapping it out with just a script
```
nmap -p443 --script=http-server-header azena.com
```

scanning for different ports together :
```
nmap -p80, 443 -A azena.com
```


preferably use security headers website , built with website etc.



Video 2) Directory enumeration and brute forcing
---
we are trying to look/guess the directories in website using tools
we utilize a wordlist to brute forcingly check for the directories and try to find directories we didnt know about because there might be info lurking in those directories


in terminal:  (Tool 1)
```
sudo apt install ffuf 
ffuf --help

ls /usr/share/wordlists


ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u https://store.azena.com/shop/FUZZ

```

output:
:: Progress: [220560/220560] :: Job [1/1] ==:: 228 req/sec== :: Duration: [0:19:02] :: Errors: 1 ::






or use dirb (prebuilt in kali linux) :  (Tool 2)
```
dirb                             (for learning how to use it)


dirb https://store.azena.com/shop/


Eg Output: 
C:\home\kali> dirb https://store.azena.com/shop/

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Tue Mar 26 09:37:04 2024
URL_BASE: https://store.azena.com/shop/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: https://store.azena.com/shop/ ----
+ https://store.azena.com/shop/favicon.ico (CODE:302|SIZE:0)                                                         
+ https://store.azena.com/shop/logout (CODE:302|SIZE:0)                                                              
+ https://store.azena.com/shop/robots.txt (CODE:200|SIZE:45)                                                         
+ https://store.azena.com/shop/tools (CODE:200|SIZE:8408)                                                            
                                                                                                                     
-----------------
END_TIME: Tue Mar 26 09:51:24 2024
DOWNLOADED: 4612 - FOUND: 4


```

dirb uses common.txt its a small wordlist so not that efficient






or use dirbuster tool (GUI):  (Tool 3)
```
dirbuster&
```

after running above command we get a gui pop up that we can use for bruteforcing:  

before putting values in :
![[Screenshot from 2024-03-26 09-43-28 1.png]]




after putting values in :
![[Screenshot from 2024-03-26 09-48-51.png]]




video 3) Subdomain Enumeration
---
what is subdomain

```
top level domain :                  .com
second level domain :          azena.com
sub domain :           connect.azena.com
```

we should find out about all the interesting subdomain that are in scope because they can have some vulnerability that we could exploit.



```
*.azena.com
```
the ( * ) is a wild card that means all subdomains are in scope except the what is explicitly mentioned as OOS .





**Method 1)** using Google to find subdomains **==(Google dorking)==** : Not the best method 
![[Pasted image 20240326112917.png]]

```
site:azena.com -www
```

```
site:azena.com -www -store
```

```
site:azena.com filetype:pdf
```

```
site:tesla.com filetype:xls password
```
we can search like this to find intresting information




![[Pasted image 20240326114005.png]]

| Command                        | Description                                                   |
| ------------------------------ | ------------------------------------------------------------- |
| site:example.com               | Search only within the specified site                         |
| link:example.com               | Find pages that link to the specified site                    |
| filetype:pdf                   | Search for specific file types (e.g., PDF)                    |
| intitle:"keyword"              | Search for pages with the specified keyword in the title      |
| inurl:"keyword"                | Search for pages with the specified keyword in the URL        |
| intext:"keyword"               | Search for pages with the specified keyword in the text       |
| cache:example.com              | View Google's cached version of a site                        |
| related:example.com            | Find sites similar to the specified site                      |
| info:example.com               | Get information about the specified site                      |
| define:term                    | Get a definition of the specified term                        |
| allintitle:"keyword1 keyword2" | Search for pages with all the specified keywords in the title |
| ext:                           | Search for specific file extensions                           |
| inanchor:                      | Search for pages with specific anchor text                    |
| site:example.com filetype:pdf  | Search for PDF files within a specific site                   |
| site:example.com intitle:admin | Search for pages with "admin" in the title on a specific site |







**Method 2)** using website(tool) to find subdomains: 

website (tool): https://crt.sh/

in search bar:
```
%.azena.com
```

output:
![[Screenshot from 2024-03-26 11-50-25.png]]








**Method 3)** (CLI) Command line tools (in terminal):

tool name: **==subfinder==**

**in terminal:**
```
sudo apt install subfinder
```

for searching domains/subdomains( -d ):
```
subfinder -d azena.com


output:
[INF] Found 678 subdomains for azena.com in 15 seconds 995 milliseconds
```

for more understanding:
```
subfinder --help
```

to save result of search in a file:
```
subfinder -d azena.com -o filename
```

this tool looks up all active & inactive domains/subdomains






tool name: **==assetfinder==**  (https://github.com/tomnomnom/assetfinder)
this tool is pre installed in kali linux.

in terminal:
```
sudo apt install assetfinder
```

for searching domains/subdomains:
```
assetfinder azina.com


output:
C:\home\kali> assetfinder azina.com 
azina.com
resources.azina.com
www.azina.com
discover.azina.com

```


```
assetfinder azina.com | grep azena.com | sort -u > azena.txt
```
**grep:** This command searches for the specified "pattern" in the file "file.txt" and prints any lines that contain the pattern.

**sort -u** : sort the findings uniquely

( **>azena.txt** : prints the findings in this txt file )






Tool name : **==amass==** 
it has a lot of capabilities , pre installed in kali

in terminal:
```
amass                (to see tool)
amass -h	Show the program usage message
```


enum -d for finding domains   |   >azena.txt to save result in txt file
```
amass enum -d azena.com > azena.txt
```
this tool takes long time to run.

output of the result :
![[azena.txt]]



tool name : **==httprobe==**   (to identify live web servers in azena.txt for further analysis.)

```
cat azena.txt | grep azena.com | sort -u | httprobe -prefer-https | grep https > azenalive.txt
```


![[azenalive.txt]]
its empty so basically there is no live subdomains

output that TCM gets for azenalive.txt(bcoz he did it in the past):
![[Screenshot from 2024-03-26 12-36-39.png]]




**==Method 1) For taking screenshot of our findings during recon process of domains/subdomains enumeration==**

Tool name : **==gowitness== (comes at 13 min in the video )**  
now as we can see here there are a lot of domain/subdomains link  and we dont want to click on each one and go see whats there because it can be 100's of links.

so we have a tool called ==gowitness== : this tools automate this process by going to every domain/subdomains link and taking screenshots of the page & saving it in the folder on our pc so we can directly go to that directory and see all the screenshots.




Video 4) Burp Suite Overview :(Imp)
---
Burp suite is a web proxy .

1) Burp is pre installed in kali 
2) go to proxy in burp suite 
3) set foxproxy extension in browser(firefox)
4) set/import ca certificate ![[cacert.pem]]
5) go to proxy in burp suite : - set intercept on
6) now we have traffic coming from browser to the burp suite and we can perform different tasks on it.
7) so we go to test our target bounty programs website azena.com(in firefox browser)



adding items to scope in burp: (on azena.com right click and add to scope)
![[Screenshot from 2024-03-26 21-43-05.png]]
we can set filter to show only in scope items  (click on filter bar (the funnel symbol) to open this filter settings)
![[Screenshot from 2024-03-26 21-45-26.png]]









or we can do the same thing by : "use advance scope control" 
![[Screenshot from 2024-03-26 21-52-12.png]]
include in scope (click add) > enter "azena.com" in host or ip range:
![[Screenshot from 2024-03-26 21-55-00.png]]
output:
![[Screenshot from 2024-03-26 22-02-36.png]]
in the output we can see 3 different folders and if we search through them we may find some other website/subdomain come/pop up


turn of the interceptor for now so that 
we can navigate through the website https://store.azena.com/shop/  ( in firefox while foxyproxy is on but interceptot in burp is off so we dont intercept the traffic instead just watch it in "target" section)to understand what things are there in the website maybe sign up to get more functionality so that we can test even deeper just get familiar with the website and do info gathering by moving around the website and its subdomains.


so basically just click around and navigate the website and gain a good understanding about what the website is doing and why, how it is doing everything. This is called business logic understand what is the business logic of the site.

do it by just clicking around like checking what is redirecting you to another page , try clicking on every thing like login,  signup , apps, azena tools ,application understand there intentions.


```

in " Target " section we dont need to turn intercpt on i.e its a passive way of recon.

in " Proxy " section we can turn intercept on and actively intercept,edit, forward,drop etc the traffic as we require.

```





Most important part of Burp Suite that we are mostly going to use all the time  :
Proxy
Repeater 
Intruder
Target












 