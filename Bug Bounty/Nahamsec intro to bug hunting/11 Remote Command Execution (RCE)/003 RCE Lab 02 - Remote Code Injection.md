Analysis of RCE lab :- ( http://rce2.naham.sec:8081/ )


==RCE Lab 02== :-  ( http://rce2.naham.sec:8081/ )

Now, let's look at our second example for remote command execution. In this case, it's no longer an ID; it's an application that performs networking. 
For example, it’s going to ping the IP address 8.8.8.8, and then it will return the result of the ping command.
![[Screenshot From 2025-03-10 20-34-53.png]]

Again, this is a command available on both Windows and Linux. It will ping that IP address and give us the results. 


Now, what happens if we pipe( `|` ) and ask for the results of the ping, but also for the results of the command `id`
![[Screenshot From 2025-03-10 20-35-48.png]]

![[Pasted image 20250310204155.png]]
Sure enough, after it's done pinging, it will return the output for the command:  `id`  , 


and, as mentioned, we can also use “uname -a.” It will execute the commands; and then immediately run “uname -a” to give us our results.
![[Screenshot From 2025-03-10 20-39-31.png]]
![[Screenshot From 2025-03-10 20-41-20.png]]


Last but not least, one of my favorites:
**==RCE Lab 03==** ( http://rce3.naham.sec:8081/ )
==this is how you can perform code injection==. We’re no longer injecting a simple Linux command into this website; instead, ==we’re going to inject code==. I have been using this application for a while. Every time I make a request, I understand that it executes certain functions, so we can add a comment and then examine the network tab.  (for me, i am using burp suite and below is the SS)
![[Screenshot From 2025-03-11 10-24-21.png]]

We see here that it's making a request—let's try it again.  (after sending it to Burp repeater for further testing),  It's making an Ajax request (comment=test), sending out our comment as data. 
![[Screenshot From 2025-03-11 10-27-52.png]]

click on **"follow redirection"** : (and you get response as shown below)
![[Screenshot From 2025-03-11 10-29-12.png]]
We can assume this is in "PHP" its still one of the common languages(or we can use Wappalyzer browser extension to find the coding language used on appliaction). You still sometimes see this in bug bounty web applications.

Now, whatever we put in Load comments drop down—for example we select **11/03/25**, the application is going to load our comment for that date and time selected :-
![[Screenshot From 2025-03-11 10-34-58.png]]

The next thing we can do is, because we know that for whatever reason, this application expects code—perhaps the developers did not properly sanitize user input—we discovered that we can inject code here. So I'm going to inject "PHP" code in here .

If you're not familiar with PHP, I highly recommend you visit https://www.php.net/ to learn about its basic functions. One common tactic is using the echo command. We’re going to echo out the string "test" just to verify that our command is executed, and then we’ll close our PHP code to see what happens.

When we go back, we see that it printed "test" as the output of echo without any errors or extra characters—it simply executed our code.

One of the most popular and common ways to verify code injection with PHP is to insert an info command that provides details such as the IP address, the Linux version, etc. This proves that the application is executing our injected code. We can also try this approach using Python, Ruby, or any other language, depending on what the backend uses, in the hope that it will evaluate and execute our code on the server.

In summary, as we examine our comment, we see that instead of printing out our code, the application is actually executing it and returning information (like version, system details, etc.). This clearly demonstrates that code injection is occurring on the server.


---

# Transcript :

1
00:00:00,180 --> 00:00:05,910
Now, let's look at our second example, foreign policy in this case, it's no longer an I.D. It's an

2
00:00:05,910 --> 00:00:10,560
application that does some networking, for example, it's going to do ping and it's going to be paying

3
00:00:10,560 --> 00:00:13,190
the IP address, eight point eight point eight point eight.

4
00:00:13,680 --> 00:00:19,230
So we're going to ping it and it's going to give us a result from a ping command.

5
00:00:19,500 --> 00:00:22,470
Again, this is a command that exists on both Windows and Linux.

6
00:00:23,010 --> 00:00:25,800
Are they going to ping out that his IP address and give us the results?

7
00:00:26,430 --> 00:00:32,220
So what happens now if we pipe and say, give me the results for Ping, but also give me the results

8
00:00:32,220 --> 00:00:33,270
for the command ID?

9
00:00:35,890 --> 00:00:41,770
And sure enough, after it's done pinging, it's going to come back and give us the output for the command

10
00:00:41,770 --> 00:00:45,010
ID and again, I'll have to always be that we can do you named Dash.

11
00:00:45,670 --> 00:00:46,450
It's going to do its thing.

12
00:00:46,450 --> 00:00:47,260
It's going to take a while.

13
00:00:47,260 --> 00:00:48,670
It's going to finish doing the you name.

14
00:00:49,090 --> 00:00:51,670
It's going to sorry, it's going to finish doing the ping.

15
00:00:51,940 --> 00:00:53,470
But right after that it's going to run.

16
00:00:53,740 --> 00:00:56,800
You named Ashleigh and give us our results.

17
00:00:57,160 --> 00:00:58,930
Last but not least, one of my favorites.

18
00:00:59,200 --> 00:01:04,360
This is how you can actually write and code, which is a code injection.

19
00:01:04,360 --> 00:01:10,720
So we're no longer are injecting a actual Linux command within this website, but instead we are going

20
00:01:10,720 --> 00:01:12,280
to go ahead and inject.

21
00:01:13,270 --> 00:01:17,110
So in this case, I've been using for this I've been using this application for a while.

22
00:01:17,380 --> 00:01:24,130
Every time I make a request, I've understood that they do things and so we can make a comment and we're

23
00:01:24,130 --> 00:01:25,510
going to look at a network tab.

24
00:01:26,890 --> 00:01:28,720
We see here that it's making a request.

25
00:01:28,720 --> 00:01:29,440
Let's try it again.

26
00:01:31,780 --> 00:01:33,370
We can suggest making some request.

27
00:01:35,530 --> 00:01:42,750
Right here, it's making an Ajax request, sending it out, and it's getting the comment as the ADA

28
00:01:42,750 --> 00:01:43,590
is going out.

29
00:01:44,340 --> 00:01:47,580
We're going to guess this is a it's one of the common languages.

30
00:01:48,000 --> 00:01:52,530
You still sometimes see him and some of the bug bounty web applications.

31
00:01:52,990 --> 00:01:54,850
But let's see what happens here for the load coming.

32
00:01:54,870 --> 00:02:01,260
So right now, whatever we put in here, let's look at this one, for example, with says it's going

33
00:02:01,260 --> 00:02:06,180
to load our command or sorry, it's going to load our comment for whatever we put in here.

34
00:02:06,430 --> 00:02:11,280
The next thing we can do, because we know that for whatever for whatever reason, this application

35
00:02:11,280 --> 00:02:12,090
expects codes.

36
00:02:12,360 --> 00:02:16,010
Maybe the developers didn't do the proper way of sanitizing user input.

37
00:02:16,290 --> 00:02:21,210
We figured out that, hey, I can actually put in code in here, so I'm going to put it up again.

38
00:02:21,210 --> 00:02:26,490
If you're not familiar with HP, I highly recommend you go into a PSP dot net and learning a little

39
00:02:26,490 --> 00:02:28,800
bit about the basic functions of PHP.

40
00:02:29,190 --> 00:02:32,630
But one of the things you can do is like any other language, you can do echo.

41
00:02:32,940 --> 00:02:39,630
And we're going to echo out the string test just to test the harmonic and then we're going to close

42
00:02:39,630 --> 00:02:42,120
out our IP code and see where this goes.

43
00:02:42,510 --> 00:02:46,960
So again, I'm going to go back here and consider it printed, test the Hunsecker.

44
00:02:46,980 --> 00:02:48,090
They didn't give us an error.

45
00:02:48,210 --> 00:02:50,160
They didn't put on the stuff around that.

46
00:02:50,330 --> 00:02:53,830
It just literally took our code and executed whatever was within it.

47
00:02:54,300 --> 00:03:02,910
So one of the most popular and common words of actually verifying code injection with PCP's to insert

48
00:03:03,420 --> 00:03:08,340
that info, which gives you information about the IP versions on the Linux box.

49
00:03:08,730 --> 00:03:10,990
And we're going to have opened this up again.

50
00:03:11,070 --> 00:03:15,900
It doesn't have to always be if you understood what the application does or if you even know what language

51
00:03:15,900 --> 00:03:20,760
you're using, you can start doing Python, you can do Ruby, you can do whatever language you think

52
00:03:20,760 --> 00:03:25,860
the back application is using and hoping that it's going to evaluate your code and actually execute

53
00:03:25,860 --> 00:03:26,650
it on the server.

54
00:03:27,060 --> 00:03:32,610
So as we look for our comment, we can see that instead of printing out whatever code we give, it is

55
00:03:32,610 --> 00:03:35,220
actually executing that info function.

56
00:03:35,550 --> 00:03:41,640
And it's giving us some information, as expected for the info function and it's telling us what version

57
00:03:41,640 --> 00:03:44,490
it's running and what the system is and so on.

58
00:03:44,520 --> 00:03:50,670
So this is something that's built in to be one of the most popular and safest ways to demonstrate that

59
00:03:51,000 --> 00:03:54,660
an application is taking your code and actually executing on the server.

60
00:03:54,750 --> 00:03:57,380
We're looking for info that does execute.

61
00:03:57,540 --> 00:03:59,880
Then we can prove that there is some code injection here.