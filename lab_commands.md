# Lab Commands Reference — Task 2

## 1. Kali Linux Initial Setup

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Create lab working directories
mkdir -p ~/lab/{scans,notes,pcaps,screenshots}
```

---

## 2. Docker + OWASP Juice Shop Deployment

```bash
# Install Docker
sudo apt install -y docker.io

# Enable and start Docker service
sudo systemctl enable --now docker

# Pull Juice Shop image
sudo docker pull bkimminich/juice-shop

# Run Juice Shop container on port 3000
sudo docker run -d -p 3000:3000 --name juice bkimminich/juice-shop

# Verify container is running
sudo docker ps

# Access Juice Shop in browser
# http://localhost:3000
# http://192.168.56.101:3000  (from Host-Only network)
```

---

## 3. Network Validation

```bash
# Check IP addresses on Kali (both adapters)
ip addr
# or
ifconfig

# Ping target to confirm connectivity
ping -c 4 192.168.56.102

# Nmap: Host discovery on lab subnet
nmap -sn 192.168.56.0/24

# Nmap: Service scan on Juice Shop port
nmap -sV -p 3000 192.168.56.102

# Nmap: Full scan with OS detection (optional)
nmap -A -p 3000 192.168.56.102
```

---

## 4. Burp Suite Setup

```
1. Open Burp Suite Community Edition
2. Proxy → Options → Listener: 127.0.0.1:8080
3. Firefox → Settings → Network → Manual Proxy
   HTTP Proxy: 127.0.0.1  Port: 8080
4. Navigate to http://192.168.56.101:3000
5. Proxy → Intercept → Intercept is ON
6. Observe captured request → Forward
```

---

## 5. Wireshark Packet Capture

```
1. Open Wireshark
2. Select interface: eth1 (Host-Only, 192.168.56.x)
3. Start capture
4. Run: ping -c 4 192.168.56.102
5. Display filter for ICMP:  icmp
6. Display filter for HTTP:  http
7. Stop capture → Save as ~/lab/pcaps/lab_capture.pcapng
```

---

## 6. Network Configuration Reference

| Interface | VM       | Type      | IP Address      |
|-----------|----------|-----------|-----------------|
| eth0      | Kali     | NAT       | 10.0.2.15       |
| eth1      | Kali     | Host-Only | 192.168.56.101  |
| eth0      | Target   | Host-Only | 192.168.56.102  |
| vboxnet0  | Host NIC | Host-Only | 192.168.56.1    |
