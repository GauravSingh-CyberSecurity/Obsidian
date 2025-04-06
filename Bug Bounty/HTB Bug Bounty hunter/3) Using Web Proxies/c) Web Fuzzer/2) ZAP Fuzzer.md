
---

ZAP's Fuzzer is called (`ZAP Fuzzer`). It can be very powerful for fuzzing various web end-points, though it is missing some of the features provided by Burp Intruder. ZAP Fuzzer, however, does not throttle the fuzzing speed, which makes it much more useful than Burp's free Intruder.

In this section, we will try to replicate what we did in the previous section using ZAP Fuzzer to have an "apples to apples" comparison and decide which one we like best.

---

## Fuzz

To start our fuzzing, we will visit the URL from the exercise at the end of this section to capture a sample request. As we will be fuzzing for directories, let's visit `<http://SERVER_IP:PORT/test/>` to place our fuzzing location on `test` later on. Once we locate our request in the proxy history, we will right-click on it and select (`Attack>Fuzz`), which will open the `Fuzzer` window:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer.jpg)

The main options we need to configure for our Fuzzer attack are:

- Fuzz Location
- Payloads
- Processors
- Options

Let's try to configure them for our web directory fuzzing attack.

---

## Locations

The `Fuzz Location` is very similar to `Intruder Payload Position`, where our payloads will be placed. To place our location on a certain word, we can select it and click on the `Add` button on the right pane. So, let's select `test` and click on `Add`:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_add.jpg)

As we can see, this placed a `green` marker on our selected location and opened the `Payloads` window for us to configure our attack payloads.

---

## Payloads

The attack payloads in ZAP's Fuzzer are similar in concept to Intruder's Payloads, though they are not as advanced as Intruder's. We can click on the `Add` button to add our payloads and select from 8 different payload types. The following are some of them:

- `File`: This allows us to select a payload wordlist from a file.
- `File Fuzzers`: This allows us to select wordlists from built-in databases of wordlists.
- `Numberzz`: Generates sequences of numbers with custom increments.

One of the advantages of ZAP Fuzzer is having built-in wordlists we can choose from so that we do not have to provide our own wordlist. More databases can be installed from the ZAP Marketplace, as we will see in a later section. So, we can select `File Fuzzers` as the `Type`, and then we will select the first wordlist from `dirbuster`:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_add_payload.jpg)

Once we click the `Add` button, our payload wordlist will get added, and we can examine it with the `Modify` button.

---

## Processors

We may also want to perform some processing on each word in our payload wordlist. The following are some of the payload processors we can use:

- Base64 Decode/Encode
- MD5 Hash
- Postfix String
- Prefix String
- SHA-1/256/512 Hash
- URL Decode/Encode
- Script

As we can see, we have a variety of encoders and hashing algorithms to select from. We can also add a custom string before the payload with `Prefix String` or a custom string with `Postfix String`. Finally, the `Script` type allows us to select a custom script that we built and run on every payload before using it in the attack.

We will select the `URL Encode` processor for our exercise to ensure that our payload gets properly encoded and avoid server errors if our payload contains any special characters. We can click on the `Generate Preview` button to preview how our final payload will look in the request:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_add_processor.jpg)

Once that's done, we can click on `Add` to add the processor and click on `Ok` in the processors and payloads windows to close them.

---

## Options

Finally, we can set a few options for our fuzzers, similar to what we did with Burp Intruder. For example, we can set the `Concurrent threads per scan` to `20`, so our scan runs very quickly:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_options.jpg)

The number of threads we set may be limited by how much computer processing power we want to use or how many connections the server allows us to establish.

We may also choose to run through the payloads `Depth first`, which would attempt all words from the wordlist on a single payload position before moving to the next (e.g., try all passwords for a single user before brute-forcing the following user). We could also use `Breadth first`, which would run every word from the wordlist on all payload positions before moving to the next word (e.g., attempt every password for all users before moving to the following password).

---

## Start

With all of our options configured, we can finally click on the `Start Fuzzer` button to start our attack. Once our attack is started, we can sort the results by the `Response` code, as we are only interested in responses with code `200`:

![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_attack.jpg)

As we can see, we got one hit with code `200` with the `skills` payload, meaning that the `/skills/` directory exists on the server and is accessible. We can click on the request in the results window to view its details: ![payload processing](https://academy.hackthebox.com/storage/modules/110/zap_fuzzer_dir.jpg)

We can see from the response that this page is indeed accessible by us. There are other fields that may indicate a successful hit depending on the attack scenario, like `Size Resp. Body` which may indicate that we got a different page if its size was different than other responses, or `RTT` for attacks like `time-based SQL injections`, which are detected by a time delay in the server response.


---

#### Questions

Answer the question(s) below to complete this Section and earn cubes!

Target(s): 94.237.51.14:52260   


+ Q)   The directory we found above sets the cookie to the md5 hash of the username, as we can see the md5 cookie in the request for the (guest) user. Visit '/skills/' to get a request with a cookie, then try to use ZAP Fuzzer to fuzz the cookie for different md5 hashed usernames to get the flag. Use the "top-usernames-shortlist.txt" wordlist from Seclists.

Hint: Use the 'MD5 Hash' processor and look for the page with a different content-length.


Solution :

# HTB Using Web Proxies — ZAP Fuzzer: **Exploring Alternatives to ZAP Fuzzer: When Fuzzing with ZAP Falls Short**


![](https://miro.medium.com/v2/resize:fit:875/1*_RkA5ZcBhVHA3qMPHgKKLQ.png)

ZAP Fuzzer is a fantastic tool for fuzz testing, but there are times when it crashes during the process. This can be frustrating, especially when you’re relying on it for critical tasks. So, what do you do if ZAP Fuzzer isn’t meeting your expectations?

Although the goal here is to learn specifically about ZAP Fuzzer, it’s important to step outside the box and explore other options. By doing this, you’ll not only complete the task but also gain valuable alternatives to ZAP for fuzzing.

In this post, we’ll explore some effective fuzzing tools you can use when ZAP Fuzzer isn’t delivering the results you’re looking for.

**Resources:** Here is the resources need to complete this task.

- Burp Suite(Intruder)
- [SecList](https://github.com/danielmiessler/SecLists)(top-usernames-shortlist.txt)
- hash-identifier

![](https://miro.medium.com/v2/resize:fit:875/1*SUhkjIVHA2AxqWcUtWAkCQ.png)

Resources to start the Task for this task we only need the IP

Question: The directory we found above sets the cookie to the md5 hash of the username, as we can see the md5 cookie in the request for the (guest) user. Visit ‘/skills/’ to get a request with a cookie, then try to use ZAP Fuzzer to fuzz the cookie for different md5 hashed usernames to get the flag. Use the “top-usernames-shortlist.txt” wordlist from Seclists.

**Answers:**

**Step 1:** We start by looking the website and see which part the website should we start fuzzing.

**Link:** [http://94.237.63.1:52690/skills/](http://94.237.63.1:52690/skills/)(IP can change)

![](https://miro.medium.com/v2/resize:fit:875/1*ZE5hGOQu6yaNmWKMMxtLww.png)

We can see that its a simple website with nothing in the website.

**Step 2: N**ow we can just look through burp suite proxy and see if we can find something.

![](https://miro.medium.com/v2/resize:fit:875/1*a9EIySS8J4cf2f6oxdFv1g.png)

We can see that there is cookie stored in this page, so now we can look through options to found our flag, Task asks us to use the **top-usernames-shortlist.txt** for fuzzing but in this file all of the users are in string and plaintext so we can’t use the usernames.

**Step 3:** We need to figure out what kind of hash is our cookie so we can change our usernames to that hash and for that to happen we use hash-identifier

hash-identifier 084e0343a0486ff05530df6c705c8bb4

![](https://miro.medium.com/v2/resize:fit:783/1*-955wbXsNdfaIiniy_XrzQ.png)

For alternative we can just ask Chatgpt it will give us the which hash it is :))

Now we need to change the users to MD5 and for that don’t make your life miserable just ask ChatGPT to do it for you.

**Step 4:** We are going to use hashes that we have in intruder and see what results we get.

![](https://miro.medium.com/v2/resize:fit:783/1*DyDpasRAsaqR-x3ZnyQyrQ.png)

After choosing Intruder we are going to paste the MD5 hashes hashes inside payload
63a9f0ea7bb98050796b649e85481845
21232f297a57a5a743894a0e4a801fc3
098f6bcd4621d373cade4e832627b4f6
084e0343a0486ff05530df6c705c8bb4
caf9b6b99962bf5c2264824231d7a40c
b09c600fddc573f117449b3723f23d64
81c3b080dad537de7e10e0987a4bf52e
==ee11cbb19052e40b07aac0ca060c23ee== (this Hash value in cookie will give the Flag)
200ceb26807d6bf99fd6f4f0d1ca54d4
a189c633d9995e11bf8607170ec9a4b8
ff104b2dfab9fe8c0676587292a636d3
72ab8af56bddab33b269c5964b26620a
768747907b90c39ab6f16fcb3320897a
640c8a5376aa12fa15cf02130ce239a6
23b0749d7d3a9ee3c0b024a86fe3e1c2
63623900c8bbf21c706c45dcb7a2c083


![](https://miro.medium.com/v2/resize:fit:874/1*pZlmPxQ5b77CXTv1Fef6oQ.png)

After that we are going to choose the positions that we are going to fuzz and that will be the cookies.

![](https://miro.medium.com/v2/resize:fit:875/1*hnu1yWMgH_3JoXan8SbWXw.png)

and at last we are going to start the attack.

**Step 5:** After the scan is finished we can look through every response to and we can find our flag there.

![](https://miro.medium.com/v2/resize:fit:875/1*_RkA5ZcBhVHA3qMPHgKKLQ.png)

![](https://miro.medium.com/v2/resize:fit:875/1*-wIPxdrlM9e4-BSZHhAAcQ.png)

this is the solution SS, with the Flag![[Screenshot From 2025-04-06 14-18-15.png]]
Good Luck!





---

My Analysis :

```
GET /skills/ HTTP/1.1
Host: 94.237.51.14:52260
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
DNT: 1
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
Priority: u=0, i
Referer: http://94.237.51.14:52260/skills


```

```
HTTP/1.1 200 OK
Date: Thu, 03 Apr 2025 07:16:19 GMT
Server: Apache/2.4.41 (Ubuntu)
Set-Cookie: cookie=084e0343a0486ff05530df6c705c8bb4
Vary: Accept-Encoding
Content-Length: 246
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8


<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Welcome</title>

</head>

<body style="background-color: #141d2b; font-family: sans-serif; color: white;">
    <center>
                    </center>
</body>

</html>
```

use : `hash-identifier 084e0343a0486ff05530df6c705c8bb4`   to find the hash format. 


Note: for the cookie 084e0343a0486ff05530df6c705c8bb4  use hashcat to crack this, and youll find its MD5 hashing and string is : 'guest'
in hashcat use this "top-usernames-shortlist.txt" wordlist, as shown below we were able to find it at  /usr/share/seclists/Usernames/top-usernames-shortlist.txt
```
C:\home\kali> sudo su
[sudo] password for kali: 
┌──(root㉿RandomHost19348)-[/home/kali]
└─# find /* -name top-usernames-shortlist.txt
find: ‘/run/user/1000/doc’: Permission denied
find: ‘/run/user/1000/gvfs’: Permission denied
find: ‘/tmp/.mount_ObsidifS2488’: Permission denied
/usr/share/seclists/Usernames/top-usernames-shortlist.txt
                                            
```

```
C:\home\kali> sudo cat /usr/share/seclists/Usernames/top-usernames-shortlist.txt 
 
[sudo] password for kali: 
root
admin
test
guest
info
adm
mysql
user
administrator
oracle
ftp
pi
puppet
ansible
ec2-user
vagrant
azureuser
C:\home\kali> 

```

| **Username**  | **MD5 Hash**                       |
| ------------- | ---------------------------------- |
| root          | `63a9f0ea7bb98050796b649e85481845` |
| admin         | `21232f297a57a5a743894a0e4a801fc3` |
| test          | `098f6bcd4621d373cade4e832627b4f6` |
| guest         | `084e0343a0486ff05530df6c705c8bb4` |
| info          | `4e971d6a0d06a4edb7a68d4086e5d4f5` |
| adm           | `490ad9d8d8b104f2d1ec20f3bd8b0a3c` |
| mysql         | `81c3b080dad537de7e10c93f05ef1b7d` |
| user          | `ee11cbb19052e40b07aac0ca060c23ee` |
| administrator | `43bea4d7f9b3d9a240b871d4d8dd7853` |
| oracle        | `627c6075b5bf38f0a8145e6e2f3d4a2a` |
| ftp           | `7215ee9c7d9dc229d2921a40e899ec5f` |
| pi            | `a0dc6b11f2a3c60e3e3455f3a8a1f7c2` |
| puppet        | `8e7b9e8d5e5f5b5f5d5e5f5b5d5e5f5b` |
| ansible       | `5d5e5f5b5d5e5f5b5d5e5f5b5d5e5f5b` |
| ec2-user      | `f5e5d5c5b5a59585f5e5d5c5b5a59585` |
| vagrant       | `5a5f5b5d5e5f5b5d5e5f5b5d5e5f5b5d` |
| azureuser     | `5d5e5f5b5d5e5f5b5d5e5f5b5d5e5f5b` |
```
63a9f0ea7bb98050796b649e85481845
21232f297a57a5a743894a0e4a801fc3
098f6bcd4621d373cade4e832627b4f6
084e0343a0486ff05530df6c705c8bb4
caf9b6b99962bf5c2264824231d7a40c
b09c600fddc573f117449b3723f23d64
81c3b080dad537de7e10e0987a4bf52e
ee11cbb19052e40b07aac0ca060c23ee
200ceb26807d6bf99fd6f4f0d1ca54d4
a189c633d9995e11bf8607170ec9a4b8
ff104b2dfab9fe8c0676587292a636d3
72ab8af56bddab33b269c5964b26620a
768747907b90c39ab6f16fcb3320897a
640c8a5376aa12fa15cf02130ce239a6
23b0749d7d3a9ee3c0b024a86fe3e1c2
63623900c8bbf21c706c45dcb7a2c083

```


Now lets find out the encoding/hashing syntax of the cookie 084e0343a0486ff05530df6c705c8bb4 , so i put it in decoder and try decode as :

![[Screenshot From 2025-04-06 12-21-22.png]]
084e0343a0486ff05530df6c705c8bb4  (decode as ASCII HEX) > ` NC HoðU0ßlp\´ `  
(i am not able to decode this further to get an actual string)


so i take the string 'guest' as i found it using hachcat , and try encode it to get the cookie exact format 084e0343a0486ff05530df6c705c8bb4  : (so i can determine the encoding/hashing syntax/format here)

guest (Hash MD5) >  ` NC HoðU0ßlp\´ `  (encode as ASCII HEX) >  084e0343a0486ff05530df6c705c8bb4 (we got the exact cookie)

therefore the syntax is :  ==string > MD5 Hash > ASCII HEX encoding > cookie=== 


now set this encoding/hashing syntax  in burp intruder 
'payload processing'  , on the cookie parameter(payload) while using this =='/usr/share/seclists/Usernames/top-usernames-shortlist.txt'==  wordlist for trying to fuzz the cookie parameter as asked in the question.

1) add cookie parameter as payload  (cookie=$ $ )
2) select attack: sniper attack , payload type: simple list
3) load '/usr/share/seclists/Usernames/top-usernames-shortlist.txt'
4) in payload processing set this flow ==string > MD5 Hash > ASCII HEX encoding > cookie=== 

![[Screenshot From 2025-04-06 12-32-59.png]]
![[Screenshot From 2025-04-06 12-33-21.png]]

----

