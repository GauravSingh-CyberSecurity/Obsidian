
Analysis of SQLi lab:-  (http://sqli.naham.sec:8081/)


![[Screenshot From 2025-03-04 13-11-55 1.png]]

click on read more on first article and see it has an id..
![[Screenshot From 2025-03-04 13-13-25.png]]

input  ( ' )  to test sqli :-  
![[Screenshot From 2025-03-04 13-14-24.png]]
since the error pop up, its " error based sqli " present here.



==test other payloads and see result on the vulnerable endpoint:-==

for payload  "  2-1 "    (both in web and burp)
![[Screenshot From 2025-03-04 13-17-25.png]]
![[Screenshot From 2025-03-04 13-19-22.png]]
we get the article with id=1,  i.e we were able to execute the subtraction command in sql DB of the application and get the result.


that kind of tells us, hey, whatever, I give it to
this application,   its evaluating it for me and giving it back as it's a query, not taking the value,
but it's actually rendering the math expression to minus one and then giving us the value for that article.
And of course, we already knew based on the MySQL error, that there is maybe a SQL injection present here.


Now, ==Lets enumerate number of columns present here :-==
http://sqli.naham.sec:8081/article?id=2%20union%20select%201,2;--         (2 union select 1,2;--)
http://sqli.naham.sec:8081/article?id=2%20union%20select%201,2,3;--      (2 union select 1,2,3;--)
http://sqli.naham.sec:8081/article?id=2%20union%20select%201,2,3,4;--  (2 union select 1,2,3,4;--)

http://sqli.naham.sec:8081/article?id=-2%20union%20select%201,2,3,4;--  (-2 union select 1,2,3,4;--)
![[Screenshot From 2025-03-04 15-04-31.png]]



---

1
00:00:00,360 --> 00:00:03,990
So now let's jump in, for example, when testing for SQL injection, the biggest thing you want to

2
00:00:03,990 --> 00:00:11,380
look for is any abnormalities or errors that may occur based on an invalid character and you would provide

3
00:00:11,380 --> 00:00:12,130
to the application.

4
00:00:12,210 --> 00:00:14,310
This case, we're going to give it a single quote.

5
00:00:15,420 --> 00:00:20,160
The application is going to come back and tell us, hey, there is a error in your mind, SQL Server

6
00:00:20,160 --> 00:00:21,540
version next to this.

7
00:00:21,570 --> 00:00:29,640
So that means that we have added a quote or a single quote next to whatever this expression was.

8
00:00:29,670 --> 00:00:33,040
So what we can do next is we can test this out a number of different ways.

9
00:00:33,060 --> 00:00:38,640
The first way we can test for second injection is just to give it regular expressions and making sure

10
00:00:38,640 --> 00:00:40,320
that it's evaluating and properly.

11
00:00:44,630 --> 00:00:52,120
So as we can see, ID, too, has a title, The Meaning of Life, that was created on 22nd of May 2020

12
00:00:52,580 --> 00:00:54,000
and has some techs attached to it.

13
00:00:54,200 --> 00:00:57,530
We're going to change it to three and we do ID3.

14
00:00:57,810 --> 00:00:59,240
The article is not located.

15
00:00:59,600 --> 00:01:04,190
If we do ID one, the Oracle name becomes how to get started hacking.

16
00:01:04,820 --> 00:01:09,740
And the article was created on the 13th of May in the year 2020.

17
00:01:10,580 --> 00:01:15,830
Now what happens if we tell it to fetch an ID, but instead of using a direct ID number, what if we

18
00:01:15,830 --> 00:01:16,880
give it a math equation?

19
00:01:17,310 --> 00:01:23,180
So if we wanted to have it pfeg ID number one, why don't we give it a math equation that says, hey,

20
00:01:23,510 --> 00:01:27,470
idea number one, but I want to do a math two minus one, which is equal to one.

21
00:01:28,070 --> 00:01:29,010
I want you to fetch that.

22
00:01:29,030 --> 00:01:35,990
So again, if the two minus one, that math expression of to one, which is the same as ID one, so

23
00:01:35,990 --> 00:01:41,360
we get the same content for the both of these, that kind of tells us, hey, whatever, I give it to

24
00:01:41,360 --> 00:01:47,300
this application, evaluating it for me and giving it back as it's a query, not taking the value,

25
00:01:47,300 --> 00:01:53,660
but it's actually rendering the math expression to minus one and then giving us the value for that article.

26
00:01:53,900 --> 00:01:59,570
And of course, we already knew based on the MySQL error, that there is maybe a sequel injection present

27
00:01:59,570 --> 00:01:59,780
here.

28
00:02:00,360 --> 00:02:07,460
So next thing we want to do is we want to enumerate for the number of columns that are available within

29
00:02:07,460 --> 00:02:08,470
this table.

30
00:02:09,140 --> 00:02:12,830
The first thing I'm going to do is we're going to go back here, just want to get a select statement

31
00:02:12,830 --> 00:02:13,250
in there.

32
00:02:13,370 --> 00:02:18,220
As long as we keep getting this error, it means that our query isn't being evaluated properly.

33
00:02:18,740 --> 00:02:20,150
So we're going to play with a little bit.

34
00:02:20,600 --> 00:02:26,870
Maybe we need to do a double quote, maybe a single call by to a comment.

35
00:02:28,310 --> 00:02:29,650
Maybe we don't need anything at all.

36
00:02:29,690 --> 00:02:31,200
We only know there is a sequel injection here.

37
00:02:31,200 --> 00:02:31,420
Right.

38
00:02:31,490 --> 00:02:36,410
So we may not actually need this single quote in there of doesn't work.

39
00:02:37,010 --> 00:02:38,180
Let's remove our comments.

40
00:02:38,570 --> 00:02:43,610
We're still getting some issues, but we try a union select so we do a union select with Arkoma.

41
00:02:44,420 --> 00:02:48,310
So getting an error, what if we ignore everything else?

42
00:02:48,450 --> 00:02:49,580
So we're getting an error.

43
00:02:50,130 --> 00:02:51,410
OK, we're going to remove this.

44
00:02:52,520 --> 00:02:57,150
And now, as you can see, the applications coming back and it's telling us, hey, the select segment

45
00:02:57,150 --> 00:03:00,980
that you've given me has a number of different columns as what I expect.

46
00:03:01,010 --> 00:03:04,550
So this, as we talked about in the slides, we want to make sure we give it the right number.

47
00:03:04,970 --> 00:03:10,060
So we're going to give it number two three, we're going to give it four.

48
00:03:10,970 --> 00:03:15,620
And now, since we're giving it the right number of columns, the application is not giving us any errors.

49
00:03:15,940 --> 00:03:16,760
It's coming back.

50
00:03:17,390 --> 00:03:23,810
It's coming back and giving us the value for it to whatever data it's in there and serving it to us.

51
00:03:24,200 --> 00:03:27,740
But it's still having trouble showing us data based on a select statement.

52
00:03:28,670 --> 00:03:33,110
The reason why it's happening in this case, again, you have to really spend a lot of time understanding

53
00:03:33,110 --> 00:03:33,980
siecle injections.

54
00:03:33,980 --> 00:03:36,140
It all depends on the application, how it's written.

55
00:03:36,650 --> 00:03:41,010
But what you want to do is you want to find a way of serving and valid data.

56
00:03:41,330 --> 00:03:44,660
So what I mean by that is you want to give it an ID that doesn't exist.

57
00:03:44,870 --> 00:03:51,080
Most people like to do negative values because developers don't use negative values when it comes down

58
00:03:51,080 --> 00:03:56,750
to giving an ID number or a numeric ID number to an article or an item within the database.

59
00:03:57,410 --> 00:04:04,910
So as soon as we do this, we give it a as soon as we do this and we give it a negative or invalid value,

60
00:04:05,210 --> 00:04:09,290
it comes back and it actually shows us the stuff that we've put in here for a select statement.

61
00:04:09,320 --> 00:04:13,670
So if I were to do NULL says, you can see it's not showing one for go to the source.

62
00:04:14,270 --> 00:04:14,960
It's the same thing.

63
00:04:14,960 --> 00:04:19,130
We see three, we see two and we have four right here.

64
00:04:19,130 --> 00:04:21,980
Article created for they showed us there is devout.

65
00:04:21,980 --> 00:04:23,320
The fourth value is date.

66
00:04:23,330 --> 00:04:23,920
Let's go back.

67
00:04:23,940 --> 00:04:25,220
The fourth value is date.

68
00:04:25,580 --> 00:04:29,270
The third one is a body and the second one as the title of it.

69
00:04:29,270 --> 00:04:33,430
And obviously the first value is a numerical ID belonging to this article.

70
00:04:34,040 --> 00:04:41,540
So what we're going to do here is we're going to just swap it out and maybe we can look for the version

71
00:04:41,540 --> 00:04:43,190
of MySQL that we're going against.

72
00:04:43,310 --> 00:04:48,710
So, for example, if you are again, if you're going to my school, this is something that exists within

73
00:04:48,710 --> 00:04:49,280
my circle.

74
00:04:49,280 --> 00:04:52,130
It's not a it's something that's built in.

75
00:04:52,370 --> 00:04:55,850
It's not in way of using is just developers use this for information.

76
00:04:56,360 --> 00:05:00,860
You can use it, then we can abuse it in some way to show that there is a sequel injection here and

77
00:05:00,860 --> 00:05:04,250
we were able to retrieve some sort of a data from this database.

78
00:05:05,240 --> 00:05:10,880
So as it comes back and shows us that we are on my second five point seven, thirty two are now going

79
00:05:10,880 --> 00:05:15,830
to eighteen or four point one, it kind of tells us, OK, at the sequel, injection worked.

80
00:05:18,640 --> 00:05:23,110
But what if you want to look for other tables, so in this case, again, we have one, two, three,

81
00:05:23,110 --> 00:05:23,510
four.

82
00:05:23,860 --> 00:05:26,790
What if we were to fetch data from another table?

83
00:05:26,800 --> 00:05:27,660
So what we wanted?

84
00:05:27,700 --> 00:05:32,170
What if we want to guess for what if we wanted to guest for the table users?

85
00:05:32,980 --> 00:05:35,740
So what we can do is we can brute force what its value here.

86
00:05:35,980 --> 00:05:39,700
As long as we're giving it invalid names, it's going to come back and tell us that it doesn't exist

87
00:05:39,700 --> 00:05:41,770
until we find the right table name.

88
00:05:42,010 --> 00:05:44,710
So in this case, users does not exist.

89
00:05:45,160 --> 00:05:57,880
What if your articles doesn't exist, give it news and so on can also go as far as guessing the names

90
00:05:57,880 --> 00:05:59,320
for each column.

91
00:05:59,350 --> 00:06:04,720
So again, right now what we're doing was we're looking for different tables or different columns are

92
00:06:04,720 --> 00:06:05,140
stored.

93
00:06:05,400 --> 00:06:10,840
What if right now I want to look for the name of the columns within the current table that we're fetching

94
00:06:10,840 --> 00:06:11,350
data from.

95
00:06:11,680 --> 00:06:14,200
So again, we go, one, two, three, four.

96
00:06:14,800 --> 00:06:19,990
Now we're going to replace this for whatever column name that we're brute forcing for so we can manually

97
00:06:19,990 --> 00:06:22,640
type in anything that we think it's relatable.

98
00:06:22,660 --> 00:06:26,920
So if I want to look for Artecoll name, we'll put that in there.

99
00:06:26,920 --> 00:06:34,030
It says, hey, this column does not exist versus you can put in let's go back, which you can put an

100
00:06:34,030 --> 00:06:36,460
idea that doesn't exist and so on.

101
00:06:36,490 --> 00:06:37,880
You can always brute force for it.

102
00:06:37,900 --> 00:06:44,560
That's a great thing about having the arrows showing up in a bicycle injection that tells you they were

103
00:06:44,560 --> 00:06:47,200
both, hey, this exists and this one doesn't.

104
00:06:47,210 --> 00:06:48,640
And you can keep going back and forth.