# 🛡️ WannaCry — Mitigation & Security Lessons

## 🔑 Key Security Failures

1. Delayed patch application (MS17-010).
2. Continued use of SMBv1.
3. Poor network segmentation.
4. Lack of offline backups.
5. Insufficient internal monitoring.

---

## ✅ Preventive Controls

### Patch Management
- Apply security patches immediately.
- Maintain automated update systems.

### Protocol Hardening
- Disable SMBv1.
- Restrict port 445 externally.

### Network Segmentation
- Separate critical systems.
- Limit lateral movement paths.

### Backup Strategy
- Maintain offline backups.
- Test restore procedures regularly.

### Monitoring & Detection
- Monitor abnormal SMB traffic.
- Deploy IDS/IPS solutions.
- Detect unusual encryption activity.

---

## 🧭 SOC Detection Indicators

- Rapid port 445 scanning
- Sudden file extension changes (.WCRY)
- High-volume file write operations
- DNS queries to suspicious domains

---

## 🎯 Strategic Lessons

WannaCry demonstrated:

- A patched vulnerability can still cause global damage if updates are ignored.
- Wormable exploits are exponentially more destructive.
- Basic cybersecurity hygiene prevents catastrophic impact.
- Ransomware preparedness must include business continuity planning.

---

## 📌 Final Takeaway

WannaCry was not a zero-day attack.
It exploited a known vulnerability with an available patch.

The incident remains one of the clearest examples of why patch management is a critical security control.
