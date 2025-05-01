# 📘 CEH Study Notes – Nmap Basic Port Scans

---

## 🧠 1. Nmap Port Scanning Overview

After discovering live hosts, the next step is identifying **open ports** and **listening services**. Nmap supports several types of scans to determine port states.

### 🧭 Nmap Scan Workflow (So Far):
1. Enumerate Targets
2. Discover Live Hosts
3. Reverse-DNS Lookup
4. Port Scanning (This Room)

---

## 📌 2. Understanding TCP and UDP Ports

| Type | Purpose |
|------|---------|
| **TCP/UDP Ports** | Identify specific services (e.g., HTTP, DNS) on a host |
| **Open Port** | A service is listening on that port |
| **Closed Port** | No service listening, but port is reachable |

### 🔒 Port States (According to Nmap):

| State            | Description |
|------------------|-------------|
| **Open**         | Service is listening |
| **Closed**       | No service, but port is accessible |
| **Filtered**     | Port unreachable (likely blocked by firewall) |
| **Unfiltered**   | Port accessible, but no conclusion on state |
| **Open|Filtered**| Cannot determine if port is open or filtered |
| **Closed|Filtered**| Cannot determine if port is closed or filtered |

---

## 🔧 3. TCP Flags (RFC 793)

| Flag | Purpose |
|------|---------|
| **URG** | Marks urgent data |
| **ACK** | Acknowledges received packets |
| **PSH** | Pushes data to the application immediately |
| **RST** | Resets a connection |
| **SYN** | Initiates a connection (part of 3-way handshake) |
| **FIN** | Closes the connection |

---

## 🔍 4. TCP Connect Scan (`-sT`)

### 📖 Description:
- Performs a **full TCP 3-way handshake** (SYN → SYN/ACK → ACK).
- If port is open, handshake is completed.
- Connection is **reset immediately after confirmation**.

### 🧪 Use Case:
- **Default** for unprivileged users (non-root).
- **Easily detectable** by firewalls and logging systems.

### 🛠 Example:
`nmap -sT MACHINE_IP`

---

## 🕵️‍♂️ 5. TCP SYN Scan (`-sS`)

### 📖 Description:
- Sends **SYN** packet only.
- If target replies with **SYN/ACK** → Port is open.
- Immediately sends **RST** → no full handshake = stealthy.

### 🧪 Use Case:
- **Default for root/privileged users**
- **Stealthier** than TCP connect scan.
- Doesn’t complete full TCP connection.

### 🛠 Example:
`sudo nmap -sS MACHINE_IP`

---

## 🌊 6. UDP Scan (`-sU`)

### 📖 Description:
- Sends **UDP packets** to target ports.
- If port is closed → **ICMP Type 3, Code 3** (port unreachable) is returned.
- If port is open → **no response** (UDP is connectionless).

### ⚠️ Considerations:
- Very **slow** (requires long timeouts).
- High **packet loss probability**.
- Useful for identifying services like DNS, SNMP, TFTP.

### 🛠 Example:
`sudo nmap -sU MACHINE_IP`

---

## 🎯 7. Specifying Port Ranges

| Option           | Description |
|------------------|-------------|
| `-p22,80,443`    | Scan specific ports |
| `-p20-25`        | Scan a range |
| `-p-`            | Scan **all 65535** ports |
| `-F`             | Scan **top 100** ports |
| `--top-ports 10` | Scan top 10 most common ports |

---

## ⚙️ 8. Timing and Performance Control

### ⏱ Timing Templates:

| Flag | Mode      | Behavior |
|------|-----------|----------|
| `-T0` | Paranoid | Extremely slow, stealthy |
| `-T1` | Sneaky   | Very slow |
| `-T2` | Polite   | Slightly slow |
| `-T3` | Normal   | Default |
| `-T4` | Aggressive | Fast, good for CTFs |
| `-T5` | Insane   | Very fast, risk of accuracy loss |

### 📉 Packet Rate Control:
- `--min-rate 10` → Send at least 10 packets per second
- `--max-rate 100` → Cap sending to 100 packets per second

### ⚙️ Probe Parallelism:
- `--min-parallelism 100`
- `--max-parallelism 512`

> Useful when scanning large IP ranges or networks.

---

## 🧪 9. Sample Nmap Outputs (for Reference)

### ✅ TCP Connect Scan (`-sT`)
```text
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
143/tcp open  imap
993/tcp open  imaps
```

### ✅ TCP SYN Scan (-sS)
```
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
110/tcp open  pop3
143/tcp open  imap
```

### ✅ UDP Scan (-sU)
```
PORT    STATE         SERVICE
68/udp  open|filtered dhcpc
111/udp open          rpcbind

```
## 📚 Summary Table
|Scan Type    | Flag |	Privileges| Stealth| Speed| Notes | 
|-------------|------|------------|--------|------|-------|
| TCP Connect |	-sT	 | No	        | ❌	   |✅   | Full TCP handshake
|TCP SYN      |	-sS  | Yes	      | ✅	   | ✅	  | Half-open scan (stealth)
|UDP          |	-sU  | Yes	      |❓	   |❌	  | No handshake; relies on ICMP

## ✅ CEH Exam Tips
- Remember **TCP Connect** (-sT) is for **unprivileged users**.
- **SYN scan** (-sS) is stealthier and faster; preferred for privileged scans.
- **UDP scan** is slower and noisier — but needed to find services like SNMP and TFTP.
- Know your **TCP flags** and how **3-way handshake** works.
- Learn how **Nmap classifies port** states (Open, Closed, Filtered, etc.).
- Use **timing templates** for stealth (-T0, -T1) or speed (-T4, -T5).
- Understand **when/why to scan specific ports** using -p, --top-ports, or -F.

## 📚 Resources

- [Nmap Reference Guide](https://nmap.org/book/man-port-scanning-techniques.html)
- [TryHackMe Nmap Rooms](https://tryhackme.com/room/nmap01)
- [Wireshark TCP Flag Analysis](https://wiki.wireshark.org/TCP)



