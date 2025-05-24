
# **VoIP PBX Lab: Asterisk + Zoiper + Wireshark Security Analysis**  
*A Raspberry Pi-based VoIP system with traffic monitoring and security testing for aspiring sysadmins/network engineers.*  

  

---

## **Project Overview**  
Built a **VoIP test environment** to:  
- 📞 Set up an **Asterisk PBX server** on Raspberry Pi.  
- 📱 Connect **Zoiper softphone** (on VMware VM) for test calls.  
- 🔍 Analyze **SIP/RTP traffic** with Wireshark for vulnerabilities.  
- 🔒 Implement **iptables firewall rules** to secure VoIP traffic.  

**Skills Demonstrated:**  
`VoIP` `Asterisk` `Wireshark` `Raspberry Pi` `Networking` `Cybersecurity`  

---

## **Hardware/Software Used**  
- **Raspberry Pi 5** (Asterisk PBX server)  
- **VMware Workstation** (Windows/Linux VM for Zoiper)  
- **Zoiper Softphone** ([Download](https://www.zoiper.com))  
- **Alfa Wi-Fi Adapter** (Packet capture)  
- **Wireshark** (Traffic analysis)  

---

## **Step-by-Step Setup**  
### 1. **Install Asterisk on Raspberry Pi**  
```bash
sudo apt update && sudo apt install asterisk -y
```  
Configured SIP extensions in `/etc/asterisk/sip.conf`:  
```ini
[1001]
type=friend
secret=1234
host=dynamic
```  

### 2. **Connect Zoiper on VMware VM**  
- Added SIP account in Zoiper:  
  - **IP:** `[Raspberry Pi's IP]`  
  - **Username:** `1001`  
  - **Password:** `1234`  

### 3. **Capture Traffic with Wireshark**  
- Filtered for SIP/RTP packets:  
  ```plaintext
  sip || rtp
  ```  


### 4. **Security Hardening**  
Blocked unauthorized SIP access via iptables:  
```bash
sudo iptables -A INPUT -p udp --dport 5060 -s [VM_IP] -j ACCEPT
sudo iptables -A INPUT -p udp --dport 5060 -j DROP
```  

---

## **Key Findings**  
- 🔎 **Unencrypted SIP credentials** visible in Wireshark.  
- ⏱️ **Jitter/latency issues** identified in RTP streams.  
- 🛡️ **Firewall rules** effectively blocked rogue SIP requests.  

---

## **Future Enhancements**  
- [ ] Add **ESP32-based intrusion alerts** (LED triggers).  
- [ ] Set up **VPN-secured VoIP** (WireGuard/OpenVPN).  
- [ ] Simulate **SIP flood attacks** for DoS testing.  

---

## **Connect**  
📧 Email: darsansabu09@gmail.com  
🔗 LinkedIn: [Darsan Sabu George](www.linkedin.com/in/darsan-sabu-george)  

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)  
