https://portswigger.net/web-security/api-testing

OWASP top 10 API vuln: https://portswigger.net/web-security/api-testing/top-10-api-vulnerabilities

# 1)Lab: Exploiting an API endpoint using documentation

To solve the lab, find the exposed API documentation and delete `carlos`. You can log in to your own account using the following credentials: `wiener:peter`.

```
#### Solution

1. In Burp's browser, log in to the application using the credentials `wiener:peter` and update your email address.
    
2. In **Proxy > HTTP history**, right-click the `PATCH /api/user/wiener` request and select **Send to Repeater**.
    
3. Go to the **Repeater** tab. Send the `PATCH /api/user/wiener` request. Notice that this retrieves credentials for the user `wiener`.
    
4. Remove `/wiener` from the path of the request, so the endpoint is now `/api/user`, then send the request. Notice that this returns an error because there is no user identifier.
    
5. Remove `/user` from the path of the request, so the endpoint is now `/api`, then send the request. Notice that this retrieves API documentation.
    
6. Right-click the response and select **Show response in browser**. Copy the URL.
    
7. Paste the URL into Burp's browser to access the documentation. Notice that the documentation is interactive.
    
8. To delete Carlos and solve the lab, click on the `DELETE` row, enter `carlos`, then click **Send request**.
```


# 2)Lab: Finding and exploiting an unused API endpoint
Lab video: https://youtu.be/qjaBIcqZlfI

To solve the lab, exploit a hidden API endpoint to buy a **Lightweight l33t Leather Jacket**. You can log in to your own account using the following credentials: `wiener:peter`.

```
#### Solution

1. In Burp's browser, access the lab and click on a product.
    
2. In **Proxy > HTTP history**, notice the API request for the product. For example, `/api/products/3/price`.
    
3. Right-click the API request and select **Send to Repeater**.
    
4. In the **Repeater** tab, change the HTTP method for the API request from `GET` to `OPTIONS`, then send the request. Notice that the response specifies that the `GET` and `PATCH` methods are allowed.
    
5. Change the method for the API request from `GET` to `PATCH`, then send the request. Notice that you receive an `Unauthorized` message. This may indicate that you need to be authenticated to update the order.
    
6. In Burp's browser, log in to the application using the credentials `wiener:peter`.
    
7. Click on the **Lightweight "l33t" Leather Jacket** product.
    
8. In **Proxy > HTTP history**, right-click the `API/products/1/price` request for the leather jacket and select **Send to Repeater**.
    
9. In the **Repeater** tab, change the method for the API request from `GET` to `PATCH`, then send the request. Notice that this causes an error due to an incorrect `Content-Type`. The error message specifies that the `Content-Type` should be `application/json`.
    
10. Add a `Content-Type` header and set the value to `application/json`.
    
11. Add an empty JSON object `{}` as the request body, then send the request. Notice that this causes an error due to the request body missing a `price` parameter.
    
12. Add a `price` parameter with a value of `0` to the JSON object `{"price":0}`. Send the request.
    
13. In Burp's browser, reload the leather jacket product page. Notice that the price of the leather jacket is now `$0.00`.
    
14. Add the leather jacket to your basket.
    
15. Go to your basket and click **Place order** to solve the lab.
```
