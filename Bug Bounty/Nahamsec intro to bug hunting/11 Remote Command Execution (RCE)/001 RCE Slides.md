



---

# Transcript :

1
00:00:00,180 --> 00:00:04,920
Let's have a look at remote command execution, also known as RC, so remote command execution is a
![[Screenshot From 2025-03-10 10-05-07.png]]
2
00:00:04,920 --> 00:00:09,770
broad term that's applied to a vulnerability that allows an attacker to execute commands on the host

3
00:00:09,780 --> 00:00:12,600
operating system via the vulnerable application.

4
00:00:12,990 --> 00:00:14,690
This can be done in a number of ways.

5
00:00:14,700 --> 00:00:19,890
It could be either injecting a command or also it could be done by injecting code that the application

6
00:00:19,890 --> 00:00:23,010
is expecting that could lead into command execution.

7
00:00:23,400 --> 00:00:25,040
Again, this is a very broad term.

8
00:00:25,050 --> 00:00:29,250
It could happen a number of different ways, but we're going to cover the most popular and common ways

9
00:00:29,250 --> 00:00:30,450
of finding an RC.

10
00:00:31,800 --> 00:00:39,960
So imagine you're going to a website where the application is looking for the stock if an item is available.

11
00:00:40,230 --> 00:00:45,060
We're just guessing that in the background there, running some command on the operating host, on the

12
00:00:45,060 --> 00:00:49,020
operating system host, and it's going to check if this exists.

13
00:00:49,170 --> 00:00:56,010
So if you're looking for the ID five one four one, our assumption is that in the back end there's going

14
00:00:56,010 --> 00:01:02,610
to be a command that's running another application on the hose that says, hey, I'm here to look for

15
00:01:02,610 --> 00:01:07,290
run this application and give it a value for five one for one.

16
00:01:07,810 --> 00:01:13,350
So it comes back and it says three items are available and that's what's being given to the user.

17
00:01:15,120 --> 00:01:19,160
So what we can do in this case, we're going to start fuzzing and we're going to start messing with

18
00:01:19,170 --> 00:01:22,280
it to see if there is a remote command execution in this case.

19
00:01:22,290 --> 00:01:24,330
And it doesn't have to be numerical IDs.

20
00:01:24,550 --> 00:01:30,330
It could be anywhere that we think this application may rely on a another application that's being run

21
00:01:30,330 --> 00:01:33,930
on the operating system to retrieve the data that's being shown to our user.

22
00:01:34,260 --> 00:01:38,770
So in this case, we're going to end our previous command in a Linux environment.

23
00:01:38,790 --> 00:01:41,310
You can do this a number of ways which will cover later on.

24
00:01:41,550 --> 00:01:46,710
But one of the most popular ways of doing this is a semicolon, which says, hey, this is command is

25
00:01:46,710 --> 00:01:47,060
done.

26
00:01:47,070 --> 00:01:48,750
I want to add another one right after this.

27
00:01:48,760 --> 00:01:54,670
So we do semicolon and we give it the URLs, which is the list of files within the directory.

28
00:01:55,020 --> 00:02:00,180
Again, if you're not familiar with these commands, I highly recommend you looking into getting very

29
00:02:00,180 --> 00:02:02,090
familiar with Linux operating system.

30
00:02:02,100 --> 00:02:03,840
You can do a boon to can you carry Linux?

31
00:02:04,080 --> 00:02:09,740
It's very beneficial just to have remote command execution, to be good at Linux in general.

32
00:02:10,110 --> 00:02:11,970
But let's look at this example again.

33
00:02:11,970 --> 00:02:19,890
We give it our value five one for one semicolon to ended and we say else which executes our Linux come

34
00:02:19,890 --> 00:02:22,410
in and it comes back and says three items are available.

35
00:02:22,560 --> 00:02:25,680
But also here is the output for the last command.

36
00:02:26,130 --> 00:02:32,220
So we get the list of every file, every folder within that folder that we're working on.

37
00:02:33,200 --> 00:02:38,910
I get that folder that we're in is wherever the second application that's being ran in the back end

38
00:02:38,910 --> 00:02:39,470
is hosted.

39
00:02:39,480 --> 00:02:43,500
So in this case, whatever that folder name is, wherever that path of it is, we're going to get a

40
00:02:43,500 --> 00:02:49,830
list of items within that directory so we get indexed FB images, access and access.

41
00:02:50,160 --> 00:02:55,920
So as I mentioned earlier, there are different methods where you can actually separate commands.

42
00:02:55,920 --> 00:02:57,530
One of them could be the semicolon.

43
00:02:57,560 --> 00:03:01,290
It could be the answer and it could be two of them could be a pipe or a double pipe.

44
00:03:01,450 --> 00:03:07,890
You can use all of those to run a command by finishing the previous one and adding another one for the

45
00:03:07,890 --> 00:03:10,460
second one you can do is abash in line execution.

46
00:03:10,470 --> 00:03:12,940
Again, highly recommend getting good at Basche.

47
00:03:12,960 --> 00:03:17,790
It would help you if you're looking for our series, which what it does is it was inline within the

48
00:03:17,790 --> 00:03:23,910
same command run, a secondary command and also output etes which will output its results again with

49
00:03:23,910 --> 00:03:24,330
backgrounders.

50
00:03:24,330 --> 00:03:28,920
You want to be very careful with what commands you run on these posts.

51
00:03:28,920 --> 00:03:32,490
You don't want to run the wrong command and cause an outage.

52
00:03:32,710 --> 00:03:34,650
So these are the four commands that I typically use.

53
00:03:34,830 --> 00:03:39,480
There's a Puedes, which is the printing which prints the working directory.

54
00:03:39,480 --> 00:03:43,860
Whatever you are working, whatever the application is hosted, it's going to come back and give you

55
00:03:44,190 --> 00:03:46,170
that directory, the unified command.

56
00:03:46,170 --> 00:03:51,840
I usually use the new namespace A this comes back and gives you basic information about the operating

57
00:03:51,840 --> 00:03:52,380
system.

58
00:03:53,370 --> 00:03:58,620
The ID command tells you about the user, what group Derian, what user you are and the numeric ID.

59
00:03:58,980 --> 00:04:04,410
And last but not least hostname, which prints the machines hostname and domain name within the DNS

60
00:04:04,410 --> 00:04:09,150
and tells you this is the applications hostname that's given to the operating system.

61
00:04:09,150 --> 00:04:13,620
And of course we just covered all of the different ways of doing OS commands.

62
00:04:13,860 --> 00:04:18,840
So we are executing operating system commands, but you can actually do this within different programming

63
00:04:18,840 --> 00:04:19,440
languages.

64
00:04:19,680 --> 00:04:27,660
So if you have the opportunity to execute and inject a script within a Web site, you can use functionalities,

65
00:04:27,930 --> 00:04:35,790
you can use functions like Shell exec, exec or different ones to actually execute a operating system

66
00:04:35,790 --> 00:04:36,630
command using.

67
00:04:37,290 --> 00:04:41,940
That's also another way that's very common when it comes down to looking for our CS the game.

68
00:04:41,940 --> 00:04:45,960
Before we wrap this chapter, I want to make sure you understand that RC is a very broad term.

69
00:04:46,110 --> 00:04:47,970
You can find them in a different number of ways.

70
00:04:47,970 --> 00:04:50,100
It could be in file uploads, which we'll cover later on.

71
00:04:50,340 --> 00:04:53,820
It could be by modifying side content, it could be debug functionalities.

72
00:04:54,180 --> 00:04:59,490
There are tons of tons of different ways of doing it by the end of the day and some similar ways to

73
00:04:59,490 --> 00:04:59,910
what we have.

74
00:05:00,240 --> 00:05:00,750
So far.