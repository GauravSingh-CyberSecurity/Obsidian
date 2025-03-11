![[Pasted image 20250311202454.png]]

1
00:00:00,360 --> 00:00:03,060
Let's talk about reconnaissance, also known as recon.


![[Screenshot From 2025-03-11 20-25-38.png]]
2
00:00:03,270 --> 00:00:10,060
The idea behind recon is to find as many assets and content on our website as we can in order to further

3
00:00:10,060 --> 00:00:11,250
our attack vector.

4
00:00:11,460 --> 00:00:16,050
In other words, the more assets we find, the more applications(locations) we have to hack on and the more content we

5
00:00:16,050 --> 00:00:19,380
have, there are more leads for us to potentially find vulnerabilities.




![[Screenshot From 2025-03-11 20-27-08.png]]
6
00:00:19,470 --> 00:00:24,410
As I mentioned earlier, the biggest reason behind doing recon is to find a bigger attack surface.

7
00:00:24,420 --> 00:00:27,570
That means that we can extend the number of applications that we can hack on.

8
00:00:27,880 --> 00:00:32,820
But more importantly, we want to find devlopment, staging or QA environments because these are

9
00:00:32,820 --> 00:00:38,460
the ones that usually have the most vulnerabilities, because they're created for testing purposes and

10
00:00:38,460 --> 00:00:39,590
only for internal users.

11
00:00:39,600 --> 00:00:46,320
In a lot of cases ,  also doing recon could lead into finding ==sensitive information like API documentation== , ==logs, backups and other forms of information that could lead to a vulnerability.==

13
00:00:51,770 --> 00:00:56,430
You can do this in a bunch of different ways, but please make sure that you read companies bug bounty program policy to make sure that you can do recon properly and go after their assets and infrastructure

15
00:01:02,370 --> 00:01:05,640
because a lot of companies do not include everything they own.

16
00:01:05,850 --> 00:01:11,010
So in other words, a company like Google, Facebook, Ryzen, Media, Snapchat or GM, they include

17
00:01:11,010 --> 00:01:16,170
all of the digital assets, which makes their scope a lot bigger than a company like Airbnb, where

18
00:01:16,170 --> 00:01:18,000
they only include their main application.





![[Screenshot From 2025-03-11 20-30-22.png]]
19
00:01:18,030 --> 00:01:19,890
Now, let's talk about asset discovery.

20
00:01:19,890 --> 00:01:27,780
Asset discovery is the idea to map out a company's infrastructure by knowing what domains they own or

21
00:01:27,780 --> 00:01:34,650
companies or companies that have acquired and also being able to map out subdomains on each of those

22
00:01:34,650 --> 00:01:35,670
main route domains.

23
00:01:36,360 --> 00:01:42,090
So, for example, if you're going to Google.com , mail.Google.com , drive.Google.com  , store.Google.com and all these

24
00:01:42,090 --> 00:01:48,030
different subdomains, all these different domains become a subdomain because they are behind the main

25
00:01:48,030 --> 00:01:49,380
route domain, like Google.com.

26
00:01:49,660 --> 00:01:54,380
We want to find as many as best as we can because those are each different assets that we can look at,

27
00:01:54,470 --> 00:01:58,500
can identify these different domains passively through sources like Google.

28
00:01:58,590 --> 00:02:00,360
We'll cover this later in our lab.

29
00:02:00,690 --> 00:02:05,430
But you can go on to Google and type in ==site: uber.com -www== and you can start seeing all the different
![[Screenshot From 2025-03-11 20-33-40.png]]
30
00:02:05,430 --> 00:02:11,910
domains that are under Uber  itself and also look for subdomains by looking at certificate transparency.

31
00:02:12,150 --> 00:02:17,760
In other words, any subdomain that has a SSL certificate attached to it because of the certificate

32
00:02:17,760 --> 00:02:24,240
transparency logs, you can pull that information out through some automation or some searches and you

33
00:02:24,240 --> 00:02:25,410
can look for them online.

34
00:02:25,440 --> 00:02:30,660
You can also brute force for these where you use a dictionary file that has a number of different words

35
00:02:30,810 --> 00:02:36,470
and you put that word before each domain and see if it comes back as positive or if it's available or

36
00:02:36,470 --> 00:02:36,540
it Responses give you a list of those domains that were available.

38
00:02:39,930 --> 00:02:41,850
==I personally don't do a lot of brute force thing.==

39
00:02:42,060 --> 00:02:44,760
It's definitely worth investing some time into doing it.

40
00:02:45,030 --> 00:02:49,830
But going down the path of doing certificate transparencies a lot faster and doing it Passively could

41
00:02:49,830 --> 00:02:51,720
save you a number of hours of work.

42
00:02:52,050 --> 00:02:54,240
But you can combine the two to get more information.

43
00:02:54,390 --> 00:02:56,370
This is all a personal preference.

44
00:02:56,490 --> 00:02:57,270
You can do both.

45
00:02:57,280 --> 00:03:02,340
You can choose to stick to one or however you find it fit, depending on the program that you're hacking on




![[Pasted image 20250311203752.png]]
47
00:03:02,870 --> 00:03:04,170
Let's talk about content discovery.

48
00:03:04,180 --> 00:03:10,800
The idea behind content discovery is to find additional or sensitive folders, endpoints, documentation

49
00:03:10,980 --> 00:03:14,550
or features that may not be directly accessible within the UI.

50
00:03:14,820 --> 00:03:20,340
So we can , this includes finding debug or diagnosis information, API documentation.

51
00:03:20,340 --> 00:03:26,220
As I mentioned earlier, we can look for admin panels which may have default or weak credentials.

52
00:03:26,430 --> 00:03:31,470
It can also do port scanning with nmap, which shows you what Other web ports or other ports are

53
00:03:31,470 --> 00:03:34,680
available on a particular domain or an IP address.

54
00:03:34,950 --> 00:03:40,560
And you can further your attack surface by finishing up the ports scan.  for example, a website may be

55
00:03:40,560 --> 00:03:45,900
running that application on Port 80 and 443 by default, which most websites do.

56
00:03:46,140 --> 00:03:51,390
But in addition to that, they may have the Port 843 opened or to have some other application

57
00:03:51,390 --> 00:03:55,980
running in the backend that communicates with the core or main application that you were looking at,

58
00:03:56,160 --> 00:03:57,660
Port 80 or 443.




![[Screenshot From 2025-03-11 20-40-11.png]]
59
00:03:57,840 --> 00:03:59,370
So let's talk about asset discovery further.

60
00:03:59,490 --> 00:04:00,190
How do you do it?

61
00:04:00,210 --> 00:04:03,390
So the first one is Brute-forcing again, this is very, very common.

62
00:04:03,420 --> 00:04:08,050
You can use tools like directory ==dirsearch== for ==WFuzz or gobuster.==

63
00:04:08,490 --> 00:04:12,510
My preference is WFuFF and then directory-search(dirsearch) is a second one.

64
00:04:12,810 --> 00:04:14,640
They're really, really good at very, very fast.

65
00:04:14,930 --> 00:04:20,520
Can also do just passively through tools like ==get all your URLs== or ==way back URLs==, which we'll

66
00:04:20,520 --> 00:04:24,860
cover later, maybe at some point throughout the course, but also have JavaScript files.

67
00:04:24,870 --> 00:04:27,030
There are a very, very good resource.

68
00:04:27,240 --> 00:04:32,430
Every application that is out there and has some functionality runs on JavaScript, uses JavaScript

69
00:04:32,430 --> 00:04:38,040
in some way, and within JavaScript you can look for different API endpoints or actual endpoints that

70
00:04:38,040 --> 00:04:42,340
the application communicates with and understand what data it requires and how it works.

71
00:04:42,810 --> 00:04:47,160
Doing this requires a little bit of ==understanding of JavaScript, which I highly recommend looking into==

==72==
==00:04:47,160 --> 00:04:49,410==
==if you want to become a successful bug bounty hunter.==

73
00:04:49,740 --> 00:04:52,860
But if you know how JavaScript works, this is a goldmine.

74
00:04:52,860 --> 00:04:55,410
Again, looking for JavaScript files, that's very, very important.




![[Screenshot From 2025-03-11 20-43-22.png]]
75
00:04:55,530 --> 00:04:56,970
So let's put this as a whole picture.

76
00:04:57,300 --> 00:04:58,170
What does this look like?

77
00:04:58,380 --> 00:04:59,820
You run nmap on a.

78
00:04:59,870 --> 00:05:05,390
Target, it comes back and tells you port 80 ,443 and 843 all open, you do directory-Bruteforcing and it shows admin is available and sends a 403 response code to go back

80
00:05:11,180 --> 00:05:12,010
to the first chapter.

81
00:05:12,020 --> 00:05:13,030
We talk to about web response.

82
00:05:13,430 --> 00:05:18,050
We've talked about response codes and what they mean , 403 means it's there, but we don't have

83
00:05:18,050 --> 00:05:18,920
access to it.

84
00:05:19,160 --> 00:05:21,350
So we brute force the admin directory again.

85
00:05:21,590 --> 00:05:27,770
We find another file, for example, user.PHP,  which returns at 200, indicating

86
00:05:27,770 --> 00:05:30,200
that we have on authenticated access to it.

87
00:05:30,470 --> 00:05:35,390
And we repeat this for every domain and subdominant port and folder, and we just extend our attack

88
00:05:35,390 --> 00:05:39,710
surface by finding more subdomains, more files and more open ports.
