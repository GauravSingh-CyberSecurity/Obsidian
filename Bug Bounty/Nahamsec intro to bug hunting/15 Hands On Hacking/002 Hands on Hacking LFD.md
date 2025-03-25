


---
https://merch.nahamsec.com/
![[Screenshot From 2025-03-24 15-50-17.png]]
1
00:00:00,180 --> 00:00:05,110
One of the things that stands out to me here is the image of these products, so I'm going to do here

2
00:00:05,110 --> 00:00:06,900
is I'm actually going to ==open up the source== (ctrl u).  view-source:https://merch.nahamsec.com/
![[Screenshot From 2025-03-24 15-50-52.png]]


3
00:00:09,300 --> 00:00:13,890
And I'm going to scroll down and look at how it's loading these images and it looks like it's using

4
00:00:13,890 --> 00:00:20,140
product/picture and then the parameter file and then some hash, we're going to click it.
https://imgproxy.fourthwall.com/cJfCX_GDQONq7Zw81Hc_jqqpXQm5pkSB1olWktXwCUo/w:120/sm:1/enc/YzZhYzc4ZjVlNWJi/MDMyZXQduLlfYdqU/iv1BfyTp5tuFqake/fTbnDyYAjyCz1GVv/jDp1RPGLPS1t5aHA/AUx76Zt3WCvG35g-/IRQzKg0l5v8MOfmH/yUKjfm-KDFXgrHA6/uQkG7aHQtTcnpUmK/Xkx-dod8KY6fo6x3/fj77LIx-EilQFu3Q/lIwRaAVyUZNMWOnD/H-ZE6S_wGW6XtZWd/X2FiRqfrY00yNLCL/6N20AAxq1ROUaAha/oKWD4jXj19EMFkNe.webp

5
00:00:20,880 --> 00:00:24,270
I'm going to open this in a new tab featuring an image.
![[Screenshot From 2025-03-24 15-53-52.png]]
6
00:00:24,580 --> 00:00:27,900
The first thing I'm going to do here is I'm going to give it a ././

7
00:00:28,380 --> 00:00:28,980
If it works.

8
00:00:29,100 --> 00:00:34,320
Does that indicate that we're more than likely may have a vulnerability here, but that's just mess

9
00:00:34,320 --> 00:00:35,160
with that a little bit more.

10
00:00:35,580 --> 00:00:41,040
The next thing I want to do is I want to see if I can check and see if this file exists within the picture

11
00:00:41,670 --> 00:00:44,810
directory so that it's not there doesn't really matter.

12
00:00:44,820 --> 00:00:45,500
In some cases.

13
00:00:45,510 --> 00:00:51,920
It's good if this comes back as a valid image and this video and picture product, some other directories

14
00:00:51,930 --> 00:00:54,510
so I can know what I'm trying to send in and out of.

15
00:00:54,870 --> 00:00:58,950
But as a matter, we're going to give us another try and see if we can find a moment.

16
00:00:59,010 --> 00:01:03,150
But first thing I'm going to do here is I'm going to give it a dot slice just to see if it reacts any

17
00:01:03,150 --> 00:01:03,480
way.

18
00:01:04,140 --> 00:01:05,020
It's like it comes back.

19
00:01:05,020 --> 00:01:06,660
It doesn't react any different way to it.

20
00:01:06,810 --> 00:01:08,280
It's still in the current directory.

21
00:01:08,670 --> 00:01:10,200
It's still looking for the same found there.

22
00:01:10,730 --> 00:01:11,610
I delete this.

23
00:01:11,970 --> 00:01:14,370
I'm going to give it a different file name.

24
00:01:14,710 --> 00:01:17,820
I see if it's going to give us an error, comes back and says file doesn't exist.

25
00:01:18,450 --> 00:01:19,340
That looks good.

26
00:01:19,770 --> 00:01:26,010
==Now, what we're gonna do is we're going to try and just fetch for a local want to traverse out of a==

==27==
==00:01:26,010 --> 00:01:28,870==
==few directories by doing that slash.==

`././././././././././././././././././././././././././././././etc/passwd`

28
00:01:29,150 --> 00:01:32,560
And then I'm going to look for etc password.

29
00:01:32,590 --> 00:01:33,300
See what happens.

30
00:01:34,140 --> 00:01:35,840
So it looks like it says this doesn't exist.

31
00:01:35,970 --> 00:01:37,410
There are two things that could happen here.

32
00:01:37,420 --> 00:01:42,450
One, there might be some filtering happening or we may have not gone out of enough directories, which

33
00:01:42,450 --> 00:01:43,440
is unlikely.

34
00:01:43,740 --> 00:01:48,000
Or two, there is no vulnerability here, but we're going to try out for a fun.

35
00:01:48,010 --> 00:01:48,590
I'm out of work.

36
00:01:48,630 --> 00:01:54,360
So here we're going to do more sashays just to make sure we have actually escaped out of enough directories

37
00:01:54,870 --> 00:01:55,800
to fix it really quick.

38
00:01:56,130 --> 00:01:56,600
Right there.

39
00:01:56,610 --> 00:01:57,810
It looks like it's not working.

40
00:01:58,420 --> 00:02:03,790
==We're going to just give it a root folder, just a root for the other Web server etc password.==
/etc/passwd


41
00:02:03,980 --> 00:02:06,060
If it works, that doesn't work either.

42
00:02:06,550 --> 00:02:11,010
==So the other option here is there are a few things where we can do as we can encode our ././ so==
==`%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f`==
==43==
==00:02:11,010 --> 00:02:12,810==
==we can do is.==

44
00:02:12,810 --> 00:02:18,220
We can do `%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f` which is the same as typing in ./././  such

47
00:02:29,210 --> 00:02:34,250
see if that works so it doesn't work.

48
00:02:34,280 --> 00:02:36,000
We don't have to always overcomplicated.

49
00:02:36,030 --> 00:02:39,360
==The next thing we can do is we can assume that the application is filtering out  ./././././././==

50
00:02:39,710 --> 00:02:44,450
That's not to say if I do this or that size, it's converting it to nothing.

51
00:02:44,460 --> 00:02:46,160
So it's going to pretty much be blank.

52
00:02:46,290 --> 00:02:51,200
==One of the things that we discover in our lab was there are times when you need to be able to escape==

==53==
==00:02:51,200 --> 00:02:51,600==
==out of this.==

54
00:02:51,600 --> 00:02:54,680
==So what I'm going to do is I want to trail a ./././==

==55==
==00:02:55,400 --> 00:02:59,100==
==So it's going to be ..././../==
56
00:02:59,510 --> 00:03:02,420
So what happens here is it's going to application is going to take these.

57
00:03:03,180 --> 00:03:08,670
Going to said with nothing, and once it's removed, it's going to have another dot, dot, dot in the

58
00:03:08,670 --> 00:03:13,320
middle, which is not going to get filtered because filtering sometimes don't work as it's intended,

59
00:03:13,540 --> 00:03:19,910
and they're only looking at whatever you're supplying and not the actual output of the filter string.

60
00:03:20,250 --> 00:03:21,060
So let's try this out.

61
00:03:21,060 --> 00:03:22,050
We're going to add this here.

62
00:03:23,010 --> 00:03:24,480
==I'm going to add a bunch of these.==
==..././../..../../..././..././.../.../.../.../../.../.../../././././etc/passwd==



64
00:03:28,690 --> 00:03:30,180
==I'm going to try this on and see if it works. in the web browser== 

==65==
==00:03:31,770 --> 00:03:34,120==
==So it looks like this is actually a valid file.==

==66==
==00:03:34,140 --> 00:03:38,550==
==It's coming back as an image and it's not showing me the contents of this file.==

==67==
==00:03:38,790 --> 00:03:42,510==
==So what we're going to do is we're going to try and view source using ctrl+u and see if there's anything in the source==

==68==
==00:03:42,510 --> 00:03:43,200==
==of this image.==

==69==
==00:03:43,500 --> 00:03:49,680==
==And it looks like, sure enough, there was actually a file on the server, a little file disclosure==

70
00:03:49,680 --> 00:03:55,770
here by escaping out of the directors directory traversal, but also playing against the filtering system

71
00:03:55,770 --> 00:03:58,170
that was in place and finding it by password.

72
00:03:58,530 --> 00:04:04,350
Again, when it comes down to looking for local file disclosure or things that could be dealing with

73
00:04:04,350 --> 00:04:08,820
a filtering, you really don't have a way of knowing if there is an actual vulnerability there.

74
00:04:09,060 --> 00:04:13,810
All you have to do is try it out, give as many people as he can think through as a puzzle.

75
00:04:14,070 --> 00:04:18,300
OK, if it's taking the ../,  I'm assuming that the filtering system on the other end is

76
00:04:18,300 --> 00:04:19,020
looking for that.

77
00:04:19,680 --> 00:04:21,940
What do I do to fix it?

78
00:04:22,080 --> 00:04:25,860
Could it be a encoding like %2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f%2e%2f

79
00:04:26,100 --> 00:04:32,700
Could it be a trailing .../..././.../.../ and appending stuff to the .../ get to work like we did at

80
00:04:32,700 --> 00:04:35,250
the site, like we did for this example?