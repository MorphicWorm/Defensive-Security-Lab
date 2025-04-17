# ⚠️ Work in Progress

This section of the Defensive Security Lab is currently under active development. Content may change frequently as new simulation techniques are added and tested.

---

# 🛡️ Persistence Techniques Simulation

This directory contains simulated persistence mechanisms used for defensive security testing, threat detection development, and blue team training. Each technique is designed to mimic common attacker behaviors, helping defenders test and validate their detection rules, EDR responses, and SOC analysis workflows.

## 📁 Directory Structure

- `startup_folder/` – Simulates payloads placed in the Windows startup folder.
- `registry_run_keys/` – Contains scripts to add persistence via `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`.
- `scheduled_tasks/` – Simulated scheduled task creation for persistence.
- `wmipersistence/` – WMI-based persistence simulation.
- `services/` – Simulated malicious services for persistence.

## 🎯 Purpose

This simulation set is part of the broader **Defensive Security Lab** and is meant for:

- Blue team hands-on practice
- Testing SIEM and EDR detection logic
- Creating and tuning alerting rules
- Building a deeper understanding of attacker persistence techniques

> ⚠️ These simulations should only be run in a **safe, isolated lab environment**.

## 📚 References

- [MITRE ATT&CK T1053 – Scheduled Task/Job](https://attack.mitre.org/techniques/T1053/)
- [MITRE ATT&CK T1547 – Boot or Logon Autostart Execution](https://attack.mitre.org/techniques/T1547/)
- [Red Canary Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)

## 🔐 Disclaimer

This repository is for **educational and defensive security training** purposes only. Do **not** use any scripts or techniques on unauthorized systems.

