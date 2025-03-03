Analysis of lab: http://idor.naham.sec:8081/

![[Screenshot From 2025-03-03 15-51-35.png]]

if we click update, nothing happens .
but if we refresh the page 

we get these Two get req:
![[Pasted image 20250303155319.png]]

if you look at  http://idor.naham.sec:8081/settings/12   this req,  there is an id 12.
send this req from Proxy to repeater.

just change the id from 12 to : 1 

![[Screenshot From 2025-03-03 15-55-02.png]]
notice that the user details changed in response,
i.e for id : 12 - username -> ryanc1
for id : 1 - username -> johna1   (as shown in ss)
for id : 2 - username ->zoeyw1   

that means we are able to get the details of other users as well, just by changing the id in the req parameter.

hence resulting in IDOR


PS:  for above idor  we can also use an intruder attack to find all the possible id's using bruteforcer payload type. as shown in below ss..
![[Pasted image 20250303160323.png]]
![[Screenshot From 2025-03-03 16-02-29.png]]

---

1
00:00:00,210 --> 00:00:05,040
Now, that's the kind of example, again, I'm going to right click, bring up, inspect, go to network,

2
00:00:05,050 --> 00:00:06,720
you can also use purposefully if you like.

3
00:00:06,960 --> 00:00:11,690
Well, just to keep this simple and easy, I'm just going to use our dev tools and chrome right here.

4
00:00:11,700 --> 00:00:14,790
We are in a place where it allows us to update our user settings.

5
00:00:14,790 --> 00:00:20,190
For this example, the name is Ryan C. Ryan Cunningham, 82.

6
00:00:20,190 --> 00:00:23,550
I think now some random numbers and we push update.

7
00:00:23,820 --> 00:00:26,170
So this allows us to update this function.

8
00:00:26,170 --> 00:00:28,690
Doesn't do much, but there is something else you can look for.

9
00:00:28,710 --> 00:00:29,940
So we're going to refresh the page.

10
00:00:30,660 --> 00:00:32,460
As you can see, we're making some calls.

11
00:00:32,460 --> 00:00:35,310
But down right here, there is a settings slash twelve.

12
00:00:35,820 --> 00:00:40,370
If you double click on it, it shows us the exact information to preview the screen.

13
00:00:40,410 --> 00:00:45,810
This is, you know, look pretty nice here a little bit, but it's giving us a JSON format for that

14
00:00:45,810 --> 00:00:46,560
exact data.

15
00:00:46,770 --> 00:00:49,260
As you can see right here, there's an eighty twelve now.

16
00:00:49,260 --> 00:00:50,910
We're going to change that ID by one.

17
00:00:50,910 --> 00:00:52,440
So we go to eleven now.

18
00:00:52,440 --> 00:00:56,010
We can say there is Michelle, there is an email, there's a phone number.

19
00:00:56,280 --> 00:00:57,060
We'll go to ten.

20
00:00:57,660 --> 00:01:02,370
Another user, John C, there is your email address and phone number as well.

21
00:01:02,670 --> 00:01:06,150
And this example, we just fetched you already twelve within settings.

22
00:01:06,450 --> 00:01:10,260
But there are times that we can update and add or remove data.

23
00:01:10,440 --> 00:01:15,390
We'll do more of this later during our lab where we can explore more ideas, where we can actually modify

24
00:01:15,390 --> 00:01:16,170
into the data.

25
00:01:16,350 --> 00:01:21,600
So having our network tab or Bergström running in the background as we check for things is a great way

26
00:01:21,600 --> 00:01:25,770
to see all these different API calls and how the application may fetch data.

27
00:01:25,800 --> 00:01:31,020
I always recommend having it open and also make sure to kind of play with these integers and see if

28
00:01:31,020 --> 00:01:32,990
you can identify other vulnerabilities.

29
00:01:33,210 --> 00:01:37,380
So while you're browsing the website or getting familiar with it, I highly recommend looking at all

30
00:01:37,380 --> 00:01:41,280
the background calls that it may be making and seeing how it fetches data.

31
00:01:41,280 --> 00:01:46,770
And if you can swap out your ID with another user ID and hopefully your secondary account to make sure

32
00:01:46,770 --> 00:01:47,970
you're not missing any IDRs.