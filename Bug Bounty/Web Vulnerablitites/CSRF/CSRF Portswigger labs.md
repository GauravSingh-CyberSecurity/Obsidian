CSRF: https://portswigger.net/web-security/csrf




CSRF Portswigger labs notes by Rana Khalil: 
https://github.com/rkhal101/Web-Security-Academy-Series/tree/main/csrf
# 1) Lab: CSRF vulnerability with no defenses

 Lab:https://portswigger.net/web-security/csrf/lab-no-defenses
 Lab video :https://www.youtube.com/watch?v=HTgyif6u5RY

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

