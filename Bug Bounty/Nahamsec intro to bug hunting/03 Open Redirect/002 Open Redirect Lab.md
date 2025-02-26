
Lab1: http://or1.naham.sec:8081/
Lab2: 

1
00:00:00,180 --> 00:00:01,320
So let's take our training site.

2
00:00:01,570 --> 00:00:06,280
This page says, welcome to my website, have you seen my new Web site called Google dot com?

3
00:00:06,720 --> 00:00:09,660
If we click it, it's just going to give us a clue what outcome?

4
00:00:09,840 --> 00:00:11,220
We don't see anything in the back.

5
00:00:11,880 --> 00:00:14,700
But if we're right, click copy link and paste it.

6
00:00:15,480 --> 00:00:21,600
We can see that this site is using a redirect parameter and whatever value opinion here is more than

7
00:00:21,600 --> 00:00:24,570
likely going to be used to redirect the user.

8
00:00:25,140 --> 00:00:32,460
So, for example, if I put in here Lahham Secombe, we're going to get redirected the namesake without

9
00:00:32,460 --> 00:00:33,240
any problems.

10
00:00:33,690 --> 00:00:36,180
This is very, very common in Buckman's after this happened.

11
00:00:36,180 --> 00:00:41,850
A lot of times you just have to be very good at seeing these different parameters and fuzzing get to

12
00:00:41,850 --> 00:00:43,970
a point where it gets redirected to your website.

13
00:00:44,310 --> 00:00:49,860
If you remember the earlier chapters that we talked about, response codes, as I type in redirect on

14
00:00:49,860 --> 00:00:55,170
our website right here, we're sending a request to Nahoum Technical Training Redirect in the hopes

15
00:00:55,170 --> 00:01:00,490
that the outcome with the request method being set to get we're getting it three or two.

16
00:01:00,540 --> 00:01:04,140
This is important because it tells us, hey, there's an open redirect order.

17
00:01:04,140 --> 00:01:07,620
Actually, there's a redirect happening here to look for it further.

18
00:01:08,070 --> 00:01:11,130
It's always good to know the status goes and understanding what each one means.

19
00:01:12,480 --> 00:01:13,680
Just another is clicked.

20
00:01:14,340 --> 00:01:20,040
The application is going to redirect us and we can either have a fishing page, a fake login page or

21
00:01:20,040 --> 00:01:23,640
whatever else right here in order to exploit our users.

22
00:01:23,940 --> 00:01:26,780
And also, I mentioned that it's always not that straightforward.

23
00:01:26,790 --> 00:01:32,370
So in this case, again, for another example, if we click the link, it's kind of a Google dot com

24
00:01:33,090 --> 00:01:35,400
again that's tried again and go to Google NORCOM.

25
00:01:35,700 --> 00:01:38,010
Now I'm going to swap out Google with knapsack.

26
00:01:38,460 --> 00:01:42,980
And this is a website that it's not trusted by the Web server.

27
00:01:42,990 --> 00:01:47,850
So it says, hey, it's not allowed to this host because I don't recognize that the name is spelled

28
00:01:47,850 --> 00:01:48,560
no homosexual.

29
00:01:48,570 --> 00:01:49,200
Try it again.

30
00:01:49,920 --> 00:01:51,480
It says, hey, it's not allowed.

31
00:01:52,080 --> 00:01:55,920
I don't recognize this, but now we have to figure out, OK, what is this application really looking

32
00:01:55,920 --> 00:01:58,260
for that for Google dot com right here.

33
00:01:58,830 --> 00:01:59,940
Obviously, it works.

34
00:02:00,390 --> 00:02:01,110
Doesn't work, is it?

35
00:02:01,110 --> 00:02:04,710
That's what dub dub, dub, dub, dub dub, Google dot com that works.

36
00:02:05,070 --> 00:02:07,740
What if I put the homosexual dot com.

37
00:02:07,930 --> 00:02:09,120
That doesn't work.

38
00:02:09,570 --> 00:02:13,930
So we start to play with it a little bit and see what things do work and what doesn't.

39
00:02:13,950 --> 00:02:15,160
So we're going to do it again.

40
00:02:15,160 --> 00:02:21,470
The homosex dot com that also isn't allowed, but there is a functionality in every browser.

41
00:02:21,510 --> 00:02:28,560
So if you actually type in a valid domain like Google dot com at a domain you want to actually direct

42
00:02:28,560 --> 00:02:31,790
with outside like that, that's actually a browser functionality.

43
00:02:31,800 --> 00:02:32,400
This would work.

44
00:02:32,400 --> 00:02:37,110
So if you do this, the user would get redirected to the website on the second hand.

45
00:02:37,110 --> 00:02:41,200
So whatever you put here is going to be what the user gets redirected to.

46
00:02:41,700 --> 00:02:43,050
So I put Yahoo!

47
00:02:43,050 --> 00:02:48,420
Dot com, whatever I put in here, dot com doesn't matter, gets ignored and we get redirected in the

48
00:02:48,780 --> 00:02:49,450
dot com instead.

49
00:02:49,710 --> 00:02:51,090
Now let's see if that trick works.

50
00:02:51,090 --> 00:02:55,950
So we're going to go back into our training site and we're going to swap out this right here with Google

51
00:02:55,950 --> 00:02:56,490
dot com.

52
00:02:56,790 --> 00:03:01,680
And we're going to tell you to bypass that and completely ignore this Google Larcombe or whatever we

53
00:03:01,680 --> 00:03:04,830
have in here and using the Hopsin at the end.

54
00:03:05,460 --> 00:03:07,440
And we're going to fit that into the application.

55
00:03:07,800 --> 00:03:12,270
And as you can see, this actually redirects the user to Nozick dot com.