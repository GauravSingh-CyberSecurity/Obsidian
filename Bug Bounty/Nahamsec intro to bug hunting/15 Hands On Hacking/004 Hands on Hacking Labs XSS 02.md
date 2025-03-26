







---

1
00:00:00,180 --> 00:00:04,860
One of my favorite things to do when it comes out here looking for bugs in the Bugs bounty program is

2
00:00:05,040 --> 00:00:06,770
observing there for fore pages.

3
00:00:06,780 --> 00:00:09,000
So we're going to give it a invalid path.

4
00:00:09,580 --> 00:00:10,410
Let's actually give a test123.
![[Screenshot From 2025-03-25 15-21-35.png]]
![[Screenshot From 2025-03-25 15-22-47.png]]
6
00:00:11,940 --> 00:00:16,600
And it looks like it says, hey, we could not find /test123 .

7
00:00:16,650 --> 00:00:20,070
This is what we're giving it right now in the address bar to /test123

8
00:00:20,430 --> 00:00:22,970
And we're going to chase it and see where it shows. in dev tools(elements) 
![[Screenshot From 2025-03-25 15-24-09.png]]
9
00:00:23,010 --> 00:00:25,380
So it looks like we're in the page not found.

10
00:00:25,380 --> 00:00:28,350
We're in a div class, blah, blah.
/test123

12
00:00:30,990 --> 00:00:33,540
This is the only place we could actually find this.

13
00:00:33,870 --> 00:00:35,220
But can we add more characters?

14
00:00:35,370 --> 00:00:38,670
So what happens if I add the sign ( < ) right here. /test123<

15
00:00:39,030 --> 00:00:45,500
in dev tools in elements tab , Right click and HTML and it looks like this one is actually getting encoded and that we can't exploit it
![[Screenshot From 2025-03-25 15-26-36.png]]


17
00:00:45,660 --> 00:00:50,190
So it's a good indication that this one is not invulnerable, but it's good to know that, hey, they reflect

18
00:00:50,190 --> 00:00:52,940
text within the fore page.

19
00:00:52,980 --> 00:00:54,030
There's also more other tricks.

20
00:00:54,030 --> 00:00:56,330
You can, you can try adding a random parameter.

21
00:00:56,340 --> 00:01:00,990
So I'm going to put in a   `/test123?nahamsecparam=test456`

23
00:01:02,490 --> 00:01:05,850
This time I'm going to let this go when I look test456
![[Screenshot From 2025-03-25 15-29-46.png]]
24
00:01:06,330 --> 00:01:11,790
So it looks like whatever we put in the address bar, if it's not found, it's reflected within the

25
00:01:12,060 --> 00:01:12,840
body of this.

26
00:01:12,840 --> 00:01:16,260
So let's add another script tag maybe or something.
`/test123?nahamsecparam=test456<h1>test123`

27
00:01:16,740 --> 00:01:18,630
We just want to see if it's going to render it or not.

28
00:01:19,210 --> 00:01:21,810
And it was like somehow we were able to break the logic.
![[Pasted image 20250326105427.png]]
29
00:01:21,810 --> 00:01:27,510
So it looks like there is some filtering happening, but because of how they are filtering it, it completely

30
00:01:27,510 --> 00:01:30,090
ignored anything that was assigned to this fake parameter.

31
00:01:30,270 --> 00:01:35,340
And they let us actually inject this additional tag in there.

32
00:01:35,340 --> 00:01:39,720
So the next step is to make it into a JavaScript payload or in its payload.

33
00:01:40,030 --> 00:01:40,680
And you can do that.

34
00:01:40,680 --> 00:01:42,090
A number of words can use image.

35
00:01:42,090 --> 00:01:44,460
Can you script whatever one you want to use?

36
00:01:44,460 --> 00:01:52,320
My favorite go to is just an image source X on error equals alert, and that should give us an XSS.
`/test123?nahamsecparam=test456<img src=x onerror=alert()> 
also this is the encoded version 

37
00:01:52,500 --> 00:01:56,400
If you're not familiar with JavaScript, why this payload works is what's happening here is we're saying,

38
00:01:56,400 --> 00:02:02,220
hey, using JavaScript, I want you to load a image called X if this file doesn't exist.

39
00:02:02,490 --> 00:02:05,810
And I want you to give me an alert because there's an error.

40
00:02:05,820 --> 00:02:10,800
So if there's an error, this follows an exists Pop-Up Alert, which is a function within JavaScript.

41
00:02:11,300 --> 00:02:15,750
We can also do other stuff like document, location, document, cookie and so on.

42
00:02:15,750 --> 00:02:16,860
We'll cover these later on.

43
00:02:16,980 --> 00:02:21,210
It also gave us our session, which doesn't matter in this case because I'm not logged in.

44
00:02:21,220 --> 00:02:28,230
I'm not exploiting another user, but it is very handy to show a real impact, especially if you can

45
00:02:28,230 --> 00:02:29,970
actually store cookies from other users.

46
00:02:30,480 --> 00:02:31,380
So that was a good one.

47
00:02:31,670 --> 00:02:33,090
We know there's two exercises here.

48
00:02:33,330 --> 00:02:34,370
We're on fire here.

49
00:02:34,650 --> 00:02:35,510
This is a good place.

50
00:02:35,520 --> 00:02:38,340
When you build momentum back monies, you want to keep pushing.

51
00:02:38,340 --> 00:02:42,870
If you see a vulnerability type occurring more than once or twice, you want to keep digging through

52
00:02:42,870 --> 00:02:43,830
and finding more of those.