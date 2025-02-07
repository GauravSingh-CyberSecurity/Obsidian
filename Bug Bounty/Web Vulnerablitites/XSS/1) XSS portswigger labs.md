
Link: https://portswigger.net/web-security/cross-site-scripting#what-is-cross-site-scripting-xss

cheat-sheet: https://portswigger.net/web-security/cross-site-scripting/cheat-sheet

Types of XSS:
1)Reflected XSS: https://portswigger.net/web-security/cross-site-scripting/reflected
2)Stored XSS: https://portswigger.net/web-security/cross-site-scripting/stored
3)
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


# 6)Lab (imp): DOM XSS in jQuery selector sink using a hashchange event

LAb: https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event

This lab contains a DOM-based cross-site scripting vulnerability on the home page. It uses jQuery's `$()` selector function to auto-scroll to a given post, whose title is passed via the `location.hash` property.

To solve the lab, deliver an exploit to the victim that calls the `print()` function in their browser.

```
 ####  Solution

1. Notice the vulnerable code on the home page using Burp or the browser's DevTools.
2. From the lab banner, open the exploit server.
3. In the **Body** section, add the following malicious `iframe`:
    
    `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>`
4. Store the exploit, then click **View exploit** to confirm that the `print()` function is called.
5. Go back to the exploit server and click **Deliver to victim** to solve the lab.
```


# 7)Lab: Reflected XSS into attribute with angle brackets HTML-encoded

LAB: https://portswigger.net/web-security/cross-site-scripting/contexts/lab-attribute-angle-brackets-html-encoded

Video: https://www.youtube.com/watch?v=8zis9TrZmfU

This lab contains a reflected cross-site scripting vulnerability in the search blog functionality where angle brackets are HTML-encoded. To solve this lab, perform a cross-site scripting attack that injects an attribute and calls the `alert` function.

```
 ####  Hint

Just because you're able to trigger the `alert()` yourself doesn't mean that this will work on the victim. You may need to try injecting your proof-of-concept payload with a variety of different attributes before you find one that successfully executes in the victim's browser.
```

#### Solution

1. Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.
2. Observe that the random string has been reflected inside a quoted attribute.
3. Replace your input with the following payload to escape the quoted attribute and inject an event handler:
    
    `"onmouseover="alert(1)`    or    "onmouseover='alert(1)' 
4. Verify the technique worked by right-clicking, selecting "Copy URL", and pasting the URL in the browser. When you move the mouse over the injected element it should trigger an alert.

```
i.e "onmouseover='alert(1)'  in this payload the ( " ) breaks out from the input string and then executes the function ( onmouseover='alert(1)' ) resulting in alert message pop up as '1' every time there is a mouse movement.
```


