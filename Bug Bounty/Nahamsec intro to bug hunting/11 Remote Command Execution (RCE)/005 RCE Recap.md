




---
# transcript :

1
00:00:00,120 --> 00:00:04,590
So that was RCE, RCE is such a broad vulnerability.

2
00:00:05,020 --> 00:00:07,340
You cannot just attach one way of finding it.

3
00:00:07,650 --> 00:00:10,540
What I just covered in this chapter is the most basic ways of finding.

4
00:00:10,740 --> 00:00:13,680
There's still very, very common to find in these ways.

5
00:00:13,890 --> 00:00:17,010
But you just have to spend the time FUZZ to every single parameter that you see.

6
00:00:17,400 --> 00:00:21,450
If you see a parameter sending some data, you think there is something happening in the back end where

7
00:00:21,720 --> 00:00:23,730
they are changing something with a command line.

8
00:00:23,920 --> 00:00:28,800
You want to make sure to find a way to inject your commander within which you can do a pipe ( | ), double  pipe ( | | ) and inline command and so on.