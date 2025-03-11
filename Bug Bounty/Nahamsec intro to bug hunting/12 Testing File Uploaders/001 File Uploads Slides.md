
**==external-assets-links :==** 

042 Content-Type
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type

042 Common-MIME-types
https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types



---
types of upload vulnerablities
![[Screenshot From 2025-03-11 11-45-45.png]]





----

![[Screenshot From 2025-03-11 11-43-46.png]]
1
00:00:00,150 --> 00:00:05,180
Testing File Uploads, 

Unrestricted uploaded files are a significant risk to any application.
![[Screenshot From 2025-03-11 11-44-28.png]]

2
00:00:05,250 --> 00:00:11,760
A lot of bounty programs or regular web applications always allow users to submit some sort of a file.

3
00:00:11,880 --> 00:00:17,760
This could be either a social media platform or it could be legal documents or could even be HTML pages.

4
00:00:17,760 --> 00:00:20,190
That's used in some aspect of the website.

5
00:00:20,370 --> 00:00:24,270
When it comes to uploading files, that could be a number of different vulnerability attacks that could

6
00:00:24,270 --> 00:00:24,630
happen.


![[Screenshot From 2025-03-11 11-45-45.png]]
7
00:00:25,050 --> 00:00:29,610
We can either upload a remote web or we can get a remote command execution.

8
00:00:29,760 --> 00:00:34,890
We can use it for Croci scripting the other file name, or we can actually upload some sort of an example,

9
00:00:35,210 --> 00:00:38,570
e-mail or SPG file what it gives us access.

10
00:00:38,910 --> 00:00:45,510
We can have Posterous or go out of the current directory and override previous files can do XXE, which

11
00:00:45,510 --> 00:00:48,330
will explore this option in the later chapters.

12
00:00:48,600 --> 00:00:50,700
And also we can do a number of different things.

13
00:00:50,820 --> 00:00:55,980
This all depends on the application, but we're going to explore some of the most common ways of exploiting

14
00:00:56,130 --> 00:00:57,060
a file uploaded.




![[Screenshot From 2025-03-11 11-46-50.png]]
15
00:00:58,960 --> 00:01:01,900
So imagine you're sending your image to our website.

16
00:01:02,410 --> 00:01:07,400
The Web site's going to make the following request to account image upload.php.

17
00:01:07,840 --> 00:01:08,990
It's going to send out some data.

18
00:01:09,010 --> 00:01:11,830
It's going to be a large forum depending on how the applications run.

19
00:01:12,100 --> 00:01:14,740
It's going to look similar to this one, this case.

20
00:01:14,740 --> 00:01:16,830
As you can see, we have a max file size.

21
00:01:17,220 --> 00:01:18,510
We're not really going to mess with that.

22
00:01:18,910 --> 00:01:26,260
But the second portion that's really important is the file name, the content type and what goes inside

23
00:01:26,260 --> 00:01:26,470
of it.

24
00:01:26,500 --> 00:01:31,990
So in this case, because we are doing a test jpeg, we're just using it to upload a normal file, an

25
00:01:31,990 --> 00:01:32,410
image.

26
00:01:32,650 --> 00:01:38,230
It's going to have the content type image/jpeg and there's going to be some data in there that's going

27
00:01:38,230 --> 00:01:39,160
to represent our image.

28
00:01:40,270 --> 00:01:43,450
If you're not familiar with content types, I highly recommend looking into them.

29
00:01:43,600 --> 00:01:46,750
Make sure to add a link in the resources section of this chapter.

30
00:01:47,110 --> 00:01:51,070
We want to make sure that you're familiar with what different content types are out there and what they

31
00:01:51,070 --> 00:01:51,250
do.

32
00:01:51,280 --> 00:01:54,760
Now, let's say if you want to exploit this particular image, upload this case.

33
00:01:54,760 --> 00:01:56,730
As you can see, we are changing a few things.

34
00:01:56,740 --> 00:02:00,820
The first thing is we're just going to straight up change the extension name from JPEG.


![[Screenshot From 2025-03-11 11-49-15.png]]
35
00:02:01,960 --> 00:02:06,520
We're going to remove the content type and we're going to give some function within our upload.

36
00:02:06,670 --> 00:02:08,730
So in other words, we're just testing our luck.

37
00:02:08,920 --> 00:02:10,090
How is this application?

38
00:02:10,090 --> 00:02:10,360
Right.

39
00:02:10,600 --> 00:02:13,820
If it's not written with security in mind, then some things can go wrong.

40
00:02:14,320 --> 00:02:18,550
So the first thing is, if it accepts any different extensions, then we don't really have to worry

41
00:02:18,550 --> 00:02:19,630
about the content type.

42
00:02:19,670 --> 00:02:22,240
We can completely remove it and try out our luck.

43
00:02:22,550 --> 00:02:25,390
If that doesn't work, we can obviously readjust the content.

44
00:02:25,390 --> 00:02:31,930
Time to match our php file and hope that the application allowed us to upload our PHP file.

45
00:02:32,350 --> 00:02:34,930
And I imagine that we tried the previous step.


46
00:02:34,930 --> 00:02:39,580
We added that they didn't allow us because it expects JPEG in our file name.

47
00:02:40,120 --> 00:02:42,100
Again, we're we're playing a guessing game here.

48
00:02:42,110 --> 00:02:45,780
We don't know how the application works, but we're going to try our best to figure it out.


![[Screenshot From 2025-03-11 11-51-22.png]]
49
00:02:46,720 --> 00:02:50,170
And this case, what we can do is we can still add a .jpeg within the file name.

50
00:02:50,440 --> 00:02:54,040
But remember that when you upload a file, the last extension is what matters.

51
00:02:54,500 --> 00:02:59,110
So in other words, whatever other filename ends in is what's going to be taken by the application

52
00:02:59,110 --> 00:02:59,830
or the server.

53
00:03:00,100 --> 00:03:04,510
And it's going to get rendered in the backend, but we're still going to leave the content type as it

54
00:03:04,510 --> 00:03:04,890
is.

55
00:03:04,900 --> 00:03:09,820
Again, if this doesn't work, our objective is to go back and change the content time to whatever one

56
00:03:10,150 --> 00:03:11,330
that matches our extension.

57
00:03:11,800 --> 00:03:12,700
Is a great example.

58
00:03:12,700 --> 00:03:17,380
Just because an application expects a certain extension, it doesn't mean that it has to be that file.

59
00:03:17,380 --> 00:03:22,180
As long as an extension is present within the application, it's going to allow us to upload whatever

60
00:03:22,180 --> 00:03:23,200
file type we want.

61
00:03:23,590 --> 00:03:27,160
This is very common obstinance and multiple pentest and bug bounty programs.

62
00:03:27,400 --> 00:03:33,680
But I was able to upload an HTML or PHP file with just including the previous extension in the file name.





![[Screenshot From 2025-03-11 11-54-38.png]]
63
00:03:34,480 --> 00:03:36,940
You also have the option to change the file name.

64
00:03:36,970 --> 00:03:38,260
This could be for XSS.

65
00:03:38,260 --> 00:03:43,630
We can abuse some of the RCE stuff that we talked about in the previous chapters to either get an exorcist

66
00:03:43,630 --> 00:03:49,240
because of the file name or you can actually try and get an RCE depending on how the application Parses

67
00:03:49,480 --> 00:03:51,000
the file names and renders.

68
00:03:51,610 --> 00:03:55,750
So in other words, you can replace it with different payloads, assuming that the application is going

69
00:03:55,750 --> 00:04:01,270
to take a literal and run it either for XSS or RCE or whatever that is when testing a file upload

70
00:04:01,270 --> 00:04:03,490
or don't limit yourself to just the content of the file.

71
00:04:03,520 --> 00:04:06,800
Always think about headers ,filename and other stuff as well.



![[Screenshot From 2025-03-11 11-58-37.png]]
72
00:04:06,880 --> 00:04:11,560
And of course, the most popular thing to do with a file upload or most people look for this as an XSS,

73
00:04:11,560 --> 00:04:13,240
you can just try and change the content.

74
00:04:13,240 --> 00:04:18,940
Time to HTML text, upload an HTML file and see if we can get XSS, .

75
00:04:19,150 --> 00:04:24,100
A lot of places allow this, but before reporting on XSS, make sure that this is not intended.

76
00:04:24,490 --> 00:04:28,900
In other words, make sure that they're not just allowing you to upload HTML and you have bypassed some

77
00:04:28,900 --> 00:04:30,190
sort of a restriction against it.


![[Screenshot From 2025-03-11 11-59-34.png]]
78
00:04:30,850 --> 00:04:35,530
And last but not least, if none of that works, you can always try doing your past traversal from the

79
00:04:35,530 --> 00:04:36,310
previous chapters.

80
00:04:36,310 --> 00:04:41,940
We talked about this where you can traverse all your current directory and read or overwrite other files.

81
00:04:41,960 --> 00:04:46,570
So in other words, we're saying, hey, instead of uploading this into the directory where it's designated

82
00:04:46,570 --> 00:04:49,600
for the users file uploads, I want you to escape out of it.

83
00:04:49,600 --> 00:04:55,810
Go all the way to the root folder of the Web server and replace the content of the authorized Keys file

84
00:04:55,990 --> 00:04:57,520
within the folder.

85
00:04:57,940 --> 00:05:02,890
And you can do this usually if there is a Path traversal over so it doesn't have to be in the Webroot folder.

86
00:05:02,920 --> 00:05:10,030
It could also be overwriting settings, overwriting files or uploading files over others depending on

87
00:05:10,030 --> 00:05:10,900
what you're going after.

88
00:05:10,930 --> 00:05:11,740
So keep that in mind.

89
00:05:11,740 --> 00:05:14,010
Path reversal in some cases also doable.