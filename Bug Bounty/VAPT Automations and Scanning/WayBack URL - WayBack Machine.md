==Note:== setup chrome extension for way back machine for easy use

Tuotrial for wayback url: https://www.geeksforgeeks.org/waybackurls-fetch-all-the-urls-that-the-wayback-machine-knows-about-for-a-domain/

```
waybackurls example.com | tee urls.txt

```


WayBack Machine: [http://wayback.archive.org/](http://wayback.archive.org/)




## Introduction

In this blog we will be covering **Waybackurls For Hackers** . **Web crawling** is a crucial component in the field of security testing. This procedure involves employing automated scripts or crawling **programmes** to index data on web pages. These scripts—also referred to as **web crawlers**, **spiders**, **spider bots**, or just **crawlers**—are essential for identifying security flaws and evaluating a web domain’s level of protection.

![](https://hackingblogs.com/wp-content/uploads/2024/05/urls.jpg)

Waybackurls For Hackers

## Understanding Web Crawling

Scanning the web in a methodical manner to gather data from **webpages** and index it for different uses is called **web crawling**. Recursively retrieving stuff, it organises it for analysis, and it does this by following hyperlinks. Web crawling helps find possible points of entry, weak points, and places that could be exploited in security testing.

## Importance in Security Testing

Web crawling is a **fundamental** method for **reconnaissance** and **vulnerability evaluation** in the context of security testing. It assists in locating potential security holes, hidden pathways, and breaches of sensitive data by methodically navigating web domains. By using automated scripts and crawling **programmes**, security experts may quickly collect information and evaluate the target domain’s risk profile.

## Installation of Waybackurls For Hackers on Kali Linux Machine

We will use the Waybackurls tool on a Kali Linux system to harness the power of web crawling in vulnerability testing. Observe these procedures to install it:

**Step 1:** Verify Golang Installation

![Waybackurls For Hackers](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-132431-1024x641.png)

Waybackurls For Hackers

```
go version
```

**Step 2:** Install Waybackurls

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133003.png)

Waybackurls For Hackers

```
sudo go install github.com/tomnomnom/waybackurls@latest
└─$ sudo cp go/bin/waybackurls /usr/local/bin/.
```

**Step 3:** Explore Tool’s Functionality

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133434.png)

Waybackurls For Hackers

```
waybackurls -h
```

## Working with Waybackurls Tool

_Example 1: Simple Scan_

Let’s initiate a basic scan using Waybackurls:

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133629-1024x635.png)

Waybackurls For Hackers

```
waybackurls hackingblogs.com
```

This command will collect all possible Wayback URLs from the target domain and display them in the terminal.

_Example 2: Using -no-subs Tag_

To restrict URLs to the main domain, use the following command:

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133830-1024x641.png)

Waybackurls For Hackers

```
echo "hackingblogs.com" | waybackurls -no-subs
```

This command ensures that only URLs directly associated with the main domain are fetched, excluding subdomains.

_Example 3: Using -dates Tag_

For obtaining the dates of URL fetches, employ the -dates tag:

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133851-1024x638.png)

Waybackurls For Hackers

```
echo "hackingblogs.com" | waybackurls -dates
```

This command displays the fetching dates of URLs, providing insights into historical data availability.

_Example 4: Using -get-versions Tag_

o retrieve versions of URLs along with their sources, utilize the -get-versions tag:

![](https://hackingblogs.com/wp-content/uploads/2024/05/Screenshot-2024-05-12-133958-1024x644.png)

Waybackurls For Hackers

```
echo "hackingblogs.com" | waybackurls -get-versions
```

This command provides additional context by indicating the sources from which URLs were crawled.

## FAQs

1. **What is the significance of web crawling in security testing?**  
    Web crawling facilitates the systematic discovery of vulnerabilities, sensitive information leaks, and potential security gaps in web domains.
2. **Is Waybackurls suitable for all operating systems?**  
    Waybackurls is primarily developed for Golang environments; thus, it’s compatible with various operating systems, including Linux, macOS, and Windows.
3. **Can Waybackurls be integrated into automated security testing pipelines?**  
    Yes, Waybackurls can be integrated into automated testing pipelines to streamline reconnaissance and vulnerability assessment processes.
4. **Is it legal to use Waybackurls for reconnaissance purposes?  
    **It is important to use Waybackurls responsibly and ensure that you have permission to conduct reconnaissance on the target domain before using the tool.
5. **Can Waybackurls be used to discover hidden subdomains of a target domain?**  
     Yes, Waybackurls can help uncover hidden subdomains that may not be easily accessible through traditional methods.
6. **Are there any limitations to using Waybackurls for hacker commands?**  
    The effectiveness of Waybackurls may be limited by the availability of archived URLs on the Wayback Machine and the accuracy of the results.

## Conclusion

A key tool for security testing is web crawling, which makes comprehensive reconnaissance and vulnerability assessment possible. Security experts may systematically examine web domains, find historical data, and spot possible security threats by utilising tools like Waybackurls. By incorporating web crawling into security testing processes, security assessments become more effective, which in turn strengthens digital ecosystems’ resistance to cyberattacks.


# chatgpt

  
**Setting Up and Using Wayback URLs for Crawling**

- **Wayback Machine** (https://web.archive.org/) stores historical snapshots of websites.
- Used to **crawl** past versions of a target domain to identify endpoints, pages, and parameters that may no longer be publicly accessible but still exist in the backend.
- Helps in **enumerating hidden endpoints** and reconstructing the application’s previous attack surface for potential vulnerabilities.

**Collecting Potential Targets from Crawled Data**

- Extract **endpoints, directories, and parameters** from archived versions of the site.
- Identify possible injection points, outdated or unpatched functionalities, and internal pages that were previously exposed.
- Use tools like **gau (GetAllURLs)**, **waybackurls**, and **katana** for automated collection.

**Using SQLmap for SQL Injection Testing**

- SQLmap is an automated tool to detect and exploit **SQL injection vulnerabilities**.
- Targets the URLs obtained from Wayback Machine to check if any archived endpoints are vulnerable.
- **Challenge:** Due to Web Application Firewall (WAF), SQLmap requests are getting filtered, preventing direct exploitation.

**Web Application Firewall (WAF) Bypassing Challenges**

- WAFs detect and block malicious SQL queries, making SQL injection testing harder.
- Possible **bypasses**:
    - Using **tamper scripts** in SQLmap (`--tamper=space2comment` etc.).
    - Encoding payloads (`--hex`, `--base64`).
    - Using time-based techniques (`--technique=T`).
    - Sending requests through **burp collaborator** or using **DNS-based exfiltration**.

**Setting Up FFUF for Fuzzing**

- **FFUF (Fuzz Faster U Fool)** is a fast web fuzzer used to brute-force directories, parameters, and files.
- Helps in **discovering hidden or unlinked resources** on BNHS systems.
- Can send **malformed or abnormal data** to test how the application behaves under unexpected inputs. 

**Fuzzing BNHS Website and Applications**

- Sending unexpected inputs to find vulnerabilities such as:
    - **Directory traversal** (`../../etc/passwd`)
    - **XSS injection points** (`<script>alert(1)</script>`)
    - **Command Injection** (`; cat /etc/passwd`)
- Helps in identifying security weaknesses that developers may have overlooked.

**Exploring the Wayback Machine for Additional Intelligence**

- Identifying **past site versions**, removed pages, and outdated functionalities.
- Finding previously **leaked API keys, internal admin panels, or exposed credentials**.
- Testing if **previously vulnerable endpoints** still exist in some form in the current application.

### **Next Steps**

- Refine SQLmap techniques to bypass WAF.
- Continue fuzzing with FFUF to identify more attack vectors.
- Investigate additional sources like **JS files, GitHub leaks, and Google Dorks** to expand the attack surface.
- Review and document findings for further security improvements.