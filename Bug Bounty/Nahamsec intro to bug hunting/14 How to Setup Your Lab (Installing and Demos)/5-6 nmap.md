
## 5

1
00:00:00,150 --> 00:00:04,470
So next thing I want to install and nmap , in order for any nmap to work, you want to make sure that your

2
00:00:04,710 --> 00:00:05,970
apt is updated.

3
00:00:06,000 --> 00:00:10,270
```
So are we going to do is type in sudo apt update and get an update?
```

4
00:00:10,320 --> 00:00:13,590
This should be the first thing you do when you create a new server.

5
00:00:13,860 --> 00:00:16,140
We're going to give it a few seconds, is going to be done soon.

6
00:00:16,350 --> 00:00:21,030
And once that is done, we can use apt to install our own nmap.

7
00:00:21,050 --> 00:00:22,140
Now it says it's done.

8
00:00:22,150 --> 00:00:23,130
We can do upgrade.

9
00:00:23,280 --> 00:00:24,270
I'm going to skip it.

10
00:00:24,270 --> 00:00:29,160
And we just typing `sudo apt install  map.`


---
## 6

1
00:00:00,760 --> 00:00:06,580
The next thing we're going to look at is how to use and nmap and map is very, very helpful when it comes

2
00:00:06,580 --> 00:00:12,400
down to scanning IT infrastructure or a particular domain or list of domains or subdomains to look for

3
00:00:12,400 --> 00:00:13,200
open ports.

4
00:00:13,240 --> 00:00:19,120
Most applications are posted on board 80 or 443, but there are a lot of cases you may find other secondary

5
00:00:19,120 --> 00:00:26,140
applications, backends or API being hosted on a different port like 8080, 8000, 10000,
fand so on.

7
00:00:27,520 --> 00:00:32,710
You can also see if there is other services running on that host and if those services are vulnerable

8
00:00:32,710 --> 00:00:38,360
to a particular CV by doing a port scan can do this in a number of different ways.

9
00:00:38,410 --> 00:00:42,970
The most basic way of doing it is just typing in nmap and whatever you want to scan for.

10
00:00:43,000 --> 00:00:48,970
So in this case, I'm going to just scan for nmap and it should come back fairly quickly

11
00:00:49,180 --> 00:00:53,770
and give us the list of open ports on this particular host.

12
00:00:54,460 --> 00:00:59,110
So as we expected, it came back and it said, hey, port eighty and four 443 three are open.

13
00:00:59,230 --> 00:01:00,520
Those two were expected.

14
00:01:00,760 --> 00:01:06,590
We can also go back and specify particular ports that we want this to scan for.

15
00:01:06,610 --> 00:01:10,620
So we're going to set up for port and we're going to give it a port numbers.

16
00:01:10,640 --> 00:01:17,920
If I wanted to look for Port 20-20 eighty eighty eight thousand three hundred eighty four for three

17
00:01:17,920 --> 00:01:23,440
just in case, 25 and whatever else I want to put on there, I can do this and it will come back as

18
00:01:23,440 --> 00:01:27,380
soon as it stands for specific ports and tell us what's open and what's not open.

19
00:01:27,880 --> 00:01:31,400
So when it comes down to any map, there are a few things that we need to understand.

20
00:01:31,420 --> 00:01:37,180
The first one being open, it means that this port is accessible and MAP has confirmed that that could

21
00:01:37,180 --> 00:01:40,540
be the term closed, which means that, hey, this port was not open.

22
00:01:40,720 --> 00:01:42,330
We can't really access it there.

23
00:01:42,400 --> 00:01:47,470
It's filtered, which in my view can determine whether or not the port is open because there's a packet

24
00:01:47,470 --> 00:01:50,860
filtering happening and unfiltered mean that the port is accessible.

25
00:01:50,860 --> 00:01:54,580
But EMAP is unable to understand whether or not it's open.

26
00:01:54,730 --> 00:01:57,130
And also read all of this on the NASA my website.

27
00:01:57,340 --> 00:02:01,770
I can link that to it in the resources, but those are the four common words you will see and maybe

28
00:02:01,780 --> 00:02:03,990
come back when it comes down to port scanning.

29
00:02:04,060 --> 00:02:07,320
You also have the ability to specify a range of ports.

30
00:02:07,340 --> 00:02:13,660
If you want to scan Port 80 all the way to Port 10000, you can also do that by doing 80, dyche 10000,

31
00:02:13,870 --> 00:02:14,740
by pushing enter.

32
00:02:14,740 --> 00:02:18,100
It will scan all those ports and let us know if they're open.

33
00:02:18,100 --> 00:02:24,910
For the sake of this example, I'm just going to do 80 to Port 500, which will result in telling us

34
00:02:24,910 --> 00:02:28,770
that Port 80 and 443 are open, as we expected early on.

35
00:02:28,810 --> 00:02:34,540
You can also use and map to see what version of whatever the version of the software in the back.

36
00:02:34,540 --> 00:02:40,000
And so, for example, they could tell us if they're using Apache, what version of a sausage based

37
00:02:40,000 --> 00:02:41,860
on its scripting, that it's been done so well.

38
00:02:41,950 --> 00:02:44,740
For example, right now I'm going to look for Port 80.

39
00:02:44,950 --> 00:02:48,130
I'm going to ask it to come back and give us some information about the house.

40
00:02:48,130 --> 00:02:54,430
As we can see right now, it came back and said, hey, this website is using Port eighty four HTP,

41
00:02:54,430 --> 00:02:58,480
which is open its running engine X one point ten point three.

42
00:02:58,660 --> 00:03:02,800
And it's using a boon to the other thing that we can do here is to give it a dashboard which will come

43
00:03:02,800 --> 00:03:08,960
back and give us the information on the operating system running on this particular host.

44
00:03:08,980 --> 00:03:11,770
So right now we're and doing end up on the hamster dot com.

45
00:03:11,770 --> 00:03:13,090
We're looking for Port 80.

46
00:03:13,300 --> 00:03:17,710
We're asking it to give us the version for whatever software is in the back end and also print out the

47
00:03:17,710 --> 00:03:19,060
operating system information.

48
00:03:19,350 --> 00:03:22,000
As you can see, it's coming back with the operating system right here.

49
00:03:22,270 --> 00:03:27,760
And it's also telling us that, again, it's using Engine X on urban to airport eighty.

50
00:03:28,030 --> 00:03:31,360
And again, if the more ports you have in here, the longer it's going to take to come up with this

51
00:03:31,360 --> 00:03:31,810
result.

52
00:03:32,090 --> 00:03:37,870
But again, this is very, very useful to see visually see what software and what things are being ran

53
00:03:37,870 --> 00:03:39,690
and the back end of a particular site.

54
00:03:39,970 --> 00:03:43,560
You also have the option to write your output to a file.

55
00:03:43,810 --> 00:03:50,530
So, for example, if you want to write this XML, all you had to do was go out and give it the dash

56
00:03:50,890 --> 00:03:51,310
o.

57
00:03:51,310 --> 00:03:58,000
But make sure the O is not capital this time and give it A and that will output the file to whatever

58
00:03:58,000 --> 00:03:59,020
file name we give it.

59
00:03:59,030 --> 00:04:03,880
You can also make a critical format or you can do it with XML depending on whichever one you want to

60
00:04:03,880 --> 00:04:04,160
use.

61
00:04:04,390 --> 00:04:10,570
I personally like to do for a while and then I'm going to give it the file name the hamster dot com

62
00:04:10,930 --> 00:04:17,830
in my text and the outputs of this will be sent into this file and we can actually check it out by copying

63
00:04:17,830 --> 00:04:23,320
it and doing a command to read the content of the file to confirm that it was actually done.

64
00:04:23,330 --> 00:04:24,160
So let's try it out.

65
00:04:24,460 --> 00:04:28,300
And as we can see right here, it's giving us the data on this host.

66
00:04:28,540 --> 00:04:29,200
It's giving us that.

67
00:04:29,200 --> 00:04:30,100
It's up there.

68
00:04:30,100 --> 00:04:32,650
It's also getting another line that says, hey, Port Authority is open.

69
00:04:32,650 --> 00:04:33,850
So we have multiple ports.

70
00:04:34,360 --> 00:04:39,370
It would do multiple lines telling us which ports are open and it would have to separated by spaces

71
00:04:39,610 --> 00:04:40,510
and giving us the port.

72
00:04:40,510 --> 00:04:43,660
No status for it if it's TCP.

73
00:04:43,660 --> 00:04:49,030
And also since we did Ardeche, S.V. is going to tell us the version of software that it's running on

74
00:04:49,030 --> 00:04:52,720
that particular host, I'm sorry, on that particular port.