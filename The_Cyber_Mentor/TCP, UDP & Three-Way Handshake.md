## 📘 Introduction

How data is transmitted over the network is crucial. TCP and UDP operate at the **Transport Layer (Layer 4)** of the **OSI Model** and are involved in most network-based attacks, reconnaissance, and exploitation techniques.

Knowing how these protocols behave helps in crafting exploits, analyzing packet captures, and understanding firewall behavior.

---

## 📶 Layer 4 - Transport Layer (OSI Model)

| Layer | Name            | Role                                       |
|-------|------------------|--------------------------------------------|
| 4     | **Transport Layer** | Responsible for **data delivery**, error handling, and session management |

---

## 📦 TCP (Transmission Control Protocol)

- **Connection-Oriented** protocol
- Ensures reliable, ordered, and error-checked delivery of data
- Uses **acknowledgements (ACKs)** and **retransmissions**
- Protocols using TCP: `HTTP`, `HTTPS`, `SSH`, `FTP`, `SMTP`, `Telnet`

### 🔐 In Ethical Hacking
- Used in **port scanning (SYN scans)** to detect open/closed ports
- Reliable behavior makes it predictable for **session hijacking**, **replay attacks**, etc.
- Important for understanding **banner grabbing** and **web application pentesting**

---

## ⚡ UDP (User Datagram Protocol)

- **Connectionless** protocol
- Faster but less reliable — no acknowledgements or sequencing
- Protocols using UDP: `DNS`, `DHCP`, `SNMP`, `VoIP`, `Streaming`, `TFTP`

### 🕵️ In Ethical Hacking
- Used for **UDP scanning**, **DoS amplification attacks** (e.g., DNS/UDP floods)
- Easier to spoof (no handshake)
- Many vulnerable services (e.g., misconfigured DNS, open SNMP) use UDP

---

## 🤝 TCP Three-Way Handshake

The handshake sets up a reliable connection between two hosts.

### Steps:

1. **SYN**: Client → Server  
   - Client initiates connection (sends SYN)

2. **SYN-ACK**: Server → Client  
   - Server acknowledges (SYN-ACK)

3. **ACK**: Client → Server  
   - Client sends final ACK to establish connection

> ✅ After this, data transfer begins securely.

### 🔍 In Ethical Hacking
- **SYN Scan (Stealth Scan)**: Sends SYN, analyzes response without completing the handshake  
  - Tools: `nmap -sS`
- **Half-open scans** are less likely to be logged
- Useful in identifying **firewalls** and **intrusion detection evasion**

---

## ⚠️ TCP vs UDP - Quick Comparison

| Feature            | TCP                            | UDP                        |
|--------------------|----------------------------------|-----------------------------|
| Type               | Connection-oriented             | Connectionless              |
| Speed              | Slower                          | Faster                      |
| Reliability        | High (error checking, ACKs)     | Low (no retransmission)     |
| Order of delivery  | Guaranteed                      | Not guaranteed              |
| Use Cases          | Web, Email, Secure Shell        | DNS, VoIP, Streaming        |
| Ethical Hacking Use| SYN scan, Session Hijacking     | UDP scan, Amplification attacks |

---

## 🧠 Concepts to go through later

- TCP Flags (`SYN`, `ACK`, `RST`, `FIN`, etc.)
- TCP Reset attacks (RST injection)
- TCP/UDP port scanning techniques (`nmap`, `hping3`)
- Banner Grabbing (via TCP ports)
- DNS-based UDP attacks (amplification, poisoning)
- UDP flood and fragmentation
- Stateful vs Stateless firewalls and how they treat TCP/UDP
- TCP sequence prediction (relevant for spoofing)

---

> 🛠️ **Practice Tip**: Use `Wireshark` or `tcpdump` to capture a handshake
