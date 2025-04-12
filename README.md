# 🧪 01 – Registry-Based Persistence Detection

## 🎯 Objective

This lab focuses on detecting **Windows registry-based persistence techniques** — specifically methods where attackers create autorun entries via registry keys.

You’ll simulate benign persistence using tools like **RegShot** and **Process Explorer** to analyze registry changes and inspect running processes.

---

## 🧭 MITRE ATT&CK Mapping

- **T1547.001** – [Registry Run Keys / Startup Folder](https://attack.mitre.org/techniques/T1547/001/)

---

## 🧰 Tools Used

| Tool | Purpose |
|------|--------|
| RegShot | Capture and compare registry snapshots |
| Process Explorer | Visual inspection of running processes and autostart locations |
| PowerShell | Simulate safe persistence |
| Notepad++ | Review `.log` diff output |
| (Optional) Sysmon | Log persistence registry key creation |

---

## 📂 Scenario Index

| Scenario | Description |
|----------|-------------|
| [`Lab-01-Benign-RunKey-Simulation`](.01-Registry-Persistence//Lab-01-Benign-RunKey-Simulation/) | Simulate and detect a benign Run key entry using RegShot and Process Explorer |
| *(Future)* `Lab-02-Autoruns-Analysis` | Detect persistence using Autoruns snapshotting |
| *(Future)* `Lab-03-ImageFileExecutionOptions` | Registry-based execution hijack technique |
| *(Future)* `Lab-04-SilentRegistryKeyViaScript` | Fileless persistence registry injection (safe simulation) |

---

## 🧠 Learning Outcomes

- Understand how registry keys are abused for persistence
- Use RegShot to identify added keys and values
- Inspect system processes using Process Explorer
- Practice safe, malware-free simulation in an isolated SOC lab environment

---

> **Note:** All simulations use benign scripts. No real malware is used. This lab is designed for blue teamers, SOC analysts, and detection engineers.

