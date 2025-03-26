
dnsgen --help















---


# Transcript :

1
00:00:00,120 --> 00:00:06,180
Now, let's have a look at the so what the NSA does, as I explained earlier, it will take a wait list.

2
00:00:06,710 --> 00:00:10,530
You can either use the one that comes with it by default or you can create your own.

3
00:00:10,950 --> 00:00:12,540
It also takes a file name.

4
00:00:13,140 --> 00:00:16,920
That is where you can put all your domains that you have found.

5
00:00:17,130 --> 00:00:22,130
And it will create more permutations of those subdomains based on the list that you give it.

6
00:00:22,260 --> 00:00:26,710
And I'm going to quickly create a list for ourselves, going to call it worthless.

7
00:00:27,030 --> 00:00:33,840
I'm going to put Dev Keyway stage and those are the only three that I want to try.

8
00:00:33,870 --> 00:00:39,030
So what I'm going to do now is I'm going to do DNS Gen on the Homosex Store and I want to use the word

9
00:00:39,030 --> 00:00:40,710
this not so.

10
00:00:40,710 --> 00:00:47,130
Now what it's doing is it's putting Dev in front in the back of each of these subdomains and printing

11
00:00:47,130 --> 00:00:47,420
it out.

12
00:00:47,430 --> 00:00:50,170
But now we have to see which one of these are actually available.

13
00:00:50,610 --> 00:00:54,600
So are we're going to do is now that we know how it works, we're going to take the outputs of this

14
00:00:54,600 --> 00:00:58,900
and we want to see how many of these websites are actually available.

15
00:00:58,920 --> 00:01:02,760
So what I'm going to do here is I'm going to feed this into HTP probe, which you talked about another

16
00:01:02,760 --> 00:01:03,300
chapter.

17
00:01:03,720 --> 00:01:07,650
But what I'm going to do is I'm going to say, hey, I want you to take all this feed to this tool and

18
00:01:07,650 --> 00:01:10,170
see which ones are these are accessible with HTP.

19
00:01:10,470 --> 00:01:16,350
So I'm going to run this that comes back and says, hey, marketing is up the home store 20, 20 years

20
00:01:16,360 --> 00:01:21,210
up, and now it's going through the rest of the list and it comes back and says, again, marketing.

21
00:01:21,210 --> 00:01:29,160
But what's really cool is I found this new home store 20 20 that I could go back to our recon sources.

22
00:01:29,490 --> 00:01:33,150
I like to use the research, so I'm going to quickly pull it up really fast.

23
00:01:33,630 --> 00:01:38,940
And what we're going to do is we're going to go to another stage and we're going to look at new home

24
00:01:38,940 --> 00:01:42,940
store just to see if that particular domain is a part of it.

25
00:01:42,960 --> 00:01:46,050
So the 2020 version is there, but what else do we have here?

26
00:01:46,060 --> 00:01:47,520
We have 20, 20 dash dev.

27
00:01:47,550 --> 00:01:53,090
So let's see if the dash dev is actually a part of this list, which is and isn't.

28
00:01:53,250 --> 00:01:59,960
You can't see the w w w side as the NOM societies as shoppers index here and so is non-store 20 20.

29
00:02:00,360 --> 00:02:06,180
But as you can see, the dev version of this was not indexed in any transparency logs.

30
00:02:06,390 --> 00:02:13,560
And it's good to actually run multiple sources and see if we can extend an attack surface and find other

31
00:02:13,560 --> 00:02:15,360
versions of these sites.

32
00:02:15,570 --> 00:02:20,760
This is very common to have a particular subdomain like marketing, so twenty, twenty, whatever it's

33
00:02:20,760 --> 00:02:26,340
called, and having the dash dev or some sort of other permutations for testing purposes available to

34
00:02:26,350 --> 00:02:32,360
employees, which would also be open to the world and accessible by us, where it could lead to a vulnerability.

35
00:02:32,850 --> 00:02:40,170
So never never underestimate the power of using different permutations and using multiple tools to find

36
00:02:40,170 --> 00:02:42,750
different assets to extend your attack surface.