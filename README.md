# Task 1 – Local Network Port Scanning

## Objective
To scan my local network (10.38.91.0/24) using Nmap to identify active hosts, discover open ports, and understand network exposure from a cybersecurity perspective.

## Tools Used
- Kali Linux (Virtual Machine)
- Nmap
- xsltproc (for XML → HTML report conversion)
- Screenshot tool (Kali Snipping Tool / gnome-screenshot)

## My IP Range
Identified using the `ip a` command:

- My IP: 10.38.91.169/24  
- Network Range: **10.38.91.0/24**

This range was used for the scanning process.

## Commands Used
ip a > ip_output.txt
sudo nmap -sS 10.38.91.0/24 -oN scan.txt


## Files Included in This Repository
- `scan.txt` — Main Nmap scan result    
- `ip_output.txt` — Output of the `ip a` command  
- `screenshots/`  
  - `ip.png` (IP address screenshot)  
  - `nmap.png` (Nmap scan screenshot)  
- `README.md` (this file)

---

# 📊 Findings (Based on scan.txt)

Nmap scanned the full subnet **10.38.91.0/24** and found **3 active hosts**.

### ### 1️⃣ Host: 10.38.91.46
- Status: Up  
- **Open Port:**
  - 53/tcp → DNS (domain service)
- Interpretation:  
  Likely a DNS server or router providing DNS services.

---

### ### 2️⃣ Host: 10.38.91.55
- Status: Up  
- All ports filtered (firewall blocking scan)  
- Interpretation:  
  Device is hardened with strict firewall rules.

---

### ### 3️⃣ Host: 10.38.91.169 (My Kali VM)
- Status: Up  
- All scanned ports closed  
- Interpretation:  
  No services exposed — secure by default.

---

# 🛡 Security Risks Identified

### 1. Open DNS Port (53) on 10.38.91.46
- DNS services can be vulnerable to:
  - DNS amplification attacks  
  - Cache poisoning  
  - Misconfiguration-based leaks  
- Should be protected with:
  - Firewall restrictions  
  - Access control  
  - Rate limiting  

### 2. Filtered Ports on 10.38.91.55
- Filtered ports are not a vulnerability by themselves  
- But they indicate:
  - The device may be hiding services  
  - Could be a firewall, IoT device, or security appliance  

### 3. My Kali Machine (10.38.91.169)
- No open ports detected  
- This is good: reduced attack surface  

---

## 📌 Conclusion
This task helped me understand:
- How to perform a TCP SYN scan using Nmap  
- How to detect active hosts in a network  
- How to interpret open, filtered, and closed ports  
- What security risks are associated with exposed network services  

This strengthens fundamental cybersecurity skills in reconnaissance and network security assessment.

