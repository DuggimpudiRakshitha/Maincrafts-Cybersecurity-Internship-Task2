# Evidence Folder — Screenshot Guide

Add your actual screenshots to this folder with the filenames below.

| Filename | What to Screenshot | How to Take It |
|---|---|---|
| 01_virtualbox_vm_list.png | VirtualBox Manager window showing both VMs | Open VirtualBox → take screenshot |
| 02_kali_ip_config.png | Kali terminal: `ip addr` output | Run `ip addr` in Kali terminal |
| 03_juiceshop_ip_config.png | Target VM terminal: `ip addr` output | Run `ip addr` in second VM |
| 04_kali_network_adapters.png | VM Settings → Network tab showing both adapters | VirtualBox → Settings → Network |
| 05_docker_ps.png | Terminal: `sudo docker ps` output | Run command in Kali terminal |
| 06_juiceshop_browser.png | Juice Shop home page in browser | Open http://localhost:3000 in Firefox |
| 07_ping_validation.png | Terminal: `ping -c 4 192.168.56.102` | Run ping from Kali terminal |
| 08_nmap_host_discovery.png | Terminal: `nmap -sn 192.168.56.0/24` | Run nmap in Kali terminal |
| 09_nmap_service_scan.png | Terminal: `nmap -sV -p 3000 192.168.56.102` | Run nmap in Kali terminal |
| 10_burp_intercept.png | Burp Suite Proxy → Intercept tab with captured request | Burp Suite → Proxy → Intercept |
| 11_burp_http_history.png | Burp Suite HTTP History showing requests | Burp Suite → Proxy → HTTP History |
| 12_wireshark_icmp.png | Wireshark showing ICMP ping packets | Wireshark capture on eth1 |
| 13_wireshark_http.png | Wireshark with `http` filter applied | Wireshark → filter: http |

> **Tip:** Use `PrtScn` or Kali's built-in screenshot tool. Save all files as PNG.
