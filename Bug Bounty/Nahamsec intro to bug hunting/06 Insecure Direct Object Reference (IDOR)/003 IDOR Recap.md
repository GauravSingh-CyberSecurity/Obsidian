1
00:00:00,180 --> 00:00:05,310
Now we know what Idris Idris stands for, insecure, direct object reference, as we mentioned in our

2
00:00:05,310 --> 00:00:09,900
slides, the point of order is to get access to another user's data.

3
00:00:10,440 --> 00:00:13,200
In this case, you can either modify, delete or read it.

4
00:00:13,440 --> 00:00:18,630
But the point of it is to look for different ways that the API or the website is making different calls

5
00:00:18,630 --> 00:00:22,140
outside of its application or to other endpoints to fetch this data.

6
00:00:22,170 --> 00:00:27,810
So, for example, you can see an application relying on the rest API and not API is making a slash

7
00:00:27,810 --> 00:00:33,870
user user ID profile which links to which shows you the user name and the address.

8
00:00:33,990 --> 00:00:38,640
And if you change the ID, the numerical ID from one, two, three, four or five to one, two, three,

9
00:00:38,640 --> 00:00:42,480
four or five, six, for example, it might show you another user's data.

10
00:00:42,720 --> 00:00:48,630
My recommendation is to just use this website as you would regularly just have a seat open on the side

11
00:00:48,630 --> 00:00:50,030
and just observe every request.

12
00:00:50,090 --> 00:00:55,650
This Web site is sending by forwarding a one by one, you can actually look at your HGP request history

13
00:00:55,770 --> 00:00:59,610
and seeing all the different calls I've been made every time you have a load of a page.

14
00:00:59,940 --> 00:01:04,770
So, again, you want to understand how the application works, understand how it fetches user data.

15
00:01:04,950 --> 00:01:09,960
And what of those calls and how is it assigning user I.D. to each user and changing that data?

16
00:01:10,290 --> 00:01:12,120
It doesn't always have to be a user ID.

17
00:01:12,120 --> 00:01:17,220
It could be things that the object itself has an ID number and you change that and it shows you another

18
00:01:17,220 --> 00:01:17,970
user's data.

19
00:01:18,120 --> 00:01:24,120
So again, numerical ID numbers in an API call and an Ajax call are very, very common for Eider.

20
00:01:24,210 --> 00:01:28,650
And I highly recommend looking for those when testing for an application or looking for a bug.

21
00:01:28,650 --> 00:01:30,030
And while you're doing bug hunting.