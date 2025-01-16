# 1)Lab: Unprotected admin functionality

Lab: https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality

This lab has an unprotected admin panel.

Solve the lab by deleting the user `carlos`.

 ####  Solution

1. Go to the lab and view `robots.txt` by appending `/robots.txt` to the lab URL. Notice that the `Disallow` line discloses the path to the admin panel.
2. In the URL bar, replace `/robots.txt` with `/administrator-panel` to load the admin panel.
3. Delete `carlos`.

# 2)Lab: Unprotected admin functionality with unpredictable URL

Lab:https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url

This lab has an unprotected admin panel. It's located at an unpredictable location, but the location is disclosed somewhere in the application.

Solve the lab by accessing the admin panel, and using it to delete the user `carlos`.

#### Solution

1. Review the lab home page's source using Burp Suite or your web browser's developer tools.
2. Observe that it contains some JavaScript that discloses the URL of the admin panel.
3. Load the admin panel and delete `carlos`.

# 3)Lab: User role controlled by request parameter
Lab:https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter

This lab has an admin panel at `/admin`, which identifies administrators using a forgeable cookie.

Solve the lab by accessing the admin panel and using it to delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

#### Solution

1. Browse to `/admin` and observe that you can't access the admin panel.
2. Browse to the login page.
3. In Burp Proxy, turn interception on and enable response interception.
4. Complete and submit the login page, and forward the resulting request in Burp.
5. Observe that the response sets the cookie `Admin=false`. Change it to `Admin=true`.
6. Load the admin panel and delete `carlos`.