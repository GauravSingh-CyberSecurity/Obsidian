1
00:00:00,180 --> 00:00:05,700
Now, let's see what this actually looks like within our browser, we can access the Chrome dev tools

2
00:00:05,700 --> 00:00:11,520
by clicking on the page, going to inspect this will show us what the browser is exchanging with the

3
00:00:11,520 --> 00:00:12,130
Web server.

4
00:00:12,360 --> 00:00:18,120
So as we refresh in the network tab, it will show us all the requests made within this page in order

5
00:00:18,120 --> 00:00:18,860
for it to render.

6
00:00:19,500 --> 00:00:22,710
As I mentioned earlier, each of these requests come with a status code.

7
00:00:22,710 --> 00:00:26,850
And as you can see, all of them come back as 200 because all of them actually exist.

8
00:00:27,450 --> 00:00:29,250
But now let's say if we go to an invalid page.

9
00:00:35,700 --> 00:00:40,950
As you can see, the website comes back and says, Page, I found it in chrome dev tools, we can actually

10
00:00:40,950 --> 00:00:46,150
see that the status code is coming back as photo for which the browser expects to say not found.

11
00:00:46,830 --> 00:00:52,650
If you go back to our current browser and we load back the website again, we can also see the headers

12
00:00:52,650 --> 00:00:56,040
and information that was exchanged between our browser and the Web server.

13
00:00:56,280 --> 00:01:03,000
By clicking on each of these requests so you can see here, we made a request to take our training.

14
00:01:03,360 --> 00:01:04,890
We use the get method.

15
00:01:05,220 --> 00:01:06,480
We got a 200 back.

16
00:01:06,870 --> 00:01:09,000
This is the IP address for the Web server.

17
00:01:09,000 --> 00:01:14,760
And you can also see all the other information, like our browser information, our hostname and so

18
00:01:14,760 --> 00:01:19,890
on, can also click at the preview and you can see what this website looks like, which kind of matches

19
00:01:19,890 --> 00:01:22,080
exactly with what we render early on.

20
00:01:22,510 --> 00:01:24,030
We could also see the response.

21
00:01:24,390 --> 00:01:28,980
In some cases you may see additional headers where the server replies with some headers and says, hey,

22
00:01:29,340 --> 00:01:30,840
this is what I want to use.

23
00:01:31,170 --> 00:01:36,240
And you can kind of see that this matches the exact thing as you can click on Right Click View page

24
00:01:36,240 --> 00:01:36,720
source.

25
00:01:37,110 --> 00:01:38,640
And they both actually match.

26
00:01:38,910 --> 00:01:44,250
So this is what the server is returning when we make our request and in return it gets rendered and

27
00:01:44,250 --> 00:01:46,020
shown to us as a user.

28
00:01:46,460 --> 00:01:50,520
Well, I encourage people to get familiar with the Google Chrome dev tools.

29
00:01:50,760 --> 00:01:56,910
We can also use burb speed to make these things look nicer and have some automation, additional tooling

30
00:01:57,150 --> 00:01:57,900
while we hack.

31
00:01:58,630 --> 00:02:03,000
You can download Bourbaki by going to the ports for our website, scrolling down and looking at the

32
00:02:03,000 --> 00:02:07,950
different burb additions and clicking on the one that fits your needs.

33
00:02:08,310 --> 00:02:12,570
For the sake of this scores, I highly recommend using the community version, which is free.

34
00:02:12,860 --> 00:02:15,390
It may be limited, but it gets the job done for us.

35
00:02:15,720 --> 00:02:20,040
If you have a little bit of extra cash and you want to upgrade, your brevetti license can spend four

36
00:02:20,040 --> 00:02:25,290
hundred dollars per year per user and download the professional version that comes with different scanners

37
00:02:25,500 --> 00:02:32,070
and additional tooling can download the community version by clicking on get community and pushing.

38
00:02:32,070 --> 00:02:37,140
Download that his version and selecting your operating system and clicking download.

39
00:02:38,010 --> 00:02:42,150
Once you open a bird seat after you have installed it, it would ask you to either create a new project

40
00:02:42,420 --> 00:02:47,610
or just simply use temporary projects with the default settings as you start it off.

41
00:02:48,120 --> 00:02:49,470
Now we have opened up.

42
00:02:49,470 --> 00:02:53,520
We want to make sure that our browser knows how to communicate with burb suite.

43
00:02:54,300 --> 00:03:01,380
When you make a request to a website that's using https, your information is getting encrypted before

44
00:03:01,380 --> 00:03:02,580
it's sent to the web server.

45
00:03:02,850 --> 00:03:07,980
So nobody else on your network could actually intercept that data and decode it and use it.

46
00:03:08,010 --> 00:03:13,710
So what we're going to do next is we're going to tell the browser, hey, burb suite is a trusted resource.

47
00:03:13,710 --> 00:03:18,300
I want you to allow him to see the information that I'm sending to each Web server and allow him to

48
00:03:18,300 --> 00:03:19,380
change or modify it.

49
00:03:20,760 --> 00:03:25,800
In order to do this, we want to download the speed certificate within our browser and also install

50
00:03:25,800 --> 00:03:26,610
it in Google Chrome.

51
00:03:27,180 --> 00:03:33,270
The steps to install the certificate may change depending on your browser and the operating system you're

52
00:03:33,270 --> 00:03:35,700
using, but they all may be a little similar.

53
00:03:35,940 --> 00:03:41,550
In order for speed to be able to intercept each request sent to any Web server, we want to make sure

54
00:03:41,550 --> 00:03:44,580
our browser knows a Bourbon Street is a trusted resource.

55
00:03:45,180 --> 00:03:50,400
This ensures that every bit of data we're sending to the Web server is encrypted and nobody on your

56
00:03:50,400 --> 00:03:54,510
local network can actually access or view the information that they're sending through.

57
00:03:54,810 --> 00:03:58,070
That could be passwords, usernames, bank account information and so on.

58
00:03:58,590 --> 00:04:03,720
So by installing burb speed certificate, we're telling our browser, hey, I trust burb suite, let

59
00:04:03,720 --> 00:04:08,610
him access my data without it being encrypted, actually decrypted and send it through before it hits

60
00:04:08,610 --> 00:04:09,270
the Web server.

61
00:04:09,360 --> 00:04:14,730
In order to install the certificate, I want to make sure our browser is actually speaking to burb suite.

62
00:04:14,940 --> 00:04:16,500
You can do this by doing different things.

63
00:04:16,500 --> 00:04:21,000
The first option is to use the Google Chrome default settings by going through proxy and pointing it

64
00:04:21,000 --> 00:04:21,720
to BRB suite.

65
00:04:21,990 --> 00:04:27,120
Or you can download tools like Proxy Proxy, which I highly recommend Foxe proxies available on both

66
00:04:27,120 --> 00:04:28,860
Google Chrome and Firefox.

67
00:04:29,070 --> 00:04:30,870
It's highly recommended to use.

68
00:04:30,870 --> 00:04:34,050
It makes it easier to enable and disable your proxy while you're hiking.

69
00:04:34,500 --> 00:04:39,510
So once you have Insull Foxe proxy, we're going to go to options and we're going to add a new proxy.

70
00:04:40,740 --> 00:04:45,330
You can get this information by going to your burb suite, clicking on proxy and then going to options.

71
00:04:45,670 --> 00:04:51,090
Want to make sure that the browser is sending all this information to this current IP address, which

72
00:04:51,090 --> 00:04:53,370
is our local host on Port AT&amp;T.

73
00:05:00,110 --> 00:05:05,570
Once you have done this, we can go to Fox proxy and enable our proxy to use that IP in port for every

74
00:05:05,570 --> 00:05:06,560
request that we make.

75
00:05:11,950 --> 00:05:17,080
Since we haven't installed the birth certificate yet, when we go to any website that uses SSL, the

76
00:05:17,080 --> 00:05:20,410
browser is not going to trust it because it doesn't know what to do with that request.

77
00:05:20,470 --> 00:05:26,260
So, for example, if I go to Twitter dot com, the browser is going to come back and say, wait a minute,

78
00:05:26,260 --> 00:05:27,690
this connection is not private.

79
00:05:27,700 --> 00:05:28,560
Something is up.

80
00:05:28,570 --> 00:05:29,790
Are you sure you want to proceed?

81
00:05:30,070 --> 00:05:34,770
But we can actually install the birth certificate by going to HTP column site.

82
00:05:34,780 --> 00:05:35,620
Stosh Berp.

83
00:05:36,130 --> 00:05:40,420
This will bring up the communications block on page one, the right hand corner.

84
00:05:40,420 --> 00:05:45,730
We can click on a certificate which will download the certificate belonging to upsweep.

85
00:05:46,210 --> 00:05:49,060
Not that we have downloaded the birth certificate.

86
00:05:49,070 --> 00:05:55,150
We're going to go through our chrome settings, type in the word certificate into the search, click

87
00:05:55,150 --> 00:06:02,140
on security, scroll all the way down Manege certificate, go to our trusted route certificates, import

88
00:06:02,140 --> 00:06:06,550
and import a certificate that we just download it once to import and push finish.

89
00:06:06,880 --> 00:06:10,390
It's going to make sure that we want to install the certificate as a security measure.

90
00:06:10,390 --> 00:06:12,940
We're going to click yes and allow to import.

91
00:06:13,900 --> 00:06:18,640
Once we've installed our certificate, we're going to simply exit out of Google Chrome and relaunch

92
00:06:18,640 --> 00:06:20,800
it to make sure all the security settings have been applied.

93
00:06:20,920 --> 00:06:25,480
Now that we've opened up our browser again, we're going to type in Twitter just to make sure it works.

94
00:06:25,880 --> 00:06:29,080
As you can see now, we can actually launch our proxy again.

95
00:06:29,680 --> 00:06:35,170
Now we can turn on the intercept and within verb suite and allow our browsers request to be intercepted.

96
00:06:36,460 --> 00:06:41,680
As you can see, every time we make a different request, it is actually able to intercept and show

97
00:06:41,680 --> 00:06:43,150
us what each request looks like.

98
00:06:43,780 --> 00:06:46,090
Now, let's go back to our training website.

99
00:06:46,330 --> 00:06:51,130
And as you can see, your browser is going to intercept every request you make and it's not going to

100
00:06:51,130 --> 00:06:52,700
work unless you forward it.

101
00:06:52,710 --> 00:06:57,550
So until you press forward, find the browser is going to be hanging and waiting for your actions.

102
00:06:57,680 --> 00:07:03,100
So if we look forward, meaning the website loads and we can see the material from the training course.