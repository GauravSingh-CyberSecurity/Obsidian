
gs.cyber.red@gmail.com
```
@9;K:ytL_2joB6gA5S,84D_]g9wjqw;6
```




Burp suite professional edition licence key Bypass:
---


https://github.com/gt0day/Burp-Suite.git

![[Burp-Suite-main.zip]]
very imp note:-    move/keep the BurpLoaderKeygen.jar and burpsuite_pro_vxxxx.x.jar in the same folder  



Download link for Burp pro: 
https://portswigger.net/burp/pro

https://portswigger.net/burp/releases/professional-community-2024-1-1-6?requestededition=professional&requestedplatform=


```
sudo apt-get upgrade burpsuite 
```



---




Steps to install/update new JAVA version
---

NOTE: the version should be what you are using at the time of updating java

It seems like there might be an issue with the Java installation or configuration. Let's try the following steps to resolve it:

1. Remove the existing JDK 22 installation:

```bash
sudo apt-get purge jdk-22
```

2. Install the JDK 22 package again:

```bash
sudo dpkg -i ~/Downloads/jdk-22_linux-x64_bin.deb
```

3. Set the Java alternatives to the JDK 22 version:

```bash
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-22-oracle-x64/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-22-oracle-x64/bin/javac 1
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk-22-oracle-x64/bin/jar 1
```

4. Set the alternatives to the JDK 22 version:

```bash
sudo update-alternatives --set java /usr/lib/jvm/jdk-22-oracle-x64/bin/java
sudo update-alternatives --set javac /usr/lib/jvm/jdk-22-oracle-x64/bin/javac
sudo update-alternatives --set jar /usr/lib/jvm/jdk-22-oracle-x64/bin/jar
```

5. Check the Java version:

```bash
java -version
```

If you encounter any errors or issues during these steps, please let me know.



Desktop shortcut
---
To create a desktop shortcut for Burp Suite, you can follow these steps:

1. Create a desktop file for Burp Suite:
   ```bash
   nano ~/.local/share/applications/burp-suite.desktop
   ```

2. Add the following content to the file:
```

[Desktop Entry]
   Version=1.0
   Type=Application
   Name=Burp Suite
   Exec=/usr/lib/jvm/jdk-22-oracle-x64/bin/java -jar /home/kali/Burp/BurpLoaderKeygen.jar
   Icon=/home/kali/Burp/i4j_extf_6_1dgj151_jehl3v.png
   Terminal=false
   
```
   Replace `/path/to/BurpLoaderKeygen.jar` with the actual path to `BurpLoaderKeygen.jar` and `/path/to/burp-icon.png` with the path to the Burp Suite icon.

3. Make the desktop file executable:
   ```bash
   chmod +x ~/.local/share/applications/burp-suite.desktop
   ```

Now, you should see the Burp Suite icon on your desktop, and you can launch Burp Suite by double-clicking on it.


chatgpt propmpt i used to help me with doing all this installation of latest burpsuite.
https://chatgpt.com/share/f43cf464-8da8-4b99-b951-8ecc8c5071b2


BurpSuite Extensions
---
Logger++
Autorize