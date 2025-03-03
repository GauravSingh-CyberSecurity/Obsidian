

![[Screenshot From 2025-02-28 13-22-19.png]]
1
00:00:00,060 --> 00:00:04,920
Now, let's talk about insecure direct object reference, also known as eider, and one of the most

2
00:00:04,920 --> 00:00:11,400
popular vulnerability types found in bug bounties and I adore is when an application provides direct



![[Screenshot From 2025-03-03 12-28-36.png]]
3
00:00:11,400 --> 00:00:14,620
access to an object that doesn't belong to that user.

4
00:00:14,670 --> 00:00:19,950
So this will allow malicious attacker to access data that doesn't belong to them, not data could be

5
00:00:19,950 --> 00:00:23,790
anywhere from Peiris invoices, receipts and so on.

6
00:00:24,540 --> 00:00:29,280
And either isn't just limited to retrieving data, but it could also allow you to modify or delete them

7
00:00:29,280 --> 00:00:29,730
as well.

8
00:00:30,150 --> 00:00:37,530
As you can see on the screen, for example, dot com API slash user is fetching an object with one six

9
00:00:37,530 --> 00:00:42,600
seven eight six five as its ID and that ID has an address.

10
00:00:42,660 --> 00:00:49,130
So that's the user ID and we're putting the address of the user specifically as we hit that as a user

11
00:00:49,130 --> 00:00:54,790
that says as mean said it's going to return the ID, the user name and my address.

12
00:00:55,230 --> 00:00:56,550
Now let's say we change that ID.

13
00:00:56,580 --> 00:01:02,820
We go from one six, seven, eight, six, five to one, and that's going to return the response for

14
00:01:02,830 --> 00:01:07,740
the user 81 and the user name being said to Aardman with their address.

15
00:01:08,080 --> 00:01:09,180
This is very common.

16
00:01:09,210 --> 00:01:10,130
That happens a lot.

17
00:01:10,140 --> 00:01:11,820
It's not always just an API.

18
00:01:11,820 --> 00:01:17,460
It could be anywhere with a numerical ID or anything that you can understand how the ID is being calculated,

19
00:01:17,460 --> 00:01:22,910
whether a base 64 or some sort of another encryption where you can break and create another one.

20
00:01:23,100 --> 00:01:28,730
In this example, we can see that we're making a request to another API endpoint.

21
00:01:28,740 --> 00:01:30,700
This one is API user profile.

22
00:01:30,810 --> 00:01:33,600
There is no idea in the actual address bar.

23
00:01:33,690 --> 00:01:37,500
But in the request that we're sending the data that's being sent to the server, we're providing an

24
00:01:37,500 --> 00:01:39,660
ID, a username and an email.

25
00:01:40,120 --> 00:01:45,510
Now let's say we want to override the user ID one, which is probably the admin or another user.

26
00:01:45,690 --> 00:01:49,920
We just swap out the ID changing using username in the sick one instead of the home sick because we

27
00:01:49,920 --> 00:01:52,290
don't want to have the same exact username for both IDs.

28
00:01:52,650 --> 00:01:54,240
It's probably not going to let us do that.

29
00:01:54,870 --> 00:01:56,820
And we also want to give it another email address.

30
00:01:57,180 --> 00:02:00,810
This way we can do a password reset or whatever else we're doing.

31
00:02:01,170 --> 00:02:05,460
And the response in some cases may come back a success and may come back as a one.

32
00:02:05,730 --> 00:02:09,630
We don't know what that response is going to look like, but for this example, the API comes back and

33
00:02:09,630 --> 00:02:11,190
says success is true.

34
00:02:11,370 --> 00:02:15,240
So now that we understand the basics of an idea, we need to look at a few different things.

35
00:02:15,690 --> 00:02:20,310
When it comes down to looking for this vulnerability to types, a deep understanding of the application

36
00:02:20,310 --> 00:02:21,590
is very, very valuable.

37
00:02:21,870 --> 00:02:26,700
How does the application fetch data, how to create new data, or how does that modify or delete them?

38
00:02:27,180 --> 00:02:33,480
Looking for any numerical ID or anything with an integer is a very good indication of an area to test

39
00:02:33,480 --> 00:02:33,750
for.

40
00:02:34,320 --> 00:02:41,130
The best way to do this is by creating two different accounts, looking at both user IDs, looking at

41
00:02:41,130 --> 00:02:46,530
the object ID, whatever we're testing for in two different browsers and replacing them back and forth.

42
00:02:46,530 --> 00:02:51,540
So you can make a user that's supposed to be your target and then you make another user that is the

43
00:02:51,540 --> 00:02:52,200
attacker.

44
00:02:52,260 --> 00:02:57,060
You grab both of those user IDs, does objects you want to fetch, and you go back and forth until you

45
00:02:57,060 --> 00:02:58,790
find a vulnerable endpoint.

46
00:02:58,950 --> 00:03:03,760
This will help you avoid fetching any data that doesn't belong to you and most companies would appreciate

47
00:03:04,260 --> 00:03:08,820
sometimes the application may use some sort of an encryption in order to hide the user ID.

48
00:03:08,820 --> 00:03:10,170
So it's not easily accessible.

49
00:03:10,440 --> 00:03:15,300
This could be a base64 or something more complicated, but at the end of the day, there's always ways

50
00:03:15,300 --> 00:03:15,780
around it.

51
00:03:15,780 --> 00:03:17,220
And we'll talk about that in a little bit.

52
00:03:17,580 --> 00:03:19,530
You can also automate this using berp.

53
00:03:19,530 --> 00:03:24,780
There are a ton of good add ons and extensions you can use on the automated, but I personally like

54
00:03:24,780 --> 00:03:29,760
to do this manually because it helps you understand the application and make sure that I'm not missing

55
00:03:29,760 --> 00:03:32,160
any endpoints or I'm not messing it up in any way.

56
00:03:32,580 --> 00:03:39,270
In the previous site, I explained how a company or an application may use some sort of complex user

57
00:03:39,270 --> 00:03:44,760
ID, and I said there may be some ways around it outside of just creating two different user IDs and

58
00:03:44,760 --> 00:03:47,280
having two different accounts that you're attacking each other with.

59
00:03:47,550 --> 00:03:52,590
You can also look for indicators that may leak the other users unique ID.

60
00:03:52,710 --> 00:03:58,230
So in this example, as you can see, the string is very random string that I put on the screen, but

61
00:03:58,560 --> 00:04:04,980
with things like a profile picture or going to the user's profile, clicking on report user and things

62
00:04:04,980 --> 00:04:10,260
like that that allows you to interact with a user's account may help you identify the unique user ID

63
00:04:10,440 --> 00:04:13,440
and help you exploit whatever either you have found further.