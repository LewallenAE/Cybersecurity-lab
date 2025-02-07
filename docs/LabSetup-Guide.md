# 🛡️ Setting Up Parrot OS for Cybersecurity Lab

## 📌 Overview

This project documents my process for the installation and configuration of my **Parrot Security OS** on a **Raspberry Pi 5** for use as a lightweight but powerful home / portable cybersecurity lab.

## 🖥️ Hardware Requirements
- **Raspberry Pi 5** (4GB/8GB RAM recommended)  **I bought the 8GB model** - [Found Here](https://www.bestbuy.com/site/canakit-raspberry-pi-5-starter-max-kit-8gb-turbine-white/6580288.p?skuId=6580288)
- **1TB SSD** (USB-C or SATA Adapter preferred for performance)  **I bought the Crucial X9 1TB External USB-C SSD** [Found Here](https://www.bestbuy.com/site/crucial-x9-1tb-external-usb-c-ssd-black/6557871.p?skuId=6557871)
- **Official Raspberry Pi 5 Power Supply** - This is included in the Raspberry Pi 5 Kit Linked Above.
- **Wireless Keyboard & Mouse** - **I bought the Rii RT-RKM709** It uses a single USB Dongle for both the keyboard and mouse. - [Found Here](https://www.amazon.com/Rii-RKM709-Gigahertz-Ultra-Slim-Multimedia/dp/B0DCVT6L91?crid=G9BZH65TSDRB&dib=eyJ2IjoiMSJ9.AIsrf58twlv45VrubqCnlwc85lfKNVBCjQT3f4lITroUM9ZUMS7Gbm8Xgz8Sea-l6jE_Sx5_kcKV5RaxIdDDeJWjERFkE96Ajm6DNcD1-G21PUqd1c1UXRABpIjp9hMDSetSPGCLeKa6ffDI2ngwGed-usTWD3qoM9hKyfGTEiasltLcvxEub86QWp6atJiYvAZDc4VLTPSqKK60gC_xXX6GDkBQwMY1CHFfyUKe8k0.xK6aJwi7CUKkkDXRZPAQ9Jb1GsMJKX28FhZoXHP-C8E&dib_tag=se&keywords=rii%2Brt-rkm709%2Bmini%2Bwireless%2Bkeyboard%2Band%2Bmouse%2Bcombo&qid=1738800403&sprefix=rii%2Brt-rkm709%2Bmini%2Bwireless%2Bkeyboard%2Band%2Bmouse%2Bcombo%2Caps%2C141&sr=8-1&th=1)
- **Ethernet Cable or Wi-Fi Dongle** (for networking) 
- **MicroSD Card (16GB or larger, optional if booting from microSD)**  **THIS COMES WITH THE MAX KIT IF YOU GET THE MAX KIT LINKED ABOVE**

## 📦 Software Requirements
- **Parrot Security OS (ARM Edition)** – [Download Here](https://parrotsec.org/download/)
- **Raspberry Pi Imager or Balena Etcher** – [Download Here](https://www.raspberrypi.com/software/)
- **Essential Cybersecurity Tools**: Metasploit, Nmap, Wireshark, John the Ripper, Burp Suite, Aircrack-ng, Cowrie
- **Python & Bash for Security Automation**
- **Docker & Virtualization Tools**
- **SSH & VNC for Remote Access**

## 🔥 Installation Steps

### 1️⃣ Flashing Parrot OS onto SSD
1. Download **Parrot OS (ARM Edition)** from [Parrot Security OS](https://parrotsec.org/download/).<br>
   a. The option for the Raspberry Pi is **IoT ----> Raspberry Pi ----> Security ----> Download**
2. Plug your SSD into your Raspberry Pi 5. You will have to use a USB to USB-C. The USB-C will plug into the Crucial SSD and the USB you will plug into the Blue (USB 3.0) port on the Raspberry Pi Computer Unit.
3. Once downloaded use the **Raspberry Pi Imager** found in the Raspberry Pi OS menu to flash the OS image onto your SSD.
4. If you used a separate computer from the Raspberry Pi, insert the SSD into the **USB-C or SATA Adapter** on the Raspberry Pi.
5. Boot the Raspberry Pi and follow the installation steps. **Note - Mine installed automatically from the Crucial SSD when I took out the SD card containing the Raspberry Pi OS.
6. If you continually press the space bar while the Raspberry Pi 5 loads, it will produce a boot menu and you can choose whether to boot from SD card, NVMe or external SSD etc.


**WARNING**   
BEFORE DOING ANY CYBERSECURITY OR PENTESTING WORK MAKE SURE THAT YOUR SYSTEM IS SETUP AND SECURED. THERE SHOULD NOT BE A DEFAULT USERNAME.
MAKE SURE THAT "HARDEN" YOUR SYSTEM, A COMMON PRACTICE IN CYBERSECURITY. DO THIS BY SETTING UP A FIREWALL, CHANGING PORTS, AND INSTALLING ANTIVIRUS.
