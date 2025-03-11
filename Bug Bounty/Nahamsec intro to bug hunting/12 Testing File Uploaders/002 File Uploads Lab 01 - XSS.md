Analysis of File uploads lab 1 :-  ( http://upload.naham.sec:8081/ )

Let's look at our example for the file upload. In this case, we're just going to use a file upload.  
We're going to take an image.  
We're going to test by uploading a PNG image.  
![[Screenshot From 2025-03-11 15-36-58.png]]
And it comes back and stores our file on the server.  
![[Screenshot From 2025-03-11 15-37-25.png]]

But I want to test for different vulnerabilities.  
So, for this case, I want to make it a little bit easier.  
File uploads can be a bit tricky.  

So we're going to use **==Burp Suite==** to capture the request that we're sending out.  
In this case, we're going to send out the same file(Linux-Commands_Cheat-Sheet.png) again.  
![[Screenshot From 2025-03-11 15-39-30.png]]
then send request to repeater for , further testing.


And for the filename of it, we're going to test out an existence payload.  
So I'm going to add an underline tag and some characters to it (filename="`test<u>hack.png`") and see how it reacts.  
![[Screenshot From 2025-03-11 16-18-33.png]]
As expected (testhack.png), this is very common in many cases if the file name doesn't actually sanitize the user's input.  
So, as expected, the string we provided after the underline tag ( <u> ) appears underlined in the output of this file.  


We're going to go back again and upload another file.  
That's the same file.  
And as we have uploaded, we are going to send a file that triggers an alert as soon as the user hovers over the image or the text.  
So, on mouseover, as soon as we hover over it with our mouse, it will trigger alert('1').  
In this case, it was alert('1').  
But we know, we've confirmed that there is a vulnerability in this case and we can actually exploit it.





---


# Transcript :

1
00:00:00,330 --> 00:00:06,350
Let's look at our example for the file upload in this case, we're just going to give it a follow upload.

2
00:00:06,690 --> 00:00:07,910
We're going to take an image.

3
00:00:07,920 --> 00:00:10,860
We're going to give a test, PMG going to upload it.

4
00:00:11,040 --> 00:00:14,340
And it comes back and it stores our file on the server.

5
00:00:14,950 --> 00:00:17,630
But I want to test out for different vulnerabilities.

6
00:00:17,640 --> 00:00:20,240
So for this case, I want to make it a little bit easier.

7
00:00:20,520 --> 00:00:22,280
File uploads could be a little bit tricky.

8
00:00:22,290 --> 00:00:26,470
So we're going to use Berp Suite to capture the request that we're sending out.

9
00:00:27,060 --> 00:00:29,610
So in this case, we're going to send out the same file again.

10
00:00:30,060 --> 00:00:33,480
And for the name of it, we're going to test out an existence payload.

11
00:00:33,490 --> 00:00:39,780
So I'm going to put a you underline tag and add some characters to it and see how it reacts.

12
00:00:40,080 --> 00:00:45,480
And as expected, this is very common in a lot of cases if the file name doesn't actually sanitize the

13
00:00:45,490 --> 00:00:46,260
user's input.

14
00:00:46,690 --> 00:00:52,890
So as expected, the the string that we gave it after the underlying tag is underlined within the output

15
00:00:52,890 --> 00:00:53,590
of this file.

16
00:00:53,610 --> 00:00:57,450
So we're going to go back again and we're going to upload another file.

17
00:00:57,460 --> 00:00:59,010
So that's the same file.

18
00:00:59,760 --> 00:01:08,370
And as as we had upload, we are going to post a file that says, hey, I want you to pop up an alert.

19
00:01:08,490 --> 00:01:14,210
As soon as the user goes over the image or the text or whatever we're giving it.

20
00:01:14,220 --> 00:01:19,150
So on mouseover, as soon as we go over it with our mouse and we'll give us an alert one.

21
00:01:19,500 --> 00:01:22,080
And in this case, it was alert one.

22
00:01:22,410 --> 00:01:29,080
But we know, hey, we've confirmed that there is an exercise in this case and we can actually exploit

23
00:01:29,100 --> 00:01:29,250
it.