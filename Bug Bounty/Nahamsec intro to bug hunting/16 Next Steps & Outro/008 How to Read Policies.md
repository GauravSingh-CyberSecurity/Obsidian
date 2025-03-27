













---

# Transcript :

1
00:00:00,390 --> 00:00:06,540
Understanding the scope is a big part of it, Bug bounty journey, so if you're going to call one, this

2
00:00:06,540 --> 00:00:08,430
is what a typical program will look like.

3
00:00:08,710 --> 00:00:11,590
I'm going to walk you through it and kind of explain what everything means.

4
00:00:12,060 --> 00:00:15,080
Also, if you're doing this and other Bargmann your platform, it would look different.

5
00:00:15,090 --> 00:00:16,740
But most of these are going to be the same.

6
00:00:17,070 --> 00:00:19,260
They're going to explore the same stuff over and over.

7
00:00:19,440 --> 00:00:24,150
I want to make sure I walk you all through this and kind of make sense of all of this and show you what

8
00:00:24,150 --> 00:00:24,750
everything means.

9
00:00:25,050 --> 00:00:26,760
So the first thing you're going to see is the reward.

10
00:00:26,760 --> 00:00:27,630
In this case.

11
00:00:27,960 --> 00:00:30,240
This company offers one hundred dollars for low.

12
00:00:30,510 --> 00:00:35,940
Medium is a thousand highest, twenty five hundred dollars and critical bucks are paid out of five thousand.

13
00:00:36,240 --> 00:00:37,910
In some cases, this could be the minimum.

14
00:00:37,920 --> 00:00:38,950
This could be the maximum.

15
00:00:39,180 --> 00:00:41,880
Some programs explain that, some programs that you way.

16
00:00:42,180 --> 00:00:45,390
But in most cases, I assume this is the maximum amount I'm going to get.

17
00:00:45,750 --> 00:00:48,870
In most cases, I assume this is the maximum amount I'm going to get paid.

18
00:00:49,140 --> 00:00:54,810
And if I land in a medium or high, I assume that there will pay me somewhere between a thousand to

19
00:00:54,810 --> 00:01:01,050
twenty five hundred dollars for a medium and somewhere between 2500 to 5000 for something else high,

20
00:01:01,290 --> 00:01:03,830
depending on the criticality and the vulnerability type.

21
00:01:04,170 --> 00:01:09,540
But again, there is no way of knowing some programs, a better job of explaining this versus some other

22
00:01:09,540 --> 00:01:10,230
programs.

23
00:01:10,470 --> 00:01:16,260
They would vaguely like this so that this you know what to expect when you report about the next thing

24
00:01:16,260 --> 00:01:17,340
is looking at the policy.

25
00:01:17,610 --> 00:01:22,080
This is where you should be very carefully understand what kind of vulnerabilities they're looking for,

26
00:01:22,320 --> 00:01:24,630
what's in scope, what is the disclosure policy.

27
00:01:24,900 --> 00:01:26,610
And I'll explain what that means in a sec.

28
00:01:26,850 --> 00:01:31,350
What are the exclusion, what kind of vulnerabilities they don't want and also safe harbor, meaning

29
00:01:31,350 --> 00:01:34,410
that they're not going to sue you or anything like that if you find a vulnerability.

30
00:01:34,740 --> 00:01:36,180
So let's talk about the disclosure policy.

31
00:01:36,480 --> 00:01:41,730
You should always assume that your submission that you're saying to this program isn't going to get

32
00:01:41,730 --> 00:01:47,640
publicly disclosed unless they've have explicitly given you a written confirmation that you can blog

33
00:01:47,640 --> 00:01:49,320
about this within your report.

34
00:01:49,350 --> 00:01:53,130
So, in other words, if you're writing a report and then later on you decide that you want to publish

35
00:01:53,130 --> 00:01:56,790
it, make a comment, ask them, hey, are you OK with me publishing this?

36
00:01:56,790 --> 00:02:01,950
If I redact some of the sensitive information that's internal or whatever and giving them a chance to

37
00:02:01,950 --> 00:02:06,930
review it before you publish it, but I always assume not to know until I hear back from them or on

38
00:02:06,930 --> 00:02:12,480
this, if I go to their program and I see that, yeah, they're allowing disclosure to other people.

39
00:02:12,480 --> 00:02:15,140
So maybe they can also disclose my book, The Exclusion.

40
00:02:15,150 --> 00:02:20,130
Again, I expressed earlier briefly, it's very important to understand what vulnerabilities are excluded.

41
00:02:20,340 --> 00:02:24,020
In some cases, some companies may not want to temporarily pay for access.

42
00:02:24,270 --> 00:02:28,830
So you want to make sure you read this so you're not wasting your time looking for vulnerabilities that

43
00:02:28,830 --> 00:02:31,620
are invaluable to the customer or to the program.

44
00:02:31,830 --> 00:02:34,290
And you're not getting paid to scroll down again.

45
00:02:34,890 --> 00:02:36,180
The bottom, you can see the scope.

46
00:02:36,180 --> 00:02:41,820
This is where the company tells you what's in scope, what's critical, what is out of scope and what

47
00:02:41,820 --> 00:02:42,690
you can get paid for.

48
00:02:42,730 --> 00:02:44,700
So let's walk through this really quickly.

49
00:02:45,000 --> 00:02:50,310
If a domain says stardate domain dot com, in this case, it's starting to harm dot com.

50
00:02:50,550 --> 00:02:55,890
That means that every single subdomain, everything that comes behind the home store dot com is in scope

51
00:02:56,190 --> 00:02:58,830
and they're going to give you a max payment of criticality.

52
00:02:59,110 --> 00:03:04,860
So that means if you find a critical bug, the highest bounty you will get as whatever it's in the critical

53
00:03:04,860 --> 00:03:10,770
bucket and that it's eligible for Boundy so you can park on it versus if we look at the marketing site

54
00:03:10,770 --> 00:03:12,690
right here, it shows that it's a high.

55
00:03:12,690 --> 00:03:17,850
It's not critical so that we can assume that here they're only going to pay you a maximum of high,

56
00:03:17,850 --> 00:03:20,610
which is twenty five hundred dollars per of vulnerability.

57
00:03:20,910 --> 00:03:25,950
This is because some of these sites may not actually have any sensitive information, any user data,

58
00:03:26,190 --> 00:03:28,620
but they still want to know if there are any vulnerabilities.

59
00:03:28,980 --> 00:03:33,330
And last but not least out of scope, it's very important to understand this means that whatever domain

60
00:03:33,330 --> 00:03:35,130
is in here do not hack on it.

61
00:03:35,340 --> 00:03:39,660
If you come up with a vulnerability on accident that even though, hey, it was an accident, I didn't

62
00:03:39,660 --> 00:03:43,710
mean to hack on this thing, but I figured I'd report it to you so you can fix it.

63
00:03:44,070 --> 00:03:50,400
Or you can always ask the program managers or the support hacker one dot com email address whether or

64
00:03:50,400 --> 00:03:53,520
not a customer will be OK with your reporting of vulnerability on this.

65
00:03:53,520 --> 00:03:56,760
To me personally, I never got out of a scope domain on this.

66
00:03:56,760 --> 00:04:00,480
I know that the program is going to be OK with me hacking on that domain.

67
00:04:00,480 --> 00:04:04,320
So if we see something out of scope, stay away from it and you'll be OK.

68
00:04:04,500 --> 00:04:10,650
There are also a few other metrics here that are very, very important to hackers and bug bounty hunters.

69
00:04:10,650 --> 00:04:13,980
I look at this as an indication of whether or not I want to hack on a program.

70
00:04:14,310 --> 00:04:18,990
So for this case, since this is a brand new program, you can see that there is no numbers here.

71
00:04:18,990 --> 00:04:21,300
But I'm going to walk you through it and tell you what everything means.

72
00:04:21,660 --> 00:04:23,130
So average time to first response.

73
00:04:23,490 --> 00:04:26,130
This is how long it takes him to respond to your vulnerability.

74
00:04:26,370 --> 00:04:27,810
The lower the number, the better.

75
00:04:28,440 --> 00:04:34,080
Average time to charge just means the average time that it takes them to validate your vulnerability,

76
00:04:34,350 --> 00:04:35,820
which is also the lower the better.

77
00:04:35,970 --> 00:04:38,460
But you want to make sure these two numbers aren't too far apart.

78
00:04:38,700 --> 00:04:44,370
So if it's a few days apart, you know, personally, I may question it, but in a lot of cases, those

79
00:04:44,370 --> 00:04:47,460
two are really, really, really close and average time to bounty.

80
00:04:47,460 --> 00:04:51,210
This is very important if you're looking to just strictly make money off of bug bounties.

81
00:04:51,510 --> 00:04:56,100
I usually don't care about this unless it's some outrageous number, but this is how long it takes them

82
00:04:56,100 --> 00:04:58,470
typically to pay you for your vulnerability.

83
00:04:59,130 --> 00:04:59,790
Average time.

84
00:04:59,850 --> 00:05:04,650
A resolution, this means this is how long it takes him to fix a vulnerability, and that indicates

85
00:05:04,650 --> 00:05:10,680
how long you have to wait until you may be able to disclose your buck and down here.

86
00:05:10,710 --> 00:05:13,980
This is really, really important to look at, especially if you're looking for more recent bug bounty

87
00:05:13,980 --> 00:05:16,290
programs that shows how much they have paid.

88
00:05:16,530 --> 00:05:18,240
This shows how much the average bounty is.

89
00:05:18,360 --> 00:05:19,350
The higher here, the better.

90
00:05:19,350 --> 00:05:21,000
That means they're paying you a lot more.

91
00:05:21,180 --> 00:05:26,520
And you can also see how much are the bug program investing in the program.

92
00:05:26,520 --> 00:05:28,100
And also the top bounty is very important.

93
00:05:28,120 --> 00:05:32,370
This shows what is the highest bounty they have paid to a bug bounty hunter.

94
00:05:32,400 --> 00:05:37,920
So if you see here is a 7500 dollars and the critical bucket shows five, that means that they are willing

95
00:05:37,920 --> 00:05:38,490
to pay more.

96
00:05:38,500 --> 00:05:40,500
If you find something really, really juicy, good.

97
00:05:40,530 --> 00:05:44,240
And of course, there is a 90 days that tells you how active this program is.

98
00:05:44,250 --> 00:05:49,950
If he shows a really large number up here, you can assume that they're pushing code regularly, making

99
00:05:49,950 --> 00:05:54,810
code changes, pushing new functionality, creating new subdomains, whatever that is in the last 90

100
00:05:54,810 --> 00:05:55,050
days.

101
00:05:55,050 --> 00:05:57,890
And hackers are hacking on him actively and they're paying.

102
00:05:58,230 --> 00:06:00,580
And also, you can see how active hackers are after is.

103
00:06:00,870 --> 00:06:02,970
Five hundred reports here in the last 90 days.

104
00:06:03,000 --> 00:06:07,740
It could indicate that there is a lot of activity on this program and you can choose to whether or not

105
00:06:07,740 --> 00:06:10,410
if you want to participate, there is a this doesn't really matter.

106
00:06:10,530 --> 00:06:14,970
Hackers think it's good to know how many hackers are looking at this report, as I was under the monitor,

107
00:06:15,180 --> 00:06:19,110
but just shows you how vulnerable this targeted, which it could be a good or a bad thing.

108
00:06:19,320 --> 00:06:23,940
Good, because it may mean that there are more bugs out there, not because all the other bugs could

109
00:06:23,940 --> 00:06:24,440
be found.

110
00:06:24,630 --> 00:06:29,130
I personally don't believe that all the other bugs have been found because I know that most companies

111
00:06:29,130 --> 00:06:32,460
have a process where they push code out every few weeks.

112
00:06:32,670 --> 00:06:35,700
They make changes regularly and new functionality comes in to the website.

113
00:06:36,030 --> 00:06:39,930
So I don't really pay attention to this and also to the top hackers.

114
00:06:39,930 --> 00:06:41,340
I don't really care to look at this.

115
00:06:41,550 --> 00:06:44,850
It's good to see what other hackers are hacking on and look at all the lists of hackers.

116
00:06:45,120 --> 00:06:47,310
But in this case, it doesn't really matter.

117
00:06:47,310 --> 00:06:51,270
I kind of ignore it, but it's good to know, OK, you know, if our friends are hacking on this program,

118
00:06:51,450 --> 00:06:55,440
I could reach out to them and collaborate with them and learn from them and kind of, you know, have

119
00:06:55,440 --> 00:06:56,210
something to work with.

120
00:06:56,370 --> 00:06:58,020
So it's kind live like on your program.

121
00:06:58,020 --> 00:07:01,170
This is how I want to go about my program and see all the different styles.

122
00:07:01,170 --> 00:07:03,310
I take seven hours to respond.

123
00:07:03,600 --> 00:07:09,180
It takes one day for hacker, one to charge twenty seven days to bounty and twenty four days time to

124
00:07:09,180 --> 00:07:09,840
resolution.

125
00:07:10,140 --> 00:07:14,820
You can also see that the highest bounty pay is 20000, which right here is just 15 k.

126
00:07:14,830 --> 00:07:18,750
So that means if something really, really good has been found there will bump that 15 K to a little

127
00:07:18,750 --> 00:07:19,320
bit higher.

128
00:07:19,590 --> 00:07:22,190
You can also see how much I've paid in the last 90 days.

129
00:07:22,230 --> 00:07:26,910
And when was the last report I was resolved on their Bargnani program and also scroll down and see who

130
00:07:26,910 --> 00:07:28,020
the top hackers are.

131
00:07:28,440 --> 00:07:32,190
And if we go all the way down, you can look at some of the ways that you can get access to some of

132
00:07:32,190 --> 00:07:33,570
these other different programs.

133
00:07:33,870 --> 00:07:40,020
You can look at consequences of complying with the policy, also scope, exclusion of things that are

134
00:07:40,020 --> 00:07:43,060
out of scope or not relevant to their bug bounty program.

135
00:07:43,770 --> 00:07:48,430
And again, as I talked earlier, the scope, as far as you can see, how one is in scope, appears

136
00:07:48,450 --> 00:07:48,990
in scope.

137
00:07:49,110 --> 00:07:50,940
Start of the hacker, one dot net.

138
00:07:50,940 --> 00:07:56,250
So anything behind VPN on hacker, one dot net is in scope and scale all the way down, supporters out

139
00:07:56,250 --> 00:07:59,100
of scope because it's a third party website not operated by them.

140
00:07:59,370 --> 00:08:01,590
And all these other different ones are also out of scope.

141
00:08:01,590 --> 00:08:03,360
So that tells you, hey, don't hack on these.

142
00:08:03,660 --> 00:08:05,600
These are the only things that we want you to hack on.