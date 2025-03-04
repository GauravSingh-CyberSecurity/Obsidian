Analysis of Blind SQLi lab:- ( http://sqli2.naham.sec:8081/ )

![[Screenshot From 2025-03-04 21-50-55.png]]
click on read more

you get rendered to ( http://sqli2.naham.sec:8081/article?id=2 )

now add ( ' )  http://sqli2.naham.sec:8081/article?id=2'
response:  nothing comes back(no error comes back) or nothing changes , the article is still the same 
![[Screenshot From 2025-03-04 21-52-05.png]]


This one's a little bit tricky because we're going to have to rely on a little bit of a deeper understanding of this application.

So let's go back to my examples.
Home page one.

Right Click on the source.

We're going to look for more places where there are different parameters.
So in this case, we have article ID =2


That's where we had our previous sql injection and that's how we load the articles that are within
the database.


---

1
00:00:00,060 --> 00:00:05,250
So, for example, now we're going to look for a blind sequel injection, so in this case, we're going

2
00:00:05,250 --> 00:00:10,410
to click read more, we're going to give it a single comment.

3
00:00:10,420 --> 00:00:11,360
Nothing comes back.

4
00:00:11,790 --> 00:00:17,130
This one's a little bit tricky because we're going to have to rely on a little bit of a deeper understanding

5
00:00:17,130 --> 00:00:17,920
of this application.

6
00:00:17,940 --> 00:00:19,140
So let's go back to my examples.

7
00:00:19,140 --> 00:00:20,240
Home page one.

8
00:00:20,340 --> 00:00:20,610
Right.

9
00:00:20,610 --> 00:00:21,630
Click on the source.

10
00:00:21,990 --> 00:00:25,720
We're going to look for more places where there are different parameters.

11
00:00:25,740 --> 00:00:28,110
So in this case, we have article ID equals one.

12
00:00:28,410 --> 00:00:33,900
That's where we had our previous equal injection and that's how we load the articles that are within

13
00:00:33,900 --> 00:00:34,620
the database.

14
00:00:35,100 --> 00:00:41,070
But at the bottom, there's also this function that says, hey, you can actually get article accounts

15
00:00:41,820 --> 00:00:42,810
within the database.

16
00:00:42,810 --> 00:00:49,110
So if we put in the month that we want from this case, we're going to look for December 2020.

17
00:00:49,950 --> 00:00:55,280
That's going to say, hey, there are zero articles in there where we know in May there were two articles.

18
00:00:55,280 --> 00:00:57,260
So we're going to switch this December for me.

19
00:00:57,600 --> 00:01:00,870
And of course, it's going to come back and say, hey, I may have two articles.

20
00:01:01,200 --> 00:01:06,150
And we can confirm that by going to the Web page and seeing one and two articles that were published

21
00:01:06,270 --> 00:01:07,430
within the month of May.

22
00:01:08,820 --> 00:01:12,710
So I want to check and see if this is vulnerable to a single injection.

23
00:01:13,230 --> 00:01:19,380
So the first thing we do is we give a usual apostrophe or a single quote, comes back and says, hey,

24
00:01:19,420 --> 00:01:22,350
nothing there, give it another one right here, OK?

25
00:01:22,380 --> 00:01:23,490
It's not really doing much.

26
00:01:24,150 --> 00:01:28,420
We're still not sure if there is a vulnerability here, but we're going to keep playing with it.

27
00:01:28,500 --> 00:01:30,270
So what if we add on at the end?

28
00:01:30,630 --> 00:01:36,210
We just again, we have to think about my sequel injections as you are ending the previous query and

29
00:01:36,210 --> 00:01:37,180
you're starting your own show.

30
00:01:37,200 --> 00:01:38,280
What if I drew two of them?

31
00:01:38,580 --> 00:01:39,990
So I close the previous one.

32
00:01:40,300 --> 00:01:41,700
There's a dangling one at the end.

33
00:01:41,940 --> 00:01:43,050
I want to close it.

34
00:01:43,410 --> 00:01:44,400
Still nothing.

35
00:01:44,790 --> 00:01:52,020
But if we do one and we comment out the rest so nothing works again with my second injection, it's

36
00:01:52,020 --> 00:01:52,890
a very, very weird.

37
00:01:52,920 --> 00:01:57,510
You have to spend some time to see how the application reacts to whatever you're giving it.

38
00:01:57,810 --> 00:02:02,310
So looking at the sequel injection here, the only thing we can rely on is whatever value comes back

39
00:02:02,310 --> 00:02:06,790
from the database for the number of optical counts within this month.

40
00:02:06,810 --> 00:02:11,490
So if we give out something invalid, it's going to come back and say zero because it doesn't understand

41
00:02:11,490 --> 00:02:15,930
why May 20, May 20, 20 apostrophe means so.

42
00:02:15,930 --> 00:02:20,940
We want to make sure that we play with this query until I understand how it's getting executed.

43
00:02:21,360 --> 00:02:27,390
So in this case, it's doing some sort of a selecting and saying, hey, do this thing where the month

44
00:02:27,390 --> 00:02:29,390
equals to May of twenty twenty.

45
00:02:29,400 --> 00:02:33,450
And then again, if you're having problems with the statements, just go ahead and look at the slides

46
00:02:33,450 --> 00:02:37,730
again where we looked at what it looks like when you give it an ID or some value here.

47
00:02:38,040 --> 00:02:40,050
Where does that go on this case?

48
00:02:40,440 --> 00:02:45,990
At this point, we're just playing a guessing game and the only way to verify it is by actually giving

49
00:02:45,990 --> 00:02:46,910
it a math expression.

50
00:02:46,920 --> 00:02:50,790
So, again, we don't know if we're doing this right or not.

51
00:02:51,090 --> 00:02:56,070
We know that there are some errors and some weird behaviors happening when we give it a single quote.

52
00:02:56,370 --> 00:03:01,620
But now we have to figure out a way to get a true statement in there, get this county go back up to

53
00:03:01,620 --> 00:03:06,240
two, because that's the only way we know there is actual vulnerabilities.

54
00:03:06,240 --> 00:03:10,170
And that's what the actual correct quarter would look like.

55
00:03:10,770 --> 00:03:14,250
Correct query would give us two, which is a number of articles in May.

56
00:03:14,250 --> 00:03:14,930
Twenty twenty.

57
00:03:15,480 --> 00:03:18,960
So what happens if we start putting the single quotes in different areas?

58
00:03:19,260 --> 00:03:21,120
Again, I don't know how this back end works.

59
00:03:21,420 --> 00:03:23,690
I want to break it apart if I put one there.

60
00:03:23,940 --> 00:03:28,620
Now, what we're doing here is we're saying, hey, apostrophe right here, it's going to I'm going

61
00:03:28,620 --> 00:03:29,580
to convert it back.

62
00:03:29,920 --> 00:03:30,960
There's a space there.

63
00:03:31,290 --> 00:03:34,100
That's a space and that's an apostrophe.

64
00:03:34,140 --> 00:03:39,750
So what's happening with our query here is again, there is the value, whatever we are paid for, May

65
00:03:39,750 --> 00:03:44,810
20, 20 is being put into single quotes like this.

66
00:03:45,420 --> 00:03:51,660
So if we were to close it out with a single one, so if we put one here, this is the expression that's

67
00:03:51,660 --> 00:03:52,680
being run in the back end.

68
00:03:52,800 --> 00:03:57,210
If I add a single quote here, we still have this remaining one, right?

69
00:03:57,540 --> 00:03:59,250
Because in the back end, it's hard coded.

70
00:03:59,250 --> 00:04:00,930
It's always going to have it at the end.

71
00:04:01,230 --> 00:04:02,920
So we have to somehow close it up.

72
00:04:03,930 --> 00:04:06,480
So what we can do here is we're going to do the math expression.

73
00:04:06,780 --> 00:04:11,030
We already know that this works and we're going to say, hey, I already know that there's going to

74
00:04:11,040 --> 00:04:14,370
it's going to add an apostrophe to the end of my career no matter what.

75
00:04:14,670 --> 00:04:16,140
I can try commenting it out.

76
00:04:16,500 --> 00:04:17,940
That may give me the right answer.

77
00:04:18,270 --> 00:04:24,420
But what we can also do is we can just simply put a single quote somewhere in there of our own, where,

78
00:04:26,070 --> 00:04:32,340
again, I put on a single call to make sure that, hey, I want you to use the leftover apostrophe from

79
00:04:32,340 --> 00:04:34,970
the previous query by closing my statements.

80
00:04:34,970 --> 00:04:36,900
So we're saying, hey, I want you to evaluate this.

81
00:04:37,170 --> 00:04:39,270
There's already a hardcoded one in there that we don't see.

82
00:04:39,570 --> 00:04:43,770
And then I also want you to do and one equals to one and give me some data.

83
00:04:43,890 --> 00:04:47,700
I can also verify that this actually works by giving it an invalid math equation.

84
00:04:48,090 --> 00:04:51,000
So if we do one over one of the two, it comes back again with the two.

85
00:04:51,450 --> 00:04:56,010
The sequel is kind of working, but maybe our apostrophe is then put into the right place.

86
00:04:56,250 --> 00:04:59,910
Let's go back and we're going to keep it as one equals.

87
00:05:00,000 --> 00:05:06,220
The because we want to get involved, Querrey, but we're going to move our apostrophe over to after

88
00:05:06,220 --> 00:05:07,300
the equals sign.

89
00:05:08,380 --> 00:05:14,920
Now you're seeing that the application is coming by with the count zero because maybe the expression

90
00:05:14,920 --> 00:05:18,550
that we give it mouth, the expression we've given it for one equal two is invalid.

91
00:05:19,030 --> 00:05:22,900
But if it's if we give it, one equals to one and it comes back with two.

92
00:05:22,910 --> 00:05:26,950
So that means it's evaluating in our math expression, one equals one is true.

93
00:05:27,220 --> 00:05:29,380
And that means we have a proper SQL injection.

94
00:05:29,900 --> 00:05:36,430
Any time you're looking for a second injection, you have to account for the number of characters that

95
00:05:36,430 --> 00:05:41,450
may be left over because of the hard coded query that's being run by the application.

96
00:05:41,710 --> 00:05:45,160
So, again, because we don't see any errors, we don't know where we're putting our expression.

97
00:05:45,370 --> 00:05:46,840
We're always playing a guessing game.

98
00:05:47,050 --> 00:05:53,750
But we have to understand how a secretary looks like and how we should close that or how we play around

99
00:05:53,750 --> 00:05:58,710
the leftover characters that may be there because we're injecting our own expression.

100
00:06:00,430 --> 00:06:05,850
So now that we have the working payload can then be replaced with an apostrophe there.

101
00:06:06,240 --> 00:06:07,390
We have a space there.

102
00:06:11,330 --> 00:06:14,190
Was based there an apostrophe there?

103
00:06:14,210 --> 00:06:20,420
So this is the query that we have and we've proven that it works and I give it an invalid one.

104
00:06:23,470 --> 00:06:27,220
It was like a zero cool, now it works, there is something here.

105
00:06:27,570 --> 00:06:29,410
Now, where is the fun part here?

106
00:06:29,430 --> 00:06:31,070
A lot of people rely on tools.

107
00:06:31,710 --> 00:06:33,680
It's great if you know how to use these tools.

108
00:06:33,690 --> 00:06:35,220
If you understand how they work, great.

109
00:06:35,570 --> 00:06:36,840
That's awesome to use tools.

110
00:06:37,200 --> 00:06:43,590
But for the sake of this cause, I'm going to show how we can extract data by actually using some techniques

111
00:06:43,590 --> 00:06:44,630
with sequel's.

112
00:06:44,640 --> 00:06:48,630
I have built in functions to kind of get the MySQL version.

113
00:06:48,780 --> 00:06:52,500
You can also use similar approaches to this one to extract data.

114
00:06:52,710 --> 00:06:58,650
I'll make sure I can link some stuff into the resources section of this chapter to make sure you have

115
00:06:58,650 --> 00:07:03,500
access to additional ways of extracting data when it comes down to a single injection.

116
00:07:03,990 --> 00:07:08,820
But for this case, what we're going to do is we're going to inject ourselves in the middle of these

117
00:07:08,820 --> 00:07:09,380
two quarters.

118
00:07:09,460 --> 00:07:12,780
Someone actually open up a notepad and copy this in.

119
00:07:15,850 --> 00:07:20,110
So we can kind of evaluate what does this actually look like, what is this square that we're running

120
00:07:20,110 --> 00:07:23,450
every time and try and make some make some sense out of it?

121
00:07:30,860 --> 00:07:37,670
So as we talked about an hour doing outside the annex mission here, key word, and what it's going

122
00:07:37,670 --> 00:07:42,620
to say is, hey, I want you to whatever you were running before it, I also want you to do this so

123
00:07:42,620 --> 00:07:46,410
and means, hey, also run this next query and the next graphic.

124
00:07:46,910 --> 00:07:49,330
Where are we going to do is we're going to inject ourselves right here.

125
00:07:49,340 --> 00:07:55,460
We're going to another and and we're going to write a query where it tells us what is the version of

126
00:07:55,700 --> 00:07:59,860
my school based on our brute force of guessing the version.

127
00:08:00,140 --> 00:08:01,820
And this is something that I covered in the slides.

128
00:08:02,180 --> 00:08:05,270
We're going to use substring and what substring does.

129
00:08:05,270 --> 00:08:11,520
It looks at the value of a particular string and it tells you what the first value is.

130
00:08:11,520 --> 00:08:15,910
Second value as or the third one is what version is actually built into my circle.

131
00:08:16,220 --> 00:08:20,080
It gives us the version of the single database that we're using.

132
00:08:20,090 --> 00:08:21,440
And this is again from my school.

133
00:08:21,770 --> 00:08:26,900
There are different functions and different ways of doing this for other database types.

134
00:08:27,170 --> 00:08:29,920
And we're going to look for the first position one.

135
00:08:30,080 --> 00:08:32,990
Again, this is, as I said, the ninth to the starting position.

136
00:08:32,990 --> 00:08:37,090
And this is the position where you want to pull the data from.

137
00:08:37,550 --> 00:08:43,380
So we're going to set this to five and we're going to say, hey, here's version of this MySQL back

138
00:08:43,400 --> 00:08:46,250
end version five, something I copy this in.

139
00:08:51,700 --> 00:08:56,720
That comes back as to who can also verify by changing it to four, because we can change it to one,

140
00:08:56,730 --> 00:08:59,410
you know, it's invalid and that comes back at zero.

141
00:08:59,730 --> 00:09:05,940
So what's happening here in this case is the my school back in is running this dysfunction and it's

142
00:09:05,940 --> 00:09:09,390
coming back as five point something, something.

143
00:09:09,690 --> 00:09:16,920
And the substring is looking at the first value of that version and saying, hey, is this Querrey true?

144
00:09:17,710 --> 00:09:19,140
Is it starting with a five?

145
00:09:19,140 --> 00:09:23,120
And if it is starting with a five, then show that nothing is wrong.

146
00:09:23,130 --> 00:09:27,000
But when we do one, because it starts with a five, it's going to say, no, that's not true.

147
00:09:27,270 --> 00:09:30,180
It's going to give back to zero because there's some sort of error there.

148
00:09:30,420 --> 00:09:32,550
But we can't figure out what it is just yet.

149
00:09:32,980 --> 00:09:35,730
You can do this and you can do this a number of different ways.

150
00:09:35,730 --> 00:09:38,910
Again, with Fogbound, you want to just show up portability.

151
00:09:39,210 --> 00:09:43,200
You can also show impact by accessing actual data depending on the program you're hiking on.

152
00:09:43,560 --> 00:09:48,340
But a lot of cases showing this is good enough to kind of show that there is a sequel injection there.

153
00:09:48,360 --> 00:09:49,290
There is impact.

154
00:09:49,290 --> 00:09:51,420
You were actually able to extract data and so on.

155
00:09:51,930 --> 00:09:54,330
Again, there are other ways you can extract other data.

156
00:09:54,330 --> 00:09:57,600
You can actually table names, call them names, usernames and so on.

157
00:09:57,970 --> 00:10:02,970
Most people either do this manually by writing really long queries or you can actually do this using

158
00:10:02,970 --> 00:10:06,030
tools like school map, which we're going to look at in just a sec.