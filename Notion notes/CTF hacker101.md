# CTF hacker101

- A little something to get you started
    
    [https://medium.com/nerd-for-tech/hacker101-a-little-something-to-get-you-started-walkthrough-46397befe1b](https://medium.com/nerd-for-tech/hacker101-a-little-something-to-get-you-started-walkthrough-46397befe1b)
    
- Micro-CMS v1
    
    [https://medium.com/@isaacwangethi30/hacker101-micro-cms-v1-ctf-walkthrough-c372a9661b91](https://medium.com/@isaacwangethi30/hacker101-micro-cms-v1-ctf-walkthrough-c372a9661b91)
    
    1. **hello<script>alert(1);</script>**
        
        This script is an example of a Cross-Site Scripting (XSS) payload. Here's how it works:
        
        - The payload is injected into the page title when creating a new page on the Micro-CMS v1 platform.
        - The payload itself is **`<script>alert(1);</script>`**. This is JavaScript code that, when executed, displays an alert box with the message "1".
        - When the page is viewed or the user goes back home, the injected script gets executed, and the alert box pops up, indicating a successful XSS attack.
        - In the context of a CTF, discovering and exploiting XSS vulnerabilities often allows attackers to execute arbitrary JavaScript code in the context of other users, potentially stealing session cookies or performing other malicious actions.
    2. **<button onclick=alert(‘xss’)>click</button>**
        
        This script is another example of an XSS payload, but it's using a different approach:
        
        - The payload is injected into the page body when creating or editing a page on the Micro-CMS v1 platform.
        - The payload is **`<button onclick=alert(‘xss’)>click</button>`**. This creates an HTML button element with an **`onclick`** attribute that triggers the **`alert('xss')`** JavaScript code when the button is clicked.
        - The goal here is to bypass any markdown filtering applied to the page body and execute JavaScript directly.
        - However, in this case, the payload itself doesn't display the flag. Instead, the flag is retrieved by viewing the page source code after the payload is executed.
    
    In summary, both scripts leverage XSS vulnerabilities in different parts of the Micro-CMS v1 platform to execute arbitrary JavaScript code. The first script demonstrates XSS in the page title, while the second one attempts to execute JavaScript within the page body using an HTML button element. The flag retrieval in the second case involves inspecting the page source code.
    
- Micro-CMS v2
    
    [https://medium.com/cyberx/ctf-hacker101-micro-cms-v2-f0e32696cdff](https://medium.com/cyberx/ctf-hacker101-micro-cms-v2-f0e32696cdff)
    
    we use error based sql injection manually
    
    username= ' +AND+EXTRACTVALUE(1337,CONCAT(' . ' , ' ~ ' ,(SELECT+group_concat(username, ' , ' ,pa ssword)+FROM+admins),' ~ '))+--+-&password=test
    

## Software is Preventing Firefox From Safely Connecting to This Site how to solve this issue while using burp suite for security practice

**edit**

**Regenerate draftrefresh**

**volume_up**

![https://www.gstatic.com/lamda/images/sparkle_resting_v2_darkmode_2bdb7df2724e450073ede.gif](https://www.gstatic.com/lamda/images/sparkle_resting_v2_darkmode_2bdb7df2724e450073ede.gif)

![https://fonts.gstatic.com/s/e/notoemoji/latest/1f680/emoji.svg](https://fonts.gstatic.com/s/e/notoemoji/latest/1f680/emoji.svg)

**Here are the steps to resolve the "Software is Preventing Firefox From Safely Connecting to This Site" issue when using Burp Suite for security practice:**

**1. Install Burp Suite's CA Certificate:**

- Open Burp Suite and go to the **Proxy** tab.
- In the **Options** tab, click on **Import/export CA certificate**.
- Click **Save** to download the certificate file (cacert.der).
- In Firefox, go to **Preferences** > **Privacy & Security** > **Security**.
- Scroll down to **Certificates** and click **View Certificates**.
- Go to the **Authorities** tab and click **Import**.
- Select the downloaded Burp Suite CA certificate file and click **Open**.
- Check the box to trust this certificate for identifying websites and click **OK**.

**2. Configure Firefox Proxy Settings:**

- In Firefox, go to **Preferences** > **General** > **Network Settings**.
- Select **Manual proxy configuration**.
- In the **HTTP Proxy** field, enter `127.0.0.1`.
- In the **Port** field, enter the port Burp Suite is listening on (usually `8080`).
- Check the box for **Use this proxy server for all protocols**.
- Click **OK** to save the settings.

**3. Intercept and Forward Traffic:**

- In Burp Suite's **Proxy** tab, ensure **Intercept is on**.
- Navigate to the website you want to test in Firefox.
- Burp Suite will intercept the request.
- Review and modify the request as needed.
- Click **Forward** in Burp Suite to send the request to the website.

**4. Bypass HSTS (Optional):**

- If the website uses HTTP Strict Transport Security (HSTS), you might need to clear your browser's HSTS cache or use Burp Suite's **HSTS Override** feature.

**5. Temporarily Disable Antivirus or Firewall Protection (If Necessary):**

- In rare cases, antivirus or firewall software might interfere with Burp Suite's interception. If you encounter issues, temporarily disable these protections for testing purposes.

**6. Handle Mixed Content Warnings (If Occurring):**

- If you see mixed content warnings, consider using Burp Suite's **Match and Replace** feature to replace insecure HTTP content with HTTPS.

**Remember:**

- Always restore Firefox's proxy settings to their default values when you're done with your security testing.
- Use Burp Suite responsibly and ethically, ensuring you have proper authorization for testing websites.