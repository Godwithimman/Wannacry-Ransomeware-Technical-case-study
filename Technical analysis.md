# 🔬 WannaCry — Technical Analysis

## 🧠 Exploited Vulnerability

- CVE: CVE-2017-0144
- Protocol: SMBv1
- Port: TCP 445
- Exploit: EternalBlue
- Backdoor Loader: DoublePulsar

The vulnerability allowed Remote Code Execution (RCE) via crafted SMB packets.

---

## 🔗 Attack Chain Breakdown

### 1️⃣ Reconnaissance
- Scans for systems with TCP 445 open.
- Identifies unpatched Windows systems.

### 2️⃣ Exploitation
- EternalBlue triggers buffer overflow.
- Attacker gains SYSTEM-level access.

### 3️⃣ Payload Deployment
- DoublePulsar backdoor injected.
- Ransomware binary executed in memory.

### 4️⃣ Encryption Routine
- Generates AES key per system.
- Encrypts files locally.
- Encrypts AES key using embedded RSA public key.
- Appends `.WCRY` extension.

### 5️⃣ Persistence
- Creates Windows service.
- Ensures execution after reboot.

### 6️⃣ Worm Propagation
- Scans internal network.
- Scans random internet IP addresses.
- Repeats exploitation process automatically.

This autonomous spread made WannaCry a ransomware worm rather than traditional ransomware.

---

## 🔐 Encryption Details

- Symmetric encryption: AES
- Key protection: RSA-2048
- Targets: ~176 file types
- Ransom note file: @Please_Read_Me@.txt

No publicly available universal decryptor exists for most victims.

---

## 🛑 Kill Switch Logic

Before encrypting files, malware checks if a specific domain resolves.

If connection succeeds:
- Malware terminates.

If connection fails:
- Encryption proceeds.

This logic flaw enabled global containment.
