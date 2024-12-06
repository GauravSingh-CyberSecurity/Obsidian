
Video 1 ) introduction to Authentication
---
authentication and authorisation/access control:

| Feature                  | Authentication                                                     | Authorization/Access Control                                     |
|--------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------|
| Definition               | Verifies the identity of a user or system.                         | Determines what a user or system can access and do.              |
| Purpose                  | Ensures that users or systems are who they claim to be.            | Ensures that authenticated users or systems have appropriate permissions. |
| Process                  | Requires users or systems to provide credentials (e.g., username and password). | Assigns permissions based on the authenticated identity.       |
| Examples                 | Logging in to a computer with a username and password.             | Accessing specific files, folders, or resources based on user roles. |
| Key Components           | User credentials, authentication methods (e.g., passwords, biometrics). | Permissions, roles, access control lists (ACLs).                 |
| Granularity              | Focuses on verifying the identity of a user or system.             | Focuses on defining and enforcing access rights and permissions. |
| Dependency               | Precedes authorization. Authentication must occur before authorization. | Relies on authentication to ensure that only authorized users gain access. |
| Importance in Security   | Fundamental for ensuring that only authorized entities access resources. | Critical for enforcing the principle of least privilege.        |
| Common Technologies      | Username/password, biometric scanners, two-factor authentication. | Role-based access control (RBAC), attribute-based access control (ABAC). |

This table provides a concise overview of the differences between authentication and authorisation/access control, highlighting their respective roles and key components in security systems.



Two ways we are going to attack Authentication :- 
1. Brute-force Attack
2. Logical issues




Note:- from here i am using my own labs because tcm labs needs subscription
I am going to use this : ( https://portswigger.net/web-security/authentication )
video 2) Brute Force Attack 
---
https://portswigger.net/web-security/authentication/password-based#brute-force-attacks




 ==**Lab: Username enumeration via different responses**==
https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses

soln:
username=atlas&password=zxcvbnm




video 3 ) Attacking MFA 
---
https://portswigger.net/web-security/authentication/multi-factor




**==Lab: 2FA simple bypass==**
https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass



soln :
my account url -> https://0a7900300343148182c44c26007f0057.web-security-academy.net/my-account?id=wiener

==my-account?id=wiener==     change it to ==my-account?id=carlos==   for bypassing carlos mfa


https://0a7900300343148182c44c26007f0057.web-security-academy.net/my-account?id=carlos





video 4)  Attack type : cluster bomb
---
we can use cluster bomb to attack username and password bruteforce at same tine

username=§atlas§&password=§kj§  

and we paste/load payload set : 1 and 2 for   username=§atlas§&password=§kj§  




video 5) introduction to authorization
---
vertical access control (admin,user)
horizontal access control (user1, user2)
context depended AC (eg: cant check out if item is sold out)


video 6) IDOR (refer Zsecurity)
---
this tcm video for IDOR basically teaches a new way of exploiting IDOR i.e

when you find an IDOR like the transcript id : 1.txt
you can use the intruder to bruteforce the 1.txt to say (1 - 100 id's)

and see which id's are related to the admin and use it to login as the admin.

Video 7) introduction to API (Application programming interface)
---
API make up more than 80% of internet traffic many apps are powered by them 
and API driven apps behave in slightly different way so our approach to this apps will be a little different.

Lets see this API : Cat Facts API ( https://catfact.ninja/ )
lets make same basic calls to the endpoints using this api and look at the structure of request and response of an api powered apps.

![[Screenshot from 2024-04-02 10-46-51.png]]


we make this get request using terminal :
```
curl https://catfact.ninja/breeds
```
the o/p in terminal is kind of unreadable so lets proxy it in burp suite and look at it in burpsuite :
run this get command in terminal to have it proxy in burp suite:
```
curl --proxy http://localhost:8080 https://catfact.ninja/breeds -k
```

so this is the get request and the data on the left side   i.e
"breed" ","country","origin","coat","pattern" 
![[Screenshot from 2024-04-02 10-53-57.png]]


so this get request on browser would have returned navigation bar, content ,html doc 
it just return raw data and we(our app) can take this data and do what we want with it.

Now the PUT request 
in terminal:
```
curl -X PUT --proxy http://localhost:8080 https://catfact.ninja/breeds -k -d '{name: "cheese cat"}'
```
PS: Documentation of this application catfact.ninja don't accepts post and put requests , but we might want to test it anyway just in case the documentation don't give us all of the information.

play with the api learn how to interact with them get info from them and how to pass it.


