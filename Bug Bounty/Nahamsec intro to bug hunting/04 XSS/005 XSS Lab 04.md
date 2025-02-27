==Stored XSS (Analysis of lab== ;-  http://xss4.naham.sec:8081/ )

look in dev tools , where you text ends up , after inputting it in the input field.
it could be in script tag, title tag(i.e head tag) , body etc.

in this our input  ends up in script  tag, 

we used ( '; )  to escape the script tag and then  ( // ) to comment rest of the query .
and in between the we included   an alert message  : ==alert(1)== 

```
non encoded format :
http://xss4.naham.sec:8081/?name=gaurav   ';   alert(2)  //comment

encoded format :
http://xss4.naham.sec:8081/?name=gaurav+++%27%3B+++alert%282%29++%2F%2Fcomment
```

i.e this is the payload    :-         `   ';   alert(2)  //   `  


![[Screenshot From 2025-02-27 16-54-47.png]]



---

1
00:00:00,630 --> 00:00:01,800
So let's take another example.

2
00:00:01,830 --> 00:00:06,180
This is going to be our last exercise example, the previous one, we were just in the title tag.

3
00:00:06,320 --> 00:00:07,920
Let's see where this one is going to end up.

4
00:00:08,340 --> 00:00:09,150
So we got to put in test.

5
00:00:09,150 --> 00:00:11,670
One, two, three says, hey, thanks for sharing your name test.

6
00:00:11,670 --> 00:00:12,390
One, two, three.

7
00:00:12,990 --> 00:00:14,420
We're going here now.

8
00:00:14,420 --> 00:00:16,110
We're in different areas.

9
00:00:16,110 --> 00:00:17,040
We're in the spin.

10
00:00:17,310 --> 00:00:22,200
I'd name one title and we're in a variable name within script.

11
00:00:22,740 --> 00:00:24,150
So let's go ahead and look at this.

12
00:00:24,200 --> 00:00:28,110
As far as you can see it this time, it's actually reflecting in the address bar.

13
00:00:28,110 --> 00:00:32,130
So we can see whenever we put into that box earlier, it's actually being shown here.

14
00:00:32,610 --> 00:00:36,240
If I go, you test two to two, it's going to come back.

15
00:00:36,240 --> 00:00:42,240
And as you can see, it's actually reflecting exactly the same code that I put in there, except it's

16
00:00:42,240 --> 00:00:43,650
not a rendering at this time.

17
00:00:43,650 --> 00:00:49,080
And showing us the XHTML rendered version, which is an underlined text, just go back and look.

18
00:00:49,530 --> 00:00:51,810
As you can see right here, it's HTML.

19
00:00:51,810 --> 00:00:54,930
It shows that the new tag is actually getting encoded.

20
00:00:54,930 --> 00:00:58,560
So that means that there properly are sanitizing the user input.

21
00:00:58,990 --> 00:01:04,890
Additionally, as I'm working there, the next one we're going to look at as within the span ID again,

22
00:01:04,890 --> 00:01:06,030
same thing right here.

23
00:01:06,270 --> 00:01:11,220
It's actually taking that you and encoding it, making sure it's safe before it's shown to the user.

24
00:01:11,460 --> 00:01:13,740
And this is now vulnerable more than likely.

25
00:01:14,670 --> 00:01:16,770
But there is, however, this one right here.

26
00:01:16,780 --> 00:01:21,240
So you can see here within a name variable, under a script tag.

27
00:01:21,480 --> 00:01:23,370
So we don't have the closing tags.

28
00:01:23,370 --> 00:01:27,410
We can't use any smaller than greater than signs for us to close the script tag.

29
00:01:27,420 --> 00:01:30,450
So if I were to go in here and put in a closing script tag.

30
00:01:32,720 --> 00:01:37,850
The application is going to look at this and realize that it's a code and they're going to actually

31
00:01:37,850 --> 00:01:45,370
sanitize it and spit out script tag, but again, it's sanitized and those tags are being converted

32
00:01:45,380 --> 00:01:48,310
properly and it's not allowing us to explain it.

33
00:01:48,980 --> 00:01:50,890
But again, it's always about the context.

34
00:01:50,900 --> 00:01:53,020
It always matters where we are with our code.

35
00:01:53,210 --> 00:01:59,750
As you can see in JavaScript, the name variable right here again, where variable name equals to whatever

36
00:01:59,750 --> 00:02:03,060
we put in here is being put between an apostrophe.

37
00:02:03,080 --> 00:02:06,890
So let's just go back and give it a regular text without any Estima code.

38
00:02:07,070 --> 00:02:13,630
So whatever we put in here, this isn't a name right here that's being put in between apostrophes.

39
00:02:14,300 --> 00:02:17,660
So if you know it's HTML and you understand JavaScript a little bit, you're going to understand that

40
00:02:17,660 --> 00:02:20,900
what we want to do is we want to close out the variable name.

41
00:02:21,110 --> 00:02:26,990
So we want to use the same exact methodology right here, the same exact logic of apostrophe semicolon

42
00:02:27,170 --> 00:02:32,240
and see if we can actually close the parameter name and the value assigned to it.

43
00:02:32,370 --> 00:02:34,460
So if I do name one, right click.

44
00:02:34,760 --> 00:02:36,290
As you can see, this actually work.

45
00:02:36,290 --> 00:02:41,510
It's not encoding an apostrophe and it's not encoding our semicolon.

46
00:02:41,810 --> 00:02:47,030
So what we can do right now is in the JavaScript, when you have a script and you want to comment things

47
00:02:47,030 --> 00:02:50,480
out like any other programming languages, it's as you does it.

48
00:02:50,600 --> 00:02:56,060
So what we want to do is wait to tell the application, hey, I want you to close it using my characters

49
00:02:56,060 --> 00:02:59,150
right here, and then I want to comment out the rest of this.

50
00:02:59,390 --> 00:03:06,440
So now everything we put in after the slide slashes should be treated as a comment, including the apostrophe

51
00:03:06,710 --> 00:03:11,480
and the semicolon between these two, because we want to make sure that JavaScript has no error.

52
00:03:11,480 --> 00:03:12,920
And this is why we're commenting these out.

53
00:03:13,280 --> 00:03:17,540
We're going to actually tell the application, hey, I want you to put in a space you can either do

54
00:03:17,540 --> 00:03:20,330
a space or a plus sign, either one works.

55
00:03:20,630 --> 00:03:22,530
And then I want you to use this other function.

56
00:03:22,550 --> 00:03:24,860
So, again, we're saying close a variable name.

57
00:03:24,860 --> 00:03:28,760
We reassign it closed with my apostrophe and my semicolon.

58
00:03:29,000 --> 00:03:30,290
And I want you to use the space.

59
00:03:30,720 --> 00:03:37,520
I want you to add the function alert with the value one, and then I want you to stop this function.

60
00:03:37,520 --> 00:03:41,770
It expects you to have a semicolon at the end and we're going to tell the application to handle this.

61
00:03:41,780 --> 00:03:47,300
Now, when we send this to it's going to, again, close that previous parameter, open up this new

62
00:03:47,300 --> 00:03:52,010
function and comment the rest of the things that were trailing after our code.

63
00:03:52,100 --> 00:03:55,550
And we have successfully been able to exploit this access.

64
00:03:56,150 --> 00:04:00,890
So, again, the piece of advice that I have for you is always, always, always look at where your

65
00:04:00,890 --> 00:04:01,720
text ends up.

66
00:04:01,790 --> 00:04:03,290
This could be in multiple places.

67
00:04:03,530 --> 00:04:04,370
It could be in a script.

68
00:04:04,370 --> 00:04:05,600
Had to give me the title tied.

69
00:04:05,960 --> 00:04:07,040
Each of these are different.

70
00:04:07,130 --> 00:04:11,180
You have to make sure you understand how to close these different parameters and different script tags

71
00:04:11,480 --> 00:04:12,680
or HTML talks.

72
00:04:12,920 --> 00:04:18,920
So never rely on copy pasting payloads because there was may not work in some context and in some cases

73
00:04:18,920 --> 00:04:23,990
it may actually get filtered by an application firewall or some sort of filtering system in place.

74
00:04:24,320 --> 00:04:30,050
So always start small, start with a text, go to an e-mail injection and then later on escalate that

75
00:04:30,050 --> 00:04:30,720
to access.

76
00:04:30,950 --> 00:04:36,170
And once you have done this enough time, you have actually your own methodology on how you look for

77
00:04:36,170 --> 00:04:37,520
the text assessment abilities.