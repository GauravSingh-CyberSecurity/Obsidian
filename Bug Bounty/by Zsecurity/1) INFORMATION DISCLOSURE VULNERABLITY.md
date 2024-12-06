

- **INFORMATION DISCLOSURE VULNERABLITY(any kind of bug that leaks information)**
    
    This is called Cryptographic faliure vulnerablity in OWASP Top 10
    
    **solving portswiggerlab:-**
    
    **Video2**
    
    **Lab: Source code disclosure via backup files**
    
    [https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)
    
    /robots.txt (these txt file contains path that website should not index i.e anything present in robots.txt will not get loaded in normal website )
    
    /backup
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
    
    <https://0ab200ad049ad2f180cc0d8d0015003f.web-security-academy.net/product?productId=1> (this 1 will be sent  as a get method to the website i.e get product with id 1 )  
    
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
    
    
    
  
    


