# Capturing Packets In WireShark Using Various Filters

## Loopback<br>
### 1. Loopback (lo) are packets that a machine sends to itself. Here I seleect eth0 for the ethernet port to capture packets from the ethernet port.
![Capture 1](screenshots/Wireshark%20Project%2001.png)


### 2. Clicking the Blue Shark Fin (In the Black circle it is now grey) to start a capture.
![Capture 2](screenshots/Wireshark%20Project%2002.png)


### 3. Clicking the Red Stop Button (now grey) to stop the capture. If we do not stop the capture then we cannot save the capture as a file.
![Capture 3](screenshots/Wireshark%20Project%2003.png)


### 4. Click the icon in the circle to save the capture as a file.
![Capture 4](screenshots/Wireshark%20Project%2004.png)


### 5. Once saved we can go to File -> Open and then choose the file we want and click "open".
![Capture 5](screenshots/Wireshark%20Project%2005.png)



### 6. By opening our saved packet capture. We can display filter. Here we have used tcp.port==443 to only show packets that have gone through port 443 which is the HTTPS (Hypertext Transfer Protocol Secure). An encrypted version of HTTP.
![Capture 6](screenshots/Wireshark%20Project%2006.png)



### 7. IP Address 52.250.42.157 is says "Client Hello" under "Info". This is a part of the handshake process for TCP protocols. As we can see it says TCP under "Protocol".
![Capture 7](screenshots/Wireshark%20Project%2007.png)



### 8. After entering the IP address into the search bar, we see that it takes us to the Duck Duck Go search engine page.
![Capture 8](screenshots/Wireshark%20Project%2008.png)



### 9. Double clicking the packet shows more information. Here we see that it shows the Src: Raspberr_81:e0:3e which is the mac address. There is also the Src: IP address (The IP for the Raspberry Pi device) and teh Destination address. (The Duck Duck Go address).
![Capture 9](screenshots/Wireshark%20Project%2009.png)



### 10. Here I've gone to http://Cygwin.com. This one is showing an IPv6 address signified by the 2620:52:3:1:0:246e. Whereas an IPv4 address is as above the 52.250.42.157.
![Capture 10](screenshots/Wireshark%20Project%2010.png)


### 11. After closing and reopening Wireshark, you can see a list of recently saved packet captures.
![Capture 11](screenshots/Wireshark%20Project%2011.png)



### 12. This is a capture of the TryHackMe website. Here it shows yet another IPv6 address. Notice in the next picture that when entering the IPv6 address we are not able to directly go to the website. This is because the IPv6 address is hosted via CloudFlare. This is a way to "hide" the actual IP adress and is called a (CDN) Content Delivery Network. This is a part of a layered security approach.<br>
It really helps against DDoS attacks as if someone tried to do a DDoS attack on CloudFlare it would just be shrugged off since CloudFlare can handle literally ***TeraBits*** of information and that's **PER SECOND** mind you.
![Capture 12](screenshots/Wireshark%20Project%2012.png)




### 13. I've put the IPv6 address into the search bar.
![Capture 13](screenshots/Wireshark%20Project%2013.png)



### 14. We see it only pulls up a search. But TryHackMe is referenced in two instances retrieved from the search.
![Capture 14](screenshots/Wireshark%20Project%2014.png)



### 15. tls.handshake.type==1 filters for the "Client Hello" info, meaning when we connect to the client destination.
![Capture 15](screenshots/Wireshark%20Project%2015.png)



### 16. Here I have added a secondary filter. The filter will show either the tls.handshake.type==1 or it will show ip.addr==192.168.1.46.
![Capture 16](screenshots/Wireshark%20Project%2016.png)



### 17. Adding an exclamation point (!) as in !(tls.handshake.type==1) means "Not that type of info" filtering OUT lines that have "Client Hello" in the info section. Using or we will see ip.addr==192.168.1.46 even if it should have been filtered out by the first condition. Since we use OR and not AND it displays this ip address as well as other addresses that do not meet the first condition.
![Capture 17](screenshots/Wireshark%20Project%2017.png)



### 18. Here I have used the filter !(tls.handshake.type==1) and (tcp.port==443 or tcp.port==80). This filters OUT any connections with the tls.handshake.type==1 (Client Hello) and only displays connections from either port 443 or port 80 or both (but it can't be sent from both at the same time). 
![Capture 18](screenshots/Wireshark%20Project%2018.png)



### 19. This specifically filters for tcp.port==80 any connections running through port 80. This capture only has IPv6 addressess.
![Capture 19](screenshots/Wireshark%20Project%2019.png)



### 20. This is the same as 19 but it shows IPv4 addresses. It is just later on in the capture meaning the capture had been running for a longer amount of time.
![Capture 20](screenshots/Wireshark%20Project%2020.png)


### 21. This is similar to 18 except this filter does not FILTER OUT the tls handshake (Client Hello). However, it does show packets from port 80 or port 443.
![Capture 21](screenshots/Wireshark%20Project%2021.png)



### 22. Notice here that by adding "and (ip.addr==192.168.1.46) This displays packets coming through port 80 OR port 443 and from the ip address 192.168.1.46. If you look closely you can se that 192.168.1.46 shows in either the Source or Destination Column. You could further filter by using "and ip.src==192.168.1.46" in which it would only show if the src ip address was the one in question.
![Capture 22](screenshots/Wireshark%20Project%2022.png)


### 23. This is the same as 22 except we added an ! before the ip address. So what this shows is it will show packets coming either through port 80 or port 443 and is not displaying any packets that have 192.168.1.46 as a source or destination IP address.
![Capture 23](screenshots/Wireshark%20Project%2023.png)

