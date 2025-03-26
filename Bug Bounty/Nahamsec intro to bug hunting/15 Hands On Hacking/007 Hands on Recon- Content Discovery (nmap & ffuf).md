

### . Run Nmap to Scan the Subdomains

Use Nmap with the `-iL` option (to specify an input file with hostnames) and the `-p` option (to define the port list):

```
nmap -iL subdomains.txt -p 80,443,8000,8443,10000,8080
```

**Explanation:**

- `-iL subdomains.txt`: the list of subdomains from the file. which came from dig, amass, sublister tools 
    
- `-p 80,443,8000,8443,10000`: Scans the specified ports on each subdomain.


**==after finding all the open ports on the list of domains/subdomains**==
==**run FFUF on all of them using desired wordlist to find more stuff.==**

 eg : 
```
 ffuf -w /wordlist   -u http://store.nahamstore.com:8080/FUZZ   -t 100  -ac -c
```

here:  the 8080 is port that was found open so i used FFUF to fuzz and find contents on the port 8080.

---

1
00:00:00,090 --> 00:00:05,550
So one of the things that we talked about in our how you set up your lab was the use of and so we're

2
00:00:05,550 --> 00:00:07,280
going to open up our terminal.

3
00:00:07,530 --> 00:00:09,200
I'm going to do a quick and map.

4
00:00:09,230 --> 00:00:13,920
Before I do, I want to remind you of the subdomains that we have found while we were setting up our

5
00:00:13,920 --> 00:00:14,280
lab.

6
00:00:14,280 --> 00:00:17,950
And this was a list of all the domains that we have came up with.

7
00:00:17,970 --> 00:00:20,430
So what I'm going to do next is I'm going to do the dash.

8
00:00:20,430 --> 00:00:26,970
I this allows us to import a list of domains to map and we're going to give it our file name, which

9
00:00:26,970 --> 00:00:28,020
is the same thing as here.

10
00:00:28,200 --> 00:00:30,200
We're going to tell it what port to scan for us.

11
00:00:30,230 --> 00:00:36,420
So in this case, I'm going to do a small list of ports port eighty four four three eight thousand eighty

12
00:00:36,420 --> 00:00:36,930
eighty.

13
00:00:37,620 --> 00:00:39,570
That's two eight four four three.

14
00:00:39,990 --> 00:00:41,550
And we're going to do 10000 again.

15
00:00:41,550 --> 00:00:46,020
You can do a list of the top ten thousand ports, can give it a range, whatever that works.

16
00:00:46,020 --> 00:00:52,710
But for the sake of this example, all I'm going to do is run an end map for the following ports on

17
00:00:52,710 --> 00:00:53,400
our file.

18
00:00:53,400 --> 00:00:56,760
That includes all of these different assets from the dot com.

19
00:00:56,940 --> 00:01:00,210
As soon as we fire this off, we're going to have to do a port scan.

20
00:01:00,480 --> 00:01:05,730
As we can see here, it's coming back and saying, hey, the shop only has a port area, four for three

21
00:01:05,730 --> 00:01:06,110
open.

22
00:01:06,360 --> 00:01:09,660
I can't tell whether these three are open when I kept moving on.

23
00:01:09,690 --> 00:01:13,770
Same thing here for marketing, but it looks like four, four, three, four.

24
00:01:13,770 --> 00:01:18,720
Marketing is close, but instead we have discovered Port 8000, which we look at in the SEC.

25
00:01:19,190 --> 00:01:20,940
Let's keep going through this port.

26
00:01:20,940 --> 00:01:22,510
Adient four four three are open.

27
00:01:22,520 --> 00:01:23,460
Doors are expected.

28
00:01:23,460 --> 00:01:24,750
Eighty four, four three.

29
00:01:25,050 --> 00:01:26,160
Eighty four for three.

30
00:01:26,430 --> 00:01:31,320
Let's just do one more, one at 22 just to see if there is a SFH available.

31
00:01:32,140 --> 00:01:34,020
And it's like this one is filtered.

32
00:01:34,260 --> 00:01:34,990
That's one is felt.

33
00:01:35,010 --> 00:01:35,490
It doesn't matter.

34
00:01:35,490 --> 00:01:37,440
I just want to do another one just to show how it looks.

35
00:01:37,860 --> 00:01:43,800
But again, we want to make sure that we look for all those additional open ports and they look like

36
00:01:43,800 --> 00:01:46,890
the marketing side had bought 8000 open.

37
00:01:47,210 --> 00:01:52,380
I'm going to pop in here and type in marketing and I'm going to go to the port.

38
00:01:52,380 --> 00:01:54,690
Eight thousand for it so soon as we go here.

39
00:01:54,690 --> 00:01:55,890
It comes up with this page.

40
00:01:56,100 --> 00:01:57,050
There's nothing on there.

41
00:01:57,060 --> 00:02:01,970
We're going to go back to our terminal and we're going to use Fefe.

42
00:02:02,100 --> 00:02:03,350
So we're going to do five.

43
00:02:03,630 --> 00:02:05,970
We're going to use our word from left.

44
00:02:06,210 --> 00:02:07,110
We're going to give it this.

45
00:02:07,110 --> 00:02:09,030
You are all that we got from our port scanned.

46
00:02:09,030 --> 00:02:15,150
We're going to add fuzz because we want to look for files and folders within the Webroot directory and

47
00:02:15,150 --> 00:02:18,600
we're going to give it a number of threads so it goes a little bit faster.

48
00:02:18,600 --> 00:02:21,870
I'm probably going to stop this once I find the thing that I'm looking for.

49
00:02:22,350 --> 00:02:24,720
But let's see, something went wrong here.

50
00:02:25,450 --> 00:02:28,560
Looks like I forgot to give it he w flag for wordlist.

51
00:02:28,920 --> 00:02:34,710
I think that's probably going to actually give it a C so it actually filters and C just to make it a

52
00:02:34,710 --> 00:02:35,430
little bit prettier.

53
00:02:35,790 --> 00:02:40,530
So it looks like right off the bat it's something that's hey, there is a folder called admin that's

54
00:02:40,530 --> 00:02:42,930
going to punch it into the you are allowed just for real quickly.

55
00:02:42,930 --> 00:02:45,170
And that brings us to the marketing manager again.

56
00:02:45,530 --> 00:02:50,610
And if we go to the actual website, when the report is open, we're going to get some of these campaigns.

57
00:02:50,880 --> 00:02:55,230
There's nothing here we can view them in some sort of a preordering interest.

58
00:02:55,560 --> 00:02:57,290
And that's one that says, how do you give away?

59
00:02:57,300 --> 00:02:59,820
So this is the actual site that we see on point eighty.

60
00:03:00,120 --> 00:03:03,980
So it's the site that we will see when we type it in in our browser without any ports.

61
00:03:04,240 --> 00:03:10,170
And if we put in 48 hours, then we come up to an admin interface for next option here is to guess for

62
00:03:10,170 --> 00:03:11,310
a username and password.

63
00:03:11,310 --> 00:03:13,890
It could be things like manager, admin, whatever else.

64
00:03:14,130 --> 00:03:17,880
So we're going to go out and brute force for the admin credentials using Birchfield.

65
00:03:18,210 --> 00:03:24,600
The first thing we're going to do is we want to capture the request sent from our browser.

66
00:03:24,600 --> 00:03:28,320
So we're going to put admin and give it a one, two, three, four or five, six as a password.

67
00:03:28,680 --> 00:03:30,360
And we're going to right click again.

68
00:03:30,360 --> 00:03:31,950
You can do this in the free version.

69
00:03:32,280 --> 00:03:38,100
But when you use free with the community edition, intruder's not going to be as fast, but it's still

70
00:03:38,100 --> 00:03:40,320
available to you and you can still do the same.

71
00:03:40,320 --> 00:03:43,710
So as I'm going to show you right now, we're going to do is we're going to start a position.

72
00:03:43,740 --> 00:03:46,620
This is the position means what do we want to brute force for?

73
00:03:46,980 --> 00:03:50,310
I want to just clear everything and I'm going to highlight the password.

74
00:03:50,580 --> 00:03:55,620
And that means, hey, I want to brute force for this parameter right here and I want to guess the value

75
00:03:56,010 --> 00:03:57,300
and not the user.

76
00:03:57,390 --> 00:03:58,050
You can also do that.

77
00:03:58,050 --> 00:03:59,310
You can say, hey, I want to do both.

78
00:03:59,520 --> 00:04:02,400
But for the sake of this example, I'm just going to do this one right here.

79
00:04:02,940 --> 00:04:05,850
So what are we going to do here is we're going to go to our payloads.

80
00:04:06,090 --> 00:04:09,330
I'm going to do a simple list and we're going to add a few things.

81
00:04:09,330 --> 00:04:10,500
For the sake of this example.

82
00:04:10,500 --> 00:04:13,500
I'm going to keep it short, but I highly recommend looking into password.

83
00:04:13,500 --> 00:04:17,670
We're less on Cycliste or creating your own, but I'm just going to give it a bunch of different ones.

84
00:04:18,930 --> 00:04:23,940
We're going to put one, two, three, four, five admin password.

85
00:04:23,940 --> 00:04:26,100
Twenty, twenty password.

86
00:04:26,100 --> 00:04:27,480
Twenty, twenty one.

87
00:04:28,140 --> 00:04:30,660
One, two, three, four, five, six, eight, nine.

88
00:04:30,780 --> 00:04:31,680
Admin one.

89
00:04:31,680 --> 00:04:32,760
I'm in one, two, three.

90
00:04:33,690 --> 00:04:36,450
So just, let's just show you how it all works.

91
00:04:36,750 --> 00:04:41,010
Now that we have our list here, we can start to attack and see where this goes.

92
00:04:41,850 --> 00:04:47,610
The thing that we're going to look for here is a change in either the status code, the length and see

93
00:04:47,610 --> 00:04:50,120
which ones are not matching as the other ones.

94
00:04:50,250 --> 00:04:55,050
And this is because when we see all of these matching, we're assuming that the password is invalid.

95
00:04:55,050 --> 00:04:58,530
It's going to go to 200 no matter what, because the passwords are involved.

96
00:04:58,530 --> 00:04:59,850
We're getting the same exact result.

97
00:05:00,250 --> 00:05:05,230
So if you were to look at this response would still be in the login page, but right here we can see

98
00:05:05,230 --> 00:05:10,660
that one of them has a different status code and they're linked for it as 295.

99
00:05:10,690 --> 00:05:12,430
And it looks like it's adding some tokens.

100
00:05:12,430 --> 00:05:15,940
So that's like right here there is some sort of a cookie here versus here.

101
00:05:15,950 --> 00:05:19,590
If you look at it, there isn't any cookies because we're not logged in fully.

102
00:05:19,900 --> 00:05:25,390
So it looks like the username and password for this request or for this login is admin admin.

103
00:05:25,630 --> 00:05:27,200
Let's go ahead back into our browser.

104
00:05:27,880 --> 00:05:33,370
We're going to close this off and we're going to type in admin and the password admin.

105
00:05:33,670 --> 00:05:39,580
And as expected, we can see that we are logged in and we have the ability to edit these things.

106
00:05:39,580 --> 00:05:44,440
So just to show that this works right here we are editing the preopening interest.

107
00:05:44,650 --> 00:05:45,700
So this is this article.

108
00:05:45,700 --> 00:05:47,280
I want to open it up just to have it.

109
00:05:47,680 --> 00:05:49,000
And this is a text for it.

110
00:05:49,330 --> 00:05:55,440
All I'm going to do right here is let's just add a payload or something.

111
00:05:55,450 --> 00:06:00,250
We're going to say each one on mouseover equals alert.

112
00:06:00,250 --> 00:06:01,120
One, two, three.

113
00:06:02,140 --> 00:06:03,820
And then we're going to say test one, two, three.

114
00:06:03,820 --> 00:06:10,030
And then when I close my tag and right here I'm going to put in a Comsec was here just to see if this

115
00:06:10,030 --> 00:06:11,800
actually does go to the production website.

116
00:06:11,800 --> 00:06:17,830
As soon as we refresh and it looks like there are some changes being made, our test one, two, three

117
00:06:17,830 --> 00:06:18,810
is added to the top.

118
00:06:19,210 --> 00:06:26,320
And if we go back to the marketing page right here, it looks like the title was also updated with what

119
00:06:26,320 --> 00:06:27,580
put it in the title early on.

120
00:06:27,850 --> 00:06:30,790
The point of this example was to show you what you can do with Rickon.

121
00:06:31,330 --> 00:06:33,830
Finding weak credentials like this is very, very common.

122
00:06:33,880 --> 00:06:38,860
There are times where you can brute force and find a sign up page for the admin panel because the developers

123
00:06:38,860 --> 00:06:40,710
were testing something and they left it behind.

124
00:06:41,020 --> 00:06:47,470
But the point was to show you how you escalate from finding a random open port to finding a credential

125
00:06:47,770 --> 00:06:53,650
and brute forcing for it and getting an access to the back end of that website and making some changes

126
00:06:53,650 --> 00:06:55,420
on the main application.