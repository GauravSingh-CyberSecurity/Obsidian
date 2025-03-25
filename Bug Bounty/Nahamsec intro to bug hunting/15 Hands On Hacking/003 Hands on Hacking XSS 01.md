Looking for XSS where ever we can find input fields, using basic payload 
` ""><U>test123" `
if this payload gets executed the result will show test123(as underlined text) 

using browser dev tools>inspect element , and look for input payloads see the input in Js body, script, and all other places where the input ends up, try to manipulate the JS and create a malicious payload with valid syntax of JS :
`" "><U>test123';alert();//"`



---
### Step 1. Preparation and Environment Setup

1. **Open the Target Website:**
    
    - Navigate to the website’s public-facing section (e.g., the shop/store area) where functionality such as registration, product search, or ordering is available.
        
    - Note that the website displays elements like the home page, registration page, and product search field—all potential injection points.
        
2. **Identify Injection Points:**
    
    - Look for user-input fields (for example, the product search field) where any text can be entered. These fields are likely candidates for testing cross-site scripting (XSS) vulnerabilities.
        

---

### Step 2. Initial Payload Injection

1. **Enter a Basic Payload:**
    
    - In the search field, input a simple XSS payload to observe if the data is reflected. For example, type:
        
        ```
        <script>alert('Test 1, 2, 3');</script>
        ```
        
    - Observe the page response. If the payload is not executed, it might be filtered or encoded.
        
2. **Inspect the Reflected Output:**
    
    - Open your browser’s Developer Tools (e.g., right-click → Inspect).
        
    - Look at the HTML source where your input appears.
        
        - If you see your text within an H3 tag or elsewhere without execution, note the context (e.g., inside a JavaScript variable or within quotes).
            

---

### Step 3. Analyze the Context

1. **Examine the DOM Structure:**
    
    - Determine if your input is being placed inside HTML tags, JavaScript code, or within attributes.
        
    - Note if special characters (such as `<`, `>`, `'`, or `;`) are being encoded.
        
        - Example: If the payload `<script>alert('XSS');</script>` appears as `&lt;script&gt;alert(&#39;XSS&#39;);&lt;/script&gt;`, it means the application is encoding certain characters.
            
2. **Context-Specific Testing:**
    
    - If the payload is reflected within single quotes, try adding payloads that exploit that context.
        
        - For instance, if it’s inside a JavaScript string, you might try:
            
            ```
            ');alert('XSS');//  
            ```
            
    - Document the output and note which characters are encoded and which are not.
        

---

### Step 4. Advanced Payload Injection

1. **Test with Variations:**
    
    - Try different payloads that target the specific reflection context. Examples include:
        
        - **Basic Script Injection:**
            
            ```html
            <script>alert('XSS');</script>
            ```
            
        - **Attribute Injection (if input is within an attribute):**
            
            ```html
            " onmouseover="alert('XSS')
            ```
            
        - **JS Context Breakout:**  
            If your input is inside single quotes, try:
            
            ```
            ');alert('XSS');//  
            ```
            
        - **SVG-based Payload:**
            
            ```html
            <svg/onload=alert('XSS')>
            ```
            
2. **Observe the Behavior:**
    
    - For each payload, inspect the output using the Developer Tools:
        
        - If the payload is encoded (e.g., special characters are replaced with HTML entities), note which characters remain unencoded.
            
        - If you see any alteration or partial execution, adjust your payload accordingly.
            

---

### Step 5. Bypass Filtering and Encoding

1. **Isolate the Problematic Context:**
    
    - Determine if additional characters such as an extra apostrophe or semicolon are being encoded.
        
    - For example, if entering `'test'` results in the apostrophes being encoded, try duplicating the input with variations to see if a syntax error occurs.
        
2. **Combine Payload Elements:**
    
    - If some characters are encoded while others are not, construct a payload that exploits the unencoded parts.
        
    - For instance, if the payload `'test'` shows one set as raw while the added characters are encoded, try:
        
        ```
        ');alert('XSS');//  
        ```
        
    - If needed, comment out the remaining original code by injecting comment syntax (e.g., `//` for JavaScript) to isolate your payload.
        

---

### Step 6. Confirm Vulnerability Exploitation

1. **Execute a Confirmatory Payload:**
    
    - Once you identify that some payloads are partially executing or causing script errors, inject a payload that triggers a clear, visible response (such as an alert box).
        
    - Example payload:
        
        ```html
        <script>alert('XSS Vulnerability Confirmed');</script>
        ```
        
    - Verify that the alert appears when the page loads or when an action (such as a mouse hover) occurs.
        
2. **Document the Results:**
    
    - Record which payloads worked, the context in which they worked, and any differences in behavior (e.g., encoded characters, error messages, or script execution).
        
    - Ensure you capture screenshots and note the exact injection point and context for later reporting.
        

---

### Step 7. Final Documentation and Next Steps

1. **Document the Vulnerability:**
    
    - Clearly detail the injection point, the payloads used, and the observed behavior.
        
    - Include information about which characters are encoded and which are not.
        
2. **Plan Remediation Testing:**
    
    - Based on the findings, plan further tests to see if additional payloads or bypass techniques could be applied.
        
    - Suggest improvements or additional filtering rules for developers to implement as part of the remediation process.
        
3. **Reporting:**
    
    - Compile a report that includes all steps, payloads, and results.
        
    - Share this report with the appropriate security team or stakeholders for further action.
        

---

This procedure provides a comprehensive, step-by-step walkthrough for conducting a hands-on XSS demonstration, including testing payloads, analyzing encoding, and documenting findings. Use this as a guide for your practical exercises and vulnerability assessments.


---

# Transcript :
1
00:00:00,550 --> 00:00:08,250
I copied out into this and we're going to go to shop and, ahem, store them because there is some functionality

2
00:00:08,250 --> 00:00:08,580
here.

3
00:00:08,850 --> 00:00:14,580
There's home, there is a turn's where you can put an order, no log in.

4
00:00:14,580 --> 00:00:17,520
And obviously there's registration and we can create a new account.

5
00:00:17,910 --> 00:00:19,500
And then there is your card as well.

6
00:00:19,900 --> 00:00:25,080
So this is looking at this website without even logging in, I see a search for products, so anywhere

7
00:00:25,080 --> 00:00:26,790
that I can put in user input.

8
00:00:27,030 --> 00:00:31,650
So I mean, anybody that can type in any text, I would like to look for a cross scripting.

9
00:00:31,980 --> 00:00:38,970
And as I've always said, I'd like to start with a ASML tag and a test one, two, three to get it started.

10
00:00:38,970 --> 00:00:39,920
So I type that in.

11
00:00:40,320 --> 00:00:47,760
It's going to come back and say, hey, that wasn't found, but it looks like we are getting some text

12
00:00:47,760 --> 00:00:56,120
reflected back when I open up our inspect element and we are going to look for test one, two, three.

13
00:00:56,520 --> 00:01:00,030
It looks like we are within a H3 tag.

14
00:01:00,690 --> 00:01:02,010
Not so much to do there.

15
00:01:02,340 --> 00:01:07,320
And if we look down here, we're it looks like we're in a JavaScript tag, in a script tag assigned

16
00:01:07,320 --> 00:01:13,980
to a variable card search, which does some stuff with it and then makes another call at the bottom.

17
00:01:13,980 --> 00:01:18,330
But it looks like it's actually taking are less than or greater than signs.

18
00:01:18,850 --> 00:01:24,370
So these two right here or these three actually right here and it's actually encoding them.

19
00:01:24,390 --> 00:01:25,890
So that means that it's not working.

20
00:01:26,160 --> 00:01:31,440
But if you look at the context of worryin, again, when it comes down to looking for Zarzis context,

21
00:01:31,440 --> 00:01:32,790
it's very, very important.

22
00:01:33,030 --> 00:01:39,330
Just because these three characters were encoded, as I mean, that we can't still look for other stuff.

23
00:01:39,330 --> 00:01:43,850
So if you can see, we are between single quotes, not double quotes and an apostrophe.

24
00:01:43,860 --> 00:01:49,050
So what I'm going to do is I'm going to add the same exact syntax and I'm going to see what comes back.

25
00:01:49,560 --> 00:01:56,940
If the other two additional characters, the apostrophe and the semicolon, they came back as encoded,

26
00:01:56,940 --> 00:01:57,870
then we can move on from it.

27
00:01:57,870 --> 00:02:00,330
But that's the kind that really quickly test one, two, three.

28
00:02:00,330 --> 00:02:02,970
It looks like it actually added our tax.

29
00:02:02,970 --> 00:02:08,510
If we look at this right here, it looks like the apostrophe and the semicolon were both taken.

30
00:02:08,520 --> 00:02:11,770
So I'm going to do is I'm going to comment the rest of it out.

31
00:02:11,780 --> 00:02:16,470
So whatever it was originally there, I'm going to comment it up and we're going to go back to it again

32
00:02:17,970 --> 00:02:19,350
by typing test one, two, three.

33
00:02:19,920 --> 00:02:23,970
And we can see that the second one to the first set, that's one right here.

34
00:02:24,360 --> 00:02:26,520
This apostrophe and semicolon were given by me.

35
00:02:26,860 --> 00:02:32,910
Everything after the the two sashays were there by default and the application it was in the source

36
00:02:32,910 --> 00:02:33,140
of it.

37
00:02:33,450 --> 00:02:38,910
So now I'm going to just add my again, this is something that we covered earlier in our other chapters,

38
00:02:39,030 --> 00:02:43,920
going out an alert to it and see if it works and looks like something just broke.

39
00:02:45,530 --> 00:02:52,280
And way to make room to fix it, so we're going to go ahead and add another apostrophe before it because

40
00:02:52,280 --> 00:02:56,680
we're in JavaScript, we know that that's how they end everything and already had an apostrophe.

41
00:02:56,690 --> 00:02:57,520
We didn't put it there.

42
00:02:57,830 --> 00:02:59,810
I think this time I should give it to us right there.

43
00:02:59,810 --> 00:03:06,830
As you can see, we gave it a valid syntax for our JavaScript and actually did alert later on.

44
00:03:06,840 --> 00:03:10,790
We'll probably cover some other stuff with JavaScript, but it's a good example of how you can actually

45
00:03:10,790 --> 00:03:14,810
discover a vulnerability for exercise and how to look for it.

46
00:03:14,810 --> 00:03:18,370
And Chase said through the DOM, not that we know there is a vulnerability here.

47
00:03:18,380 --> 00:03:19,400
This is a pretty obvious one.

48
00:03:19,410 --> 00:03:21,710
The first thing we did was look at the search box.

49
00:03:21,920 --> 00:03:25,700
I know it sounds unrealistic, but trust me, there's been a ton of times when I've been invited to

50
00:03:25,700 --> 00:03:31,550
a private program, a new program where I found some really weird subdomain that things like that existed

51
00:03:31,550 --> 00:03:32,510
and it was exploitable.

52
00:03:32,720 --> 00:03:36,520
It may be a dupe, but that means there are other vulnerabilities to look for.