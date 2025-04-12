1. Use **RegShot** to detect registry changes (persistence indicators).  
2. Use **Process Explorer** to visually inspect processes and persistence hooks.  
3. ✅ Ensure both tools are installed and working.  
4. ✅ Know which VM to run it on.  
5. ✅ Test only with benign or EICAR-style files.

---

## 🖥️ VM TO USE

✅ **Windows Server Victim VM**  
This is where you simulate persistence and run both **RegShot** and **Process Explorer**.

---

## 🧰 STEP 1: Install & Verify RegShot + Process Explorer

### 🔹 RegShot
1. Download RegShot portable (e.g., from [https://sourceforge.net/projects/regshot/](https://sourceforge.net/projects/regshot/)).
2. Extract and run `regshot-x64-unicode.exe` or `regshot.exe` depending on your system.
3. ✅ **Verify it's working:**
   - Launch it.
   - Click **"1st shot"**, wait.
   - Click **"2nd shot"**, then **"Compare"**.
   - Confirm that it outputs a diff file.

### 🔹 Process Explorer
1. Download Process Explorer from [https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)
2. Extract and run `procexp64.exe` (or `procexp.exe`).
3. ✅ **Verify it's working:**
   - Launch it.
   - Confirm it loads and shows processes in a tree view.
   - Look for `autostart` locations in **View > Show Lower Pane**, then `Ctrl+L` for DLLs or handles.

---

## 🧪 STEP 2: Safe Persistence Simulation (Benign)

Use **PowerShell** or **cmd** to simulate a benign persistence mechanism.

### ✅ Startup Registry Entry:
```powershell
New-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "FakeStartup" -Value "C:\Users\Public\benign_test.bat" -PropertyType String
```

Or create the test batch file:

```powershell
echo echo Hello from benign test > C:\Users\Public\benign_test.bat
```

---

## 📸 STEP 3: Use RegShot to Detect Registry Persistence

1. Launch **RegShot** as admin.
2. Set output folder (e.g., Desktop).
3. Click **"1st shot"**, name it something like `before.log`.
4. Run your benign persistence simulation (add reg key or startup shortcut).
5. Back in RegShot, click **"2nd shot"** → then **"Compare"**.
6. ✅ **Review Output:**
   - Look under added keys for `"HKCU\Software\Microsoft\Windows\CurrentVersion\Run\FakeStartup"` or similar.

---

## 🔍 STEP 4: Use Process Explorer to Inspect for Persistence

1. Launch **Process Explorer** as admin.
2. Click `Find > Find Handle or DLL...` and search for:
   - `benign_test.bat`
   - or `FakeStartup`
3. Also:
   - Use **Options > Verify Signatures**
   - Use **View > Select Columns > Autostart Location**
   - Inspect suspicious entries in `explorer.exe`, `cmd.exe`, or your test file

---

## 🧹 STEP 5: Clean Up (Optional)

```powershell
Remove-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "FakeStartup"
Remove-Item "C:\Users\Public\benign_test.bat"
```

---

## 🧠 What You Learn

✅ Real-world use of **RegShot** for persistence diffing  
✅ Visual inspection with **Process Explorer**  
✅ Hands-on practice identifying startup methods  
✅ Confidence using these tools in malware analysis or SOC investigations  

---
