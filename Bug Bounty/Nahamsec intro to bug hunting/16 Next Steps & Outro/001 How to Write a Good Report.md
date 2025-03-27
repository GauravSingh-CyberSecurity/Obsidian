Article: https://docs.hackerone.com/en/articles/8473994-submitting-reports | https://docs.hackerone.com/en/articles/8496338-report-templates
**How to Write a Great Report on HackerOne** (https://hackerone.com/security)

Writing a clear and effective vulnerability report is essential for getting your findings recognized and addressed. Follow this guide to create structured, detailed reports that help program owners understand your findings and prioritize them.

Sample report : https://hackerone.com/reports/867513

---

### 1. **Select the Right Domain & Asset**

Before you start writing your report, make sure you’ve selected the right **domain** and **asset**:

- **Domain**: Choose the appropriate domain you’re targeting, such as "Nahamstore" or a marketing site.
    
- **Asset**: Clearly define which part of the website or application you're working on, ensuring you are reporting the vulnerability for the correct asset.
    

**Example**: If you're reporting on Nahamstore, select the Nahamstore domain.

---

### 2. **Choose the Vulnerability Type**

Next, identify the **vulnerability type** you're working with. Common examples include:

- **Reflected vs. Stored Cross-Site Scripting (XSS)**
    
- **SQL Injection (SQLi)**
    
- **Authentication Bypass**
    

Ensure that you select the correct category, and if needed, go back to adjust it if you realize a mistake was made.

---

### 3. **Set the Severity Level** 

==**Severity** determines how critical the vulnerability is. The **Common Vulnerability Scoring System (CVSS)** is used to score vulnerabilities based on factors like: (there is a ? symbol next to all below parameters in hackerone that shows the description for them.)==

- ==**Attack Vector**: Is it exploitable over the internet, local network, or does it require physical access?==
	1) ==Network - using the internet==
	2) ==Adjacent- need to be close to router/network or target==
	3) ==Local - need to have access of local server/machine==
	4) ==Physical - need physical access to exploit==
- ==**Attack Complexity**: How difficult is the attack? Is it blocked by a web application firewall or requires a unique setup?==
	1) ==Low==
	2) ==High==
    
- ==**Privileges Required**: What kind of access does the attacker need? Are they an admin, or can anyone exploit it?==
	1) ==None(no id require)==
	2) ==Low(self register or signup)==
	3) ==High(eg: admin access required)==
    
- ==**User Interaction**: Does the attacker require the victim to click something or visit a page?==
	    ==1) None==
	    ==2) Required==

==For example, if the vulnerability is easily exploited with no user interaction, you’d mark it as low in complexity.==

- ==**Scope:**  can I change the scope?Can I pivot into the network, can access internal resources, can access things outside of that particular domain .==
		==1) changed (if this vulnerability can be used to pivot to next , like ssrf to RCE)==
		==2) Unchanged (eg: data leak through idor, no rate limiting)==

- ==**Confidentiality:** How confidential data can you access using the vulnerablity(is it PII, user id or nothing)==
	1) ==None==
	2) ==Low (user ids , etc)==
	3) ==High (PII)==

 - ==**Integrity:** Are you able to modify data, on what scale like how much of data can be modified==
	 1) ==None==
	 2) ==Low(most vulnerablity are low integrity)==
	 3) ==High (eg: can modify the price of a product to 0 and purchase it for free or ship someone else product to your address)==

- ==**Availablity:** can you do DOS or DDOS, and on what level==
		==1) None==
		==2) Low==
		==3) High==
---

### 4. **Provide a Clear and Concise Report Title**

The title should include:

- **Vulnerability Type** (e.g., XSS, SQLi)
    
- **Specific Details**: Reflect or stored type, URL, parameter, etc.
    

**Example**:  
"Reflected XSS on Nahamstore.com in search parameter."

---

### 5. **Write a Strong Description**

The description should be:

- **Brief & To the Point**: Summarize the issue in a few sentences, explaining what the vulnerability is and why it matters.
    
- **Explain the Impact**: Describe what can happen if this vulnerability is exploited.
    

**Example**:  
"This reflected XSS vulnerability allows attackers to inject JavaScript into the search parameter, leading to the execution of arbitrary scripts in the user’s browser."

---

### 6. **Step-by-Step Reproduction Guide**

Provide a **step-by-step** guide to reproduce the vulnerability. This is critical for program owners to verify the issue.
Tip: start reproducing the vulnerability on a screen and writing the guide here.

- **Steps to Reproduce**: Clearly explain what to do, what URL to visit, and any specific interactions needed.
    
- **Screenshots or Screencasts**: Include visuals to help explain each step.
    
- **Additional Details**: Include any necessary HTTP headers or source code snippets if applicable.
    

**Example**:

1. Navigate to `https://nahamstore.com/search?query=`.
    
2. Input `<script>alert('XSS')</script>` into the search field.
    
3. Observe the alert popup that shows up on the page.
    

---

### 7. **Supporting Materials**

- **Attachments**: Add any relevant **screenshots**, **videos**, or **HTTP headers**.
    
- **Source Code**: If applicable, include a snippet of the vulnerable code or input that causes the vulnerability.
    
- **External References**: Include links to related documentation or other resources that can support your finding.
    

---

### 8. **Impact Statement**

Explain the **potential impact** of the vulnerability:

- **What can an attacker do with it?**  
    For example, "An attacker can steal session cookies or execute malicious code on the user's browser."
    
- **Justification for Severity**:  
    Link the impact to the **CVSS score** to help the program owner understand the seriousness of the vulnerability.
    

**Example**:  
"This vulnerability could lead to account takeover by executing malicious scripts in the victim's browser."

---

### 9. **Review Your Report Before Submitting**

- **Preview** your report to ensure clarity and accuracy.
    
- Make sure your **steps to reproduce** are clear and that all information is well-organized.
    
- **Double-check** all visuals and examples.
    

Once everything looks good, submit your report to the program owner.

---

### 10. **Summary**

**Title**: Choose an informative title that captures the vulnerability and its location.  
**Description**: Clearly explain the issue and its impact.  
**Reproduction Steps**: Provide precise instructions for replicating the issue.  
**Supporting Materials**: Attach screenshots, HTTP headers, or code snippets.  
**Impact Statement**: Justify the severity based on potential damage or exploitation.

---

### Final Tip:

While screenshots and videos can enhance the report, they aren't necessary for every vulnerability. If the issue is simple, a well-written report with clear reproduction steps and a description will suffice.

By following this structure, you can create effective, clear reports that are easy for program owners to review and act upon.









---

# Transcript :

1
00:00:00,090 --> 00:00:03,370
Now, let's talk about writing a report and what everything means in here.

2
00:00:03,660 --> 00:00:07,920
So as one of the first things here, as the asset you're hacking on, you want to make sure you're clear

3
00:00:07,920 --> 00:00:10,280
on where you're hacking, what you're hacking on.

4
00:00:10,470 --> 00:00:12,390
You want to make sure you're selecting the right domain.

5
00:00:12,540 --> 00:00:15,480
If your domain is under Nahamstore, you want to click on this.

6
00:00:15,750 --> 00:00:18,060
If it's a marketing site, you want to click on this and so on.

7
00:00:18,360 --> 00:00:23,260
So this case of this example, we're going to click on the home store and move on.

8
00:00:23,370 --> 00:00:25,380
We're going to click on the home store and move on.

9
00:00:25,710 --> 00:00:27,380
Next thing you want to select is your weakness.

10
00:00:27,390 --> 00:00:32,070
So if you're looking for accessories, you want to search for accessories and they will bring up the

11
00:00:32,280 --> 00:00:34,790
different vulnerability types under exercise.

12
00:00:34,980 --> 00:00:36,590
And you want to make sure you select the right ones.

13
00:00:36,600 --> 00:00:40,110
If you're doing reflected versus store, you want to make sure you select the right one.

14
00:00:40,350 --> 00:00:45,840
If you make it and if you make a mistake, you can select that type of exercise again and select the

15
00:00:45,840 --> 00:00:47,980
right appropriate, accessible ability.

16
00:00:48,240 --> 00:00:49,830
The next thing is the severity.

17
00:00:49,830 --> 00:00:53,700
Hucko one here relies on CBS other platforms to do this differently.

18
00:00:53,700 --> 00:00:58,080
Some platforms allow you to select a criticality level or some other platform.

19
00:00:58,080 --> 00:01:01,630
Assign it to your vulnerability based on what you're reporting.

20
00:01:01,930 --> 00:01:04,470
So for this case, we're going to go through CBS very quickly.

21
00:01:04,650 --> 00:01:08,280
The attack vector is attack vector means how do you exploit this?

22
00:01:08,280 --> 00:01:09,800
But do you have to be on the Internet?

23
00:01:09,810 --> 00:01:13,890
You have to be close to the local network, or do you have to have physical access to it?

24
00:01:14,100 --> 00:01:17,790
Also, if we are confusing and you want to using them on your own, you can click on the question mark.

25
00:01:18,060 --> 00:01:18,840
It would explain it.

26
00:01:18,840 --> 00:01:24,270
But I want to quickly cover some of these things and help you understand how they work so you can select

27
00:01:24,270 --> 00:01:29,880
your CBSA score manually and make sure it's the closest to your vulnerability as well.

28
00:01:31,280 --> 00:01:32,820
The next thing is attack complexity.

29
00:01:33,030 --> 00:01:34,550
How hard is it to exploit this?

30
00:01:34,560 --> 00:01:38,010
Are you going against a filter or are you going against a Web application firewall?

31
00:01:38,310 --> 00:01:44,190
Are you relying on some weird conditions to be met in order to this in order for this to work?

32
00:01:44,400 --> 00:01:48,930
So if they said, yes, we're going to do high, if no weird scenario is supposed to be met, we can

33
00:01:48,930 --> 00:01:51,020
click onto the next thing that's required.

34
00:01:51,240 --> 00:01:52,500
This is very, very tricky.

35
00:01:52,500 --> 00:01:55,440
You have to understand, how do you get access to this application?

36
00:01:55,710 --> 00:01:59,190
If you have to be an admin, then obviously you have to go on the high end.

37
00:01:59,370 --> 00:02:03,060
If you have to be invited where you can't self register can go to a low.

38
00:02:03,210 --> 00:02:08,040
And of course, if anybody could just sign up for an account without any ID, any invitation, nothing

39
00:02:08,040 --> 00:02:10,290
like that, then I usually tend to go with none.

40
00:02:10,530 --> 00:02:15,030
Again, these may change depending on the program, but in most cases that's how I've scored mine.

41
00:02:15,300 --> 00:02:20,550
User interaction means does the user have to interact with that particular thing to have to click on

42
00:02:20,550 --> 00:02:21,030
anything?

43
00:02:21,030 --> 00:02:22,350
Did I have to visit some page?

44
00:02:22,590 --> 00:02:25,710
And that based on that, you have to set this to required or not.

45
00:02:25,950 --> 00:02:32,760
Most vulnerabilities like either SRF or see things that are server side comes down to being known versus

46
00:02:32,760 --> 00:02:34,440
something like Stridex.

47
00:02:34,440 --> 00:02:39,090
Assess where the user has to click on the link, then that requires some sort of user interaction.

48
00:02:39,780 --> 00:02:41,280
The scope could mean many things.

49
00:02:41,490 --> 00:02:47,880
In our case, I usually look at this as can I access things other than the current website?

50
00:02:47,890 --> 00:02:51,570
So in other words, if it's necessary for an RC, can I change the scope?

51
00:02:51,570 --> 00:02:57,750
Can I pivot into the network, can access internal resources, can access things outside of that particular

52
00:02:57,750 --> 00:02:58,110
domain.

53
00:02:58,380 --> 00:03:03,150
So if you're doing an RC or SRF or something like that, you can go to change and otherwise you can

54
00:03:03,150 --> 00:03:03,930
go to unchanged.

55
00:03:04,650 --> 00:03:07,230
Confidentiality is based on the data that you have access to.

56
00:03:07,500 --> 00:03:12,180
So if you find a vulnerability that gives you some weird data that should be confidential, maybe something

57
00:03:12,180 --> 00:03:17,940
like a full name, you can go with low, which is finding an address, Social Security number, phone

58
00:03:17,940 --> 00:03:18,330
number.

59
00:03:18,330 --> 00:03:21,150
You can go on to click on High Integrity.

60
00:03:22,200 --> 00:03:24,390
You can go and click on High for Integrity.

61
00:03:24,390 --> 00:03:29,610
It comes down to if you can actually modify this data and how much can you modify.

62
00:03:29,640 --> 00:03:36,090
So in a lot of cases like exercise can go on the non or low depending on what you could do or how you

63
00:03:36,090 --> 00:03:36,720
exploit it.

64
00:03:37,050 --> 00:03:40,760
But in the case of most vulnerabilities, you can go with low on this.

65
00:03:40,770 --> 00:03:42,930
You are 100 percent sure that you can change data.

66
00:03:42,930 --> 00:03:47,490
For example, you have an idea that allows you to change a user's address.

67
00:03:47,700 --> 00:03:53,520
They can go on high because, you know, for e-commerce website, you can force them to ship stuff to

68
00:03:53,520 --> 00:03:56,250
your address or whatever that is availability.

69
00:03:56,280 --> 00:03:58,440
Think about it as a denial service.

70
00:03:58,650 --> 00:04:00,900
Can you deny access to this user?

71
00:04:00,900 --> 00:04:04,920
In most cases, it's none depending on their vulnerability, but in most cases it's none.

72
00:04:05,190 --> 00:04:07,290
But if he can deny it easily, then it's slow.

73
00:04:07,440 --> 00:04:11,670
And if you can, for example, have an RC where you can turn off the server or something like that,

74
00:04:11,880 --> 00:04:13,050
you can click on Hi.

75
00:04:14,350 --> 00:04:16,830
Now let's talk about how to run our report.

76
00:04:17,430 --> 00:04:19,260
The first thing you want to do is the title.

77
00:04:19,350 --> 00:04:23,860
So the first thing that I want to write in my title is a vulnerability type exercise.

78
00:04:24,180 --> 00:04:25,820
I adore SRF.

79
00:04:25,830 --> 00:04:28,650
Whatever the vulnerability type is, we're going to type it in for.

80
00:04:28,710 --> 00:04:33,720
So let's just say we're going to type in exercice and the next thing we want to do is we actually want

81
00:04:33,720 --> 00:04:35,280
to get more specific is installed.

82
00:04:35,280 --> 00:04:36,660
Is that reflected as a dome.

83
00:04:36,660 --> 00:04:37,110
What is it.

84
00:04:37,450 --> 00:04:42,270
We're going to type in store for example then I like to type in the asset where the vulnerability is.

85
00:04:42,450 --> 00:04:48,330
So for example, if it's an shoptalk NAHOUM store dot com we're going to have to send right here and

86
00:04:48,330 --> 00:04:50,790
then we're going to say the endpoint or the parameter.

87
00:04:51,060 --> 00:04:52,470
The error page.

88
00:04:54,920 --> 00:05:04,310
And the X parameter, or you can say the error page and introducing a new parameter, whatever the exploitation

89
00:05:04,310 --> 00:05:07,820
technique is, you want to put that in there and you also want to make sure you have an endpoint.

90
00:05:07,820 --> 00:05:09,590
That was an error page with the error page.

91
00:05:09,800 --> 00:05:16,670
But if it's in the basket, you want to put it in a basket in here and however else you are exploiting

92
00:05:16,670 --> 00:05:16,810
it.

93
00:05:18,720 --> 00:05:24,330
This also helps this also helps the program owners to be able to DDP vulnerability, make sure there's

94
00:05:24,330 --> 00:05:29,160
no duplicates, nothing like that, also helps them identify who the owner is, if they've already seen

95
00:05:29,160 --> 00:05:32,670
this before, and it just helps with the overall triage process.

96
00:05:33,060 --> 00:05:34,790
The next thing is the description.

97
00:05:34,830 --> 00:05:36,690
This is really easy to do.

98
00:05:36,870 --> 00:05:40,890
The summary, obviously, you want to tell them what the summary of the bug is kind of like introduction

99
00:05:40,890 --> 00:05:52,920
of what it is there is and exercise and whatever by manipulating whatever else and X, Y, Z, you page

100
00:05:53,040 --> 00:05:57,120
something short, something to understand what is the vulnerability and where they can find it.

101
00:05:57,630 --> 00:06:02,940
The next thing is you want to write step by step how to reproduce a small number that what looks and

102
00:06:02,940 --> 00:06:07,310
you have to click on where you have to log and what functionality you have to go to, what requested

103
00:06:07,320 --> 00:06:08,930
you to intercept and so on.

104
00:06:08,970 --> 00:06:14,820
The way I like to write this as I start reproducing the bug on one screen and then coming back to my

105
00:06:14,820 --> 00:06:20,160
report and typing each step as I go and make sure it all makes sense and also includes screenshots if

106
00:06:20,160 --> 00:06:22,050
it's required and whatnot.

107
00:06:22,060 --> 00:06:23,670
You can also include the HTP header.

108
00:06:23,880 --> 00:06:26,900
I like to usually do it specifically for the vulnerable endpoints.

109
00:06:26,910 --> 00:06:30,540
I can say, hey, this is the parameter, this is the endpoint that's vulnerable.

110
00:06:30,720 --> 00:06:37,020
And also for a thing like an exercise, I also try to grab a screenshot or a snippet of the source to

111
00:06:37,020 --> 00:06:40,320
tell them, hey, this is whatever or nobody goes and we'll cover this later on.

112
00:06:40,350 --> 00:06:42,150
The supporting material is good to have.

113
00:06:42,390 --> 00:06:44,460
It's good to link to Ola's or something like that.

114
00:06:44,490 --> 00:06:45,570
I personally don't do it.

115
00:06:45,570 --> 00:06:50,270
I skip this part, but I try to attach any references, any attachments, any pictures, videos that

116
00:06:50,280 --> 00:06:50,730
I can.

117
00:06:51,090 --> 00:06:56,820
The rule of the rule of thumb here is you don't need to put a video for every single PEOC.

118
00:06:56,820 --> 00:07:00,900
If you have something complex that takes a few steps to do it, you can attach a video.

119
00:07:01,170 --> 00:07:03,210
But in a lot of cases, I don't think you need a video.

120
00:07:03,210 --> 00:07:06,420
You can skip that and just do your APRC right here and send it out.

121
00:07:07,170 --> 00:07:09,060
Last but not least, you want to do your impact statement.

122
00:07:09,060 --> 00:07:11,610
You want to tell them what Kandace vulnerability to do.

123
00:07:11,790 --> 00:07:17,340
If there's an exercise, if you have a good policy waiting for, you can say this exercise could lead

124
00:07:17,340 --> 00:07:20,130
to taking over another user's account.

125
00:07:22,440 --> 00:07:26,160
This helps the program owners understand what this vulnerability could do.

126
00:07:26,310 --> 00:07:31,710
It helps you make a justification on your CV, SS, and also helps them determine if you see the SS

127
00:07:31,710 --> 00:07:33,060
calculation as correct or not.

128
00:07:33,330 --> 00:07:37,350
So you always want to put something right here that explains, um, hey, that explains to them, hey,

129
00:07:37,560 --> 00:07:39,930
this is what you can accomplish with this warning of any type.

130
00:07:40,080 --> 00:07:43,050
And this is why I've marked the CBO score as what it is.

131
00:07:45,140 --> 00:07:48,800
And of course, the best thing to do at the end is to preview everything, make sure it looks good,

132
00:07:48,950 --> 00:07:53,930
and last but not least, want to scroll down and submit as soon as you're ready to send the to program

133
00:07:53,930 --> 00:07:55,220
owners for review.

134
00:07:55,730 --> 00:07:57,110
And again, we're going to cover all these.

135
00:07:57,110 --> 00:08:00,350
I'm going to give you a few examples of how to write a report for access.

136
00:08:00,710 --> 00:08:01,150
I do.

137
00:08:01,160 --> 00:08:02,300
And a few other Vaughn types.

138
00:08:02,480 --> 00:08:07,100
But I want to make sure I walk through all of this and explain my thought process before we jump into

139
00:08:07,100 --> 00:08:07,730
the examples.