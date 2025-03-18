

Earlier, I talked about the crt.sh and how we can actually automate this. This is a simple way of automating the crt.sh.

All I'm doing here is making a command. I'm actually switching resources using a command and doing a silent version of it. Right here is where we're going to put our domain name.

For example, when using gm.com, right here, gm.com — using a tool called `jq` — I look for the "name" value. We're going to clean this up and make sure the domains are unique so we don't have any duplications.

Here’s the `curl` command you can use to fetch data from **crt.sh** and parse the `"name_value"` fields using **jq**, ensuring unique subdomains (removing duplicates):

bash

CopyEdit

`curl -s "https://crt.sh/?q=%.gm.com&output=json" | jq -r '.[].name_value' | sort -u`

---

### Explanation:

✅ `curl -s "https://crt.sh/?q=%.gm.com&output=json"`

- `-s`: silent mode (no progress meter)
- `%.gm.com`: wildcard search for all subdomains of `gm.com`
- `output=json`: response in JSON format

✅ `| jq -r '.[].name_value'`

- Extracts the `name_value` field from each JSON object
- `-r`: outputs raw strings instead of JSON quotes

✅ `| sort -u`

- Sorts the output and removes duplicate domain names

==Again, this is something that I’ve learned using Bash. If you’re not familiar with it, I highly recommend learning it. You can also do this with Python, Ruby, Go, or any other programming language you use.==

Typing this will give us a list of domains that are available on gm.com. As it comes back, it gives us a ton of different results. We're going to just go ahead and type in another pipe.

What I’m doing with the pipe here — if you’re not familiar with Bash — is taking the results of this command and feeding it into the next one. Then, using another pipe, we're feeding it into another command, and the results of all this get fed to you.

We're also going to feed the results of all of this into another tool that we discussed when setting up our lab, which is `httpx`. This tool will tell us how many of these subdomains are actually accessible through HTTP or HTTPS.

`-c` is the concurrency flag, and we're setting it to 50. This is going to run every single subdomain in that list with `httpx` and tell us which ones are available through HTTPS, HTTP, or both.

So, in this case, you can hit them both ways as protocols, but we can click and open them up for further testing. Now that we know these are done, we can also run another way and go back to the same command.

Not only are we fetching data from Cert.sh, but we're also making it clean by removing duplicates. This tool that we talked about in our setup tells us which sites are open and available.

We can also take screenshots by typing in `aquatone`, and this will give us a list of all the available domains. It will also give us screenshots. For the purpose of this tutorial and to save time, I'm not going to actually run this command and show the results.

Once you run this, I highly recommend creating a folder called `gm.com`, for example, on your machine and then running this. Once you run this, it starts doing its thing and creates folders for screenshots, HTTPS results, HTTP results, or whatever came back as a response from each server.

It will also give you a report that you can look at — all these different assets together with a list of the subdomains and their screenshots. You can do this as a part of your recon to get an overview of every site that’s available and what they look like.

Based on the website’s look or whatever the screenshot is, you can decide which targets you want to go after. Again, this is just an example of how you can chain a ton of different commands to get the results.

Run it one more time, give it a sec, and see if it created those different folders. You can see the headers — this is where it would store the original report with all the screenshots and the subdomains.

The screenshots folder is where you will have the images. Once that's done, you can go to the original folder — there will be a file there. You can open it up on your local machine and see all the images in a nicely written report, and then decide what you want to hack on.




---

# Transcript: 

1
00:00:00,120 --> 00:00:03,390
Earlier, I talked about sort of the siege and how we can actually automate this.

2
00:00:03,680 --> 00:00:05,980
This is a simple way of automating sort of the stage.

3
00:00:06,030 --> 00:00:08,220
All I'm doing here is I'm making a command.

4
00:00:08,860 --> 00:00:13,440
I'm actually switching resources, using a command, doing a silence version of it.

5
00:00:13,680 --> 00:00:16,770
And right here is where we're going to put our domain name.

6
00:00:18,870 --> 00:00:26,100
So, for example, when the GM dotcom 125 right here, Jim Dotcom, using a tool called JQ Jacobs,

7
00:00:26,100 --> 00:00:30,890
I look for the name value and we're going to give this to set of cleaning up and using sort of you.

8
00:00:31,170 --> 00:00:36,520
We're going to be able to make sure that they're sort of in a unique way so we don't have any duplications.

9
00:00:36,780 --> 00:00:42,030
Again, this is something that I've learned using Basche, if you're not familiar with my highly recommend

10
00:00:42,030 --> 00:00:42,520
doing it.

11
00:00:42,540 --> 00:00:47,690
You can also do it with Python, Ruby, go whatever other programming language you use, typing this

12
00:00:47,700 --> 00:00:52,470
and you come back and give us a list of domains that are available on GM dotcom.

13
00:00:54,110 --> 00:00:56,990
As it comes back, it gives us a ton of different results.

14
00:00:57,200 --> 00:00:59,830
We're going to just go ahead and type in another pipe.

15
00:00:59,840 --> 00:01:03,590
So what I'm doing with the pipe here, if you're not familiar with Bash, is we're going to take the

16
00:01:03,590 --> 00:01:09,380
results of this command feed into this one and then using another pipe, we're feeding into this one

17
00:01:09,620 --> 00:01:12,260
and then the results of all of this gets fed to you.

18
00:01:12,590 --> 00:01:17,770
We're also going to feed the results of all of this right here into another tool that we discussed and

19
00:01:17,780 --> 00:01:19,530
are setting up our lab, which is HTP.

20
00:01:19,530 --> 00:01:26,210
You probe this tool will tell us how many of these subdomains are actually accessible through HTP or

21
00:01:26,220 --> 00:01:26,990
ETPs.

22
00:01:27,290 --> 00:01:30,010
Dachsie is the concurrency we're going to at 50.

23
00:01:30,390 --> 00:01:35,240
This is going to run every single supplement in that list with HTP probe and it's going to tell us which

24
00:01:35,240 --> 00:01:40,110
one is available through ETPs, which ones are available to HTP or both.

25
00:01:40,130 --> 00:01:45,710
So in this case, you can hit em in both ways as prototypes, but we can click it and open it up for

26
00:01:45,710 --> 00:01:47,740
us and we can do further testing.

27
00:01:48,170 --> 00:01:49,230
Now we know these are done.

28
00:01:49,250 --> 00:01:52,520
We can also do it another way and go back to the same command.

29
00:01:52,790 --> 00:01:59,170
Not only we are fetching data from certain S.H. We're also making it clean by doing this command, feeding

30
00:01:59,180 --> 00:02:02,210
it to you to make sure there's no duplicate domains in there.

31
00:02:02,460 --> 00:02:07,670
This tool that we have talked about in our setup tells us which sites are open, which are available.

32
00:02:07,910 --> 00:02:13,880
We can also do screenshots by typing an Accattone, and this will give us a list of all the available

33
00:02:13,880 --> 00:02:14,540
domains.

34
00:02:14,750 --> 00:02:18,290
And also it will give us screenshots for the purpose of this tutorial.

35
00:02:18,440 --> 00:02:22,700
And because of saving time, I'm not going to actually run this command and show the results.

36
00:02:22,910 --> 00:02:25,670
But once you run this, I was going to make a folder.

37
00:02:25,670 --> 00:02:30,770
So I highly recommend going to a folder called GM dot com, for example, in your machine and then running

38
00:02:30,770 --> 00:02:31,100
this.

39
00:02:31,340 --> 00:02:38,090
And once you run this, I starts doing its thing and it's going to have a folder for screenshots, https

40
00:02:38,870 --> 00:02:43,220
HTP results or the Hellersdorf came back for the response on each server.

41
00:02:43,460 --> 00:02:48,820
And it's also going to give you a report that you can look at all these different assets together with

42
00:02:48,830 --> 00:02:51,830
a list of the subdomains and whatever the screenshot looks like.

43
00:02:52,160 --> 00:02:57,890
So you can do this as a part of your recon to get a overview of every site that's available and what

44
00:02:57,890 --> 00:02:58,520
they look like.

45
00:02:58,520 --> 00:03:04,580
And based on the websites, looks at whatever the screenshot is, you can decide what targets you want

46
00:03:04,580 --> 00:03:05,540
to go after.

47
00:03:05,600 --> 00:03:13,100
So, again, this is just an example of how you can add on a ton of different commands for it to come

48
00:03:13,100 --> 00:03:17,870
back and show you the results right on this one more time, give it a sec, see if it created those

49
00:03:17,870 --> 00:03:19,910
different folders that you can see the headers.

50
00:03:20,190 --> 00:03:25,980
This is where it would store the original report with all the screenshots and the subdomains and then

51
00:03:26,030 --> 00:03:28,590
screenshots is where you would have this screenshot.

52
00:03:28,610 --> 00:03:31,480
So once that done, you can just go to the original folder.

53
00:03:31,490 --> 00:03:32,840
There's going to be a file there.

54
00:03:33,030 --> 00:03:39,380
You can open it up on your local machine and you can see all the images in a very nicely written report

55
00:03:39,530 --> 00:03:41,270
and then decide what you want to hack on.