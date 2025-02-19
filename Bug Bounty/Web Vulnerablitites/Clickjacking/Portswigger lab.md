Labs:  https://portswigger.net/web-security/all-labs#clickjacking

# 1)Lab: Basic clickjacking with CSRF token protection

This lab contains login functionality and a delete account button that is protected by a CSRF token. A user will click on elements that display the word "click" on a decoy website.

To solve the lab, craft some HTML that frames the account page and fools the user into deleting their account. The lab is solved when the account is deleted.

You can log in to your own account using the following credentials: `wiener:peter`


#### Note

The victim will be using Chrome so test your exploit on that browser.


#### Solution
1. Log in to your account on the target website.
2. Go to the exploit server and paste the following HTML template into the **Body** section:
```

```