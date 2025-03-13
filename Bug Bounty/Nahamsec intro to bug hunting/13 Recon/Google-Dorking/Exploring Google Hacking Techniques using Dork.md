
![](https://miro.medium.com/v2/resize:fit:700/1*oAgc1dTS5vorJM5j8fjxHw.png)

# **What is Google Dork?**

It is basically a search string that uses advanced search query to find information that are not easily available on the websites. It is also regarded as illegal google hacking activity which hackers often uses for purposes such as cyber terrorism and cyber theft.

> **Dork**
> 
> They are like search criteria in which a search engine returns results related to your dork.

# **Can Google be used by Hackers to hack websites?**

People often take Google as just a search engine used to find text, images, videos, and news. However, in the infosec world, it has a very vast role. Google can also be used as a very useful hacking tool.

You cannot hack websites directly using Google. But, it’s tremendous web crawling capabilities can be of great help to index almost anything within any websites which includes sensitive information. This can include from username, password and other general vulnerabilities you won’t even be knowing.

Basically, using Google Dorking you can find vulnerabilities of any web applications and servers with the help of native Google Search engine.

> **Important Things To Know**
> 
> Before starting with Google Dork, one needs to be aware that Google knows who you are and when you perform these kinds of activities. Only use these information for legal purposes. Just because the information are open on the internet, do not use it to harm others. Any illegal activity caught on the internet, you will be charged as a cyber criminal. This articles highly influences you to use the information with good intentions.

# Special google search operators

Before starting with google dorks, you need to have basic understanding of few special google search operators and also how it functions.

1. **intitle:**

This will ask google to show pages that have the term in their html title.

**2. inurl:**

Searches for specified term in the URL. **_For example:_** **_inurl:register.php_**

**3. filetype:**

Searched for certain file type. **Example:** **_filetype:pdf_** will search for all the pdf files in the websites.

**4. ext:**

It works similar to filetype. **Example:** **_ext:pdf_** finds pdf extension files.

**5. intext:**

This will search content of the page. This works somewhat like plain google search

**6. site:**

This limits the search to a specific site only. **Example: _site:abc@d.com_** will limit search to only abc@d.com.

**7. Cache:**

This will show you cached version of any website. **Example:** **_cache: aa.com_**

**8. ***

This works like a wildcard. **Example: _How to * sites_**, will show you all the results like _“how to…” design/create/hack, etc… “sites”_

# **Basic Formula of Dork**

"inurl:."domain"/"dorks" "

**Here,**  
**“inurl”** = _input URL_  
**“domain”** = _your desired domain ex. .gov_  
**“dorks”** = _your dork of your choice_

# **Examples of Google Dorking**

_Moving forward, let us explore on few Google Dork examples and how it can be easily used to find private information on the Internet._

1. **Explore LOG Files For Login Credentials**

This is a process to find the .LOG files accidentally exposed on the internet. This is basically a LOG file containing clues about what the credentials to the system might be or various user/ admin accounts that exists in the system.

**Search query to perform the action**

==allintext:password filetype:log after:2019==

When you enter this command in your google search box, you will find list of applications with exposed log files.

**Dork command using two google operators**

You can also use two combined google operators all in text and filetype.

allintext:username filetype:log

The above command with expose you all the results that includes username inside *.log files

> **Recommendation:**
> 
> Website owners must configure a file name robots.txt file properly. It is a must to prevent Google Dorks from accessing important data of your site through a google search. Also, it is very important to keep the plugins up to date.

**2. Explore Configurations Using ENV files**

.env is used by various popular web development frameworks to declare general variables and configurations for local as well as dev environment.

DB_USERNAME filetype:envDB_PASSWORD filetype:enc=v

By using the command you can find list of sites that expose their env file publicly on the internet. Most of the devs inserts their .env file in the main website public directory, which can cause a great harm to their site if gets in hand of any cyber criminals.

If you click into any of the exposed .env file, you will notice unencrypted usernames, passwords and IPs are directly exposed in the search results.

> **Recommendation:**
> 
> Move .env files to somewhere that is not publicly accessible.

**3. Explore Live Cameras**

This sounds a bit creepy but have you ever wondered if your private live camera could be watched by anyone on the internet?

Using Google hacking techniques, you can fetch live camera web pages that are not restricted by IP. If you are creative enough to play with Google Dork, not just view, but you can also to take control of the full admin panel remotely, and even re-configure the cameras as you want to.

Using “top.htm” in the URL with the current time and date, you can find list of live cams that are publicly exposed.

inurl:top.htm inurl:currenttime

Another dork for cameras for list of common live-view page hosted on routers

inurl:”lvappl.htm”

**4. To Explore Open FTP Servers**

The lack of setting access permissions in the FTP can be the direct cause of internal information getting published unintentionally. Even dangerous, if the FTP server is in “Write” status, this can create risk of the server being used as “storage” for computer viruses and illegally copied files.

With the following dork command, you will be able to easily explore the publicly exposed FTP Servers, which can sometimes explore many things.

intitle:"index of" inurl:ftp

In order to search for list of websites that uses HTTP protocol, you can simply type the following dork command.

intitle:"index of" inurl:http after:2018

You can also be more specific and and search for online forums that uses HTTP by simply changing the text in the search title.

intitle:"forum" inurl:http after:2018

**5. Explore Specific websites with specific domains**

Let’s say you want to explore websites or certain organization that has certain domain. You can simply do that by entering the following code:

“inurl:."domain"/”dorks” “

**Example:** _“inurl:.gov/index.php?id=”_

You can use the above example to explore all the list of government sites. You can also replace inurl: with some other google search operators for interesting results.

**6. View most recent Cache**

This can show you the most recent cache of a specified webpage. This can be useful to identify when a page was last crawled.

cache:websitename.com

# **How can Google Dork Cyber Security Enthusiast?**

Google almost indexes everything connected with the internet, which also includes different private informations of misconfigured services. This can often be useful as well as equally harmful at the same time. You need to make sure that do not log in to any of the services, even if the password is exposed, as this could get you into trouble because you don’t have permission.

However, if you have something hosted online, you can use some of the dork commands on your domain just to make sure you did not left anything exposed that hacker can use to get you.

# **Conclusion**

In the second part of the tutorial, I will show you more complicated formulas as well as tips and tricks to find web vulnerabilities.