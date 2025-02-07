# 🛡️ Setting Up Parrot OS for a Cybersecurity Lab

## 📌 Overview
This project documents my process for the **installation and configuration** of **Parrot Security OS** on a **Raspberry Pi 5**, designed as a **lightweight but powerful home/portable cybersecurity lab**.

---

## 🖥️ Hardware Requirements

- **Raspberry Pi 5 (4GB/8GB RAM recommended)** — *I bought the 8GB model* [Found Here]
- **1TB SSD (USB-C or SATA Adapter preferred for performance)** — *I’m using the Crucial X9 1TB External USB-C SSD* [Found Here]
- **Official Raspberry Pi 5 Power Supply** — *Included in the Raspberry Pi 5 Kit* [Linked Above]
- **Wireless Keyboard & Mouse** — *I’m using the Rii RT-RKM709, which uses a single USB dongle for both* [Found Here]
- **Ethernet Cable or Wi-Fi Dongle** *(for networking)*
- **MicroSD Card (16GB or larger)** — *Optional if booting from microSD; this is included in the Max Kit if purchased* [Found Here]

---

## 📦 Software Requirements

- **Parrot Security OS (ARM Edition)** — [Download Here](https://www.parrotsec.org/)
- **Raspberry Pi Imager or Balena Etcher** — [Download Here](https://www.raspberrypi.com/software/)
- **Essential Cybersecurity Tools:**
  - 🛠️ *Metasploit*  
  - 🌐 *Nmap*  
  - 📊 *Wireshark*  
  - 🔐 *John the Ripper*  
  - 🕵️‍♂️ *Burp Suite*  
  - 📡 *Aircrack-ng*  
  - 🗃️ *Cowrie Honeypot*  
- **Languages for Automation:** *Python* & *Bash*
- **Virtualization:** *Docker & Virtualization Tools*
- **Remote Access Tools:** *SSH* & *VNC*

---

## 🔥 Installation Steps

### 1️⃣ Flashing Parrot OS onto SSD

1. **Download** Parrot OS (ARM Edition) from the [Parrot Security OS](https://www.parrotsec.org/) website.  
   - Navigate to: `IoT → Raspberry Pi → Security → Download`
2. **Connect Your SSD** to the Raspberry Pi 5:
   - Use a **USB to USB-C cable**:  
     - **USB-C** plugs into the Crucial SSD  
     - **USB** plugs into the **blue USB 3.0 port** on the Raspberry Pi
3. **Flash the OS Image**:
   - Open the **Raspberry Pi Imager** (found in the Raspberry Pi OS menu).
   - Select the Parrot OS image and flash it onto the SSD.
4. **Insert the SSD** (if using a separate computer to flash, connect the SSD to the Pi afterward).
5. **Boot the Raspberry Pi**:
   - *Note:* Mine booted automatically from the Crucial SSD when I **removed the SD card** containing Raspberry Pi OS.
6. **Access the Boot Menu (if needed):**
   - Press the **space bar repeatedly** while the Raspberry Pi boots to open the boot menu.
   - Select the boot device: **SD card, NVMe, or external SSD**.

---

## ⚠️ **Important Security Warning**

> 🔒 **BEFORE performing any cybersecurity or penetration testing work:**  
>  
> Ensure that your system is properly **secured**. This includes:  
> 
> - **Removing default usernames**  
> - **Hardening your system** (a best practice in cybersecurity)  
> - **Setting up a firewall (e.g., UFW or iptables)**  
> - **Changing default ports for services**  
> - **Installing antivirus and monitoring tools**

Failure to secure your environment can expose your system to vulnerabilities. Always follow **best practices for cybersecurity hardening** before engaging in testing activities.

---

