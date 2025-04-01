### ✅ **Step-by-Step Guide: Connect HTB Lab via Your Own Browser**

#### 🟢 **1. Download Your VPN Configuration File:**
1) go here(vpn settings) https://academy.hackthebox.com/vpn
2) Download "VPN connection File"  
3) i downloaded that file here (/home/kali/Documents/Obsidian Vault/Bug Bounty/HTB Bug Bounty hunter/**academy-regular.ovpn** )

#### 🟢 **2. Install OpenVPN (Linux/Windows/Mac):**

- **Linux:**
```
 sudo apt update
sudo apt install openvpn -y
 
```


#### 🟢 **3. Connect to the HTB VPN:**
- **Linux:**
```
sudo openvpn --config /path/to/HTB-username.ovpn

```

actual command that i used :  got to this folder C:\home\kali\Documents\Obsidian Vault\Bug Bounty\HTB Bug Bounty hunter and click "open in terminal" :
```
C:\home\kali\Documents\Obsidian Vault\Bug Bounty\HTB Bug Bounty hunter> sudo openvpn --config academy-regular.ovpn

```
