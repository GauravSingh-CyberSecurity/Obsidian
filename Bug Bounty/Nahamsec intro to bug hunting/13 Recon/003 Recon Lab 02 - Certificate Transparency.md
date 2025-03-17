


Now, let's talk about cert transparency. cert.sh(https://crt.sh/) , this is very, very cool.
it will Index every certificate that's out there, and all you have to do is type in the domain name.
We're going to start with gm.com for this case.
![[Screenshot From 2025-03-17 20-55-47.png]]

It's going to take a second, depending on how large your target is.
It's going to give you a list of matching identities, for gm.com, and so on.
![[Pasted image 20250317205852.png]]


You can also just type in a wildcard behind us.

Either one works.

We can also do a percent sign or percent 25, which is an encoded version of it.

It will bring back the same thing as well, and we get the good results.

You can also automate this using JSON.

You can output it, of course, as JSON if you want to automate on top of this.

You can also do some automation.

If you're good with Bash, Python, or whatever programming language you use, you can actually automate it and have it pull the domain name.

You can do the name value or the common name.

Right here, you can see it brings you all the domains for gm.com.

You can do this.

I can change this value for this domain, type in whatever it is, and it'll give you the same data.

Name value is one of them, and then there's common name as well.

I highly recommend doing both just to make sure you don't lose anything.

We'll probably look at these further in our labs, but I just want to make sure I cover it in this part of our recon module for this course.




---

# Transcript :

1
00:00:00,360 --> 00:00:04,560
Now, let's talk about transparency, transparency, that this is very, very cool.

2
00:00:04,920 --> 00:00:09,220
Index every certificate that's out there and all you have to do is type in the domain name.

3
00:00:09,240 --> 00:00:12,000
We're going to start with Gökhan for this case.

4
00:00:13,160 --> 00:00:16,500
It's going to take a second, depending on how large your target is.

5
00:00:16,830 --> 00:00:20,540
It's going to give you a list of matching identities, gay.com and so on.

6
00:00:20,550 --> 00:00:24,300
You can also just type in a wild card behind us.

7
00:00:24,330 --> 00:00:25,170
Either one works.

8
00:00:25,630 --> 00:00:29,880
We can also do a percent sign or present 25, which is an encoded version of it.

9
00:00:30,210 --> 00:00:32,330
Never bring back the same thing as well.

10
00:00:32,700 --> 00:00:33,810
And we get the good results.

11
00:00:34,050 --> 00:00:36,660
You can also automate this using Jason.

12
00:00:36,690 --> 00:00:38,370
You can do outputted course adjacency.

13
00:00:38,370 --> 00:00:39,780
You want to automate on top of this.

14
00:00:40,080 --> 00:00:41,550
You can also do some automation.

15
00:00:41,550 --> 00:00:46,530
If you're good with Barsh, Python or whatever programming language you use can actually automated and

16
00:00:46,530 --> 00:00:48,210
have it pull the domain name.

17
00:00:48,210 --> 00:00:51,330
You can do the name value or the common name right here.

18
00:00:51,330 --> 00:00:56,340
You can see it brings you all the domains for GM dot com.

19
00:00:56,610 --> 00:00:57,300
You can do this.

20
00:00:57,750 --> 00:01:02,670
I can change this value for this domain and type in whatever it is and it'll give you the same data.

21
00:01:03,540 --> 00:01:04,670
Name value is one of them.

22
00:01:04,950 --> 00:01:06,590
And then there's common name as well.

23
00:01:06,810 --> 00:01:09,930
I highly recommend doing both just to make sure you don't lose anything.

24
00:01:10,080 --> 00:01:16,020
Probably look at these further and our lives, but I just want to make sure I cover it and that part

25
00:01:16,020 --> 00:01:18,510
of our recon module for this course.