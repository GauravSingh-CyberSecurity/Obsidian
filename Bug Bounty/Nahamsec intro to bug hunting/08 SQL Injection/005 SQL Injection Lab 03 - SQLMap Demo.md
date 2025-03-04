






----



1
00:00:00,480 --> 00:00:05,610
It's one of the most popular tools for a injection is Seacombe map will cover how to install this and

2
00:00:05,610 --> 00:00:07,950
our how to set up your lab section of this course.

3
00:00:08,350 --> 00:00:12,270
We can actually use this tool to look for my injections.

4
00:00:12,300 --> 00:00:16,770
So what I usually do myself is kind of play around with it manually confirmed.

5
00:00:16,770 --> 00:00:18,270
There is a vulnerability there.

6
00:00:18,390 --> 00:00:24,050
And if there is vulnerability there and I want to speed up my process, I will go ahead and use map.

7
00:00:25,230 --> 00:00:31,230
So what you can do is you can actually read the sequel map, how to guide.

8
00:00:31,240 --> 00:00:32,460
We're doing a dash H.

9
00:00:34,060 --> 00:00:37,560
It tells you all the different options for it.

10
00:00:37,740 --> 00:00:43,830
But for this case, we're just going to give it to you, which is that you are we want to test out there.

11
00:00:43,840 --> 00:00:47,100
We're going to give it a valid we're going to give it a valid.

12
00:00:47,100 --> 00:00:52,380
You are go in this up really quickly.

13
00:00:54,060 --> 00:00:59,130
So we're giving it a value URL and we're going to see if it actually can exploit this.

14
00:01:04,380 --> 00:01:08,950
So what school map does is not it's those are a bunch of different payloads.

15
00:01:09,330 --> 00:01:15,300
It looks at it and sees if it comes back with any errors or anything, that could look like it's a vulnerable

16
00:01:15,300 --> 00:01:15,870
application.

17
00:01:16,290 --> 00:01:19,230
So in this case, it's saying, hey, I think I'm going after my school.

18
00:01:19,560 --> 00:01:22,800
I'm going to try payloads that are at a level one risk one.

19
00:01:22,810 --> 00:01:24,450
You can go all the way to five, the computer.

20
00:01:24,660 --> 00:01:28,230
This, if you like, or you can take Sukma suggestion.

21
00:01:30,840 --> 00:01:36,810
So, again, it's going to throw out a bunch of queries, it's going to look for one that comes back

22
00:01:36,810 --> 00:01:42,390
and confirms that, hey, this application is actually vulnerable and this is how you can prove it by

23
00:01:42,720 --> 00:01:45,690
using this particular query.

24
00:01:45,900 --> 00:01:51,060
It's going to give you an example query that confirms there is actually a sequel injection present in

25
00:01:51,060 --> 00:01:51,830
this application.

26
00:01:53,660 --> 00:01:59,870
So it says right here, hey, it looks at the date parameter is vulnerable and we're going against a

27
00:01:59,870 --> 00:02:04,430
potential Marsico 5.0 12 and we did it with a sleep.

28
00:02:04,440 --> 00:02:09,680
So I talked about doing a sleep function before you can use it to confirm if they query worked out or

29
00:02:09,680 --> 00:02:09,890
not.

30
00:02:09,920 --> 00:02:14,940
So I say, yes, that's the wrap up its work and see if it actually works.

31
00:02:15,380 --> 00:02:20,440
So as we expected, it came back in and said, hey, the date parameter is vulnerable.

32
00:02:20,660 --> 00:02:21,590
Do you want to keep testing?

33
00:02:21,590 --> 00:02:24,380
If there's others, we can say no and now we can study.

34
00:02:24,380 --> 00:02:28,550
Came back and said, hey, I was actually able to verify it with this payload.

35
00:02:28,560 --> 00:02:32,060
So this is one that they tried similar to what we had earlier.

36
00:02:32,240 --> 00:02:37,850
And of that equals to one, they did this one and added some letters as well so that we know this is

37
00:02:37,850 --> 00:02:38,480
vulnerable.

38
00:02:39,050 --> 00:02:40,930
We already confirming this is vulnerable.

39
00:02:40,970 --> 00:02:44,160
It can also copy one of their payloads just to see if it works.

40
00:02:44,230 --> 00:02:45,740
Let's try this out really quickly.

41
00:02:46,020 --> 00:02:49,640
We're going to throw this in there, comes back and says count is equal to two.

42
00:02:49,970 --> 00:02:55,400
What if we change the value of 30, 37 through 38 comes back zero?

43
00:02:55,430 --> 00:02:57,140
OK, same as what we're doing manually.

44
00:02:57,470 --> 00:03:00,320
But now we know that second map was also able to identify it.

45
00:03:00,860 --> 00:03:04,220
So now what we can do is go back to school, maps, help.

46
00:03:04,400 --> 00:03:08,240
We can see that there's different ways we can get information so we can retrieve everything.

47
00:03:08,570 --> 00:03:09,710
We can retrieve the banner.

48
00:03:09,710 --> 00:03:12,230
We can do the current user current database.

49
00:03:12,230 --> 00:03:15,240
We can pull tables, columns for the sake of this material.

50
00:03:15,500 --> 00:03:17,840
And for this section, we're just going to grab the banner.

51
00:03:18,180 --> 00:03:26,660
We're going to go back to our original query and we're going to do a B square back like we go on the

52
00:03:26,660 --> 00:03:27,240
dashboard.

53
00:03:27,590 --> 00:03:29,620
It's going to start receiving data for us.

54
00:03:29,630 --> 00:03:32,360
So right now it's going to brute force for the version.

55
00:03:32,520 --> 00:03:36,740
What it's doing is literally it could be doing something like a sleep or substring and saying, hey,

56
00:03:37,040 --> 00:03:42,200
look, for the first value is at five, OK, is the second one at seven, 32.

57
00:03:42,470 --> 00:03:45,530
And then it's getting the letters as well until it's finished.

58
00:03:45,530 --> 00:03:50,300
And it's going to go to the next thing you think will be very handy when it comes down to speeding up

59
00:03:50,300 --> 00:03:50,890
the process.

60
00:03:50,900 --> 00:03:52,130
A lot of hackers rely on it.

61
00:03:52,340 --> 00:03:59,120
But I highly recommend getting good at sequel injections because tools often miss finding his vulnerabilities

62
00:03:59,330 --> 00:04:00,500
and doing it manually.

63
00:04:00,500 --> 00:04:03,320
It's easier to discover than relying on a tool.