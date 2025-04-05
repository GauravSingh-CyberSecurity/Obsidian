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
3) send a login request > capture it using burp suite > in burp suite review the request >  you'll find a cookie 
