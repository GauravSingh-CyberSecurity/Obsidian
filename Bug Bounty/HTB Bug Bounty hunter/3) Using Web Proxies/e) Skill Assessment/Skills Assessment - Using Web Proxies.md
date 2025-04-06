#### Questions

Answer the question(s) below to complete this Section and earn cubes!

Target(s): 94.237.55.234:47257

Cheat Sheet

+ ==Q1)==  The /lucky.php page has a button that appears to be disabled. Try to enable the button, and then click it to get the flag.
##### Hint
###### The button does not always give the flag from the first click, so try to make it easy to click it many times until you get the flag.

Solution :  
1) turn on openvpn and connect to HTb , then search http://94.237.55.234:47257/lucky.php
2) youll see ![[Screenshot From 2025-04-05 18-19-29.png]]
3) but its not clickable, Now go to inspect page , youll see
`<button class="btn block-cube block-cube-hover" id="submit" type="submit" formmethod="post" name="getflag" value="true" disabled="">`  , you need to remove this  ==disabled=""== to make that button clickable. 

4) in inspect> elements> right click > edit as html > remove ==disabled=""== and the code will look like this >     `<button class="btn block-cube block-cube-hover" id="submit" type="submit" formmethod="post" name="getflag" value="true">`    >then click out of editable HTML box and the page button become clickable .
5) click the button, nothing happened.
6) remove ==disabled=""== again from the code  using inspect and click the button again, do this multiple times till flag comes up , like this:![[Screenshot From 2025-04-05 18-28-09.png]]

submit this flag : HTB{d154bl3d_bu770n5_w0n7_570p_m3}

---

-  ==Q2)== The /admin.php page uses a cookie that has been encoded multiple times. Try to decode the cookie until you get a value with 31-characters. Submit the value as the answer.
#####  Hint
###### For the first value try multiple encoders until you get a clear text value.

solution : 
1) turn on openvpn and connect to HTb , then search http://94.237.55.234:47257/admin.php
2) youll see a login page.![[Screenshot From 2025-04-05 18-37-38.png]]
3) send a login request > capture it using burp suite > in burp suite review the request >  you'll find a cookie being used :  Cookie: PHPSESSID=bsfrplsh8qd2jga27kvj3hrqdf; cookie=4d325268597a6b7a596a686a5a4449314d4746684f474d7859544d325a6d5a6d597a63355954453359513d3d,   
4) from this take this cookie :     cookie=4d325268597a6b7a596a686a5a4449314d4746684f474d7859544d325a6d5a6d597a63355954453359513d3d
5) 4d325268597a6b7a596a686a5a4449314d4746684f474d7859544d325a6d5a6d597a63355954453359513d3d    put this  in burp decoder
6) ![[Screenshot From 2025-04-05 18-42-25.png]] Decode with ascii hex > Decode with base 64 > 3dac93b8cd250aa8c1a36fffc79a17a 
7) submit 3dac93b8cd250aa8c1a36fffc79a17a and solved this.

---

- ==Q3)== Once you decode the cookie, you will notice that it is only 31 characters long, which appears to be an md5 hash missing its last character. So, try to fuzz the last character of the decoded md5 cookie with all alpha-numeric characters, while encoding each request with the encoding methods you identified above. (You may use the "alphanum-case.txt" wordlist from Seclist for the payload)
#####   Hint
###### With payload processing in Burp Intruder, first add the decoded cookie as a prefix to the payload, then encode the entire payload with the same encoding methods you identified earlier (in reverse order). The final payload should be 88 characters long, similar to the one from the previous question.

solution:
1) this is continuation of Q2 , now the encoding method we identified was aschii hex > base 64
2) find the "alphanum-case.txt" wordlist in /usr/share/seclists/Fuzzing/alphanum-case.txt
cookie=3dac93b8cd250aa8c1a36fffc79a17a in intruder we need to add a last character at this using a word list, then md5 hash that , after that base64 whole thing and above it aschii hexx encode whole thing

==To perform this attack using Burp Intruder, follow these steps:==

1. **Capture the Request:**
   - Open Burp Suite and navigate to the target site.
   - Access `/admin.php` to capture the request in Burp's Proxy.

2. **Send to Intruder:**
   - Right-click the captured request and select **Send to Intruder**.

3. **Configure Positions:**
   - In the **Positions** tab, clear all default payload positions.
   - Highlight the cookie value and set it as the payload position by clicking **Add §** (e.g., `cookie=§value§;`).

4. **Set Payload Type:**
   - Go to the **Payloads** tab.
   - Under **Payload Options**, load the `alphanum-case.txt` wordlist from SecLists.

5. **Payload Processing:**
   - In the **Payload Processing** section, add the following rules in **exact order**:
     1. **Add Prefix**: Enter the prefix `3dac93b8cd250aa8c1a36fffc79a17a`.
     2. **Base64-encode**: Encode the entire string (prefix + payload).
     3. **Encode as... Hex**: Convert each character of the Base64 string to its two-digit hex representation.

6. **Start the Attack:**
   - Launch the attack by clicking **Start Attack**.
   - Burp will generate payloads by appending each alphanumeric character to the prefix, Base64 encoding, then hex encoding.

7. **Identify the Successful Payload:**
   - Look for a response with a significantly larger size (~1,900 bytes). This response contains the flag.
![[Screenshot From 2025-04-05 19-28-04.png]]
![[Screenshot From 2025-04-05 19-27-41.png]]

**Summary:**  
Burp Intruder automates fuzzing the last MD5 character by applying payload processing rules to replicate the cookie encoding steps (prefix + payload → Base64 → Hex). The correct payload triggers a distinct response containing the flag.


so after the intruder attack finished ,  we found a request with larger size of "response recived" the size was 1615.  and in the response we found the flag
![[Screenshot From 2025-04-05 19-21-23.png]]
![[Screenshot From 2025-04-05 19-23-01.png]]
the flag : HTB{burp_1n7rud3r_n1nj4!}

---

-  ==Q4)==   You are using the 'auxiliary/scanner/http/coldfusion_locale_traversal' tool within Metasploit, but it is not working properly for you. You decide to capture the request sent by Metasploit so you can manually verify it and repeat it. Once you capture the request, what is the 'XXXXX' directory being called in '/XXXXX/administrator/..'? 
#####   Hint
###### You may set any website as your RHOST.

Solution : 

1) search metasploit and open it , once it turns on .
2) ![[Screenshot From 2025-04-06 11-34-38.png]]
you'll see this,  msf6 >
3) now turn on burpsuite , on the side.  Make sure its running and configured to listen on `127.0.0.1:8080`  , so that your burp can intercept the metasploit requests when running on your local machine, since we will need it in this lab.  ![[Screenshot From 2025-04-06 11-36-54.png]]
4) now go back to metaspoit  and input these commands ,

```

Metasploit Documentation: https://docs.metasploit.com/

msf6 > 
msf6 > use auxiliary/scanner/http/coldfusion_locale_traversal

msf6 auxiliary(scanner/http/coldfusion_locale_traversal) > 
msf6 auxiliary(scanner/http/coldfusion_locale_traversal) > set RHOST google.com
msf6 auxiliary(scanner/http/coldfusion_locale_traversal) > set RPORT 80
msf6 auxiliary(scanner/http/coldfusion_locale_traversal) > set PROXIES HTTP:127.0.0.1:8080
```
after running these commands , go to burpsuite and turn interceptor on
