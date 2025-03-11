Analysis of RCE lab :  the lab3 continued from previous (003 RCE Lab 02) notes: 
( http://rce3.naham.sec:8081/ )
![[Screenshot From 2025-03-11 11-20-40.png]]


And last but not least, if we want to actually run a command using coding language(in this case PHP) , PHP has different functions that allow an application to run an operating system command. We can actually look it up.  
We're going to look for **PHP shell exec**.  
And we're going to check the manual for it to understand how it works( https://www.php.net/manual/en/function.shell-exec.php ). 

The good thing is that it has really good documentation, you can see all the similar functions that allow you to execute commands, execute system commands, and even provide examples :-
![[Screenshot From 2025-03-11 11-25-12 2.png]] 
```
<?php  
$output = shell_exec('ls -lart');  
echo "<pre>$output</pre>";  
?>
```
What this does is assign our command to a variable called output, and then it echoes that output to display whatever comes back as a result.  

So, let's go ahead and type that in.  
```
<?php  
$output = shell_exec('uname -a');  
echo "<pre>$output</pre>";  
?>
```
We're going to actually change this (`shell_exec('ls -lart')` ) to use the "id" `shell_exec('id')`command or "uname" `shell_exec('uname')` or whatever we want. 

In this case, with "uname -a" ( `shell_exec('uname -a')` ), I'm going to Paste our command as is in the comment.
![[Screenshot From 2025-03-11 11-32-27.png]]


As you can see, the application took our code, executed it at the operating system level, and returned the output of the command (  Linux c649de042813 6.12.13-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11) x86_64 x86_64 x86_64 GNU/Linux )
![[Screenshot From 2025-03-11 11-34-08.png]]


---

# Transcript :
1
00:00:00,100 --> 00:00:07,350
And not least if we wanted to actually run a command using so PSB has different functions that allows

2
00:00:07,350 --> 00:00:12,540
an application to run an operating system command, we can actually look it up.

3
00:00:12,540 --> 00:00:15,270
We're going to look for special exact.

4
00:00:17,420 --> 00:00:20,390
And we're going to have the manual for it to understand how it works.

5
00:00:20,990 --> 00:00:26,510
The good thing about years of some really good documentation here, you can see all the similar functions

6
00:00:26,510 --> 00:00:32,030
that allow you to execute commands, executor systems, even give you examples.

7
00:00:32,720 --> 00:00:38,930
You're going to copy this or this is doing is it's going to assign our command to a variable called

8
00:00:38,930 --> 00:00:44,090
output, and then we're going to echo it and write out whatever is coming back as a result of output

9
00:00:44,090 --> 00:00:44,900
into the page.

10
00:00:45,560 --> 00:00:46,990
So let's go ahead and type that in.

11
00:00:47,540 --> 00:00:51,650
We're going to actually change this to ID or you name whatever we want.

12
00:00:52,490 --> 00:00:56,870
This case with the you name a I'm going to leave our comment go down here.

13
00:00:57,180 --> 00:01:03,230
As you can see, the application took our code, executed it on the operating system level and gave

14
00:01:03,230 --> 00:01:05,360
us the outputs of the command.