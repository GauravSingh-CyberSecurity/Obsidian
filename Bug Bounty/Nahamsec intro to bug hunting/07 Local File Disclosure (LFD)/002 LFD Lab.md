Analysis of LFD lab:-    http://lfi.naham.sec:8081/

to find the Local file disclosure like    /etc/passwd.

lets go to lab and start the analysis.


the page only have cat photos and gif that is (i.e it allows more than single format of file, that is jpg, gif), hence we can rule out that the file format( file extension) might have been hard coded  i.e that we are in a hardcoded directory like .png or .jpeg and need to escape out of it using  ? , so we dont need to try and exit out of a file format (using    ? )
![[Screenshot From 2025-03-03 16-48-29.png]]




What are we going to do is we're going to look at the source of this page and we can see that here there
is an energy source that's relying on the image endpoint with the file parameter and it points to a

JPEG image.
![[Screenshot From 2025-03-03 17-00-38.png]]




we are going to type and to fetch the file for



it etc/passwd by giving it the root folder, /etc folder and the password file   /passwd.

/etc/passwd   as shown in below ss



![[Screenshot From 2025-03-03 17-05-32.png]]
It comes back and says file not found.


This could be for multiple reasons.


One, it could be because we are either in a hard coded directory, which means that we have to escape


out of it with a directory traversal or we have to escape the format file for whatever it's hardcoded.


So in other words, if it's expecting a JPEG at the end, you have to escape out of it.


But based on the view source that we saw, it looks like it ignores the extension because it takes both gif and jpg.

So we can kind of assume that it's not a hard coding any extensions, but there is something we've got

==to figure out in order to get to the file that we want to fetch.==

==So for this case, as I mentioned, we expect it to be a directory traversal.==



==So we're going to traverse as many directly as we can.==
![[Screenshot From 2025-03-03 17-17-03.png]]

==Again, if you do extra directories, it doesn't matter.==
In Linux, you can add as many as you want and you're going to say etc/passwd or password.

And that is going to bring on the file that we asked for, which is a local file on this server that's
not on the website's root directory.

![[Screenshot From 2025-03-03 17-17-29.png]]


PS: Burp repeater view
![[Pasted image 20250303171845.png]]

Burp repeater Request
```
GET /image?file=/../../../../../../../../../../../../../../../../../../../../etc/passwd HTTP/1.1
Host: lfi.naham.sec:8081
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Priority: u=4

```

Burp repeater Response
```
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Mon, 03 Mar 2025 11:46:54 GMT
Content-Type: text/plain;charset=UTF-8
Connection: keep-alive
Content-Length: 1289

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
mysql:x:101:101:MySQL Server,,,:/nonexistent:/bin/false
messagebus:x:102:102::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:103:103:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
systemd-network:x:104:105:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:105:106:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin

```

---
==**Imp explaination of LFD :-**== 



1
00:00:00,330 --> 00:00:04,770
That's the kind of example in this case we can see that this website is showing us some cat photos,

2
00:00:05,130 --> 00:00:10,380
but unfortunately there is no other links or any other functionality available to us.

3
00:00:10,500 --> 00:00:12,770
So, in other words, it's not always easy.

4
00:00:12,780 --> 00:00:15,670
It's not obvious when it comes to looking for vulnerabilities.

5
00:00:15,750 --> 00:00:20,130
What are we going to do is we're going to look at the source of this page and we can see that here there

6
00:00:20,130 --> 00:00:26,040
is an energy source that's relying on the image endpoint with the file parameter and it points to a

7
00:00:26,040 --> 00:00:26,880
JPEG image.

8
00:00:26,940 --> 00:00:27,990
So we're going to click on this.

9
00:00:28,270 --> 00:00:35,050
As expected, it opened up our file CAT five, and we can try and do a cat for to see if this works.

10
00:00:35,130 --> 00:00:38,780
There's no false ground we can look here, says Cat four as a gif.

11
00:00:39,180 --> 00:00:45,870
So I'm going to change this and it loads it for us so we can see that it's working based on our slides.

12
00:00:45,880 --> 00:00:49,260
We talked about checking and seeing if this is actually a vulnerability.

13
00:00:49,770 --> 00:00:54,390
So we're going to give it a dot slash, meaning that we want to look for the current folder and get

14
00:00:54,390 --> 00:00:56,940
the cat for dot gif.

15
00:00:57,180 --> 00:01:06,740
So now we're going to go back to our training site and we are going to type and to fetch the file for

16
00:01:06,740 --> 00:01:14,640
it etek password by giving it the root folder, ETSI or ETEK folder and the password file.

17
00:01:14,940 --> 00:01:16,770
It comes back and says file not found.

18
00:01:17,220 --> 00:01:18,810
This could be for multiple reasons.

19
00:01:19,050 --> 00:01:24,930
One, it could be because we are either in a hard coded directory, which means that we have to escape

20
00:01:24,930 --> 00:01:31,040
out of it with a directory traversal or we have to escape the format file for whatever it's hardcoded.

21
00:01:31,090 --> 00:01:35,310
So in other words, if it's expecting a JPEG at the end, you have to escape out of it.

22
00:01:35,310 --> 00:01:40,650
But based on the view source that we saw, it looks like it ignores the extension because it takes both

23
00:01:40,800 --> 00:01:42,510
gif and jpg.

24
00:01:42,780 --> 00:01:47,970
So we can kind of assume that it's not a hard coding any extensions, but there is something we've got

25
00:01:47,970 --> 00:01:51,510
to figure out in order to get to the file that we want to fetch.

26
00:01:51,570 --> 00:01:56,460
So for this case, as I mentioned, we expect it to be a directory traversal.

27
00:01:56,460 --> 00:01:58,660
So we're going to traverse as many directly as we can.

28
00:01:59,090 --> 00:02:01,380
Again, if you do extra directories, it doesn't matter.

29
00:02:01,380 --> 00:02:05,990
In Linux, you can add as many as you want and you're going to say ETSI password or password.

30
00:02:06,000 --> 00:02:11,910
And that is going to bring on the file that we asked for, which is a local file on this server that's

31
00:02:11,910 --> 00:02:13,650
not on the website's root directory.