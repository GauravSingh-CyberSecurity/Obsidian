

---

# Transcript :

1
00:00:00,330 --> 00:00:05,520
So that was it for file uploads, follow ups have unlimited ways of looking for vulnerabilities.

2
00:00:05,550 --> 00:00:09,560
There isn't a single volume type that's attached to testing for follow uploads there.

3
00:00:09,570 --> 00:00:14,690
You can test for RCE, you can test for XXE, you can text for Path traversal.

4
00:00:14,700 --> 00:00:17,370
So you can test for a number of different things.

5
00:00:17,610 --> 00:00:20,010
But it all comes down to understanding what the uploader does.

6
00:00:20,010 --> 00:00:25,080
How does it store files, what extensions are allowed, what's not allowed, and just messing with it

7
00:00:25,080 --> 00:00:28,660
back and forth until you get the vulnerability that you're looking for.

8
00:00:28,830 --> 00:00:34,050
The top three things that I do when it comes down to looking for follow up bugs is putting payloads

9
00:00:34,050 --> 00:00:34,830
in the file name.

10
00:00:35,010 --> 00:00:40,250
That could be an RC payload, it could be an exercise payload and also changing the extension.

11
00:00:40,260 --> 00:00:45,630
So if I'm doing test on Panji to send out an image, I can make a test as HTML and seeing if it lets

12
00:00:45,630 --> 00:00:47,220
me upload an e-mail file.

13
00:00:47,250 --> 00:00:50,730
Another common way of doing this is putting another extension in the file.

14
00:00:50,730 --> 00:00:57,540
And then, for example, if it allows to do test PMG, if it's just allowing it to do images on the

15
00:00:57,540 --> 00:01:05,430
test on PMG and Shamal or the other way, you can do a test on question mark PMG, because in some cases

16
00:01:05,700 --> 00:01:10,680
they may be just matching that string to see if it exists in the file name and ignoring everything else.

17
00:01:10,980 --> 00:01:14,070
So again, there are a number of different ways to do follow up testing.

18
00:01:14,250 --> 00:01:18,840
But you want to look at those main three things when it comes onto uploading files into the servers

19
00:01:18,960 --> 00:01:20,190
and seeing how it works.