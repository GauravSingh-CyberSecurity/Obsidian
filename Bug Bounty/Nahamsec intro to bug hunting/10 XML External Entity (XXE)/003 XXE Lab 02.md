


Now, this is a second example. In this case, the website allows us to upload a contact file.

Clicking on it provides us with an example file that we can download to see its format.

As you can see, the file contains multiple email addresses and different names.

We will copy this into our notepad and give it a try.

We will send this file as it is to see how the application processes it.

In other words, we are using the default example file provided by the application. Many websites provide such templates to ensure compatibility with their systems.

We will now use the template to observe how the website interacts with it.

We will save it as "contacts.xml" and navigate back to our documents.

Next, we will upload the "contacts.xml" file, which is the default template provided by the website.

Now, let's see the response.

As you can see, the upload is completed. However, the application does not display any output or return any processed files.

This suggests that the XML is being processed in the backend, but we do not receive a direct response—indicating a potential blind XXE (XML External Entity) vulnerability.

Now that we have confirmed the vulnerability and observed that it reaches out to our remote server using Burp Collaborator, we will proceed with an external DTD (Document Type Definition) attack.

I am currently hosting this DTD file on my private server.

Here's what happens:

1. We retrieve the contents of `/etc/passwd` using the `file://` scheme.
2. We store this content in a variable named "data."
3. The contents of `/etc/passwd` are then Base64-encoded.
4. Finally, the encoded data is exfiltrated to our remote server.

Encoding the file in Base64 ensures that we capture the entire content instead of just the first few lines. This also prevents the application from breaking the content due to newline characters.

Now, let's modify our `contacts.xml` file.

First, we replace the Burp Collaborator link with our private server's URL, which references the external DTD file.

Next, we define XML entities that reference the external DTD.

We set up two key entities:

- `param1`, which references the external entity.
- `remote`, which points to our remote DTD.

We then ensure that the external DTD file properly executes system calls.

To accomplish this, we append an ampersand (`&`) followed by a semicolon (`;`) to invoke the necessary functions.

Now, we save the modified `contacts.xml` file and proceed to upload it.

Before submitting the file, we start an HTTP server to capture incoming requests.

As expected, the target server reaches out to our machine and fetches the external DTD.

The application processes the DTD, retrieves `/etc/passwd`, encodes it in Base64, and sends it to our server.

We now copy the Base64-encoded data and paste it into Burp Suite for decoding.

After decoding, we successfully retrieve the contents of `/etc/passwd`, confirming that the XXE attack was successful.






---

# Transcript :-

1
00:00:00,180 --> 00:00:05,820
Now, that's a kind of second example in this case, the website allows us to upload a contact as we

2
00:00:05,820 --> 00:00:06,390
click on it.

3
00:00:06,400 --> 00:00:12,390
That's going to give us a example file you can do if you saw so we can download it to see what this

4
00:00:12,390 --> 00:00:12,900
looks like.

5
00:00:12,930 --> 00:00:16,590
As you can see, it has multiple email addresses and different names.

6
00:00:16,750 --> 00:00:21,390
What a copy this into our notepad and we're going to give it a try.

7
00:00:21,420 --> 00:00:25,670
We're just going to send this on its own I to see how the application works.

8
00:00:25,690 --> 00:00:30,720
So in other words, we're using the default exemplar file provided by the application, which is very

9
00:00:30,720 --> 00:00:35,430
common in a lot of different websites that will give you a template to use in order for it to work with

10
00:00:35,430 --> 00:00:36,080
their systems.

11
00:00:36,300 --> 00:00:40,010
And we're just going to use a template just to see how the website interacts.

12
00:00:40,060 --> 00:00:42,690
So we're going to go ahead and save it as contacts.

13
00:00:43,200 --> 00:00:48,420
That example, we're going to go back to our documents.

14
00:00:48,720 --> 00:00:52,710
We're going to click on Contact, which is the default template provided by the website.

15
00:00:52,920 --> 00:00:55,440
And we're going to go just to see what comes back.

16
00:00:55,450 --> 00:00:57,360
As you can see, upload as completed.

17
00:00:57,600 --> 00:01:01,300
It looks like that doesn't show the outputs of any other files that we have given it.

18
00:01:01,670 --> 00:01:07,020
So it indicates that XML gets passed in the back end, but we don't get to see its response, which

19
00:01:07,020 --> 00:01:12,240
hints at having a blind xixi now that we know this is actually vulnerable and it's reaching out to our

20
00:01:12,240 --> 00:01:17,760
remote server and we confirm that Weisburd collaborator, what we're going to do is we're going to use

21
00:01:17,760 --> 00:01:18,840
an external DDT.

22
00:01:19,080 --> 00:01:21,690
I'm actually hosting this on my private server right now.

23
00:01:21,870 --> 00:01:28,310
And what's happening here is we're going to get the contents of ETEK password using file.

24
00:01:28,650 --> 00:01:33,230
We're going to assign its content to data and what's going to happen.

25
00:01:33,240 --> 00:01:40,860
The second line is we're going to actually exfil this entire thing by passing the contents of ETEK password

26
00:01:40,860 --> 00:01:43,530
and if base64 format to the server.

27
00:01:43,530 --> 00:01:47,490
So in other words, as we're reading it, whatever the content of the file is, it's going to become

28
00:01:47,490 --> 00:01:51,870
base64 encoded and it's going to be sent to our remote server to receive it.

29
00:01:52,050 --> 00:01:58,890
And there's an why we're doing base64 in this case is because this is because this file with the password

30
00:01:58,890 --> 00:02:02,640
is actually multiline and we want to receive the whole thing.

31
00:02:02,640 --> 00:02:08,010
So when it's based 64, we can take it, decode it and see the entire content versus maybe the first

32
00:02:08,010 --> 00:02:12,750
line or risking the chances of this application, breaking the content and never receiving it.

33
00:02:13,260 --> 00:02:16,950
So what we're going to do here, we're going to pop back into our contents, that XML.

34
00:02:17,880 --> 00:02:19,080
We're going to add a few things.

35
00:02:19,350 --> 00:02:23,310
The first thing is when I switch this out to even the DDT, I've already done this.

36
00:02:23,310 --> 00:02:29,280
So I went from the burb collaborator link to my private server and it's going to reach for Evo DDT.

37
00:02:29,640 --> 00:02:32,020
And then down here, one of the a few other things.

38
00:02:32,040 --> 00:02:38,500
So first of all, we want to call the entities that are being used in this XML or this external DDT.

39
00:02:38,700 --> 00:02:42,720
So the first thing I want to call it is I want to call Parum one, but we also want to call remote.

40
00:02:42,720 --> 00:02:45,450
We're going to remove this in exchange for something else later on.

41
00:02:45,870 --> 00:02:47,010
So we're going to put this right here.

42
00:02:47,010 --> 00:02:51,510
We're going to say, hey, call remote and also parum, one remote being this one.

43
00:02:51,810 --> 00:02:54,630
And then Perram one is the one right here.

44
00:02:54,930 --> 00:02:59,790
And of course, we have Explorer here that needs to be used because we want to be able to call the system

45
00:02:59,790 --> 00:03:00,030
call.

46
00:03:00,120 --> 00:03:06,570
So are we going to do is we're going to put that right in here by doing an ampersand and doing a semicolon?

47
00:03:06,740 --> 00:03:14,130
So I think this should work this time when I save it, go to our application, put contacts and run

48
00:03:14,130 --> 00:03:18,160
our HTP server to make sure we receive the contents of our file.

49
00:03:18,660 --> 00:03:25,050
So as you can see, the server reached out to our box, grabbed everybody that took the contents of

50
00:03:25,060 --> 00:03:32,100
evil DDT, passed it and gave us a base64 which I'm hoping is the content of ETEK password.

51
00:03:32,100 --> 00:03:37,770
So let's go ahead, paste it into burb suite and we're going to decode this as base64.

52
00:03:37,980 --> 00:03:42,690
And sure enough, we have the contents of our target file that we're fetching for.