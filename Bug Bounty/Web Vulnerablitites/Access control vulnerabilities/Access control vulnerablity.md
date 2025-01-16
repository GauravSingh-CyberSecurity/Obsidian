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

