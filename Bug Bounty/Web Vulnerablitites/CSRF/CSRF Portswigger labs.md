CSRF: https://portswigger.net/web-security/csrf
Notes by Rana Khalil:  
https://github.com/rkhal101/Web-Security-Academy-Series/blob/main/csrf/

## How to construct a CSRF attack

Manually creating the HTML needed for a CSRF exploit can be cumbersome, particularly where the desired request contains a large number of parameters, or there are other quirks in the request. The easiest way to construct a CSRF exploit is using the [CSRF PoC generator](https://portswigger.net/burp/documentation/desktop/tools/engagement-tools/generate-csrf-poc) that is built in to Burp Suite Professional:

- Select a request anywhere in Burp Suite Professional that you want to test or exploit.
- From the right-click context menu, select Engagement tools / Generate CSRF PoC.
- Burp Suite will generate some HTML that will trigger the selected request (minus cookies, which will be added automatically by the victim's browser).
- You can tweak various options in the CSRF PoC generator to fine-tune aspects of the attack. You might need to do this in some unusual situations to deal with quirky features of requests.
- Copy the generated HTML into a web page, view it in a browser that is logged in to the vulnerable website, and test whether the intended request is issued successfully and the desired action occurs.
- 

CSRF Portswigger labs notes by Rana Khalil: 
https://github.com/rkhal101/Web-Security-Academy-Series/tree/main/csrf



# 1) Lab: CSRF vulnerability with no defenses

 Lab:https://portswigger.net/web-security/csrf/lab-no-defenses


```
This lab's email change functionality is vulnerable to CSRF.

To solve the lab, craft some HTML that uses a CSRF attack to change the viewer's email address and upload it to your exploit server.

You can log in to your own account using the following credentials: `wiener:peter`
```

#### Hint
```

You cannot register an email address that is already taken by another user. If you change your own email address while testing your exploit, make sure you use a different email address for the final exploit you deliver to the victim.
```

#### Solution

1. Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.
2. If you're using Burp Suite Professional, right-click on the request and select Engagement tools / Generate CSRF PoC. Enable the option to include an auto-submit script and click "Regenerate".
    
    Alternatively, if you're using Burp Suite Community Edition, use the following HTML template. You can get the request URL by right-clicking and selecting "Copy URL".

```
<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email"> <input type="hidden" name="email" value="anything%40web-security-academy.net"> 

</form> 
<script> 

document.forms[0].submit(); </script>
```
1. Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".
2. To verify that the exploit works, try it on yourself by clicking "View exploit" and then check the resulting HTTP request and response.
3. Change the email address in your exploit so that it doesn't match your own.
4. Click "Deliver to victim" to solve the lab.


Notes by Rana Khalil:  
https://github.com/rkhal101/Web-Security-Academy-Series/blob/main/csrf/lab-01/notes.txt

 Lab video :https://www.youtube.com/watch?v=HTgyif6u5RY
```
Lab #1 - CSRF vulnerability with no defenses

Vulnerable parameter - email change functionality

Goal - exploit the CSRF vulnerability and change the email address

creds - wiener:peter

Analysis:

In order for a CSRF attack to be possible:
- A relevant action - email change functionality
- Cookie based session handling - session cookie
- No unpredictable request parameters - satisfied
```


# 2) Lab: CSRF where token validation depends on request method

Lab video: (by rana khalil): 

This lab's email change functionality is vulnerable to CSRF. It attempts to block CSRF attacks, but only applies defenses to certain types of requests.

To solve the lab, use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

You can log in to your own account using the following credentials: `wiener:peter`

#### Hint

You cannot register an email address that is already taken by another user. If you change your own email address while testing your exploit, make sure you use a different email address for the final exploit you deliver to the victim

#### Solution

1. Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.
2. Send the request to Burp Repeater and observe that if you change the value of the `csrf` parameter then the request is rejected.
3. Use "Change request method" on the context menu to convert it into a GET request and observe that the CSRF token is no longer verified.
4. If you're using Burp Suite Professional, right-click on the request, and from the context menu select Engagement tools / Generate CSRF PoC. Enable the option to include an auto-submit script and click "Regenerate".
    
    Alternatively, if you're using Burp Suite Community Edition, use the following HTML template. You can get the request URL by right-clicking and selecting "Copy URL".
```
<form action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email"> <input type="hidden" name="email" value="anything%40web-security-academy.net"> </form> <script> document.forms[0].submit(); </script>
```

1. Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".
2. To verify if the exploit will work, try it on yourself by clicking "View exploit" and checking the resulting HTTP request and response.
3. Change the email address in your exploit so that it doesn't match your own.
4. Store the exploit, then click "Deliver to victim" to solve the lab.

Notes by Rana Khalil: 
https://github.com/rkhal101/Web-Security-Academy-Series/blob/main/csrf/lab-02/notes.txt

```
Lab #2 - CSRF where token validation depends on request method

Vulnerable parameter - email change functionality

Goal - exploit CSRF to change email address

Creds - wiener:peter

Analysis:

In order for a CSRF attack to be possible:
- A relevant action: change a users email
- Cookie-based session handling: session cookie
- No unpredictable request parameters: Request method can be changed to GET which does not require CSRF token

Testing CSRF Tokens:
1. Change the request method from POST to GET
```