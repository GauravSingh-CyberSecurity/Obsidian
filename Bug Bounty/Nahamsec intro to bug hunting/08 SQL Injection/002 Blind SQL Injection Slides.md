
Refrence: 
- study a mysql course
- study about mysql on mysql website (https://dev.mysql.com/doc/   | https://www.w3schools.com/MySQL/default.asp )


---

![[Screenshot From 2025-03-04 12-43-53.png]]

1
00:00:00,060 --> 00:00:04,320
So, again, before we jump into the bland sequel injection, the dash is very important, it always

2
00:00:04,320 --> 00:00:04,890
comes out.

3
00:00:04,890 --> 00:00:07,470
Whatever is left over, we don't know where we are in the query.

4
00:00:07,720 --> 00:00:12,360
So we want to make sure if there are anything left over, we completely ignored by giving it a dash

5
00:00:12,360 --> 00:00:16,020
dash and commenting out, especially when it comes down to blind sequel injection.

6
00:00:16,030 --> 00:00:22,110
But the blind SQL injection, we're relying on conditions to be true in order to receive a response.

7
00:00:22,140 --> 00:00:24,450
So in other words, we're not seeing an error.

8
00:00:24,460 --> 00:00:29,460
There's no way of knowing if the thing that we're giving it, if that query is actually working out

9
00:00:29,460 --> 00:00:29,890
or not.

10
00:00:30,270 --> 00:00:31,920
So we have to give it a true condition.

11
00:00:32,190 --> 00:00:36,640
If that condition is met, we're going to look at the response and see if it's valid.

12
00:00:37,080 --> 00:00:39,090
So we talked about this early on.

13
00:00:39,120 --> 00:00:41,540
We're going to close the previous query.

14
00:00:41,550 --> 00:00:44,370
It could be a single code, it could be quotations, whatever that is.

15
00:00:44,700 --> 00:00:50,760
And then we can say and one equals one, because in mathematics, one equals one is a true statement.

16
00:00:51,090 --> 00:00:54,210
We're going to come back with the application, giving us some response.

17
00:00:54,450 --> 00:00:55,530
That is not an error.

18
00:00:55,650 --> 00:00:58,140
That could be a 400 HGP response code.

19
00:00:58,440 --> 00:01:00,030
That could be no data coming back.

20
00:01:00,360 --> 00:01:01,670
Could be a number of different things.

21
00:01:01,680 --> 00:01:06,210
You have to understand how the application works for blind SQL injection to make sense.

22
00:01:06,810 --> 00:01:09,660
So, again, for the second one, we're doing the same thing.

23
00:01:09,990 --> 00:01:11,640
We are giving it a true condition.

24
00:01:11,970 --> 00:01:13,540
He comes back and it works.

25
00:01:13,680 --> 00:01:16,500
But the last but not least, the third one is very important here.

26
00:01:16,500 --> 00:01:22,410
We're saying, hey, I want you to finish a previous query from the double quotes and and one equals

27
00:01:22,410 --> 00:01:26,330
to two, which is not valid when no one doesn't include it, it's not valid.

28
00:01:26,340 --> 00:01:31,260
And with math and this going to be an invalid condition and we may get an invalid response, and that's

29
00:01:31,260 --> 00:01:34,710
kind of how we can actually confirm if a sequel injection exists.

30
00:01:35,220 --> 00:01:38,130
Simple math we do one equals one true response.

31
00:01:38,370 --> 00:01:40,890
We get some sort of a valid response from the Web server.

32
00:01:41,070 --> 00:01:41,970
One equals two.

33
00:01:41,970 --> 00:01:43,260
We're not getting anything valid.

34
00:01:43,500 --> 00:01:47,250
It's going to give us some sort of an error that indicates, OK, maybe there's a sequel injection here.

35
00:01:47,250 --> 00:01:48,300
Let's look into it further.



![[Screenshot From 2025-03-04 12-47-56.png]]
36
00:01:48,450 --> 00:01:52,920
That way we can actually verify a sequel injection exists outside of giving it true conditions.

37
00:01:53,190 --> 00:01:58,440
We can use some functions that delays the response coming back from the server to candidates in two

38
00:01:58,440 --> 00:02:00,450
ways, depending on what backing you're using.

39
00:02:00,450 --> 00:02:06,150
The first way is to just say, hey, close the previous query, which is what we're doing here, saying

40
00:02:06,150 --> 00:02:10,680
and sleep five, which is what we're doing here.

41
00:02:10,890 --> 00:02:15,390
What we're saying is one quotation mark that causes the previous query.

42
00:02:15,690 --> 00:02:20,940
And then we're going to say, hey, once that is done, I want you to also do this step five, so we

43
00:02:20,940 --> 00:02:22,590
say and sleep five.

44
00:02:22,590 --> 00:02:27,360
And then we commentor the rest of the query if there's anything afterwards and if there's a single injection

45
00:02:27,360 --> 00:02:32,310
here, the Web server is going to take five seconds before it comes back and gives us a response.

46
00:02:32,610 --> 00:02:36,570
There's a number of different ways to do this, depending on the back and cycle database.

47
00:02:36,840 --> 00:02:41,580
By the end of the day, they all have similar functions when we can delay the response to confirm our

48
00:02:41,820 --> 00:02:43,080
sequence injection exists.


![[Screenshot From 2025-03-04 12-49-45.png]]
49
00:02:43,270 --> 00:02:48,450
So in other words, to wrap it up, what we're doing here is we're closing the previous statement again

50
00:02:48,450 --> 00:02:49,200
with SQL injection.

51
00:02:49,210 --> 00:02:53,700
You always want to close the previous statement, whatever that equal query as you want to close it.

52
00:02:53,910 --> 00:02:57,780
And then for blind second injection, you want to say, OK, here is a true statement.

53
00:02:58,020 --> 00:03:00,810
If this is valid, then I want you to sleep for five seconds.

54
00:03:01,140 --> 00:03:02,310
The expression is true.

55
00:03:02,490 --> 00:03:06,090
I want you to sleep for five second, but doesn't have to always be a sleep function.

56
00:03:06,090 --> 00:03:09,450
We can actually guess the value that we're expecting.

57
00:03:09,450 --> 00:03:14,900
We can brute force for it by giving it different functions on our belt and within the database query

58
00:03:14,910 --> 00:03:15,480
that they're using.

59
00:03:15,480 --> 00:03:19,620
So whatever the secret language are using, whatever the back end is, we have to go look at it and

60
00:03:19,620 --> 00:03:23,790
see what functions are available to us and use some of those to brute force it.

61
00:03:24,030 --> 00:03:29,520
So, for example, my school can use substring, which takes the string start in value.

62
00:03:29,520 --> 00:03:35,400
So if we are looking for a particular information, we can say, hey, I want you to use substring look

63
00:03:35,400 --> 00:03:40,370
for this string and tell me if it's the first letter of it is equal to this.

64
00:03:40,380 --> 00:03:42,750
So in our first example, we have no Comsec.

65
00:03:43,020 --> 00:03:47,430
We're saying, hey, I want you to get the first letter starting at point one.

66
00:03:47,430 --> 00:03:53,070
So we're saying the homesick start at point one, the first letter and give me the first value is that

67
00:03:53,070 --> 00:03:56,400
n if it is true, it's going to come back and give us no error.

68
00:03:56,400 --> 00:04:00,510
And if it's not true, it's going to give us some sort of an error indicating that it didn't work.

69
00:04:00,960 --> 00:04:06,720
From the second line, we're saying select substring namesake start add value to and give me the first

70
00:04:06,720 --> 00:04:07,080
letter.

71
00:04:07,680 --> 00:04:12,540
So we're getting a back, which means second letter of the string, not homesick.

72
00:04:13,100 --> 00:04:18,120
We can also ask it to give us two letters back so we can say, hey, start up position one, this is

73
00:04:18,120 --> 00:04:23,670
where we start and give me the first two letters, which is an A you can actually, instead of waiting

74
00:04:23,670 --> 00:04:28,740
for it to give it back to you, you can say, hey, does select substring namesake one want equal.

75
00:04:28,740 --> 00:04:30,830
And if that is true, there's no errors.

76
00:04:30,890 --> 00:04:33,960
If it's not true, then it's going to say, no, that is not correct.

77
00:04:34,170 --> 00:04:34,860
There's an error.

78
00:04:34,860 --> 00:04:35,760
I don't know what happened.

79
00:04:37,050 --> 00:04:39,030
So now we're going to use this functionality.

80
00:04:39,030 --> 00:04:40,020
This was an example.

81
00:04:40,530 --> 00:04:45,030
We're going to use this functionality and guess the MySQL version.

82
00:04:45,030 --> 00:04:51,180
So in this case, what I'm doing is I'm saying, hey, I want to use a substring use a function at @

83
00:04:51,180 --> 00:04:51,780
version.

84
00:04:52,020 --> 00:04:58,950
And I want you to see if starting out the first point value with the first position doesn't start with

85
00:04:58,950 --> 00:04:59,460
a five.

86
00:04:59,940 --> 00:05:04,530
If there's no error, it's going to come back and give us no error, which indicates that we are on

87
00:05:04,530 --> 00:05:08,220
version five and if there is an error, it's going to just give us an error, like saying, hey, I

88
00:05:08,220 --> 00:05:09,000
don't know what happened.

89
00:05:09,000 --> 00:05:11,490
I don't know what I'm doing with this statement that you have given me.

90
00:05:11,850 --> 00:05:12,650
There is an error.

91
00:05:12,660 --> 00:05:17,970
So we continue to for three, hopefully not on a super old version, but the point is to show there

92
00:05:18,000 --> 00:05:22,860
are different methodologies that you can follow when it comes down to blind SQL injection to extract

93
00:05:22,860 --> 00:05:26,220
data and verify your vulnerability quickly.


![[Screenshot From 2025-03-04 12-52-56.png]]
94
00:05:26,280 --> 00:05:27,570
Let's revisit all of this.

95
00:05:27,590 --> 00:05:29,070
But I'm sure you all understand this.

96
00:05:29,370 --> 00:05:34,010
The point of it is you want to make sure you are actually closing out their previous statement.

97
00:05:34,020 --> 00:05:37,530
You have to find out if they were using a single code, double quote, whatever that was.

98
00:05:37,770 --> 00:05:41,880
You want to close it and then insert your own query within the next slide.

99
00:05:41,940 --> 00:05:43,260
So right now we're doing one.

100
00:05:43,480 --> 00:05:46,400
We know that they're putting the ID within two single quotes.

101
00:05:46,410 --> 00:05:49,440
So it goes equals to single code, one single quote.

102
00:05:49,710 --> 00:05:52,150
We're closing it and then inserting our own statement.

103
00:05:52,320 --> 00:05:57,360
The biggest thing to understand for this chapter is how school works and how you can inject your sequel

104
00:05:57,360 --> 00:06:02,910
injection query, which is a regular school query into this application and retrieve the data that you

105
00:06:02,910 --> 00:06:04,900
want if you want to get better at sequel injection.

106
00:06:04,920 --> 00:06:11,500
My biggest advice is to look into a my school course, learn the basics, go to my school's website.

107
00:06:11,500 --> 00:06:16,260
They have great documentation, kind of understand the basics of school queries and take it from their.