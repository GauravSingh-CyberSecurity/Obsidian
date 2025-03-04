



![[Screenshot From 2025-03-04 12-24-06.png]]
1
00:00:00,450 --> 00:00:05,970
Now, let's talk about SQL injection, SQL stands for structured query language to language use to communicate

2
00:00:05,970 --> 00:00:06,780
with the database.

3
00:00:06,930 --> 00:00:12,150
Almost every single application that stores data will use some sort of a school in some way.


![[Pasted image 20250304122547.png]]
4
00:00:12,210 --> 00:00:17,280
A single injection will allow an attacker to potentially execute malicious queries that would lead him

5
00:00:17,280 --> 00:00:20,490
to create, read, update or even delete data out of the database.

6
00:00:20,760 --> 00:00:25,440
So when you're making a request to retrieve some sort of a data, a query similar to the ones on this

7
00:00:25,440 --> 00:00:28,020
screen may appear in the background.


![[Screenshot From 2025-03-04 12-26-28.png]]
8
00:00:28,200 --> 00:00:33,960
There are two major types of SQL injection error based, which is not as usual anymore thanks to our

9
00:00:34,050 --> 00:00:34,920
new libraries.

10
00:00:34,920 --> 00:00:40,230
But also there is blind SQL injection, which is more likely to run into an bug bounties in case of



11
00:00:40,230 --> 00:00:41,620
an Arab SQL injection.


![[Screenshot From 2025-03-04 12-27-18.png]]
12
00:00:41,640 --> 00:00:46,740
The application comes back and tells you that your sequel query has some sort of an error in the syntax.

13
00:00:47,310 --> 00:00:52,550
For example, you could see it come back and say there is a syntax error near the character that you

14
00:00:52,550 --> 00:00:53,040
have put in.

15
00:00:53,490 --> 00:00:59,850
So our example on the screen, we're making a request, for example, dot com slash some endpoint and

16
00:01:00,150 --> 00:01:03,960
we're assigning the apostrophe to the second example.

17
00:01:03,960 --> 00:01:06,060
We're doing quotes and so on.

18
00:01:06,300 --> 00:01:11,040
In case of an Arab SQL injection, the application is going to come back and that, you know, that

19
00:01:11,040 --> 00:01:15,030
the character you have provided has broken the cycle query that's running in the background.

20
00:01:15,180 --> 00:01:20,250
So in this case, cycle is coming back and saying, hey, there is a syntax error next to the character

21
00:01:20,250 --> 00:01:22,920
apostrophe and you can do this in different ways.

22
00:01:22,920 --> 00:01:29,070
You can see on the screen as an apostrophe, I quote, adding brackets, an array to the parameter and

23
00:01:29,070 --> 00:01:29,500
so on.

24
00:01:29,820 --> 00:01:31,620
So what actually happens when you put an apostrophe?


![[Screenshot From 2025-03-04 12-28-44.png]]
25
00:01:31,620 --> 00:01:32,340
Why is this work?

26
00:01:32,700 --> 00:01:33,560
On the left hand side?

27
00:01:33,570 --> 00:01:38,130
You can see the request and the right hand side is an example that would happen in the background of

28
00:01:38,130 --> 00:01:38,840
the application.

29
00:01:39,690 --> 00:01:45,300
The first request here we're making is to an application to the endpoint news that B and we're fetching

30
00:01:45,300 --> 00:01:46,230
the ID one.

31
00:01:46,790 --> 00:01:52,230
This could be an article that in the database is numbered as ID one.

32
00:01:52,470 --> 00:01:57,600
So in this case, we are fetching data based on the ID one and the query on the right hand side.

33
00:01:57,600 --> 00:02:01,410
We're doing all of this and we're adding the ID from the request to the end.

34
00:02:01,530 --> 00:02:08,580
So you can see the number one is being put into two apostrophes and being fetched from the articles

35
00:02:08,700 --> 00:02:11,700
table where the UID column is equal to one.

36
00:02:12,690 --> 00:02:15,600
And the next request, we're going to add an apostrophe to our request.

37
00:02:15,840 --> 00:02:21,870
And as you can see in the request in the back end, the articles table with the UID column is equal

38
00:02:21,870 --> 00:02:24,420
to one with an extra apostrophe.

39
00:02:24,780 --> 00:02:29,850
This will actually break the query that's being ran in the back end, which will cause an error that

40
00:02:29,850 --> 00:02:35,130
could indicate for a sequel injection and the last example we're using and to say we want to finish

41
00:02:35,130 --> 00:02:38,230
a previous square and also run the next query.

42
00:02:38,250 --> 00:02:41,760
So in this case, we're just saying, hey, the expression one equals two.

43
00:02:41,760 --> 00:02:45,380
One, which is true in the database, is not going to give us an error.

44
00:02:45,720 --> 00:02:49,830
So for this slide, we just want to look at what a quarter looks like and why does it throw out an error

45
00:02:49,830 --> 00:02:51,030
when we add an apostrophe?



![[Screenshot From 2025-03-04 12-30-47.png]]
46
00:02:51,330 --> 00:02:57,330
So in the next example, what we're going to do is we're going to end our previous query.

47
00:02:57,360 --> 00:03:02,160
This is why we got the single quote and we're going to add the next query that's going to fetch the

48
00:03:02,160 --> 00:03:07,560
data that we want so far in this example where we're doing it close to one without the second junction,

49
00:03:07,920 --> 00:03:12,660
the web application is going back and saying, hey, give me the information for the news article that

50
00:03:12,660 --> 00:03:13,530
has ID one.

51
00:03:13,950 --> 00:03:18,510
But when we do a sequel injection, we say, OK, now that you have done this and this particular query,

52
00:03:18,510 --> 00:03:23,220
but also I want you to fetch the data that I want so that the attacker we could be looking for passwords,

53
00:03:23,220 --> 00:03:27,480
username, email addresses or whatever that were after the first example.

54
00:03:27,480 --> 00:03:33,330
When we do a union select one, we practically are trying to guess how many different columns exist

55
00:03:33,330 --> 00:03:34,380
in this particular table.

56
00:03:34,720 --> 00:03:39,630
So we were still in the article's table, as you can see, its articles and the next DOT uid, which

57
00:03:39,630 --> 00:03:40,590
is the column name.

58
00:03:41,010 --> 00:03:45,120
We're still looking to see how many columns are actually within this table.

59
00:03:45,480 --> 00:03:49,920
So in this case, because we're giving the wrong number of columns, the application comes back and

60
00:03:49,920 --> 00:03:55,610
responds and says, hey, the select segment you have given me has less numbers of columns that I expect.

61
00:03:55,620 --> 00:03:57,060
So there's different numbers of columns.

62
00:03:57,300 --> 00:03:58,390
So we add another number.

63
00:03:58,410 --> 00:03:59,400
These numbers could be there.

64
00:03:59,400 --> 00:04:02,550
One doesn't have to be in order of one, two, three, four.

65
00:04:02,550 --> 00:04:04,860
It's just placeholders for us to count.

66
00:04:05,130 --> 00:04:10,890
How many actual tables are there either has to be no or we have to give it numbers and not actual characters

67
00:04:11,070 --> 00:04:14,130
that could be mistaken for a name of a column.

68
00:04:14,520 --> 00:04:19,920
So the next example we're doing select one, two, and it comes back and says, hey, I'm expecting

69
00:04:19,920 --> 00:04:20,340
more.

70
00:04:20,580 --> 00:04:21,990
There are different number of columns.

71
00:04:22,170 --> 00:04:27,390
We add three, which in this case means there are three columns within the table articles and those

72
00:04:27,390 --> 00:04:33,860
could be different columns like UID the title and the body of that news article that we're looking for.

73
00:04:34,230 --> 00:04:38,550
So because we're doing the number of valid requests, it's going to come back and says, hey, here's

74
00:04:38,550 --> 00:04:39,390
a data you asked.

75
00:04:39,570 --> 00:04:41,250
I'm going to print some random data for you.

76
00:04:41,790 --> 00:04:44,340
As you can see in our fourth example, we're doing the same thing.

77
00:04:44,820 --> 00:04:49,980
We're closing out the query and we're saying, hey, union, select one, two, three, four, which

78
00:04:49,980 --> 00:04:52,830
is one more calm than the application expects.

79
00:04:53,010 --> 00:04:54,480
And it comes back and says the same thing.

80
00:04:54,480 --> 00:04:57,150
Hey, you're select statement has a different number of columns.

81
00:04:57,420 --> 00:04:58,760
I can't help you with this query.

82
00:04:59,220 --> 00:04:59,910
So when we do this.

83
00:05:00,240 --> 00:05:07,320
Our based SQL injection, we're guessing the number of actual columns that exists within that table.

84
00:05:07,550 --> 00:05:08,880
In this case there are only three.

85
00:05:09,230 --> 00:05:15,070
And as you can see at the end of each of these statements, we have the dash dash plus the dash.

86
00:05:15,070 --> 00:05:16,400
That's usually in a square.

87
00:05:16,430 --> 00:05:21,750
It means a comments or anything after that is ignored in the plus sign is actually a space.

88
00:05:21,820 --> 00:05:25,700
What we're doing is we're saying, hey, I want you to comment out and ignore everything that comes

89
00:05:25,970 --> 00:05:29,060
after my query that may be hard coded within the code.

90
00:05:29,420 --> 00:05:34,280
So, again, the dash dash that we have at the end of it is just a comment out and force the application

91
00:05:34,580 --> 00:05:38,520
to ignore if there is any leftover code from the original query.

92
00:05:38,900 --> 00:05:43,340
So now that we know this application, for example, has three different columns we're going to do is

93
00:05:43,820 --> 00:05:46,850
guess for the name of each column.

94
00:05:47,000 --> 00:05:51,040
So in this example, we're saying, hey, I want to select one title and three.

95
00:05:51,410 --> 00:05:56,330
So now that we have successfully found out how many columns exist within this table, the next thing

96
00:05:56,330 --> 00:06:00,140
we want to do is guess for the name of each column.

97
00:06:00,440 --> 00:06:03,040
Again, when it comes out, the hacking context matters.

98
00:06:03,050 --> 00:06:08,930
So in this case, because we know that we're looking at the articles table, we want to guess things

99
00:06:08,930 --> 00:06:13,460
that are related to an article like a title, the body ID and so on.

100
00:06:13,490 --> 00:06:16,070
So in this case, what we're going to do is we're going to guess for the title.

101
00:06:16,070 --> 00:06:19,790
We're going to say, hey, I want you to fetch one title and three.

102
00:06:20,000 --> 00:06:25,760
If that column exists, we're going to get some data coming back from the website, which is the second

103
00:06:25,760 --> 00:06:26,000
line.

104
00:06:26,000 --> 00:06:27,470
You can see we're giving it a fake name.

105
00:06:27,470 --> 00:06:32,420
We're saying, hey, select one fake name three, which is going to come back and say, hey, fake name

106
00:06:32,420 --> 00:06:33,020
doesn't exist.

107
00:06:33,020 --> 00:06:34,310
And this table.

108
00:06:34,520 --> 00:06:38,060
And again, on the third line and the third example, the union select one, two, three.

109
00:06:38,330 --> 00:06:43,640
We're doing this again to just show an example that, OK, if we give it a valid query, we return data.

110
00:06:43,910 --> 00:06:45,530
We see that this is actually working.

111
00:06:45,740 --> 00:06:48,230
And if we give it something invalid, it's not going to work.

112
00:06:48,830 --> 00:06:53,430
You can also forced a sequel injection to fetch data from a different table.

113
00:06:53,750 --> 00:06:59,420
So in this case, I'm saying, hey, I'm going to guess one, two, three, four from fake name, which

114
00:06:59,420 --> 00:07:00,440
is the name of the table.

115
00:07:00,440 --> 00:07:05,300
We're now saying, hey, I want you to forget whatever you're running into this table.

116
00:07:05,330 --> 00:07:07,970
So this application is working within the article table.

117
00:07:08,150 --> 00:07:09,020
Forget that table.

118
00:07:09,020 --> 00:07:11,570
I want to go after a particular table name, fake name.

119
00:07:12,080 --> 00:07:16,670
And if that table name doesn't exist, the application is going to come back and say, hey, this fake

120
00:07:16,670 --> 00:07:18,000
name that you're giving me doesn't exist.

121
00:07:18,020 --> 00:07:22,790
So, for example, a valid one that would be good to look for would be the user's table when we can

122
00:07:22,790 --> 00:07:25,610
say, hey, one, two, three, four from users.

123
00:07:25,850 --> 00:07:30,470
And if the user's table actually exists, the application is going to come back and say, hey, there

124
00:07:30,470 --> 00:07:32,360
was more than four columns within this table.

125
00:07:32,430 --> 00:07:37,250
Now, if they go back to step one and figure out how many columns are within the next table that were

126
00:07:37,250 --> 00:07:42,230
enumerating, if this is confusing, trust me, it's all going to make sense for me to go to our lab.