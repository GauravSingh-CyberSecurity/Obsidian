
video 1) web technologies 
---
HTML image :
![[Screenshot from 2024-03-25 22-27-13.png]]

HTML (Hyper text markup language): it is used to create web pages
it structures the content such as text, images, lengths it consists of elements represented by tags which define structure and content of pages and generally acts like skeleton of a web page.

we'll be seeing a lot of HTML while bug hunting and also look how we can achieve HTML injection as an indentation of a potential XSS 



CSS image :
![[Screenshot from 2024-03-25 22-36-02.png]]

CSS(cascading Style sheets) : used for describing a representation of a document written in HTML it consists of rule sets where rule defines styling for HTML making it visually appealing. 
we dont care very much about CSS in bug hunting or pentesting but there are some attacks that can be pulled of on CSS as well Eg : stealing user inputs if we are able to inject CSS.










JS(Java Script) image :
![[Pasted image 20240325224457.png]]

JS (java script) : a high level interpreted programming language primarily used to make web pages interactive . It make use of variables, function, objects and events and accessing behaviour of a web page adding dynamic functionality .
JS can give us interesting insights at behaviour on front end and info about endpoints the application is using.
Node.js is popular so learning it a little is needed for server side attacks against node applications.

we need to learn about both Client and Server side attacks.

client side (users device/browser)
server side (the server were web page is hosted and data is stored , retried from)


Here's a table comparing ***traditional and modern web applications*** based on various technical aspects:

| Aspect                 | Traditional Web Apps                              | Modern Web Apps                                   |
|------------------------|---------------------------------------------------|---------------------------------------------------|
| Framework              | Often built with server-side frameworks like      | Built with client-side frameworks like React,     |
|                        | ASP.NET, Ruby on Rails, or Django                | Angular, or Vue.js                               |
| Applications           | Typically monolithic applications with a          | More modular applications with a focus on        |
|                        | single codebase                                   | microservices architecture                       |
| Server Communication   | Primarily server-rendered pages with full page   | Heavy use of APIs for server-client communication|
|                        | reloads                                           | and client-side rendering                         |
| Data Loading           | Data loaded on demand or via full page reloads   | Data loaded asynchronously using AJAX or         |
|                        |                                                | WebSockets                                       |
| Scalability            | Horizontal scaling can be challenging due to     | Easier horizontal scaling due to microservices   |
|                        | monolithic architecture                          | architecture                                      |
| State Management       | State managed primarily on the server             | Client-side state management using libraries     |
|                        |                                                | like Redux or Vuex                               |
| Development            | Usually slower development cycles due to         | Faster development cycles with hot reloading     |
| Experience             | full page reloads                                | and component-based development                  |
| Performance            | Slower performance due to full page reloads      | Faster performance with client-side rendering    |
|                        | and server processing                            | and efficient data loading                       |
| SEO                    | Requires server-side rendering for SEO           | Can be SEO-friendly with server-side rendering   |
|                        | purposes                                          | or pre-rendering                                  |
| Deployment             | Deployment can be complex due to the need        | Easier deployment with containers like Docker    |
|                        | for server setup and configuration               | and orchestration tools like Kubernetes          |
| Important Aspects      | Understanding of server-side technologies like   | Proficiency in client-side frameworks and        |
|                        | PHP, ASP.NET, or Java; knowledge of database     | libraries; understanding of APIs and             |
|                        | technologies like MySQL or SQL Server            | asynchronous programming                         |

These aspects can vary based on specific technologies and approaches used in individual applications.






video 2) HTTP & DNS 
---


HTTP Requests:
![[Screenshot from 2024-03-25 23-22-45.png]]




Response Codes :
![[Screenshot from 2024-03-26 00-02-26.png]]




HTTP is stateless i.e every request from client to the server is considered as a new standalone request with no memory of prior request.
 This is why Cookies are used to maintain states across multiple requests.
 Eg: the server will give user a cookie when they are logged in and use that cookie to identify that user this is used for authentication purposes.






***DNS*** : ==domain name system== is a hierarchical & decentralised naming system  for services or resources that is connected to internet.
DNS translates the human readable domain names to IP addresses

it has a hierarchical structure

top level domain :-   .com , .net , .org
second level :-   tcmsec.com
(sub domain)third level :- dev.tcmsec.com




Here's a table outlining different types of DNS records and their purposes:

| Record Type | Description                                                  |
|-------------|--------------------------------------------------------------|
| A           | Maps a domain name to an IPv4 address                        |
| AAAA        | Maps a domain name to an IPv6 address                        |
| CNAME       | Maps an alias domain name to the canonical domain name       |
| MX          | Specifies mail servers responsible for accepting email       |
| TXT         | Contains text information, such as SPF records for email     |
| NS          | Specifies authoritative name servers for the domain          |
| SOA         | Specifies the start of a zone of authority for the domain    |
| PTR         | Maps an IP address to a domain name (reverse DNS lookup)     |

These records are fundamental to the Domain Name System and are used to manage various aspects of domain name resolution and services.


