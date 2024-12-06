![[Pasted image 20240910110306.png]]



**XSS in get and post method**

- Get Method Reflected XSS attacks, also known as non-persistent attacks, occur when a malicious script is reflected off of a web application to the victim's browser. The script is activated through a link, which sends a request to a website with a vulnerability that enables execution of malicious scripts. -

- Post method What is POST XSS? It is a client-side vulnerability that is used to run malicious script by sending input to the vulnerable website via the form with the POST method of the HTTP protocol


**Xss reflected (Get)**
Eg of XSS using the get method (it is shown in URL parameter) 
![[Pasted image 20240910111306.png]]



**Xss reflected (Post method)**  nothing is shown in url, but message reflected on UI as shown in SS
![[Pasted image 20240910112547.png]]

payload used in input after we understood there is  reflected XSS (post method) present 
![[Pasted image 20240910113127.png]]

after hitting input as go 

![[Pasted image 20240910113452.png]] 




