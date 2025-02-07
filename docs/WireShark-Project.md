# 📡 Capturing Packets in Wireshark Using Various Filters

## 🔄 Loopback
### 1️⃣ Loopback (lo)
Loopback (lo) refers to packets that a machine sends to itself. Here, I selected `eth0` to capture packets from the Ethernet port.  
![Capture 1](screenshots/Wireshark%20Project%2001.png)

### 2️⃣ Starting the Capture
Click the **Blue Shark Fin** (now grey in the black circle) to start capturing packets.  
![Capture 2](screenshots/Wireshark%20Project%2002.png)

### 3️⃣ Stopping the Capture
Click the **Red Stop Button** (now grey) to stop capturing. If we don’t stop the capture, we can’t save it as a file.  
![Capture 3](screenshots/Wireshark%20Project%2003.png)

### 4️⃣ Saving the Capture
Click the **Save** icon to store the captured packets as a file.  
![Capture 4](screenshots/Wireshark%20Project%2004.png)

### 5️⃣ Opening Saved Captures
Go to **File → Open**, choose your file, and click "Open."  
![Capture 5](screenshots/Wireshark%20Project%2005.png)

---

## 📊 Using Display Filters

### 6️⃣ Filtering by Port
Using the filter `tcp.port == 443` displays only HTTPS (encrypted HTTP) packets.  
![Capture 6](screenshots/Wireshark%20Project%2006.png)

### 7️⃣ TCP Handshake - Client Hello
Packet from IP `52.250.42.157` shows "Client Hello," part of the TCP handshake process.  
![Capture 7](screenshots/Wireshark%20Project%2007.png)

### 8️⃣ Identifying Traffic Sources
Entering the IP address in a browser redirects to **DuckDuckGo**.  
![Capture 8](screenshots/Wireshark%20Project%2008.png)

### 9️⃣ Inspecting Packet Details
Double-clicking the packet reveals source MAC (`Raspberr_81:e0:3e`), source IP, and destination IP.  
![Capture 9](screenshots/Wireshark%20Project%2009.png)

---

## 🌍 IPv6 Traffic Analysis

### 🔟 Capturing IPv6 Packets
Visiting `http://Cygwin.com` shows an IPv6 address (`2620:52:3:1:0:246e`), using colons instead of dots like IPv4.  
![Capture 10](screenshots/Wireshark%20Project%2010.png)

### 1️⃣1️⃣ Recently Opened Files
Wireshark displays recently saved captures upon reopening.  
![Capture 11](screenshots/Wireshark%20Project%2011.png)

### 1️⃣2️⃣ Content Delivery Network (CDN)
Capture of **TryHackMe** shows IPv6, hidden via **Cloudflare CDN** for DDoS protection.  
![Capture 12](screenshots/Wireshark%20Project%2012.png)

### 1️⃣3️⃣ Searching with IPv6
Entering the IPv6 address only returns search results.  
![Capture 13](screenshots/Wireshark%20Project%2013.png)

### 1️⃣4️⃣ CDN Effects on Accessibility
TryHackMe is referenced in search results but inaccessible directly via IP due to CDN protection.  
![Capture 14](screenshots/Wireshark%20Project%2014.png)

---

## 🔍 Advanced Filtering Techniques

### 1️⃣5️⃣ Filtering "Client Hello"
Using `tls.handshake.type == 1` filters for **"Client Hello"** packets.  
![Capture 15](screenshots/Wireshark%20Project%2015.png)

### 1️⃣6️⃣ Combining Filters with OR
Filter: `tls.handshake.type == 1 || ip.addr == 192.168.1.46` shows either condition.  
![Capture 16](screenshots/Wireshark%20Project%2016.png)

### 1️⃣7️⃣ Excluding Packets with NOT (!)
Filter: `!(tls.handshake.type == 1) || ip.addr == 192.168.1.46` excludes "Client Hello" but includes specified IP.  
![Capture 17](screenshots/Wireshark%20Project%2017.png)

### 1️⃣8️⃣ Complex Filtering
Filter: `!(tls.handshake.type == 1) && (tcp.port == 443 || tcp.port == 80)` filters out "Client Hello" and shows HTTP/HTTPS traffic.  
![Capture 18](screenshots/Wireshark%20Project%2018.png)

### 1️⃣9️⃣ Focusing on Port 80 (IPv6)
Filter: `tcp.port == 80` captures HTTP traffic with IPv6 addresses.  
![Capture 19](screenshots/Wireshark%20Project%2019.png)

### 2️⃣0️⃣ Port 80 (IPv4)
Same filter as above but showing IPv4 traffic captured later.  
![Capture 20](screenshots/Wireshark%20Project%2020.png)

---

## 🧪 Combining Filters for Deeper Insights

### 2️⃣1️⃣ HTTP/HTTPS Traffic (Including Handshake)
Shows both port 80 and 443 without excluding "Client Hello."  
![Capture 21](screenshots/Wireshark%20Project%2021.png)

### 2️⃣2️⃣ Adding IP Filters
Filter: `(tcp.port == 80 || tcp.port == 443) && ip.addr == 192.168.1.46` filters traffic from/to a specific IP.  
![Capture 22](screenshots/Wireshark%20Project%2022.png)

### 2️⃣3️⃣ Excluding Specific IP
Filter: `(tcp.port == 80 || tcp.port == 443) && !(ip.addr == 192.168.1.46)` excludes packets related to that IP.  
![Capture 23](screenshots/Wireshark%20Project%2023.png)

---

## ✅ Conclusion
Wireshark offers powerful filtering capabilities to analyze network traffic effectively. By combining various filters, you can narrow down the data to specific protocols, IPs, and packet types, aiding in cybersecurity investigations and network troubleshooting. 🚀
