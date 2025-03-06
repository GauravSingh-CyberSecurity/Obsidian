

SSRF is one of my absolute favorite vulnerabilities to look for. Not only is it a critical or high-severity vulnerability, but it also often has the highest payout in bug bounty programs. It's also really fun to find because there are endless ways to exploit it. However, it all comes down to deeply understanding how it works, how the application functions, and then combining that knowledge to identify the vulnerability.

For this specific type of SSRF, I highly recommend looking for integrations, webhooks, or any feature that allows you to input a URL. Point the URL to your own server and check if the request to your server is made from the client side or the server side. If the request is coming from an IP that doesn’t belong to you, or if it's an IP associated with the company or their cloud provider, you may have found an SSRF vulnerability.

When it comes to SSRF, the biggest areas to target are internal networks and cloud metadata services. You can conduct reconnaissance to find out where internal services are hosted and attempt to query them. Alternatively, you can target cloud metadata services (such as AWS metadata endpoints) to extract sensitive information like instance credentials.

SSRF comes in different forms. It can be **blind SSRF**, **full-response SSRF**, or **limited-response SSRF**. If you notice that a request is coming from a server, experiment with it—figure out what data you have access to and how you can demonstrate its impact. When reporting SSRF vulnerabilities, proving the full impact is essential for maximizing your bounty and ensuring the security team understands the severity of the issue.



---

1
00:00:00,060 --> 00:00:06,330
So that was a SRF as a as one of my absolute favorite vulnerabilities to look forward, not only it's

2
00:00:06,330 --> 00:00:12,120
a critical or high vulnerability, it's the most pay-out in some cases, but it also becomes really,

3
00:00:12,120 --> 00:00:12,570
really fun.

4
00:00:12,580 --> 00:00:17,270
There's endless ways I find it necessary, but it all comes down to really deeply understanding how

5
00:00:17,330 --> 00:00:23,370
it works and how the application works and combining the two together in order to find him for this

6
00:00:23,370 --> 00:00:28,740
one type specifically, I highly recommend looking for integration's web hook, anything that actually

7
00:00:28,770 --> 00:00:33,960
allows you to feel that you are URL and pointing it to your server and seeing if the request to your

8
00:00:33,960 --> 00:00:39,000
server is being made client side or server side as the IP address that's making the request doesn't

9
00:00:39,000 --> 00:00:43,950
belong to you or is a random IP that belongs to this company or it's coming from the AWB or the cloud

10
00:00:43,950 --> 00:00:47,730
in the sense that the company is using and it comes to SRF.

11
00:00:48,030 --> 00:00:53,460
==The biggest thing is you can either look for local network so you do some recon, find out where the==

==12==
==00:00:53,640 --> 00:00:59,330==
==internal services are pointing to sort of to it and see if it renders or you can actually look for HWC==

==13==
==00:00:59,340 --> 00:01:04,590==
==metadata or other cloud providers metadata and seeing if you can pull data from it in that way.==

==14==
==00:01:05,250 --> 00:01:09,330==
==Last but not least, I want to make sure I call this out as a sort of has a ton of different flavors.==

==15==
==00:01:09,520 --> 00:01:15,360==
==There is blind, there is the full response and limited necessar of foul play around.==

==16==
==00:01:15,360 --> 00:01:20,550==
==If you see a request coming from a server, play around with it, understand what data you have access==

==17==
==00:01:20,550 --> 00:01:25,860==
==to and how can you prove impact to the customer's team that's receiving a vulnerability in order to==

==18==
==00:01:25,860 --> 00:01:30,840==
==maximize your bounty and also showing the impact of your vulnerability based on the things that you==

==19==
==00:01:30,840 --> 00:01:31,240==
==have found.==