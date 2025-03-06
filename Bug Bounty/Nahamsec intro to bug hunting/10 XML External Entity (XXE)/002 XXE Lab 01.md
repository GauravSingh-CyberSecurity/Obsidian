






---


1
00:00:00,330 --> 00:00:06,240
Now, let's have a look at our XXXI example, this case we're going against the site map to where the

2
00:00:06,240 --> 00:00:09,730
application is actually giving us an example of how this is very common.

3
00:00:09,750 --> 00:00:14,130
A lot of times the applications that you're using, they're going to give a demo file so you can understand

4
00:00:14,130 --> 00:00:16,740
what the format is and how to import your own data.

5
00:00:16,860 --> 00:00:23,480
Just go ahead and save this file like, let's say Flink, and we're going to save it on our local machine.

6
00:00:23,880 --> 00:00:25,410
We're going to open up notepad again.

7
00:00:25,410 --> 00:00:27,240
You can use whatever text editor you like.

8
00:00:27,240 --> 00:00:28,680
I'm using notepad for this case.

9
00:00:29,170 --> 00:00:30,510
I'm going to open it up and look at it.

10
00:00:30,930 --> 00:00:37,100
So in this case, this application is expecting us to send a set of you URLs, give it a location that's

11
00:00:37,110 --> 00:00:39,060
a website location and give it a priority.

12
00:00:39,540 --> 00:00:43,990
And whenever it gets uploaded, it's going to pass this data and show it back to the user.

13
00:00:44,070 --> 00:00:44,910
So let's give it a try.

14
00:00:45,480 --> 00:00:52,050
Going to go right here and we're going to set go once we head, go Google dot com test and test out

15
00:00:52,050 --> 00:00:57,300
what came back, which looks like this is where these are the information that's going to be presented

16
00:00:57,300 --> 00:00:58,560
to the user.

17
00:00:58,770 --> 00:01:03,680
And we want to make sure that this is where we also query for our file that we're going after.

18
00:01:03,690 --> 00:01:08,220
So if we're going after ETSI password, we want to make sure that it's being shown in the location and

19
00:01:08,220 --> 00:01:12,360
not in priority since the priority is not being visible within this results.

20
00:01:13,240 --> 00:01:15,360
So let's go ahead and go back to our example really quickly.

21
00:01:15,780 --> 00:01:21,150
We're going to just copy our payload and compare it to choosing the example from our presentation.

22
00:01:21,150 --> 00:01:23,390
We can see that we already have the signature.

23
00:01:23,400 --> 00:01:24,240
We don't need this.

24
00:01:24,600 --> 00:01:27,180
This is usually by default that part of the XML file.

25
00:01:27,510 --> 00:01:33,320
But however, we don't have an element or the entity that we need to call system to fetch default faulty

26
00:01:33,360 --> 00:01:39,150
password and assign it to our entity XXXI so we can just copy this, can do this either in multiline

27
00:01:39,270 --> 00:01:40,620
or you can make a one single line.

28
00:01:41,070 --> 00:01:42,600
I have to keep it all in one line.

29
00:01:42,630 --> 00:01:44,160
I'm just going to bump it right there.

30
00:01:44,520 --> 00:01:45,600
Leave it there again.

31
00:01:45,600 --> 00:01:50,790
We're calling etsi password for assigning it to Xixi, but down here somewhere we want to make sure

32
00:01:50,790 --> 00:01:54,240
we call for Xixi and get the content that was assigned to it.

33
00:01:54,600 --> 00:02:00,060
So since we know the application is going to show a list of you else like this one test and test two,

34
00:02:00,330 --> 00:02:06,750
we're going to replace one of these values and have it represent the data that was assigned to our entity.

35
00:02:07,170 --> 00:02:08,780
And once we have this, we're going to save it.

36
00:02:09,000 --> 00:02:10,930
You can either overwrite your current file.

37
00:02:10,980 --> 00:02:16,410
I highly suggest writing this into our second file, so not to keep downloading the original template

38
00:02:16,710 --> 00:02:18,840
in case something goes wrong.

39
00:02:19,080 --> 00:02:20,280
So we're going to go back here.

40
00:02:20,640 --> 00:02:21,870
We're going to update our file.

41
00:02:22,230 --> 00:02:23,190
We're going to push go.

42
00:02:25,030 --> 00:02:26,430
So our example here failed.

43
00:02:26,640 --> 00:02:29,460
This is because I forgot to remove the payload that we had the bottom.

44
00:02:29,520 --> 00:02:32,940
Well, you want to make sure is in case it doesn't work, you don't have any errors.

45
00:02:32,940 --> 00:02:33,720
All the syntax.

46
00:02:33,720 --> 00:02:34,170
All right.

47
00:02:34,530 --> 00:02:37,830
There are no extra DOCTYPE elements at the bottom of this.

48
00:02:37,830 --> 00:02:39,240
You want to make sure it fits the template.

49
00:02:39,240 --> 00:02:40,980
You have to remove it again.

50
00:02:41,280 --> 00:02:44,310
Now, we have it at Xixi being called for right here.

51
00:02:44,310 --> 00:02:46,890
Xixi has the value of the file.

52
00:02:46,890 --> 00:02:49,710
It's all assigned to exact into that we just created.

53
00:02:50,020 --> 00:02:51,810
I'm just going to go ahead and upload this again.

54
00:02:51,810 --> 00:02:54,390
So we're going to save this just to make sure it's safe.

55
00:02:54,780 --> 00:03:00,630
We're going to upload and right here, as we can see, instead of showing us the Google dot com, Tetsuro,

56
00:03:00,630 --> 00:03:06,720
that we had, it's showing us the content that was assigned to Xixi at the top and above that at the

57
00:03:06,720 --> 00:03:11,050
top and bottom of this request, we can see the other two UI ls that we had.

58
00:03:11,400 --> 00:03:12,930
So again, this is very straightforward.

59
00:03:13,110 --> 00:03:16,770
Sometimes you may have to do this through purposely to see the actual results.

60
00:03:17,050 --> 00:03:19,620
Again, it all depends on how the application is working.

61
00:03:19,890 --> 00:03:21,780
So let's run this really quickly through Burpengary.

62
00:03:21,790 --> 00:03:23,220
Just to give an example as well.

63
00:03:23,490 --> 00:03:25,470
We're going to download our sample file.

64
00:03:25,770 --> 00:03:34,200
We're going to call this sample X amount to we're going to open it up and our notepad just to make sure

65
00:03:34,200 --> 00:03:36,390
that the original version, there's no Xixi here.

66
00:03:36,780 --> 00:03:42,360
We're going to feed it to this uploader and we're going to intercept this with burb suite.

67
00:03:42,690 --> 00:03:44,160
We can see the content of the file.

68
00:03:44,490 --> 00:03:50,130
We're going to go to action sent repeater to send this out.

69
00:03:50,130 --> 00:03:50,850
It comes back.

70
00:03:51,170 --> 00:03:53,010
Same thing we Prisco.

71
00:03:56,060 --> 00:04:01,880
It comes back and tells us, hey, this is it, you are all you had Google dot com test to see you again.

72
00:04:01,890 --> 00:04:06,470
I'm showing this in case this was an API where the API is going to come back and give you some tax and

73
00:04:06,470 --> 00:04:07,550
not the entire Shamo.

74
00:04:07,550 --> 00:04:12,950
In that case, you can just replace this with your payload again, send it out and the application is

75
00:04:12,950 --> 00:04:17,060
going to come back and give you the form that you looking for.