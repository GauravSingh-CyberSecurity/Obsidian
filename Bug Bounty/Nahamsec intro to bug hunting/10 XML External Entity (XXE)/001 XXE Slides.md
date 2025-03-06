





---

![[Screenshot From 2025-03-06 16-50-45.png]]
1
00:00:00,150 --> 00:00:07,020
Ximo external entity, also known as Xixi and Xixi, happens where the application just relies on X
![[Screenshot From 2025-03-06 16-51-17.png]]

2
00:00:07,020 --> 00:00:12,570
amount, Xixi, like any other languages, comes with a variety of different functions and entities

3
00:00:12,810 --> 00:00:15,510
that could be used to exploit a Web server.

4
00:00:15,540 --> 00:00:22,680
So again, if the application is not creating any defense mechanism against Xixi by default, it may

5
00:00:22,680 --> 00:00:23,940
be vulnerable to Xixi.

6
00:00:24,290 --> 00:00:31,020
Xixi could be very obvious to look for because a lot of times you would actually seed XML format like

7
00:00:31,020 --> 00:00:31,260
the one.

8
00:00:31,260 --> 00:00:35,400
For example, coming up right now, you're going to see some request being sent to the server that looks
![[Screenshot From 2025-03-06 16-52-27.png]]
9
00:00:35,400 --> 00:00:40,950
and screams XML whether the content type is set to XML or you actually see the data that's being sent

10
00:00:40,950 --> 00:00:41,970
to the server is redundant.

11
00:00:41,970 --> 00:00:47,760
XML and ExactTarget typically happens against an application that passes XML input, whether it's through

12
00:00:47,760 --> 00:00:49,590
an API or a file upload.

13
00:00:49,770 --> 00:00:55,350
In some way, the application is accepting XML, parsing it and then putting it to the server and representing

14
00:00:55,350 --> 00:00:56,470
data back to the user.

15
00:00:57,000 --> 00:01:02,490
These types of attacks usually lead to disclosure of confidential data, denial-of-service server site

16
00:01:02,490 --> 00:01:05,550
request forgery, port scanning and so on.

17
00:01:05,910 --> 00:01:09,950
The disclosure of confidential data isn't just limited to data that's on the website.

18
00:01:09,960 --> 00:01:11,760
It could also be access to local.

19
00:01:12,590 --> 00:01:15,990
It could be also access to local files on the system.

20
00:01:15,990 --> 00:01:21,180
Host If you're not familiar with XML, I highly recommend looking into the basics of XML, looking at

21
00:01:21,180 --> 00:01:23,910
over and understanding how XML is structured.

22
00:01:24,120 --> 00:01:25,610
So a lot of these make more sense.



![[Screenshot From 2025-03-06 16-52-27 1.png]]
23
00:01:25,630 --> 00:01:26,970
Consider the following request.

24
00:01:27,120 --> 00:01:33,240
We are importing some sort of a file to the import system for our target site and it accepts XML.

25
00:01:34,210 --> 00:01:39,150
So in the request that we're sending to the server, they've given us some sort of XML template we downloaded.

26
00:01:39,300 --> 00:01:41,580
This application accepts a list of usernames.

27
00:01:41,760 --> 00:01:43,950
So in this case we're sending the user names handshake.

28
00:01:44,130 --> 00:01:47,290
The application takes that and responds with no take back.

29
00:01:47,310 --> 00:01:51,630
So that means that past it took the value it was looking for and return it back to us.

30
00:01:52,580 --> 00:01:58,260
But now what we can do in this case is we can use a system identifier, which is very common in XML.

31
00:01:58,500 --> 00:02:05,550
We can assign a new entity called Xixi and using system since it actually expects a file wrapper or

32
00:02:05,820 --> 00:02:07,560
a U or I could actually tell it.

33
00:02:07,560 --> 00:02:13,020
Hey, I want you to do a file wrapper, look for the Etsy folder within the root folder and give me

34
00:02:13,020 --> 00:02:15,300
the password file within that folder.

35
00:02:15,660 --> 00:02:22,710
And using the full amount, we are going to call our entity Xixi, which has the value set to the file

36
00:02:22,710 --> 00:02:23,530
that we're searching for.

37
00:02:24,000 --> 00:02:29,610
So again, what we're doing here is we're telling it, hey, use system, assign the value of that file

38
00:02:29,610 --> 00:02:30,480
to see.

39
00:02:30,750 --> 00:02:36,600
We're going to call that Xixi entity within our element Downbelow on their food.

40
00:02:37,380 --> 00:02:41,910
And once the application parses this and comes back and instead of giving us the list of user name,

41
00:02:42,210 --> 00:02:45,050
it gives us back the content of that file.

42
00:02:45,360 --> 00:02:47,790
So if we were explaining its application, we could give it FUX.

43
00:02:47,790 --> 00:02:51,660
It may come back and say, hey, I don't know what Foo means, I'm expecting username.

44
00:02:51,870 --> 00:02:57,930
We go back, we change Foo to username Miklosi username, but we put an element in there and it comes

45
00:02:57,930 --> 00:03:00,680
back and gives us the contents of that file.

46
00:03:02,130 --> 00:03:05,610
We can also do this, as mentioned earlier, to leverage SRF.

47
00:03:05,730 --> 00:03:11,280
We can access local network and IP addresses that are hosting some sort of another application within

48
00:03:11,280 --> 00:03:12,220
it's part of the network.

49
00:03:12,540 --> 00:03:19,580
So in this case we are going to look for the metadata provided by the cloud service providers.

50
00:03:19,590 --> 00:03:25,470
After using AWB, for example, we can query for the IP address one six nine to five four one six nine

51
00:03:25,470 --> 00:03:29,730
to five for using system by assigning it to our Xixi entity.

52
00:03:29,940 --> 00:03:35,040
And again, Downbelow within Fux we're calling it and we having get past that data and send it back

53
00:03:35,040 --> 00:03:35,420
to us.

54
00:03:35,790 --> 00:03:40,340
There might be times where we may have a blind xixi where we don't see the response.

55
00:03:40,350 --> 00:03:46,080
So for example, if I may tell my X amount of payload to fetch the ETSI password file, but the application

56
00:03:46,220 --> 00:03:51,090
back may come back and say, OK, it's not, it's done.

57
00:03:51,180 --> 00:03:55,200
They may not give us the actual data, it may just give us a generic message that says, hey, this

58
00:03:55,200 --> 00:03:58,620
task was completed status, OK, status one, whatever that is.

59
00:03:58,830 --> 00:04:01,560
So in other words, it's not going to give us the value of the file.

60
00:04:01,560 --> 00:04:06,750
We want to it's just going to give us a generic message where we can't really see anything behind it.

61
00:04:07,050 --> 00:04:12,180
So in other words, while the XXXI vulnerability is present because of the way that the application

62
00:04:12,180 --> 00:04:14,970
is built, we can see the result of our payload.

63
00:04:15,160 --> 00:04:20,670
So we want to make sure we can send it back to our own server or someone we trust to retrieve the data

64
00:04:20,670 --> 00:04:21,510
that we're looking for.

65
00:04:21,540 --> 00:04:27,120
So in this case, instead of searching for the local file or the local website where we're going after,

66
00:04:27,240 --> 00:04:31,440
we're going to call for even the DTD, which is hosted on our server.

67
00:04:31,440 --> 00:04:32,730
We can use burb collaborator.

68
00:04:32,730 --> 00:04:38,580
We could use a Web server like Apache, but we file on our server somewhere and we tell it, hey, I

69
00:04:38,580 --> 00:04:44,490
want you to reach us file and within eval that DDT or we're going to do is we're going to define our

70
00:04:44,490 --> 00:04:45,000
exploit.

71
00:04:45,330 --> 00:04:51,030
So evil that DDT, where it's posted on our Web server, we're going to assign the value of the file

72
00:04:51,030 --> 00:04:55,980
etsi password to our exact CPAC entity and within XML data.

73
00:04:55,980 --> 00:04:59,040
What we're going to do is we're going to call an Excel using system.

74
00:04:59,580 --> 00:05:04,550
The system, we're going to call our website back and say, hey, I'm going to send you some data and

75
00:05:04,550 --> 00:05:06,540
it's going to log it through our server.

76
00:05:06,590 --> 00:05:12,260
So what we're doing here is we're pretty much sending the content of this essive password file to our

77
00:05:12,260 --> 00:05:15,010
Web server because there's no other ways of seeing it.

78
00:05:15,020 --> 00:05:16,630
And I'll show this in the labs later on.

79
00:05:16,940 --> 00:05:22,610
But the whole goal is read the file that we want, assign it to an entity and send the content of the

80
00:05:22,610 --> 00:05:25,280
entity to the remote server for an exfil.

81
00:05:25,520 --> 00:05:29,960
Just go on and search to our labs and see what this actually looks like in a real application.