1) Directory listing vulnerability:
```
site:site.com intitle:index.of
```


2) Exposed Configuration files
```
site:site.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg | ext:txt | ext:ora | ext:ini
```


3) Exposed Database files
```
site:site.com ext:sql | ext:dbf | ext:mdb
```


4) Find WordPress
```
site:site.com inurl:wp- | inurl:wp-content | inurl:plugins | inurl:uploads | inurl:themes | inurl:download
```


5) Exposed log files
```
site:site.com ext:log
```


6) Backup and old files
```
site:site.com ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
```

7) Login pages
```
site:site.com inurl:login
```


8) SQL errors
```
site:site.com intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:"Warning: mysql_query()" | intext:"Warning: pg_connect()"
```


9) Publicly exposed documents
```
site:site.com ext:doc | ext:docx | ext:odt | ext:pdf | ext:rtf | ext:sxw | ext:psw | ext:ppt | ext:pptx | ext:pps | ext:csv
```


10) phpinfo()
```
site:site.com ext:php intitle:phpinfo "published by the PHP Group"
```


11) Finding Backdoors
```
site:site.com inurl:shell | inurl:backdoor | inurl:wso | inurl:cmd | shadow | passwd | boot.ini | inurl:backdoor
```


12) Install / Setup files
```
site:site.com inurl:readme | inurl:license | inurl:install | inurl:setup | inurl:config
```


13) Open Redirects
```
site:site.com inurl:redir | inurl:url | inurl:redirect | inurl:return | inurl:src=http | inurl:r=http
```


14) Apache STRUTS RCE
```
site: site.com ext:action | ext:struts | ext:do
```


15) Find Pastebin entries
```
site:pastebin.com site.com
```


16) Employees on LINKEDIN (or any platform like slack,teams)
```
site:linkedin.com employees site.com
```


17) .htaccess sensitive files
```
site:bnhs.org inurl:"/phpinfo.php" | inurl:".htaccess" | inurl:"/.git" bnhs.org -github
```


18) Find Subdomains
```
site:*.site.com
```


19) Find Sub-Subdomains
```
site:*.*.site.com
```


20) Find WordPress #2
```
site:bnhs.org inurl:wp-content | inurl:wp-includes
```


21) Find WordPress [Wayback Machine]
```
http://wwwb-dedup.us.archive.org:8083/cdx/search?url=site.com/&matchType=domain&collapse=digest&output=text&fl=original,timestamp&filter=urlkey:.*wp[-].*&limit=1000000&xx=
```


22) Search in GitHub 
```
https://github.com/search?q=%22*.site.com%22&type=host
```


23) search in Open Bug Bounty 
```
https://www.openbugbounty.org/search/?search=site.com&type=host
```


24) search in reddit 
```
https://www.reddit.com/search/?q=site.com&source=recent
```


25) test cross domain 
```
https://site.com/crossdomain.xml
```


26) check in threat crowd 
```
http://threatcrowd.org/domain.php?domain=site.com
```



27) Find .SWF file (Google)
```
inurl:site.com ext:swf
```


28) Find .SWF file (Yandex)
```
https://yandex.com/search/touch/?text=site%3Asite.com+mime%3Aswf&lr=21310&redircnt=1753791125.1
```



29) Search SWF in WayBack Machine
```
https://web.archive.org/cdx/search?url=site.com/&matchType=domain&collapse=urlkey&output=text&fl=original&filter=urlkey:.*swf&limit=100000&_=1507209148310
```


30) Search in WayBack Machine #2
```
https://web.archive.org/cdx/search?url=site.com/&matchType=domain&collapse=urlkey&output=text&fl=original&filter=mimetype:application/x-shockwave-flash&limit=100000&_=1507209148310
```



31) Search in WayBack Machine #3
```
https://web.archive.org/web/*/site.com/*
```


32) Search in WayBack Machine [List/All]
```
https://web.archive.org/web/*/site.com/*
```



33) check in crt.sh
```
https://crt.sh/?q=%25.site.com
```


34) Check in censys - IP4:
```
https://search.censys.io/search?resource=hosts
```


35) check in censys - Domain:
```
https://search.censys.io/domain?q=site.com
```


36) check in census - certs:
```
https://search.censys.io/certificates?q=site.com
```


37) search in shodan:
```
https://www.shodan.io/search?query=site.com
```


Helper Websites

1) DNSBin - The request.bin of DNS!
```
https://requestbin.net/
```


2) WordPress Scan #1
```
https://hackertarget.com/wordpress-security-scan/
```


3) WordPress Scan #2
```
https://wprecon.com/
```



4) Facebook Certificate Transparency Monitoring [Recon]
```
Facebook Certificate Transparency Monitoring [Recon]
```



5) IP converter
```
https://www.smartconversion.com/ip-address-long-number-converter
```



6) Domain history checker
```
https://whoisrequest.com/history/
```


7) source code search engine:
```
https://publicwww.com/
```

