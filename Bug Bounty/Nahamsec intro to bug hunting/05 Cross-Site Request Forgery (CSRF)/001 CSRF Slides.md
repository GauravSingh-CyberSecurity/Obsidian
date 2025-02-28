









---

1
00:00:00,570 --> 00:00:06,330
The next vulnerability we're going to look for is CSRF short for a cross site request forgery.

2
00:00:06,750 --> 00:00:14,070
So what is CSIRO and CSIRO vulnerability allows an attacker to perform an action on a victim's behalf

3
00:00:14,100 --> 00:00:15,290
without them knowing it.

4
00:00:15,720 --> 00:00:22,890
The difference between CSF and exercise is that you can't actually still any data, but you can just

5
00:00:22,890 --> 00:00:27,530
force the user to perform some action without them knowing that it happened.

6
00:00:28,080 --> 00:00:30,030
So, again, this could be changing password.

7
00:00:30,060 --> 00:00:31,450
This could be transferring money.

8
00:00:31,680 --> 00:00:34,410
It's an action, but you can't actually still data from it.

9
00:00:34,410 --> 00:00:35,670
You can't see anything in return.

10
00:00:35,940 --> 00:00:39,870
You can just have them do some stuff because of the way that the application works.

11
00:00:40,210 --> 00:00:41,330
So that's the kind of example.

12
00:00:42,060 --> 00:00:48,090
Think about having a adjust field where you go to your user profile, you want to change your email

13
00:00:48,090 --> 00:00:48,630
address.

14
00:00:48,960 --> 00:00:52,350
You see a box like the one on the screen says new email address.

15
00:00:52,350 --> 00:00:53,700
You type it and you push submit.

16
00:00:54,120 --> 00:00:58,620
An attacker can actually force the user to do this thing without them knowing.

17
00:00:58,830 --> 00:01:02,400
But you can't actually see what's in that email address bar already.

18
00:01:02,400 --> 00:01:07,350
With Exercice, you have the ability to write JavaScript and within JavaScript you can tell the application

19
00:01:07,350 --> 00:01:11,510
to perform separate things or actually pull data and send it back to your server.

20
00:01:11,520 --> 00:01:13,660
So if you are proficient in JavaScript, thanks.

21
00:01:13,680 --> 00:01:19,020
It says could be very, very valuable to you, which is a CSR if it can only change data and that's

22
00:01:19,020 --> 00:01:19,480
about it.

23
00:01:19,890 --> 00:01:24,870
So again, if you put in the email address field, if you don't actually have some sort of random CSF

24
00:01:24,870 --> 00:01:30,180
token or some sort of protection, then the attacker could force the user to change your email address.

25
00:01:30,390 --> 00:01:33,630
So it's just going to have to always necessarily be within a form.

26
00:01:33,660 --> 00:01:36,470
This could also be actions that are done within a get request.

27
00:01:36,720 --> 00:01:41,700
These are not typically common, but I've also seen some of applications still rely on this method to

28
00:01:41,700 --> 00:01:42,660
move data around.

29
00:01:42,990 --> 00:01:47,640
So let's think about a bank, for example, where it's using by that FB and saying, hey, I want you

30
00:01:47,640 --> 00:01:53,730
to transfer money from this wallet, this amount in this type Bitcoin, and we can swap out the wallet

31
00:01:53,730 --> 00:01:57,150
for the attackers wallet where the money gets transferred to them instead.

32
00:01:58,590 --> 00:02:04,800
So, again, that's one example of what we can do here is on a website that the attacker is controlling.

33
00:02:04,800 --> 00:02:09,630
We can put an image tag or hyperlink where as soon as the victim visits it or clicks on that link,

34
00:02:09,840 --> 00:02:15,630
it performs an action for us when we're within a form or we have to do instead of a link or an image

35
00:02:15,630 --> 00:02:18,120
tag, we actually have to recreate that form.

36
00:02:18,300 --> 00:02:21,480
And as soon as the user clicks on it, that action is performed.

37
00:02:21,580 --> 00:02:25,080
And all this will make sense once we do our live and our practice examples.

38
00:02:25,350 --> 00:02:27,600
But for now, let's just stick to the example we have on the screen.

39
00:02:27,840 --> 00:02:33,720
In some cases, you may see that a website has some sort of a CSR protection, some token.

40
00:02:34,020 --> 00:02:36,960
It could be either reused, it could be random.

41
00:02:36,960 --> 00:02:39,840
You just have to understand how that protection mechanism works.

42
00:02:40,140 --> 00:02:45,900
So in a lot of cases, what I have seen is that a lot of applications define a CSR token as CSR token,

43
00:02:45,900 --> 00:02:50,940
as some sort of a signature, something that says, hey, this token belongs to this user.

44
00:02:51,030 --> 00:02:54,090
As long as this token is there and others, words can use it.

45
00:02:54,090 --> 00:02:59,030
And I confirms that this action is actually intended by the user, that it's making it.

46
00:02:59,370 --> 00:03:04,260
So I think it has a signature that says, hey, I am this user, here's my signature.

47
00:03:04,290 --> 00:03:05,610
I want to perform this action.

48
00:03:06,030 --> 00:03:11,580
But what I've seen in other cases is that either one that token or the signature, whatever you want

49
00:03:11,580 --> 00:03:13,260
to call it, could be reused.

50
00:03:13,260 --> 00:03:19,340
So you can have the token from user A B used on user B and actually allows you to exploit it.

51
00:03:19,380 --> 00:03:22,890
So all you have to do is make sure you get a valid token, you swap it out.

52
00:03:22,890 --> 00:03:27,570
Is that the victim, the victim clicks on the form, on the link or whatever it is, and the action

53
00:03:27,570 --> 00:03:28,110
performs.

54
00:03:28,620 --> 00:03:35,160
The other one that I've seen a lot of cases is even though there is a CSR token in the you are if you

55
00:03:35,160 --> 00:03:40,170
completely remove the entire parameter that still works, it's just there to make it look like there's

56
00:03:40,170 --> 00:03:42,450
a protection, what actually doesn't do anything.

57
00:03:42,840 --> 00:03:47,700
So, for example, in this one, we want to say, hey, the form we're going after is located on by

58
00:03:47,700 --> 00:03:50,400
that B and expects the method post.

59
00:03:50,820 --> 00:03:55,320
There's going to be a bunch of different parameters and values that it's expecting like a wallet.

60
00:03:55,590 --> 00:04:01,470
It's expecting the amount, it's expecting type, it's expecting a CSR of token, as in this example,

61
00:04:01,470 --> 00:04:03,360
we've identified that we can reuse it.

62
00:04:03,720 --> 00:04:07,830
And also it is a button that says submit and you click click here to win.

63
00:04:08,250 --> 00:04:11,910
The attacker created this and the victim just clicks on it.

64
00:04:11,910 --> 00:04:16,710
And as soon as they click on it, it performs that action and sends all this information to this by

65
00:04:17,400 --> 00:04:18,450
using a post request.

66
00:04:18,780 --> 00:04:20,940
This is something that I've seen on some other applications.

67
00:04:20,940 --> 00:04:22,230
It's not very, very common.

68
00:04:22,230 --> 00:04:27,130
But a lot of times the encoding or the way they create these signatures are easily guessable.

69
00:04:27,420 --> 00:04:33,510
So in this example, if you actually decode the string that's on the screen starting in E three to base64

70
00:04:33,510 --> 00:04:37,430
that's encoded into the user ID, whereas user ID 44.

71
00:04:37,740 --> 00:04:42,810
So you just have to understand how this sort of token mechanism works, how you're protecting against

72
00:04:42,810 --> 00:04:44,460
it, and how can you actually break it.

73
00:04:44,670 --> 00:04:46,440
In some cases you may be successful.

74
00:04:46,680 --> 00:04:48,990
In others, you may not have the best luck.