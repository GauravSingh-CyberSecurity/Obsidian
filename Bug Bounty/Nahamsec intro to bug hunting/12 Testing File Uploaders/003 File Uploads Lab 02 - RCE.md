Analysis of File uploads lab  :-  ( http://upload.naham.sec:8081/ )
![[Screenshot From 2025-03-11 16-39-19.png]]
But what about other vulnerabilities? I mentioned vulnerabilities like RCE, SSRF, depending on how this application works


So now we're going to do the same thing. We're going to intercept (in Burp Suite) and send out the same file(Linux-Commands_Cheat-Sheet.png). We're going to send it to the Burp repeater by right-clicking and selecting "Send to Repeater." If you're on Windows, it's Control+R, and if you're on Mac, it's Command+R.

This sends the entire request to the repeater, and every time we send this request in, 
I'm going to test this as  "test123." Every time we push "Send," it makes a request for us. If we look  at our website response, we can see that it has successfully done that.
![[Screenshot From 2025-03-11 16-42-12.png]]

But I want to test out for an RCE. If I remember the slides from our RCE chapter, there are a number of ways to get an RCE to work. One of those is to just give it a pipe ( | ). So at the end of that, we can add a pipe, which tells the system to finish whatever last command it's doing and then run the second command  "ls".
We tried that, refreshed, and nothing worked. 
We can see that. 
![[Screenshot From 2025-03-11 16-46-01.png]]

What about if we wanted to test out something like a semicolon? We're going to do the same thing. ![[Screenshot From 2025-03-11 16-46-49.png]]
That doesn't work either. We already covered the pipe and the semicolon.



One of the things we talked about was the concept of an ==inline command==. This means if you're in the middle of the command line while the application is running its own command as an argument of some sort, we want to insert our own command within it. If you're not familiar with this, I highly recommend looking into it and reviewing the slides.

In this case, we're going to give it an inline RCE using `$(command)`. Our command goes in there - `$(ls)` , and we push "Go."

As expected, nothing has worked.

From previous tests, we can see that nothing is really working. It's not giving us an RCE. In this case, we have to test for a blind RCE. I know we haven't covered this previously in our slides. It's almost the same as an RCE; we just have to find a different way to see the output of a command.

This could be done in several ways. The first thing we can try is sending a cURL request. We can say, "Hey, I want you to make a cURL command," and use a Burp Collaborator link. We copy the link and tell it to send the request to our Burp Collaborator, hoping that this command gets executed.

We send this out and hope for a hit. We poll for responses and see that we are getting a request sent to our Burp Collaborator. It comes from a user agent with cURL, which indicates that our command has executed.

To confirm, we can extract content from the website. One way to do this is by adding a subdomain in Burp Collaborator. We'll type in "test123" to confirm that the request is actually coming from the web server we're attacking and not some random IP on the internet.

We still want to make a cURL request, but instead of just sending a regular cURL request, we're also going to attach the results of our command as a DNS record. This means saying, "Hey, I want you to take the output of this command." In this case, we'll use "uname" and tell it to reach whatever the output of this command is as the record under this domain.

We request it, go back, poll for it, and see another HTTP request come in. Looking at the results, it says "Linux," which is likely the result of our "uname" command being attached to the DNS. This is a great technique when dealing with blind RCE.

By default, you should always try these cURL commands and have a server where you can monitor requests. This could be a Burp Collaborator, Netcat listener, or a subdomain you own. Having some way to monitor requests is crucial.

It doesn't have to be "uname." We can also send an "ls" command. We poll again, and another request comes in. Looking at it, it says "uploads," meaning that the uploads folder exists.

We can verify further by trying "ls uploads." Depending on how the application works, this may or may not give an answer due to spacing within the command. We try again, poll, and see a response: "test123.png," which was one of the first files we uploaded to the web server. This confirms that we are successfully executing commands.

Again, it's important to understand how these applications work. You want to test every single user input that has an output. There are many different attack scenarios that can come up. It all comes down to what you're testing for.

RCE, especially blind RCE, is very common, particularly if the application is processing file names—renaming them, moving them, or modifying them in some way. You always want to look for these vulnerabilities.

Again, they are very common, and understanding how to test for them properly is key to security testing.

---

# Transcript :

1
00:00:00,210 --> 00:00:06,150
But what about other vulnerabilities, I mentioned vulnerabilities like our CBS SRF, depending on how

2
00:00:06,150 --> 00:00:07,380
this application works.

3
00:00:07,960 --> 00:00:09,230
So now we're going to do the same thing.

4
00:00:09,240 --> 00:00:15,780
We're going to intercept and we are going to send out the same file we're going to send to repeater

5
00:00:15,780 --> 00:00:18,480
by right clicking and going to send to repeater.

6
00:00:18,720 --> 00:00:23,360
Or if you're on a windows, it's control or if you're UniMac, it's command are.

7
00:00:23,730 --> 00:00:29,040
And this sends the entire request to repeaters and every time we send this request in.

8
00:00:29,040 --> 00:00:34,740
So I'm going to test test one, two or three every time we push send, it makes our request for us.

9
00:00:34,980 --> 00:00:38,760
And if it was at our website, we can see that it successfully has done that.

10
00:00:39,060 --> 00:00:45,090
But I want to test out for an RC, if I remember the slides from our RC chapter, there are a different

11
00:00:45,090 --> 00:00:47,680
number of ways to get an RC to work.

12
00:00:47,790 --> 00:00:49,740
One of those is to just give it a pipe.

13
00:00:50,040 --> 00:00:54,990
So at the end of that we can go, that's just a pipe for hey, finish whatever last command you're doing

14
00:00:55,260 --> 00:00:56,850
and then run my second command.

15
00:00:57,400 --> 00:00:59,340
We gave that to it with fresh.

16
00:00:59,640 --> 00:01:00,450
Nothing worked.

17
00:01:00,450 --> 00:01:00,960
We can see that.

18
00:01:01,290 --> 00:01:01,800
Is there.

19
00:01:02,310 --> 00:01:08,490
Well, what about if we wanted to test out something like a semicolon, we're going to do the same thing

20
00:01:08,790 --> 00:01:12,780
else that doesn't work on other things that we talked about.

21
00:01:12,800 --> 00:01:13,950
We recovered the pipe.

22
00:01:13,950 --> 00:01:15,720
We already covered the semicolon.

23
00:01:16,090 --> 00:01:19,740
One of the things that we talked about was the concept of an inline command.

24
00:01:19,740 --> 00:01:24,480
So that means if you're in between somewhere in the middle of the command line, so the application

25
00:01:24,480 --> 00:01:25,650
is running its own command.

26
00:01:25,650 --> 00:01:27,120
It's an argument of some sort.

27
00:01:27,270 --> 00:01:29,580
We want to insert our own command within it.

28
00:01:29,790 --> 00:01:33,780
So if you're not familiar with this, I highly recommend looking into it and going back over the slides.

29
00:01:34,110 --> 00:01:39,600
But in this case, we're going to give it an inline RC, which goes into dollars, same parentheses.

30
00:01:39,600 --> 00:01:42,300
Our command goes in here and we push go.

31
00:01:42,870 --> 00:01:45,690
And as we expected it, nothing has worked.

32
00:01:46,980 --> 00:01:50,940
The previous test that I've done on this, but we can see that nothing is really working.

33
00:01:51,180 --> 00:01:52,420
It's not giving us an RC.

34
00:01:52,440 --> 00:01:56,070
So in this case, we have to test for a blind RC.

35
00:01:56,430 --> 00:01:58,950
I know we haven't covered this previously in our slides.

36
00:01:59,100 --> 00:02:01,500
It's almost the same as just having an RC.

37
00:02:01,500 --> 00:02:04,620
We just have to find a different way to see the output of a command.

38
00:02:05,010 --> 00:02:06,250
This could be a number of different ways.

39
00:02:06,270 --> 00:02:11,310
The first thing we can try and do is we can try and send the Kearl so we can say, hey, I want you

40
00:02:11,310 --> 00:02:18,720
to make a call command and I want you to oops, I want you to use this burb collaborators with a collaborator

41
00:02:18,720 --> 00:02:19,020
here.

42
00:02:20,550 --> 00:02:21,840
We're going to copy the link.

43
00:02:22,200 --> 00:02:30,060
We're going to say, hey, I want you to come to this burb collaborator and I want you to upload this

44
00:02:30,060 --> 00:02:30,420
file.

45
00:02:30,420 --> 00:02:33,660
But we're hoping that this command gets executed.

46
00:02:33,780 --> 00:02:35,700
So we're going to send this out right here.

47
00:02:35,700 --> 00:02:37,290
We're going to hope that we get a hit.

48
00:02:37,710 --> 00:02:42,660
We're going to pull now and we can see that, OK, we're making we're getting a request sent to our

49
00:02:42,900 --> 00:02:43,950
burb collaborator.

50
00:02:44,760 --> 00:02:50,550
And it's coming from a user agent with Kerl, which indicates it is what we are looking for.

51
00:02:50,580 --> 00:02:54,270
So again, we're using Kerl that matches what we want to confirm.

52
00:02:54,270 --> 00:02:57,370
We can actually extract content from this website.

53
00:02:57,540 --> 00:03:00,240
So what we're going to do in this case is a few things we can do.

54
00:03:00,570 --> 00:03:02,760
The first thing is we can add a subdomain here.

55
00:03:03,030 --> 00:03:03,570
Collaborators.

56
00:03:03,570 --> 00:03:04,740
Great allows you to do that.

57
00:03:05,140 --> 00:03:06,830
We're going to type in test one, two, three.

58
00:03:07,080 --> 00:03:12,060
I just want to confirm that this request is actually coming from the Web server that I'm attacking and

59
00:03:12,060 --> 00:03:17,310
not some just random IP on the Internet that's randomly scanning our IP space or whatever it is people

60
00:03:17,310 --> 00:03:17,790
do that.

61
00:03:17,820 --> 00:03:20,360
We want to confirm that this request is legit.

62
00:03:20,370 --> 00:03:23,730
So what we want to do here is we still want to make a couple request.

63
00:03:24,060 --> 00:03:28,500
But instead of just sending a regular Kearl request, we're also going to attach the results of our

64
00:03:28,500 --> 00:03:30,090
command as a DNS record.

65
00:03:30,100 --> 00:03:35,250
So what we're doing is we're saying, hey, I want you to also take the outputs of this command.

66
00:03:35,250 --> 00:03:42,060
So in this case, I'm going to do a you name and we're going to say, I want you to reach whatever the

67
00:03:42,060 --> 00:03:44,730
value of this command is, whatever the output is.

68
00:03:44,970 --> 00:03:49,260
I want that to be the record under this domain that you're going to reach out to.

69
00:03:49,410 --> 00:03:54,900
So we're not requesting we go back, we pull for it and we can say there's another HTP request that

70
00:03:54,900 --> 00:03:55,590
just came in.

71
00:03:55,860 --> 00:04:01,710
And if we look at the results, it says Linux, which is probably the result that we got from our you

72
00:04:01,710 --> 00:04:05,050
name command that's been attached to the DNS.

73
00:04:05,070 --> 00:04:06,160
So this is very great.

74
00:04:06,270 --> 00:04:11,790
This is a very good tool and a very good track when it comes down to a blind RC by default.

75
00:04:11,820 --> 00:04:17,410
Should always just try the scroll commands and have a server where there's a collaborator, Netcare

76
00:04:17,460 --> 00:04:21,930
subdivisional, you own whatever that is, having some sort of a way to monitor for his request.

77
00:04:22,230 --> 00:04:23,480
And again, it doesn't have to be you name.

78
00:04:23,480 --> 00:04:26,350
We can also send a less command over this one works.

79
00:04:27,280 --> 00:04:28,860
We're going to pull for it again.

80
00:04:29,970 --> 00:04:31,860
And it's another request that just came in.

81
00:04:31,980 --> 00:04:38,700
We're going to look at it and it says uploads, which we're assuming that the uploads folder exists.

82
00:04:38,970 --> 00:04:44,520
Then we can also just verify by doing less uploads, depending on how the application works, this may

83
00:04:44,520 --> 00:04:48,950
or may not actually give us an answer because of the space that's going within this command.

84
00:04:49,380 --> 00:04:57,810
So we're going to try it again and we're going to pull and let's see, is this the right one test?

85
00:04:57,810 --> 00:04:59,580
One, two, three, PMG, which is.

86
00:04:59,980 --> 00:05:05,320
The first one of the first files that we uploaded within the Web server, and we're getting it as a

87
00:05:05,320 --> 00:05:07,120
result to our command.

88
00:05:08,380 --> 00:05:11,230
So, again, you want to make sure you understand how these applications work.

89
00:05:11,440 --> 00:05:15,310
You want to test every single user input that's given as an output.

90
00:05:15,490 --> 00:05:17,800
There's a ton of different attack scenarios that can come up with.

91
00:05:17,980 --> 00:05:20,410
Again, it all comes down to what you're testing for.

92
00:05:20,660 --> 00:05:26,650
And RC, especially a blind RC, is very common, especially if they are doing something to these file

93
00:05:26,650 --> 00:05:30,670
names, whether they're renaming them, they're moving them, whatever that is.

94
00:05:30,910 --> 00:05:32,290
You want to always look for these.

95
00:05:33,300 --> 00:05:34,480
Again, they're very common.

96
00:05:34,810 --> 00:05:40,420
Blinder's these are very useful is have to make sure you have a way to collect your response.