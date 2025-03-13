

The idea of using Google as a hacking tool or platform certainly isn’t novel, and hackers have been leveraging this incredibly popular search engine for years. **Google Dorks** had their roots in 2002 when a man named Johnny Long started using custom queries to search for elements of certain websites that he could leverage in an attack. At its core, that’s what Google Dorks are – a way to use the search engine to pinpoint websites that have certain flaws, vulnerabilities, and sensitive information that can be taken advantage of. As a side note, some people refer to Google Dorks as Google Hacking (they’re more or less synonymous terms).

![](https://www.hackingloops.com/wp-content/uploads/2016/07/1-cover-Google-Dork-1024x536.png)

Google Dorking is a technique used by hackers to find the information exposed accidentally to the internet. For example, log files with usernames and passwords or cameras, etc. It is done mostly by using the queries to go after a specific target gradually. We start with collecting as much data as we can using general queries, and then we can go specific by using complex queries.

Believe it or not, Google Dorks can uncover great information such as email addresses and lists, login credentials, sensitive files, website vulnerabilities, and even financial information (e.g., Payment card data). In fact, in our WordPress hacking tutorial, we listed a few Google Dorks that could be used to find SQLi (SQL injection) vulnerabilities. And the wonderful thing is that this is an incredibly passive form of attack that doesn’t draw much attention to the hacker. Unfortunately, some people use these techniques for illicit and nefarious activities such as cyberwarfare, digital terrorism, identity theft, and many other undesirable activities.

If you are reading this to learn how to break into a website and harm others just for kicks, perhaps you should pursue other interests. Let me caution you by stating that breaking into websites is an _illegal activity_, and it violates not only laws but also moral codes. If you get caught, the consequences could be dire. Then why learn this, to begin with, you ask? Well, the first place any white-hat hacker needs to start is with understanding how hackers operate. Only then can they plug up security holes to prevent future attacks.

## **Fundamentals of Google Dorking**

There are seven fundamentals of google Dorking. These are nothing but just how we can use google with advanced techniques. These seven fundamentals are seven types of main queries which make the basic structure of google Dorking. We will now see one by one how these queries are used by hackers(back/grey/white hat) to get the information related to an organization or even an individual.

### **Note:** 

Google Dorking is not hacking itself. Google Dorking is a technique that comes in handy in one of the phases of hacking, i.e., Information Gathering, and this is the most important phase of hacking. There are five phases of hacking, i.e., reconnaissance, scanning, gaining access, maintaining access, and clearing tracks. Google Dorking is used in the starting phases where hackers try to get all the information linked to any specific organization or an individual. After getting all information then hackers pick out the information they need for the next phases.

### **Captcha Issue while using Google Dork**

As we can use google for the activity, which can disclose the information of others, and that information can be used for wrong purposes. Many black hat hackers have put bots online to scrawl the websites, find weaknesses in the pages, and then send information back to servers. To stop and degrade this issue, Google has introduced a captcha in this process. You will need to enter a captcha almost every time you use a dork. This way, Google stops bots from using google for illegal purposes.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/2-captcha-Google-Dork-2-1024x547.png)

### **Understanding Google Dorks Operators**

Just like in simple math equations, programming code, and other types of algorithms, Google Dorks has several operators that aspiring white hat hackers need to understand. There are far too many to include in this guide, but we will go over some of the most common:

- intitle – This allows a hacker to search for pages with specific text in their HTML title. So intitle: “login page” will help a hacker scour the web for login pages.
- allintitle – Similar to the previous operator, but only returns results for pages that meet _all_ of the keyword criteria.
- inurl – Allows a hacker to search for pages based on the text contained in the URL (i.e., “login.php”).
- allinurl – Similar to the previous operator, but only returns matches for URLs that meet _all_ the matching criteria.
- filetype – Helps a hacker narrow down search results to specific files such as PHP, PDF, or TXT file types.
- ext – Very similar to filetype, but this looks for files based on their file extension.
- intext – This operator searches the entire content of a given page for keywords supplied by the hacker.
- allintext – Similar to the previous operator but requires a page to match _all_ of the given keywords.
- site – Limits the scope of a query to a single website.

## **Queries:**

### **Cache Command**

Google not only lists current versions of web pages, but it also stores the previous versions of websites in its cache, and those pages sometimes can give you a lot of information about the technology being used by the developers. It can also sometimes disclose information initially used for testing purposes only and was removed in the later versions but still viewable in the versions that Google has in its cache.

#### **Syntax**

Its syntax is “cache:website address”. For example, let’s use the cache command for a random website and see the results. Results may vary from time to time as we see updates from google as well.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/3-cache-Google-Dork-1024x734.png)

As for results, we have multiple responses that can gather further information related to that website.

We can also use this search query to highlight some keywords in our search results. Let us suppose that we want to highlight the “flex” word in our research, and then we will write the query as follows:

“cache:[https://flexstudent.nu.edu.pk/Login](https://flexstudent.nu.edu.pk/Login) flex.” It will highlight this keyword in the results.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/4-Flex-Google-Dork-1024x636.png)

### **intext & allintext Command**

The intext command is used to find specific text within the search result from the webpage. Intext can be used in two ways. The first is to get a single keyword in the results and the second way is to get multiple keywords in the search. To accomplish the first task, the syntax for the command is

intext:usernames

To accomplish the second task, we use allintext instead of intext. And we separate the keywords using a single space. If we use allintext, then google will add all those pages in the result with all the keywords in their text mentioned in the query. If a web page has some missing keywords, it will be discarded from the results, and the user will not see that web page. That is why these commands are used with proper keywords so that necessary information is not discarded.

#### **Syntax**

Let’s say we want to find out some pages having information related to usernames and passwords, and then we will write the query as follows:

allintext:”username” “password”

And the result we got in the result is as follows:

![](https://www.hackingloops.com/wp-content/uploads/2016/07/5-username-and-password-Google-Dork-1-1024x609.png)

As you can see that all the return pages have username and password in them, and that is because of our query, which we have used. It has given us those pages that have both keywords in them.

### **Filetype command**

Filetype is one of those seven famous fundamentals of google Dorking as it helps in filtering out a large number of files. It can filter pdf files for you. It can even filter log files for you. Log files are very useful for collecting information related to an organization as these are the files that keep track of all the events that happen in an organization. If we want to get access to simple log files, we can write this command: filetype:log, and it will give us all types of log files, but this cannot be of much help until and unless we try to narrow down our search with some filters.

#### **Syntax**

Let us make it more specific by specifying that we want those files with usernames and passwords. For this purpose, we will modify our query like this:

allintext:username filetype:log

It will display those results that have usernames and passwords mentioned in them. If these files belong to any server, one cannot imagine how much damage they can cause.

Opening a random file after gettings result by applying this query is as follows:

![](https://www.hackingloops.com/wp-content/uploads/2016/07/6-filetype-Google-Dork-1024x751.png)

As you can see, it may not have any meaning for beginners, but it may play an important role in information gathering related to a company or a server. This information can be the key to many new adventures.

Looking at another file on the internet, we may end up having usernames and passwords as well.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/7-passwords-Google-Dork-1024x606.png)

You can use this technique to narrow down the results to some specific user.

First, you will get log files using this query, and then you can easily find the required username after searching through that document.

### **Intitle command**

The intitle is a command which is used when we want to filter out the documents based on the titles of HTML pages. As we know that HTML pages have those keywords in the title that define the whole document. They represent the summary of what is described in the document. We can use this feature to get exactly what we want. Suppose we are looking for documents that contain the information related to IP-Camera then we will write a query to tell google that filter out all the pages based on the provided argument. 

#### **Syntax**

The basic syntax to use this command is as follows:

intitle:”ip camera”

We also have an option to use multiple keywords to get more precise results. To use multiple keywords, we write them in separate commas. Google gets all the pages first, and it then applies filters to the results. Those web pages that do not have provided keywords in the title of the website are discarded. The syntax for using this command is as follows:

allintitle:”ip camera” “dvr”

Below is the result of this query. You can see that it has shown us all those pages that have both these keywords in their title. We can use this technique to filter our results very effectively.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/8-dvr-Google-Dork.png)

### **inurl command**

Inurl command works the same as intitle. The difference is that Inurl is a command used when we want to filter out the documents based on the URL’s text, as we know that HTML pages have those keywords in the URL that define the whole document. They represent the summary of what is described in the document. We can use this feature to get exactly what we want. Again, suppose we are looking for documents that contain the information related to IP-Camera. We will write a query to tell google that filters out all the pages based on the provided argument. We also have an option to use multiple keywords to get more precise results.

#### **Syntax**

The basic syntax to use this command is as follows:

allinurl:tesla lambo  
![](https://www.hackingloops.com/wp-content/uploads/2016/07/9-tesla-lambo-Google-Dork.png)

### **Site command**

We have another command that is very useful when we want to search for a specific entity. At first, we make our search criteria broad and collect information that may or may not be related to our needs. After getting enough for a starting point, we start narrowing down our search using other commands. For example, suppose we want to buy a car, and we were searching about cars introduced later in 2020. After getting a list from the results, we studied the pages and found that Honda and Ford are reliable. Now our next step would be to gather information about these cars from authentic websites. So here comes the use of site command. Now, we will narrow down our search to some specific websites only.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/10-tesla-honda-Google-Dork-1024x831.png)

#### **Syntax**

site:[https://global.honda/](https://global.honda/)

It will give us all related to this website only. Similarly, if we want to search ford now, we may only change the website address and get our results.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/11-ford-Google-Dork-1024x848.png)

### **ext command**

Sometimes, we want to search for documents that are of a specific type. For example, we want to write an article about “phishing detection.” We cannot just start writing about it unless we first do our research on it. Research articles are mostly published in pdf formats. Now, if we want to read previous research that has been done on this topic, we would add another dork in our command, which is called ext. Ext is a command that is used to specify file extensions. It works like a filetype command. If we modify our previous search, which we did about ford cars, we may now want to look for only pdf files, and then we will write the query as follows:

#### Syntax

site:https://www.ford.com/ ext:pdf

![](https://www.hackingloops.com/wp-content/uploads/2016/07/11.2-syntax-pdf-1024x768.png)

From the results below, you can see that we now have only pdf files as our results.

### **More Sample Examples**

Suppose we want to access an FTP server. The command would be to mix queries and then achieve what we want.

#### **Finding FTP servers**

Syntax is : intitle:”index of” inurl:ftp

It will find all the index pages related to an FTP server and show the directories.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/12-ftp-Google-Dork-1024x788.png)

After getting results, we can check different URLs for information.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/13-ftp-2-Google-Dork.png)

We can even see the source code sometimes, which should not be public. The image attached below cannot be considered confidential, but the procedure for this activity is the same. Stating our recommendation not to download files from the unsecured servers as they may have already been compromised.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/14-ftp-3-Google-Dork-1.png)

### **Accessing Online Cameras**

Now, as we have read a lot about these dorks, we may come across something that should not be accessed because it may hurt someone’s privacy. The purpose of this activity is to spread the word that we need to take our privacy seriously. People nowadays are putting CCTV cameras in place to make them secure, but they are not making those cameras safe. They are even doing it worse by making them public. Below are some screenshots of cameras that are public, and anyone can see what is going on there.

#### **Syntax**

Intitle:”webcamXP 5”’

![](https://www.hackingloops.com/wp-content/uploads/2016/07/15-cctv-footage-1-Google-Dork-1024x652.png)

You can see that these people are more vulnerable now because people can keep track of their activities easily.

Some more examples:

![](https://www.hackingloops.com/wp-content/uploads/2016/07/16-cctv-footage-2-Google-Dork.png)

![](https://www.hackingloops.com/wp-content/uploads/2016/07/17-cctv-footage-3-Google-Dork.png)

Even I cannot post more than that. People are even exposing their homes which is not ethical to see even if we access it.

## **How not to get Dorked!**

Google dorks or Google hacking for regular individuals is just scratching the surface. Indexing can discover pictures, videos, ISO or other file types, and even cached versions of a website. Vulnerable data is easily exposed to Google Dorking, which can easily lead to hacking or penetrating the website itself. To prevent such attacks from fingerprinting vulnerable applications, we need to understand how they work in the wild.

Although it’s pretty easy to expose some data using Google Dorks, prevention is not that tough either. There are a couple of things we can do to stay safe from Google hacking.

**IP-based Restriction:** IP-based restrictions should be given priority. Wherever possible, use two-factor authentication, encryption, IP restriction, and secure password to stay free from Google Dorking.

**Vulnerability scans:** Vulnerability scans can be a website owners’ best friend. There are so many loopholes to cover, and they can easily be overlooked. Vulnerability scans have specific queries to prevent Google dorks, which is highly beneficial.

**Google search console:** The Google search console can help remove sensitive content such as payment pages, user information, and insider data. If those are required to run the platform, they can be indexed and, as a result, could be prone to such attacks. Google search console helps to remove them from the search query database.

**Be the hacker to keep them away:** A great way to find any part exposed is by running dork queries yourself. It is one of the best methods, and even website owners pay others to run dork queries on their website. As it can get quite complicated pretty quickly, running queries yourself on the whole platform and later specific sensitive parts can expose if it’s safe or not. Measures can be taken afterward.

**Dorking types:** Commonly used methods of Google Dorking include website URL Dorking and sequence-based Dorking.

**robots.txt:** Another great way to hide sensitive information from the google Dorking query is utilizing the robots.txt document. Robots.txt denies the registry and hides private information. However, it also indicates, sensitive data is on that file, so it can turn out to be a two-way sword.

To set up robots.txt and freely index internal content:

User-agent: *

Disallow: /

File access restriction:

User-agent: *

Disallow: /admin/

&

User-agent: *

Disallow: /privatearea/file.html

Restrict access to dynamic URL with ‘?’ symbol:

User-agent: *

Disallow: /*?

**Testing common keywords:** one of the simplest and common Google dork keywords is site. We can use it to narrow down the findings of a particular website. In our case, we keyworded the site to see Google cached pages from hackingloops.com. It is all fun and games, but to further look into the details and block Dorking’s outcome, we can use tools such as Gooscan, Wikto, or Sitedigger. Although, we only recommend trying out sites made specifically for testing or your own.

**Security camera dork prevention:** We already talked about how Google Dorking can give access to vulnerable security cameras (CCTV live footage), alongside we can have control over camera modifiers such as moving, zoom in in-out, changing resolution, refresh rate, etc. While it can be intriguing to observe this kind of stuff anonymously, it is highly likely to leak your privacy and security information.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/18-netwrok-cameara-2-Google-Dork.png)

To view open CCTV, type in

inurl: top.htm inurl:currenttime

intittle:”webcamXP 6”

inurl: “lvappl.htm”

inurl:” viewframe?mode=motion

![](https://www.hackingloops.com/wp-content/uploads/2016/07/20-netwrok-cameara-3-Google-Dork-1024x519.png)

The command will list available CCTV cameras based on routing results. To get the best result, we can open all possible results and view the GUI. Securing those GUI pages not to be affected by indexing is the suggested idea. Also, some users keep the default network monitoring password mode on; the danger is that the password remains quite the same across manufacturers, and it’s easy to get picked. So, if the network camera is your priority, change the default password to a stronger one. Also, disable remotely logging in to the security system as this too is enabled by default.

**XSS prevention:** XSS remains one of the core fundamentals that must be secured before even deploying a webpage for the public. Severer side sanitation is not a hard problem to solve but remains in the hands of filter blocking function. Though it is quite hard to write a filter to block XSS attacks, rich text formatting, using simpler cases, data sanitization, utilizing tags such as <b> or <i> can solve the issue.

**Personal data:** Nothing severe is losing personal data to someone you don’t know or can cause harm. It’s as easy as using a simple command like

filetype:php inurl:list/admin/ intittle:”payment methods”  or

intittle:index.of finanaces.xls

These simple queries can list personal and even bank information. To avoid them encrypting and password protect data. Even if it’s not your data, there is a responsibility to protect customer information. A directory-level configuration such as .htaccess can protect your directory from Google crawlers.

GoogleDork: As crawlers are important to index data with Google search engine, it will always look for new information. So, data is prone to fall under Dorking unless you’re careful. [Exploit-db.com](https://www.exploit-db.com/google-hacking-database) has updated dork commands which is helpful to get familiarized.

![](https://www.hackingloops.com/wp-content/uploads/2016/07/21-exploit-database-Google-Dork-1024x635.png)

Even if you’re trying to stay safe from hackers, checking them will give a rough idea of the latest tactics, so you know how to handle the situation beforehand. Although there are many more prevention techniques, adaption to these will roughly give a solid protection against Google Dorking. For further prevention expand upon the ideas mentioned throughout the article which will make things fairly easy.

### **Google Dorks automation tools**

As we mentioned, Google Dorking requires lots of keywords and patience to find the specific vulnerability. Though it is not recommended to search for other platforms’ vulnerabilities, bug-bounty programs are specifically for that. Attend them! But for testing our skills, practicing in the wild is a must. Sending dork requests to Google can give fascinating results.

But if you ever thought it’s easy to manipulate all day, then you’re wrong. Google’s mechanism to stop Dorking is quite accurate. Sending multiple Dorking requests may block the IP in rare cases, but users get captcha for the common case of various searches. Attackers and hackers both use Google dorks, but to make stuff easy, they use automation tools. There are many automation tools such as Zeus, xgdork, Dorkme, Bingoo, GoogD0rker, gD0rk, M-dork, Gooscan, and many more. These tools are just a few clicks away and help in automating Google Dorking.

Black hat, White hat, Red hat everyone keeps some of these tools in their arsenal for finding vulnerability pretty quick and easily. As Google has a strict limitation on the query sent per IP address, proxies are mandatory. Python is the most popular scripting language for automation. A simple run of Selenium-based script can hack a website or collect its data. Similarly, Python automation scripts are a dangerous combination in a mix with proxy and Google Dorking tools.

# **Important Note**

The purpose of using google Dorking should be to use these tricks to make people and yourself secure. If you are reading this, it means you have to some extent in cybersecurity. It is the responsibility of every individual to use the information for well-being, which should be the final goal.

To get more knowledge about complex commands, you can refer to Github. People have written complex commands by combining two or more dorks for accurate results. In the end, it is all about practice.

### **Custom Crafting Google Dork Queries**

Now that we have a basic understanding of some of the operators and how Google Dorks can scour the web, it’s time to look at query syntax. The following is the high-level structure of Google Dorks that targets a specific domain:

“inurl: domain/” “additional dorks”

A hacker would plug in the desired parameters as follows:

- inurl = The URL of a site you want to query
- domain = The domain for the site
- dorks = The sub-fields and parameters that a hacker wants to scan

If a hacker wishes to search by a field other than the URL, the following can be effectively substituted:

- intitle:
- inurl:
- intext:
- define:
- site:
- phonebook:
- maps:
- book:
- info:
- movie:
- weather:
- related:
- link:

These options will help a hacker uncover a lot of information about a site that isn’t readily apparent without a Google Dork. These options also offer ways to scan the web to locate hard-to-find content. The following is an example of a Google Dork:

[inurl:login.jsp intitle:login](http://www.google-dorking.com/2016/04/inurlbackoffice-intitlelogin.html)

### **Making Effective Use of Operators**

It may seem a little cryptic at first, so let me provide a few examples that show how the different operators can locate content and website data. A user can make effective use of the **intitle** operator to find anything on a website. Perhaps they are scraping email addresses and want to scan sites for the “@” symbol, or maybe they are looking for an index of other files.

Furthermore, the **intext** operator can be used to scan individual pages for any text you want, such as a target’s email address, name, the name of a web page (like a login screen), or other personal information to collect data about them.

The more you practice, the further you’ll be able to hone your queries to pinpoint different types of websites, pages, and vulnerabilities. Again, I need to caution you not to use these queries to attack another website because that would be illegal and could get you into a lot of trouble. Still, Google Dorks are a great way to locate hidden information on the web, which is why hackers love to use them to find security flaws in websites.

If you want to dig into some more queries, there are some great [Google Dork resources](http://www.google-dorking.com/) on the web