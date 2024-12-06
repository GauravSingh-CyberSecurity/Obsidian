- **INFORMATION DISCLOSURE VULNERABLITY(any kind of bug that leaks information)**
    
    This is called Cryptographic faliure vulnerablity in OWASP Top 10
    
    **solving portswiggerlab:-**
    
    Video2
    
    **Lab: Source code disclosure via backup files**
    
    [https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)
    
    /robots.txt (these txt file contains path that website should not index i.e anything present in robots.txt will not get loaded in normal website )
    
    /backup
    
    ```
     ConnectionBuilder connectionBuilder = ConnectionBuilder.from(
                    "org.postgresql.Driver",
                    "postgresql",
                    "localhost",
                    5432,
                    "postgres",
                    "postgres",
                    **"5foef5g6dq09j52bvb75l3l7iak56zpf"
    (i.e we found PW so its a bug)**
    
    **Video3 :**
    now searching /robot.txt or /backup for vulnerablity is time consuming so we can use **FEROXBUSTER** tool for 
    automation
    
    **install feroxbuster**
    sudo apt update && sudo apt install -y feroxbuster
    
    **searching url with common.txt file**                                          (<https://github.com/danielmiessler/SecLists.git>)
    ****
    feroxbuster --url <https://0af7004b033422dc83ba9e5100ce00b4.web-security-academy.net/> --wordlist "/home/kali/BUG BOUNTY/CRYPTOGRAPHIC FALIURE VULNREABLITY/SecLists-master/Discovery/Web-Content/common.txt"
    
    **video 4 (HTTP status code)
    Lab: Information disclosure in version control history**
    <https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history>
    
    command:
    C:\\home\\kali> feroxbuster --url <https://0a1700ca049ac6a18088f87600d40063.web-security-academy.net/> --wordlist "/home/kali/BUG BOUNTY/CRYPTOGRAPHIC FALIURE VULNREABLITY/common.txt"
    
    by using this we found many diffrent links of login pages, and this repo
    <https://0a1700ca049ac6a18088f87600d40063.web-security-academy.net/.git/>
    
    in this repo we click on config link and found 
    
    core]
    	repositoryformatversion = 0
    	filemode = true
    	bare = false
    	logallrefupdates = true
    [user]
    	**email = carlos@evil-user.net
    	name = Carlos Montoya  (i.e this is info disclosure bug)**
    
     
    now we found 1 single bug but there can be many more bugs in the repo so if you dont have information about the repo or anything(data) that you are seeing , search and learn about it than come back and find the bug.
    
    **bounty hunters may take several months to do these kind of research to understand the tech and then might or might not find the bug**
    
    now since the repo we found was of git , lets learn about git and try to find more bugs(i.e finding admin PW because thats the goal of this videos task)
    
    we downloaded git gui, and now we download the repo to find bugs (admin PW) from the repo.
    
    Download command :
    C:\\home\\kali\\Downloads> wget -r <https://0a1700ca049ac6a18088f87600d40063.web-security-academy.net/.git/>
    
    we open this repo /home/kali/Downloads/0aeb008104ee2bac84d8198100e60062.web-security-academy.net in git-gui and search for admin PW (bug)
    
    then as per video we go to Reposiotry/visualize masters history and we found the old password deleted by the devloper 
    
    ---------------------------------- admin.conf ----------------------------------
    index a07b064..21d23f1 100644
    @@ -1 +1 @@
    -ADMIN_PASSWORD=**qddpg6x6y2pqap8w5oie**
    +ADMIN_PASSWORD=env('ADMIN_PASSWORD')
    
    now by using this PW we went to website and logged in as 
    
    Administrator
    PW: **qddpg6x6y2pqap8w5oie**
    
    and also deleted carlos user and made our own email id as an admin id (hence found the bug and we can report this bug to get a bounty)
    
    **Video 6**  (HTTP methods "GET"):-
    
    <https://0ab200ad049ad2f180cc0d8d0015003f.web-security-academy.net/product?productId=**1> (this 1 will be sent  as a get method to the website i.e get product with id 1 )**   
    
    any value in url that is after "=" sign is sent as get request to target web app , this target web app will process this get request and we can manipulate this value to make the web app to misbehave 
    
    we used BURP SUITE and enabled foxyproxy on firfox browser to proxy traffic from burp and then clicked on the link of product to generate the get request
    then in burp we put garbage value at product id and found a vulnerablity that is disclosing inforamtion 
    
    version of **Apache struts 2 2.3.31 (i.e a bug)**
    
    **Video 7** (Lab: Insecure direct object references**(IDOR)**) IMP in Bug bounty
    
     Lab: Insecure direct object references
    <https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references>
    
    This lab stores user chat logs directly on the server's file system, and retrieves them using static URLs.
    
    Solve the lab by finding the password for the user carlos, and logging into their account.
    
    we using burp suite for reviwing URL
    Select the Live chat tab.
    Send a message and then select View transcript.
    Review the URL and observe that the transcripts are text files assigned a filename containing an incrementing number.
    Change the filename to 1.txt and review the text. Notice a password within the chat transcript.
    Return to the main lab page and log in using the stolen credentials.
    
    Note: we using burp suite for reviwing URL,
    in IDOR 
    Object refrence means : an ID that is unique (in this lab it is Transript(1.txt))
    
    video 8: (capturing post requests using burp suite chromium browsers)
    ```
    
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
    
- **Path Directory Traversal**
    
    **Video1**: Intro to path Traversal vulnerablity and basic discovery
    
    **Lab: [File path traversal](https://portswigger.net/web-security/file-path-traversal), traversal sequences blocked with absolute path bypass**
    
    ([https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass](https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass))
    
    **Video2**: Bypassing absolute path restriction
    
    **Lab: [File path traversal](https://portswigger.net/web-security/file-path-traversal), simple case(**[https://portswigger.net/web-security/file-path-traversal/lab-simple**](https://portswigger.net/web-security/file-path-traversal/lab-simple**))**
    
    GET /image?filename=../../../etc/passwd HTTP/2