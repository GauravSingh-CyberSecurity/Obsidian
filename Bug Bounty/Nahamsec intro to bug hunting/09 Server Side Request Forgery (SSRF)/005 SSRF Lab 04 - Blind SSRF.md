Analysis of SSRF lab:-  (http://ssrf5.naham.sec:8081/)




---
1
00:00:00,120 --> 00:00:04,740
Now, let's take another example of this SRF and this case, this website is going to tell us whether

2
00:00:04,740 --> 00:00:06,390
or not a website is accessible.

3
00:00:06,420 --> 00:00:10,920
So if I typed in something like Google dot com, it's going to come back and say, hey, this website

4
00:00:10,920 --> 00:00:13,620
is accessible and I can actually get a hold of it.

5
00:00:13,630 --> 00:00:15,060
So let's try another random website.

6
00:00:15,060 --> 00:00:17,730
We're going to example dot com, just another one to see if it works.

7
00:00:17,940 --> 00:00:18,760
Website is up.

8
00:00:18,780 --> 00:00:24,380
Sure enough, when I want to see if we can exploit this in any way where it could be a potential port

9
00:00:24,420 --> 00:00:27,300
scan, said SRF, bonus SRF or whatever else.

10
00:00:27,390 --> 00:00:31,310
So the first step we want to do is we can verify that this is actually vulnerable.

11
00:00:31,560 --> 00:00:35,180
You can either do this with your Nikhat or you can use burb sweet collaborator.

12
00:00:35,460 --> 00:00:40,710
I'm going to just have it on the Claverie client just makes it easier for me for the sake of this example.

13
00:00:41,550 --> 00:00:44,040
Again, you can use a you can use your own server.

14
00:00:44,070 --> 00:00:45,570
You can use an account, whatever that is.

15
00:00:45,880 --> 00:00:49,230
And we're just going to send this request out to says website is up.

16
00:00:49,230 --> 00:00:56,010
So that should probably get a request right here to tell us that we did get a request from the server

17
00:00:56,630 --> 00:01:01,320
and to our collaborator so that we can confirm that, hey, this does make a suicide request.

18
00:01:01,560 --> 00:01:07,640
The API, just that it's coming from, is from the remote server and not our own browser and computer.

19
00:01:07,680 --> 00:01:10,950
So next thing I want to do here is we want to see if we have access to localhost.

20
00:01:11,190 --> 00:01:14,820
You can do this either by typing in localhost or the API just for it.

21
00:01:15,100 --> 00:01:20,970
So I'm going to try this comes back and says, hey, only you URLs are allowed, so we can't really

22
00:01:21,240 --> 00:01:22,320
type in any IP.

23
00:01:22,340 --> 00:01:25,920
I just want to just go ahead and try localhost say the same thing.

24
00:01:26,190 --> 00:01:27,990
Well, let's see if we can trick this into working.

25
00:01:27,990 --> 00:01:33,960
So I'm going to do here is I'm going to serve localhost and ask for Port A-T, which comes back surprisingly

26
00:01:33,960 --> 00:01:38,550
and breaks the logic on this app and says, hey, the website is up and we can make sure this is invalid

27
00:01:38,550 --> 00:01:42,750
by giving it a random port, 80 one unlikely for it to be open on the server.

28
00:01:42,900 --> 00:01:45,060
I'm going to go ahead and hit it says requests failed.

29
00:01:45,330 --> 00:01:51,120
So now we know that we can actually hit a local service like localhost or any other IP addresses that

30
00:01:51,120 --> 00:01:54,690
are around it, and we are able to communicate with it back and forth.

31
00:01:55,060 --> 00:01:59,400
So now the next thing we want to do is we want to see if it actually allows us to scan some of the most

32
00:01:59,400 --> 00:02:01,450
common ports that is usually open on a server.

33
00:02:01,710 --> 00:02:06,940
Again, this depends on your target, but a lot of cases, port twenty two is used for a sausage.

34
00:02:07,170 --> 00:02:08,430
That's how they accessed the server.

35
00:02:08,610 --> 00:02:11,370
We're going to try and see if this comes back and give us anything.

36
00:02:11,730 --> 00:02:14,260
And if we do that, it comes back and gives us a different error.

37
00:02:14,280 --> 00:02:19,860
It's not saying, hey, the website is not up, so let's try, for example, localhost eighty one again,

38
00:02:19,860 --> 00:02:20,910
which was an invalid port.

39
00:02:21,160 --> 00:02:22,590
It doesn't say request failed.

40
00:02:22,740 --> 00:02:27,960
It says, hey, I don't recognize this as an HTP request, but something is coming back which is giving

41
00:02:27,960 --> 00:02:32,160
us a different area where it indicates that, hey, this port may be actually open.

42
00:02:32,160 --> 00:02:35,610
We can try and do another port like a thousand again, request failed.

43
00:02:35,970 --> 00:02:36,480
What about port?

44
00:02:36,510 --> 00:02:42,510
Twenty five requests so we can pretty much port scan and understand how many ports and what exact ports

45
00:02:42,750 --> 00:02:45,690
are open on this box based on the orders that we get.

46
00:02:45,720 --> 00:02:50,910
So again, if I do Port 20, port twenty two, I get a different era indicator.

47
00:02:50,910 --> 00:02:52,110
Something is coming back.

48
00:02:52,330 --> 00:02:57,480
It's not the response that the server was expecting, but as the other thing, another area for us that

49
00:02:57,480 --> 00:03:02,700
indicates, hey, there's something fishy happening here and shows us that there is actually a valid

50
00:03:02,700 --> 00:03:07,680
open port and we can use that as a proof of concept to tell the company that, hey, not only this has

51
00:03:08,040 --> 00:03:13,140
giving us access to a local network, but it also allows us to port Skane.

52
00:03:13,290 --> 00:03:18,390
But we can't really see the content of any of these ports, but we can actually see that for four,

53
00:03:18,630 --> 00:03:21,390
three and twenty two for localhost are open.

54
00:03:21,660 --> 00:03:24,210
In this case, we don't have access to any other IP addresses.

55
00:03:24,390 --> 00:03:27,940
But let's say if we could access some random local IP, we could do the same thing.

56
00:03:27,960 --> 00:03:33,210
So if you think there are other IP addresses, if you think there are other IP addresses within this

57
00:03:33,210 --> 00:03:38,670
private network, you can do the same thing by giving it the IP address, Port 22 and seeing what comes

58
00:03:38,670 --> 00:03:38,940
back.

59
00:03:39,210 --> 00:03:43,410
And of course, if he comes back with request failed, then we can kind of assume that this IP address

60
00:03:43,410 --> 00:03:47,910
is not up and we don't have access to it or there are no reports.

61
00:03:48,270 --> 00:03:49,680
There are no open ports on it.

