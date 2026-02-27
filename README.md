# 🛑 WannaCry Ransomware — Technical Case Study (2017)

## 🧑‍💻 Learning Objective

This repository is part of my beginner cybersecurity learning journey.
I am studying historical ransomware incidents to understand:
- Vulnerability exploitation
- Worm propagation
- Encryption techniques
- Incident response basics

## 📌 Overview

WannaCry (also known as WannaCrypt or WCry) was a worm-based ransomware attack that began on 12 May 2017. It rapidly spread across the globe by exploiting a vulnerability in Microsoft Windows systems.

- **Type:** Ransomware worm  
- **Outbreak Date:** 12 May 2017  
- **Systems Affected:** Unpatched Windows machines (SMBv1 enabled)  
- **Ransom Demand:** ~$300 in Bitcoin  
- **Countries Impacted:** 150+  
- **Total Infections:** ~230,000 systems  

---

## 🔎 Vulnerability Exploited

WannaCry exploited a Windows SMB vulnerability:

- **Exploit Name:** EternalBlue  
- **CVE:** CVE-2017-0144  
- **Protocol Targeted:** SMBv1 (TCP Port 445)  
- **Patch Released By Microsoft:** March 2017 (MS17-010)

The exploit allowed Remote Code Execution (RCE) by sending specially crafted SMB packets to vulnerable systems.

Despite a patch being available two months prior to the attack, many systems remained unpatched.

---

## 🧠 Attack Chain (Technical Flow)

### 1️⃣ Initial Exploitation
- Attacker scans for systems with TCP port 445 open.
- EternalBlue exploit triggers remote code execution.

### 2️⃣ Backdoor Installation
- DoublePulsar backdoor injected.
- Used to load ransomware payload.

### 3️⃣ Encryption Phase
- Generates AES encryption key.
- Encrypts files locally.
- AES key encrypted using embedded RSA public key.
- Appends `.WCRY` extension to files.
- Drops ransom note: `@Please_Read_Me@.txt`

### 4️⃣ Worm Propagation
- Scans local subnet.
- Scans random external IP ranges.
- Repeats exploitation process automatically.

This worm capability enabled rapid global spread without user interaction.

---

## 🛑 Kill Switch Discovery

Security researcher Marcus Hutchins discovered that the malware checked a hardcoded domain before executing.

If the domain responded, the ransomware terminated itself.

The domain: 
Hutchins registered the domain, which significantly slowed the spread of the attack.

Important: This did not decrypt infected machines — it only stopped new infections.

---

## 🏥 Major Organizations Affected

- UK National Health Service (NHS)
- Telefónica (Spain)
- FedEx
- Renault

The NHS experienced major disruption including:
- Cancelled surgeries
- Ambulance diversion
- Disabled hospital systems

---

## 💥 Global Impact & Damage

- ~230,000 computers infected
- 150+ countries affected
- Estimated economic damage: $4B – $8B
- Ransom collected: ~51.6 BTC (~$130,000 in 2017 value)

Most damage resulted from operational downtime and recovery costs, not ransom payments.

---

## 🧭 MITRE ATT&CK Mapping

| Stage | Technique |
|-------|-----------|
| Initial Access | Exploit Public-Facing Application |
| Execution | Command Shell |
| Persistence | Service Installation |
| Lateral Movement | SMB / Admin Shares |
| Impact | Data Encrypted for Impact |

---

## 🚨 Indicators of Compromise (IOCs)

- Port 445 scanning activity
- SMBv1 traffic spikes
- `.WCRY` file extensions
- `@Please_Read_Me@.txt` ransom note
- Suspicious outbound DNS requests to kill-switch domain

---

## 🛡️ Mitigation & Defensive Lessons

1. Apply security patches immediately (MS17-010).
2. Disable SMBv1 protocol.
3. Implement network segmentation.
4. Maintain offline backups.
5. Monitor port 445 traffic.
6. Use IDS/IPS for exploit detection.

---

## 🔍 Attribution

In December 2017, the United States and United Kingdom publicly attributed the attack to the Lazarus Group, a North Korean state-sponsored threat actor.

---

## 📚 References

- Microsoft Security Bulletin MS17-010
- CVE-2017-0144
- Public government attribution statements (2017)
- Industry incident response reports

---

## 🎯 Purpose of This Repository

This case study was created for cybersecurity learning and portfolio demonstration purposes.  
It analyzes the attack from a defensive and threat intelligence perspective.

No malware code or exploit scripts are included.

---
