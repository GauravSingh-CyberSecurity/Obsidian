Analysis of SSRF lab:- ( http://ssrf4.naham.sec:8081/ )

![[Pasted image 20250306123054.png]]
this example is another website that says check whether a website is up.


So whatever I.P. address we give it, it's going to tell us if there is a response for it, whether
if or not, if the website is up.
As always, we're going to type in **Google.com**. This comes back and says, "Hey, the website is up."

![[Screenshot From 2025-03-06 12-42-12.png]]
Obviously, we can't use a file:///etc/passwd because it's being filtered. But this is a blind SSRF, so whatever IP address we provide, it will check if there is a response, indicating whether the website is up or not.


In this case, if we get a **404**, we know that the **metadata IP address** for https://example.com/nonexistentpage returns a **404**.
![[Screenshot From 2025-03-06 12-44-21.png]]
 If I enter this IP address and it says "Invalid," it means there should be a response.



Now, let's try giving it an **invalid IP address**—one that is not available. It should come back with a **request failed** message.
![[Screenshot From 2025-03-06 12-45-52.png]]
When dealing with a **blind SSRF**, it's important to observe how the application behaves. In some cases, the application may return different responses depending on the request. For example, in this case, the server responds with **"Request Failed"** when attempting to connect.





![[Screenshot From 2025-03-06 12-52-00.png]]
Now, let's try scanning different ports (for this target http://localhost ). I'll start with **port 10000**(http://localhost:10000 ). As you can see, it's taking a little longer to load before returning a response. Now, let's try **port 80**, which is typically used for HTTP.


http://localhost:80
For this one, I'm going to try **localhost on port 80**. It comes back and confirms that we have access to **localhost**, proving that an SSRF vulnerability exists. We are able to access the local network.
![[Screenshot From 2025-03-06 12-52-58.png]]









![[Screenshot From 2025-03-06 12-54-20.png]]
Now, let's try the same request but using an **IP address ( http://127.0.0.1 ) instead of localhost**. You'll notice that some blind SSRF protections exist, but there are restrictions we might need to bypass. 


Since we were able to access **localhost** (http://localhost ), let's try scanning another port.
I'll attempt to connect to another **port on localhost** (http://localhost:8080). This time, the response is **"Request Failed"**, and it returned fairly quickly. Now, let's try another port (http://localhost:10000) and observe the response time.



The goal here is to scan as many ports as possible to determine whether the SSRF vulnerability grants access to an **internal network**. This allows us to enumerate the internal infrastructure and identify **open ports** that could be further explored.


---

Now, let's have a look at another example. This example is another website that checks whether a website is up.

















Always pay close attention to responses. In some cases, the application may not return verbose error messages, but a noticeable **delay** can indicate whether a port is open or closed.

For example, if the response takes significantly longer, it suggests that the request was processed but the port might be closed. If the response is instant, it likely means the request was blocked or failed.

In this case, if I provide a different IP address, you’ll notice that it takes longer compared to an available resource, which responds much faster.

So, from this example, remember that **blind SSRFs** can be tricky. You need to experiment and analyze how the application behaves. Pay close attention to **response times, error messages, and unusual behaviors** to identify potential vulnerabilities.

# Transcript of lab: 

1
00:00:00,360 --> 00:00:06,210
Now, let's have a look at another example, and this example is another website that says check whether

2
00:00:06,240 --> 00:00:07,310
a website is up.

3
00:00:07,320 --> 00:00:09,930
So as always, we're going to type in Google dot com.

4
00:00:10,470 --> 00:00:13,050
This comes back and says, hey, website is up.

5
00:00:13,650 --> 00:00:17,550
Obviously, we can use a faulty password because it's being filtered.

6
00:00:17,820 --> 00:00:19,590
But also this is a blog necessary.

7
00:00:19,680 --> 00:00:25,120
So whatever I.P. address we give it, it's going to tell us if there is a response for it, whether

8
00:00:25,120 --> 00:00:26,620
it or not, if the website is up.

9
00:00:27,150 --> 00:00:33,930
So in this case, if we had a 404, because again, from our previous examples, we know that the metadata

10
00:00:33,930 --> 00:00:37,920
IP address for the general ocean comes back with a four or four.

11
00:00:38,250 --> 00:00:40,860
So if I take this and it says involved, it should be a response.

12
00:00:41,160 --> 00:00:43,320
But now we're going to give it an invalid IP address.

13
00:00:43,320 --> 00:00:44,850
This IP address is not available.

14
00:00:45,210 --> 00:00:46,980
Should come back and say a request felt.

15
00:00:47,370 --> 00:00:52,830
So when it comes down to a block necessary, if you want to pay attention to how the application behaves,

16
00:00:53,040 --> 00:00:58,860
in some cases, the application may even come back and say something like for this case we're doing.

17
00:00:58,950 --> 00:01:00,480
22 says requests felt.

18
00:01:00,750 --> 00:01:02,730
Let's try a port like 10000.

19
00:01:04,260 --> 00:01:09,450
As you can see, it's taking a little bit longer in some cases to load and give us an answer.

20
00:01:09,450 --> 00:01:11,370
So I'm going to try Port 80.

21
00:01:12,390 --> 00:01:14,070
That's actually localhost for this one.

22
00:01:14,490 --> 00:01:20,460
We're going to try localhost Port 80 that comes back and says, hey, you have access to localhost for

23
00:01:20,460 --> 00:01:22,170
that proves that there isn't a SRF here.

24
00:01:22,470 --> 00:01:24,810
We are pretty much accessing a local network.

25
00:01:25,260 --> 00:01:27,660
So I'm going to try the same thing with the IP address.

26
00:01:28,230 --> 00:01:33,960
So it's you know, you will see that there are some sort of a planet SRF with some restrictions and

27
00:01:33,960 --> 00:01:37,500
we need to do a bypass, in which case we were able to do a local host.

28
00:01:37,980 --> 00:01:40,770
Now we're going to try another port on port.

29
00:01:41,410 --> 00:01:46,830
We're going to try another port on localhost that comes back and says requests felt fairly quickly.

30
00:01:47,280 --> 00:01:51,380
Now let's try a port and the same thing and so on.

31
00:01:51,390 --> 00:01:56,010
So that's the point of this, as you want to scan as many different ports as you can to kind of prove

32
00:01:56,010 --> 00:02:03,480
that this is a sort of has access to some sort of an internal network which allows you to enter to either

33
00:02:03,480 --> 00:02:07,140
enumerate the space that they're in the local private network.

34
00:02:07,350 --> 00:02:12,840
And you can also check for the open ports that may be available to play around with it.

35
00:02:13,620 --> 00:02:15,800
Always observe the responses.

36
00:02:15,840 --> 00:02:17,640
It may not be verbose in some cases.

37
00:02:17,640 --> 00:02:22,560
You may actually have the issue of the website taking way too long to respond.

38
00:02:22,860 --> 00:02:25,590
In that case, you know that that port is not open to containment.

39
00:02:25,590 --> 00:02:30,690
If a response comes back very quickly like this one, we know that we have access to it versus giving

40
00:02:30,690 --> 00:02:33,090
it something that doesn't exist at all.

41
00:02:33,120 --> 00:02:36,780
So for this instance, I would giving it a little bit of a different IP address.

42
00:02:37,080 --> 00:02:42,650
It takes a little bit longer than something that is available and comes back fairly quickly.

43
00:02:42,930 --> 00:02:48,390
So, again, I want to make sure you take this away from this example that blunt assessors are very

44
00:02:48,390 --> 00:02:48,840
tricky.

45
00:02:49,140 --> 00:02:54,000
You just have to play around and understand how they work and then make sure that you are paying attention

46
00:02:54,000 --> 00:03:00,600
to how long it takes to load each resource and kind of look at those weird behaviors.