## 📘 Introduction

As an ethical hacker, knowing **common ports and protocols** is critical for effective **reconnaissance, enumeration, vulnerability scanning**, and **exploitation**. Understanding how services communicate helps you map the attack surface and select appropriate tools and payloads.

Additionally, the **OSI model** helps you understand *where* attacks and defenses apply in a networked system. This layered model is foundational when analyzing packets, interpreting logs, and crafting exploits.

---

## 🔢 Common Ports & Protocols

### 📦 TCP (Transmission Control Protocol) - Connection-Oriented

| Port | Protocol | Description / Use Case                                |
|------|----------|--------------------------------------------------------|
| 21   | FTP      | File Transfer Protocol - upload/download files         |
| 22   | SSH      | Secure Shell - encrypted remote login                  |
| 23   | Telnet   | Unencrypted remote login (legacy, insecure)            |
| 25   | SMTP     | Simple Mail Transfer Protocol - sending emails         |
| 53   | DNS      | Domain Name System - also uses UDP                     |
| 80   | HTTP     | Web traffic (insecure)                                 |
| 110  | POP3     | Post Office Protocol - retrieving emails               |
| 139  | SMB      | Server Message Block - file and printer sharing (NetBIOS) |
| 143  | IMAP     | Internet Message Access Protocol - email retrieval     |
| 443  | HTTPS    | Secure HTTP traffic (TLS encryption)                   |
| 445  | SMB      | Direct over TCP - common target for Windows exploits   |

> 🧑‍💻 **Hacker Tip**: Many exploits target **SMB (445)** or **RDP (3389, not listed here)**. Knowing what services run on what ports is essential for fingerprinting and exploiting systems.

---

### ⚡ UDP (User Datagram Protocol) - Connectionless

| Port | Protocol | Description / Use Case                                  |
|------|----------|----------------------------------------------------------|
| 53   | DNS      | Resolves names to IP addresses (UDP often used for queries) |
| 67/68| DHCP     | Dynamic Host Configuration Protocol - assigns IP addresses |
| 69   | TFTP     | Trivial File Transfer Protocol - lightweight, no auth    |
| 161  | SNMP     | Simple Network Management Protocol - device monitoring   |

> 🕵️ UDP services are great for scanning (fast, stealthy) and often overlooked. **TFTP** and **SNMP** are commonly misconfigured, leading to info leaks.

---

## 🧱 OSI Model Overview

| Layer | Name                | Ethical Hacking Relevance                                 |
|-------|---------------------|------------------------------------------------------------|
| 1     | **Physical Layer**      | Cables, interfaces, physical attacks (e.g., plugging devices) |
| 2     | **Data Link Layer**     | MAC addresses, ARP spoofing, switch attacks                  |
| 3     | **Network Layer**       | IP addressing, routing, NAT, reconnaissance                  |
| 4     | **Transport Layer**     | TCP/UDP scans, firewalls, connection hijacking               |
| 5     | **Session Layer**       | Session control, authentication bypass                       |
| 6     | **Presentation Layer**  | Encoding, encryption/decryption (SSL/TLS)                    |
| 7     | **Application Layer**   | HTTP, DNS, FTP, etc. — where most **web app** attacks happen |

> 🎯 Most attacks target **Layer 7 (Application)** and **Layer 3–4 (Network/Transport)**. For example:
> - **SQLi/XSS** → Layer 7  
> - **MITM** → Layer 2/3  
> - **SYN Scans** → Layer 4

---

## 🧠 Concepts Related to visit later

- Well-known port ranges (0–1023), registered (1024–49151), dynamic (49152–65535)
- Port knocking & firewall evasion techniques
- TCP vs UDP scans in `nmap`, `hping3`, `netcat`
- Service fingerprinting (e.g., with `nmap -sV`)
- DNS Zone Transfer (TCP 53)
- Layered defense and how each OSI layer can be hardened

---

> 🛠️ **Practice Tip**: Use `nmap -sS`, `nmap -sU`, and `nmap -sV` to scan for open ports, determine protocol types, and identify services running behind them.
