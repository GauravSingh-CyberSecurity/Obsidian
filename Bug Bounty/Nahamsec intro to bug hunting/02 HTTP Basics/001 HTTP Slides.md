1
00:00:00,180 --> 00:00:05,460
But before we jump into the hacking, I want to talk about the basics of an HGP request, what happens

2
00:00:05,460 --> 00:00:08,370
when you type in a Web address into your browser?

3
00:00:08,550 --> 00:00:12,370
What information is sent to these Web server and while you receive back in return.

4
00:00:12,690 --> 00:00:17,940
So when you visit in the Homestake dot com, my personal website, your browser is sending a request

5
00:00:17,940 --> 00:00:22,320
to the Web RWD, which is a slash saying this is the host, this is a user agent.

6
00:00:22,320 --> 00:00:28,080
I have, for example, I'm using Firefox and it's going to say this is what I'm expecting to accept.

7
00:00:28,290 --> 00:00:32,700
There's going to be an authorization perhaps, where you authorize yourself because you're already logged

8
00:00:32,700 --> 00:00:34,610
in and it's going to also have a referral.

9
00:00:34,620 --> 00:00:37,660
That means the website that you already coming from.

10
00:00:37,680 --> 00:00:42,240
So if you on Google looking for my website and you click on it, my website is going to know where you're

11
00:00:42,240 --> 00:00:42,930
coming from.

12
00:00:45,330 --> 00:00:48,360
So just to break it down again, the first one is the endpoint.

13
00:00:48,360 --> 00:00:49,490
That's the page you're fetching.

![[Screenshot From 2025-02-17 19-48-45.png]]
14
00:00:49,500 --> 00:00:54,150
So if you're looking at your profile, it will be something like profile that profile your user ID.

15
00:00:54,510 --> 00:00:55,570
The next one is the host.

16
00:00:55,590 --> 00:00:57,490
Again, this is the website you are fetching.

17
00:00:58,140 --> 00:01:02,460
The third thing, user agent is the browser you're using Sattell, the web server.

18
00:01:02,490 --> 00:01:06,540
This is a browser I have give me the best version of the website destitutes, my browser.

19
00:01:07,110 --> 00:01:11,520
And the next one is what type of content you want to receive, which is the content type, as I mentioned,

20
00:01:11,520 --> 00:01:12,280
authorization.

21
00:01:12,300 --> 00:01:16,230
This is where you authorize yourself, if you're already logged into this website is going to say,

22
00:01:16,230 --> 00:01:17,740
hey, I have an authorization code.

23
00:01:18,030 --> 00:01:18,630
Here it is.

24
00:01:18,880 --> 00:01:19,920
Let me be logged in.

25
00:01:20,280 --> 00:01:23,970
And the referrer is the website where you were referred to the next one.

26
00:01:24,210 --> 00:01:28,440
But as you saw in the last slide, there is a keyword called Get.

![[Screenshot From 2025-02-17 19-51-02.png]]
27
00:01:28,440 --> 00:01:30,570
I mean that I'm saying get this page for me.

28
00:01:30,570 --> 00:01:35,190
I want you to fetch this data from this page, but you can also make other requests.

29
00:01:35,190 --> 00:01:40,530
For example, if you post requests that meat could be that you're creating or changing data with a put

30
00:01:40,530 --> 00:01:41,010
request.

31
00:01:41,010 --> 00:01:46,140
It means you're replacing or modifying some sort of a data deleting, as obvious as it sounds or to

32
00:01:46,140 --> 00:01:51,660
delete some data and options is to communicate to see what options does that particular endpoint take.

33
00:01:51,930 --> 00:01:55,770
And there's also had this one is the same as yet, but it doesn't show you a response.

34
00:01:55,770 --> 00:01:58,330
It just requests to see if that pages there or not.

35
00:01:58,340 --> 00:01:59,810
So it doesn't give you a response at all.

36
00:01:59,820 --> 00:02:02,130
It just looks to see if that page is available.


![[Screenshot From 2025-02-17 19-52-13.png]]
37
00:02:02,730 --> 00:02:07,500
When you make a request to a Web server, the server is going to respond with a variety of ranges.

38
00:02:07,860 --> 00:02:11,380
Each of these mean different things and it kind of that's your browser, know what to expect.

39
00:02:11,760 --> 00:02:17,550
So, again, if you make a request to a webroot and the page is available, it's going to be in the

40
00:02:17,550 --> 00:02:18,480
200 ranges.

41
00:02:18,870 --> 00:02:24,030
If you go to a website and it redirects you to another page, that's going to come back as to 300.

42
00:02:24,600 --> 00:02:28,410
And if you are unauthorized, maybe you don't have access to this resource.

43
00:02:28,420 --> 00:02:34,140
The page is there or the method you are using is not allowed that it's going to be within the 400 range.

44
00:02:34,650 --> 00:02:36,710
There's also the last one was 500.

45
00:02:36,720 --> 00:02:39,780
This is where the server doesn't know how to handle your request.

46
00:02:40,110 --> 00:02:42,770
And it comes back and says, hey, I don't know what to do with this request.

47
00:02:42,780 --> 00:02:43,380
There is an error.

48
00:02:43,380 --> 00:02:43,860
Fix it.

49
00:02:44,100 --> 00:02:47,610
It's a very important for you to understand as you get into your hacking.

50
00:02:47,610 --> 00:02:51,060
So I highly recommend getting familiar with each response status code.

51
00:02:51,360 --> 00:02:55,650
You can go to Mozilla's website, as I put it, in the resource section of this course, and kind of

52
00:02:55,650 --> 00:02:57,680
get familiar what each one means.

53
00:02:57,700 --> 00:03:01,830
Or if you come up with them and you see them while you're hiking, you can look them up and learn more

54
00:03:01,830 --> 00:03:02,330
about them.