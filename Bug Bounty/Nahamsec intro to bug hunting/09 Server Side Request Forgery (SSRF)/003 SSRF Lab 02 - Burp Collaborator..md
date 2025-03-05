Analysis of SSRF lab:-  ( http://ssrf2.naham.sec:8081/ )

![[Screenshot From 2025-03-05 12-09-19.png]]
this example is the same thing as ssrf lab1, instead of giving us a source code
for the Web page, it's actually taking a screenshot( instead of giving source code like lab1).



==Now we use burp collaborator:== 
- Go to **Burp Suite** → **Burp Collaborator** tab.
-  set Payloads to generate:  (as per requirement, by default 1)
- Click on **"Copy to clipboard"**.  To copy the payload
- Burp will provide a **unique URL** that can be used to capture interactions from external sources.
- paste it in the above webpages input( field to be tested for ssrf)
- Go to Collaborator
- click on " Poll Now"  and see an http req was recived. and ip address( 49.248.248.54:46926 ) in the request is not our own ip address, hence it is servers ip .
- ![[Screenshot From 2025-03-05 12-27-55.png]]
- Therefore SSRF can be present





---



1
00:00:00,090 --> 00:00:04,170
Let's look at a second example, this example is the same thing, instead of giving us a source code

2
00:00:04,170 --> 00:00:06,390
for the Web page, it's actually taking a screenshot.

3
00:00:06,900 --> 00:00:09,690
In this case, we're going to give it again, Google dot com.

4
00:00:10,800 --> 00:00:13,440
It's going to come back and say, hey, here's your screenshot.

5
00:00:13,890 --> 00:00:14,910
This is what it looks like.

6
00:00:14,920 --> 00:00:16,380
We see this opening up Google.

7
00:00:16,710 --> 00:00:20,670
But this time in the first example, I used my personal server.

8
00:00:20,940 --> 00:00:21,420
I had it.

9
00:00:21,420 --> 00:00:23,610
Give me the request for this case.

10
00:00:23,610 --> 00:00:25,890
We're going to use burb suite again.

11
00:00:25,890 --> 00:00:28,440
If you want to do this, you will need burb speed pro.

12
00:00:28,890 --> 00:00:35,430
You can actually use a collaborator to see if there is any request being made server side or if it's

13
00:00:35,430 --> 00:00:37,950
being made on the client side.

14
00:00:38,040 --> 00:00:40,560
We're going to do here is we're going to look for our burb collaborative client.

15
00:00:41,070 --> 00:00:46,660
It's going to give us a real we go copy clipboard that's going to say you are.

16
00:00:46,660 --> 00:00:51,360
Oh, this is very helpful if you don't want to open up your own server just to verify if a request is

17
00:00:51,360 --> 00:00:58,170
being created by the server or if it's being by your browser can use burb suite, it gives you out as

18
00:00:58,170 --> 00:01:00,210
soon as you hit, go and you click pull.

19
00:01:00,240 --> 00:01:05,670
Now, if there is a request made, it's going to come back and say, hey, here's the request that was

20
00:01:05,670 --> 00:01:06,390
made on my end.

21
00:01:06,640 --> 00:01:09,960
So one more time I'm going to say HTP, I'm going to do this.

22
00:01:10,360 --> 00:01:11,610
So screenshots ready.

23
00:01:12,540 --> 00:01:15,510
This matches the you are all we had to do pull now.

24
00:01:15,990 --> 00:01:20,260
And we can see there was a request that was made by HTP from the IP address.

25
00:01:20,310 --> 00:01:23,130
This is the servers IP address, not my personal IP address.

26
00:01:23,130 --> 00:01:26,490
So this is the machine where the application is being hosted on.

27
00:01:26,760 --> 00:01:27,870
That's the IP for it.

28
00:01:28,140 --> 00:01:31,110
That indicates that it's making requests on the server side.

29
00:01:31,380 --> 00:01:34,050
So there's a chance of SRF depending on what we do.

30
00:01:34,440 --> 00:01:39,170
So we can do here is we can type in our usual command.

31
00:01:39,180 --> 00:01:42,650
We can go in here and say, hey, I want you to excuse me, not our commander.

32
00:01:42,660 --> 00:01:45,900
Want to type in our usual guesses.

33
00:01:45,900 --> 00:01:47,550
We always start with a local follow.

34
00:01:47,550 --> 00:01:50,550
You can do file etsi password, give us a try.

35
00:01:51,840 --> 00:01:58,200
And as expected, because there are no defenses made against this SRF, the application comes back and

36
00:01:58,200 --> 00:02:03,690
says, hey, here is the content of the file that you want to look for with the file wrapper and it

37
00:02:03,690 --> 00:02:04,710
puts on a screenshot.

38
00:02:05,270 --> 00:02:08,070
Also, do this again with the amount of data you are.

39
00:02:08,130 --> 00:02:11,940
So again, this comes to this comes by default by most cloud providers.

40
00:02:12,480 --> 00:02:16,410
NWS is your Google and Digital Ocean all have it.

41
00:02:16,680 --> 00:02:23,280
The you are the IP address is always the same, but the naming conventions of the API endpoints are

42
00:02:23,280 --> 00:02:23,730
different.

43
00:02:23,730 --> 00:02:25,680
So you may have to look out for each one.

44
00:02:25,860 --> 00:02:32,490
You have to see where this is hosted and then send this look at the documentation and follow it and

45
00:02:32,490 --> 00:02:34,650
look for this amount of data for digital ocean.

46
00:02:34,650 --> 00:02:36,950
I know that they use metadata V1.

47
00:02:37,320 --> 00:02:38,280
We're going to give it a go.

48
00:02:38,610 --> 00:02:40,860
Look at our screenshot and it comes back.

49
00:02:41,070 --> 00:02:45,720
And if I were to go to this IP address right now, it wouldn't work because this is IP address that

50
00:02:46,050 --> 00:02:51,600
is used in a private network and it's not accessible unless you have it within your network as well.

51
00:02:51,990 --> 00:02:58,020
So we prove that there is some sort of local authority that can read files that are hosted locally on

52
00:02:58,020 --> 00:02:58,650
that machine.

53
00:02:58,950 --> 00:03:00,960
Or we can also look for metadata.

54
00:03:01,170 --> 00:03:07,500
And if there is any other IP addresses like localhost, you can either do HGP localhost or you can do

55
00:03:07,500 --> 00:03:12,630
one two seven zero zero one, which is the same notation for localhost machine.

56
00:03:13,230 --> 00:03:15,810
And if you have access to it, it's going to give us a screenshot.

57
00:03:16,680 --> 00:03:18,660
And as expected, it came back a status.

58
00:03:18,660 --> 00:03:20,850
OK, same as our first example.

59
00:03:21,090 --> 00:03:23,580
This is the result we got gave us the same thing.