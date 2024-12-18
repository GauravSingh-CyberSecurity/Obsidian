https://www.youtube.com/watch?v=wX6tszfgYp4

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