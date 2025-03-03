





![[Screenshot From 2025-03-03 16-27-13.png]]
1
00:00:00,060 --> 00:00:04,440
Now, let's talk about local fathers disclosure, this vulnerability would allow an attacker to practically

2
00:00:04,440 --> 00:00:09,150
fetch any local files on the system, depending on how the application is implemented.

3
00:00:09,300 --> 00:00:14,040
The files that we can fetch with this vulnerability strictly depends on how the application is written.

4
00:00:14,310 --> 00:00:19,800
But in some cases, we can either access user files on the Web server or actually read files on our

5
00:00:19,800 --> 00:00:20,730
local to that box.

6
00:00:20,920 --> 00:00:25,890
In other words, this vulnerability would allow us to read practically any files total on this machine,

7
00:00:26,100 --> 00:00:30,300
whether it belongs to the users or it's a default file on the Web server.

8
00:00:30,420 --> 00:00:31,560
Now, let's look at an example.



![[Screenshot From 2025-03-03 16-28-22.png]]
9
00:00:31,950 --> 00:00:36,630
In this example, we can see that my banking site, dot com, has an endpoint called view file.

10
00:00:36,960 --> 00:00:42,810
And this endpoint has a parameter called image where it touches a user's image like the avatar using

11
00:00:42,810 --> 00:00:44,100
the format above.

12
00:00:44,520 --> 00:00:52,440
Now, if we change that path from image, my avatar to that dot, at that stage, those dots Etsy password

13
00:00:52,870 --> 00:00:57,450
would actually pull up the ETSI password on the local machine and show it to us.


![[Screenshot From 2025-03-03 16-29-34.png]]
14
00:00:57,690 --> 00:01:02,730
As you can see here, we're pushing an Etsy password and result is going to show us the content of that

15
00:01:02,730 --> 00:01:03,070
file.

16
00:01:03,330 --> 00:01:07,200
And again, if you're not familiar with Linux filesystems, this is a default file.

17
00:01:07,380 --> 00:01:10,470
It gives you information on every user that's on this box.

18
00:01:10,950 --> 00:01:13,890
Now, let's go back to our example and look at what this means.

19
00:01:14,130 --> 00:01:20,580
As you can see here, the application is saying, hey, I want you to search for images and get my avatar

20
00:01:20,770 --> 00:01:23,340
jpeg as my avatar will be any arbitrary file.

21
00:01:23,610 --> 00:01:26,440
So, again, the application is saying within wherever I'm at.

22
00:01:26,460 --> 00:01:32,010
So wherever my script is running, whatever this file is hosted on the machine, I want you to fetch

23
00:01:32,010 --> 00:01:35,850
the folder images and the found my avatar jpeg again.

24
00:01:35,850 --> 00:01:39,310
My avatar could be any name or any file that belongs to a user.

25
00:01:39,480 --> 00:01:41,740
It could be our file that we want to fetch.

26
00:01:41,760 --> 00:01:48,750
It could be an invoice, whatever it is, the path now it's assumed that we are in home Bankside Dub

27
00:01:48,750 --> 00:01:50,310
Dub Dub Slash images.

28
00:01:51,090 --> 00:01:56,640
This is where the application is hosting all these images and every web site that we go across has some

29
00:01:56,640 --> 00:01:58,200
sort of a similar path.

30
00:01:58,230 --> 00:02:05,130
So in other words, it's not always slash home slash Bankside dub dub dub images that could change depending

31
00:02:05,130 --> 00:02:09,870
on how the site is configured by doing at that stage in the Linux environment, we're actually telling

32
00:02:09,870 --> 00:02:14,550
the website to traverse out of each directory and go back one.

33
00:02:14,580 --> 00:02:20,480
So when we do the first dot dot slash, it takes us out of the images folder and we do another one.

34
00:02:20,490 --> 00:02:25,770
It goes back from the dub dub dub and then the third one goes out of Bankside and the fourth one puts

35
00:02:25,770 --> 00:02:27,900
us in the root directory, which is just a slash.

36
00:02:28,290 --> 00:02:33,720
If you're not familiar with how the Linux system works, I highly recommend either installing an operating

37
00:02:33,720 --> 00:02:39,420
system like Ubuntu or Karley and getting familiar with it, or at least looking into how files are stored

38
00:02:39,540 --> 00:02:42,470
and what are some of the default files on in the next box.

39
00:02:42,690 --> 00:02:43,920
So that's pieces back together.

40
00:02:43,920 --> 00:02:48,780
When we give the application our first of that stage, it's going to take it and put it in front of



![[Screenshot From 2025-03-03 16-32-14.png]]
41
00:02:48,780 --> 00:02:50,790
the actual path that we're looking for.

42
00:02:50,940 --> 00:02:52,770
So again, this is where the images are stored.

43
00:02:52,960 --> 00:02:55,170
It's going to say fetch that's large.

44
00:02:55,770 --> 00:03:01,630
And that would translate into home Bogside dub dub dub, which means that we have came out of this images

45
00:03:01,650 --> 00:03:01,980
folder.

46
00:03:02,670 --> 00:03:05,760
Now we're going to the same thing at another celling outside.

47
00:03:06,270 --> 00:03:10,380
And since there's two of them that we're going out of, it's going to take out images, end up typed

48
00:03:10,380 --> 00:03:11,910
up and translated into home.

49
00:03:12,090 --> 00:03:14,010
Bankside We do the third one.

50
00:03:14,150 --> 00:03:17,640
So it's going to be one, two or three which is going to become just home.

51
00:03:18,030 --> 00:03:22,830
And if we do a fourth one, one, two, three and four it's going to just go to a slide which is the

52
00:03:22,830 --> 00:03:23,700
root directory.

53
00:03:23,970 --> 00:03:29,730
And once you give it our ETSI password, it's going to just transmit that to the ETSI password where

54
00:03:29,730 --> 00:03:32,610
the file is stored and it's going to display its content.

55
00:03:32,850 --> 00:03:37,950
In some cases you may actually not need to do a slash, but it's very helpful to do it, especially


![[Screenshot From 2025-03-03 16-33-50.png]]
56
00:03:37,950 --> 00:03:42,270
in the case of having the power for each folder being hard coded into the code.

57
00:03:42,630 --> 00:03:48,030
So in this example, if I just say etsi password, it's going to come back and say, hey, I can't locate

58
00:03:48,030 --> 00:03:51,710
etsi password within images and I can't show you any files.

59
00:03:52,080 --> 00:03:56,520
This may not happen in every web application because sometimes the errors may be hidden, but in this

60
00:03:56,520 --> 00:04:01,390
case the application is coming back and it says, hey, etsi password doesn't exist within the folders

61
00:04:01,390 --> 00:04:02,170
and I'm working with.

62
00:04:02,820 --> 00:04:08,340
So this is a perfect time to actually go ahead and use our trick escape out of the current directories,

63
00:04:08,340 --> 00:04:10,140
our end and fetch for our file.


![[Screenshot From 2025-03-03 16-36-24.png]]
64
00:04:10,620 --> 00:04:14,880
So for example, if we go to download our transaction from this bank site, it's going to actually spit

65
00:04:14,880 --> 00:04:16,850
out a username that's useful.

66
00:04:16,860 --> 00:04:20,810
But as you can see in the request, we don't see the extension of the file that we're downloading.

67
00:04:21,240 --> 00:04:23,610
This could be because the application has a hardcoded.

68
00:04:23,790 --> 00:04:25,500
So we may have to find a way around it.

69
00:04:25,560 --> 00:04:30,330
For this example, we can either, you know, bite on the picture to have this, including the resources.

70
00:04:30,330 --> 00:04:34,590
And sometimes it can actually use a questionmark depending on how the application is coded.

71
00:04:34,830 --> 00:04:39,870
But you have to kind of spend some time and understand how each request is being sent and what kind

72
00:04:39,870 --> 00:04:41,070
of a filtering you're dealing with.

73
00:04:41,310 --> 00:04:43,640
So, again, this doesn't have to always be no bite.

74
00:04:43,650 --> 00:04:46,710
It could also be by adding an invalid character or a question mark.

75
00:04:46,980 --> 00:04:51,540
But it just comes down to how the application works and what are the limitations that you're going against


![[Screenshot From 2025-03-03 16-39-29.png]]
76
00:04:52,770 --> 00:04:58,980
while I the injunction or a question mark may help us get rid of the remainder of the string, that's

77
00:04:58,980 --> 00:04:59,810
not always the case.

78
00:04:59,820 --> 00:04:59,870
We.

79
00:04:59,940 --> 00:05:04,650
Max, you have to deal with other limitations and in some cases, it may be a filtering in place when

80
00:05:04,720 --> 00:05:07,530
a seismic has filtered or taken out of our request.

81
00:05:08,070 --> 00:05:09,810
So let's talk about your coding first.

82
00:05:10,210 --> 00:05:15,150
You are uncowed string is universally accepted by both the Web server and the Web browser.

83
00:05:15,180 --> 00:05:20,070
So in other words, if you provide an application, a YORO and coded string, it would understand how

84
00:05:20,070 --> 00:05:22,140
to deal with it and what to translate it to.

85
00:05:23,040 --> 00:05:28,530
For example, a dot becomes a person to E and its source becomes a percent to F, and the combination

86
00:05:28,530 --> 00:05:32,640
of dot dot slash becomes two percent to eight percent to eight percent to f it's not.

87
00:05:32,640 --> 00:05:38,040
Imagine if you give an application at that stage and the application converts into an empty string.

88
00:05:38,070 --> 00:05:42,540
So in other words, we provide an application at that stage it may actually take it and convert it to

89
00:05:42,540 --> 00:05:43,350
an empty string.

90
00:05:43,500 --> 00:05:48,540
So in other words, it's going to say if you see a dot dot large as a string, ignore it and replace

91
00:05:48,540 --> 00:05:49,230
it with nothing.

92
00:05:49,410 --> 00:05:54,330
So in this case, it means we can go back out of our directory and it doesn't help us to traverse out

93
00:05:54,330 --> 00:05:56,040
in order to get a local file disclosure.

94
00:05:56,070 --> 00:06:00,630
But since the application is looking for a set of strings in a particular order, we can actually mess

95
00:06:00,630 --> 00:06:02,910
with it a little bit until we understand how it works.

96
00:06:03,240 --> 00:06:08,510
In this case, the application looks for two dots and a slash and only that string and replaces that

97
00:06:08,520 --> 00:06:09,060
with nothing.

98
00:06:09,240 --> 00:06:15,210
So if we add a dot in the beginning and a dot stosz at the end of the dot dot stage, it will take down

99
00:06:15,210 --> 00:06:18,130
the middle part and convert it to a star at the end.

100
00:06:18,450 --> 00:06:23,670
We can also just add two additional dots in the beginning and a slash at the end and the application

101
00:06:23,670 --> 00:06:26,420
is going to look at it and only match the thought that started.

102
00:06:26,430 --> 00:06:31,170
It's expecting replace it with nothing, but at the end it would convert our entire string into a dot,

103
00:06:31,170 --> 00:06:34,380
dot, dot and allow us to exploit our vulnerability.

104
00:06:34,590 --> 00:06:37,920
Again, this is all about creativity and understanding how the filtering system works.

105
00:06:38,130 --> 00:06:42,090
But I've seen this in a bunch of applications in the past and it's allowed me to exploit them further.