## 🧠 Introduction to Nmap Live Host Discovery

When targeting a network, the first step is to **identify live hosts**. Scanning offline systems wastes time and generates unnecessary noise.

**Questions Nmap helps answer:**
- Which systems are up?
- What services are running on these systems?

**Nmap** (Network Mapper) is a free, open-source tool developed by **Gordon Lyon (Fyodor)** in 1997. It is widely used for network discovery, service enumeration, and vulnerability assessment.

**Nmap Host Discovery** identifies **live hosts** *before* proceeding to port scanning.

---

## 🔍 Approaches for Live Host Discovery

Nmap uses multiple protocols across TCP/IP layers to detect live systems:

| Protocol | Layer         | Purpose |
|----------|---------------|---------|
| **ARP**  | Link Layer     | Discover MAC addresses on local networks |
| **ICMP** | Network Layer  | Ping, timestamp, and address mask requests |
| **TCP**  | Transport Layer | SYN and ACK probes to discover live hosts |
| **UDP**  | Transport Layer | Probes to find reachable systems |

---

## 🌐 Nmap Host Discovery Techniques

### 1. ARP Scan (Local Network Discovery)

- **Command:** `sudo nmap -PR -sn <target>/24`
- Works only on the **same subnet** (Ethernet/WiFi).
- Sends **ARP requests** to discover MAC addresses.
- Systems that reply to ARP are **online**.
- Very reliable on local networks.

> Note: Use tools like `arp-scan` for advanced ARP queries:
> - `sudo arp-scan -l`
> - `sudo arp-scan -I eth0 -l`

---

### 2. ICMP Echo Scan (Ping Scan)

- **Command:** `sudo nmap -PE -sn <target>/24`
- Sends **ICMP Echo Request (Type 8)** and expects **Echo Reply (Type 0)**.
- Some firewalls **block ICMP Echo**.
- Reliable on open networks but less effective on hardened hosts.

---

### 3. ICMP Timestamp Scan

- **Command:** `sudo nmap -PP -sn <target>/24`
- Sends **ICMP Timestamp Request (Type 13)** and expects a **Timestamp Reply (Type 14)**.
- Alternative method when ICMP Echo is blocked.

---

### 4. ICMP Address Mask Scan

- **Command:** `sudo nmap -PM -sn <target>/24`
- Sends **ICMP Address Mask Request (Type 17)** and expects an **Address Mask Reply (Type 18)**.
- Rarely successful; often blocked by modern firewalls.

---

### 5. TCP SYN Ping Scan

- **Command:** `sudo nmap -PS<port(s)> -sn <target>/24`
- Sends **SYN packets** to common ports (default 80).
- Open ports respond with **SYN-ACK**.
- Closed ports respond with **RST**.
- Good method when ICMP is blocked.

Examples:
- `sudo nmap -PS22,80,443 -sn <target>/24`

---

### 6. TCP ACK Ping Scan

- **Command:** `sudo nmap -PA<port(s)> -sn <target>/24`
- Sends **ACK packets** to specified ports.
- Target replies with **RST** if host is alive.
- Helps in discovering **firewall rules**.

Examples:
- `sudo nmap -PA22,80,443 -sn <target>/24`

---

### 7. UDP Ping Scan

- **Command:** `sudo nmap -PU<port(s)> -sn <target>/24`
- Sends **UDP packets** to selected ports.
- **No response** may indicate an open UDP port.
- **ICMP Port Unreachable** error indicates closed UDP ports.

Examples:
- `sudo nmap -PU53,161,162 -sn <target>/24`

> UDP discovery is slow due to retransmission delays and rate-limiting.

---

## 🛰️ Other Host Discovery Tools

### 1. arp-scan
- Focuses only on **ARP-based host discovery**.
- Useful for local network enumeration.

### 2. masscan
- **Very fast** network scanner (aggressive packet rates).
- Syntax similar to Nmap:
  - `masscan <target>/24 -p80`
  - `masscan <target>/24 --top-ports 100`
- Used when scanning **huge networks quickly**.

---

## 📡 Reverse DNS Lookup in Nmap

- **Default Behavior:** Nmap performs reverse-DNS lookup for live hosts.
- **Disable DNS Lookup:** `-n`
- **Force Reverse-DNS Lookup:** `-R`
- **Use a Specific DNS Server:** `--dns-servers <DNS_IP>`

---

## 🧠 Conceptual Summary: Layered Approach for Host Discovery

| Layer          | Method | Purpose |
|----------------|--------|---------|
| Link Layer     | ARP     | Discover local devices using MAC addresses |
| Network Layer  | ICMP    | Discover devices using Ping, Timestamp, or Address Mask |
| Transport Layer| TCP/UDP | SYN/ACK/UDP packets to discover reachable systems |

---

## 📚 Important Nmap Host Discovery Commands

| Scan Type                | Example Command |
|---------------------------|-----------------|
| ARP Scan                  | `sudo nmap -PR -sn MACHINE_IP/24` |
| ICMP Echo Scan            | `sudo nmap -PE -sn MACHINE_IP/24` |
| ICMP Timestamp Scan       | `sudo nmap -PP -sn MACHINE_IP/24` |
| ICMP Address Mask Scan    | `sudo nmap -PM -sn MACHINE_IP/24` |
| TCP SYN Ping Scan         | `sudo nmap -PS22,80,443 -sn MACHINE_IP/30` |
| TCP ACK Ping Scan         | `sudo nmap -PA22,80,443 -sn MACHINE_IP/30` |
| UDP Ping Scan             | `sudo nmap -PU53,161,162 -sn MACHINE_IP/30` |

---

## ✅ Key CEH Exam Tips:

- **ARP scans** are extremely reliable for local network discovery.
- **ICMP Echo** may be blocked; use TCP SYN or ACK pings as alternatives.
- Understand the difference between **TCP SYN, TCP ACK**, and **UDP-based** discovery.
- Know when **privileged access** (root) is required (for SYN, ACK, UDP scans).
- **Masscan** is faster but noisier.
- Remember **ARP discovery** works only inside the same subnet.

---

