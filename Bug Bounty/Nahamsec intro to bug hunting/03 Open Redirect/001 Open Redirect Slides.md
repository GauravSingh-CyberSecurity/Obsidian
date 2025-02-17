
# Links/urls working breakdown: 
Sure! Let's break down every part of this **Google redirect URL** and explain what each component does.

---

## **Full URL:**

```
https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.linkedin.com/pulse/best-cve-sources-cyber-security-news-stay-informed-secure-evans-&ved=2ahUKEwjIie-2yJeEAxW84jgGHSvHDooQFnoECBwQAQ&usg=AOvVaw2y8pLq50J_RX4Ck7hRi8kj
```

---

## **Breakdown of Each Part**

### **1️⃣ Base URL:**

```
https://www.google.com/url
```

- This means **Google is handling the redirection** to another webpage.
- Google often uses such links when users click on search results or ads.

---

### **2️⃣ Query Parameters (After `?`)**

Everything after the `?` is a **query string**, consisting of **key-value pairs** separated by `&`.

### **🔹 `sa=t`**

```
sa=t
```

- `sa` (Source Action) refers to **how the URL was accessed**.
- `t` means it was accessed through a **text link**.

---

### **🔹 `source=web`**

```
source=web
```

- Indicates that the user clicked this link **from a web search** (Google Search results page).
- If the link was from Google Images, it might say `source=images`.

---

### **🔹 `rct=j`**

```
rct=j
```

- `rct` (Redirect Type) specifies **the type of redirection**.
- `j` likely refers to a **JavaScript-based redirect** used by Google.

---

### **🔹 `opi=89978449`**

```
opi=89978449
```

- This seems to be a unique **tracking identifier**.
- Google sometimes appends this for **internal analytics**.

---

### **🔹 `url=https://www.linkedin.com/...`**

```
url=https://www.linkedin.com/pulse/best-cve-sources-cyber-security-news-stay-informed-secure-evans-
```

- This is the **actual destination URL** where the user will be redirected.
- It's a **LinkedIn article** about CVE sources and cybersecurity news.

---

### **🔹 `ved=2ahUKEwjIie-2yJeEAxW84jgGHSvHDooQFnoECBwQAQ`**

```
ved=2ahUKEwjIie-2yJeEAxW84jgGHSvHDooQFnoECBwQAQ
```

- This is a **Google tracking parameter**.
- It stores **encoded metadata** about:
    - The search result position
    - The click context
    - Possibly A/B testing data
- Google uses it to track user interactions.

---

### **🔹 `usg=AOvVaw2y8pLq50J_RX4Ck7hRi8kj`**

```
usg=AOvVaw2y8pLq50J_RX4Ck7hRi8kj
```

- **Google's URL Signature (usg)**
- It **prevents tampering** with the redirect.
- If modified, Google may block the redirect for security reasons.

---

## **Final Explanation**

1. **Google tracks the link click** and logs metadata.
2. **The user is redirected** to the real URL (`linkedin.com`).
3. The extra parameters help Google **analyze search behaviors, prevent spam, and improve ad performance**.

---

### **How to Extract the Clean URL?**

To get the **actual LinkedIn URL** without Google tracking: 👉 **Copy everything after `url=` and decode it:**

```
https://www.linkedin.com/pulse/best-cve-sources-cyber-security-news-stay-informed-secure-evans-
```

This removes all **Google tracking** and gives you a direct link! 🚀


# Transcript of video:
1
00:00:00,240 --> 00:00:05,880
Now let's check out our first vulnerability open redirect, also known as unvalidated redirects and



![[Screenshot From 2025-02-17 20-30-23.png]]
2
00:00:05,880 --> 00:00:11,580
forwards, ==open redirects happens when the application takes an unprecedented input and redirects the==

3
00:00:11,580 --> 00:00:17,460
user from the Web application to an untrusted site or resource that will be used further for malicious

4
00:00:17,460 --> 00:00:18,010
purposes.

5
00:00:18,360 --> 00:00:23,850
The impact of an open redirect is usually set too low unless you're using it to escalate another vulnerability

6
00:00:24,180 --> 00:00:33,660
to think about open redirect as a user sharing link on Facebook and an email on SLOK, where it shows

7
00:00:33,660 --> 00:00:34,950
a trusted website.

8
00:00:34,950 --> 00:00:39,320
But once you click on it, it will redirect you to a malicious site controlled by an attacker.

9
00:00:39,540 --> 00:00:42,780
But in a lot of cases, it may not be as straightforward as it sounds.

10
00:00:42,790 --> 00:00:49,230
A lot of times developers either define a trusted or untrusted lots of resources to limit the exposure

11
00:00:49,230 --> 00:00:51,560
of where you can actually direct the users to.

12
00:00:52,170 --> 00:00:56,790
But if you understand how this limitation of filters work, you may be able to bypass it.




![[Screenshot From 2025-02-17 20-32-15.png]]
13
00:00:57,000 --> 00:01:01,650
So, for example, as I mentioned earlier, you can go to example, dot com login and next page would

14
00:01:01,650 --> 00:01:03,300
be Google and you go to Google.

15
00:01:03,300 --> 00:01:06,990
If you put in Google dot com and that parameter, this may be allowed.

16
00:01:07,500 --> 00:01:11,890
If you go to example dot com and you put an evil site where evil site as an untrusted resource that

17
00:01:11,890 --> 00:01:17,240
the developers have not defined in their white listing and the application is going to clean it.

18
00:01:17,700 --> 00:01:23,340
However, if you combine the two because the application is expecting to have Google somewhere in that

19
00:01:23,340 --> 00:01:29,970
stream for next page, you have it after question mark or before as a subdomain and different variations

20
00:01:29,970 --> 00:01:32,250
of it, you may be able to bypass those restrictions.

21
00:01:32,460 --> 00:01:38,280
So as I mentioned earlier, if you have a website that says log in next page and after logging in is

22
00:01:38,280 --> 00:01:41,400
going to be directed to Google dot com, that is going to be allowed.

23
00:01:41,490 --> 00:01:47,820
However, if you change Google dot com to evil site where evil site is not defined in the pre submitted

24
00:01:48,150 --> 00:01:52,950
whitelist and websites as a part of the filtering, it's not going to be allowed and the Web application

25
00:01:52,950 --> 00:01:56,460
may come back and say, hey, this is not allowed or it was not trusted.

26
00:01:56,670 --> 00:02:02,340
However, if you combine the two, if you put evil site dot com slash Google dot com or Google dot com

27
00:02:02,340 --> 00:02:08,180
was a lot earlier, this may actually work because the filtering system in place is just looking for

28
00:02:08,180 --> 00:02:08,640
that stream.

29
00:02:08,640 --> 00:02:09,510
Google dot com.

30
00:02:09,540 --> 00:02:14,910
As long as that's in that string, as long as it shows up, is going to allow the application to use

31
00:02:14,910 --> 00:02:18,900
it, even though it could be invalid and it may still go to evil site dot com.

32
00:02:19,590 --> 00:02:23,040
Now, let's look at this on an actual example application.















