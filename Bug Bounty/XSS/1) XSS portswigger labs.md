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

Lab:https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink

```

This lab contains a DOM-based cross-site scripting vulnerability in the search query tracking functionality. It uses the JavaScript `document.write` function, which writes data out to the page. The `document.write` function is called with data from `location.search`, which you can control using the website URL.

To solve this lab, perform a cross-site scripting attack that calls the `alert` function.




 ####  Solution

1. Enter a random alphanumeric string into the search box.
2. Right-click and inspect the element, and observe that your random string has been placed inside an `img src` attribute.
3. Break out of the `img` attribute by searching for:
    
    `"><svg onload=alert(1)>`
```

# 4)Lab: DOM XSS in `innerHTML` sink using source `location.search`

Lab: https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink

```
This lab contains a DOM-based cross-site scripting vulnerability in the search blog functionality. It uses an `innerHTML` assignment, which changes the HTML contents of a `div` element, using data from `location.search`.

To solve this lab, perform a cross-site scripting attack that calls the `alert` function.



 ####  Solution

1. Enter the following into the into the search box:
    
    `<img src=1 onerror=alert(1)>`
2. Click "Search".

The value of the `src` attribute is invalid and throws an error. This triggers the `onerror` event handler, which then calls the `alert()` function. As a result, the payload is executed whenever the user's browser attempts to load the page containing your malicious post.

 
```


# 5)Lab: DOM XSS in jQuery anchor `href` attribute sink using `location.search` source

Lab: https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink

```
This lab contains a DOM-based cross-site scripting vulnerability in the submit feedback page. It uses the jQuery library's `$` selector function to find an anchor element, and changes its `href` attribute using data from `location.search`.

To solve this lab, make the "back" link alert `document.cookie`.


 ####  Solution

1. On the Submit feedback page, change the query parameter `returnPath` to `/` followed by a random alphanumeric string.
2. Right-click and inspect the element, and observe that your random string has been placed inside an a `href` attribute.
3. Change `returnPath` to:
    
    `javascript:alert(document.cookie)`
    
    Hit enter and click "back".
```

