
Docker setup guide on kali linux: https://www.kali.org/docs/containers/installing-docker-on-kali/
# Setup Guide for Nahamsec’s Intro To Bug Bounty Labs    https://medium.com/@hackitdamn/setup-guide-for-nahamsecs-intro-to-bug-bounty-labs-f398ab26dae9






Transcript of video: 
1
00:00:00,150 --> 00:00:02,490
Hello and welcome to introduce bug hunting.

2
00:00:02,610 --> 00:00:07,470
My name has been said before, but most people know me online as the harm said, and I'll be your instructor

3
00:00:07,470 --> 00:00:08,340
throughout this course.

4
00:00:08,670 --> 00:00:12,930
Before we jump into the contents of this cause, I want to quickly get the background on who I am and

5
00:00:12,930 --> 00:00:14,040
how this course looks.

6
00:00:14,070 --> 00:00:19,800
I currently work as the head of hacker education and hacker one by day and at night I a content on hacking

7
00:00:19,800 --> 00:00:21,720
and dabbling bug bounties on my free time.

8
00:00:21,750 --> 00:00:26,280
You may have seen some of my content on Twitch, but I do love recon and bring guests and some of the

9
00:00:26,280 --> 00:00:31,380
top hackers in the industry to ask him how they approached the targets and how they get better on hacking.

10
00:00:31,600 --> 00:00:35,880
We have also seen me on YouTube with some of my research and other videos I've posted.

11
00:00:36,290 --> 00:00:41,520
I've also seen me at conferences like Def Con Bseiso and OPSEC, where I presented my research on when

12
00:00:41,520 --> 00:00:45,600
I hacked into companies like Apple, Lyft, Snapchat and Airbnb.

==13==
==00:00:45,840 --> 00:00:46,740==
==Let's talk about this course.==

==14==
==00:00:46,920 --> 00:00:49,010==
==Each chapter is going to have three different things.==

==15==
==00:00:49,050 --> 00:00:53,370==
==The first thing is we're going to talk about what the vulnerabilities are, how to look for him, and==

==16==
==00:00:53,370 --> 00:00:58,020==
==then we're going to do a live demo of how to actually exploit and find these vulnerabilities in different==

==17==
==00:00:58,020 --> 00:00:58,700==
==applications.==

==18==
==00:00:58,830 --> 00:01:00,690==
==Later, we'll have a hands on that.==

==19==
==00:01:00,760 --> 00:01:04,290==
==We have created an entire infrastructure to show you how to push a target.==

==20==
==00:01:04,410 --> 00:01:08,910==
==How do I do recon and how do I look for each vulnerability type in a specific application?==

21
00:01:09,240 --> 00:01:09,570
All right.

22
00:01:09,750 --> 00:01:10,800
Let's now jump into it.