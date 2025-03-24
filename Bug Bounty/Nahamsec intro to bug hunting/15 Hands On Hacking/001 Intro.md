

1
00:00:00,410 --> 00:00:04,740
Right now that we have covered all of these fires, we know what these vulnerabilities look like, we're

2
00:00:04,740 --> 00:00:09,960
==going to move into our lab area== and I'm going to look at our website, which we have created as an infrastructure

3
00:00:09,960 --> 00:00:10,890
with subdomains.

4
00:00:11,100 --> 00:00:12,510
So require some recon.

5
00:00:12,750 --> 00:00:16,100
And then we're also going to look at a few applications that are on this infrastructure.

6
00:00:16,320 --> 00:00:20,880
And what I'm going to do is I'm going to literally think out loud, tell you what I see, what I would

7
00:00:20,880 --> 00:00:23,340
test for and why or how I would look for it.

8
00:00:23,550 --> 00:00:24,290
Let's jump into it.

9
00:00:24,540 --> 00:00:29,250
So the first thing we're going to do is we're going to open up a terminal one and we're going to use

10
00:00:29,250 --> 00:00:32,260
some of our tools that we covered in the recon slides.




https://merch.nahamsec.com/
![[Screenshot From 2025-03-21 13-23-07.png]]
11
00:00:32,280 --> 00:00:37,560
So the first thing we're going to do is we're going to actually subdomain brute force and look for some
 
12
00:00:37,560 --> 00:00:40,290
of the applications that are on here or the other approaches.

13
00:00:40,290 --> 00:00:44,390
We can just focus on this main domain (https://merch.nahamsec.com/ ), which is the way that we are in the house next door.

14
00:00:44,430 --> 00:00:47,970
If we go to it quickly right now, that's going to bring up the same page.

15
00:00:48,250 --> 00:00:48,930
Let's look around.

![[Screenshot From 2025-03-21 13-25-53.png]]
16
00:00:48,930 --> 00:00:52,260
There's nothing in the source, nothing of interest just yet.
 
17
00:00:52,270 --> 00:00:55,620
There are some JavaScript files that's not hosted on the site itself.

18
00:00:55,950 --> 00:01:01,770
So we can assume that a third party scripts that doesn't really have any functionality within it.

19
00:01:01,780 --> 00:01:03,930
But let's go ahead and look into Google, for example.

20
00:01:03,930 --> 00:01:08,310
The first thing I always do is I'm going to plug in this thing(https://www.nahamsec.com/) into a Google search.  
`site:nahamsec.com`
![[Screenshot From 2025-03-24 14-29-20.png]]

21
00:01:08,310 --> 00:01:13,860
I'm going to say site is this and this is going to bring up some stuff for us to consider is home.

22
00:01:13,860 --> 00:01:18,960
There is product registered, everything in the site, in the home store Dotcom, which is a domain

23
00:01:18,960 --> 00:01:19,700
name we're looking at.

24
00:01:20,190 --> 00:01:21,300
So now we go to register.

25
00:01:21,390 --> 00:01:22,200
It's not there.

26
00:01:23,100 --> 00:01:24,810
Maybe there's a cached version of this.

27
00:01:24,910 --> 00:01:26,670
Let's see, no cash.

28
00:01:27,090 --> 00:01:28,170
This is got the other two.

29
00:01:29,010 --> 00:01:32,290
It looks like something used to be here, but it's unfortunately been removed.

30
00:01:32,610 --> 00:01:36,240
==So what we're going to do is we're going to actually go ahead and do some recon.==
`amass enum -brute -active -d nahamsec.com -p 80,443,8080,8000`  or use 
`amass enum -brute -active -d nahamsec.com -o nahamsec.com.txt -p 80,443,8080,8000`
for adding the results to a txt file 

![[Screenshot From 2025-03-24 14-37-37.png]]

31
00:01:36,430 --> 00:01:40,410
So the first thing we're going to do is we're going to do some subdomain brute focusing on the nahamsec.com



33
00:01:41,220 --> 00:01:42,630
I'm going to do this using amass.

34
00:01:42,630 --> 00:01:47,610
We're going to assume we're going to try to brute force using the domain nahamsec.com .

35
00:01:47,850 --> 00:01:52,650
It's going to like all the outputs in the nahamsec.com, which is let's make a text file actually.

36
00:01:53,460 --> 00:01:56,490
And we're going to give this a Doszpot which supports ganef report.

37
00:01:56,490 --> 00:02:00,000
Eighty four for 388, four for three and eight thousand.

38
00:02:00,330 --> 00:02:02,340
Then you can make this list, you can make it more.

39
00:02:02,340 --> 00:02:07,040
But for the sake of this example, these are the only commands that I'm going to write.

40
00:02:07,170 --> 00:02:10,050
And again, you don't have to use amass if you like other tools.

41
00:02:10,410 --> 00:02:14,080
like subfinder, you want to use sublister or you're more than welcome to.

42
00:02:14,100 --> 00:02:15,360
This is my personal preference.

43
00:02:15,630 --> 00:02:17,820
I was going to run with this for this example.

44
00:02:17,950 --> 00:02:20,100
Again, there are tons of tools out there you can use.

45
00:02:20,310 --> 00:02:24,510
There is no right or wrong way of doing this all comes down to personal preference and what you want

46
00:02:24,510 --> 00:02:24,900
to use.

47
00:02:25,290 --> 00:02:27,840
So it looks like it came back with some data for us.

48
00:02:28,170 --> 00:02:30,600
==It looks like it didn't do the port scan, but that's good.==

==49==
==00:02:30,840 --> 00:02:37,410==
==We can do the additional port scanning with nmap, but for now we have a list of domains that we==

==50==
==00:02:37,410 --> 00:02:37,750==
==can use.==

51
00:02:37,770 --> 00:02:39,390
So these are the domains that he gave us.

52
00:02:39,800 --> 00:02:43,230
I'm going to see if that actually wrote everything to a file.

53
00:02:43,240 --> 00:02:44,040
It looks like it did.

54
00:02:44,070 --> 00:02:46,710
So we have all of this it stored for us.

55
00:02:46,720 --> 00:02:49,460
It's not required to have this, but it's good to have historic data.

56
00:02:49,710 --> 00:02:53,730
So at least we have it written somewhere in case we lose this and want to come back to it.

57
00:02:53,970 --> 00:02:59,430
OK, ==so far we know that the nahamsec Web site has nothing on it, but it doesn't hurt to do a directory==

==58==
==00:02:59,430 --> 00:02:59,880==
==brute force.==

==59==
==00:02:59,880 --> 00:03:05,640==
==We can do this using FFUF and we're going to give it== a 
`sudo ffuf -u https://www.nahamsec.com/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-words.txt`

![[Screenshot From 2025-03-24 14-51-01.png]]

60
00:03:05,640 --> 00:03:11,220
You are also going to grab this because your TPS type send, we're going to happen first.

61
00:03:11,250 --> 00:03:18,240
So this is where it would look for content and we are going to give it a word list.

62
00:03:18,240 --> 00:03:19,530
If you want to use a word list.

63
00:03:19,530 --> 00:03:21,360
I highly recommend looking at seclist.

64
00:03:21,600 --> 00:03:28,770
I'm actually going to pull it up really quick and we're going to look for Cycliste on GitHub and we're

65
00:03:28,770 --> 00:03:33,090
going to download if you of these worthless again, if you don't want to use as Australia OK, you can

66
00:03:33,090 --> 00:03:35,430
actually use whichever one you like.

67
00:03:35,730 --> 00:03:38,370
But this has been a very good place to start for worthless.

68
00:03:38,380 --> 00:03:44,130
And they do have a ton of different ones that have some for DNS to have, some for come in and languages

69
00:03:44,130 --> 00:03:48,330
like Italian, Spanish, Portuguese, or if you're hacking on a Portuguese site to have some common

70
00:03:48,330 --> 00:03:49,080
file names.

71
00:03:49,260 --> 00:03:53,460
The one that I use a lot, it's called the raft rouf large words.

72
00:03:53,460 --> 00:03:59,250
I think this one has some of the best word that we can use for this example.

73
00:03:59,250 --> 00:04:06,390
We're going to just go ahead and just look for a download and we're going to pull this and we're going

74
00:04:06,390 --> 00:04:07,560
to put to our server.

75
00:04:07,590 --> 00:04:15,810
So I'm going to go back here and we're going to create a directory card wordlist going to our list and

76
00:04:15,810 --> 00:04:19,200
we're going to just download this file from GitHub.

77
00:04:19,440 --> 00:04:26,580
And then when it's downloaded, we're going to grab this file name and we're going to run our command

78
00:04:26,580 --> 00:04:32,820
again and we're going to give it the word this we just found and we going to give it about seventy five

79
00:04:32,820 --> 00:04:33,300
threads.

80
00:04:33,810 --> 00:04:35,180
I think that should do it for us.

81
00:04:35,190 --> 00:04:36,690
So right now it's going to brute force.

82
00:04:36,690 --> 00:04:42,030
It's going to look if there are any files or folders on the hamster dotcom, I don't think there is

83
00:04:42,030 --> 00:04:42,720
anything on here.

84
00:04:42,720 --> 00:04:46,230
But we're going to have to do its thing while we look at other websites.

85
00:04:46,380 --> 00:04:49,920
So we're going to scroll up again and look at some of the other sites that we have.

86
00:04:49,930 --> 00:04:54,840
So this there's shop, there's stock marketing and the main site that we already were looking at.

87
00:04:54,840 --> 00:04:56,010
So let's start off with QOF.