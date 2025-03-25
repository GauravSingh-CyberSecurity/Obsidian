Looking for XSS where ever we can find input fields, using basic payload ` ""><U>test123" `
if this payload gets executed the result will show test123(as underlined text) 

using browser dev tools>inspect element , and look for input payloads see the input in Js body, script, 

1
00:00:00,550 --> 00:00:08,250
I copied out into this and we're going to go to shop and, ahem, store them because there is some functionality

2
00:00:08,250 --> 00:00:08,580
here.

3
00:00:08,850 --> 00:00:14,580
There's home, there is a turn's where you can put an order, no log in.

4
00:00:14,580 --> 00:00:17,520
And obviously there's registration and we can create a new account.

5
00:00:17,910 --> 00:00:19,500
And then there is your card as well.

6
00:00:19,900 --> 00:00:25,080
So this is looking at this website without even logging in, I see a search for products, so anywhere

7
00:00:25,080 --> 00:00:26,790
that I can put in user input.

8
00:00:27,030 --> 00:00:31,650
So I mean, anybody that can type in any text, I would like to look for a cross scripting.

9
00:00:31,980 --> 00:00:38,970
And as I've always said, I'd like to start with a ASML tag and a test one, two, three to get it started.

10
00:00:38,970 --> 00:00:39,920
So I type that in.

11
00:00:40,320 --> 00:00:47,760
It's going to come back and say, hey, that wasn't found, but it looks like we are getting some text

12
00:00:47,760 --> 00:00:56,120
reflected back when I open up our inspect element and we are going to look for test one, two, three.

13
00:00:56,520 --> 00:01:00,030
It looks like we are within a H3 tag.

14
00:01:00,690 --> 00:01:02,010
Not so much to do there.

15
00:01:02,340 --> 00:01:07,320
And if we look down here, we're it looks like we're in a JavaScript tag, in a script tag assigned

16
00:01:07,320 --> 00:01:13,980
to a variable card search, which does some stuff with it and then makes another call at the bottom.

17
00:01:13,980 --> 00:01:18,330
But it looks like it's actually taking are less than or greater than signs.

18
00:01:18,850 --> 00:01:24,370
So these two right here or these three actually right here and it's actually encoding them.

19
00:01:24,390 --> 00:01:25,890
So that means that it's not working.

20
00:01:26,160 --> 00:01:31,440
But if you look at the context of worryin, again, when it comes down to looking for Zarzis context,

21
00:01:31,440 --> 00:01:32,790
it's very, very important.

22
00:01:33,030 --> 00:01:39,330
Just because these three characters were encoded, as I mean, that we can't still look for other stuff.

23
00:01:39,330 --> 00:01:43,850
So if you can see, we are between single quotes, not double quotes and an apostrophe.

24
00:01:43,860 --> 00:01:49,050
So what I'm going to do is I'm going to add the same exact syntax and I'm going to see what comes back.

25
00:01:49,560 --> 00:01:56,940
If the other two additional characters, the apostrophe and the semicolon, they came back as encoded,

26
00:01:56,940 --> 00:01:57,870
then we can move on from it.

27
00:01:57,870 --> 00:02:00,330
But that's the kind that really quickly test one, two, three.

28
00:02:00,330 --> 00:02:02,970
It looks like it actually added our tax.

29
00:02:02,970 --> 00:02:08,510
If we look at this right here, it looks like the apostrophe and the semicolon were both taken.

30
00:02:08,520 --> 00:02:11,770
So I'm going to do is I'm going to comment the rest of it out.

31
00:02:11,780 --> 00:02:16,470
So whatever it was originally there, I'm going to comment it up and we're going to go back to it again

32
00:02:17,970 --> 00:02:19,350
by typing test one, two, three.

33
00:02:19,920 --> 00:02:23,970
And we can see that the second one to the first set, that's one right here.

34
00:02:24,360 --> 00:02:26,520
This apostrophe and semicolon were given by me.

35
00:02:26,860 --> 00:02:32,910
Everything after the the two sashays were there by default and the application it was in the source

36
00:02:32,910 --> 00:02:33,140
of it.

37
00:02:33,450 --> 00:02:38,910
So now I'm going to just add my again, this is something that we covered earlier in our other chapters,

38
00:02:39,030 --> 00:02:43,920
going out an alert to it and see if it works and looks like something just broke.

39
00:02:45,530 --> 00:02:52,280
And way to make room to fix it, so we're going to go ahead and add another apostrophe before it because

40
00:02:52,280 --> 00:02:56,680
we're in JavaScript, we know that that's how they end everything and already had an apostrophe.

41
00:02:56,690 --> 00:02:57,520
We didn't put it there.

42
00:02:57,830 --> 00:02:59,810
I think this time I should give it to us right there.

43
00:02:59,810 --> 00:03:06,830
As you can see, we gave it a valid syntax for our JavaScript and actually did alert later on.

44
00:03:06,840 --> 00:03:10,790
We'll probably cover some other stuff with JavaScript, but it's a good example of how you can actually

45
00:03:10,790 --> 00:03:14,810
discover a vulnerability for exercise and how to look for it.

46
00:03:14,810 --> 00:03:18,370
And Chase said through the DOM, not that we know there is a vulnerability here.

47
00:03:18,380 --> 00:03:19,400
This is a pretty obvious one.

48
00:03:19,410 --> 00:03:21,710
The first thing we did was look at the search box.

49
00:03:21,920 --> 00:03:25,700
I know it sounds unrealistic, but trust me, there's been a ton of times when I've been invited to

50
00:03:25,700 --> 00:03:31,550
a private program, a new program where I found some really weird subdomain that things like that existed

51
00:03:31,550 --> 00:03:32,510
and it was exploitable.

52
00:03:32,720 --> 00:03:36,520
It may be a dupe, but that means there are other vulnerabilities to look for.