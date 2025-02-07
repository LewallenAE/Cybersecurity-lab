# 🦈 Wireshark Permission Setup on Parrot OS

This guide outlines the steps to configure Wireshark with proper permissions on Parrot OS without running it as the root user.

## 📋 Prerequisites
- Parrot OS installed
- `sudo` privileges
- Wireshark installed

---

## ⚙️ Step 1: Verify or Create the `wireshark` Group and add the current user.
Check if the `wireshark` group exists:<br>
getent group wireshark

![Capture 1](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2001.png)

If it doesn't exist, create it:<br>
sudo groupadd wireshark
![Capture 2](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2001.png)<br><br><br>

## 👤 Step 2: Add a User to the wireshark Group
The following code will add the current user you are logged into to the group.<br>
sudo usermod -aG wireshark $USER
![Capture 3](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2001.png)<br><br><br>

## Step 3: Adjust Permissions for dumpcap.
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 750 / user/bin/dumpcap<br>

**Note**<br>
750 7 gives read, write, and execute priviledges to the Owner, 5 gives read and execute priviledges to the group, and 0 means no rights to others.
![Capture 3](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2003.png)
sudo setcap cap_net_raw, cap_net_admin=eip /usr/bin/dumpcap
<br><br><br>
## Step 4: Verify that lipcap2-bin is installed and verify the capabilities
sudo apt install libcap2-bin<br>

![Capture 4](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2004.png)<br>
getcap /usr/bin/dumpcap

If the command isn't found:
sudo find / -name getcap 2>/dev/null   (this might take a bit to complete)

Add getcap to the system path:

export PATH=$PATH:/usr/sbin
echo 'export PATH=$PATH:/usr/sbin' >> ~/.bashrc
source ~/.bashrc

Verify again:
getcap /usr/bin/dumpcap

Expected output should be:
/usr/bin/dumpcap cap_net_admin, cap_net_raw=eip

Sometimes when exiting the terminal when going back into wireshark it doesn't display eth0 or wlan etc. (Shown in the last screenshot) In this case you might have to type newgrp wireshark (hit enter) and then wireshark (hit enter) (in the terminal) and it should show eth0.<br>
It's possible that the user permissions are not saving and this requires logging out of the user and rebooting. If you have issues my contact information is on the front page.<br><br><br>
![Capture 5](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2005.png)
![Capture 6](screenshots/Wire_Shark_Permission_Setup/Wireshark%20Permission%20Setup%2006.png)
