# 🧪 Full Lab Workflow: Detecting Persistence with RegShot + Process Explorer

### 🖥️ VM to Use:
- ✅ **Windows Server Victim VM**  
  (This is the only VM you need for this lab.)

---

## 🔢 PHASE 1: TOOL CHECK – Are RegShot and Process Explorer Installed?

### 1. 🔍 Check if RegShot is Installed:
- Press `Win + S`, search for **RegShot**
- Or navigate to common paths like:
  - `C:\Tools\RegShot\`
  - `C:\Program Files\RegShot\`
  - `Desktop\RegShot\`
- Look for:
  - `regshot.exe` or `regshot-x64-unicode.exe`
- ✅ If found, double-click and confirm it launches  
- ❌ If not found, download from:  
  [https://sourceforge.net/projects/regshot/](https://sourceforge.net/projects/regshot/)

---

### 2. 🔍 Check if Process Explorer is Installed:
- Search for **Process Explorer** or locate:
  - `C:\Tools\Sysinternals\`
  - `C:\Program Files\ProcessExplorer\`
  - `Desktop\ProcessExplorer\`
- Look for:
  - `procexp64.exe` or `procexp.exe`
- ✅ If found, double-click and confirm it launches with process tree  
- ❌ If not found, download from:  
  [https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)

---

## 🔢 PHASE 2: SETUP BENIGN PERSISTENCE SIMULATION

### 3. 🛠 Create a Safe Test File:
Open PowerShell as Administrator and run:

```powershell
echo echo Hello from benign test > C:\Users\Public\benign_test.bat
```

### 4. 🧪 Add a Registry Run Key (Common Persistence Method):

```powershell
New-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" `
  -Name "FakeStartup" -Value "C:\Users\Public\benign_test.bat" -PropertyType String
```

---

## 🔢 PHASE 3: SNAPSHOT DETECTION WITH REGSHOT

### 5. 🚀 Launch RegShot as Administrator

### 6. 📸 Take First Snapshot ("Before")
- Click **1st Shot**
- Select save location (e.g., Desktop)
- Name it `before`

### 7. 📸 Take Second Snapshot ("After")
- After step 4 (persistence added), return to RegShot
- Click **2nd Shot**
- Name it `after`

### 8. 📊 Compare Snapshots
- Click **Compare**
- Output will show:
  - ✅ Added registry entry:  
    `HKCU\Software\Microsoft\Windows\CurrentVersion\Run\FakeStartup`

---

## 🔢 PHASE 4: ANALYZE WITH PROCESS EXPLORER

### 9. 🚀 Launch Process Explorer as Administrator

### 10. ⚙️ Setup for Analysis:
- Go to:
  - `Options > Verify Image Signatures`
  - `View > Show Lower Pane`
  - `View > Lower Pane View > DLLs` or `Handles`

### 11. 🔍 Search for the Benign File:
- Press `Ctrl + F` or go to `Find > Find Handle or DLL`
- Search for:
  - `benign_test.bat`
  - or `FakeStartup`
- Use the Process Tree to inspect:
  - Startup hooks  
  - Suspicious parent-child process relationships

---

## 🔢 PHASE 5: CLEAN-UP (OPTIONAL)

### 12. ❌ Remove Test Registry Key and File:

```powershell
Remove-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "FakeStartup"
Remove-Item "C:\Users\Public\benign_test.bat"
```

---

## ✅ WHAT YOU GAINED

| Tool             | Skill Practiced                                                               |
|------------------|--------------------------------------------------------------------------------|
| RegShot          | Detecting registry-based persistence with before/after snapshot diffs         |
| Process Explorer | Investigating runtime persistence, startup entries, process trees             |
| Safe Simulation  | Learned real-world detection using 100% benign test methods                   |

---

