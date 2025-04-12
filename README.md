# 🧪 Lab 01 – Registry-Based Persistence Detection

## 🎯 Objective

Simulate and detect a basic **registry-based persistence** technique using:

- 🧠 **RegShot** – to compare registry changes.
- 🔍 **Process Explorer** – to inspect running processes and persistence hooks.

---

## 🖥️ Environment

| Component | Details |
|----------|---------|
| VM | Windows Server 2025 (Victim) |
| Network | Internal-only (SOC_Lab_Net) |
| Tools | RegShot, Process Explorer, PowerShell |

---

## 🧰 Tools Setup

### 🔹 RegShot

- Download: [https://sourceforge.net/projects/regshot/](https://sourceforge.net/projects/regshot/)
- Run `regshot-x64-unicode.exe` as admin

### 🔹 Process Explorer

- Download: [https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)
- Run `procexp64.exe` as admin

---

## 🔬 Simulation – Fake Persistence Entry

1. Create a benign `.bat` file:

```powershell
echo echo Hello from benign test > C:\Users\Public\benign_test.bat
```

2. Create a startup registry key:

```powershell
New-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "FakeStartup" -Value "C:\Users\Public\benign_test.bat" -PropertyType String
```

---

## 🔍 Detection Workflow

### ✅ RegShot

1. Open RegShot
2. Take `1st shot`
3. Run persistence simulation
4. Take `2nd shot` → Click `Compare`
5. Review registry diff output:
   - Look for added key: `FakeStartup` in `Run` path

### ✅ Process Explorer

1. Search (`Ctrl+F`) for:
   - `benign_test.bat`
   - `FakeStartup`
2. Enable:
   - `View > Show Lower Pane`
   - `Options > Verify Signatures`

---

## 🧹 Cleanup

```powershell
Remove-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "FakeStartup"
Remove-Item "C:\Users\Public\benign_test.bat"
```

---

## 🧠 Skills Practiced

- Registry diffing with RegShot
- Visual process inspection
- Detecting startup registry persistence
- Cleanup and simulation hygiene

---
