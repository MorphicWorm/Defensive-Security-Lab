# 🛡️ Defensive Security Lab

Welcome to my **Defensive Security Lab** — a personal, hands-on learning space focused on simulating and detecting common attacker techniques such as persistence, process injection, and system tampering on Windows systems.

This repo is designed to demonstrate real-world investigation and detection skills using safe, malware-free simulations. Each lab focuses on specific techniques, tools, or scenarios.

---

## 🔬 Lab Environment Setup

All labs are run in a fully isolated virtual lab built on VirtualBox. The setup includes a Windows target system used for simulation and analysis, with room for expansion as new tools and skills are added.

### 🖥️ Virtual Machine Layout

| VM | Role | Tools/Configs |
|----|------|----------------|
| **Windows Server 2025** *(Victim VM)* | Primary system for persistence simulation and detection | RegShot, Process Explorer, PowerShell, Sysmon, Event Viewer |
| **(Optional) Analyst Workstation** | For future centralized log collection and IR tools | Splunk, Velociraptor, Wireshark, Notepad++ |
| **Network** | Internal virtual switch only (`SOC_Lab_Net`) | Dual NIC: NAT (for updates), Internal (lab communication only) |

---

## 🔒 Simulation Approach

- No real malware is used — only safe batch files and EICAR test strings.
- Simulated persistence techniques (e.g., startup folder, Run keys, scheduled tasks).
- Focus on system changes, registry behavior, process trees, and autostarts.
- Labs are documented with snapshots, commands, and cleanup steps.

---

## 🧪 Lab Index

| Lab | Description |
|-----|-------------|
| `01-RegShot-ProcessExplorer` | Detecting registry-based persistence using RegShot and analyzing startup processes with Process Explorer |
| `02-Startup-Folder-Persistence` | Simulating persistence via Startup folder entries |
| `03-Scheduled-Task-Persistence` | Creating and detecting benign scheduled tasks for persistence |
| `04-Active-Setup-Persistence` *(coming soon)* | Analyzing how Active Setup can be abused for stealthy execution |
| `05-Windows-Logs-Investigation` *(future)* | Reviewing Event Viewer and Sysmon logs related to persistence activity |
| `06-Phishing-Header-Analysis` *(optional/future)* | Parsing and analyzing email headers using test phishing messages |

---

## 🧰 Tools Used Across Labs

- [RegShot](https://sourceforge.net/projects/regshot/) – Registry snapshot and diff
- [Process Explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer) – Advanced process inspection
- PowerShell – Scripting and automation of benign simulations
- Sysmon – System event logging for future log analysis labs
- Event Viewer – Manual log inspection
- Notepad++ – Log and diff analysis

