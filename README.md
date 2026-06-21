# Task 2 — Build Your Personal Cybersecurity Lab

**Internship:** Maincrafts Technology | Cybersecurity Analyst Intern  
**Intern ID:** MT5540  
**Intern:** Duggimpudi Rakshitha  

---

## Objective

Built a safe, isolated cybersecurity practice environment using VirtualBox, Kali Linux, and OWASP Juice Shop — serving as the foundation for all future VAPT and web application testing tasks.

---

## Lab Architecture

```
+------------------------------------------+
|         Host System (Windows 11)         |
|                                          |
|   Virtualization: Oracle VirtualBox 7.x  |
|   ├── Kali Linux (Attacker VM)           |
|   │     Adapter 1: NAT  → Internet       |
|   │     Adapter 2: Host-Only → Lab       |
|   │                                      |
|   └── OWASP Juice Shop (Docker)          |
|         Port 3000 on Host-Only network   |
|                                          |
|   Networks:                              |
|   • NAT       → 10.0.2.0/24             |
|   • Host-Only → 192.168.56.0/24         |
+------------------------------------------+
```

---

## Environment Details

| Component       | Details                              |
|----------------|--------------------------------------|
| Hypervisor      | Oracle VirtualBox 7.x               |
| Attacker VM     | Kali Linux 2024.x                   |
| Target App      | OWASP Juice Shop (Docker)           |
| Attacker IP     | 192.168.56.101 (Host-Only)          |
| Target Port     | localhost:3000                       |
| Lab Subnet      | 192.168.56.0/24                     |
| Host OS         | Windows 11                          |
| RAM (Kali VM)   | 4 GB                                |
| vCPUs (Kali VM) | 2                                   |

---

## Tools Used

| Tool             | Purpose                              |
|-----------------|--------------------------------------|
| VirtualBox       | Hypervisor for VM management        |
| Kali Linux       | Attacker machine                    |
| Docker           | Container runtime for Juice Shop    |
| OWASP Juice Shop | Intentionally vulnerable web target |
| Nmap             | Network and service scanning        |
| Burp Suite       | HTTP traffic interception           |
| Wireshark        | Packet capture and analysis         |

---

## Key Commands

```bash
# System update
sudo apt update && sudo apt upgrade -y

# Create lab folders
mkdir -p ~/lab/{scans,notes,pcaps,screenshots}

# Deploy Juice Shop via Docker
sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo docker pull bkimminich/juice-shop
sudo docker run -d -p 3000:3000 --name juice bkimminich/juice-shop

# Verify container running
sudo docker ps

# Network validation
ping -c 4 192.168.56.102
nmap -sn 192.168.56.0/24
nmap -sV -p 3000 192.168.56.102
```

---

## Deliverables

- [x] Full Lab Build PDF Report (`/report/`)
- [x] VirtualBox VM list (Screenshot 01)
- [x] IP configuration documented (Screenshots 02, 03)
- [x] Ping / Nmap validation (Screenshots 07, 08, 09)
- [x] Burp Suite interception (Screenshots 10, 11)
- [x] Wireshark packet capture (Screenshots 12, 13)

---

## Evidence Screenshots

All screenshots are in the `/evidence/` folder.

| File | Description |
|------|-------------|
| 01_virtualbox_vm_list.png | VirtualBox Manager showing both VMs |
| 02_kali_ip_config.png | Kali Linux `ip addr` output (both adapters) |
| 03_juiceshop_ip_config.png | Juice Shop VM IP config |
| 04_kali_network_adapters.png | VM Settings → Network tab |
| 05_docker_ps.png | `docker ps` showing Juice Shop container running |
| 06_juiceshop_browser.png | Juice Shop loaded in browser |
| 07_ping_validation.png | Successful ping to target |
| 08_nmap_host_discovery.png | `nmap -sn` host scan results |
| 09_nmap_service_scan.png | `nmap -sV -p 3000` result |
| 10_burp_intercept.png | Burp Suite intercepted request |
| 11_burp_http_history.png | Burp HTTP History log |
| 12_wireshark_icmp.png | Wireshark ICMP capture |
| 13_wireshark_http.png | Wireshark HTTP filter |

---

## Skills Demonstrated

- Virtualization and VM lifecycle management
- Lab network segmentation (NAT + Host-Only)
- Docker deployment of intentionally vulnerable applications
- Network reconnaissance with Nmap
- HTTP proxy interception with Burp Suite
- Packet-level traffic analysis with Wireshark
