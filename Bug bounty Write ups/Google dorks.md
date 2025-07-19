
Dorking commands tool:
https://dorkking.blindf.com/

Note: In the following Google Dorking commands, the site: field is left empty intentionally.
👉 Replace it with your target domain like this :
```
site:target.com
```

-----

----


Directory listing:
```
site:  intitle:index.of
```


Config files:
```
site: ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg | ext:txt | ext:ora | ext:ini
```



DB files:
```
site: ext:sql | ext:dbf | ext:mdb
```


WordPress:
```
site: inurl:wp- | inurl:wp-content | inurl:plugins | inurl:uploads | inurl:themes | inurl:download
```


Log files:
```
site: ext:log
```


Backup/Old files:
```
site: ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
```



Login page:
```
site: inurl:login | inurl:signin | intitle:Login | intitle: signin | inurl:auth
```
Or
```
site:*.company.com admin  
site:*.company.com login
```



SQL error:
```
site: intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:"Warning: mysql_query()" | intext:"Warning: pg_connect()"
```





Exposed docs:
```
site: ext:doc | ext:docx | ext:odt | ext:pdf | ext:rtf | ext:sxw | ext:psw | ext:ppt | ext:pptx | ext:pps | ext:csv
```



PhP info() :
```
site: ext:php intitle:phpinfo 'published by the PHP Group'
```


Backdoor :
```
site: inurl:shell | inurl:backdoor | inurl:wso | inurl:cmd | shadow | passwd | boot.ini | inurl:backdoor
```




==Open redirect== :
```
site: inurl:redir | inurl:url | inurl:redirect | inurl:return | inurl:src=http | inurl:r=http
```
OR
```
site: inurl:(redir|url|redirect|return|next|src|r|out|view|to|dest|destination)=http
OR site:target.com inurl:(redir|url|redirect|return|next|src|r|out|view|to|dest|destination)=https
OR site:target.com inurl:(redir|url|redirect|return|next|src|r|out|view|to|dest|destination)=// 
OR site:target.com inurl:(redir|url|redirect|return|next|src|r|out|view|to|dest|destination)=%2f%2f
OR site:target.com inurl:(redir|url|redirect|return|next|src|r|out|view|to|dest|destination)=/redirect?
```



3rd party exposure:
```
site:http://ideone.com | site:http://codebeautify.org | site:http://codeshare.io | site:http://codepen.io | site:http://repl.it | site:http://justpaste.it | site:http://pastebin.com | site:http://jsfiddle.net | site:http://trello.com | site:*.atlassian.net | site:bitbucket.org ""
```



Find in pastebin:
```
site:pastebin.com "target.com"
```


Subdomains(crt.sh) :
```
https://crt.sh/?q=target.com
```



Find WordPress #2 :
```
site:target.com inurl:wp-content | inurl:wp-includes
```



Bitbucket/Atlassian:
```
site:atlassian.net | site:bitbucket.org "target.com"
```



Stack Overflow:
```
site:stackoverflow.com "target.com"
```


All WayBack URL's :
```
https://web.archive.org/cdx/search/cdx?url=*.target.com/*&output=text&fl=original&collapse=urlkey
```


Search in GitHub:
```
https://github.com/search?q=%22*.target.com%22
```
Or
```
https://github.com/search?q=%22*.target.com%22&type=repositories
```

Open Bug Bounty:
```
https://www.openbugbounty.org/search/?search=target.com
```


.git Folder
```
inurl:"/.git "target.com -github
```


Find .swf(Google)
```
inurl:target.com ext:swf"
```


S3 buckets :
```
site:.s3.amazonaws.com "target.com"
```



Shodan search :
```
https://www.shodan.io/search?query=target.com
```


API (WSDL)
```
site:target.com filetype:wsdl | filetype:WSDL | ext:svc | inurl:wsdl | Filetype: ?wsdl | inurl:asmx?wsdl | inurl:jws?wsdl | intitle:_vti_bin/sites.asmx?wsdl | inurl:_vti_bin/sites.asmx?wsdl
```


GIST(GitHub search)
```
https://gist.github.com/search?q=*.%22target.com%22
```



Apache config files :
```
site:target.com filetype:config "apache"
```



Install/setup files :
```
site:target.com inurl:readme | inurl:license | inurl:install | inurl:setup | inurl:config
```



Apache struts RCE :
```
site:target.com ext:action | ext:struts | ext:do
```


.htaccess/phpinfo() :
```
site:target.com inurl:"/phpinfo.php" | inurl:".htaccess"
```



==Security Headers== :
```
https://securityheaders.com/?q=target.com&followRedirects=on
```



Source code (publicwww.com) :
```
https://publicwww.com/websites/%22target.com%22/
```


Search Gitlab and GitHub:
```
site:github.com | site:gitlab.com "target.com"
```



Find .pho WayBack: (use UI)
```
https://web.archive.org/cdx/search?url=target.com/&matchType=domain&collapse=urlkey&output=text&fl=original&filter=urlkey:.*php&limit=100000
```