
 we're going to look at is how to use Accattone

![[Screenshot From 2025-03-26 13-10-10.png]]
```
subdoamin-found-on-target.txt | httprobe | aquatone  path-to-the-folder/where-want-to-store-target-websites-screenshots
```


after above , 
then we also use ==dnsgen tool==, it makes diffrent permutations on the dns like it will permute QA, Staging, Live (any dns that we feed to it via a wordlist)

![[Screenshot From 2025-03-26 13-15-05.png]]
```
 dnsge -w  wordlist  subdoamin-found-on-target.txt | httprobe | aquatone  path-to-the-folder/where-want-to-store-target-websites-screenshots

```


then next 
![[Screenshot From 2025-03-26 13-16-59.png]]
```
cat  subdoamin-found-on-target.txt | httprobe -c 20 | aquatone  path-to-the-folder/where-want-to-store-target-websites-screenshots
```





And once this is done, we're going to actually go ahead and look at the outputs of the Aquatone report. So we're going to do is we're going to actually run a Python3 and using Python3, we're going to run an HTTP server on Port 8000(or any other that is available)
This will allow us to ==open up the content of this folder (path-to-the-folder/where-want-to-store-target-websites-screenshots) in our browser and be able to see that HTML file for all the screenshots of the whole target domain/subdomain== 
![[Screenshot From 2025-03-26 13-22-16.png]]

this is how it looks in browser 
![[Pasted image 20250326132326.png]]
This is very helpful when you have hundreds of subdomains, but you want to get a overview of what this company looks like



---


1
00:00:00,180 --> 00:00:05,190
The last thing we're going to look at is how to use Accattone, what we're going to do here is we have

2
00:00:05,190 --> 00:00:07,260
already done our asset discovery.

3
00:00:07,470 --> 00:00:10,470
We wrote all of that to Nahoum Secombe, not Texte.

4
00:00:10,770 --> 00:00:13,090
But are we going to do is we're going to feed it to agitprop.

5
00:00:13,230 --> 00:00:16,740
This is to see which ones of these websites are available.

6
00:00:16,980 --> 00:00:18,210
And we're going to later on.

7
00:00:18,210 --> 00:00:19,230
Senator Aquitaine.

8
00:00:19,410 --> 00:00:23,880
But just to make things a little bit more interesting, I'm also going to use DNS, John, and this

9
00:00:23,880 --> 00:00:27,210
is going to do is it's going to generate different permutations.

10
00:00:27,450 --> 00:00:34,770
I'm going to give it the word this word list and the following is going to be our new home sexto dot

11
00:00:34,770 --> 00:00:35,440
com file.

12
00:00:35,440 --> 00:00:37,610
So I'm just going to go here and type in the home next door.

13
00:00:37,850 --> 00:00:40,420
This isn't going to work because they're worthless, isn't there?

14
00:00:40,740 --> 00:00:46,560
I'm going to quickly make it worthless to when I call it Deve Kuai and stage and we're going to run

15
00:00:46,560 --> 00:00:55,290
this command all at once just to create a bigger list of targets and htp over it and then feed it to

16
00:00:55,290 --> 00:00:55,890
Aquitania.

17
00:00:55,920 --> 00:01:02,640
So let's do this really quickly when I give it some concurrency with you and I see now it's running

18
00:01:02,640 --> 00:01:08,570
this Accattone on the output of HTP probe based on whatever DNS change creates for us.

19
00:01:08,580 --> 00:01:13,020
And right now we can see that it's creating some stuff, it's feeding in and is doing screenshots as

20
00:01:13,020 --> 00:01:16,650
done the status code for us.

21
00:01:16,860 --> 00:01:21,090
And if we do, unless we can see that these have been created, there are the headers right here for

22
00:01:21,090 --> 00:01:22,050
each domain.

23
00:01:22,590 --> 00:01:24,510
There are the HTML outputs.

24
00:01:25,590 --> 00:01:27,360
And we also have screenshots.

25
00:01:28,590 --> 00:01:34,530
And I think it took screenshots of marketing in the home store 20-20 Dev and this one as well could

26
00:01:34,530 --> 00:01:35,880
also just do it without.

27
00:01:35,890 --> 00:01:38,430
So if you're paranoid, I then give us enough data.

28
00:01:38,640 --> 00:01:43,440
Dinnerstein And you know, combining different commands may break some stuff so we can just remove this

29
00:01:43,440 --> 00:01:49,200
and just do a cut and that I do additional screenshots.

30
00:01:49,250 --> 00:01:52,820
Looks like we missed we missed this stock one and maybe the shops.

31
00:01:52,830 --> 00:01:54,120
It's going to do a few more.

32
00:01:54,330 --> 00:01:57,390
It's going to read all of them into the same file and folder.

33
00:01:57,570 --> 00:02:03,750
And once this is done, we're going to actually go ahead and look at the outputs of the quarterly report.

34
00:02:03,900 --> 00:02:08,550
So we're going to do is we're going to actually run a Python three and using Python three, we're going

35
00:02:08,550 --> 00:02:11,640
to run an HGP server on Port eight thousand.

36
00:02:11,790 --> 00:02:17,430
This will allow us to open up the content of this folder in our browser and be able to see that original

37
00:02:17,430 --> 00:02:18,930
file that I pointed out early on.

38
00:02:21,000 --> 00:02:25,620
We're going to go to our browser and we're going to navigate two or eight thousand.

39
00:02:25,770 --> 00:02:28,680
This will bring up a list of all those files that we created.

40
00:02:28,980 --> 00:02:33,540
This was the file that we used as a seed for all the domains that we have found.

41
00:02:33,810 --> 00:02:36,600
But now we're going to look at Accattone report on each HTML.

42
00:02:36,820 --> 00:02:41,190
As you can see, it's grouping them each by subdomains so stocked on the home.

43
00:02:41,190 --> 00:02:43,130
So dot com there is marketing.

44
00:02:43,140 --> 00:02:43,890
This is what it looks like.

45
00:02:43,890 --> 00:02:45,090
We can click and look at it.

46
00:02:45,280 --> 00:02:49,740
This is very helpful when you have hundreds of subdomains, but you want to get a overview of what this

47
00:02:49,740 --> 00:02:53,070
company looks like so that you can see the home side wood shop.

48
00:02:53,070 --> 00:02:54,060
This is what it looks like.

49
00:02:54,300 --> 00:02:57,690
It's running Ingenix on a boon to using Bootstrap in January.

50
00:02:58,080 --> 00:03:01,890
It's also doing that for the other subdomains and domains as well.

51
00:03:01,890 --> 00:03:03,330
So you can, you know, do this with subdomains.

52
00:03:03,570 --> 00:03:06,450
You can do that with Domain's whatever list of sites you give it.

53
00:03:06,630 --> 00:03:12,360
It's going to look for and take screenshots and actually give you a really look a very cool looking

54
00:03:12,660 --> 00:03:13,050
report.

55
00:03:13,050 --> 00:03:18,900
And it's also going to show you what IPS are there, what I can it's using and so on.

56
00:03:19,200 --> 00:03:22,110
There's also a lot of other features by similarity, by host.

57
00:03:22,470 --> 00:03:24,990
It's good to have these kinds of visualisation.

58
00:03:25,140 --> 00:03:33,630
Obviously, the more domains you have, the more useful these graphs and the sorting with pages come

59
00:03:33,630 --> 00:03:34,080
in handy.