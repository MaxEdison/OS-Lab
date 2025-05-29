---
title: Linux Network
sub_title: OS Lab
authors:
  - AmirHossein Heidari
  - Fasa University
  - 2025 | ۴۰۴۱
---

<!-- font_size: 3 -->
OSI & Networking Tools
=======================
# The OSI model has **7 layers** (Physical → Application):
## We’ll map Linux tools to OSI layers:
<!-- pause -->
  - **Layer 3 (Network)**: `ip` (interfaces/routes) and `ping` (ICMP echo)
  - **Layer 4 (Transport)**: `ss` (sockets) and `netcat` (TCP/UDP client/server) 
  - **Layer 7 (Application)**: `curl` (HTTP/web requests) 
  - **Firewall (`ufw`)**: filters by IP/port at layers 3/4
<!-- end_slide -->

<!-- font_size: 3 -->
Network Interfaces & IP
=======================
- `ip addr show`: lists all network interfaces and their IP addresses (Network layer)
- `ip route show`: shows the routing table (default gateway and networks).
```bash
ip addr show
```
<!-- pause -->
```bash
ip route show
```

<!-- end_slide -->

<!-- font_size: 3 -->
Ping (Layer 3)
=======================
- ping: sends ICMP echo requests to test connectivity (Network layer)

<!-- pause -->

```bash
ping -c 2 127.0.0.1
```
* Limit the count with `-c` to avoid endless pings.

<!-- end_slide -->

<!-- font_size: 3 -->
TraceRoute (Layer 3)
=======================
- traceroute: Shows the path packets take to a destination

```bash
traceroute fasau.ac.ir
```
<!-- end_slide -->

<!-- font_size: 3 -->
Socket Statistics with ss (Layer 4)
=======================

- `ss` (socket statistics) lists active TCP/UDP sockets

```bash
ss -tulwn
```
- ss shows established TCP connections; add options for listening sockets:
  - `-l`: show listening ports
  - `-t`: TCP, `-u`: UDP
  - `-w`: sockets waiting for connection
  - `-n`: numeric (no DNS resolution)

<!-- end_slide -->


<!-- font_size: 3 -->
curl (HTTP)
=======================
- curl is a command-line tool to transfer data with network protocols (Application layer): 
  - Fetch HTTP headers from a website:
```bash
curl -I https://pershiess.fasau.ac.ir
```
<!-- end_slide -->


<!-- font_size: 2 -->
Firewall with ufw
=======================
- An easy frontend to iptables (Layer 3 & 4):
  - check status:
```bash
sudo ufw status verbose
```
<!-- pause -->

  - Enable / Disable firewall:
```bash
sudo ufw enable
sudo ufw disable
```
<!-- pause -->

  - Allow / Deny IN-OUT traffic:
```bash
sudo ufw default allow incoming
sudo ufw default allow outgoing

sudo ufw default deny incoming
sudo ufw default deny incoming
```
<!-- end_slide -->

<!-- font_size: 2 -->
Firewall with ufw
=======================
  - Allow / Deny specific por:
```bash
sudo ufw allow PORT
sudo ufw allow in PORT

sudo ufw deny PORT
sudo ufw deny out PORT
```

<!-- end_slide -->

<!-- font_size: 3 -->
DNS
=======================

- Domain names to IP addresses

  - dig --> DNS query tool
  - nslookup --> Interactive DNS tool

```bash
dig fasau.ac.ir

nslookup food.fasau.ac.ir
```

# Change DNS server address:
```bash
sudo nano /etc/resolve.conf
```