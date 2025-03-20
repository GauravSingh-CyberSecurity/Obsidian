
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
The next thing we're going to look at is how to use Nmap, and Nmap is very, very helpful when it comes

2  
00:00:06,580 --> 00:00:12,400  
down to scanning IT infrastructure or a particular domain or list of domains or subdomains to look for

3  
00:00:12,400 --> 00:00:13,200  
open ports.

4  
00:00:13,240 --> 00:00:19,120  
Most applications are hosted on port 80 or 443, but there are a lot of cases where you may find other secondary

5  
00:00:19,120 --> 00:00:26,140  
applications, backends, or APIs being hosted on a different port like 8080, 8000, 10000, and so on.

6  
00:00:26,140 --> 00:00:27,240  
You can also see if there are other services running on that host and if those services are vulnerable

7  
00:00:27,520 --> 00:00:32,710  
to a particular CVE by doing a port scan. You can do this in a number of different ways.

8  
00:00:32,710 --> 00:00:38,360  
The most basic way of doing it is just typing in Nmap and whatever you want to scan for.



10
00:00:43,000 --> 00:00:48,970
So in this case, I'm going to just scan for ==`nmap nahamstore.com`== and it should come back fairly quickly
and give us the list of open ports on this particular host.

11
00:00:54,460 --> 00:00:59,110
So as we expected, it came back and it said, hey, port 80 and 443 are open.

12  
00:00:54,460 --> 00:00:59,110  
Those two were expected.

13  
00:00:59,230 --> 00:01:00,520  
We can also go back and specify particular ports that we want this to scan for.

14  
00:01:00,760 --> 00:01:06,590  
So we're going to set it up for ports and we're going to give it some port numbers.
![[Screenshot From 2025-03-20 14-32-33.png]]
15  
00:01:06,610 --> 00:01:10,620  
If I wanted to look for ports 20, 22, 8080, 8000, 3389, 25, and whatever else I want to put on there, I can do this, and it will come back as

16  
00:01:10,640 --> 00:01:17,920  
soon as it scans for specific ports and tell us what's open and what's not open.
![[Pasted image 20250320143424.png]]
17  
00:01:17,920 --> 00:01:23,440  
So when it comes down to Nmap, there are a few things that we need to understand.

18  
00:01:23,440 --> 00:01:27,380  
The first one being "open," which means that this port is accessible and Nmap has confirmed that that could

19  
00:01:27,880 --> 00:01:31,400  
be the term "closed," which means that, hey, this port was not open.

20  
00:01:31,420 --> 00:01:37,180  
We can't really access it there.

21  
00:01:37,180 --> 00:01:40,540  
It's "filtered," which means Nmap can't determine whether or not the port is open because there's packet

22  
00:01:40,720 --> 00:01:42,330  
filtering happening, and "unfiltered" means that the port is accessible,

23  
00:01:42,400 --> 00:01:47,470  
but Nmap is unable to understand whether or not it's open.

24  
00:01:47,470 --> 00:01:50,860  
And also, you can read all of this on the Nmap website.

25  
00:01:50,860 --> 00:01:54,580  
I can link that to it in the resources, but those are the four common terms you will see and may

26  
00:01:54,730 --> 00:01:57,130  
come across when it comes down to port scanning.

27  
00:01:57,340 --> 00:02:01,770  
You also have the ability to specify a range of ports.

30
00:02:07,340 --> 00:02:13,660
If you want to ==scan Port 80 all the way to Port 10000==, you can also do that by typing 80-10000,
![[Screenshot From 2025-03-20 14-35-33.png]]

or  ==`nmap nahamstore.com -p0-65535`==  or   `nmap -p 0-10000 digicompany.deriviumcap.com`


31
00:02:13,870 --> 00:02:14,740
by pushing enter.

32
00:02:14,740 --> 00:02:18,100
It will scan all those ports and let us know if they're open.

![[Pasted image 20250320143622.png]]
33
00:02:18,100 --> 00:02:24,910
For the sake of this example, I'm just going to do 80 to Port 500, which will result in telling us

34
00:02:24,910 --> 00:02:28,770
that Port 80 and 443 are open, as we expected early on.



![[Pasted image 20250320143712.png]]
33  
00:02:18,100 --> 00:02:24,910  
You can also use Nmap to see what version of software is running on the backend.

34  
00:02:24,910 --> 00:02:28,770  
So, for example, it can tell us if they are using Apache, what version of it, or if it's running a specific software like Nginx or others.

35  
00:02:28,810 --> 00:02:34,540  
For example, right now I'm going to look for port 80.

36  
00:02:34,540 --> 00:02:40,000  
I'm going to ask it to come back and give us some information about the host.
![[Pasted image 20250320143802.png]]
37  
00:02:40,000 --> 00:02:41,860  
As we can see right now, it came back and said, hey, this website is using port 80 for HTTP,

38  
00:02:41,950 --> 00:02:44,740  
which is open. It's running Nginx 1.10.3.

39  
00:02:44,950 --> 00:02:48,130  
And it's using Ubuntu.


![[Screenshot From 2025-03-20 14-39-10 1.png]]
The other thing that we can do here is to give it a command to detect the operating system running on this particular host.

41  
00:02:54,460 --> 00:02:59,110  
So right now we're doing an Nmap scan on **hamster.com**, and we're looking for port 80.

42  
00:02:59,110 --> 00:03:02,800  
We're asking it to give us the version of whatever software is in the backend and also print out the

43  
00:03:02,800 --> 00:03:08,960  
operating system information.

44  
00:03:08,980 --> 00:03:11,770  
As you can see, it's coming back with the operating system information right here.

45  
00:03:11,770 --> 00:03:13,090  
And it's also telling us that, again, it's using Nginx on Ubuntu for port 80.

46  
00:03:13,300 --> 00:03:17,710  
And again, the more ports you have in your scan, the longer it will take to come up with this

47  
00:03:17,710 --> 00:03:19,060  
result.

48  
00:03:19,350 --> 00:03:22,000  
But again, this is very, very useful to visually see what software and services are running

49  
00:03:22,270 --> 00:03:27,760  
on the backend of a particular site.

50  
00:03:28,030 --> 00:03:31,360  
You also have the option to write your output to a file.

51  
00:03:31,360 --> 00:03:31,810  
So, for example, if you want to write this to XML, all you had to do was go out and give it the -o

52  
00:03:31,810 --> 00:03:37,860  
(ensure the "o" is lowercase this time) and specify a filename, and it will output the results to the specified file.

53  
00:03:37,870 --> 00:03:40,510  
You can also choose other formats, such as XML, depending on whichever one you want to use.

54  
00:03:40,510 --> 00:03:43,660  
I personally prefer to use the "txt" format and then give it the filename, for example, **hamster.com.txt**,

55  
00:03:43,660 --> 00:03:49,030  
and the output of this will be sent into this file. We can then check it out by copying the file and using

56  
00:03:49,030 --> 00:03:52,720  
a command to read the content of the file to confirm that it was done properly.

57  
00:03:52,720 --> 00:03:59,020  
Let's try it out.

58  
00:03:59,030 --> 00:04:03,880  
As we can see right here, it's giving us the data on this host.

59  
00:04:03,880 --> 00:04:04,160  
It's showing that

60  
00:04:04,160 --> 00:04:07,870  
it's up and running. It's also showing another line that says, hey, port 80 is open.

61  
00:04:07,870 --> 00:04:08,790  
So we have multiple ports

62  
00:04:08,790 --> 00:04:13,360  
listed, with each one showing if it's open or closed, as well as the protocol and version.

63  
00:04:13,660 --> 00:04:19,030  
It will list each port and its status if it's TCP, and also, since we did `-sV`, it will tell us the version of the software running

64  
00:04:19,030 --> 00:04:22,720  
on that particular host and port.