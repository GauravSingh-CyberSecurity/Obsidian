Always reproduce the bug in 1st window, when writing the report in 2nd window simultane
### Example Report: CVSS_IDOR Vulnerability

---

#### **Vulnerability Type**: Insecure Direct Object Reference (IDOR)

**Affected Domain**: shop.com **Endpoint**: /shipping-address/basket

---

#### **Vulnerability Description**:

An IDOR vulnerability exists in the shopping cart page of shop.com, which allows an attacker to access and retrieve Personally Identifiable Information (PII) of other users. This includes full names, addresses, phone numbers, and other sensitive details associated with users of the website.

---

#### **Steps to Reproduce the Vulnerability**:

1. **Step 1**: Go to the shopping page of shop.com.
    
2. **Step 2**: Click on the **Basket** logo in the top-right corner to go to your cart.
    
3. **Step 3**: If you don’t already have an address created, add a new address.
    
4. **Step 4**: After creating an address, use a proxy tool like Burp Suite to intercept the request.
    

---

#### **Exploit**:

Once you've intercepted the request, you’ll see the following:

- The request made contains a **shipping address ID** parameter.
    
- Modify the **address ID** to correspond to another user’s ID (e.g., change the ID to 3, belonging to a test account).
    
- Send the request and the basket will update, now displaying the victim's address and other sensitive details such as:
    
    - Name
        
    - Address
        
    - Zip code
        
    - Phone number
        

This is a direct result of the **IDOR vulnerability** that allows unauthorized access to another user's information.

---

#### **Visual Guide for Exploitation**:

- **Step 1**: Add an address to your account.
    
- **Step 2**: Intercept the request using your proxy tool (e.g., Burp Suite).
    
- **Step 3**: Modify the **address ID** field to the ID of another user (e.g., `address_id=3`).
    
- **Step 4**: Send the modified request, which will update the shopping cart with the unauthorized user’s address.
    

---

#### **Vulnerability Impact**:

This vulnerability has severe consequences, as an attacker can easily harvest sensitive information for all users on the site, including their:

- **Full name**
    
- **Address**
    
- **Phone number**
    
- **Email** (if available)
    

This can lead to various malicious activities such as **identity theft**, **fraud**, or **targeted attacks**.

---

#### **CVSS Score Calculation**:

- **Severity**: Critical (9.3)
    
- **Vector**: Remote (network-based attack)
    
- **Complexity**: Low (simple to exploit)
    
- **Privileges Required**: None (any user can perform the attack)
    
- **Scope**: Unchanged (no impact on system behavior or availability)
    
- **Confidentiality**: High (access to PII of other users)
    
- **Integrity**: Low (the attacker cannot modify data, just retrieve it)
    
- **Availability**: Low (no direct impact on availability)
    

#### **Suggested Fixes**:

- Ensure that the application correctly verifies ownership of sensitive data, such as addresses.
    
- Implement proper access control mechanisms to prevent unauthorized access to data belonging to other users.
    

---

#### **Impact Statement**:

This vulnerability allows an attacker to harvest sensitive data on every user on the website, including their address, name, and other personally identifiable information.

---

#### **Conclusion**:

This IDOR vulnerability poses a significant risk to the confidentiality of user data on the site. It is recommended that the development team urgently addresses this issue by implementing proper authorization checks for user-specific resources.

---

#### **Attachments**:

- **Request Example**:
    

```
POST /shipping-address/basket HTTP/1.1
Host: shop.com
Content-Type: application/json
Authorization: Bearer {token}

{
  "address_id": "3", // Modify this to target another user's address
  "basket_id": "12345"
}
```

---

#### **Final Steps**:

Once the report is ready and you are satisfied with the content, submit it to the relevant program or bug bounty platform for further review.

---

### Final Thoughts:

This structured approach, with clear headings and a visual flow, will help make the report more accessible and easy to understand for both technical and non-technical reviewers.



---

# Transcript :

1
00:00:00,360 --> 00:00:03,810
Now, let's talk about reporting this to a two hour program.

2
00:00:04,020 --> 00:00:08,010
So what we're going to do is we're going to go to HOKA one, we're going to go submit report.

3
00:00:08,790 --> 00:00:15,150
And here we're going to select Nahum Sudhakar because we are on the up or shoptalk in the house or dot

4
00:00:15,150 --> 00:00:20,700
com and we're going to type an idea which is right here.

5
00:00:21,180 --> 00:00:24,120
And we're going to scroll down and give it a severity.

6
00:00:24,900 --> 00:00:28,200
The severity we've talked about this earlier chapter.

7
00:00:28,320 --> 00:00:29,460
I'm going to do this manually.

8
00:00:30,000 --> 00:00:30,690
It's easier.

9
00:00:30,930 --> 00:00:32,760
So I select my options.

10
00:00:32,760 --> 00:00:35,390
Obviously, it's network because we have to be in a remote network.

11
00:00:35,730 --> 00:00:37,320
The complexity was not super hard.

12
00:00:37,320 --> 00:00:38,160
It was super easy to do it.

13
00:00:38,160 --> 00:00:39,990
It's low privilege required.

14
00:00:40,260 --> 00:00:42,300
This could be an argument depending on the program.

15
00:00:42,300 --> 00:00:47,550
I usually put none if you are able to create an account without any information.

16
00:00:47,620 --> 00:00:50,160
In other words, it doesn't cost any money to have to be invited.

17
00:00:50,430 --> 00:00:54,030
The privilege requires not anybody could sign up the interaction.

18
00:00:54,030 --> 00:00:56,900
It's not because you don't require the victim to do anything.

19
00:00:57,210 --> 00:00:58,440
The scope is unchanged.

20
00:00:58,680 --> 00:01:05,190
Confidentiality is high, integrity could be known and availability could be done as well, which gives

21
00:01:05,190 --> 00:01:06,930
us a critical nine point three.

22
00:01:07,920 --> 00:01:09,810
We can argue that this could also be low.

23
00:01:10,170 --> 00:01:12,120
Depends on the information that you have found.

24
00:01:12,120 --> 00:01:18,090
But because this is addresses and phone numbers and full name, it's of sensitive information that you

25
00:01:18,090 --> 00:01:19,590
don't want anybody to have access to.

26
00:01:19,860 --> 00:01:21,480
We may be able to get away with a high.

27
00:01:21,480 --> 00:01:22,980
But again, this depends on the program.

28
00:01:23,220 --> 00:01:27,720
I tend to go on the high end of this, but a program may come back and say, hey, we think this is

29
00:01:27,720 --> 00:01:29,070
low, which is still good.

30
00:01:29,070 --> 00:01:32,550
It's a medium vulnerability and it was easy to find and easy to exploit.

31
00:01:33,360 --> 00:01:35,400
So we're going to go down here, we're going to give it a title.

32
00:01:35,670 --> 00:01:38,820
I like to do my titles with a few things.

33
00:01:38,820 --> 00:01:42,870
So first, I want to make sure I want to highlight what domain is in the vulnerability.

34
00:01:43,320 --> 00:01:50,940
So we're going to put in the vulnerability type and shop that New Hampshire dotcom when adding or when

35
00:01:50,940 --> 00:01:51,510
shipping.

36
00:01:53,070 --> 00:01:54,420
When selecting.

37
00:01:56,160 --> 00:02:00,220
Shipping address and slash basket.

38
00:02:00,240 --> 00:02:01,960
So, again, we're going to look at our feet.

39
00:02:02,340 --> 00:02:05,280
This is the domain we're attacking.

40
00:02:05,550 --> 00:02:08,220
This is the endpoint that is vulnerable.

41
00:02:08,500 --> 00:02:09,720
We can at the parameter.

42
00:02:09,720 --> 00:02:16,290
But this gives the program a good idea of what the vulnerability is, where is it and what the endpoint

43
00:02:16,290 --> 00:02:17,480
is, the vulnerability in.

44
00:02:17,490 --> 00:02:23,100
So we can either use the template right here or we can actually create our own.

45
00:02:23,150 --> 00:02:25,440
So for this case, we're just going to use this for the summary.

46
00:02:25,440 --> 00:02:30,090
We're going to type in what that vulnerability allows us to do and then we're going to write our policy.

47
00:02:30,120 --> 00:02:39,540
So right here, we're going to say there is an eye door in the shop that allows an attacker to pull

48
00:02:40,140 --> 00:02:41,880
PII and Prentice's.

49
00:02:41,880 --> 00:02:49,980
We can put addresses belonging to other users of hampster dot com.

50
00:02:52,830 --> 00:03:00,130
Of store dotcom, this gives us a good idea what it is now, we can use this vulnerability.

51
00:03:00,180 --> 00:03:00,990
It's an idea.

52
00:03:01,260 --> 00:03:06,810
We can use it to pull Ippei or I just has to be very specific that belong to other users and not ours.

53
00:03:07,230 --> 00:03:09,720
So I actually like to reproduce the bug as I'm writing it.

54
00:03:09,720 --> 00:03:13,800
So I'm going to do as I'm going to go ahead and redo this entire thing.

55
00:03:13,800 --> 00:03:18,290
While I'm writing the report for us, we're going to say, I don't need your basket.

56
00:03:19,770 --> 00:03:27,930
Step one, step two, click on the basket logo on the right.

57
00:03:30,020 --> 00:03:32,450
Top corner to go to your heart.

58
00:03:37,190 --> 00:03:42,380
If you do not have an address created already.

59
00:03:45,270 --> 00:03:51,450
And you adjust to your account from the current page, which is this right here.

60
00:03:56,330 --> 00:03:58,700
Once you have created an address.

61
00:04:01,450 --> 00:04:05,890
Launch your proxy to like berp.

62
00:04:08,590 --> 00:04:15,420
Intercept the request, and that's for us to be able to tell the program with the charge team that we

63
00:04:15,420 --> 00:04:19,290
want to see this request right here and this is the vulnerable.

64
00:04:20,550 --> 00:04:24,150
Now, this is the vulnerable part of this entire process.

65
00:04:25,000 --> 00:04:31,410
So we're going to say we're going to add and you should have a request similar to the one below.

66
00:04:35,390 --> 00:04:39,380
We're going to actually use Mark down, if you're not familiar with Mark down right here, you can actually

67
00:04:39,380 --> 00:04:41,720
click and read how Mark works.

68
00:04:41,750 --> 00:04:43,280
I highly recommend styling.

69
00:04:43,280 --> 00:04:46,910
Your reports will make it look better and also make it easier to read.

70
00:04:47,350 --> 00:04:50,000
Got to remove some of this information that we don't need already.

71
00:04:50,600 --> 00:04:52,740
It's going to give him this for the hundredth time.

72
00:04:52,770 --> 00:04:57,260
Hey, this is the request we're making and we're going to do this.

73
00:04:57,260 --> 00:05:01,750
And I understand we're just making a shorter I decide is three.

74
00:05:02,240 --> 00:05:05,510
You can also remove us if you don't want to give me your ID, you can do like this, but you can leave

75
00:05:05,540 --> 00:05:06,110
as it is.

76
00:05:06,870 --> 00:05:08,600
I'm going to go to the next step.

77
00:05:08,600 --> 00:05:10,700
And what we're going to say is.

78
00:05:13,410 --> 00:05:17,970
Change the address ID parameter to.

79
00:05:19,760 --> 00:05:30,740
The ID of another user in this case, I'm using ID three that belongs to my test account today, they

80
00:05:30,750 --> 00:05:37,670
understand that, hey, I'm using a test account and this is going to give you some information that

81
00:05:37,670 --> 00:05:38,720
doesn't belong to your user.

82
00:05:46,460 --> 00:05:53,270
Once you make the request, the basket will be updated with your victim's.

83
00:05:54,720 --> 00:06:01,720
Address, which leaks their name, address, zip code, etc..

84
00:06:02,640 --> 00:06:06,830
Now you have to understand what the vulnerability impact is so we can just go ahead and do this.

85
00:06:06,840 --> 00:06:08,460
We can preview it to make sure looks good.

86
00:06:09,030 --> 00:06:10,170
Everything looks great.

87
00:06:10,740 --> 00:06:13,710
They know what they going to be does how to reproduce it.

88
00:06:14,010 --> 00:06:16,440
Since the numbering is off, we're going to edit this really quickly.

89
00:06:21,100 --> 00:06:22,170
Make sure it looks better.

90
00:06:22,230 --> 00:06:23,580
Want to make sure it looks professional.

91
00:06:24,340 --> 00:06:25,510
It looks like it's being broken.

92
00:06:25,540 --> 00:06:26,400
We can leave it as it is.

93
00:06:26,410 --> 00:06:27,780
I like to do dashers anyways.

94
00:06:28,210 --> 00:06:29,420
I think it makes it easier a little bit.

95
00:06:29,650 --> 00:06:31,000
Just go ahead and edit this again.

96
00:06:32,130 --> 00:06:36,070
I want to make sure it looks as good as we can and we want to make sure that they can read out very

97
00:06:36,070 --> 00:06:39,220
easily, understand everything that's connected to each other.

98
00:06:39,340 --> 00:06:41,920
We're going to preview and it looks good.

99
00:06:42,220 --> 00:06:44,280
The last thing I want to do is write an impact statement.

100
00:06:44,290 --> 00:06:46,570
I usually try to put my impact statement in the summary.

101
00:06:46,570 --> 00:06:48,520
If you don't do it, I can type it in here.

102
00:06:48,520 --> 00:06:52,840
You can just copy, paste it and say something very quick, short and to the point to make sure that

103
00:06:52,840 --> 00:07:02,920
I understand this allows an attacker to harvest data on every single user on your website, including

104
00:07:04,780 --> 00:07:09,690
their address, name and other API.

105
00:07:11,550 --> 00:07:16,590
Now, we done we can just reveal one more time or have you in a serious escort again, it could go either

106
00:07:16,590 --> 00:07:16,980
way.

107
00:07:17,250 --> 00:07:20,670
You can go on high confidentiality, let him decide.

108
00:07:21,060 --> 00:07:21,410
Right.

109
00:07:21,600 --> 00:07:22,530
Good title to mention.

110
00:07:22,530 --> 00:07:24,060
In a time of vulnerability, it is.

111
00:07:24,330 --> 00:07:27,600
Make sure you have a volunteer weakness type selected right here.

112
00:07:27,600 --> 00:07:33,240
We can see it or I'm just going to push, submit and send us in to the program for review.