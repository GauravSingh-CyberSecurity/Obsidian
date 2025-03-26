



---

1
00:00:00,210 --> 00:00:06,480
So we're going to look at this product right here, we're going to click are a few things we can mess

2
00:00:06,480 --> 00:00:06,680
with.

3
00:00:06,690 --> 00:00:07,830
There is a name right here.

4
00:00:08,040 --> 00:00:11,270
I kind of suspect an exercise, but I'm going to skip it for now.

5
00:00:11,270 --> 00:00:12,420
That's a little too obvious.

6
00:00:12,690 --> 00:00:15,060
I should definitely poke around and see if we can exploit it.

7
00:00:15,060 --> 00:00:16,320
But there's also a discount code.

8
00:00:16,320 --> 00:00:22,110
When I'm going to do here is I'm going to actually add one, two, three and push enter and we're going

9
00:00:22,110 --> 00:00:25,620
to give it a minute and see what happens when we put in that one, two, three.

10
00:00:26,280 --> 00:00:28,520
So it looks like there's nothing being reflected in the DOM.

11
00:00:28,530 --> 00:00:30,570
What I'm going to do is I'm going to pop up sweet.

12
00:00:30,930 --> 00:00:32,520
We're going to actually take a look at it again.

13
00:00:32,520 --> 00:00:36,510
We're going to add one, two, three checks to see what happens.

14
00:00:37,470 --> 00:00:43,290
Not much there, but funny enough, if we're looking at it, there are some other cool stuff that we

15
00:00:43,290 --> 00:00:43,950
can mess with.

16
00:00:44,370 --> 00:00:46,020
If you look, there is a server here.

17
00:00:46,950 --> 00:00:48,900
It's showing a you oh, we'll talk about that later.

18
00:00:48,900 --> 00:00:51,390
But that screams vulnerability at me.

19
00:00:51,780 --> 00:00:52,890
There's product ID.

20
00:00:52,920 --> 00:00:54,440
I've talked about this in our second version.

21
00:00:54,470 --> 00:00:59,640
Either any time with an integer or a numerical idea, it's a good place to look for vulnerabilities.

22
00:00:59,970 --> 00:01:02,220
When I skip it for now, let it go forward.

23
00:01:02,220 --> 00:01:03,540
It nothing there.

24
00:01:03,540 --> 00:01:05,630
It looks like there are just many in stock.

25
00:01:06,360 --> 00:01:09,750
OK, I'm going to do another one.

26
00:01:10,020 --> 00:01:12,720
It's going to push, enter and see if it looks like it worked.

27
00:01:13,080 --> 00:01:16,140
So right here we can see that there is a few things.

28
00:01:16,740 --> 00:01:19,070
First of all, there isn't actually enough here.

29
00:01:19,080 --> 00:01:25,230
We don't see any CSR after tokens, no Excel token nothing, which is a great indication that we can

30
00:01:25,230 --> 00:01:26,190
exploit this further.

31
00:01:26,190 --> 00:01:31,290
But we can also see that whatever we put in in the discount right here in this box that's being reflected

32
00:01:31,290 --> 00:01:38,130
in to someone to push us to repeat, I did it on my keyboard with control in front of Keys command are

33
00:01:38,280 --> 00:01:38,970
can also right.

34
00:01:38,970 --> 00:01:41,310
Click and send to repeated right here.

35
00:01:41,790 --> 00:01:42,510
I'm going to switch over.

36
00:01:42,510 --> 00:01:43,680
I want to drop this one.

37
00:01:43,680 --> 00:01:44,490
I'm going to repeat her.

38
00:01:44,670 --> 00:01:47,040
We're going to take a look at this in depth.

39
00:01:47,340 --> 00:01:47,970
It's not that we're here.

40
00:01:47,970 --> 00:01:49,530
We're going to send this request one more time.

41
00:01:49,770 --> 00:01:52,650
It's going to take three or two thousand, which is going to redirect us somewhere.

42
00:01:52,980 --> 00:01:53,970
It's just one more time.

43
00:01:54,870 --> 00:01:57,450
I'm going to follow the direction it goes.

44
00:01:57,450 --> 00:02:00,110
One goes, we'll go here and put one, two, three.

45
00:02:00,120 --> 00:02:00,960
Nothing shows up.

46
00:02:01,380 --> 00:02:02,440
There's actually a really cool trick.

47
00:02:02,460 --> 00:02:08,460
A lot of times what developers do is whatever is in the post request right here, you can see right

48
00:02:08,460 --> 00:02:10,350
here, it's sending it in the post.

49
00:02:11,040 --> 00:02:12,510
You can actually copy this.

50
00:02:12,690 --> 00:02:16,830
And this isn't always work, but I've seen it work in a number of different programs, can actually

51
00:02:16,830 --> 00:02:19,830
copy it and make it into a get request.

52
00:02:20,220 --> 00:02:25,080
So you're pretty much sending the same exact request, but instead of using post and taking the data

53
00:02:25,080 --> 00:02:26,400
based on your request.

54
00:02:26,760 --> 00:02:31,650
So again, we're taking whatever this was, the same parameter, same data, we're just adding it to

55
00:02:31,650 --> 00:02:35,400
our get requests instead of using the post body one, two percent.

56
00:02:35,700 --> 00:02:39,060
I just have one more time and we're going two percent.

57
00:02:39,510 --> 00:02:42,610
And then we're going to see if there is one, two, three showing up anywhere in the source.

58
00:02:42,610 --> 00:02:43,530
It looks like it's right here.

59
00:02:43,800 --> 00:02:49,080
It's adding an input and it says a name is discount and value is one, two, three.

60
00:02:49,800 --> 00:02:50,790
We can do two things here.

61
00:02:50,790 --> 00:02:54,150
One, as we can see if we can give it a fake parameter name.

62
00:02:54,150 --> 00:02:55,740
So I'm going to do five, six, six, seven.

63
00:02:57,540 --> 00:03:01,830
I didn't come up so I can go back to discount or we can actually text.

64
00:03:01,830 --> 00:03:08,580
So I'm going to do here is I'm going to add a few are those juicy characters that I know will yield

65
00:03:08,580 --> 00:03:12,150
and some exercise attacked at the end of the protests.

66
00:03:12,150 --> 00:03:12,870
One, two, three.

67
00:03:14,010 --> 00:03:23,220
And as we see here, it looks like it took out our less than it took our less and greater than signs,

68
00:03:23,610 --> 00:03:26,280
but it's keeping the quotes right there.

69
00:03:26,310 --> 00:03:28,320
So we're going to get rid of everything else.

70
00:03:28,320 --> 00:03:29,580
We know what works and what doesn't.

71
00:03:29,580 --> 00:03:30,720
So we're going to get rid of these.

72
00:03:31,710 --> 00:03:35,790
And we know that we are between quotes and we're going to send it.

73
00:03:38,110 --> 00:03:39,410
I'm going to search for it again.

74
00:03:39,930 --> 00:03:45,310
It looks like we have an extra quote, so it looks like the one that we added right here that is ours

75
00:03:45,310 --> 00:03:46,930
because it's before test one, two, three.

76
00:03:47,260 --> 00:03:51,580
And the one that originally was in the application, it came after our test.

77
00:03:51,580 --> 00:03:52,090
One, two, three.

78
00:03:52,120 --> 00:03:55,000
So what I'm going to do here now is same thing as we were doing earlier.

79
00:03:55,030 --> 00:03:58,750
Again, this is why I like to do exercise hunting manually.

80
00:03:58,990 --> 00:04:02,500
If you're a copy pasting payloads, you may miss out on time zones.

81
00:04:02,860 --> 00:04:05,170
But now that we know this works, we're going to add another payload.

82
00:04:05,170 --> 00:04:08,680
We're going to stay on load or on error, whichever one you want to use.

83
00:04:10,150 --> 00:04:18,550
And we're going to unload alert one, two, three, and we're going to close it out.

84
00:04:19,280 --> 00:04:21,880
So it's actually copy this request from right here.

85
00:04:23,590 --> 00:04:24,850
We're going to copy this.

86
00:04:24,880 --> 00:04:26,980
We can actually copy to you earlier if we wanted to.

87
00:04:27,760 --> 00:04:30,510
And we're going to go back to our burb seat or we're going to go back to work.

88
00:04:30,910 --> 00:04:32,170
We're going to go back to our chrom.

89
00:04:32,530 --> 00:04:34,570
I'm going to visit it and see if it works.

90
00:04:34,690 --> 00:04:39,180
So let's make sure we turn proxy off, go back to our browser.

91
00:04:39,360 --> 00:04:40,480
Let's say something broke.

92
00:04:41,060 --> 00:04:45,890
So there's a way this isn't working as because we're telling the browser to do an alert, to perform

93
00:04:45,910 --> 00:04:49,390
an alert for us when there is an error, since there are no errors here.

94
00:04:49,540 --> 00:04:50,980
Of course, this isn't going to work.

95
00:04:51,280 --> 00:04:55,500
But on top of that, the reason why it's not working is because we have too many quotes.

96
00:04:55,510 --> 00:05:00,040
So if you can see why there's one closing in right there and there is one more at the end of it to get.

97
00:05:00,880 --> 00:05:05,520
So let's get rid of our last one right there just to alert with an error.

98
00:05:05,660 --> 00:05:07,480
So not going to work because there is no errors.

99
00:05:07,480 --> 00:05:12,990
But at least now we know this is working out and we can exploit it for it.

100
00:05:13,900 --> 00:05:14,890
So let's go ahead.

101
00:05:14,890 --> 00:05:19,750
And now changes to on mouseover.

102
00:05:20,920 --> 00:05:24,070
If you mouse over it, it's going to pop up with an empty alert.

103
00:05:24,400 --> 00:05:27,250
Again, you can do other things like actually store cookies.

104
00:05:27,580 --> 00:05:28,720
We'll talk about those later.

105
00:05:29,050 --> 00:05:35,830
But for now, I'm going to do documents, dot or document, dot, cookie, and that's going to give

106
00:05:35,830 --> 00:05:37,850
us our cookie as soon as we mouse over it.

107
00:05:38,170 --> 00:05:39,100
That's a great PEOC.

108
00:05:39,100 --> 00:05:40,390
You're showing vulnerability.

109
00:05:40,390 --> 00:05:41,670
You're showing how you can exploit it.

110
00:05:41,680 --> 00:05:44,080
You have a valid possie and it all works out.

111
00:05:44,080 --> 00:05:49,080
And you can just keep this as it is and send it to the program on the receiving end.