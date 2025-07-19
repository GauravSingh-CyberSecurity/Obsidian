
Dorking commands tool:
https://dorkking.blindf.com/

Note: in below Dorking commands put values of the target site(targetsite.com), like this-
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