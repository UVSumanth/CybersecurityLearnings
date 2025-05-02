## 📘 Introduction

IP addresses help identify devices on a network and are foundational to reconnaissance, exploitation, and post-exploitation phases. You’ll encounter both **IPv4** and **IPv6** in external/internal network pentests, especially when identifying targets, mapping networks, and understanding how traffic flows.

---

## 🌐 IP Versions

### 🔹 IPv4 (Internet Protocol version 4)
- 32-bit address (e.g., `192.168.1.1`)
- Provides ~4.3 billion unique addresses
- Commonly used, especially in legacy and private networks
- Divided into classes (A, B, C, D, E) — mainly A-C used for addressing

### 🔹 IPv6 (Internet Protocol version 6)
- 128-bit address (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`)
- Supports vastly more addresses (~3.4×10^38)
- Used in modern networks, but adoption is still growing
- Better security features and no need for NAT

---

## 📦 Networking Layers Context

| Layer | Name              | Common Device | Protocol Example |
|-------|-------------------|---------------|------------------|
| 3     | **Network Layer** | **Router**    | IP (IPv4, IPv6)  |

- IP addressing operates at **Layer 3** (Network layer) in the **OSI model**.
- Routers use Layer 3 IPs to make routing decisions between networks.

---

## 🔁 NAT (Network Address Translation)

### What is NAT?
- **NAT** maps **private IPs** to a **public IP**
- Allows multiple internal devices to share a single public IP when accessing the internet

### Types of NAT:
- **Static NAT**: One-to-one mapping (internal IP → public IP)
- **Dynamic NAT**: Uses a pool of public IPs
- **PAT (Port Address Translation)**: Many-to-one mapping (most common form of NAT)

> 🔐 From an ethical hacking POV, NAT hides internal IPs, adding a layer of **obfuscation**. When scanning from the outside, you’ll often hit the NAT boundary and need to rely on **OSINT, VPN leaks, misconfigured firewalls**, or **pivoting** techniques during internal tests.

---

## 🏠 Private vs Public IPs

### Private IP Ranges (RFC1918):
| Class | Range                    |
|-------|--------------------------|
| A     | 10.0.0.0 – 10.255.255.255 |
| B     | 172.16.0.0 – 172.31.255.255 |
| C     | 192.168.0.0 – 192.168.255.255 |

- **Private IPs** are used inside networks (not routable on the internet)
- **Public IPs** are assigned by ISPs and are internet-routable

> 🕵️‍♂️ In pentesting, identifying if an IP is public or private helps determine whether you're dealing with external or internal infrastructure.

---

## 🧠 Concepts Related to IP Address

- Subnetting (CIDR notation, subnet masks)
- DHCP vs Static IPs
- ARP (Address Resolution Protocol) for Layer 2 <-> Layer 3 mapping
- IPv6 tunneling & reconnaissance
- NAT traversal techniques
- IP spoofing basics
- Geolocation from IP
- IPsec & VPNs
- IPv4 exhaustion and impact on security

---

> ✅ **Tip**: During recon, tools like `nmap`, `whois`, `nslookup`, and `ipcalc` can help analyze IP address space. Recognize public IPs, determine network ranges, and look for misconfigurations or exposures.

