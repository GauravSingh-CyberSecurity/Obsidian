

![[Screenshot From 2025-02-27 12-12-16.png]]
1
00:00:00,480 --> 00:00:05,550
That's going to cost rescripting crosshatch scripting is also known as access, and it comes in different

2
00:00:05,550 --> 00:00:06,110
flavors.

3
00:00:07,230 --> 00:00:09,570
But let's talk about what it is first before we jump into that.

4
00:00:09,990 --> 00:00:16,140
Exercise usually allows the attacker to execute any arbitrary client side code on a victim's browser.

5
00:00:16,740 --> 00:00:22,680
Exercise could be used in a number of ways, including phishing, exploding data, account takeovers

6
00:00:22,680 --> 00:00:23,110
and more.

7
00:00:23,730 --> 00:00:28,920
Think of exercise as a way where you can actually execute JavaScript onto a browser and control the

8
00:00:28,920 --> 00:00:31,330
behavior, especially within the website.

9
00:00:31,500 --> 00:00:37,500
So if a website like a bank is vulnerable to an exercise, we can start transferring money from one

10
00:00:37,500 --> 00:00:40,860
year to another, change their password and so on.


![[Screenshot From 2025-02-27 12-13-34.png]]
11
00:00:41,430 --> 00:00:42,270
So how does that work?

12
00:00:42,450 --> 00:00:48,540
Let's say an attacker has a vulnerability on their website within the user's first name in a common

13
00:00:48,540 --> 00:00:55,200
section, anywhere that they could insert any text to answer their payload, the user or the victim

14
00:00:55,200 --> 00:00:58,590
that we're going after, visits that page or clicks on the link.

15
00:00:58,950 --> 00:01:05,520
And as soon as they visit that page and executes on the browser and the payload is predefined to perform

16
00:01:05,520 --> 00:01:10,320
some malicious action, this action, again, could be transferring money from account to account.

17
00:01:10,320 --> 00:01:13,050
It could be changing their passport and so on.

18
00:01:14,010 --> 00:01:19,590
And a lot of cases, if our victim is an admin user or a user with special privileges, it could become

19
00:01:19,590 --> 00:01:20,550
even more dangerous.

20
00:01:20,730 --> 00:01:26,520
So, for example, as an admin, if you have access to file uploads and other functionality within the

21
00:01:26,520 --> 00:01:30,320
website and access against that user could be very, very beneficial.


![[Pasted image 20250227121530.png]]
22
00:01:30,600 --> 00:01:34,700
The impact for Accessors it actually depends on a lot of different factors.

23
00:01:34,710 --> 00:01:43,320
This could be if it requires any user privileges, if we're accessing or attacking any users with special

24
00:01:43,320 --> 00:01:47,510
access, depending on the data, the site stores and so on.

25
00:01:47,760 --> 00:01:53,460
But typically a reflective exercise could be anywhere from medium and in-store exercise could go up

26
00:01:53,460 --> 00:01:56,830
to a high or critical depending on the end results.



![[Screenshot From 2025-02-27 12-16-11.png]]
27
00:01:57,000 --> 00:01:59,150
So again, can have mentioned a different types of exercise.

28
00:01:59,490 --> 00:02:05,310
The two very, very common ones are reflected in store exercise and also there is damage assess, which

29
00:02:05,310 --> 00:02:06,530
we'll discuss a little bit.

30
00:02:07,230 --> 00:02:08,940
The first one being reflected exercise.

31
00:02:09,000 --> 00:02:12,810
The payload is usually injected from the victim's request.

32
00:02:13,080 --> 00:02:17,550
Usually you have to click on a link because it is in the address bar of the website.

33
00:02:17,550 --> 00:02:23,970
So it could be something like example dot com slash something equals to our payload versus historic

34
00:02:23,970 --> 00:02:26,550
success says it's actually stored server side.

35
00:02:26,550 --> 00:02:32,880
So any time a user visits a particular page, it pulls that payload from the web server, from the database

36
00:02:33,150 --> 00:02:34,380
and it shows it on the screen.

37
00:02:34,650 --> 00:02:39,900
Nomics says usually is some the client side code versus the server side.

38
00:02:40,230 --> 00:02:45,570
The injection typically so happens on the victims request, but it gets passed for different function

39
00:02:45,570 --> 00:02:48,090
or different JavaScript code for it to work.



![[Screenshot From 2025-02-27 12-17-42.png]]
40
00:02:48,420 --> 00:02:52,500
So let's look at reflected exercise, exercise, an example on the screen.

41
00:02:52,500 --> 00:02:57,900
You can see that we're going to site dot com, some random Web page and there's a parameter called name

42
00:02:58,140 --> 00:03:02,940
that takes your username, whatever you put in that search box or whatever you put on the website,

43
00:03:03,120 --> 00:03:05,760
it gets put into that address bar for name.

44
00:03:06,120 --> 00:03:08,450
And the response would be, Hello, John.

45
00:03:08,500 --> 00:03:10,740
So that message, John, could be anything.

46
00:03:11,040 --> 00:03:14,520
And whatever we put in there, it gets reflected back onto the page.

47
00:03:14,760 --> 00:03:15,890
And that's a normal request.

48
00:03:15,900 --> 00:03:20,100
That's what it's supposed to be, functioning us and it returns whatever we give it.

49
00:03:20,760 --> 00:03:23,070
Now, imagine if you put some token in there.

50
00:03:23,430 --> 00:03:30,120
If we put in, for example, the HMO code for UNDERLINE, which is the new tag, if the application

51
00:03:30,120 --> 00:03:35,010
is not vulnerable to Exercice, then it's going to come back and say hello, it's HTML tag, John,

52
00:03:35,010 --> 00:03:37,660
closing tag, which kind of shows that there is no access.

53
00:03:38,130 --> 00:03:43,560
However, if this was actually vulnerable when the application returns, the user input Rejon and the

54
00:03:43,560 --> 00:03:48,210
underlying tags around that, it would actually underline the text that we have given it.

55
00:03:49,110 --> 00:03:54,420
Just because we have HTML injection doesn't mean that we have exercice, but in a lot of cases there

56
00:03:54,420 --> 00:03:56,820
is a way to escalate to access to.

57
00:03:57,000 --> 00:04:01,020
The best way to actually look for exercise, in my opinion, is to actually look for places where you

58
00:04:01,020 --> 00:04:02,190
can insert HTML.

59
00:04:02,490 --> 00:04:07,440
And if the website comes back and renders this HTML code and there's a possibility to look for further

60
00:04:07,440 --> 00:04:08,670
access has vulnerabilities.



![[Screenshot From 2025-02-27 12-22-31.png]]
61
00:04:08,700 --> 00:04:13,590
Some of the examples that have been found previously on Facebook, for example, is, as you can see,

62
00:04:13,590 --> 00:04:15,810
the Q parameter in here on Facebook.

63
00:04:15,810 --> 00:04:21,120
Dot com translation has been swapped out from a text to a payload where it says, hey, I want to use

64
00:04:21,120 --> 00:04:24,000
a script tag and I want to pop up with an alert.

65
00:04:24,210 --> 00:04:27,060
And within that alert, I want to document cookies.

66
00:04:27,390 --> 00:04:32,130
And as you can see right here, it's returning the user's cookie and it's telling us that there's an

67
00:04:32,130 --> 00:04:32,730
exercise.

68
00:04:32,880 --> 00:04:38,340
If you're not familiar with script tags or JavaScript, I highly recommend looking up some resources.

69
00:04:38,550 --> 00:04:43,740
And I'm also going to make sure to attach it to this chapter of this course stories that says, on the


![[Screenshot From 2025-02-27 13-02-42.png]]
70
00:04:43,740 --> 00:04:46,410
other hand, is also known as persistent exercise.

71
00:04:46,530 --> 00:04:51,900
Again, this exercise payload usually gets stored somewhere in the database and then later on it would

72
00:04:51,900 --> 00:04:58,040
be shown to any user or particular users once that information is looked for it to, for example, leave

73
00:04:58,050 --> 00:04:59,790
a comment on our website.

74
00:05:00,120 --> 00:05:04,170
The website's going to be stored in the database, and any time someone loads that page where your comment

75
00:05:04,170 --> 00:05:06,360
was made, it would bring it up and show it.

76
00:05:06,690 --> 00:05:12,450
We can use it for access, especially if it allows us to inject HTML with JavaScript within it.

77
00:05:12,820 --> 00:05:19,850
As you can see, there was a very famous story that says recently that happened in 2014 on TweetDeck.

78
00:05:19,860 --> 00:05:24,660
So any user that would see this tweet, they would tweet this.

79
00:05:24,810 --> 00:05:28,470
So their followers would also get this, so the followers would be retweeted and so on.

80
00:05:28,470 --> 00:05:33,410
So everybody that would see this script tag or this exercise payload will be vulnerable to it.

81
00:05:33,720 --> 00:05:39,450
And again, this was stored on to Twitter and there wasn't any user interaction required on visiting

82
00:05:39,450 --> 00:05:40,640
this because of every tweet.

83
00:05:40,680 --> 00:05:43,320
Again, it would trigger it over and over and over again.

84
00:05:43,500 --> 00:05:45,390
There's also other examples of it right here.

85
00:05:45,400 --> 00:05:47,010
There is on Facebook.

86
00:05:47,010 --> 00:05:52,280
It's an integration from Dropbox where a file name was set to an its payload.

87
00:05:52,290 --> 00:05:57,620
And as soon as you go to Dropbox and you select your file, the exercise payload would pop up.

88
00:05:57,810 --> 00:06:00,080
We'll look for those in a little bit on their hands on that.

89
00:06:00,570 --> 00:06:05,730
But always think about anywhere that you can put any user input or any text that you can input to the

90
00:06:05,730 --> 00:06:10,860
website could be a potential for access as the last, but not least, there is access.

==Note: to better understand DOM XSS get familiar with javascript==
![[Screenshot From 2025-02-27 14-45-54.png]]
91
00:06:10,890 --> 00:06:16,090
This is typically when JavaScript reflects data from an attacker controlled resource, for example.

92
00:06:16,110 --> 00:06:21,020
This could be within the UI l and he passes on that data to a function later on.

93
00:06:21,480 --> 00:06:24,780
Consider the following piece of code isn't actually an example from a hacker.

94
00:06:24,780 --> 00:06:30,660
One report where it's looking for a location, as you can see right here, to load a particular page

95
00:06:30,660 --> 00:06:32,700
within that visit website.

96
00:06:32,940 --> 00:06:38,340
All we have to do is swap it out for some HTML code and JavaScript and then it would be able to pop

97
00:06:38,340 --> 00:06:39,930
an alert or whatever we're looking for.

98
00:06:40,320 --> 00:06:41,490
Consider this piece of code.

99
00:06:41,490 --> 00:06:43,420
As you can see, it's looking for some location.

100
00:06:43,590 --> 00:06:47,760
Again, if you're not familiar with what these are, I highly, highly recommend familiarizing yourself

101
00:06:47,760 --> 00:06:48,660
with JavaScript.

102
00:06:49,020 --> 00:06:55,280
But in this case, the page is going to rely on whatever comes off of this sign to load the next resource.

103
00:06:55,350 --> 00:07:01,240
This could be a contact form that it loads by clicking on a link within that same exact page.

104
00:07:01,530 --> 00:07:06,180
So if you understand how this works in JavaScript, you can replace that page with some of your own

105
00:07:06,330 --> 00:07:10,890
HTML call to a JavaScript with an edge and get an exercise to work again.

106
00:07:11,250 --> 00:07:16,470
Dumex says is one of those things where you want to learn about JavaScript before you start looking

107
00:07:16,470 --> 00:07:20,750
for it, because it relies on you understanding how the code works and where to look for it.


