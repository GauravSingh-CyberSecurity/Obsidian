
---

`HTML Injection` vulnerabilities can often be utilized to also perform [Cross-Site Scripting (XSS)](https://owasp.org/www-community/attacks/xss/) attacks by injecting `JavaScript` code to be executed on the client-side. Once we can execute code on the victim's machine, we can potentially gain access to the victim's account or even their machine. `XSS` is very similar to `HTML Injection` in practice. However, `XSS` involves the injection of `JavaScript` code to perform more advanced attacks on the client-side, instead of merely injecting HTML code. There are three main types of `XSS`:

|Type|Description|
|---|---|
|`Reflected XSS`|Occurs when user input is displayed on the page after processing (e.g., search result or error message).|
|`Stored XSS`|Occurs when user input is stored in the back end database and then displayed upon retrieval (e.g., posts or comments).|
|`DOM XSS`|Occurs when user input is directly shown in the browser and is written to an `HTML` DOM object (e.g., vulnerable username or page title).|

In the example we saw for `HTML Injection`, there was no input sanitization whatsoever. Therefore, it may be possible for the same page to be vulnerable to `XSS` attacks. We can try to inject the following `DOM XSS` `JavaScript` code as a payload, which should show us the cookie value for the current user:

Code: javascript

```javascript
#"><img src=/ onerror=alert(document.cookie)>
```

Once we input our payload and hit `ok`, we see that an alert window pops up with the cookie value in it:

![Dialog box displaying a cookie value and a 'Close' button.](https://academy.hackthebox.com/storage/modules/75/web_apps_xss_2.jpg)

This payload is accessing the `HTML` document tree and retrieving the `cookie` object's value. When the browser processes our input, it will be considered a new `DOM`, and our `JavaScript` will be executed, displaying the cookie value back to us in a popup.

An attacker can leverage this to steal cookie sessions and send them to themselves and attempt to use the cookie value to authenticate to the victim's account. The same attack can be used to perform various types of other attacks against a web application's users. `XSS` is a vast topic that will be covered in-depth in later modules.



---

#### Questions

Answer the question(s) below to complete this Section and earn cubes!

Target(s): 83.136.253.25:51662   

Life Left: 78 minute(s)

+ Q)   Try to use XSS to get the cookie value in the above page

#####   Hint
###### You can borrow the XSS payload we used earlier in this section. Enter the cookie value as the answer, without 'cookie='.


Solution: 

1) start the machine and go to the ip(83.136.253.25:51662) , there you'll see a button "click to enter your name" - click the button
2) an input field pops up , saying enter your name 
3) in input field enter the XSS injection payload  
==` #"><img src=/ onerror=alert(document.cookie)> `==  and hit "ok"   
4) 4) the XSS injection was successfull and we got an alert popup "cookie=XSSisFun"  on the web page 
5) submit the value of cookie= ( ==XSSisFun== ) and the lab is solved