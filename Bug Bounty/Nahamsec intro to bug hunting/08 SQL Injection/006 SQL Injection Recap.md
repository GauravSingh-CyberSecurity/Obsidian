

So to recap, SQL injection is very, very important to look for abnormalities when you're sending a request. SQL injection could be very, very tedious.

Ton of good tools out there that do it, but it really comes down to actually understanding how it works.

The way I look at a SQL injection is always reminding myself that I'm somewhere in a SQL query. We don't know where—we have to figure it out.

And that's kind of obvious when it comes down to the application or the part of the application that you're targeting.

So, for example, if you're updating something and you have a SQL injection, more than likely you are in an update statement where you have to figure out how to put your next query in it and how to end that previous one.

If you are just viewing something, like you're going to an article with `id=`, and that's fetching data, you know you're in a SELECT statement, and you want to break out of that current query and add your own query to it.

When it comes down to blind SQL injection, it could get very, very tricky.

You have to understand exactly where you are. With regular SQL injection, it gives you a hint and tells you, “Hey, your SQL query in UPDATE has this error.”

But you don't have this luxury when it comes down to blind SQL injection.

So you want to make sure you understand where you are, how to end it, and what you are going to abuse.

What functionality are you going to abuse? Is it a sleep function? Is it a benchmark?

You need to understand what the backend is to determine if you are making it a time-based or boolean-based attack—where it tells you if the statement you sent is true or false.

Take some time, go back and review all these slides from this chapter.

Make sure you understand how an injection works, and spend some time with different labs, including the ones included in this course, and make sure you get very familiar with it.

SQL injection could be very, very lucrative but hard to look for.

You have to pay attention to everything happening around the application and know where to look for it.

Places that I like to look for SQL injection are anywhere I see an ID—some sort of numerical ID that says, “Hey, I want you to fetch this data.”

Not really in an API—I don’t look for those. Sometimes, REST APIs are vulnerable, but in general, when you see a question mark followed by some parameter assigned to a number, you can try SQL injection there.

If you see a POST request without changing data that says `id="1"`, you want to go ahead and check if that is also vulnerable to injection.

So again, don't be afraid of putting a quotation mark here and there.

Look for any error that comes back. If it hints at SQL injection, try to exploit it.

If not, just move on to the next vulnerability type.






---
1
00:00:00,300 --> 00:00:05,430
So to recap, SQL injection is very, very important to look for abnormalities when you're sending a

2
00:00:05,430 --> 00:00:08,190
request, SQL injection could be very, very tedious.

3
00:00:08,580 --> 00:00:12,810
Ton of good tools out there that does it, but it really comes down to actually understanding how it

4
00:00:12,810 --> 00:00:13,140
works.

5
00:00:13,350 --> 00:00:18,980
The way I look at a single injection is always reminding myself that I'm somewhere and a sequel query.

6
00:00:19,020 --> 00:00:20,910
We don't know where we have to figure it out.

7
00:00:20,910 --> 00:00:25,830
And that's kind of obvious when it comes down to the application or the part of the application that

8
00:00:25,830 --> 00:00:26,410
you're talking.

9
00:00:26,430 --> 00:00:31,380
So, for example, if you're updating something and you have a sequel injection, more than likely you

10
00:00:31,380 --> 00:00:36,270
are in an updated statement where you have to figure out how to put your next query in it and how to

11
00:00:36,270 --> 00:00:37,290
end that previous one.

12
00:00:37,500 --> 00:00:42,990
If you are just viewing something like you're going to article about it equal to something that's fetching

13
00:00:42,990 --> 00:00:48,000
data, you know, you're in a select and you want to break out of that Krenzler query and add your own

14
00:00:48,000 --> 00:00:48,780
query to it.

15
00:00:49,080 --> 00:00:52,640
When it comes down to blind SQL injection could get very, very tricky.

16
00:00:52,650 --> 00:00:57,350
You have to understand exactly where you are with regular simple injection that gives your hand and

17
00:00:57,350 --> 00:01:02,520
tells you, hey, your secret query and update has this error, but you don't have this luxury when

18
00:01:02,520 --> 00:01:04,320
it comes out to buy a single injection.

19
00:01:04,480 --> 00:01:08,880
So you want to make sure you understand where you are, how to end it, and what are you going to abuse?

20
00:01:08,880 --> 00:01:10,310
What functionality you going to abuse?

21
00:01:10,320 --> 00:01:11,070
Is that a sleep?

22
00:01:11,280 --> 00:01:17,640
Is it a benchmark with the backend is to make sure you make it a time based or a boolean based attack

23
00:01:17,820 --> 00:01:22,650
where it tells you if the statement that you have sent it is true or false, take some time, go back

24
00:01:22,650 --> 00:01:28,680
and review all these slides from this chapter, make sure you understand how a injection works and spend

25
00:01:28,690 --> 00:01:34,380
some time with different labs, including ones included in this course, and make sure you get very

26
00:01:34,380 --> 00:01:35,220
familiar with it.

27
00:01:35,220 --> 00:01:38,520
SQL injection could be very, very lucrative, but just hard to look for.

28
00:01:38,520 --> 00:01:42,690
And you have to just pay attention to everything that's happening around the application and knowing

29
00:01:42,690 --> 00:01:43,600
where to look for it.

30
00:01:44,370 --> 00:01:49,410
So places that I like to look for it is anywhere that I see an ID, some sort of ID.

31
00:01:49,410 --> 00:01:52,980
That's a numerical thing that says, hey, I want you to fetch this data.

32
00:01:53,190 --> 00:01:54,300
Not really in an API.

33
00:01:54,300 --> 00:01:55,040
I don't look for those.

34
00:01:55,110 --> 00:01:56,430
There are sometimes valid.

35
00:01:56,430 --> 00:02:01,890
You can see the rest API, but in other ways, when you see a question mark, some parameter looking

36
00:02:01,890 --> 00:02:04,860
to a number, you can try SQL injection there.

37
00:02:04,980 --> 00:02:09,450
If you see a post request without changing data, it says ID quotation mark one.

38
00:02:09,630 --> 00:02:13,650
You want to go ahead and look and see if that is also vulnerable to conjecture.

39
00:02:14,040 --> 00:02:17,280
So again, don't be afraid of putting a quotation mark here and there.

40
00:02:17,550 --> 00:02:21,960
Look for any error that comes back if it hints for a sequel injection and just try and exploit it.

41
00:02:22,290 --> 00:02:24,510
If not, just move on to the next vulnerability type.