Link: https://portswigger.net/web-security/cross-site-scripting#what-is-cross-site-scripting-xss



# 1)Lab: Reflected XSS into HTML context with nothing encoded
lab: https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded

```
 ####  Solution

1. Copy and paste the following into the search box:
    
    `<script>alert(1)</script>`
    
1. Click "Search".

```



# 2)Lab: Stored XSS into HTML context with nothing encoded

LAB: https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded

```
 ####  Solution

1. Enter the following into the comment box:
    
    `<script>alert(1)</script>`
2. Enter a name, email and website.
3. Click "Post comment".
4. Go back to the blog.
```


# 3)Lab: DOM XSS in `document.write` sink using source `location.search`

```
 ####  Solution

1. Enter a random alphanumeric string into the search box.
2. Right-click and inspect the element, and observe that your random string has been placed inside an `img src` attribute.
3. Break out of the `img` attribute by searching for:
    
    `"><svg onload=alert(1)>`
```
