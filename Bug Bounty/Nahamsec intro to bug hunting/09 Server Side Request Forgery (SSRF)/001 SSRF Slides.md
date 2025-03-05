

026 URI-Schemes
https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml


Note: open redirects can be escalated to SSRF.

---

1
00:00:00,060 --> 00:00:05,460
The next vulnerability we're going to look at is server side, of course, forgery, also known as necessary,


![[Pasted image 20250305083028.png]]
2
00:00:05,670 --> 00:00:07,640
and a server site request, forgery, attack.

3
00:00:07,650 --> 00:00:12,120
The attacker can abuse a functionality on the server to read or update internal resources.

4
00:00:12,470 --> 00:00:18,390
So think of this as having a Web browser within an application that allows you to browse through an

5
00:00:18,390 --> 00:00:22,430
internal and private network that's only accessible within the application.

6
00:00:22,500 --> 00:00:27,000
It's SRF comes in different flavors, but the three top common ones that I've seen are listed below

7
00:00:27,300 --> 00:00:32,640
Vlogger SRF, which allows you to scan for accessible hosts and open ports that come with it.

8
00:00:32,640 --> 00:00:37,380
A full response SRF, which allows you to see the entire response from the server and last but not least

9
00:00:37,380 --> 00:00:38,790
is limited or no response.

10
00:00:38,790 --> 00:00:44,250
SRF, which shows you a portion of the response, like a title or a specific part, or the nonresponse

11
00:00:44,250 --> 00:00:47,270
where you have access to the resource but you can't directly see them.

12
00:00:47,310 --> 00:00:50,900
So in other words, you can actually interact with them, but you can't see the results.


![[Screenshot From 2025-03-05 08-31-27.png]]
13
00:00:50,940 --> 00:00:52,200
So this is kind of an example here.

14
00:00:52,420 --> 00:00:58,710
Imagine the website has a proxy where it says, I want you to fetch an image from a remote host and

15
00:00:58,710 --> 00:00:59,940
displayed within the website.

16
00:01:00,150 --> 00:01:05,190
So the website does in the background, it sends a request to a proxy, gives it that you are of the

17
00:01:05,190 --> 00:01:06,660
remote family want to fetch in.

18
00:01:06,660 --> 00:01:12,240
This example is Gravett or dot com stocks, one dot PMG and it displays the content of that file from

19
00:01:12,240 --> 00:01:13,050
the remote server.


![[Screenshot From 2025-03-05 08-32-23.png]]
20
00:01:13,170 --> 00:01:18,690
So depending how the application is actually coded and what you are asking you have access to, you

21
00:01:18,690 --> 00:01:20,130
may be able to do different things.

22
00:01:20,360 --> 00:01:25,350
But if you're not familiar with a you are I scheme also known as a uniform resource identifier, I'll

23
00:01:25,350 --> 00:01:29,960
make sure to leave a link down in the resource section so you can read over it and understand it better.

24
00:01:30,210 --> 00:01:35,700
But in this example, what we're doing is we're pointing the you are all parameter to a local IP address

25
00:01:35,700 --> 00:01:38,680
within the private network instead of what it was originally fetching.

26
00:01:38,850 --> 00:01:42,810
So in other words, we're telling the application, hey, forget about this file that we're looking

27
00:01:42,810 --> 00:01:43,860
for from a remote host.

28
00:01:44,010 --> 00:01:46,860
I want you to fetch whatever is hosted on this IP address.

29
00:01:47,190 --> 00:01:52,770
In this example, we're assuming that this IP address actually exists and is hosting some application

30
00:01:52,770 --> 00:01:53,310
internally.

31
00:01:53,500 --> 00:01:58,410
Just to be clear, this IP address is just an example of something that could be hosting a potential

32
00:01:58,410 --> 00:01:59,570
internal application.

33
00:01:59,580 --> 00:02:01,280
So it may not always be the same.

34
00:02:01,290 --> 00:02:05,790
In other words, you may have to look for an internal IP address that will allow you to fetch internal

35
00:02:05,790 --> 00:02:09,620
resources that is accessible only by this application and that's responsive.

36
00:02:09,630 --> 00:02:14,850
You can see when we hit 10 dot 0.01, the application comes back and says, hey, I don't have anything

37
00:02:14,850 --> 00:02:15,750
in the root folder.

38
00:02:15,900 --> 00:02:20,620
But here is a response that I would give you if you are an internal unauthenticated user.

39
00:02:20,640 --> 00:02:26,850
So, again, in this example, we're assuming that 10 dot 0.01 is actually accessible and is hosting

40
00:02:26,850 --> 00:02:28,040
some sort of an application.

41
00:02:28,380 --> 00:02:33,630
And when we actually access it within the proxy endpoint, it comes back and gives us an error or something

42
00:02:33,630 --> 00:02:36,670
that indicates, hey, I have this application hosted here.

43
00:02:36,840 --> 00:02:37,770
Here are the roots.

44
00:02:37,950 --> 00:02:39,300
And here's what I will show you.

45
00:02:39,300 --> 00:02:44,070
If you were actually sitting within our internal network, the best thing about  SSRF it  necessarily is that
![[Screenshot From 2025-03-05 08-35-52.png]]
46
00:02:44,070 --> 00:02:49,800
it doesn't just limit you to internal resources, but it also allows you to search internal files depending

47
00:02:49,800 --> 00:02:51,780
on what you are Eyskens you have access to.

48
00:02:52,020 --> 00:02:57,330
So in this case, the application allows us to use foul language, which actually features an internal

49
00:02:57,330 --> 00:03:00,060
file and displays the contents of it within the application.



![[Screenshot From 2025-03-05 08-37-26.png]]
50
00:03:00,210 --> 00:03:05,670
Now let's talk about the blindness SRF blindness SRF happens where you are actually able to hit an internal

51
00:03:05,700 --> 00:03:10,420
website, but you can actually see what it comes back or the response of the request.

52
00:03:10,740 --> 00:03:17,340
So in the first example we were looking for 10 zero zero one and it takes about 80 milliseconds to come

53
00:03:17,340 --> 00:03:21,210
back, which we assume something may be up or we're not very sure of it.

54
00:03:22,020 --> 00:03:25,990
So what we can confirm that by actually giving it an invalid port to see how he reacts.

55
00:03:26,010 --> 00:03:30,720
So if we give it Port 81, where we are assuming in this example that it's not hosting anything, it's

56
00:03:30,720 --> 00:03:31,590
not an open port.

57
00:03:31,830 --> 00:03:34,720
It takes longer to load, which indicates that there isn't necessary.

58
00:03:34,790 --> 00:03:38,700
And we can actually port scanned the internal network and every IP address within it.

59
00:03:38,770 --> 00:03:43,740
And in the last example, as you can see, we're looking for Port six three seven nine, which takes

60
00:03:43,740 --> 00:03:48,150
about ninety four milliseconds, which is close to our first example, which could indicate that something

61
00:03:48,150 --> 00:03:50,180
may be running within six three seven nine.



![[Screenshot From 2025-03-05 08-39-00.png]]
62
00:03:50,520 --> 00:03:56,280
Whereas in SRF we are getting some sort of a response by looking at the HTP response code.

63
00:03:56,310 --> 00:04:03,330
So for example, when we request 10 DOT 0.01, the application comes back and says, Hey, I got a 200,

64
00:04:03,330 --> 00:04:08,520
OK, but I can't show you the content because what I'm giving you back in the response is limited because

65
00:04:08,520 --> 00:04:09,770
of how the application works.

66
00:04:10,260 --> 00:04:12,060
So we can actually give it a port 87.

67
00:04:12,550 --> 00:04:14,540
Port 87 doesn't have anything on it.

68
00:04:14,550 --> 00:04:17,770
It may come back and say, hey, 404, I didn't find anything.

69
00:04:17,800 --> 00:04:21,960
And of course, last but not least, it could be that we find some other ports other than Port 80,

70
00:04:21,960 --> 00:04:26,070
which we're assuming in the first example and looking for Port Adelaide.

71
00:04:26,190 --> 00:04:31,580
And the application comes back and says, hey, 200, OK, there is something actually board 80, 80

72
00:04:31,590 --> 00:04:32,010
as well.


![[Screenshot From 2025-03-05 08-40-05.png]]
73
00:04:32,400 --> 00:04:36,610
Now, let's look at some of these limitations and potential blockers when it comes down to looking for

74
00:04:36,610 --> 00:04:41,970
necessarily, for example, an application may have a white listing in place where it only allows you

75
00:04:41,970 --> 00:04:48,090
to fetch data from domains that has been specified within the application and you can't really get out

76
00:04:48,090 --> 00:04:49,500
of those limitations.

77
00:04:50,190 --> 00:04:56,070
A block listing could be something that's blocking access to a potential IP address as domains or keywords.

78
00:04:56,360 --> 00:04:59,550
So in other words, they allow everything else but these.

79
00:04:59,930 --> 00:05:05,190
Mattresses are being predefined and of course, we could have a restricted content type extensions or

80
00:05:05,190 --> 00:05:09,270
characters where it only allows a particular file or format to be loaded.

81
00:05:09,600 --> 00:05:14,400
And last but not least, as I mentioned this earlier, you may actually have unnecessary if you don't

82
00:05:14,400 --> 00:05:15,510
see the response.

83
00:05:15,750 --> 00:05:19,380
So you may have to play around and find a way around it.


![[Screenshot From 2025-03-05 08-41-24.png]]
84
00:05:19,650 --> 00:05:20,870
Now, let's talk about a solution.

85
00:05:21,330 --> 00:05:23,540
In an earlier chapter, we talked about open redirect.

86
00:05:23,700 --> 00:05:27,860
This is very, very handy when it comes down to bypassing a white listing.

87
00:05:27,870 --> 00:05:32,610
So, for example, if we're hacking on the Hammarstedt Dotcom, the application may only allow to fetch

88
00:05:32,610 --> 00:05:36,320
resources on the Homestake Dotcom and that website only.

89
00:05:36,600 --> 00:05:40,800
But if we have an open window on the home, that dot com, we can actually use the open redirect to

90
00:05:40,800 --> 00:05:45,030
treat this as SRF, to point it to another resource that may not be in the white list.

91
00:05:45,270 --> 00:05:50,190
When it comes down to dealing with a white listing, you may see that the application only allows to

92
00:05:50,910 --> 00:05:53,050
fetch a resource from the Target website.

93
00:05:53,070 --> 00:05:57,600
So in other words, if you're hiking on the dot com, but you haven't necessarily with a white listing

94
00:05:57,600 --> 00:06:03,180
in place, the application is only going to allow you to fetch resources within the norms that dot com

95
00:06:03,180 --> 00:06:03,610
website.

96
00:06:04,020 --> 00:06:08,640
So if you have an open redirect, you can tell the application, hey, I'm using a wireless resource,

97
00:06:08,820 --> 00:06:13,950
but I'm going to trick you into going to another website by using an open redirect to a lot of cases.

98
00:06:13,950 --> 00:06:19,080
I actually recommend a lot of hackers and bug bounty hunters to keep their open redirects for a few

99
00:06:19,080 --> 00:06:21,710
days in case of finding an SRF.

100
00:06:21,870 --> 00:06:26,820
When it comes down to blacklisting, the application may actually say, hey, you can't use this particular

101
00:06:26,820 --> 00:06:28,290
keywords or IP addresses.

102
00:06:28,470 --> 00:06:31,500
There are a ton of good tricks that you can do to bypass these restrictions.

103
00:06:31,650 --> 00:06:38,250
So, for example, if the application is filtering 10 dot 0.01, we can actually register a domain or

104
00:06:38,250 --> 00:06:42,480
a subdomain and pointed to that IP address and bypass the restrictions.

105
00:06:42,630 --> 00:06:47,580
And if you have a restricted content type, extensions or characters would have to manually fuzz and

106
00:06:47,580 --> 00:06:49,470
understand it further for it to make sense.

107
00:06:49,680 --> 00:06:52,800
And there isn't a one type fits all solution for this one.

108
00:06:53,310 --> 00:06:55,350
And last but not least, this is my favorite one.

109
00:06:55,620 --> 00:07:01,890
While you may have a no response SRF, you can actually leverage JavaScript to make a request and retrieve

110
00:07:01,890 --> 00:07:02,700
the file content.

111
00:07:02,740 --> 00:07:08,100
So in other words, we're going to say, hey, I want you to load this HTML page and using JavaScript

112
00:07:08,100 --> 00:07:13,010
we're going to start hafitz this file faster response that I cannot see and send it back to my server.

113
00:07:13,350 --> 00:07:16,760
So there's a few things you may want to keep in mind while fighting for ISIS.

114
00:07:17,190 --> 00:07:19,950
First of all, remember, you're making a server side request.

115
00:07:19,960 --> 00:07:24,780
So that means the request you're making is on the servers behalf and not your browser.

116
00:07:25,320 --> 00:07:29,550
They're actually different ways to look for content on our local hosts other than looking for the keyword

117
00:07:29,550 --> 00:07:33,780
localhost or pointing to the 127 zero zero one IP address.

118
00:07:34,050 --> 00:07:39,330
You might want to get creative, understand how to use the different bypasses to achieve what you're

119
00:07:39,330 --> 00:07:39,870
looking for.

120
00:07:40,200 --> 00:07:42,660
Also, remember that an open redirect could be very handy.

121
00:07:42,900 --> 00:07:43,640
So don't burn.

122
00:07:43,800 --> 00:07:46,860
If you find open redirect, try and keep it for necessar.

123
00:07:46,860 --> 00:07:52,200
If I'm not saying to not report this vulnerability, but I'm saying make sure you cover all your bases

124
00:07:52,350 --> 00:07:54,450
before you report the operator act on its own.

125
00:07:54,870 --> 00:07:58,710
Last but not least, the one thing I want to make sure you understand with unnecessary death is that

126
00:07:58,920 --> 00:08:03,690
you want to make sure that the request comes from a remote server and it doesn't come from your personal

127
00:08:03,690 --> 00:08:04,560
IP address.

128
00:08:04,860 --> 00:08:10,110
So that said, if it does happen and you see a request coming from a remote server, which I will make

129
00:08:10,110 --> 00:08:12,320
sure to demo in our next example.

130
00:08:12,330 --> 00:08:17,160
So if that does happen and the request comes from a remote server, always remember that this particular

131
00:08:17,160 --> 00:08:23,070
machine may be able to talk to other micro services within this PIVER network that may require to be

132
00:08:23,070 --> 00:08:23,820
on a VPN.

133
00:08:24,030 --> 00:08:29,130
If you see that the request is coming from your personal IP address, then that means that this vulnerability

134
00:08:29,130 --> 00:08:32,430
isn't actually necessary if you just making a request through your browser.