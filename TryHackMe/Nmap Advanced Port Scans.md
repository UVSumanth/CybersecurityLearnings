## 🔰 Introduction

This is the third in the Nmap series:
- ✅ Nmap Live Host Discovery
- ✅ Nmap Basic Port Scans
- ✅ Nmap Advanced Port Scans (this file)
- ⏭️ Nmap Post Port Scans (next)

This section explores **advanced TCP scans** and **evasion techniques** for IDS/firewall bypass. It includes:

- Null, FIN, Xmas, Maimon, ACK, and Window Scans
- IP and MAC Spoofing
- Decoy and Fragmented Packet Scans
- Idle/Zombie Scans
- Verbosity, debugging, and interpretation options

---

## 🔍 TCP Flag Manipulation-Based Scans

### 🔹 Null Scan (`-sN`)
- No TCP flags set.
- **Open/filtered** → No response
- **Closed** → RST response
- Useful for bypassing stateless firewalls.

### 🔹 FIN Scan (`-sF`)
- Sends TCP packet with **FIN flag** only.
- Similar to Null scan in behavior.
- **Open/filtered** → No response
- **Closed** → RST response

### 🔹 Xmas Scan (`-sX`)
- Sets **FIN + PSH + URG** flags.
- Name comes from “lighting up all flags like a Xmas tree.”
- **Open/filtered** → No response
- **Closed** → RST response

> ✅ Use when scanning targets behind **stateless firewalls**.

---

## 🔸 TCP Maimon Scan (`-sM`)
- Sets **FIN + ACK** flags.
- Originally exposed behavior in BSD systems.
- **Modern systems** treat open/closed ports the same → not useful now.
- Most replies are **RST**, regardless of port state.

---

## 🕵️ ACK-Based Scans

### 🔹 ACK Scan (`-sA`)
- Sends **ACK** packets.
- Always expects **RST** if host responds.
- Determines **firewall rules**, not open ports.
- Ports are marked as:
  - **Unfiltered** → Response received
  - **Filtered** → No response

### 🔹 Window Scan (`-sW`)
- Similar to ACK scan.
- Analyzes **TCP window size** in RST responses.
- On some systems:
  - **Window > 0** → Open
  - **Window = 0** → Closed

---

## ⚙️ Custom TCP Flag Scans

### 🔹 Custom Flag Scan (`--scanflags`)
- Combine TCP flags manually.
- Example: `--scanflags URGACKPSHRSTSYNFIN`
- Use carefully; results depend on target's TCP stack behavior.

---

## 🕶️ Spoofing Techniques

### 🔹 IP Spoofing (`-S SPOOFED_IP`)
- Sends packets with **forged source IP**.
- Needs attacker to **sniff responses** manually.
- Example: `nmap -Pn -e eth0 -S 192.168.1.100 <target>`

### 🔹 MAC Spoofing (`--spoof-mac`)
- Use when on same subnet (Ethernet/WiFi).
- Example: `nmap --spoof-mac 00:11:22:33:44:55 <target>`

---

## 🧩 Decoy Scans

### 🔹 Decoy Option (`-D`)
- Makes scan appear to come from multiple IPs.
- Example:  
  `nmap -D 10.0.0.1,10.0.0.2,ME <target>`  
  `nmap -D RND,RND,ME <target>`

> Helps avoid attribution by **confusing IDS systems**.

---

## ✂️ Fragmented Packets

### 🔹 Fragmentation (`-f`, `-ff`)
- Breaks packets into **8-byte** chunks (`-f`) or **16-byte** chunks (`-ff`).
- Helps **bypass simple packet filters** or **IDS detection**.

### 🔹 Change MTU
- `--mtu <value>`: Use custom fragment size (must be multiple of 8).

### 🔹 Add Padding
- `--data-length <num>`: Appends random data to hide payload patterns.

---

## 🧟 Idle/Zombie Scan (`-sI ZOMBIE_IP TARGET`)

- Spoofs IP of idle host and observes IP ID changes.
- Uses 3 steps:
  1. Probe zombie for current IP ID.
  2. Spoof a SYN packet to target (from zombie IP).
  3. Probe zombie again for new IP ID.

### 🧠 Result Interpretation:
| IP ID Difference | Meaning |
|------------------|---------|
| 2                | Target port is **open** |
| 1                | Target port is **closed** |
| No change        | Port is **filtered** or zombie is not truly idle |

> Must use a **truly idle machine** with predictable IP ID behavior.

---

## 🔎 Enhancing Output & Detail

| Option       | Description |
|--------------|-------------|
| `--reason`   | Shows **why** a port was marked open/closed |
| `-v`, `-vv`  | Verbose and very verbose |
| `-d`, `-dd`  | Debug and deep debug (for advanced troubleshooting) |

> Use `--reason` to understand **Nmap's logic** behind results (e.g., syn-ack, RST).

---

## 🧠 Summary Table of Advanced Scans

| Scan Type          | Command Example                        | Purpose |
|--------------------|----------------------------------------|---------|
| TCP Null Scan      | `sudo nmap -sN <IP>`                   | Bypass simple firewalls |
| TCP FIN Scan       | `sudo nmap -sF <IP>`                   | Stateless firewall bypass |
| Xmas Scan          | `sudo nmap -sX <IP>`                   | Evasion scan with unusual flag combo |
| Maimon Scan        | `sudo nmap -sM <IP>`                   | Rare; old BSD exposure |
| ACK Scan           | `sudo nmap -sA <IP>`                   | Identify firewall rules |
| Window Scan        | `sudo nmap -sW <IP>`                   | Analyze TCP window size |
| Custom Flags       | `--scanflags URGACKPSHRSTSYNFIN`       | Build your own scan |
| Spoofed IP         | `-S <IP>`                              | IP obfuscation |
| Spoofed MAC        | `--spoof-mac <MAC>`                    | MAC obfuscation |
| Decoy Scan         | `-D IP1,IP2,ME`                        | Anti-attribution tactic |
| Fragment Packets   | `-f` / `-ff` / `--mtu <val>`           | Bypass IDS/firewall |
| Idle Scan          | `sudo nmap -sI <zombie> <target>`      | Stealth + spoofing |
| Padding            | `--data-length <num>`                  | Add junk data to packets |

---

## ✅ CEH Exam Tips

- Null, FIN, and Xmas scans rely on **no response = open|filtered**, **RST = closed**
- ACK and Window scans help identify **firewall rules**, **not port states**
- Maimon scan is outdated, but good to know for **theory**
- Use **-f**, `--data-length`, and `--scanflags` for **evasion**
- Idle scans are **advanced stealth techniques** needing zombie hosts with predictable IP ID
- Use `--reason`, `-vv`, and `-dd` for **interpreting** and **debugging scan output**

---

## 📚 Resources

- [Nmap Port Scanning Techniques](https://nmap.org/book/man-port-scanning-techniques.html)
- [TryHackMe – Nmap Advanced Scans](https://tryhackme.com/)
- [Wireshark TCP Header Info](https://wiki.wireshark.org/TCP)

---
