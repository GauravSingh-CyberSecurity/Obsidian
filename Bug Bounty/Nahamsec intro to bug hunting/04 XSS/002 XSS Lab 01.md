Reflected XSS (Analysis of lab:-  http://xss.naham.sec:8081/)

using this in input  field , check if they execute or not:
<script>alert(document.cookie)</script> test123
<script>alert(1)</script>
<U>test</U>

---

1
00:00:00,300 --> 00:00:02,200
Now, let's look at some examples of exercise.

2
00:00:02,580 --> 00:00:08,970
One of the things that I like to do usually is have my Google Chrome developer tools up right here so

3
00:00:08,970 --> 00:00:13,800
I can monitor whatever I put into this box or anything that I can actually input a text into.

4
00:00:14,830 --> 00:00:17,940
So, for example, we're going to type in test one, two, three.

5
00:00:18,930 --> 00:00:21,420
The it's going to come back and say hello, test one, two, three.

6
00:00:21,780 --> 00:00:25,800
There's nothing up here in the address bar, but we're going to look up and to test one, two, three

7
00:00:25,800 --> 00:00:26,340
right here.

8
00:00:26,770 --> 00:00:31,110
As you can see, this is where the text is and that's the only time that it comes up.

9
00:00:31,470 --> 00:00:32,970
Now, let's go back refresh.

10
00:00:34,950 --> 00:00:37,200
Now we're going to try and put some estimate on it.

11
00:00:37,210 --> 00:00:43,060
So we're going to put a sample, you underline it just to see if it works or not.

12
00:00:45,150 --> 00:00:46,200
We can see the test.

13
00:00:46,200 --> 00:00:47,550
One, two, three is underlined.

14
00:00:47,910 --> 00:00:49,280
I want to look for it right here.

15
00:00:49,800 --> 00:00:52,170
I always like to click here and do anything else.

16
00:00:52,170 --> 00:00:52,770
I can see it.

17
00:00:55,320 --> 00:00:59,130
As you can see, it shows, OK, the military that we put on there is getting rendered.

18
00:00:59,560 --> 00:01:01,080
Now, I want to look for exercise.

19
00:01:01,830 --> 00:01:06,180
One of the most common exercises Payloaders suggests is a script tag, which is very well known for

20
00:01:06,180 --> 00:01:09,530
JavaScript and doing an alert document cookie.

21
00:01:09,690 --> 00:01:11,630
You can also do document location.

22
00:01:11,940 --> 00:01:15,720
Again, if you're not familiar with these, I'll leave a link attached to these resources.

23
00:01:16,020 --> 00:01:18,270
Are you able to review them and understand them a little bit better?

24
00:01:18,660 --> 00:01:22,590
But we're going to put this in here and also put test one, two or three just to see how it works.

25
00:01:23,460 --> 00:01:28,500
So right here we have an exercise payload to just JavaScript that's going to use an alert function.

26
00:01:28,800 --> 00:01:33,900
And that alert function is going to give us a document cookie with the text test.

27
00:01:33,900 --> 00:01:34,530
One, two, three.

28
00:01:34,770 --> 00:01:35,730
We're going to push enter.

29
00:01:36,090 --> 00:01:39,750
As soon as we do this, it's going to give us a blank alert because I have no cookies left in there.

30
00:01:40,680 --> 00:01:41,520
I'm not authenticated.

31
00:01:41,520 --> 00:01:45,540
There are no cookies attached to my user right now, but it shows that the alert function worked.

32
00:01:45,690 --> 00:01:47,610
And again, you can replace it with anything.

33
00:01:47,610 --> 00:01:50,790
You can put an actual text in here, you can put numbers.

34
00:01:50,960 --> 00:01:52,890
A lot of people just like to do alert one.

35
00:01:53,160 --> 00:01:54,150
So we're going to do this.

36
00:01:54,450 --> 00:01:59,670
If this successfully works, it's going to use the alert function within JavaScript and give us a one

37
00:01:59,670 --> 00:02:00,120
within it.

38
00:02:01,310 --> 00:02:03,000
And again, as you can see, this one worked.

39
00:02:03,420 --> 00:02:09,930
And as we can look for it right here, that shows hello, script tag, alert one script test, one,

40
00:02:09,930 --> 00:02:10,440
two, three.

41
00:02:11,100 --> 00:02:12,090
These are still common.

42
00:02:12,090 --> 00:02:17,280
They may not be as common as some of the private programs or some of the more commonly look programs.

43
00:02:17,400 --> 00:02:20,220
But again, it's a very, very common way to look for exercise.

44
00:02:20,520 --> 00:02:26,430
And this works because we actually are injecting an exercise payload within the page and it's rendering

45
00:02:26,430 --> 00:02:27,090
it as it is.

46
00:02:27,570 --> 00:02:29,100
But it's not usually this easy.

47
00:02:29,100 --> 00:02:30,750
And we'll talk about those in a little bit.