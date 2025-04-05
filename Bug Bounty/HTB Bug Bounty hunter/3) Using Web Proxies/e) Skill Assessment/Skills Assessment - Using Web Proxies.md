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