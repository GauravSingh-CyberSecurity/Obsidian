==Stored XSS (Analysis of lab== ;-   http://xss3.naham.sec:8081/ )

to solve lab:- 
input "gaurav"  and enter

![[Screenshot From 2025-02-27 16-12-24.png]]

see the input is stored in header : (Welcome, gaurav)  , and not reflected in the body. 

![[Screenshot From 2025-02-27 16-13-05.png]]

![[Screenshot From 2025-02-27 16-14-11.png]]



now in dev tools "edit as html" 
![[Screenshot From 2025-02-27 16-15-39.png]]
and escape the " title tags " , and just create a simple alert payload :- 

![[Screenshot From 2025-02-27 16-24-14.png]]
i.e this the payload  (  </title>  <script>alert("gaurav")</script> ), lets try it out -


![[Screenshot From 2025-02-27 16-24-58.png]]
after inputting the payload and clikc enter,  it worked and the alert ->  gaurav .  was generated

![[Screenshot From 2025-02-27 16-26-12.png]]

==hence we are able to take the stored input in header field, manipulate the html code  and exploit the xss.==


---
1
00:00:00,270 --> 00:00:05,880
Now, let's look at our third example for says this case, the opposition is asking you for your name.

2
00:00:06,090 --> 00:00:10,770
I'm going to put in the homosexual and as we enter says things, we're entering your name.

3
00:00:10,980 --> 00:00:12,690
But it's not saying it anywhere here.

4
00:00:12,690 --> 00:00:14,460
We're not seeing our users data.

5
00:00:15,210 --> 00:00:16,800
eXistenZ relies on that output.

6
00:00:16,840 --> 00:00:18,380
So we're going to look at the view page source.

7
00:00:18,390 --> 00:00:23,400
You can either do view page view, page source or inspect who can do both.

8
00:00:23,700 --> 00:00:25,080
I'm going to choose this one for now.

9
00:00:25,440 --> 00:00:29,910
You can see that the user input that we give it, Nahum is going into the title of a page and you can

10
00:00:29,910 --> 00:00:31,110
send the top left corner.

11
00:00:31,290 --> 00:00:35,600
The title says Welcom Namesake, which is a user input that we've given it.

12
00:00:35,950 --> 00:00:36,860
So there's two things here.

13
00:00:36,870 --> 00:00:43,280
One, it's taking our user input as putting it somewhere on the page and to win the title tag and I've

14
00:00:43,290 --> 00:00:48,720
said this a few times in the past while covering Exercice context makes a huge difference, we want

15
00:00:48,720 --> 00:00:53,570
to understand where your data is going to and see if you have to close out the previous tags.

16
00:00:54,090 --> 00:00:55,230
Let's go back here again.

17
00:00:55,590 --> 00:00:56,800
And so homesick.

18
00:00:56,820 --> 00:01:02,790
We're going to give it a you talk again to you is for underline and we're going to close it out.

19
00:01:02,820 --> 00:01:06,720
We don't need to do their closing time, but we're just going to do it to be safe and have the same

20
00:01:07,090 --> 00:01:07,770
same thing.

21
00:01:07,770 --> 00:01:09,180
We're not in the house like anywhere.

22
00:01:09,180 --> 00:01:10,110
It's in the title.

23
00:01:10,290 --> 00:01:13,080
Are you tag is there we look at open source.

24
00:01:13,560 --> 00:01:14,310
It's still in there.

25
00:01:14,340 --> 00:01:18,450
However, again, because we're in the title tag, the HMO is now being shown.

26
00:01:18,450 --> 00:01:20,100
It's not rendering our payload.

27
00:01:20,430 --> 00:01:23,460
So we want to make sure that we close it up so we go back again.

28
00:01:23,760 --> 00:01:30,000
And this time since we know that it's not escaping any of the tags, it's not encoding it.

29
00:01:30,000 --> 00:01:31,170
It's not sanitizing it.

30
00:01:31,380 --> 00:01:32,670
It's not filtering it at all.

31
00:01:32,730 --> 00:01:33,420
It's sitting there.

32
00:01:33,420 --> 00:01:35,130
It's just not being evaluated.

33
00:01:35,250 --> 00:01:39,690
So I'm going to close the title tag by giving it a closing tag and then we're going to put our estimate

34
00:01:39,690 --> 00:01:45,480
at the end, which results and was getting a similar injection, which indicates that, OK, we probably

35
00:01:45,480 --> 00:01:50,700
escaped out of the place that we were and we're stuck in title and now we're able to inject it on to

36
00:01:50,700 --> 00:01:51,300
the page.

37
00:01:51,570 --> 00:01:55,800
And now we can go back and test for exercise.

38
00:01:57,030 --> 00:01:59,490
We can go back and test for exercise using JavaScript.

39
00:01:59,700 --> 00:02:03,990
What are we going to do here is going to type in script and we're just going to have to do an alert

40
00:02:04,410 --> 00:02:05,550
and alert one.

41
00:02:05,760 --> 00:02:06,720
We're going to close it out.

42
00:02:06,720 --> 00:02:09,270
What this does, again, it's a set of generic test payload.

43
00:02:09,480 --> 00:02:11,670
It's just a shockwave will never really exist.

44
00:02:11,880 --> 00:02:18,000
I was able to inject script into the Web page and it gave me an alert one, of course, sure enough,

45
00:02:18,000 --> 00:02:19,980
because we were able to get out of the title tag.

46
00:02:20,190 --> 00:02:21,450
There are no limitations there.

47
00:02:21,450 --> 00:02:23,850
Again, this application is not sanitizing anything.

48
00:02:23,850 --> 00:02:29,400
There's no filtering in place that helped us get across that scripting within this application.