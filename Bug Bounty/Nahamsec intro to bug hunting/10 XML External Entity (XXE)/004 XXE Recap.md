
If an XML parser is vulnerable to XXE, an attacker can define an external entity that points to a URL—forcing the server to make an HTTP request. By targeting internal network endpoints or services with that URL, ==the XXE can effectively be escalated to an SSRF attack==.

---
# Example Scenario:

1. **XXE for File Disclosure:**
    
    An application processes XML files without proper safeguards. An attacker submits:
    
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE data [
      <!ENTITY file SYSTEM "file:///etc/passwd">
    ]>
    <data>
      <info>&file;</info>
    </data>
    ```
    
    _What happens:_  
    The XML parser reads the `/etc/passwd` file and includes its contents in the response, disclosing sensitive information.
    
2. **Escalation to SSRF:**
    
    Instead of reading a file, the attacker changes the external entity to point to an internal service:
    
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE data [
      <!ENTITY ext SYSTEM "http://localhost:8080/admin">
    ]>
    <data>
      <info>&ext;</info>
    </data>
    ```
    
    _What happens:_  
    The XML parser now makes an HTTP request to `http://localhost:8080/admin` (an internal endpoint). This forces the server to send a request to a service that is normally not reachable from the outside, effectively turning the XXE into an SSRF attack.
    

---

In simple terms, by changing the entity from reading a file (XXE) to fetching a URL, you can force the server to interact with internal systems—escalating an XXE into an SSRF.

---

# Transcript :-

1
00:00:00,060 --> 00:00:06,180
So that was everything from XXE is still very, very common, it's not always limited to a application

2
00:00:06,180 --> 00:00:08,250
that allows you to just upload XML.

3
00:00:08,370 --> 00:00:16,190
You can actually find XML in a lot of other applications like documents, presentations, spreadsheets.

4
00:00:16,200 --> 00:00:21,010
Those are all zip files that have been packed and they also have XML files within them.

5
00:00:21,030 --> 00:00:26,970
So anywhere you see that allows you to upload some documentation or integration, you want to make sure

6
00:00:26,970 --> 00:00:29,510
that you put your XXE payload in there as well.

7
00:00:29,910 --> 00:00:33,060
We'll cover more of this in our lab where it comes out to document files.

8
00:00:33,330 --> 00:00:36,210
But I want to make sure I echo that is still very common.

9
00:00:36,360 --> 00:00:41,760
And because it's a server side vulnerability that allows you to either fetch local files or actually

10
00:00:41,760 --> 00:00:47,850
perform an SSRF, it's a very, very valuable and it could become a critical or high paid bug that can

11
00:00:47,850 --> 00:00:50,910
get you a lot of boundy depending on how you exploit it.

12
00:00:50,970 --> 00:00:54,090
But also don't limit yourself to looking for a full response XXE,

13
00:00:54,090 --> 00:00:57,420
 blind XXE  are always there as well.

14
00:00:57,610 --> 00:01:01,680
But what you want to make sure is you want to take it step by step, make sure you get the first step

15
00:01:01,680 --> 00:01:02,180
to work.

16
00:01:02,190 --> 00:01:06,450
As always, the first step is to make sure you can actually use a system called to hit your own server

17
00:01:06,450 --> 00:01:09,360
or your burp collaborator and make sure that connection is made.

18
00:01:09,570 --> 00:01:13,860
If that connection is made, depending on what the service is given back to you when you open your XML 

19
00:01:13,860 --> 00:01:18,660
or document, then you want to take the next steps and figure out if it's blind for full response and if

20
00:01:18,660 --> 00:01:22,530
it is blind how to approach it and how to send data back and forth.

21
00:01:22,800 --> 00:01:25,620
So always think that they're very, very common.

22
00:01:25,620 --> 00:01:31,260
And I highly recommend looking for any places that allows you to import your data in an XML format

23
00:01:31,290 --> 00:01:31,960
when it comes out.

24
00:01:31,960 --> 00:01:33,030
These vulnerability types.