Reflected XSS (Analysis of lab:-  http://xss2.naham.sec:8081/)



---
1
00:00:00,300 --> 00:00:01,330
Let's take another example.

2
00:00:01,530 --> 00:00:05,460
So an exercise to that same thing that says, hey, what's your name?

3
00:00:05,490 --> 00:00:06,960
We're going to protest one, two, three.

4
00:00:08,280 --> 00:00:10,500
And as we can see, we're in some sort of text box.

5
00:00:10,870 --> 00:00:13,880
They're putting us in some definite [REMOVED] code.

6
00:00:14,250 --> 00:00:17,770
One of the things that's really important with exercise is to understand the context.

7
00:00:17,880 --> 00:00:22,070
It's really, really important to understand where is our text being reflected?

8
00:00:22,080 --> 00:00:24,500
What is it going the HMO down when you look it up?

9
00:00:24,670 --> 00:00:26,040
If we look up, test one, two, three.

10
00:00:26,910 --> 00:00:30,550
The only place that it comes in, it's in an input value tag.

11
00:00:30,930 --> 00:00:38,430
So if we were to put another script alert like this and test one, two, three, but put that in there,

12
00:00:38,490 --> 00:00:39,180
let's go back.

13
00:00:40,050 --> 00:00:45,560
So if we were to put just a script alert, function one, test one, two, three, and pass it in here,

14
00:00:46,350 --> 00:00:50,720
this comes back, as you can see right here, it's not getting filtered at all.

15
00:00:50,820 --> 00:00:52,400
That's exactly how I would put it in there.

16
00:00:52,770 --> 00:00:53,770
None of that has changed.

17
00:00:54,000 --> 00:00:57,810
However, it's not working, and that's because we're within an input tag.

18
00:00:58,290 --> 00:01:02,700
If you were in a context of a different e-mail where there may have some limitations, you want to be

19
00:01:02,700 --> 00:01:04,020
able to escape out of it.

20
00:01:04,380 --> 00:01:07,680
So if you're not familiar with attachment, I highly recommend getting familiar with it.

21
00:01:07,920 --> 00:01:13,750
But as you can see, each tag starts with a regular tag and a closing time like this one.

22
00:01:13,770 --> 00:01:14,660
So it's sensitive.

23
00:01:14,970 --> 00:01:18,960
And this one has a Sachdev, meaning that's going to close it and every single one of them have the

24
00:01:18,960 --> 00:01:19,710
closing time.

25
00:01:20,400 --> 00:01:24,930
So if you think about the fact that whatever we have put in here, it's coming between two quotation

26
00:01:24,930 --> 00:01:28,780
marks and it's getting assigned to the parameter value within the input time.

27
00:01:29,190 --> 00:01:34,220
So we want to do is we want to escape out of this input tag by closing this.

28
00:01:34,230 --> 00:01:35,700
So let's just give it a regular text.

29
00:01:36,770 --> 00:01:41,910
We want to close this out if we want to make sure our similar code finishes this up and says, hey,

30
00:01:42,120 --> 00:01:46,500
I want you to end this and replace it with our code.

31
00:01:46,530 --> 00:01:47,660
So let's try this one more time.

32
00:01:47,670 --> 00:01:48,390
We're going to go back.

33
00:01:48,390 --> 00:01:53,610
I think once I show it, it will make more sense, whereas I test one, two, three, as you can see.

34
00:01:53,620 --> 00:01:57,870
So when we put in test one, two, three comes back, it's putting it into the value parameter right

35
00:01:57,870 --> 00:01:58,190
here.

36
00:01:58,230 --> 00:02:02,290
It's assigning it there between this quotation marks and a greater side.

37
00:02:02,550 --> 00:02:07,710
So we want to do as we want to mimic this exact behavior and say, hey, I want you to close this tag

38
00:02:07,710 --> 00:02:08,270
right here.

39
00:02:08,400 --> 00:02:13,090
Whatever is in this parameter, I want you to close it and start a new original code.

40
00:02:13,380 --> 00:02:14,400
So we're going to go in here.

41
00:02:14,920 --> 00:02:19,830
We're going to go back to our main site and we're going to just simply say, since I know I'm within

42
00:02:19,830 --> 00:02:25,740
these two quotation marks and this is how it ends, I'm going to move the ending characters to the beginning.

43
00:02:26,220 --> 00:02:30,990
That means he tests one and I'm going to say test two.

44
00:02:31,320 --> 00:02:36,840
I want you to put test one in there and then I want you to close it and I want to see how this reacts.

45
00:02:37,020 --> 00:02:42,000
So when we put in here, as you can see, we've escaped out of this box and test two is being shown

46
00:02:42,000 --> 00:02:42,360
here.

47
00:02:42,600 --> 00:02:46,790
And the closing characters that were in there already as being shown afterwards.

48
00:02:47,070 --> 00:02:50,310
So in the code, if we look at says hello, I put test one.

49
00:02:50,580 --> 00:02:54,870
I said, hey, I want you to put a quotation mark on the closing time and then I could test you.

50
00:02:55,110 --> 00:02:57,040
And there's the last two letters right there.

51
00:02:57,060 --> 00:03:00,920
The last two characters are the things that were already predefined in the code.

52
00:03:00,930 --> 00:03:02,290
So it's leaking those as well.

53
00:03:02,790 --> 00:03:09,900
Now, if we go back again, so right here, we're going to say test one, closed that value parameter.

54
00:03:10,350 --> 00:03:15,830
And then I want you to open up a new script tag, alert script and enter that.

55
00:03:16,020 --> 00:03:23,670
As we do this, it's going to work because we told the application to close out the input tag with a

56
00:03:23,670 --> 00:03:28,170
test, one quotation quotidien, and then insert our Schimel code in there.

57
00:03:28,470 --> 00:03:32,940
And then the rest of it is going to get leaked because it's unused code that the application doesn't

58
00:03:32,940 --> 00:03:33,750
know what to do with.