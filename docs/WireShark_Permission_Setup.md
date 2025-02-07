# 🚈 Wireshark Permission Setup on Parrot OS

This guide outlines the steps to configure Wireshark with proper permissions on Parrot OS without running it as the root user.

---

## 📋 Prerequisites
- Parrot OS installed
- `sudo` privileges
- Wireshark installed

---

## ⚙️ Step 1: Verify or Create the `wireshark` Group and Add the Current User

Check if the `wireshark` group exists:
```bash
getent group wireshark
```
![Capture 1](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2001.png)

If it doesn't exist, create it:
```bash
sudo groupadd wireshark
```
![Capture 2](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2002.png)

---

## 👤 Step 2: Add a User to the `wireshark` Group

To add the current logged-in user to the group:
```bash
sudo usermod -aG wireshark $USER
```
In this example, I’ve added the user `pi`:
```bash
sudo usermod -aG wireshark pi
```
![Capture 3](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2003.png)

---

## 🗂️ Step 3: Adjust Permissions for `dumpcap`

Change the group ownership to `wireshark`:
```bash
sudo chgrp wireshark /usr/bin/dumpcap
```

Set the correct permissions:
```bash
sudo chmod 750 /usr/bin/dumpcap
```

**Note:**  
- **7** gives read, write, and execute permissions to the owner.  
- **5** gives read and execute permissions to the group.  
- **0** means no permissions for others.

![Capture 4](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2004.png)

Grant necessary capabilities:
```bash
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
```

---

## 🗒️ Step 4: Verify `libcap2-bin` is Installed and Check Capabilities

Ensure `libcap2-bin` is installed:
```bash
sudo apt install libcap2-bin
```
![Capture 5](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2005.png)

Verify `dumpcap` capabilities:
```bash
getcap /usr/bin/dumpcap
```

If `getcap` is not found:
```bash
sudo find / -name getcap 2>/dev/null
```
*(This may take a while to complete.)*

Add `getcap` to the system path if needed:
```bash
export PATH=$PATH:/usr/sbin
echo 'export PATH=$PATH:/usr/sbin' >> ~/.bashrc
source ~/.bashrc
```

Verify again:
```bash
getcap /usr/bin/dumpcap
```

**Expected Output:**
```bash
/usr/bin/dumpcap cap_net_admin,cap_net_raw=eip
```

---

## ⚡ Common Issue: Interfaces Not Displaying

Sometimes, after closing the terminal, Wireshark may not display interfaces like `eth0` or `wlan0`.

### ✅ **Fix:**
```bash
newgrp wireshark
wireshark
```

If this issue persists, it might require logging out and rebooting to ensure group permissions are fully applied.

For further assistance, my contact information is available on the front page.

---

![Capture 6](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2006.png)
