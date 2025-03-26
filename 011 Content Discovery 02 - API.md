











---
# Transcript :
1
00:00:00,390 --> 00:00:04,520
Now, let's have a look at the rest of the assets that we have discovered on the home store dot com,

2
00:00:04,980 --> 00:00:10,320
one of the things that we came up with while looking at DNS, Jane, was the fact that this domain right

3
00:00:10,320 --> 00:00:13,230
here in the home store 20/20 had a deficit.

4
00:00:13,230 --> 00:00:19,770
So if we were to go to the home store 20/20 dash dev, we can see that this actually exists.

5
00:00:20,090 --> 00:00:26,460
We kind of looked for it into the other sources and it was there and only came up because we used permutations

6
00:00:27,060 --> 00:00:27,960
via DNS.

7
00:00:28,200 --> 00:00:34,470
So what we're going to do here now is, again, this site isn't showing us anything, but we're going

8
00:00:34,470 --> 00:00:35,760
to do a quick brute force again.

9
00:00:35,760 --> 00:00:37,050
We're going to use FA for this.

10
00:00:37,440 --> 00:00:39,150
We're going to use our wordlist.

11
00:00:41,460 --> 00:00:47,160
Raft, and we're going to give it this, you are all we're going to give it some threads and make it

12
00:00:47,160 --> 00:00:48,510
look pretty with see.

13
00:00:48,750 --> 00:00:50,210
Looks like I'm missing something again.

14
00:00:52,540 --> 00:00:58,030
I forgot to put fuzz at the end of the world, but let's try this out again and I was doing this thing,

15
00:00:58,030 --> 00:01:02,770
looks like API is coming back, putting a dot there for a reason, as if we look at the source of this

16
00:01:02,770 --> 00:01:03,020
page.

17
00:01:03,020 --> 00:01:06,520
There's not much there to go back, but I think we have API here.

18
00:01:06,520 --> 00:01:13,960
So it's just go ahead and see what's on API by closing stop and go to our API here and it looks like

19
00:01:13,960 --> 00:01:16,240
it comes back and says there is a server or something here.

20
00:01:16,480 --> 00:01:17,650
We're not sure what it is yet.

21
00:01:17,660 --> 00:01:21,310
I'm going to go ahead and cancel this because I've looked at this before.

22
00:01:21,580 --> 00:01:22,510
I put this example.

23
00:01:22,510 --> 00:01:25,630
I know there's nothing else, but I highly recommend if you're doing this for the first time on your

24
00:01:25,630 --> 00:01:27,250
target to let this finish.

25
00:01:27,610 --> 00:01:34,150
And for the sake of this example and to save some time, I'm going to jump ahead to do the API brute

26
00:01:34,150 --> 00:01:36,580
force thing and see what's within API that we can find.

27
00:01:36,990 --> 00:01:38,170
You can also do this manually.

28
00:01:38,170 --> 00:01:43,980
If you have seen enough APIs, you can do things like users see if anything comes up user.

29
00:01:43,990 --> 00:01:53,170
We can mainly brute force for it and see if these exist something maybe like ID counts and maybe we

30
00:01:53,170 --> 00:01:55,240
could do something like customers.

31
00:01:56,540 --> 00:02:02,090
And it looks like customers actually exist and it's giving us a verbose error that says, hey, customer

32
00:02:02,090 --> 00:02:02,930
ID is required.

33
00:02:02,930 --> 00:02:06,620
So when this comes up, there are two ways this work, it will gain all this experience.

34
00:02:06,890 --> 00:02:12,050
The more you hack on APIs, it's either something like custom data equals to one, which it looks like

35
00:02:12,050 --> 00:02:16,340
in this first case it actually worked or it could be something like sosh ID.

36
00:02:16,610 --> 00:02:17,510
You have to look for it.

37
00:02:17,750 --> 00:02:19,880
There are times when it may not give you this parameter.

38
00:02:19,880 --> 00:02:21,020
You would have to brute force for it.

39
00:02:21,020 --> 00:02:22,100
You can do this with fuzz.

40
00:02:22,320 --> 00:02:28,550
You can download a list of parameters from Cycliste and just look for using fuzz or speed up the game

41
00:02:28,550 --> 00:02:29,110
without error.

42
00:02:29,120 --> 00:02:35,750
We could pretty much guess customer ID and we can just go one, two, three, and it will give us some

43
00:02:35,750 --> 00:02:41,270
information like their phone number, email address and full name, which is considered as and it could

44
00:02:41,270 --> 00:02:46,160
get us a pretty good bounty because of the fact that it's leaking information that belongs to other

45
00:02:46,160 --> 00:02:47,740
users that we shouldn't be able to see.