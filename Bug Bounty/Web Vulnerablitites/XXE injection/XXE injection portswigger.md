XXE portswigger: https://portswigger.net/web-security/xxe

1) check is there an XML that is sent in Post request or in any other request
2) insert a DTD tag , followed by an entity(the entity is external)
eg:
# 1)Lab: Exploiting XXE using external entities to retrieve files
Lab:https://portswigger.net/web-security/xxe/lab-exploiting-xxe-to-retrieve-files


This lab has a "Check stock" feature that parses XML input and returns any unexpected values in the response.

To solve the lab, inject an XML external entity to retrieve the contents of the `/etc/passwd` file.

#### Solution

1. Visit a product page, click "Check stock", and intercept the resulting POST request in Burp Suite.
2. Insert the following external entity definition in between the XML declaration and the `stockCheck` element:
    
    `<!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>`
3. Replace the `productId` number with a reference to the external entity: `&xxe;`. The response should contain "Invalid product ID:" followed by the contents of the `/etc/passwd` file.

lab video: https://www.youtube.com/watch?v=0DQnWalxYb4&ab_channel=Intigriti
- XML DTD :https://www.w3schools.com/xml/xml_dtd.asp