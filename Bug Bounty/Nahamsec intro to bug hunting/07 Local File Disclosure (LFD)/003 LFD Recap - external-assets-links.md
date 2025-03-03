

**external-assets-links** :-
017 Null-Byte-Injection
http://projects.webappsec.org/w/page/13246949/Null%20Byte%20Injection








---
1
00:00:00,180 --> 00:00:05,730
So that's it for LFG again, these things for local father closure, the point of doing local fathers

2
00:00:05,730 --> 00:00:09,330
closure is to be able to fetch a file locally on that box.

3
00:00:09,360 --> 00:00:10,700
This could be a case.

4
00:00:10,710 --> 00:00:11,580
It could be secrets.

5
00:00:11,790 --> 00:00:14,550
It could be a password file.

6
00:00:14,790 --> 00:00:20,340
But the whole point is to be able to demonstrate that you actually have access to a local file on the

7
00:00:20,340 --> 00:00:25,170
server when it comes to looking for other to always be clear of what you're looking for.

8
00:00:25,200 --> 00:00:29,370
So in other words, what I mean by that is make sure you understand that this application is looking

9
00:00:29,370 --> 00:00:30,060
for a JPEG.

10
00:00:30,370 --> 00:00:35,270
So in some cases, it may actually have a hardcoded extension at the end or there may be some filtering.

11
00:00:35,280 --> 00:00:40,530
So if you see a parameter that says file and it's pointing to another extension file, like one that

12
00:00:40,530 --> 00:00:45,870
jpeg or image dot org, you see that in there, you are allowed just part inside of the parameter when

13
00:00:45,870 --> 00:00:51,240
it says something equal to the file name you want to look for and then left and see if you can actually

14
00:00:51,240 --> 00:00:51,770
read the file.

15
00:00:51,930 --> 00:00:57,060
And don't be afraid of using directory traversal to go out of the current directory, to go back a few

16
00:00:57,060 --> 00:01:02,880
directories to get those files or also put in question marks or no bytes in order to get rid of the

17
00:01:02,880 --> 00:01:08,610
extension that may be coded at the end of that particular call when it's calling out or fetching the

18
00:01:08,610 --> 00:01:09,780
file that you're looking for.

19
00:01:09,900 --> 00:01:14,490
So just because there's no extension and then a request, it doesn't mean that it's not being hard coded

20
00:01:14,490 --> 00:01:18,600
at the end of it when the server is sending it to the back end to fetch whatever file is supposed to

21
00:01:18,600 --> 00:01:18,930
fetch.

