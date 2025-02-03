
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
3. Log out of your account.
4. Log in using the victim's credentials.
5. When prompted for the verification code, manually change the URL to navigate to `/my-account`. The lab is solved when the page loads.