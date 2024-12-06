- **Broken Access control vulnerablity**
    
    most common vulnerablity with 94% of the website tested being vulnerable to it
    
    what we can do using this vulnerablity is
    
    modify/access user info without logging in that belongs to some other user .
    
    
    
    
    
    **Video 2: cookie manipulation**
    
    **Lab: User role controlled by request parameter** ([https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter))
    
    we logged into the website as a user , than tried to get admin by /admin after the url but it only allows access to admin for that /admin repo .
    
    so we used burp suite and captured the request and in interceptor at cookies we saw there is a section admin and its value is false we changed it to true and send request back to website and got logged in as admin
    
    now , we will have to change false to true again and again at every request that is send to website because we havent put the admin id and pw to get authenticated , so instead of changing the false to true every time burp intercept the request.
    
    we can go to proxy settings>match and replace rules>Add>match (Admin=false)>replace(Admin=true)
    
    
    
    
    
    **video 3:** Accessing private user data
    
    **Lab: User ID controlled by request parameter, with unpredictable user IDs**
    
    ([https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids))
    
    This lab has a horizontal privilege escalation vulnerability on the user account page, but identifies users with GUIDs.
    
    To solve the lab, find the GUID for `carlos`, then submit his API key as the solution.
    
    You can log in to your own account using the following credentials: `wiener:peter`
    
    view posts
    
    see carlos posts
    
    click on carlos and youll find user id in url, copy it
    
    click on my account
    
    paste carlos user id in urld of , my accounts user id
    
    you get :-
    
    Your username is: carlos
    
    Your API Key is: naczvyX5SXT6B1ZDjPwrMFAm5SoTs3H4
    
    **Lab: User ID controlled by request parameter with password disclosure**
    
    ([https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure))
    
    This lab has user account page that contains the current user's existing password, prefilled in a masked input.
    
    To solve the lab, retrieve the administrator's password, then use it to delete the user `carlos`.
    
    You can log in to your own account using the following credentials: `wiener:peter`
    
    1. Log in using the supplied credentials and access the user account page.
    2. Change the "id" parameter in the URL to `administrator`.
    3. View the response in Burp and observe that it contains the administrator's password.
    4. Log in to the administrator account and delete `carlos`.
    
    <input required="" type="password" name="password" value="tnzsmhfdlszs2cb780o4">
    
    
    
    
    
    
    **video4:-** Discovring IDOR vulnerablity
    
    **Lab: Insecure direct object references(**[https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references**](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references**))**
    
    
    
    
    
    
    **video 5:**- Privilege escalation with burp repeater
    
    **Lab: User role can be modified in user profile(**[https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile**](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile**))**
    
    This lab has an admin panel at `/admin`. It's only accessible to logged-in users with a `roleid` of 2.
    
    Solve the lab by accessing the admin panel and using it to delete the user `carlos`.
    
    You can log in to your own account using the following credentials: `wiener:peter`
    
    1. Log in using the supplied credentials and access your account page.
    2. Use the provided feature to update the email address associated with your account.
    3. Observe that the response contains your role ID.
    4. Send the email submission request to Burp Repeater, add `"roleid":2` into the JSON in the request body, and resend it.
    5. Observe that the response shows your `roleid` has changed to 2.
    6. Browse to `/admin` and delete `carlos`.
    
    
    
    
    
    **video6:**- .Debugging Flows with HTTP TRACE and gaining admin access
    
    **Lab: Authentication bypass via information disclosure(**[https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass**](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass**))**