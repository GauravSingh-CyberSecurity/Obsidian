Aquatone repo: [GitHub - michenriksen/aquatone: A Tool for Domain Flyovers](https://github.com/michenriksen/aquatone)
**Aquatone Installation Tutorial** 

The next tool we’re going to install is **Aquatone**, which is a very popular tool among bug bounty hunters. This tool helps collect information on assets, including screenshots, and it also grabs HTTP headers, allowing us to enumerate different components sitting on these assets.

### Installation Steps:

1. **Download Aquatone**  
    First, let’s download Aquatone. You can grab the executable for it from the official repository. I recommend downloading version 1.4.3, which also has a tutorial available in the GitHub repository.


```
C:\home\kali\Tools> ls
aquatone_linux_amd64_1.7.0.zip  Sublist3r

C:\home\kali\Tools> unzip aquatone*.zip
Archive:  aquatone_linux_amd64_1.7.0.zip
  inflating: aquatone                
  inflating: README.md               
  inflating: LICENSE.txt   
            
C:\home\kali\Tools> ls
aquatone  aquatone_linux_amd64_1.7.0.zip  LICENSE.txt  README.md  Sublist3r
C:\home\kali\Tools> sudo mv aquatone /usr/local/bin/
C:\home\kali\Tools> aquatone --help
```

### Conclusion

At this point, Aquatone should be ready to use. In this tutorial, we’ve covered the installation of Aquatone and how to set it up properly with Chromium. In the next steps, we'll use Aquatone for recon tasks. But for now, we’ve successfully installed the tool and are ready to proceed.


---
# Transcript :
1
00:00:00,150 --> 00:00:05,190
The next thing we're going to install as Aquata on this as a very popular show amongst bug bounty hunters.

2
00:00:05,520 --> 00:00:12,810
This allows us to collect some data on our assets, including screenshots, and also grabs the HTP header,

3
00:00:13,020 --> 00:00:17,310
or we can enumerate what's sitting on these different assets.

4
00:00:17,340 --> 00:00:18,560
So let's go out and download it.

5
00:00:18,990 --> 00:00:21,610
So we're going to go ahead and install this inside.

6
00:00:21,630 --> 00:00:22,980
This should be fairly easy.

7
00:00:23,550 --> 00:00:28,170
We're just going to have to pull the source and give it a try.

8
00:00:28,760 --> 00:00:33,330
The first thing we're going to do, the entire Accattone, is want to download an executable for it.

9
00:00:33,360 --> 00:00:37,830
I'm going to go ahead and download the one point four three version has also one of the tutorials that's

10
00:00:37,830 --> 00:00:39,420
on the GitHub repository for it.

11
00:00:39,760 --> 00:00:47,250
We're going to end up this, but we may have to install on quickly prototype and install unzip to make

12
00:00:47,250 --> 00:00:48,740
sure we can actually unzip this file.

13
00:00:48,750 --> 00:00:55,110
And once that's done it, we're going to go ahead and unzip our file or type and unzip and extract the

14
00:00:55,110 --> 00:00:55,890
contents of it.

15
00:00:56,250 --> 00:00:59,100
And now that we have it, we have the AQUATINTED binary here.

16
00:00:59,490 --> 00:01:03,990
And if we execute it, it's going to come back and say in Stockholm.

17
00:01:04,260 --> 00:01:05,140
And that's another thing.

18
00:01:05,140 --> 00:01:06,350
That's one of the requirements.

19
00:01:06,360 --> 00:01:09,930
It also is shown in the repository for it.

20
00:01:09,930 --> 00:01:13,950
And all you want to do is type in SNOP if you have it installed, highly recommend having stock should

21
00:01:13,950 --> 00:01:17,610
be already on Boonchu, especially if you use digital ocean.

22
00:01:17,880 --> 00:01:21,570
We're going to just type in Insaaf chromium or you can do chrome, whatever.

23
00:01:22,500 --> 00:01:24,090
It's not installed chromium.

24
00:01:29,880 --> 00:01:31,860
It's going to take a second and then an install.

25
00:01:35,880 --> 00:01:41,730
And then once that is installed, we want to tell Aquitaine, hey, this is where the chromium version

26
00:01:41,730 --> 00:01:43,110
that I want to use is installed.

27
00:01:46,280 --> 00:01:52,490
So let's try it again, type in Accattone and I highly recommend actually moving awkward time to your

28
00:01:52,490 --> 00:01:52,930
Benfold.

29
00:01:53,060 --> 00:01:58,180
So are we going to do is we're going to move this into our executables.

30
00:01:58,180 --> 00:02:00,860
So we're going to do move actually comput.

31
00:02:00,860 --> 00:02:04,260
If you prefer to do that, we're just going to put it in user local.

32
00:02:04,490 --> 00:02:08,640
Then I just go back and type in what I want to move Aquitania.

33
00:02:08,660 --> 00:02:10,430
We're going to move it to this folder.

34
00:02:10,440 --> 00:02:15,230
So now every time, no matter where we are, if we're typing Accattone, it's going to call for it and

35
00:02:15,230 --> 00:02:20,450
want to make sure that when we use it, we tell it, hey, when you run Accattone, I want you to know

36
00:02:20,450 --> 00:02:26,810
that the chrome path, which we can also see here, which is this chrome path, you want to make sure

37
00:02:26,810 --> 00:02:27,380
we define it.

38
00:02:27,380 --> 00:02:30,170
So we're going to type in Aquata on Chrome path.

39
00:02:30,380 --> 00:02:35,810
And since we installed in SNOP, it's going to be on there's not been chromium and now we're not going

40
00:02:35,810 --> 00:02:40,580
to have any issues and it's running later on down the course, we're going to actually use Aqua trying

41
00:02:40,580 --> 00:02:45,680
to do some recon, but for now is going to skip that and revisit it once we have installed all of our

42
00:02:45,680 --> 00:02:46,040
tools.