
```
FFUF -h
```


eg:
```

ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-words.txt -u https://www.nahamsec.com/FUZZ
```

---


# Transcript :


1
00:00:00,180 --> 00:00:05,250
The first thing we're going to do is we're going to go ahead and look for fluff, fluff is a great father.

2
00:00:05,430 --> 00:00:10,140
Not only can do directly brute forcing with it, but you can use it for other purposes for this case.

3
00:00:10,140 --> 00:00:16,920
We're just going to go ahead and use it for directory brute forcing and filing and finding files that

4
00:00:16,920 --> 00:00:19,160
may be left behind by the developers.

5
00:00:19,590 --> 00:00:22,350
The good thing would go is that the installations are really, really easy.

6
00:00:22,560 --> 00:00:27,750
All you have to do is type in, go get the sheet and give it the get WRAL where it's hosted.

7
00:00:28,150 --> 00:00:30,550
We're going to go back to our machine.

8
00:00:30,570 --> 00:00:37,140
We're going to go get you get out of this stuff and it's going to come back and be installed and wants

9
00:00:37,140 --> 00:00:37,470
to type.

10
00:00:37,470 --> 00:00:39,090
And there it is.

11
00:00:39,300 --> 00:00:41,130
It's ready and we have it set up.

12
00:00:41,970 --> 00:00:48,390
Now, let's have a deeper look at the point of what is to be able to fuzz and look for a particular

13
00:00:48,600 --> 00:00:55,890
asset, like a parameter name or maybe even a file name, the most common way of using stuff that I've

14
00:00:55,890 --> 00:01:04,680
seen from hackers is to actually run far to find the endpoints and folders that may lead into some information

15
00:01:04,860 --> 00:01:06,650
or a way of finding a vulnerability.

16
00:01:06,900 --> 00:01:13,410
If you actually type in stuff that will bring up this how to help center.

17
00:01:14,950 --> 00:01:20,470
If you type in dash, it will bring up to help and it kind of tells you what to do and how to use it.

18
00:01:20,680 --> 00:01:25,150
So if you do a C, for example, it would automatically calibrate filtering options.

19
00:01:26,020 --> 00:01:31,660
So that means you would look at the responses and I would look at the responses and decide whether or

20
00:01:31,660 --> 00:01:32,680
not he wants to use it.

21
00:01:32,980 --> 00:01:34,410
There's a ton of different options here.

22
00:01:34,420 --> 00:01:39,220
You can actually use M.S. to match for what response codes you're looking for.

23
00:01:39,400 --> 00:01:40,480
You can exclude some of them.

24
00:01:40,480 --> 00:01:42,130
You can include the other ones by default.

25
00:01:42,130 --> 00:01:45,730
It looks for two hundred three or one, three or two for one in four or four.

26
00:01:46,010 --> 00:01:50,320
But if you only care about two hundreds, then you can use M.S. to make it happen.

27
00:01:51,100 --> 00:01:55,630
You can also filter, which is F.C. So if you want to filter for three or one and you don't want it

28
00:01:55,630 --> 00:02:01,060
to be included in there, you can do F.C. three or one that won't show anything that comes back has

29
00:02:01,060 --> 00:02:02,890
three or one and so on.

30
00:02:02,900 --> 00:02:04,720
There's a ton of different things you can do with it.

31
00:02:06,130 --> 00:02:13,210
I'm going to I'm going to try and show you the way I use it and just to get some of the basic recon

32
00:02:13,210 --> 00:02:13,450
done.

33
00:02:13,450 --> 00:02:20,560
But again, I highly recommend opening this up, taking a look and understanding how it works and also

34
00:02:20,560 --> 00:02:24,490
understanding the different options and use cases for fun.

35
00:02:24,940 --> 00:02:25,740
Let's jump into it.

36
00:02:25,900 --> 00:02:28,210
The first thing I'm going to do is we want to give it a word list.

37
00:02:28,240 --> 00:02:32,380
So right now, in my word list directory, I want to use the word list raft again.

38
00:02:32,380 --> 00:02:33,850
I downloaded this from Cycliste.

39
00:02:34,000 --> 00:02:36,190
I've linked this before and one of the earlier slides.

40
00:02:36,460 --> 00:02:41,830
But I want to use this and I want to use the Nahoum shop as the home.

41
00:02:43,210 --> 00:02:45,130
Then I want to use a new home store as a target.

42
00:02:45,130 --> 00:02:46,290
So I'm going to give it to you.

43
00:02:46,510 --> 00:02:47,080
That's where you are.

44
00:02:47,080 --> 00:02:49,270
I want to go after which is shoptalk.

45
00:02:49,750 --> 00:02:53,020
Nahum store dotcom and fuzz is where I want to look.

46
00:02:53,030 --> 00:02:58,150
So if I knew a folder existed called Test and I want to look for files within test, then I would put

47
00:02:58,150 --> 00:03:03,930
Serzh test fuzz and it would only look for the files and folders within the directory.

48
00:03:04,120 --> 00:03:06,940
I'm going to give it a dachsie that makes things look a little bit nicer.

49
00:03:07,090 --> 00:03:08,110
You can give us some threads.

50
00:03:08,110 --> 00:03:12,670
I'm not going to for this case and I'm going to clear my screen really quickly and run this as it is.

51
00:03:13,090 --> 00:03:16,030
And as we can see right now, it's making a ton of requests.

52
00:03:16,240 --> 00:03:19,570
It comes back as two hundred with green, meaning that search exist.

53
00:03:19,570 --> 00:03:24,280
And we can confirm this by going to our Google Chrome and typing and slash search.

54
00:03:24,580 --> 00:03:30,220
And that brings up the search page for this website and tells us that, hey, this actually does exist.

55
00:03:30,760 --> 00:03:33,580
And the two of the two hundred that we received is actually there.

56
00:03:33,850 --> 00:03:35,050
Same thing with the three older ones.

57
00:03:35,050 --> 00:03:36,250
We can manually confirm it.

58
00:03:36,250 --> 00:03:39,880
If I go to uploads as they're going to send me to another folder.

59
00:03:40,030 --> 00:03:40,570
It does.

60
00:03:40,570 --> 00:03:41,710
It adds a slash.

61
00:03:41,710 --> 00:03:44,920
It takes as a redirect and it comes back as four or three.

62
00:03:45,430 --> 00:03:50,140
So if I had a, for example, I thought a leading slash at the end of us, then that would have came

63
00:03:50,140 --> 00:03:52,450
back as four or three.

64
00:03:52,690 --> 00:03:55,150
Another one we have found right here is the folder called Stuff.

65
00:03:55,390 --> 00:03:56,590
This is something that may be hidden.

66
00:03:56,590 --> 00:04:02,020
We may not have access to it, but if I type in stuff, it's going to take me to another page right

67
00:04:02,020 --> 00:04:04,460
here, says members only staff member Adam.

68
00:04:04,480 --> 00:04:08,830
And looks like this is supposed to be private, not accessible by anybody else, but unfortunately,

69
00:04:08,830 --> 00:04:12,720
because of how this is when we got access to this particular folder.

70
00:04:13,180 --> 00:04:15,280
So now we can also brute force for other things.

71
00:04:15,280 --> 00:04:17,700
I want to really quickly show the leading slash.

72
00:04:17,710 --> 00:04:22,210
If I do this right now, you can see it comes back with a four or three, but it's missing some of the

73
00:04:22,210 --> 00:04:23,470
other ones like search maybe.

74
00:04:23,470 --> 00:04:23,920
Who knows?

75
00:04:23,920 --> 00:04:28,570
It might find that it may not find it depending on how it's created, but it's very helpful when it

76
00:04:28,570 --> 00:04:30,670
comes to looking for random files and folders.

77
00:04:31,210 --> 00:04:33,220
This is very, very useful.

78
00:04:33,340 --> 00:04:36,460
You can find what's on this server, especially if you have a really good word list.

79
00:04:36,700 --> 00:04:42,850
So I highly recommend getting familiar with using an advantage and reading the Read Me and the Help

80
00:04:42,850 --> 00:04:45,190
page and understanding the other use cases.

81
00:04:45,190 --> 00:04:51,100
But is it a but this is at a basic level of how to use it and how you can find directories and files

82
00:04:51,100 --> 00:04:53,220
on a particular domain or subdomain.