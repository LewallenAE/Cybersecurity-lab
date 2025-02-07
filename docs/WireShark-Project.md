# Capturing Packets In WireShark Using Various Filters

## Loopback<br>
### 1. Loopback (lo) are packets that a machine sends to itself. 
![Capture 1](screenshots/Wireshark%20Project%2001.png)


### 2. We click the Blue Shark Fin (In the Black circle it is now grey) to start a capture.
![Capture 2](screenshots/Wireshark%20Project%2002.png)


### 3. We click the Red Stop Button (now grey) to stop the capture. If we do not stop the capture then we cannot save the capture as a file.
![Capture 3](screenshots/Wireshark%20Project%2003.png)


### 4. We click here to save the capture as a file.
![Capture 4](screenshots/Wireshark%20Project%2004.png)


### 5. Once saved we can go to File -> Open and then choose the file we want and click "open".
![Capture 5](screenshots/Wireshark%20Project%2005.png)



### 6. By opening our saved packet capture. We can display filter. Here we have used tcp.port==443 to only show packets that have gone through port 443 which is the HTTPS (Hypertest Transfer Protocol Secure). An encrypted version of HTTP.
![Capture 6](screenshots/Wireshark%20Project%2006.png)



### 7. IP Address 52.250.42.157 is says "Client Hello" under "Info". This is a part of the handshake process for TCP protocols. As we can see it says TCP under "Protocol".
![Capture 7](screenshots/Wireshark%20Project%2007.png)



### 8. After entering the IP address into the search bar, we see that it takes us to the Duck Duck Go search engine page.
![Capture 8](screenshots/Wireshark%20Project%2008.png)



### 9. Double clicking the packet shows more information. Here we see that it shows the Src: Raspberr_81:e0:3e which is the mac address. There is also the Src: IP address (The IP for the Raspberry Pi device) and teh Destination address. (The Duck Duck Go address).
![Capture 9](screenshots/Wireshark%20Project%2009.png)



