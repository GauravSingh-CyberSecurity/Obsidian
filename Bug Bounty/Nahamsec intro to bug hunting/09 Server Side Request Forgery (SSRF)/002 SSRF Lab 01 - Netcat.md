Analysis of SSRF lab:-  ( http://ssrf.naham.sec:8081/ )  


So, for example, what we're seeing is an application that just features the source code for any website, so if you put in Google dot com, it actually fetches it and gives you the source code for the whatever web page.
![[Screenshot From 2025-03-05 09-02-25.png]]




since , for this lab request comes from a remote server, we can found this using netcat or burp.

lets , try these payloads to see if the response is success

http://lochalhost
![[Pasted image 20250305115348.png]]


![[Screenshot From 2025-03-05 11-57-03.png]]


we can use Netcat or Burp-suite to test for SSRF to see if request comes from a remote server,  of your own ip address.

Now, The first thing we want to do is we want to Setup "Netcat" - ( setup guide available in this course's 
[14.] How to Setup Your Lab (Installing and Demos) )
```
$ netcat -h
[v1.10-50]
connect to somewhere:	nc [-options] hostname port[s] [ports] ... 
listen for inbound:	nc -l -p port [-options] [hostname] [port]
options:
	-c shell commands	as `-e'; use /bin/sh to exec [dangerous!!]
	-e filename		program to exec after connect [dangerous!!]
	-b			allow broadcasts
	-g gateway		source-routing hop point[s], up to 8
	-G num			source-routing pointer: 4, 8, 12, ...
	-h			this cruft
	-i secs			delay interval for lines sent, ports scanned
        -k                      set keepalive option on socket
	-l			listen mode, for inbound connects
	-n			numeric-only IP addresses, no DNS
	-o file			hex dump of traffic
	-p port			local port number
	-r			randomize local and remote ports
	-q secs			quit after EOF on stdin and delay of secs
	-s addr			local source address
	-T tos			set Type Of Service
	-t			answer TELNET negotiation
	-u			UDP mode
	-v			verbose [use twice to be more verbose]
	-w secs			timeout for connects and final net reads
	-C			Send CRLF as line-ending
	-z			zero-I/O mode [used for scanning]
port numbers can be individual or ranges: lo-hi [inclusive];
hyphens in port names must be backslash escaped (e.g. 'ftp\-data').
C:\home\kali> netcat -h

```


Then , Turn on netcat by .
netcat command to listen to port 8000

 
```
nc -lvnp 8000
```




for burpsuite 
### **Method 1: Using Burp Suite Proxy Listener (Similar to Netcat -l Mode)**

If you want Burp Suite to listen for incoming connections on a specific port (like Netcat does):

1. **Open Burp Suite** → Go to **Proxy** tab.
2. Click on **Proxy Settings** → Under **Proxy Listeners**, click **Add**.
3. Set **Bind to address** to `All interfaces` or `127.0.0.1` (localhost).
4. Set **Bind to port** to `800` (or any desired port).
5. Ensure **"Support invisible proxying"** is enabled if needed.
6. Click **OK** → Ensure the listener is **turned on**.

This will make Burp Suite listen on **port 800**0, similar to `nc -lvnp 8000`.




---



1
00:00:00,210 --> 00:00:05,330
So, for example, what we're seeing is an application that just features the source code for any website,

2
00:00:05,340 --> 00:00:11,940
so if you put in Google dot com, it actually fetches it and gives you the source code for the whatever

3
00:00:11,940 --> 00:00:12,370
web page.

4
00:00:12,430 --> 00:00:14,670
We've given it before us to make sure there's Matsusaka fear.

5
00:00:14,670 --> 00:00:18,260
The first thing we want to do is we want to spin up a netcat.The first thing we want to do is we want to spin up a net counter.

6
00:00:18,270 --> 00:00:18,930
Can you see?

7
00:00:18,970 --> 00:00:20,720
I'll show you both of Winnicott.

8
00:00:20,730 --> 00:00:25,680
We cover this in our How to set up your own lab section of the course.

9
00:00:25,680 --> 00:00:30,750
But what are we doing with that cat is we're telling it, hey, I want you to listen and open on put

10
00:00:31,050 --> 00:00:31,950
a thousand.

11
00:00:32,730 --> 00:00:37,150
So now that we have a port 8000 open, I know the iPad just for my box.

12
00:00:37,210 --> 00:00:43,410
I'm going to put that in here and I'm going to make it HTP request and I'm going to head Port 8000 because

13
00:00:43,620 --> 00:00:45,180
that's the port we opened up here.

14
00:00:45,420 --> 00:00:49,460
And we want to see what we want to see who is making that request.

15
00:00:49,480 --> 00:00:55,800
Is this being made on the server side or is it being made on the client side to clients?

16
00:00:55,800 --> 00:01:00,900
I being my browser, if my iPad just shows up in the request, that means my browser is doing this and

17
00:01:00,900 --> 00:01:02,040
not the server itself.

18
00:01:03,310 --> 00:01:09,140
As you can see here with the IP just coming back, it's one for two ninety three thousand forty nine.

19
00:01:09,450 --> 00:01:12,120
I know my personal IP address and I know that's not it.

20
00:01:12,420 --> 00:01:15,000
So that's the IP address that belongs to the server.

21
00:01:15,690 --> 00:01:20,610
So what we can do next is we know that the request has been made is from this IP address.

22
00:01:20,880 --> 00:01:22,800
This is not our servers.

23
00:01:23,070 --> 00:01:27,480
So it means there's something in the background, some work that's being done by the server.

24
00:01:27,480 --> 00:01:31,110
It's rendering and fetching data on the server side.

25
00:01:31,260 --> 00:01:33,240
And I want to start messing with it now.

26
00:01:33,240 --> 00:01:40,650
I want to see if we can actually access any local networks or any other sensitive data that could give

27
00:01:40,650 --> 00:01:42,880
us some sort of impact.

28
00:01:42,900 --> 00:01:45,060
So the first thing we can do is we can use a file wrapper.

29
00:01:45,360 --> 00:01:50,400
We can say, hey, news file, give me the ETSI password content.

30
00:01:50,700 --> 00:01:51,580
That was pretty easy.

31
00:01:51,810 --> 00:01:53,160
This case, it came back.

32
00:01:53,190 --> 00:01:58,590
This is still very, very common in bug bounties when it comes back and says, OK, here's the data.

33
00:01:58,590 --> 00:02:01,260
You asked for it and as easily giving it to us.

34
00:02:01,560 --> 00:02:03,780
If that doesn't work, we also look for localhost.

35
00:02:03,780 --> 00:02:09,060
So every machine that's running some sort of a Web server could be accessible within its own machine

36
00:02:09,060 --> 00:02:11,130
and network by going through localhost.

37
00:02:11,460 --> 00:02:15,840
So if you're not familiar with this, I highly recommend looking into it and getting familiar with how

38
00:02:15,840 --> 00:02:17,130
private networks work.

39
00:02:17,130 --> 00:02:22,710
What is a localhost or even going as far as setting up your own localhost with some Apache in Mexico

40
00:02:22,710 --> 00:02:26,370
in the background for this case, we're going to give it localhost that comes back.

41
00:02:26,370 --> 00:02:31,260
It's a status, OK, which means that we're accessing a local private network that wouldn't have been

42
00:02:31,260 --> 00:02:33,650
accessible without this SRF.

43
00:02:34,350 --> 00:02:36,070
Again, we also talked about an SSR.

44
00:02:36,420 --> 00:02:41,010
The most important thing that a lot of hackers go after, especially with bug bounties, is looking

45
00:02:41,010 --> 00:02:42,000
for metadata.

46
00:02:42,420 --> 00:02:50,670
So the first step to do is we want we want to do is we want to go to one six nine to five four one six

47
00:02:50,670 --> 00:02:58,830
nine to five for this as a universal IP address, the most cloud service providers offer that just gives

48
00:02:58,830 --> 00:02:59,730
you some metadata.

49
00:02:59,730 --> 00:03:04,470
In some cases, it might give you keys, it may give you some extra information that you can use as

50
00:03:04,470 --> 00:03:05,420
a part of your privacy.

51
00:03:05,930 --> 00:03:09,060
So in this case, we hit this first URL.

52
00:03:09,510 --> 00:03:11,160
It comes back and says not found.

53
00:03:11,490 --> 00:03:13,740
We're going to try and do metadata V1.

54
00:03:14,520 --> 00:03:21,060
And this comes back and gives us some data so we can actually query for additional information like

55
00:03:21,060 --> 00:03:25,020
the public keys, we can look for the DNS information again is metadata.

56
00:03:25,230 --> 00:03:31,980
In some cases there are keys available where you can actually use them for HWC or whatever the cloud

57
00:03:31,980 --> 00:03:35,640
service instance provider is and you can get additional access.

58
00:03:35,640 --> 00:03:42,770
And it's your privilege to be doing more like Arcy from your SRF.


