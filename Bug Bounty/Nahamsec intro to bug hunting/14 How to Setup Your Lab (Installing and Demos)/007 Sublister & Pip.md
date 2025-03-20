


1  
00:00:00,180 --> 00:00:05,760  
The next tool we're going to install is Sublist3r. Some people enjoy using Sublist3r over others. It's

2  
00:00:05,760 --> 00:00:08,400  
an older tool, I believe it comes in Kali Linux.

3  
00:00:08,700 --> 00:00:15,240  
It's a great tool to find a ton of assets and subdomains on an asset when it comes down to

4  
00:00:15,240 --> 00:00:16,010  
doing recon.

5  
00:00:16,090 --> 00:00:18,730  
So we're going to go ahead and look at sublisster(https://github.com/aboul3la/Sublist3r) on GitHub.

6  
00:00:19,080 --> 00:00:20,040  
This is an easy one.

7  
00:00:20,220 --> 00:00:27,930  
All we have to do is create a tools directory (mkdir tools) , go to our tools directory, and clone our GitHub repository. Then we are going to install the dependencies.

8  
00:00:27,930 --> 00:00:32,990  
So we're going to go into the Sublist3r folder, and we're going to say `git clone`.
9  
00:00:44,200 --> 00:00:49,510  
Now that we have our repository cloned, the next thing we want to do is install the
![[Screenshot From 2025-03-20 15-14-12.png]]
10  
00:00:49,510 --> 00:00:50,290  
dependencies.

11  
00:00:50,590 --> 00:00:54,050  
But as soon as I hit enter, it's going to tell us that we don't have `pip` installed.

---
To install **Sublist3r** on a Linux system, you can follow these steps using the terminal:

1. **Clone the Sublist3r GitHub repository:**
    
    First, make sure you have `git` installed. If not, you can install it with:
    
    ```bash
    sudo apt-get install git
    ```

![[Screenshot From 2025-03-20 15-14-12.png]]
    Then, clone the Sublist3r repository from GitHub:
    
    ```bash
    git clone https://github.com/aboul3la/Sublist3r.git
    ```
    
2. **Navigate to the Sublist3r directory:**
    
    ```bash
    cd Sublist3r
    ```
    

### Option 1: Using a Virtual Environment (Recommended)

This approach avoids modifying the system Python installation and ensures that the dependencies are isolated.

1. **Create a Virtual Environment**: Run the following command to create a virtual environment for Sublist3r:
    C:\home\kali\Tools\Sublist3r>
    ```bash
    python3 -m venv sublist3r-venv
    ```
    
2. **Activate the Virtual Environment**: To activate the virtual environment, use the following command:
    
    ```bash
    source sublist3r-venv/bin/activate
    ```
    
3. **Install the Dependencies**: Now that you're inside the virtual environment, run the following command to install the required dependencies for Sublist3r:
    
    ```bash
    pip install -r requirements.txt
    ```
    
4. **Run Sublist3r**: After the dependencies are installed, you can run Sublist3r as follows:
    
    C:\home\kali\Tools\Sublist3r> python sublist3r.py -d example.com

    ```bash
    python sublist3r.py -d example.com
    ```
    C:\home\kali\Tools\Sublist3r>  python sublist3r.py -d example.com
    Replace `example.com` with the domain you want to scan for subdomains.
    
5. **Deactivate the Virtual Environment** (When you're done): To exit the virtual environment, simply run:
    
    ```bash
    deactivate
    ```
    

That's it! You've installed and run Sublist3r on your Linux machine.

---
12  
00:00:54,070 --> 00:01:01,030  
So what we're going to do is type in `apt install python3-pip`, and that's going

13  
00:01:01,030 --> 00:01:08,800  
to install it for us. `pip` helps us install dependencies for Python tools, as long as they give us

14  
00:01:08,800 --> 00:01:12,670  
the `requirements.txt`, which most tools nowadays come with.

15  
00:01:13,510 --> 00:01:17,170  
Now that we have `pip` installed, we're going to go in here, type in `pip3` because we're on Python

16  
00:01:17,170 --> 00:01:18,920  
3, and we're going to have it install

17  
00:01:18,920 --> 00:01:22,570  
the requirements for this tool to work.

18  
00:01:22,570 --> 00:01:25,710  
Now that we have it done, we're going to run `python3 sublist3r.py`.

19  
00:01:26,090 --> 00:01:29,050  
This is going to come back and ask us to give it some arguments.

20  
00:01:29,630 --> 00:01:34,020  
If you're not familiar with Sublist3r, I highly recommend looking at the help documentation.

21  
00:01:34,270 --> 00:01:39,280  
This will tell you how it's used, but it's pretty basic. If you're doing brute-forcing, which is up

22  
00:01:39,280 --> 00:01:39,650  
to you,

23  
00:01:39,670 --> 00:01:44,140  
I personally don't use brute force, but if I have a good dictionary, I'll make sure to link some word

24  
00:01:44,470 --> 00:01:48,970  
lists and dictionary lists in the resources you can use because it's open source.

25  
00:01:49,270 --> 00:01:53,440  
You can configure it to use brute force for subdomains, or you can just leave it blank.

26  
00:01:53,680 --> 00:01:57,700  
But the biggest one is to make sure you give it a `-d` option, which is the domain you want to target.

27  
00:01:57,880 --> 00:01:58,450  
For this case,

28  
00:01:58,460 --> 00:02:05,590  
we're going to type in `noharmsector.training`, and we want to run this.

29  
00:02:05,590 --> 00:02:08,800  
If there's anything out there for `noharmsector.training`, it's going to come back.

30  
00:02:09,100 --> 00:02:11,050  
The good thing about this is it's going to search through Baidu, Yahoo!

31  
00:02:11,050 --> 00:02:13,540  
Google, Bing, Ask, and a bunch of different sources, and it's going to give us a list of subdomains.

32  
00:02:13,540 --> 00:02:19,750  
Unfortunately, there isn't much out there.

33  
00:02:19,810 --> 00:02:20,280  
Let's try a smaller target.

34  
00:02:20,290 --> 00:02:21,980  
We're going to try HackerOne just to make it easy.

35  
00:02:27,010 --> 00:02:31,210  
It's going to do the same thing, and it's going to give us some domains.

36  
00:02:31,450 --> 00:02:34,060  
As expected, it came back and gave us some domains.

37  
00:02:34,300 --> 00:02:39,430  
We have `api.hackerone.com`, `docs.hackerone.com`, `events.hackerone.com`, and so on.

38  
00:02:39,640 --> 00:02:40,390  
It's a great tool.

39  
00:02:40,390 --> 00:02:45,550  
It uses a bunch of open-source or free resources and gives you a list of potential subdomains.

40  
00:02:45,700 --> 00:02:50,890  
You can also have it do some scanning, a lot of people like to use Nmap instead.

41  
00:02:51,160 --> 00:02:56,290  
But if you want to look for particular ports, you can also do that. To make it faster,

42  
00:02:56,290 --> 00:03:02,020  
if you're doing a large target, I highly recommend using threads and specifying a number so that

43  
00:03:02,020 --> 00:03:08,440  
the program runs a lot faster and gives you results more quickly.

