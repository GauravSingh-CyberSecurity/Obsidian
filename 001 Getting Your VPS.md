
1
00:00:00,060 --> 00:00:05,460
So before we get started with a lab setting, the first thing I want to do is you want to find a terminal

2
00:00:05,660 --> 00:00:06,480
illness terminal.

3
00:00:06,480 --> 00:00:09,090
To be more specific, you can do this in two ways.

4
00:00:09,390 --> 00:00:11,550
One is you can download Pudi on this.

5
00:00:11,550 --> 00:00:17,970
Sure, you link it in the resource section or you can actually download a Windows subsystem through

6
00:00:17,970 --> 00:00:18,870
the Microsoft store.

7
00:00:19,100 --> 00:00:25,530
But before we do that, you have to make sure you going to your futures turn off or on a future in your

8
00:00:25,770 --> 00:00:29,890
settings and you want to make sure that you have this thing on.

9
00:00:29,910 --> 00:00:33,360
So it needs to be set to open Windows subsystem for Linux.

10
00:00:33,780 --> 00:00:35,480
Once you do, this is going to ask to reboot.

11
00:00:35,490 --> 00:00:38,900
You go out and reboot and you come back to this screen and then you want to go to the Microsoft store.

12
00:00:38,910 --> 00:00:45,990
So we want to type and store Microsoft store and we're just gonna type in Linux and see what's available

13
00:00:45,990 --> 00:00:46,410
to us.

14
00:00:46,860 --> 00:00:49,920
Most people and infosec enjoy using Linux.

15
00:00:50,340 --> 00:00:52,530
I'm one of the odd people that doesn't enjoy it.

16
00:00:52,860 --> 00:00:54,510
I prefer to use a bone to.

17
00:00:54,510 --> 00:00:55,620
It's a personal preference.

18
00:00:55,620 --> 00:00:57,630
You can use whatever one you're more comfortable with.

19
00:00:58,090 --> 00:01:03,780
I personally enjoy going to for different reasons, one of them being that there are tons and tons of

20
00:01:04,020 --> 00:01:09,510
resources out there for me to read and get better when you get stuck on a particular thing.

21
00:01:10,050 --> 00:01:14,070
When I push, get it install, it's going to ask you to log in.

22
00:01:14,340 --> 00:01:15,480
You can pick it, do it or not.

23
00:01:15,480 --> 00:01:19,940
I'm just gonna say no thanks for the sake of this material and we're just going to install it.

24
00:01:20,310 --> 00:01:22,640
So now that you haven't installed a few things you can do, no.

25
00:01:22,650 --> 00:01:28,200
One thing is we're going to go in here and type in Ubuntu that will pull up the Ubuntu terminal.

26
00:01:28,530 --> 00:01:32,550
This is where you can access it into your cloud service, whatever you're using.

27
00:01:32,550 --> 00:01:38,850
I personally prefer to use a VPs, which is a virtual private server I hosted in the cloud for different

28
00:01:38,850 --> 00:01:39,420
reasons.

29
00:01:39,600 --> 00:01:44,820
No one being that you don't want to get your IP blocked, for example, if you're hacking on our website

30
00:01:44,820 --> 00:01:49,860
to have some firewall, but also often online store use as if you're IP gets blocked on one of these

31
00:01:49,860 --> 00:01:53,460
websites, then you can't access any other customers of theirs.

32
00:01:53,730 --> 00:01:57,000
That means you can't shop online or do your day to day work.

33
00:01:57,000 --> 00:02:00,090
So I highly recommend using a virtual private server.

34
00:02:00,090 --> 00:02:04,890
You want to use a virtual private server because some of the tools may not work with a subsystem.

35
00:02:05,220 --> 00:02:06,780
So you have different options.

36
00:02:07,000 --> 00:02:12,210
Again, I just installed a subsystem on Windows, just second situation to my box.

37
00:02:12,210 --> 00:02:17,310
And if you have Linux, you have a VM, you like to use some other OS that also works.

38
00:02:17,310 --> 00:02:18,440
There is no right or wrong here.

39
00:02:18,460 --> 00:02:21,750
It's just personal preference, what you're good with and what you want to do.

40
00:02:22,410 --> 00:02:24,900
For the sake of this, I like to use the Windows terminal.

41
00:02:25,110 --> 00:02:30,870
I'll make sure to leave a link in the second and the resource sections so I can also have access to

42
00:02:30,870 --> 00:02:31,110
it.

43
00:02:31,110 --> 00:02:32,400
It just looks a little bit better.

44
00:02:32,400 --> 00:02:33,570
It's more customizable.

45
00:02:34,710 --> 00:02:36,720
I use it for a while now.

46
00:02:36,720 --> 00:02:37,350
I enjoy it.

47
00:02:37,350 --> 00:02:38,280
It's more smooth.

48
00:02:39,000 --> 00:02:43,650
I'll make sure to leave a link down below so you can also follow along and make sure you make it look

49
00:02:43,650 --> 00:02:46,680
like this so that we are going to go to Digital Ocean.

50
00:02:49,040 --> 00:02:50,480
We're going to open up our Google Chrome.

51
00:02:56,390 --> 00:03:01,490
We're going to create a new account, and again, I'm going to make sure to link my personal referral

52
00:03:01,490 --> 00:03:01,790
link.

53
00:03:01,940 --> 00:03:05,150
You don't have to use it, but if you do, you get one hundred dollars of free credit.

54
00:03:05,420 --> 00:03:09,500
And if you spend some money, they would also give me 25 dollars for my account.

55
00:03:09,500 --> 00:03:12,970
What I will use it for different research, hacking purposes and so on.

56
00:03:13,450 --> 00:03:14,650
You're going to sign up for an account?

57
00:03:14,870 --> 00:03:16,650
I'm not going to do this portion is super easy.

58
00:03:16,670 --> 00:03:20,720
You can sign up with a Google account, you can sign up with GitHub, or you can just sign up with your

59
00:03:20,720 --> 00:03:21,090
email.

60
00:03:21,140 --> 00:03:26,690
So when you go into this resource page, it's going to say research for me, because this is a project

61
00:03:26,690 --> 00:03:28,970
that I'm in can see I have different projects.

62
00:03:28,970 --> 00:03:31,970
It's going to look similar regardless of what project you're in.

63
00:03:32,310 --> 00:03:35,390
We're going to go to create and you're going to deploy a droplet.

64
00:03:35,700 --> 00:03:40,280
This is where you get to pick what kind of server you want and you have until you can you figure see

65
00:03:40,280 --> 00:03:42,170
a fedora centaurus, whatever you're into.

66
00:03:42,500 --> 00:03:48,710
For the purpose of this tutorial, we're going to stick to Ubuntu and we're going to do a semi decent

67
00:03:48,710 --> 00:03:49,180
server.

68
00:03:49,190 --> 00:03:50,470
You can start with five dollars.

69
00:03:50,480 --> 00:03:53,300
This is the one that I started with when I first got it into hacking.

70
00:03:53,300 --> 00:03:57,920
The differences in the resources you get to, the more work you put on the server, obviously, the

71
00:03:57,920 --> 00:04:00,710
better and the higher number of resources you want to give it.

72
00:04:01,070 --> 00:04:07,790
Right now, as I do most of my hacking, I use this box with 16 gigs of RAM, eight CPU's and a ton

73
00:04:07,790 --> 00:04:10,400
of SSD, but you can decide which one you want to use.

74
00:04:10,410 --> 00:04:15,950
But for the sake of this tutorial, we're going to go ahead and stick to the fifteen dollars a month

75
00:04:15,950 --> 00:04:18,500
with two gigs of RAM and into CPU's.

76
00:04:18,860 --> 00:04:22,030
And if you're in a different country, you want to get it closer to where you are.

77
00:04:22,300 --> 00:04:25,950
You can pick different countries or different areas that may be closer to you.

78
00:04:26,150 --> 00:04:30,830
I don't think it makes a huge difference for hacking, but this is also, again, personal preference.

79
00:04:31,270 --> 00:04:31,940
The private key.

80
00:04:31,940 --> 00:04:33,620
You can click on the private key here.

81
00:04:33,880 --> 00:04:40,310
We can just give it a password and set up whatever password you want for your S.H. When you log in for

82
00:04:40,310 --> 00:04:42,280
the first time, you can also give it a hostname.

83
00:04:42,290 --> 00:04:45,230
We're going to call this information like training.

84
00:04:45,620 --> 00:04:50,050
That's a matter you can name it whatever you want or leave it as it is, can add tags.

85
00:04:50,060 --> 00:04:50,690
I don't need that.

86
00:04:50,690 --> 00:04:51,710
We don't need backups.

87
00:04:52,190 --> 00:04:53,750
We just want to make sure we have everything right.

88
00:04:53,750 --> 00:04:55,730
So it looks like it's not liking my password.

89
00:04:55,820 --> 00:05:01,400
Now we're going to click create password or create droplet and it's going to take a few seconds.

90
00:05:01,760 --> 00:05:07,580
But after a while it will give us an IP address and we can use it to log in the our terminal.

91
00:05:07,700 --> 00:05:09,740
Again, you don't have to install Ubuntu.

92
00:05:09,770 --> 00:05:11,930
You don't have to use Windows subsystem.

93
00:05:12,230 --> 00:05:16,400
Can you do about your PC, have callisthenics on one side, you can do a VM.

94
00:05:16,610 --> 00:05:18,650
You don't really even need to get a VPs.

95
00:05:18,980 --> 00:05:23,450
Most hackers do just because it helps to have two different environments.

96
00:05:23,690 --> 00:05:25,100
So now we have our IP address.

97
00:05:25,340 --> 00:05:27,350
We're going to log in to it with our router account.

98
00:05:27,640 --> 00:05:28,750
I do the DP.

99
00:05:28,760 --> 00:05:33,200
In some cases you may not need it, but the way my account is set up, I believe with the DP, which

100
00:05:33,200 --> 00:05:36,650
says ask for a password, we're going to put in our password.

101
00:05:36,770 --> 00:05:37,430
Let's try it again.