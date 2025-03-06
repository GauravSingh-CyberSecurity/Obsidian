Analysis of SSRF lab:-  (http://ssrf6.naham.sec:8081/)

![[Screenshot From 2025-03-06 14-58-04.png]]
Let's look at our next example. In this example, we're going to try reaching a remote website. As always, we'll try Google.com.

As we can see, it replies and confirms that it can fetch the contents of the remote website we requested. We can also confirm this by using a Burp Collaborator or Netcat—whichever tool you prefer. Both are good ways to check for SSRF.

We’ll now push that in and confirm that a request is coming from another server that is not our IP address. For example, if I know my IP address and this request is coming from a different one, I can confirm that the request originated from a remote server.

To further validate this, we can enter a URL with an SSRF test from the target site. Once we submit the request, we can observe the incoming request and confirm that it was sent from the target website. Additionally, we can check the IP address, headers, and other request details.

Now, let's test with a local IP. For example, if we check the metadata service IP address, we know that every cloud service provider has this IP address, which sometimes provides metadata and, in some cases, even secret keys, depending on how it's configured.

We attempt to access this IP, but the server responds with a message stating that only remote URLs are allowed. Next, we try accessing localhost to see if we can reach the backend of the machine. Entering localhost yields the same restriction, implying that either there is an SSRF defense mechanism in place or some filtering is being applied.

However, a useful trick is leveraging a domain like `x.ip.io`. This domain allows you to resolve any IP address by appending it to their domain. This means we can use it to bypass filters and access internal IPs, such as `10.x.x.x` or even the cloud metadata service.

In our case, we attempt to resolve `169.254.169.254` using `169.254.169.254.ip.io`. We ensure the request is prefixed with `http://` and send it. This time, the response changes—it no longer states that the request is not remote. Instead, we get a "404 Not Found" response, likely because there is nothing hosted on the webroot.

To dig deeper, we try accessing the `/metadata` endpoint. Again, the response is "404 Not Found." However, for DigitalOcean, the correct metadata endpoint is `/metadata/v1`. When we send this request, the server responds with access to metadata information.

Although this specific case does not expose highly sensitive data, it demonstrates the impact of an SSRF vulnerability that allows access to localhost.

We also attempt to access `127.0.0.1` directly, but it appears there is some filtering against this address. The server blocks requests to `127.0.0.1`, but it allowed the metadata IP via the bypass.

This technique of using an external domain like `x.ip.io` is very useful for bypassing SSRF filters. Alternatively, you can create your own subdomain and configure an A record pointing to an internal IP address. This allows further testing, including targeting `169.254.169.254` for metadata access.

Using this approach, we successfully bypassed the blacklist and demonstrated how SSRF can be leveraged even when some filtering is in place.







---

1
00:00:00,120 --> 00:00:05,840
Let's look at our next example and this example, we're going to try and reach to a remote website,

2
00:00:05,850 --> 00:00:08,850
as always, we'll try Google dot com, but put it in.

3
00:00:08,850 --> 00:00:15,270
As we can see, it is going to reply and tell us that, hey, I can fetch the contents of the remote

4
00:00:15,270 --> 00:00:16,260
website you have asked for.

5
00:00:16,630 --> 00:00:21,450
We can also confirm this by using a bird collaborator or you can use Netcare, whatever one you want

6
00:00:21,450 --> 00:00:22,020
to use.

7
00:00:22,440 --> 00:00:23,140
It's up to you.

8
00:00:23,160 --> 00:00:28,290
Both of them are a good way to make sure there's a nice SRF going to push that in there.

9
00:00:28,800 --> 00:00:31,950
And we're going to actually put it in there.

10
00:00:32,310 --> 00:00:37,500
And we're going to confirm that there is going to be a request coming from another server.

11
00:00:37,500 --> 00:00:38,980
That's not our IP address.

12
00:00:39,000 --> 00:00:41,640
So, for example, here I know my IP address.

13
00:00:41,820 --> 00:00:46,560
This is not that I can confirm that this request came from remote server.

14
00:00:46,710 --> 00:00:55,980
You can also go as far as typing in our URL and putting in SRF test from Target site.

15
00:00:56,320 --> 00:01:02,670
As soon as we put that in, we'll get another request and we can observe the request that came in and

16
00:01:02,670 --> 00:01:08,820
we can confirm that this is the request that we wanted to send from our Target website.

17
00:01:09,150 --> 00:01:14,430
And of course, we have the IP address and we can see what kind of header is it sent us and so on.

18
00:01:15,390 --> 00:01:19,210
But now let's look at what we can do with a local IP.

19
00:01:19,230 --> 00:01:24,900
So, for example, if I want to check for the amount of data IP address, again, as a reminder, every

20
00:01:24,900 --> 00:01:27,720
cloud service provider has this IP address.

21
00:01:28,020 --> 00:01:33,400
They gave me some metadata sometimes to give you access to the secret keys depending on how it's configured.

22
00:01:33,780 --> 00:01:39,300
So in this case, we're going to try it out and the server comes back and says, hey, only remote,

23
00:01:39,300 --> 00:01:40,200
you are allowed.

24
00:01:40,220 --> 00:01:42,030
We're also going to look for localhost.

25
00:01:42,780 --> 00:01:49,920
We want to see if we have access to the localhost on the machine where this backend is functioning or

26
00:01:49,920 --> 00:01:50,350
working on.

27
00:01:50,530 --> 00:01:52,440
So we're going to type that same thing.

28
00:01:52,750 --> 00:01:59,520
So that implies that either they're they have some defense mechanism against SRF or that there is some

29
00:01:59,520 --> 00:02:00,480
filtering in place.

30
00:02:01,140 --> 00:02:04,350
Lucky for us, there is a website called IP Io.

31
00:02:04,440 --> 00:02:06,570
You can also create your own domain and do this.

32
00:02:06,870 --> 00:02:12,390
You can both of those work, but it's IP pretty much lets you resolve whatever IP address you put in

33
00:02:12,390 --> 00:02:13,470
behind their domain.

34
00:02:13,470 --> 00:02:20,280
So whatever goes behind X IP that IO will be the IP were resolve to and that could be always a local

35
00:02:20,280 --> 00:02:22,260
IP address like 10 days or that one.

36
00:02:22,560 --> 00:02:27,360
Or it could be something like the metadata IP address that we want to get access to.

37
00:02:28,050 --> 00:02:28,950
So we got to type that in.

38
00:02:28,950 --> 00:02:36,120
And in this example, I want to access one six nine to five four one six nine to five for that IP that

39
00:02:36,120 --> 00:02:42,280
I oh I got to make sure but HTP before it and we're going to send our request.

40
00:02:42,300 --> 00:02:47,040
So now the request is no longer telling us that it's not a remote website, just simply coming back

41
00:02:47,040 --> 00:02:48,660
and saying, hey, for or for not found.

42
00:02:49,080 --> 00:02:51,440
And that's probably because nothing is hosted on the webroot.

43
00:02:51,720 --> 00:02:57,000
But if we type in metadata metadata, we send that request, same thing.

44
00:02:57,000 --> 00:03:02,210
But we know for the ocean, the correct request is metadata slash V1.

45
00:03:02,370 --> 00:03:05,070
We're going to try that out, as we put it, go.

46
00:03:05,280 --> 00:03:11,100
It comes back and gives us access to the metadata and stance and the information that comes with it.

47
00:03:11,340 --> 00:03:18,570
In this case, we don't have access to anything supersensitive, but we are showing the impact of having

48
00:03:18,570 --> 00:03:24,480
necessar with access to localhost and also changes how to localhost itself.

49
00:03:24,900 --> 00:03:31,200
Again, if you want to refer to a local host with an IP address that IP addresses one seven zero zero

50
00:03:31,830 --> 00:03:37,140
one, we're going to push that in and we to take the metadata out and it goes back and it says same

51
00:03:37,140 --> 00:03:37,560
thing.

52
00:03:37,800 --> 00:03:44,070
It looks like they are doing some sort of filtering against one two seven zero one.

53
00:03:44,220 --> 00:03:49,800
So, I mean, this is still being filtered in comparison to the metadata IP address that we found to

54
00:03:49,800 --> 00:03:50,520
bypass for it.

55
00:03:50,910 --> 00:03:53,760
So it's a great tool to know, again, you can make your own domain.

56
00:03:53,760 --> 00:04:00,930
So if you own a domain like sec dot com, you can go ahead and make that record and a record within

57
00:04:00,930 --> 00:04:06,870
your management with the domain management site and pointed to you can make it as a sort of domain and

58
00:04:07,710 --> 00:04:13,380
point that to whatever IP address you want, including the one six nine to five for IP address that

59
00:04:13,380 --> 00:04:14,130
we're going to use.

60
00:04:14,580 --> 00:04:21,150
But we want to make a complicated IP that I is a great resource to use in case of unnecessary.
