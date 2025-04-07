# 📚 Computer Security Incident Handling Guide (Based on NIST SP 800-61r2)

## 🎯 Overview
Computer security incidents are inevitable. This guide provides actionable insights on organizing and handling incident response effectively, based on NIST SP 800-61 Revision 2 (now archived but still useful for foundational understanding).

---

## 🔐 Section 2: Organizing a Computer Security Incident Response Capability (CSIRC)

### 2.1 Events and Incidents
- **Event**: Observable occurrence (e.g., logins, system alerts).
- **Adverse Event**: Negative consequence (e.g., crash, malware).
- **Security Incident**: Violation or imminent threat of violation of security policies or practices.

---

### 2.2 Why Incident Response Matters
- Data breaches and service disruptions are frequent.
- IR minimizes impact, ensures systematic recovery.
- Facilitates preparation for future incidents via insights from past cases.

---

### 2.3 Creating Policy, Plan & Procedures

#### 🔸 2.3.1 Policy Elements
- Management commitment
- Incident definitions & scope
- Roles & authority (e.g., ability to disconnect systems)
- Reporting requirements

#### 🔸 2.3.2 Plan Elements
- Mission, goals, and strategies
- Communication structure
- Metrics and maturity roadmap

#### 🔸 2.3.3 Procedure Elements
- Standard Operating Procedures (SOPs) for technical handling
- Checklists and forms

#### 🔸 2.3.4 Sharing with Outside Parties
- **Media**: Designated POC, mock drills, sensitive info protocol
- **Law Enforcement**: Define jurisdiction, escalation processes
- **US-CERT**: Mandatory for federal agencies
- **Others**: ISPs, vendors, incident response teams, affected users

---

### 2.4 Incident Response Team Structure

#### 🔸 2.4.1 Team Models
- **Central**: One team, ideal for small orgs.
- **Distributed**: Multiple teams (geographic or logical split).
- **Coordinating**: Advisory-only role, not authority-based.
- **Staffing Models**: In-house, partially outsourced, fully outsourced.

#### 🔸 2.4.2 Team Model Selection - Key Factors
- 24/7 availability
- Cost, morale, staff expertise
- Outsourcing risks: loss of org-specific knowledge, data leakage, skill atrophy

#### 🔸 2.4.3 IR Personnel Requirements
- Skills: technical (forensics, detection, systems), soft skills, teamwork
- Roles: Team Lead, Technical Lead, Incident Lead
- Maintain morale: learning, rotation, mentorship

#### 🔸 2.4.4 Dependencies
- Legal, HR, IT, Management, Public Affairs, Physical Security

---

### 2.5 Team Services
- **Primary**: Incident detection & handling
- **Others**: Intrusion detection, advisory distribution, training, info sharing

---

### ✅ 2.6 Recommendations
- Establish IR policy, plan, and procedures
- Identify internal groups involved
- Select proper team structure
- Share information responsibly

---

## 🚨 Section 3: Handling an Incident

### 🔁 Incident Response Life Cycle
**Phases**: Preparation → Detection & Analysis → Containment → Eradication → Recovery → Post-Incident Activities

---

### 3.1 Preparation

#### 🔸 Tools & Resources
- Contact directories, reporting mechanisms, war rooms, forensics kits
- Laptops, sniffers, removable media, evidence tools

#### 🔸 Prevention Focus
- Risk assessments
- User awareness
- Host/network security

---

### 3.2 Detection & Analysis

#### 🔸 3.2.1 Attack Vectors
- Web, Email, Removable Media, Attrition, Improper Usage, Impersonation, Equipment Theft

#### 🔸 3.2.2 Signs of Incidents
- **Precursors**: Rare, may signal future threats (e.g., vulnerability alerts)
- **Indicators**: Logs, IDS alerts, user reports

#### 🔸 3.2.3 Sources of Indicators
- SIEMs, IDS/IPS, Antivirus, Logs, Threat Feeds, Human Reports

#### 🔸 3.2.4 Incident Analysis Tips
- Know your baseline
- Use synchronized time
- Maintain a knowledge base
- Use packet sniffers + filters

#### 🔸 3.2.5 Documentation Checklist
- Incident status, summary, indicators, evidence, contact info, chain of custody

#### 🔸 3.2.6 Prioritization Factors
- Functional, Information, and Recoverability Impact

#### 🔸 3.2.7 Notifications
- CIO, Security Head, Legal, HR, Public Affairs, Law Enforcement, US-CERT

---

### 3.3 Containment, Eradication & Recovery

#### 🔸 Containment Strategy Factors
- Damage potential
- Service availability
- Evidence preservation
- Strategy duration

#### 🔸 Evidence Handling
- Forensics, backups, chain of custody

#### 🔸 Identify Attack Source
- IP traceback, OSINT, monitoring channels

---

### 3.4 Post-Incident Activity

#### 🔸 Lessons Learned
- What failed? What helped? What to improve?
- Share cross-org insights

#### 🔸 Data Usage
- Track incident metrics (time, type, impact)
- Use reports for audits & training

#### 🔸 Evidence Retention
- Align with legal & business requirements

---

### 🧾 3.5 Checklist (Quick Actions Summary)
- Identify, Analyze, Contain, Document, Notify, Eradicate, Recover, Review

---

## 🤝 Section 4: Coordination & Information Sharing

### 4.1 Coordination
- Establish team-to-team, team-to-coordinator, and external partnerships

### 4.2 Info Sharing Techniques
- Ad hoc, partially automated, fully automated
- Beware of oversharing sensitive data

### 4.3 Types of Shared Information
- **Business Impact**: Helps with risk understanding
- **Technical Indicators**: Aids threat detection

---

### ✅ 4.4 Key Recommendations
- Build sharing agreements in advance
- Involve legal before sharing data
- Automate sharing where possible
- Balance transparency with confidentiality

---

## 🧠 Final Thoughts
While this document is based on NIST SP 800-61r2 (now replaced by Rev. 3), it provides foundational guidance that’s still applicable. Incident response is not just a technical discipline — it involves coordination, communication, legal, and organizational strategy.

---

## 📎 Appendix
- [NIST SP 800-61r3 - Latest Version (April 2025)](https://doi.org/10.6028/NIST.SP.800-61r3)
- [Incident Response Checklist Template](https://www.sans.org/media/score/checklists/Incident-Handler-Checklist.pdf)
