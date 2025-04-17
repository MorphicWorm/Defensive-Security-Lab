## 🧪 Enhanced Safe Phishing Simulation – Offline (All on Server Victim VM)  
📁 **Lab Folder:** `C:\Phishing-Email-Lab`  
🎯 **Focus:** Analyze phishing headers + generate hash for simulated attachment  
🛡️ **Defender-safe options included**

---

### ✅ 1. Create Lab Directory & Simulated Phishing Email

Copy and paste below code to Powershell:

```powershell
New-Item -Path "C:\Phishing-Email-Lab" -ItemType Directory -Force
Set-Location "C:\Phishing-Email-Lab"

$email = @"
Return-Path: <alert@paypal.com>
Received: from unknown (HELO smtp.fakehost.net) (203.0.113.5)
    by mx1.mail.local with ESMTP; Sat, 13 Apr 2025 09:40:12 +0000
Received: from internal.fake ([10.0.0.5])
    by smtp.fakehost.net with ESMTP; Sat, 13 Apr 2025 09:38:45 +0000
From: PayPal Security <alert@paypal.com>
Reply-To: noreply-paypal-verification@protonmail.com
To: victim@domain.local
Subject: [PayPal Alert] Unusual Login Attempt Detected
Date: Sat, 13 Apr 2025 09:42:00 +0000
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----=_Part_002"

------=_Part_002
Content-Type: text/html; charset="UTF-8"
Content-Transfer-Encoding: quoted-printable

<html>
<body>
<p>Dear Customer,</p>
<p>We detected a suspicious login attempt from a new device:</p>
<ul>
  <li><b>Device:</b> Windows 10 Chrome Browser</li>
  <li><b>Location:</b> Lagos, Nigeria</li>
  <li><b>Time:</b> Sat, April 13 2025, 09:33 UTC</li>
</ul>
<p>If this was not you, please <a href="http://paypal-account-verify.com/secure">click here to verify your account</a> and secure your access immediately.</p>
<p>Regards,<br>PayPal Security Team</p>
</body>
</html>

------=_Part_002
Content-Type: application/octet-stream; name="invoice.exe"
Content-Disposition: attachment; filename="invoice.exe"
Content-Transfer-Encoding: base64

WDVPIVAlQEFQWzRcUFpYNTRQXl4pN0NDKTd9JEVJQ0FSLVNUQU5EQVJELUFOVElWSVJVUy1URVNULUZJTEUhJEgrSCo=
------=_Part_002--
"@

$email | Out-File -FilePath ".\phish_email.eml" -Encoding UTF8
```

---

### 🧪 Two Options for the Attachment

#### ✅ Option 1 – Recreate Actual EICAR Attachment (May Trigger AV)

```powershell
$eicar = 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*'
$eicar | Out-File -FilePath "C:\Phishing-Email-Lab\invoice.exe" -Encoding ASCII
```

> ⚠️ **May be quarantined by Defender as a test virus.** Safe, but blocked.

---

#### 🛡️ If Defender Blocks It — Fix with These Options:

##### 🔒 Option A: Temporarily Disable Defender (Lab-Only)

1. Open **Windows Security**
2. Go to **Virus & Threat Protection**
3. Click **Manage Settings**
4. Turn **off Real-Time Protection**
5. Recreate the `invoice.exe` file
6. Re-enable protection after analysis

##### ✅ Option B: Use a Safe Dummy File Instead

```powershell
"This is just a fake invoice for phishing simulation." | Out-File -FilePath "C:\Phishing-Email-Lab\invoice.exe"
```

> ✅ This avoids AV quarantine and still lets you practice hash analysis.

---

### ✅ 2. Analyze the Email

```powershell
notepad C:\Phishing-Email-Lab\phish_email.eml
```

Check:
- `From:` vs `Reply-To:`
- IP hops in `Received:` headers
- Suspicious phishing link
- `.exe` file embedded in base64 format

---

### ✅ 3. Get Attachment Hashes

```powershell
$hashAlgos = @("MD5", "SHA1", "SHA256")

foreach ($algo in $hashAlgos) {
    Get-FileHash "C:\Phishing-Email-Lab\invoice.exe" -Algorithm $algo
}
```

> 💡 Save these for manual IOC tracking or submit to VirusTotal (if allowed).
