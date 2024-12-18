https://www.youtube.com/watch?v=wX6tszfgYp4

SQLi Product category filter (https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data) 

Query structure : SELECT * FROM products WHERE category = 'Gifts' AND released = 1

end goal: display all products regardless of category both released and unreleased.
application by default do show unreleased product to user but sqli does it.

