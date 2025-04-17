# 🧪 Phishing Email Analysis Simulation Lite Lab

This lab simulates the analysis of a realistic phishing email and its malicious attachment — all performed locally and safely within a controlled environment.

## 🎯 Objective

- Manually review phishing email headers
- Identify suspicious fields (e.g., `Reply-To`, `Received`, links)
- Generate cryptographic hashes of the attachment for IOC analysis
- Simulate quarantine and detection behavior in a SOC-like scenario

---

## 📁 Lab Environment

All simulation artifacts are stored in:

```
C:\Phishing-Email-Lab
```

Files included:
- `phish_email.eml` – Simulated phishing email (spoofed headers + base64 attachment)
- `invoice.exe` – Simulated malicious attachment (EICAR or dummy file)
- [Future] PowerShell script to automate full simulation

---

## 📌 Key Concepts Practiced

- Manual header analysis (`From`, `Reply-To`, `Received`, MIME structure)
- Base64-encoded attachment identification
- Attachment hash generation (`MD5`, `SHA1`, `SHA256`)
- Defender-safe test file handling (EICAR trigger or dummy file fallback)

---

## ⚠️ Defender Note

If using the EICAR string, Windows Defender may auto-quarantine `invoice.exe`. You may:

- **Option A:** Temporarily disable real-time protection to complete the analysis  
- **Option B:** Use a harmless dummy `.exe` file as a safe alternative

---

## 🔄 Next Steps

- [ ] Add `simulate-lab.ps1` for full step automation
- [ ] Extend to parse `.eml` and auto-extract base64 attachments
- [ ] Create PowerShell log/report output from each run

---

**Status:** ✅ Initial version complete — ready for hash and header analysis practice.

